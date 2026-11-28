# Client Application Development

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1073a3b39ff1929d726da25749252544adc3f89e translatedAt=2026-11-28T01:24:29.709Z nl=1 -->

## When to Use

The [OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md) content embedding module provides an object editing framework and technology for inter-application document embedding and collaborative editing.

An OE client application embeds external documents into its own application. By calling the APIs provided by [content_embed_proxy.h](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md) in the OE framework layer, it can embed external documents, display document snapshots, and launch an OE server application on demand to edit the documents.

Typical use cases include:
- Embedding an Excel spreadsheet into a CAD document and starting Excel to edit the spreadsheet by clicking the embedded object.
- Embedding documents in various formats, such as images and tables, into a document editor.
- Embedding documents from other applications into a note-taking application for cross-application collaboration.

## Constraints
Before calling the APIs, ensure that the device supports the `SystemCapability.ContentEmbed.ObjectEditor` system capability. For details about checking whether a system capability is supported, see [canIUse()](../reference/common/syscap-ndk-8h.md#caniuse). You must also declare the `ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION` permission. For details, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).

## Available APIs

Common APIs are listed in the following table. For more API details, see [OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md).

**Table 1** Main client APIs

| API | Description |
| ------- | ---- |
| OH_ContentEmbed_CreateDocumentByFile | Creates an [OE document](content-embed-kit-terminology.md#oe-document) based on the path of the embedded document. |
| OH_ContentEmbed_CreateDocumentByOEid | Creates an OE document based on an [OEID](content-embed-kit-terminology.md#oeid).|
| OH_ContentEmbed_LoadDocumentFromFile | Loads an OE document from an existing [OE format file](content-embed-kit-terminology.md#oe-format-file). |
| OH_ContentEmbed_CreateExtensionProxy | Creates a [client OE object](content-embed-kit-terminology.md#client-oe-object). |
| OH_ContentEmbed_DestroyExtensionProxy | Destroys the client OE object and releases related resources. |
| OH_ContentEmbed_Proxy_RegisterOnUpdateFunc | Registers a callback with the client OE object for OE document updates. |
| OH_ContentEmbed_Proxy_RegisterOnErrorFunc | Registers a callback with the client OE object for errors triggered by the OE document. |
| OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc | Registers a callback with the client OE object for OE document editing completion. |
| OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc | Registers a callback with the client OE object for [OE Extension](content-embed-kit-terminology.md#oe-extension) stop events. |
| OH_ContentEmbed_Proxy_StartWork | Enables the client to communicate with the Object Editor service across processes through the client OE object, start the OE Extension component, and create a server OE object. |
| OH_ContentEmbed_Proxy_StopWork | Enables the client to communicate with the Object Editor service across processes through the client OE object, destroy the server OE object, and release resources. |
| OH_ContentEmbed_Proxy_GetSnapshot | Obtains the snapshot image of the current OE document from the client OE object for preview or thumbnail display. |
| OH_ContentEmbed_Proxy_DoEdit | Enables the client to communicate with the OE Extension component across processes through the client OE object and notify the server to start a UIAbility for editing the OE document. |
| OH_ContentEmbed_Proxy_GetDocument | Obtains the OE document object associated with the client OE object. |
| OH_ContentEmbed_Document_Read | Reads OE format file data from an OE document and stores the data in a buffer. |
| OH_ContentEmbed_DestroyDocument | Destroys an OE document object and releases resources. |

## How to Develop

The following example shows the complete process of developing an OE client application using Native APIs.

### Adding Dynamic Libraries
Add the following link libraries to **src/main/cpp/CMakeLists.txt** of the Native project.

<!-- @[content_embed_client_cmake](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/CMakeLists.txt) -->  

``` Text
target_link_libraries(entry PUBLIC
    libcontent_embed_ndk.so
    libhilog_ndk.z.so
    libace_napi.z.so
    libpixelmap.so
    libohfileshare.so
)
```

### Including Header Files

<!-- @[content_embed_client_include_headers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/content_embed/content_embed_proxy.cpp) -->  

``` C++
#include <string>
#include <ContentEmbedKit/content_embed/content_embed_common.h>
#include <ContentEmbedKit/content_embed/content_embed_document.h>
#include <ContentEmbedKit/content_embed/content_embed_proxy.h>
#include <hilog/log.h>
#include <multimedia/image_framework/image/pixelmap_native.h>
```

### Querying Embeddable Document Information Supported by the Current Device

Query information about all embeddable documents supported by the current device in the specified language.

<!-- @[content_embed_client_query_all_format](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/content_embed/content_embed_proxy.cpp) -->  

``` C++
ContentEmbed_Info* CreateContentEmbedInfoWithCount(
    const std::string &locale, uint32_t& outCount, ContentEmbed_ErrorCode& outErr)
{
    outCount = 0;
    ContentEmbed_Info* info = nullptr;
    // Create a ContentEmbedInfo object.
    ContentEmbed_ErrorCode err = OH_ContentEmbed_CreateContentEmbedInfo(&info);
    if (err != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_CreateContentEmbedInfo failed, errCode: %{public}d.", err);
        outErr = err;
        return nullptr;
    }
    // Obtain ContentEmbedInfo for the specified locale.
    err = OH_ContentEmbed_GetContentEmbedInfo(locale.c_str(), info);
    if (err != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_GetContentEmbedInfo failed, errCode: %{public}d.", err);
        // Destroy the ContentEmbedInfo object if the query fails.
        OH_ContentEmbed_DestroyContentEmbedInfo(info);
        outErr = err;
        return nullptr;
    }
    // Obtain the number of Format objects in the ContentEmbedInfo object.
    err = OH_ContentEmbed_GetFormatCountFromInfo(info, &outCount);
    if (err != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_GetFormatCountFromInfo failed, errCode: %{public}d.", err);
        // Destroy the ContentEmbedInfo object if the query fails.
        OH_ContentEmbed_DestroyContentEmbedInfo(info);
        outErr = err;
        return nullptr;
    }
    outErr = CE_ERR_OK;
    return info;
}

ContentEmbed_ErrorCode QueryAllFormat(const std::string &locale)
{
    uint32_t count = 0;
    ContentEmbed_ErrorCode errCode = CE_ERR_OK;
    ContentEmbed_Info* contentEmbedInfo = CreateContentEmbedInfoWithCount(locale, count, errCode);
    if (contentEmbedInfo == nullptr) {
        return errCode;
    }
    for (uint32_t i = 0; i < count; i++) {
        ContentEmbed_Format* ceFormat = nullptr;
        // Obtain ContentEmbed_Format information with index i from the ContentEmbedInfo object.
        errCode = OH_ContentEmbed_GetFormatFromInfo(contentEmbedInfo, i, &ceFormat);
        if (errCode != CE_ERR_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_GetFormatFromInfo failed, errCode: %{public}d.", errCode);
            continue;
        }
        char oeid[MAX_OEID_LENGTH];
        // Obtain the OEID.
        errCode = OH_ContentEmbed_GetOEidFromFormat(ceFormat, oeid);
        if (errCode != CE_ERR_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_GetOEidFromFormat failed, errCode: %{public}d.", errCode);
            continue;
        }
        char name[MAX_NAME_LENGTH];
        char description[MAX_DESCRIPTION_LENGTH];
        // Obtain the name and description.
        errCode = OH_ContentEmbed_GetNameAndDescriptionFromFormat(ceFormat, name, description);
        if (errCode != CE_ERR_OK) {
            OH_LOG_ERROR(LOG_APP,
                "OH_ContentEmbed_GetNameAndDescriptionFromFormat failed, errCode: %{public}d.", errCode);
            continue;
        }
        OH_PixelmapNative* pixelMap = nullptr;
        // Obtain the icon.
        errCode = OH_ContentEmbed_GetIconFromFormat(ceFormat, &pixelMap);
        if (errCode != CE_ERR_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_GetIconFromFormat failed, errCode: %{public}d.", errCode);
            continue;
        }
        // Release pixelMap when it is no longer needed.
        if (pixelMap != nullptr) {
            OH_PixelmapNative_Destroy(&pixelMap);
        }
        unsigned int extensionCount = 0;
        // Obtain file name extensions.
        char **fileNameExtensions = OH_ContentEmbed_GetFileNameExtensionsFromFormat(ceFormat, &extensionCount);
        if (fileNameExtensions == nullptr) {
            OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_GetFileNameExtensionsFromFormat failed");
            continue;
        }
        // ...
    }
    // Destroy the ContentEmbedInfo object.
    OH_ContentEmbed_DestroyContentEmbedInfo(contentEmbedInfo);
    return errCode;
}
```

### Querying Format Information Corresponding to an OEID

<!-- @[content_embed_client_query_format_by_oeid](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/content_embed/content_embed_proxy.cpp) -->  

``` C++
ContentEmbed_Format* QueryFormatByOEid(const std::string &oeid, const std::string &locale,
    ContentEmbed_ErrorCode& outErr)
{
    ContentEmbed_Format* ceFormat = nullptr;
    // Create ContentEmbed_Format.
    ContentEmbed_ErrorCode errCode = OH_ContentEmbed_CreateContentEmbedFormat(&ceFormat);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_CreateContentEmbedFormat failed, errCode: %{public}d.", errCode);
        outErr = errCode;
        return nullptr;
    }
    errCode = OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale(oeid.c_str(), locale.c_str(), ceFormat);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP,
            "OH_ContentEmbed_GetContentEmbedFormatByOEidAndLocale failed, errCode: %{public}d.", errCode);
        // Destroy the ContentEmbed_Format object if the query fails.
        OH_ContentEmbed_DestroyContentEmbedFormat(ceFormat);
        outErr = errCode;
        return nullptr;
    }
    char name[MAX_NAME_LENGTH];
    char description[MAX_DESCRIPTION_LENGTH];
    // Obtain the name and description.
    errCode = OH_ContentEmbed_GetNameAndDescriptionFromFormat(ceFormat, name, description);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_GetNameAndDescriptionFromFormat failed, errCode: %{public}d.", errCode);
        OH_ContentEmbed_DestroyContentEmbedFormat(ceFormat);
        outErr = errCode;
        return nullptr;
    }
    OH_PixelmapNative* pixelMap = nullptr;
    // Obtain the icon.
    errCode = OH_ContentEmbed_GetIconFromFormat(ceFormat, &pixelMap);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_GetIconFromFormat failed, errCode: %{public}d.", errCode);
        OH_ContentEmbed_DestroyContentEmbedFormat(ceFormat);
        outErr = errCode;
        return nullptr;
    }
    if (pixelMap != nullptr) {
        OH_PixelmapNative_Destroy(&pixelMap);
    }
    unsigned int count = 0;
    // Obtain file name extensions.
    char **fileNameExtensions = OH_ContentEmbed_GetFileNameExtensionsFromFormat(ceFormat, &count);
    if (fileNameExtensions == nullptr) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_GetFileNameExtensionsFromFormat failed");
        OH_ContentEmbed_DestroyContentEmbedFormat(ceFormat);
        outErr = CE_ERR_NULL_POINTER;
        return nullptr;
    }
    outErr = CE_ERR_OK;
    return ceFormat;
}
```

### Creating an OE Document

1. Create an OE document based on an OEID.

    <!-- @[content_embed_client_create_document_by_oeid](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/content_embed/content_embed_proxy.cpp) -->  
    
    ``` C++
    ContentEmbed_Document* CreateDocumentByOEid(const std::string &oeid, ContentEmbed_ErrorCode& errCode)
    {
        ContentEmbed_Document* ceDocument = nullptr;
        // Create an OE document based on the OEID.
        errCode = OH_ContentEmbed_CreateDocumentByOEid(oeid.c_str(), &ceDocument);
        if (errCode != CE_ERR_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_CreateDocumentByOEid failed, errCode: %{public}d.", errCode);
            return nullptr;
        }
        return ceDocument;
    }
    ```

2. Create an OE document based on a file.

    <!-- @[content_embed_client_create_document_by_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/content_embed/content_embed_proxy.cpp) -->  
    
    ``` C++
    // Whether to create the OE document in linked mode. If isLinking is true, the OE document is created in linked mode. If isLinking is false, the OE document is created in embedded mode.
    ContentEmbed_Document* CreateDocumentByFile(const std::string &filePath, bool isLinking,
        ContentEmbed_ErrorCode& errCode)
    {
        ContentEmbed_Document* ceDocument = nullptr;
        // Create an OE document based on a file.
        errCode = OH_ContentEmbed_CreateDocumentByFile(filePath.c_str(), filePath.size(), isLinking, &ceDocument);
        if (errCode != CE_ERR_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_CreateDocumentByFile failed, errCode: %{public}d.", errCode);
            return nullptr;
        }
        return ceDocument;
    }
    ```

3. Load an OE document from an [OE format file](content-embed-kit-terminology.md#oe-format-file). If the OE format file is stored as a data stream, save it to local storage before using this API.

    <!-- @[content_embed_client_load_document_from_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/content_embed/content_embed_proxy.cpp) -->  
    
    ``` C++
    static ContentEmbed_Document* LoadDocumentFromFile(const std::string &oeFormatFilePath, ContentEmbed_ErrorCode& errCode)
    {
        ContentEmbed_Document* ceDocument = nullptr;
        // Load an OE document from an OE format file.
        errCode = OH_ContentEmbed_LoadDocumentFromFile(oeFormatFilePath.c_str(),
            oeFormatFilePath.size(), &ceDocument);
        if (errCode != CE_ERR_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_LoadDocumentFromFile failed, errCode: %{public}d.", errCode);
            return nullptr;
        }
        return ceDocument;
    }
    ```

### Creating a Client OE Object

Create a client OE object based on the OE document and the current context instance, associate the OE document with the client OE object, and use the object to communicate with the server.

<!-- @[content_embed_client_create_proxy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/content_embed/content_embed_proxy.cpp) -->  

``` C++
constexpr size_t CHUNK_SIZE = 4 * 1024 * 1024;
void ClientCallBack_OnUpdateFunc(ContentEmbed_ExtensionProxy *proxy)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallBack_OnUpdateFunc");
    // Write OE document data to the client application document.
    ContentEmbed_Document *document = nullptr;
    ContentEmbed_ErrorCode errCode = OH_ContentEmbed_Proxy_GetDocument(proxy, &document);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Proxy_GetDocument failed, errCode: %{public}d.", errCode);
        return;
    }
    bool isLinking = false;
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Document_IsLinking(document, &isLinking);
    OH_LOG_INFO(LOG_APP, "ret: %{public}d, isLinking: %{public}d", ret, isLinking);
    if (ret == CE_ERR_OK && isLinking) {
        OH_LOG_INFO(LOG_APP, "linking document, No need to save to the sandbox");
        return;
    }
    uint8_t *buffer = new (std::nothrow) uint8_t[CHUNK_SIZE + 1];
    if (!buffer) {
        return;
    }
    size_t offset = 0;
    size_t actualRead = 0;

    do {
        // Read OE document content.
        ret = OH_ContentEmbed_Document_Read(buffer, CHUNK_SIZE, document, offset, &actualRead);
        if (ret != CE_ERR_OK || actualRead == 0) {
            break;
        }
        // Process the buffer data stream as needed.
        // ...
        offset += actualRead;
    } while (ret == CE_ERR_OK && actualRead != 0);
    delete[] buffer;
}

void ClientCallBack_OnErrorFunc(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)
{
    OH_LOG_ERROR(LOG_APP, "Enter ClientCallBack_OnErrorFunc, error: %{public}d", error);
}

void ClientCallBack_OnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, bool dataModified)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallBack_OnEditingFinishedFunc, dataModified: %{public}d", dataModified);
    // After editing is complete, destroy the client OE object if it is no longer needed.
    OH_ContentEmbed_DestroyExtensionProxy(proxy);
}

void ClientCallBack_OnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallBack_OnExtensionStoppedFunc");
}

// contextPtr: current context instance.
// oeDocument: OE document.
void CreateProxy(void* contextPtr, ContentEmbed_Document *oeDocument)
{
    ContentEmbed_ExtensionProxy* proxy = nullptr;
    // Create a client OE object.
    ContentEmbed_ErrorCode errCode = OH_ContentEmbed_CreateExtensionProxy(oeDocument, &proxy, contextPtr);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_CreateExtensionProxy failed, errCode: %{public}d.", errCode);
        return;
    }
    // Register callbacks for document updates, errors, editing completion, and other events. The callbacks can be registered in any order, but none can be omitted.
    // Register the OE document update callback.
    errCode = OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(proxy, ClientCallBack_OnUpdateFunc);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Proxy_RegisterOnUpdateFunc failed, errCode: %{public}d.", errCode);
        return;
    }
    // Register the OE document error callback.
    errCode = OH_ContentEmbed_Proxy_RegisterOnErrorFunc(proxy, ClientCallBack_OnErrorFunc);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Proxy_RegisterOnErrorFunc failed, errCode: %{public}d.", errCode);
        return;
    }
    // Register the OE document editing completion callback.
    errCode = OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(proxy, ClientCallBack_OnEditingFinishedFunc);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP,
            "OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc failed, errCode: %{public}d.", errCode);
        return;
    }
    // Register the callback for Extension instance stop events.
    errCode = OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(proxy, ClientCallBack_OnExtensionStoppedFunc);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP,
            "OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc failed, errCode: %{public}d.", errCode);
        return;
    }
}
```

Obtain the current context instance.

<!-- @[content_embed_client_get_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
testNapi.receiveContext(context);
```

<!-- @[content_embed_client_receive_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
napi_value ReceiveContext(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value argv[2] = {nullptr};
    napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);

    // Obtain the UIAbilityContext object passed from ArkTS.
    napi_value contextObj = argv[0];
    void* contextPtr = nullptr;
    napi_ref tmp = nullptr;
    // Create a strong reference and increment the reference count by 1 to prevent the Context from being reclaimed by ArkTS garbage collection.
    napi_create_reference(env, contextObj, 1, &tmp);
    // Unwrap the ArkTS object into a C++ pointer.
    napi_status status = napi_unwrap(env, contextObj, &contextPtr);
    if (status != napi_ok || contextPtr == nullptr) {
        // Error handling.
        napi_throw_error(env, nullptr, "Failed to unwrap context");
        return nullptr;
    }
    // Record contextPtr for later use.
    // ...
    return nullptr;
}

EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        // ...
        {"receiveContext", nullptr, ReceiveContext, nullptr, nullptr, nullptr, napi_default, nullptr},
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END
```

### Implementing Interaction Between the Client OE Object and the OE Extension

1. Start the OE Extension component.
2. Query the capabilities of the OE Extension component.
3. Edit a document by notifying the OE server to start a UIAbility.
4. Query the editing status of the OE document.
5. Obtain the OE document snapshot.

<!-- @[content_embed_client_handle_proxy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEClientDemo/entry/src/main/cpp/content_embed/content_embed_proxy.cpp) -->  

``` C++
static void HandleProxy(ContentEmbed_ExtensionProxy* proxy)
{
    ContentEmbed_ErrorCode errCode = CE_ERR_OK;
    // Start the OE Extension component.
    errCode = OH_ContentEmbed_Proxy_StartWork(proxy);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Proxy_StartWork failed, errCode: %{public}d.", errCode);
        return;
    }
    uint32_t bitmask = 0;
    // Query the capabilities of the OE Extension component.
    errCode = OH_ContentEmbed_Proxy_GetCapability(proxy, &bitmask);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Proxy_GetCapability failed, errCode: %{public}d.", errCode);
        return;
    }
    if ((bitmask & CE_CAPABILITY_SUPPORT_DO_EDIT) != 0) {
        // If the server supports editing, notify the OE server to edit the OE document.
        errCode = OH_ContentEmbed_Proxy_DoEdit(proxy);
        if (errCode != CE_ERR_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Proxy_DoEdit failed, errCode: %{public}d.", errCode);
            return;
        }
    }
    // Proactively query the editing status of the OE document.
    bool isEditing = false;
    bool isModified = false;
    // Query the editing status of the embedded document.
    errCode = OH_ContentEmbed_Proxy_GetEditStatus(proxy, &isEditing, &isModified);
    if (errCode != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Proxy_GetEditStatus failed, errCode: %{public}d.", errCode);
    }
    if ((bitmask & CE_CAPABILITY_SUPPORT_SNAPSHOT) != 0) {
        // If the server supports OE snapshot retrieval, obtain the OE document snapshot from the OE server.
        OH_PixelmapNative* pixelMap = nullptr;
        // Obtain the OE document snapshot.
        errCode = OH_ContentEmbed_Proxy_GetSnapshot(proxy, &pixelMap);
        if (errCode == CE_ERR_OK && pixelMap != nullptr) {
            OH_PixelmapNative_Release(pixelMap);
        }
    }
    // Stop the proxy when it no longer needs to interact with the server.
    OH_ContentEmbed_Proxy_StopWork(proxy);
}
```
