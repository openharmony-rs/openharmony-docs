# Server Application Development

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=f70c18b4fce2f79f2f5957342d67b8cf123678ec translatedAt=2026-11-28T01:24:29.784Z nl=1 -->

## When to Use

The [OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md) content embedding module provides an object editing framework and technology for inter-application document embedding and collaborative editing.

An OE server application uses the APIs provided by [content_embed_extension.h](../reference/apis-content-embed-kit/capi-content-embed-extension-h.md) to provide client applications with embedding and editing capabilities for documents in specific formats.

## Constraints
Before using the APIs, check whether the device supports the `SystemCapability.ContentEmbed.ObjectEditor` system capability. For details about how to check system capabilities, see [canIUse()](../reference/common/syscap-ndk-8h.md#caniuse). You must also declare the `ohos.permission.REGISTER_OBJECTEDITOR_EXTENSION` permission. For details, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).

## Available APIs

Common APIs are listed in the following table. For more API details, see [OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md).

**Table 1** Main server-side APIs

| API | Description |
| ------- | ---- |
| OH_ContentEmbed_Extension_GetExtensionInstance | Obtains the corresponding [OE Extension](content-embed-kit-terminology.md#oe-extension) instance from the ExtensionAbility base class instance. |
| OH_ContentEmbed_Extension_GetContentEmbedContext | Obtains the corresponding OE Extension context object from an OE Extension instance. |
| OH_ContentEmbed_Extension_GetContext | Obtains the AbilityRuntime context from an OE Extension context. |
| OH_ContentEmbed_Extension_RegisterOnCreateFunc | Registers the lifecycle callback invoked when an OE Extension instance is created. |
| OH_ContentEmbed_Extension_RegisterOnDestroyFunc | Registers the lifecycle callback invoked when an OE Extension instance is destroyed. |
| OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc | Registers the callback invoked when a [client OE object](content-embed-kit-terminology.md#client-oe-object) is connected. |
| OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc | Registers the callback invoked when a client OE object is disconnected. |
| OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc | Registers the callback invoked when a [server OE object](content-embed-kit-terminology.md#server-oe-object) writes data to an [OE document](content-embed-kit-terminology.md#oe-document) data stream. |
| OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc | Registers the callback invoked when a client OE object requests the OE document snapshot. |
| OH_ContentEmbed_Extension_RegisterOnDoEditFunc | Registers the callback invoked when a client OE object requests editing of an OE document. |
| OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc | Registers the callback invoked when a client OE object requests the OE document editing status. |
| OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc | Registers the callback invoked when a client OE object queries the capabilities supported by an OE Extension instance. |
| OH_ContentEmbed_Extension_GetContentEmbedDocument | Obtains the OE document instance associated with a server OE object. |
| OH_ContentEmbed_Extension_CallbackToOnUpdate | Triggers the OE document update callback registered by a client OE object. |
| OH_ContentEmbed_Extension_CallbackToOnError | Triggers the OE document error callback registered by a client OE object. |
| OH_ContentEmbed_Extension_CallbackToOnEditingFinished | Triggers the OE document editing completion callback registered by a client OE object. |
| OH_ContentEmbed_Extension_CallbackToOnExtensionStopped | Triggers the OE Extension stop callback registered by all client OE objects associated with the OE Extension. |
| OH_ContentEmbed_Extension_SetSnapshot | Sets the OE document snapshot image associated with a client OE object. |
| OH_ContentEmbed_Extension_ContextStartSelfUIAbility | Starts the application's own UIAbility through the OE Extension context. |

## How to Develop

The following example shows the complete process of developing an OE server application using Native APIs. It demonstrates how an OE server registers Extension component callbacks, responds to client requests, returns OE document snapshots, and starts a UIAbility to edit OE documents.

### Configuring OE ExtensionAbility for the OE Server

Since API version 24, configure OE ExtensionAbility in the `extensionAbilities` tag of the `module.json5` file. An example is as follows:

```json
"extensionAbilities": [
    {
        "name": "OEExtAbility",
        "srcEntry": "libentry.so",
        "type": "contentEmbed",
        "exported": true,
        "metadata": [
            {
                "name": "content_embed_config",
                "resource": "$profile:content_embed_config"
            }
        ]
    }
]
```

Configuration description:
- `name`: Name of the Extension component.
- `srcEntry`: Path of the entry library file of the Extension component.
- `type`: Must be set to `"contentEmbed"`.
- `exported`: Must be set to `true`, indicating that the component is exposed externally.
- [metadata](../quick-start/module-configuration-file.md#metadata): The `metadata` field adds a data item whose `name` is `"content_embed_config"` and whose `resource` is the resource index of the OE Extension configuration file.

You need to add a secondary JSON configuration file for configuring OE Extension information. For example, set `resource` to `"$profile:content_embed_config"` to point to the `resources/base/profile/content_embed_config.json` configuration file. The following is an example JSON file:

```json
{
    "content_embed_config": [
        {
            "oeid": "E0A8B74A-445B-4D7A-8B05-07B5509B50D8",
            "file_exts": ".doc|.docx",
            "icon": "$media:app_logo",
            "name": "$string:name",
            "description": "$string:description"
        }
    ]
}
```

Configuration description:
- `oeid`: System-recognizable identifier of an OE document, used to locate the OE server application that supports the OE document.
  - If the OE server application provides the same function on other operating systems, reuse the ID already used on those systems.
  - If this function of the OE server application is provided only on OpenHarmony, you are advised to use the built-in Terminal tool and run the `uuidgen` command to generate a new ID.
- `file_exts`: Supported file extensions, such as `".doc"` and `".docx"`. Use `"|"` to separate multiple file extensions.
- `icon`: Display icon used for OE document queries. The value is the index of the icon resource file.
- `name`: Display name used for OE document queries. Use a resource index for the name to support multiple languages.
- `description`: Display description used for OE document queries. Use a resource index for the description to support multiple languages.

### Adding Dynamic Libraries
Add the following link libraries to **src/main/cpp/CMakeLists.txt** of the Native project.

<!-- @[content_embed_server_cmake](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/CMakeLists.txt) -->  

``` Text
target_link_libraries(entry PUBLIC
    libcontent_embed_ndk.so
    libhilog_ndk.z.so
    libace_napi.z.so
    libpixelmap.so
    libability_runtime.so
    libability_base_want.so
    libimage_source.so
    libohfileuri.so
    libuv.so
)
```

### Including Header Files

<!-- @[content_embed_server_include_headers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
#include <cstdint>
#include <string>
#include <vector>
#include <unordered_map>
#include <fstream>
#include <hilog/log.h>
#include <AbilityKit/ability_base/want.h>
#include <AbilityKit/ability_runtime/application_context.h>
#include <ContentEmbedKit/content_embed/content_embed_document.h>
#include <ContentEmbedKit/content_embed/content_embed_extension.h>
#include <filemanagement/file_uri/oh_file_uri.h>
#include <multimedia/image_framework/image/image_source_native.h>
```

### Defining Global Variables

<!-- @[content_embed_server_global_variable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
static ContentEmbed_ExtensionInstanceHandle g_instance = nullptr;
```

### Registering Extension Callback Functions

When the OE Extension of an OE server application is started by the system to respond to an OE client request, the [OH_AbilityRuntime_OnNativeExtensionCreate](../reference/apis-ability-kit/capi-extension-ability-h.md#oh_abilityruntime_onnativeextensioncreate) function is executed first. You need to register OE Extension callbacks in this function to respond to client requests.

<!-- @[content_embed_server_register_extension_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
extern "C" void OH_AbilityRuntime_OnNativeExtensionCreate(AbilityRuntime_ExtensionInstance *instance,
                                                          const char *abilityName)
{
    if (instance == nullptr) {
        OH_LOG_ERROR(LOG_APP, "instance is null");
        return;
    }

    ContentEmbed_ExtensionInstanceHandle ceExtensionInstance;
    // Obtain the OE Extension instance.
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Extension_GetExtensionInstance(instance, &ceExtensionInstance);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_GetExtensionInstance failed, errCode: %{public}d.", ret);
        return;
    }
    // Assign the value to the global variable.
    g_instance = ceExtensionInstance;
    // Register the OE Extension creation callback.
    ret = OH_ContentEmbed_Extension_RegisterOnCreateFunc(ceExtensionInstance, NativeOnCreate);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnCreateFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // Register the OE Extension destruction callback.
    ret = OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ceExtensionInstance, NativeOnDestroy);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnDestroyFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // Register the server OE object attach callback.
    ret = OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ceExtensionInstance, RegisterOnObjectAttachFunc);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // Register the server OE object detach callback.
    ret = OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ceExtensionInstance, RegisterOnObjectDetachFunc);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc failed, errCode: %{public}d.", ret);
        return;
    }
}
```

### Implementing Lifecycle Callbacks for Creation and Destruction

<!-- @[content_embed_server_on_create_destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
static void NativeOnCreate(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)
{
    OH_LOG_INFO(LOG_APP, "enter NativeOnCreate");
}

static void NativeOnDestroy(ContentEmbed_ExtensionInstanceHandle instance)
{
    OH_LOG_INFO(LOG_APP, "enter NativeOnDestroy");
}
```

### Implementing Callbacks for Server OE Object Attach and Detach Events

When an OE client calls [OH_ContentEmbed_Proxy_StartWork](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork) to attach a client OE object to a server OE object, the system triggers the `RegisterOnObjectAttachFunc` callback of the OE server. In this callback, the OE server must call the registration functions of the server OE object to respond to OE client requests.

When an OE client calls [OH_ContentEmbed_Proxy_StopWork](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork) to detach the client OE object from the server OE object, the system triggers the `RegisterOnObjectDetachFunc` callback of the OE server. After this callback, the server OE object becomes invalid.

<!-- @[content_embed_server_on_object_attach_detach](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
static void RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
{
    // ...
    ContentEmbed_ErrorCode ret = CE_ERR_OK;
    // This callback is executed when the OE document is created based on a file.
    ret = OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(object, NativeOnWriteToDataStream);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP,
            "OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // Obtain the capabilities of the current OE Extension.
    ret = OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(object, NativeOnGetCapability);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP,
            "OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // Trigger the editing operation for the OE document.
    ret = OH_ContentEmbed_Extension_RegisterOnDoEditFunc(object, NativeOnDoEdit);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnDoEditFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // Request the OE document snapshot.
    ret = OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(object, NativeOnGetSnapshot);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // Query the current editing status of the OE document.
    ret = OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(object, NativeOnGetEditStatusFunc);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP,
            "OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc failed, errCode: %{public}d.", ret);
        return;
    }
}

static void RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
{
    OH_LOG_INFO(LOG_APP, "enter RegisterOnObjectDetachFunc");
    // ...
}
```

### Implementing OE Document Snapshot Retrieval

When an OE client embeds an OE object by creating a new object type or using an existing file, the OE object can be displayed as a document snapshot in the OE client UI. After the OE Extension starts, the OE client obtains the document snapshot by calling [OH_ContentEmbed_Proxy_GetSnapshot](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot), which triggers the `NativeOnGetSnapshot` callback of the OE server. In this callback, the OE server application must call [OH_ContentEmbed_Extension_SetSnapshot](../reference/apis-content-embed-kit/capi-content-embed-extension-h.md#oh_contentembed_extension_setsnapshot) to set the OE document snapshot.

<!-- @[content_embed_server_on_get_snapshot](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
static void NativeOnGetSnapshot(ContentEmbed_ObjectHandle object)
{
    // ...
    std::string objectKey = std::to_string(reinterpret_cast<uintptr_t>(object));
    std::string path = "/data/storage/el2/base/haps/entry/temp/web_snapshot_" + objectKey + ".png";
    // Check whether a thumbnail generated by the UI exists.
    FILE *srcFile = fopen(path.c_str(), "rb");
    if (!srcFile) {
        OH_LOG_ERROR(LOG_APP, "Open file failed");
        return;
    }
    int fd = fileno(srcFile);
    // Create an ImageSource instance.
    OH_ImageSourceNative *source = nullptr;
    Image_ErrorCode errCode = OH_ImageSourceNative_CreateFromFd(fd, &source);
    if (errCode != IMAGE_SUCCESS) {
        OH_LOG_ERROR(LOG_APP, "OH_ImageSourceNative_CreateFromFd failed, errCode: %{public}d.", errCode);
        if (fclose(srcFile) != 0) {
            OH_LOG_ERROR(LOG_APP, "NativeOnGetSnapshot fclose failed after CreateFromFd.");
        }
        return;
    }
    // Create a PixelMap object based on image decoding parameters.
    OH_DecodingOptions *ops = nullptr;
    OH_DecodingOptions_Create(&ops);
    // When AUTO is set, decoding is performed based on the image resource format. If the image resource is an HDR resource, it is decoded into an HDR pixel map.
    OH_DecodingOptions_SetDesiredDynamicRange(ops, IMAGE_DYNAMIC_RANGE_AUTO);
    OH_PixelmapNative *resPixMap = nullptr;
    // The ops parameter can be nullptr. If no decoding parameters need to be set, you do not need to create it.
    errCode = OH_ImageSourceNative_CreatePixelmap(source, ops, &resPixMap);
    OH_DecodingOptions_Release(ops);
    if (errCode != IMAGE_SUCCESS) {
        OH_LOG_ERROR(LOG_APP, "OH_ImageSourceNative_CreatePixelmap failed, errCode: %{public}d.", errCode);
        OH_ImageSourceNative_Release(source);
        if (fclose(srcFile) != 0) {
            OH_LOG_ERROR(LOG_APP, "NativeOnGetSnapshot fclose failed after CreatePixelmap.");
        }
        return;
    }
    // Set the snapshot.
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Extension_SetSnapshot(object, resPixMap);
    // Release the ImageSource instance.
    OH_ImageSourceNative_Release(source);
    OH_PixelmapNative_Release(resPixMap);
    if (fclose(srcFile) != 0) {
        OH_LOG_ERROR(LOG_APP, "NativeOnGetSnapshot fclose failed.");
    }
}
```

### Implementing OE Document Editing

After the OE Extension starts, the OE client notifies the OE server to edit the OE document by calling [OH_ContentEmbed_Proxy_DoEdit](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit), which triggers the `NativeOnDoEdit` callback of the OE server. In this callback, the OE server application must call [OH_ContentEmbed_Extension_ContextStartSelfUIAbility](../reference/apis-content-embed-kit/capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability) or [OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](../reference/apis-content-embed-kit/capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions) to start the UIAbility of the OE server application for document editing.

<!-- @[content_embed_server_on_do_edit](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
constexpr const char* TEMP_CACHE_PATH_PREFIX = "/data/storage/el2/base/cache/temp_";
constexpr const char* DOC_STREAM_NAME = "aaa";
constexpr uint32_t BUNDLE_NAME_BUFFER_SIZE = 100;
static void SetTempWantUri(AbilityBase_Want *want, const std::string &objectKey)
{
    // Set the file path.
    std::string tempPath = std::string(TEMP_CACHE_PATH_PREFIX) + objectKey + ".aaa";
    char *tempFileUri = nullptr;
    OH_FileUri_GetUriFromPath(tempPath.c_str(), tempPath.size(), &tempFileUri);
    if (tempFileUri != nullptr) {
        OH_AbilityBase_SetWantUri(want, tempFileUri);
        free(tempFileUri);
    } else {
        OH_LOG_ERROR(LOG_APP, "SetTempWantUri GetUriFromPath returned null: %{public}s", tempPath.c_str());
    }
}

static AbilityBase_Want* PrepareDoEditWant(ContentEmbed_Document* ceDocument, const std::string& objectKey,
                                           char* bundleNameBuffer, uint32_t bundleNameBufferSize)
{
    // ...
    int32_t writeLen = 0;
    AbilityRuntime_ErrorCode abilityCode =
        OH_AbilityRuntime_ApplicationContextGetBundleName(bundleNameBuffer, bundleNameBufferSize, &writeLen);
    if (abilityCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        OH_LOG_ERROR(LOG_APP, "OnCreate get bundleName failed: %{public}d", abilityCode);
        return nullptr;
    }
    const char* moduleName = "entry";
    const char* abilityName = "EntryAbility";
    AbilityBase_Element element = {
        .bundleName = bundleNameBuffer,
        .moduleName = const_cast<char*>(moduleName),
        .abilityName = const_cast<char*>(abilityName),
    };
    AbilityBase_Want* want = OH_AbilityBase_CreateWant(element);
    if (want == nullptr) {
        OH_LOG_ERROR(LOG_APP, "NativeOnDoEdit CreateWant failed");
        return nullptr;
    }
    // ...
    return want;
}

static bool WriteEmbeddedDocToTemp(ContentEmbed_Stream* childStream, AbilityBase_Want* want,
                                   const std::string& objectKey)
{
    size_t bufferSize = 0;
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Stream_GetSize(childStream, &bufferSize);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Stream_GetSize failed, errCode: %{public}d.", ret);
        return false;
    }
    ret = OH_ContentEmbed_Stream_Seek(childStream, 0);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Stream_Seek failed, errCode: %{public}d.", ret);
        return false;
    }
    unsigned char* buffer = nullptr;
    size_t num = 0;
    ret = OH_ContentEmbed_Stream_Read(childStream, &buffer, bufferSize, &num);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Stream_Read failed, errCode: %{public}d.", ret);
        return false;
    }
    std::string tempPath = std::string(TEMP_CACHE_PATH_PREFIX) + objectKey + ".aaa";
    std::ofstream outputFile(tempPath, std::ios::out | std::ios::binary);
    if (outputFile.is_open()) {
        outputFile.write(reinterpret_cast<const char*>(buffer), bufferSize);
        outputFile.close();
        OH_LOG_INFO(LOG_APP, "Write data successful.");
    } else {
        OH_LOG_ERROR(LOG_APP, "Cannot open output file.");
    }
    SetTempWantUri(want, objectKey);
    return true;
}

