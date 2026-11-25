# 服务端应用开发

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## 场景介绍

[OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md)内容嵌入模块提供对象编辑框架与技术，支持应用间文档嵌入与协同编辑。

OE服务端应用使用OE Extension框架[content_embed_extension.h](../reference/apis-content-embed-kit/capi-content-embed-extension-h.md)提供的接口，向客户端应用提供特定格式文档的嵌入与编辑能力。

## 约束限制
在使用接口前，需先确认设备具备SystemCapability.ContentEmbed.ObjectEditor系统能力，判断方式请参阅[canIUse()](../reference/common/syscap-ndk-8h.md#caniuse)接口查询指定的系统能力是否被支持。并申请ohos.permission.REGISTER_OBJECTEDITOR_EXTENSION权限，配置方式请参阅[声明权限](../security/AccessToken/declare-permissions.md)。

## 接口说明

常用接口如下表所示。更多API说明请参考[OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md)。

**表1** 服务端主要接口

| 接口名称 | 功能描述 |
| ------- | ---- |
| OH_ContentEmbed_Extension_GetExtensionInstance | 从ExtensionAbility基类实例中获取对应的[OE Extension](content-embed-kit-terminology.md#oe-extension)实例。|
| OH_ContentEmbed_Extension_GetContentEmbedContext | 从OE Extension实例中获取其对应的OE Extension上下文对象。|
| OH_ContentEmbed_Extension_GetContext | 从OE Extension上下文中获取AbilityRuntime上下文。|
| OH_ContentEmbed_Extension_RegisterOnCreateFunc | 注册OE Extension实例创建时的生命周期函数。|
| OH_ContentEmbed_Extension_RegisterOnDestroyFunc | 注册OE Extension实例销毁时的生命周期函数。|
| OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc | 注册[客户端OE对象](content-embed-kit-terminology.md#客户端oe对象)连接时的回调函数。|
| OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc | 注册客户端OE对象断开连接时的回调函数。|
| OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc | 注册[服务端OE对象](content-embed-kit-terminology.md#服务端oe对象)写入[OE文档](content-embed-kit-terminology.md#oe文档)数据流时的回调函数。|
| OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc | 注册客户端OE对象请求获取OE文档快照时的回调函数。|
| OH_ContentEmbed_Extension_RegisterOnDoEditFunc | 注册客户端OE对象请求编辑OE文档时的回调函数。|
| OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc | 注册客户端OE对象请求OE文档编辑状态时的回调函数。|
| OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc | 注册客户端OE对象查询OE Extension实例支持能力时的回调函数。|
| OH_ContentEmbed_Extension_GetContentEmbedDocument | 获取服务端OE对象关联的OE文档实例。|
| OH_ContentEmbed_Extension_CallbackToOnUpdate | 触发客户端OE对象注册的OE文档更新回调函数。|
| OH_ContentEmbed_Extension_CallbackToOnError | 触发客户端OE对象注册的OE文档错误回调函数。|
| OH_ContentEmbed_Extension_CallbackToOnEditingFinished | 触发客户端OE对象注册的OE文档编辑完成回调函数。|
| OH_ContentEmbed_Extension_CallbackToOnExtensionStopped | 触发OE Extension关联的所有客户端OE对象注册的OE Extension停止时的回调函数。|
| OH_ContentEmbed_Extension_SetSnapshot | 设置客户端OE对象关联的OE文档快照图像。|
| OH_ContentEmbed_Extension_ContextStartSelfUIAbility | 通过OE Extension上下文启动自身的UIAbility。|

## 开发步骤

以下演示使用Native API开发OE服务端应用的完整流程，演示了OE服务端注册Extension组件回调，响应客户端请求，返回OE文档快照和启动UIAbility编辑OE文档。

### OE服务端配置OE ExtensionAbility

从API version 24版本开始，在`module.json5`文件的`extensionAbilities`标签中配置OE ExtensionAbility，示例如下：

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

配置说明：
- name：Extension组件的名称。
- srcEntry：Extension组件的入口库文件路径。
- type：必须设置为"contentEmbed"。
- exported：必须设置为true，表示对外暴露。
- [metadata](../quick-start/module-configuration-file.md#metadata标签)：元数据信息"metadata"新增一个"name"为"content_embed_config"的数据项，"resource"为OE Extension配置文件的资源索引。

开发者需要新增一个二级配置json文件，用于配置OE Extension信息。例如将"resource"配置成"$profile:content_embed_config"，表示指向`resources/base/profile/content_embed_config.json`配置文件。json文件示例如下：

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

配置说明：
- oeid：OE文档的系统可识别标识符，用于定位支持该OE文档的OE服务端应用。
  - 如果OE服务端应用在其它操作系统上也有相同功能，建议复用已在其它系统中使用的ID；
  - 如果OE服务端应用该功能仅在OpenHarmony系统上提供，则建议使用系统自带的“终端”工具，通过`uuidgen`命令生成新的ID。
- file_exts：支持的文件扩展名，如".doc"、".docx"等，如果支持多个文件后缀，使用"|"进行隔开。
- icon：OE文档查询显示图标，取值为图标资源文件的索引。
- name：OE文档查询显示名称，要求采用该名称的资源索引，以支持多语言。
- description：OE文档查询显示描述，要求采用该名称的资源索引，以支持多语言。

### 添加动态链接库
在Native工程的src/main/cpp/CMakeLists.txt，添加如下链接库：

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

### 导入头文件

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

### 定义全局变量

<!-- @[content_embed_server_global_variable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
static ContentEmbed_ExtensionInstanceHandle g_instance = nullptr;
```

### 注册Extension回调函数

当OE服务端应用的OE Extension被系统启动以响应OE客户端请求时，首先执行[OH_AbilityRuntime_OnNativeExtensionCreate](../reference/apis-ability-kit/capi-extension-ability-h.md#oh_abilityruntime_onnativeextensioncreate)函数，需在该函数中注册OE Extension回调，以响应客户端请求。

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
    // 获取OE Extension实例
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Extension_GetExtensionInstance(instance, &ceExtensionInstance);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_GetExtensionInstance failed, errCode: %{public}d.", ret);
        return;
    }
    // 给全局变量赋值
    g_instance = ceExtensionInstance;
    // 注册OE Extension创建函数回调
    ret = OH_ContentEmbed_Extension_RegisterOnCreateFunc(ceExtensionInstance, NativeOnCreate);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnCreateFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // 注册OE Extension销毁函数回调
    ret = OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ceExtensionInstance, NativeOnDestroy);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnDestroyFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // 注册服务端OE对象绑定回调
    ret = OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ceExtensionInstance, RegisterOnObjectAttachFunc);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // 注册服务端OE对象解绑回调
    ret = OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ceExtensionInstance, RegisterOnObjectDetachFunc);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc failed, errCode: %{public}d.", ret);
        return;
    }
}
```

### 实现创建和销毁生命周期回调函数

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

### 实现服务端OE对象绑定和解绑的回调函数

当OE客户端调用[OH_ContentEmbed_Proxy_StartWork](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_startwork)函数将客户端OE对象与服务端OE对象绑定时，系统会触发OE服务端的`RegisterOnObjectAttachFunc`回调。在此回调中，OE服务端需调用服务端OE对象的注册函数以响应OE客户端的请求。

当OE客户端调用[OH_ContentEmbed_Proxy_StopWork](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_stopwork)函数将客户端OE对象与服务端OE对象解除绑定时，系统会触发OE服务端的`RegisterOnObjectDetachFunc`回调，在该回调后服务端OE对象将失效。

<!-- @[content_embed_server_on_object_attach_detach](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
static void RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
{
    // ...
    ContentEmbed_ErrorCode ret = CE_ERR_OK;
    // 当OE文档是通过文件创建的时候执行该回调函数
    ret = OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(object, NativeOnWriteToDataStream);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP,
            "OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // 获取当前OE Extension的能力
    ret = OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(object, NativeOnGetCapability);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP,
            "OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // OE文档触发编辑操作
    ret = OH_ContentEmbed_Extension_RegisterOnDoEditFunc(object, NativeOnDoEdit);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnDoEditFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // OE文档请求获取快照
    ret = OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(object, NativeOnGetSnapshot);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc failed, errCode: %{public}d.", ret);
        return;
    }
    // OE文档查询当前编辑状态
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

### 实现获取OE文档快照

当OE客户端通过新建对象类型或已存在文件来嵌入OE对象时，OE对象在OE客户端界面中可能呈现为文档快照（Snapshot），当OE Extension被启动后，OE客户端会通过[OH_ContentEmbed_Proxy_GetSnapshot](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot)获取文档快照，此时会触发OE服务端的`NativeOnGetSnapshot`回调，在该回调中OE服务端应用需调用[OH_ContentEmbed_Extension_SetSnapshot](../reference/apis-content-embed-kit/capi-content-embed-extension-h.md#oh_contentembed_extension_setsnapshot)设置OE文档快照。

<!-- @[content_embed_server_on_get_snapshot](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
static void NativeOnGetSnapshot(ContentEmbed_ObjectHandle object)
{
    // ...
    std::string objectKey = std::to_string(reinterpret_cast<uintptr_t>(object));
    std::string path = "/data/storage/el2/base/haps/entry/temp/web_snapshot_" + objectKey + ".png";
    // 判断当前是否有UI生成的缩略图
    FILE *srcFile = fopen(path.c_str(), "rb");
    if (!srcFile) {
        OH_LOG_ERROR(LOG_APP, "Open file failed");
        return;
    }
    int fd = fileno(srcFile);
    // 创建ImageSource实例
    OH_ImageSourceNative *source = nullptr;
    Image_ErrorCode errCode = OH_ImageSourceNative_CreateFromFd(fd, &source);
    if (errCode != IMAGE_SUCCESS) {
        OH_LOG_ERROR(LOG_APP, "OH_ImageSourceNative_CreateFromFd failed, errCode: %{public}d.", errCode);
        if (fclose(srcFile) != 0) {
            OH_LOG_ERROR(LOG_APP, "NativeOnGetSnapshot fclose failed after CreateFromFd.");
        }
        return;
    }
    // 通过图片解码参数创建PixelMap对象
    OH_DecodingOptions *ops = nullptr;
    OH_DecodingOptions_Create(&ops);
    // 设置为AUTO会根据图片资源格式解码，如果图片资源为HDR资源则会解码为HDR的pixelmap
    OH_DecodingOptions_SetDesiredDynamicRange(ops, IMAGE_DYNAMIC_RANGE_AUTO);
    OH_PixelmapNative *resPixMap = nullptr;
    // ops参数支持传入nullptr, 当不需要设置解码参数时，不用创建
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
    // 设置快照
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Extension_SetSnapshot(object, resPixMap);
    // 释放ImageSource实例
    OH_ImageSourceNative_Release(source);
    OH_PixelmapNative_Release(resPixMap);
    if (fclose(srcFile) != 0) {
        OH_LOG_ERROR(LOG_APP, "NativeOnGetSnapshot fclose failed.");
    }
}
```

### 实现编辑OE文档

当OE Extension被启动后，OE客户端会通过[OH_ContentEmbed_Proxy_DoEdit](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_doedit)通知OE服务端编辑OE文档，此时会触发OE服务端的`NativeOnDoEdit`回调，在该回调中OE服务端应用需调用[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](../reference/apis-content-embed-kit/capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiability)或[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](../reference/apis-content-embed-kit/capi-content-embed-extension-h.md#oh_contentembed_extension_contextstartselfuiabilitywithstartoptions)启动OE服务端应用的UIAbility编辑文档。

<!-- @[content_embed_server_on_do_edit](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
constexpr const char* TEMP_CACHE_PATH_PREFIX = "/data/storage/el2/base/cache/temp_";
constexpr const char* DOC_STREAM_NAME = "aaa";
constexpr uint32_t BUNDLE_NAME_BUFFER_SIZE = 100;
static void SetTempWantUri(AbilityBase_Want *want, const std::string &objectKey)
{
    // 设置文件路径
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
    // 获取ceDocument、context、设置want
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
    // 启动UIAbility 对文档进行编辑操作
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

### 实现获取OE Extension能力

当OE Extension被启动后，OE客户端会通过[OH_ContentEmbed_Proxy_GetCapability](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability)获取OE服务端具备的能力，此时会触发OE服务端的`NativeOnGetCapability`回调，在该回调中OE服务端应用通过给`bitmask`属性赋值，通知OE客户端自身具备的能力。

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

### 实现查询OE文档编辑状态

当OE Extension被启动后，OE客户端会通过[OH_ContentEmbed_Proxy_GetEditStatus](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_geteditstatus)获取OE文档编辑状态，此时会触发OE服务端的`NativeOnGetEditStatusFunc`回调，在该回调中OE服务端应用通知OE客户端文档编辑状态。

<!-- @[content_embed_server_on_get_edit_status](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->

``` C++
static void NativeOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)
{
    if (!isEditing || !isModified) {
        OH_LOG_ERROR(LOG_APP, "param is null");
        return;
    }
    // 若文档未处于编辑态
    *isEditing = false;
    *isModified = false;
    // ...
}
```

### 实现OE文档写流操作

当OE客户端通过已存在文件来嵌入OE对象且OE Extension被启动后，此时会触发OE服务端的`NativeOnWriteToDataStream`回调，在该回调中OE服务端需往OE文档中写入数据。

<!-- @[content_embed_server_on_write_to_data_stream](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ContentEmbedKit/OEServerDemo/entry/src/main/cpp/ole_ext_ability.cpp) -->  

``` C++
// 获取名字为aaa的流
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
    // 获取OE文档
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
    // 获取本地文件路径
    char nativeFilePath[MAX_PATH_LENGTH] = {0};
    ret = OH_ContentEmbed_Document_GetNativeFilePath(ceDocument, nativeFilePath);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_ContentEmbed_Document_GetNativeFilePath ret: %{public}d", ret);
        OH_ContentEmbed_DestroyStream(destStream);
        return;
    }
    // 读取本地文件，往OE文档写数据
    ret = WriteFileToStream(destStream, nativeFilePath);
    if (ret != CE_ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "WriteFileToStream ret: %{public}d", ret);
        OH_ContentEmbed_DestroyStream(destStream);
        return;
    }
    // 刷新OE文档
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