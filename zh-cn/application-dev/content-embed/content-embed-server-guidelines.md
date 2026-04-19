# 服务端应用开发
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice-->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @zhaotianyu-->
<!--Adviser: @jinqiuheng-->

## 场景介绍

[OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md)内容嵌入模块提供对象编辑框架与技术，支持应用间文档嵌入与协同编辑。
OE服务端应用利用[OE Extension框架](../reference/apis-content-embed-kit/capi-content-embed-extension-h.md)提供的接口，向客户端应用提供特定格式文档的嵌入与编辑能力。

## 约束限制
- 使用此接口，需确认设备具有以下系统能力：SystemCapability.ContentEmbed.ObjectEditor。
- 申请权限：开发者需要申请ohos.permission.REGISTER_OBJECTEDITOR_EXTENSION权限，配置方式请参阅[声明权限](../security/AccessToken/declare-permissions.md)。

## 接口说明

常用接口如下表所示。更多API说明请参考[OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md)。

**表1** 服务端主要接口

| 接口名称 | 功能描述 |
| ------- | ---- |
| OH_ContentEmbed_Extension_GetExtensionInstance | 从ExtensionAbility基类实例中获取对应的[OE Extension](content-embed-kit-terminology.md#OE-Extension)实例。|
| OH_ContentEmbed_Extension_GetContentEmbedContext | 从OE Extension实例中获取其对应的OE Extension上下文对象。|
| OH_ContentEmbed_Extension_GetContext | 从OE Extension上下文中获取AbilityRuntime上下文。|
| OH_ContentEmbed_Extension_RegisterOnCreateFunc | 注册OE Extension实例创建时的生命周期函数。|
| OH_ContentEmbed_Extension_RegisterOnDestroyFunc | 注册OE Extension实例销毁时的生命周期函数。|
| OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc | 注册[客户端OE对象](content-embed-kit-terminology.md#客户端OE对象)连接时的回调函数。|
| OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc | 取消注册客户端OE对象连接时的回调函数。|
| OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc | 注册[服务端OE对象](content-embed-kit-terminology.md#服务端OE对象)写入[OE文档](content-embed-kit-terminology.md#OE文档)数据流时的回调函数。|
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

OE服务端开发的步骤包括：
1. 配置OE ExtensionAbility：从API version 24版本开始，开发者需要在`module.json5`文件的`extensionAbilities`标签中配置OE ExtensionAbility，需要将`type`属性配置成`contentEmbed`，并且在`metadata`中增加`content_embed_config`配置文件。其中，`type`属性作为OE ExtensionAbility的唯一标识，`metadata`中的配置文件用于配置OE Extension信息。
2. 创建配置文件：开发者需要新增一个二级配置json文件，用于启用OE配置。该json文件需要开发者自行创建，并放置在工程目录下。推荐的文件名及路径为`resources/base/profile/content_embed_config.json` 。
3. 实现入口函数：实现OH_AbilityRuntime_OnNativeExtensionCreate函数。
4. 注册回调：注册ExtensionAbility回调，以响应客户端请求。
5. 编辑OE文档：在OnDoEdit回调中拉起UIAbility编辑文档，并返回OE文档快照。

以下演示使用Native API开发OE服务端应用的完整流程，演示了OE服务端注册Extension组件回调，响应客户端请求，返回OE文档快照和拉起UIAbility编辑OE文档。

### OE服务端配置OE ExtensionAbility

在`module.json5`文件的`extensionAbilities`标签中配置OE ExtensionAbility，示例如下：

```json
"extensionAbilities": [
    {
        "name": "OEExtAbility",
        "srcEntry": "./libentry.so",
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
- metadata：元数据信息"metadata"新增一个"name"为"content_embed_config"的条目。

在元数据资源配置文件中，开发者需要新增一个二级配置json文件，用于配置OE Extension信息。推荐的文件名及路径为`resources/base/profile/content_embed_config.json` 。示例如下：

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

CMakeLists.txt中添加以下lib。

```text
# content embed
libcontent_embed_ndk.so
# hilog
libhilog_ndk.z.so
# ace
libace_napi.z.so
# piexlmap
libpixelmap.so
# ability
libability_runtime.so
# want
libability_base_want.so
# fileuri
libohfileuri.so
```

### 导入头文件

```cpp
#include <cstdint>
#include <fstream>

#include <AbilityKit/ability_base/want.h>
#include <AbilityKit/ability_runtime/application_context.h>
#include <content_embed/content_embed_document.h>
#include <content_embed/content_embed_extension.h>
#include <filemanagement/file_uri/oh_file_uri.h>
#include <multimedia/image_framework/image/image_source_native.h>
```

### 定义全局变量

```cpp
static ContentEmbed_ExtensionInstanceHandle g_instance = nullptr;
```

### OE服务端应用需实现入口函数，在该函数中注册Extension回调

当OE服务端应用的OE Extension被系统拉起以响应OE客户端请求时，首先执行`OH_AbilityRuntime_OnNativeExtensionCreate` 函数。

```cpp
extern "C" void OH_AbilityRuntime_OnNativeExtensionCreate(AbilityRuntime_ExtensionInstance *instance, const char *abilityName) {
    if (instance == nullptr) {
        OH_LOG_ERROR(LOG_APP, "instance is null");
        return;
    }

    ContentEmbed_ExtensionInstanceHandle ceExtensionInstance;
    // 获取OE Extension实例
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Extension_GetExtensionInstance(instance, &ceExtensionInstance);
    // 给全局变量赋值
    g_instance = ceExtensionInstance;
    // 注册OE Extension创建函数回调
    ret = OH_ContentEmbed_Extension_RegisterOnCreateFunc(ceExtensionInstance, NativeOnCreate);
    // 注册OE Extension销毁函数回调
    ret = OH_ContentEmbed_Extension_RegisterOnDestroyFunc(ceExtensionInstance, NativeOnDestroy);
    // 注册服务端OE对象绑定回调
    ret = OH_ContentEmbed_Extension_RegisterOnObjectAttachFunc(ceExtensionInstance, RegisterOnObjectAttachFunc);
    // 注册服务端OE对象解绑回调
    ret = OH_ContentEmbed_Extension_RegisterOnObjectDetachFunc(ceExtensionInstance, RegisterOnObjectDetachFunc);
}
```

### OE Extension创建和销毁生命周期回调

```cpp
static void NativeOnCreate(ContentEmbed_ExtensionInstanceHandle instance, AbilityBase_Want *want)
{
    OH_LOG_INFO(LOG_APP, "enter NativeOnCreate");
}

static void NativeOnDestroy(ContentEmbed_ExtensionInstanceHandle instance)
{
    OH_LOG_INFO(LOG_APP, "enter NativeOnDestroy");
}
```

### OE Extension实现服务端OE对象绑定和解绑回调

当OE客户端通过[OH_ContentEmbed_Proxy_StartWork](../reference/apis-content-embed-kit/capi-content-embed-proxy-h#OH_ContentEmbed_Proxy_StartWork)函数拉起OE Extension，并将客户端OE对象与服务端OE对象绑定时，会触发OE服务端的`RegisterOnObjectAttachFunc` 回调，在该回调中OE服务端需调用服务端OE对象的注册函数以响应OE客户端的请求。

当OE客户端通过[OH_ContentEmbed_Proxy_StopWork](../reference/apis-content-embed-kit/capi-content-embed-proxy-h#OH_ContentEmbed_Proxy_StopWork)函数将客户端OE对象与服务端OE对象解除绑定时，会触发OE服务端的`RegisterOnObjectDetachFunc` 回调，在该回调后服务端OE对象将失效。

```cpp

static void RegisterOnObjectAttachFunc(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
{
    ContentEmbed_ErrorCode ret = CE_ERR_OK;
    // 当OE文档是通过文件创建的时候执行该回调函数
    ret = OH_ContentEmbed_Extension_RegisterOnWriteToDataStreamFunc(object, NativeOnWriteToDataStream);
    // 获取当前OE Extension的能力
    ret = OH_ContentEmbed_Extension_RegisterOnGetCapabilityFunc(object, NativeOnGetCapability);
    // OE文档触发编辑操作
    ret = OH_ContentEmbed_Extension_RegisterOnDoEditFunc(object, NativeOnDoEdit);
    // OE文档请求获取快照
    ret = OH_ContentEmbed_Extension_RegisterOnGetSnapshotFunc(object, NativeOnGetSnapShot);
    // OE文档查询当前编辑状态
    ret = OH_ContentEmbed_Extension_RegisterOnGetEditStatusFunc(object, NativeOnGetEditStatusFunc);
}

static void RegisterOnObjectDetachFunc(ContentEmbed_ExtensionInstanceHandle instance, ContentEmbed_ObjectHandle object)
{
    OH_LOG_INFO(LOG_APP, "enter RegisterOnObjectDetachFunc");
}
```

### OE文档获取快照

当OE客户端通过新建对象类型或已存在文件来嵌入OE对象时，OE对象在OE客户端界面中可能呈现为文档快照（Snapshot），当OE Extension被拉起后，OE客户端会通过[OH_ContentEmbed_Proxy_GetSnapshot](../reference/apis-content-embed-kit/capi-content-embed-proxy-h#OH_ContentEmbed_Proxy_GetSnapshot)获取文档快照，此时会触发OE服务端的`NativeOnGetSnapShot`回调，在该回调中OE服务端应用需调用[OH_ContentEmbed_Extension_SetSnapshot](../reference/apis-content-embed-kit/capi-content-embed-extension-h#OH_ContentEmbed_Extension_SetSnapshot)设置OE文档快照。

```cpp
static void NativeOnGetSnapShot(ContentEmbed_ObjectHandle object)
{
    // 当前OE文档快照路径
    std::string path = "/data/storage/el2/base/haps/entry/temp/web_snapshot.png";
    // 判断当前是否有UI生成的缩略图
    FILE *srcFile = fopen(path.c_str(), "rb");
    if (!srcFile) {
        OH_LOG_ERROR(LOG_APP, "文件打开失败");
        return;
    }
    int fd = fileno(srcFile);
    // 创建ImageSource实例。
    OH_ImageSourceNative *source = nullptr;
    Image_ErrorCode errCode = OH_ImageSourceNative_CreateFromFd(fd, &source);
    if (errCode != IMAGE_SUCCESS) {
        OH_LOG_ERROR(LOG_APP, "ImageSourceNativeCTest sourceTest OH_ImageSourceNative_CreateFromUri failed, errCode: %{public}d.", errCode);
        return;
    }
    // 通过图片解码参数创建PixelMap对象。
    OH_DecodingOptions *ops = nullptr;
    OH_DecodingOptions_Create(&ops);
    // 设置为AUTO会根据图片资源格式解码，如果图片资源为HDR资源则会解码为HDR的pixelmap。
    OH_DecodingOptions_SetDesiredDynamicRange(ops, IMAGE_DYNAMIC_RANGE_AUTO);
    OH_PixelmapNative *resPixMap = nullptr;

    // ops参数支持传入nullptr, 当不需要设置解码参数时，不用创建。
    errCode = OH_ImageSourceNative_CreatePixelmap(source, ops, &resPixMap);
    OH_DecodingOptions_Release(ops);
    if (errCode != IMAGE_SUCCESS) {
        OH_LOG_ERROR(LOG_APP, "ImageSourceNativeCTest sourceTest OH_ImageSourceNative_CreatePixelmap failed, errCode: %{public}d.", errCode);
        return;
    }
    // 设置快照
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Extension_SetSnapshot(object, resPixMap);
    // 释放ImageSource实例。
    OH_ImageSourceNative_Release(source);
}
```

### OE文档编辑操作

当OE Extension被拉起后，OE客户端会通过[OH_ContentEmbed_Proxy_DoEdit](../reference/apis-content-embed-kit/capi-content-embed-proxy-h#OH_ContentEmbed_Proxy_DoEdit)通知OE服务端编辑OE文档，此时会触发OE服务端的`NativeOnDoEdit`回调，在该回调中OE服务端应用需调用[OH_ContentEmbed_Extension_ContextStartSelfUIAbility](../reference/apis-content-embed-kit/capi-content-embed-extension-h#OH_ContentEmbed_Extension_ContextStartSelfUIAbility)或[OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions](../reference/apis-content-embed-kit/capi-content-embed-extension-h#OH_ContentEmbed_Extension_ContextStartSelfUIAbilityWithStartOptions)启动OE服务端应用的UIAbility编辑文档。

```cpp
static void NativeOnDoEdit(ContentEmbed_ObjectHandle object)
{
    ContentEmbed_ErrorCode ret = CE_ERR_OK;
    ContentEmbed_Document* ceDocument;
    // 获取当前OE文档
    ret = OH_ContentEmbed_Extension_GetContentEmbedDocument(object, &ceDocument);
    // 获取当前上下文实例
    ContentEmbed_ExtensionContextHandle context;
    ret = OH_ContentEmbed_Extension_GetContentEmbedContext(g_instance, &context);
    // 需要拉起UIAbility的信息
    char* bundleName = "";
    char* moduleName = "entry";
    char* abilityName = "EntryAbility";
    // 创建Want对象
    AbilityBase_Element element = {
        .bundleName = bundleName,
        .moduleName = moduleName,
        .abilityName = abilityName,
    };
    AbilityBase_Want* want = OH_AbilityBase_CreateWant(element);
    // 获取OE文档的RootStorage
    ContentEmbed_Storage *rootStorage = nullptr;
    ret = OH_ContentEmbed_Document_GetRootStorage(ceDocument, &rootStorage);
    // 判断document中是否有指定stream
    ContentEmbed_Stream *childStream;
    char* fileType = "aaa";
    ret = OH_ContentEmbed_Storage_GetStream(rootStorage, fileType, &childStream);
    if (ret == CE_ERR_OK) {
        size_t bufferSize;
        // 获取OE文档流的大小
        ret = OH_ContentEmbed_Stream_GetSize(childStream, &bufferSize);
        // Read之前需要将流位置重置
        ret = OH_ContentEmbed_Stream_Seek(childStream, 0);
        unsigned char *buffer;
        size_t num = 0;
        // 读取流数据
        ret = OH_ContentEmbed_Stream_Read(childStream, &buffer, bufferSize, &num);
        std::string tempPath = "/data/storage/el2/base/cache/temp.aaa";
        // 创建输出文件流对象，并以二进制模式打开文件
        std::ofstream outputFile(tempPath, std::ios::out | std::ios::binary);
        // 检查文件是否成功打开
        if (outputFile.is_open()) {
            // 将缓冲区内容写入文件
            outputFile.write(reinterpret_cast<const char*>(buffer), bufferSize);
            // 关闭文件（析构函数会自动调用，但显式关闭是好习惯）
            outputFile.close();
            OH_LOG_INFO(LOG_APP, "数据写入成功。");
        } else {
            OH_LOG_INFO(LOG_APP, "无法打开文件。");
        }
        char* tempFileUri;
        OH_FileUri_GetUriFromPath(tempPath.c_str(), tempPath.size(), &tempFileUri);
        // 设置文件路径
        OH_AbilityBase_SetWantUri(want, tempFileUri);
    }
    // 拉起UIAbility 对文档进行编辑操作
    int32_t result = OH_ContentEmbed_Extension_ContextStartSelfUIAbility(context, want);
}
```

### OE文档获取OE Extension能力

当OE Extension被拉起后，OE客户端会通过[OH_ContentEmbed_Proxy_GetCapability](../reference/apis-content-embed-kit/capi-content-embed-proxy-h#OH_ContentEmbed_Proxy_GetCapability)获取OE服务端具备的能力，此时会触发OE服务端的`NativeOnGetCapability`回调，在该回调中OE服务端应用通过给`bitmask`属性赋值，通知OE客户端自身具备的能力。

```cpp
static void NativeOnGetCapability(ContentEmbed_ObjectHandle object, uint32_t *bitmask)
{
    if (!bitmask) {
        OH_LOG_ERROR(LOG_APP, "bitmask is null");
        return;
    }
    *bitmask = CE_CAPABILITY_SUPPORT_SNAPSHOT | CE_CAPABILITY_SUPPORT_DO_EDIT;
}
```

### OE文档查询编辑状态

当OE Extension被拉起后，OE客户端会通过[OH_ContentEmbed_Proxy_GetEditStatus](../reference/apis-content-embed-kit/capi-content-embed-proxy-h#OH_ContentEmbed_Proxy_GetEditStatus)获取OE文档编辑状态，此时会触发OE服务端的`NativeOnGetEditStatusFunc`回调，在该回调中OE服务端应用通知OE客户端文档编辑状态。

```cpp
static void NativeOnGetEditStatusFunc(ContentEmbed_ObjectHandle object, bool *isEditing, bool *isModified)
{
    if (!isEditing || !isModified) {
        OH_LOG_ERROR(LOG_APP, "param is null");
        return;
    }
    // 若文档未处于编辑态
    *isEditing = false;
    *isModified = false;
}
```

### OE文档写流操作

当OE客户端通过已存在文件来嵌入OE对象且OE Extension被拉起后，此时会触发OE服务端的`NativeOnWriteToDataStream`回调，在该回调中OE服务端需往OE文档中写入数据。

```cpp
static void NativeOnWriteToDataStream(ContentEmbed_ObjectHandle object)
{
    ContentEmbed_ErrorCode ret = CE_ERR_OK;
    ContentEmbed_Document* ceDocument = nullptr;
    // 获取OE文档
    ret = OH_ContentEmbed_Extension_GetContentEmbedDocument(object, &ceDocument);
    if (ret != CE_ERR_OK) {
        OH_LOG_INFO(LOG_APP, "OH_ContentEmbed_Extension_GetContentEmbedDocument ret: %{public}d", ret);
        return;
    }
    // 获取Root Storage
    ContentEmbed_Storage *rootStorage = nullptr;
    ret = OH_ContentEmbed_Document_GetRootStorage(ceDocument, &rootStorage);
    if (ret != CE_ERR_OK) {
        OH_LOG_INFO(LOG_APP, "OH_ContentEmbed_Document_GetRootStorage ret: %{public}d", ret);
        return;
    }

    ContentEmbed_Stream *destStream;
    char* fileType = "aaa";
    // 获取名字为aaa的流
    ret = OH_ContentEmbed_Storage_GetStream(rootStorage, fileType, &destStream);
    if (ret != CE_ERR_OK) {
        // 获取失败创建名字为aaa的流
        ret = OH_ContentEmbed_Storage_CreateStream(rootStorage, fileType, &destStream);
    }
    // 获取本地文件路径
    char nativeFilePath[MAX_PATH_LENGTH];
    ret = OH_ContentEmbed_Document_GetNativeFilePath(ceDocument, nativeFilePath);
    if (ret != CE_ERR_OK) {
        OH_LOG_INFO(LOG_APP, "OH_ContentEmbed_Document_GetNativeFilePath ret: %{public}d", ret);
        return;
    }

    std::string srcStreamPath = std::string(nativeFilePath);
    std::ifstream oriFile(srcStreamPath, std::ios::binary);
    if (!oriFile) {
        OH_LOG_ERROR(LOG_APP, "std::ifstream: File not existed");
        return;
    }
    oriFile.seekg(0, std::ios::end);
    size_t oriFileSize = oriFile.tellg();
    oriFile.seekg(0, std::ios::beg);
    std::vector<unsigned char> buffer(oriFileSize);
    oriFile.read(reinterpret_cast<char*>(buffer.data()), oriFileSize);
    size_t num = 0;
    // 往OE文档写数据
    ret = OH_ContentEmbed_Stream_Write(destStream, buffer.data(), oriFileSize, &num);
    // 刷新OE文档
    ret = OH_ContentEmbed_Document_Flush(ceDocument);
}
```