// ...

static bool AcquireDoEditResources(ContentEmbed_ObjectHandle object, const std::string& objectKey,
                                   ContentEmbed_Document** doc, ContentEmbed_ExtensionContextHandle* ctx,
                                   AbilityBase_Want** want, char* bundleNameBuffer,
                                   uint32_t bundleNameBufferSize)
{
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Extension_GetContentEmbedDocument(object, doc);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_GetContentEmbedDocument failed, errCode: %{public}d.", ret);
        return false;
    }
    ret = OH_ContentEmbed_Extension_GetContentEmbedContext(g_instance, ctx);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_GetContentEmbedContext failed, errCode: %{public}d.", ret);
        return false;
    }
    *want = PrepareDoEditWant(*doc, objectKey, bundleNameBuffer, bundleNameBufferSize);
    return *want != nullptr;
}

static void ReleaseDoEditResources(AbilityBase_Want* want, ContentEmbed_Stream* childStream,
                                   ContentEmbed_Storage* rootStorage)
{
    if (want != nullptr) {
        OH_AbilityBase_DestroyWant(want);
    }
    if (childStream != nullptr) {
        OH_ContentEmbed_DestroyStream(childStream);
    }
    if (rootStorage != nullptr) {
        OH_ContentEmbed_DestroyStorage(rootStorage);
    }
}

static void NativeOnDoEdit(ContentEmbed_ObjectHandle object)
{
    // ...
    std::string objectKey = std::to_string(reinterpret_cast<uintptr_t>(object));
    char bundleNameBuffer[BUNDLE_NAME_BUFFER_SIZE] = {};
    ContentEmbed_Document* ceDocument = nullptr;
    ContentEmbed_ExtensionContextHandle context = nullptr;
    AbilityBase_Want* want = nullptr;
    // Obtain ceDocument and context, and set want.
    if (!AcquireDoEditResources(object, objectKey, &ceDocument, &context, &want,
                                 bundleNameBuffer, BUNDLE_NAME_BUFFER_SIZE)) {
        return;
    }
    ContentEmbed_ErrorCode ret = CE_ERR_OK;
    ContentEmbed_Storage* rootStorage = nullptr;
    ContentEmbed_Stream* childStream = nullptr;
    ret = OH_ContentEmbed_Document_GetRootStorage(ceDocument, &rootStorage);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Document_GetRootStorage failed, errCode: %{public}d.", ret);
        ReleaseDoEditResources(want, childStream, rootStorage);
        return;
    }
    ret = OH_ContentEmbed_Storage_GetStream(rootStorage, DOC_STREAM_NAME, &childStream);
    if (ret == CE_ERR_OK) {
        if (!WriteEmbeddedDocToTemp(childStream, want, objectKey)) {
            ReleaseDoEditResources(want, childStream, rootStorage);
            return;
        }
    } else {
        // ...
    }
    // Start the UIAbility to edit the document.
    ret = OH_ContentEmbed_Extension_ContextStartSelfUIAbility(context, want);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_ContextStartSelfUIAbility failed, errCode: %{public}d.", ret);
        ReleaseDoEditResources(want, childStream, rootStorage);
        return;
    }
    ReleaseDoEditResources(want, childStream, rootStorage);
    // ...
}
```

### Implementing OE Extension Capability Query

After the OE Extension starts, the OE client obtains the capabilities of the OE server by calling [OH_ContentEmbed_Proxy_GetCapability](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability), which triggers the `NativeOnGetCapability` callback of the OE server. In this callback, the OE server application assigns a value to the `bitmask` attribute to notify the OE client of its capabilities.

<!-- @[content_embed_server_on_get_capability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
static void NativeOnGetCapability(ContentEmbed_ObjectHandle object, uint32_t *bitmask)
{
    if (!bitmask) {
        OH_LOG_ERROR(LOG_APP, "bitmask is null");
        return;
    }
    *bitmask = CE_CAPABILITY_SUPPORT_SNAPSHOT | CE_CAPABILITY_SUPPORT_DO_EDIT;
}
```

### Implementing OE Document Editing Status Query

After the OE Extension starts, the OE client obtains the editing status of the OE document by calling [OH_ContentEmbed_Proxy_GetEditStatus](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_geteditstatus), which triggers the `NativeOnGetEditStatusFunc` callback of the OE server. In this callback, the OE server application notifies the OE client of the document editing status.

<!-- @[content_embed_server_on_get_edit_status](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->

``` C++
static void NativeOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)
{
    if (!isEditing || !isModified) {
        OH_LOG_ERROR(LOG_APP, "param is null");
        return;
    }
    // If the document is not being edited.
    *isEditing = false;
    *isModified = false;
    // ...
}
```

### Implementing OE Document Stream Writing

When an OE client embeds an OE object based on an existing file and the OE Extension starts, the `NativeOnWriteToDataStream` callback of the OE server is triggered. In this callback, the OE server must write data to the OE document.

<!-- @[content_embed_server_on_write_to_data_stream](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
// Obtain the stream named aaa.
constexpr const char* DOCUMENT_STREAM_NAME = "aaa";
static ContentEmbed_ErrorCode OpenOrCreateChildStream(ContentEmbed_Document *document,
                                                      ContentEmbed_Stream **stream)
{
    ContentEmbed_Storage *rootStorage = nullptr;
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Document_GetRootStorage(document, &rootStorage);
    if (ret != CE_ERR_OK || rootStorage == nullptr) {
        OH_LOG_ERROR(LOG_APP, "OpenOrCreateChildStream GetRootStorage failed: %{public}d", ret);
        return ret;
    }
    ret = OH_ContentEmbed_Storage_GetStream(rootStorage, DOCUMENT_STREAM_NAME, stream);
    if (ret != CE_ERR_OK) {
        ret = OH_ContentEmbed_Storage_CreateStream(rootStorage, DOCUMENT_STREAM_NAME, stream);
    }
    OH_ContentEmbed_DestroyStorage(rootStorage);
    if (ret != CE_ERR_OK || *stream == nullptr) {
        OH_LOG_ERROR(LOG_APP, "OpenOrCreateChildStream open/create stream failed: %{public}d", ret);
        if (*stream != nullptr) {
            OH_ContentEmbed_DestroyStream(*stream);
            *stream = nullptr;
        }
        return ret;
    }
    return CE_ERR_OK;
}

static ContentEmbed_ErrorCode WriteFileToStream(ContentEmbed_Stream *stream, const std::string &filePath)
{
    std::ifstream oriFile(filePath, std::ios::binary);
    if (!oriFile) {
        OH_LOG_ERROR(LOG_APP, "WriteFileToStream open file failed: %{public}s", filePath.c_str());
        return CE_ERR_FILE_OPERATION_FAILED;
    }
    oriFile.seekg(0, std::ios::end);
    size_t oriFileSize = static_cast<size_t>(oriFile.tellg());
    oriFile.seekg(0, std::ios::beg);
    std::vector<unsigned char> buffer(oriFileSize);
    oriFile.read(reinterpret_cast<char *>(buffer.data()), static_cast<std::streamsize>(oriFileSize));
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Stream_Seek(stream, 0);
    OH_LOG_INFO(LOG_APP, "WriteFileToStream Seek ret: %{public}d", ret);
    size_t num = 0;
    ret = OH_ContentEmbed_Stream_Write(stream, buffer.data(), oriFileSize, &num);
    OH_LOG_INFO(LOG_APP, "WriteFileToStream Write ret: %{public}d, num: %{public}zu", ret, num);
    return ret;
}

static void NativeOnWriteToDataStream(ContentEmbed_ObjectHandle object)
{
    ContentEmbed_ErrorCode ret = CE_ERR_OK;
    ContentEmbed_Document* ceDocument = nullptr;
    // Obtain the OE document.
    ret = OH_ContentEmbed_Extension_GetContentEmbedDocument(object, &ceDocument);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_GetContentEmbedDocument ret: %{public}d", ret);
        return;
    }
    ContentEmbed_Stream* destStream = nullptr;
    ret = OpenOrCreateChildStream(ceDocument, &destStream);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OpenOrCreateChildStream failed: %{public}d", ret);
        return;
    }
    // Obtain the local file path.
    char nativeFilePath[MAX_PATH_LENGTH] = {0};
    ret = OH_ContentEmbed_Document_GetNativeFilePath(ceDocument, nativeFilePath);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Document_GetNativeFilePath ret: %{public}d", ret);
        OH_ContentEmbed_DestroyStream(destStream);
        return;
    }
    // Read the local file and write the data to the OE document.
    ret = WriteFileToStream(destStream, nativeFilePath);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "WriteFileToStream ret: %{public}d", ret);
        OH_ContentEmbed_DestroyStream(destStream);
        return;
    }
    // Flush the OE document.
    ret = OH_ContentEmbed_Document_Flush(ceDocument);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Document_Flush ret: %{public}d", ret);
        OH_ContentEmbed_DestroyStream(destStream);
        return;
    }
    OH_LOG_INFO(LOG_APP, "enter NativeOnWriteToDataStream %{public}p", object);
    OH_ContentEmbed_DestroyStream(destStream);
}
```
