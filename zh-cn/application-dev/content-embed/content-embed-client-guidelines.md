# 客户端应用开发
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @zhaotianyu-->
<!--Adviser: @jinqiuheng-->

## 场景介绍

[OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md)内容嵌入模块提供对象编辑框架与技术，支持应用间文档嵌入与协同编辑。

OE客户端应用：指面向终端用户且被嵌入文档的应用。通过调用[OE框架层接口](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md)实现业务逻辑，如嵌入外部文档、展示文档快照，以及按需拉起OE服务端应用以触发文档编辑操作。

典型应用场景包括：
- 在CAD文档中嵌入Excel表格，通过点击嵌入对象拉起Excel应用进行编辑。
- 在文档编辑器中嵌入图片、表格等多种格式的文档。
- 在笔记应用中嵌入其他应用的文档，实现跨应用协作。

## 约束限制
- 使用此接口，需确认设备具有以下系统能力：SystemCapability.ContentEmbed.ObjectEditor。
- 申请权限：开发者需要申请ohos.permission.CONNECT_OBJECTEDITOR_EXTENSION权限，配置方式请参阅[声明权限](../security/AccessToken/declare-permissions.md)。

## 接口说明

常用接口如下表所示。更多API说明请参考[OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md)。

**表1** 客户端主要接口

| 接口名称 | 功能描述 |
| ------- | ---- |
| OH_ContentEmbed_CreateDocumentByFile | 通过被嵌入文档路径创建[OE文档](content-embed-kit-terminology.md#OE文档)。|
| OH_ContentEmbed_CreateDocumentByOEId | 通过[OEID](content-embed-kit-terminology.md#OEID)创建OE文档。|
| OH_ContentEmbed_LoadDocumentFromFile | 通过已存在的[OE格式文件](content-embed-kit-terminology.md#OE格式文件)加载OE文档。|
| OH_ContentEmbed_CreateExtensionProxy | 创建[客户端OE对象](content-embed-kit-terminology.md#客户端OE对象)。|
| OH_ContentEmbed_DestroyExtensionProxy | 销毁客户端OE对象，释放相关资源。|
| OH_ContentEmbed_Proxy_RegisterOnUpdateFunc | 向客户端OE对象注册OE文档更新时的回调函数。|
| OH_ContentEmbed_Proxy_RegisterOnErrorFunc | 向客户端OE对象注册OE文档触发错误时回调函数。|
| OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc | 向客户端OE对象注册OE文档编辑完成时的回调函数。|
| OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc | 向客户端OE对象注册[OE Extension](content-embed-kit-terminology.md#OE-Extension)停止时的回调函数。|
| OH_ContentEmbed_Proxy_StartWork | 客户端通过客户端OE对象与Object Editor服务跨进程通信，拉起OE Extension组件，并创建服务端OE对象。|
| OH_ContentEmbed_Proxy_StopWork | 客户端通过客户端OE对象与Object Editor服务跨进程通信，销毁服务端OE对象，释放资源。|
| OH_ContentEmbed_Proxy_GetSnapshot | 从客户端OE对象获取当前OE文档的快照图像，用于预览或缩略图显示。|
| OH_ContentEmbed_Proxy_DoEdit | 客户端通过客户端OE对象与OE Extension组件跨进程通信，通知服务端拉起UIAbility编辑OE文档。|
| OH_ContentEmbed_Proxy_GetDocument | 从客户端OE对象获取其关联的OE文档对象。|
| OH_ContentEmbed_Document_Read | 从OE文档中读取OE格式文件数据，存入buffer。|
| OH_ContentEmbed_DestroyDocument | 销毁OE文档对象，释放资源。|

## 开发步骤

以下演示使用Native API开发OE客户端应用的完整流程。

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
```

### 引用头文件

```cpp
#include <content_embed/content_embed_common.h>
#include <content_embed/content_embed_document.h>
#include <content_embed/content_embed_proxy.h>
#include <hilog/log.h>
#include <multimedia/image_framework/image/pixelmap_native.h>
```

### 查询当前设备支持的OE信息

查询当前设备支持的某个语言下所有的OE信息

```cpp
bool ContentEmbedManager::QueryAllFormat(const std::string &locale)
{
    ContentEmbed_Info* contentEmbedInfo = nullptr;
    // 创建ContentEmbedInfo
    ContentEmbed_ErrorCode errCode = OH_ContentEmbed_CreateContentEmbedInfo(&contentEmbedInfo);
    if (errCode != CE_ERR_OK) {
        return;
    }
    // 获取locale语言的ContentEmbedInfo信息
    errCode = OH_ContentEmbed_GetContentEmbedInfo(locale.c_str(), contentEmbedInfo);
    if (errCode != CE_ERR_OK) {
        // 查询失败销毁ContentEmbedInfo对象
        OH_ContentEmbed_DestroyContentEmbedInfo(contentEmbedInfo);
        return;
    }
    uint32_t count = 0;
    // 获取ContentEmbedInfo对象Format对象数量
    errCode = OH_ContentEmbed_GetFormatCountFromInfo(contentEmbedInfo, &count);
    if (errCode != CE_ERR_OK) {
        // 查询失败销毁ContentEmbedInfo对象
        OH_ContentEmbed_DestroyContentEmbedInfo(contentEmbedInfo);
        return;
    }
    for (int i = 0; i < count; i++) {
        ContentEmbed_Format* ceFormat = nullptr;
        // 从ContentEmbedInfo对象获取索引为i的ContentEmbed_Format信息
        errCode = OH_ContentEmbed_GetFormatFromInfo(contentEmbedInfo, i, &ceFormat);
        if (errCode != CE_ERR_OK) {
            continue;
        }
        char oeid[MAX_OEID_LENGTH];
        // 获取OEID
        errCode = OH_ContentEmbed_GetOEIdFromFormat(ceFormat, oeid);
        OH_LOG_INFO(LOG_APP, "OH_ContentEmbed_Format_GetOEId ret: %{public}d, oeid: %{public}s", errCode, oeid);
        char name[MAX_NAME_LENGTH];
        char description[MAX_DESCRIPTION_LENGTH];
        // 获取名称和描述
        errCode = OH_ContentEmbed_GetNameAndDescriptionFromFormat(ceFormat, name, description);
        OH_PixelmapNative* pixelMap = nullptr;
        // 获取图标
        errCode = OH_ContentEmbed_GetIconFromFormat(ceFormat, &pixelMap);
    }
    // 销毁ContentEmbedInfo对象
    OH_ContentEmbed_DestroyContentEmbedInfo(contentEmbedInfo);
}
```

### 根据OEID查询特定格式文件的名称和描述

```cpp
bool ContentEmbedManager::QueryFormatByOEId(const std::string &oeid, const std::string &locale)
{
    ContentEmbed_Format* ceFormat = nullptr;
    // 创建ContentEmbed_Format
    ContentEmbed_ErrorCode = OH_ContentEmbed_CreateContentEmbedFormat(&ceFormat);
    if (errCode != CE_ERR_OK) {
        return;
    }
    errCode = OH_ContentEmbed_GetContentEmbedFormatByOEIdAndLocale(oeid.c_str(), locale.c_str(), ceFormat);
    if (errCode != CE_ERR_OK) {
        // 查询失败销毁ContentEmbed_Format对象
        OH_ContentEmbed_DestroyContentEmbedFormat(ceFormat);
    }
    // 获取OEID
    errCode = OH_ContentEmbed_GetOEIdFromFormat(ceFormat, oeid);
    OH_LOG_INFO(LOG_APP, "OH_ContentEmbed_Format_GetOEId ret: %{public}d, oeid: %{public}s", errCode, oeid);
    char name[MAX_NAME_LENGTH];
    char description[MAX_DESCRIPTION_LENGTH];
    // 获取名称和描述
    errCode = OH_ContentEmbed_GetNameAndDescriptionFromFormat(ceFormat, name, description);
    OH_PixelmapNative* pixelMap = nullptr;
    // 获取图标
    errCode = OH_ContentEmbed_GetIconFromFormat(ceFormat, &pixelMap);
    // 销毁ContentEmbed_Format对象
    OH_ContentEmbed_DestroyContentEmbedInfo(contentEmbedInfo);
}
```

### 创建OE文档

1. 基于OEID创建OE文档

```cpp
ContentEmbed_Document* oeDocument;
// 基于OEID创建OE文件
ContentEmbed_ErrorCode errCode = OH_ContentEmbed_CreateDocumentByOEId(oeid.c_str(), &oeDocument);
```

2. 基于文件创建OE文档

```cpp
std::string GetFileFromPicker()
{
    std::string filePath;
    // 从file picker中获取文档路径
    return filePath;
}

std::string filePath = GetFileFromPicker();
// 基于文件创建OE文档
ContentEmbed_Document *ceDocument;
// 是否以链接形式创建OE文档，当isLinking为true时，表示以链接方式创建OE文档；当isLinking为false时，表示以嵌入方式创建OE文档。
bool isLinking = false;
ContentEmbed_ErrorCode ret = OH_ContentEmbed_CreateDocumentByFile(filePath.c_str(), filePath.size(), isLinking, &ceDocument);
```

3. 基于[OE格式文件](content-embed-kit-terminology.md#OE格式文件)加载OE文档，当OE格式文件为数据流存储时需先落盘至本地再使用此接口。

```cpp
// OE格式文件路径
std::string filePath;
ContentEmbed_Document *ceDocument;
ContentEmbed_ErrorCode ret = OH_ContentEmbed_LoadDocumentFromFile(filePath.c_str(), filePath.size(), &ceDocument);
```

### 创建客户端OE对象

基于OE文档和当前上下文实例创建客户端OE对象，实现OE文档与客户端OE对象的关联，并用于与服务端通信。

```cpp
void ClientCallBack_OnUpdateFunc(ContentEmbed_ExtensionProxy *proxy)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallBack_OnUpdateFunc");
    //将OE文档数据写入客户端应用文档
    ContentEmbed_Document *document = nullptr;
    ContentEmbed_ErrorCode errCode = OH_ContentEmbed_Proxy_GetDocument(proxy, &document);
    bool isLinking = false;
    ContentEmbed_ErrorCode ret = OH_ContentEmbed_Document_IsLinking(document, &isLinking);
    OH_LOG_INFO(LOG_APP, "ret: %{public}d, isLinking: %{public}d", ret, isLinking);
    if (ret == CE_ERR_OK && isLinking) {
        OH_LOG_INFO(LOG_APP, "liking document, No need to save to the sandbox");
        return;
    }
    const size_t CHUNK_SIZE = 4096; // 分块大小
    uint8_t *buffer = new (std::nothrow) uint8_t[CHUNK_SIZE + 1];
    if (!buffer)
        return;
    size_t offset = 0;
    size_t actualRead = 0;
    do {
        ret = OH_ContentEmbed_Document_Read(buffer, CHUNK_SIZE, document, offset, &actualRead);

        if (ret != CE_ERR_OK || actualRead == 0)
            break;

        // 自行处理buffer数据流
        ...
        offset += actualRead;
    } while (true);

    delete[] buffer;
}

void ClientCallBack_OnErrorFunc(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallBack_OnErrorFunc, error: %{public}d", error);
}

void ClientCallBack_OnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, bool dataModified)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallBack_OnEditingFinishedFunc, dataModified: %{public}d", dataModified);
    // 建议此时销毁OE文档和客户端OE对象，释放资源。
    ContentEmbed_Document *document = nullptr;
    ContentEmbed_ErrorCode errCode = OH_ContentEmbed_Proxy_GetDocument(proxy, &document);
    OH_ContentEmbed_DestroyDocument(document);
    OH_ContentEmbed_DestroyExtensionProxy(proxy);

}

void ClientCallBack_OnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallBack_OnExtensionStoppedFunc");
}

// contextPtr: 当前上下文实例
// oeDocument: OE文档
void ContentEmbedManager::CreateProxy(void* contextPtr, ContentEmbed_Document *oeDocument)
{
    ContentEmbed_ExtensionProxy* proxy;
    // 创建客户端OE对象
    ContentEmbed_ErrorCode errCode = OH_ContentEmbed_CreateExtensionProxy(oeDocument, &proxy, contextPtr);
    // 注册回调：注册文档更新、错误、编辑结束等回调函数，回调函数注册顺序无要求，但不能遗漏。
    // 注册OE文档更新回调
    errCode = OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(proxy, ClientCallBack_OnUpdateFunc);
    // 注册OE文档发生错误回调
    errCode = OH_ContentEmbed_Proxy_RegisterOnErrorFunc(proxy, ClientCallBack_OnErrorFunc);
    // 注册OE文档编辑结束回调
    errCode = OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(proxy, ClientCallBack_OnEditingFinishedFunc);
    // 注册Extension实例关闭回调
    errCode = OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(proxy, ClientCallBack_OnExtensionStoppedFunc);
}
```

获取当前上下文实例

```ArkTS
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
nativeModule.receiveContext(context); // 调用Native接口
```

```cpp
static napi_value ReceiveContext(napi_env env, napi_callback_info info) {
    size_t argc = 1;
    napi_value argv;
    napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);

    // 获取ArkTS传递的UIAbilityContext对象
    napi_value contextObj = argv;
  
    // 转换为Native可操作指针（需提前通过napi_wrap绑定）
    void* contextPtr = nullptr;
    napi_status status = napi_unwrap(env, contextObj, &contextPtr);
  
    if (status != napi_ok || nativeContextPtr == nullptr) {
        // 错误处理
        napi_throw_error(env, nullptr, "Failed to unwrap context");
        return nullptr;
    }
    // 记录contextPtr，后续使用
    ...
    return nullptr;
}

// napi注册
EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports) {
    napi_property_descriptor desc[] = {
        {"receiveContext", nullptr, ReceiveContext, nullptr, nullptr, nullptr, napi_default, nullptr},
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END  
```

### 客户端OE对象和OE Extension交互

1. 拉起OE Extension：启动OE Extension组件。
2. 查询OE Extension组件能力。
3. 编辑文档：通知OE服务端拉起UIAbility编辑文档。
4. 查询OE文档编辑状态。
5. 获取OE文档快照

```cpp
void ContentEmbedManager::HandleProxy(ContentEmbed_ExtensionProxy* proxy)
{
    ContentEmbed_ErrorCode errCode = CE_ERR_OK;
    // 拉起OE Extension组件
    errCode = OH_ContentEmbed_Proxy_StartWork(proxy);
    if (errCode != CE_ERR_OK) {
        return;
    }
    uint32_t bitmask = 0;
    // 查询OE Extension组件能力
    errCode = OH_ContentEmbed_Proxy_GetCapability(proxy, &bitmask);
    // 编辑被嵌入文档
    errCode = OH_ContentEmbed_Proxy_DoEdit(proxy);
    if (errCode != CE_ERR_OK) {
        return;
    }
    bool isEditing = false;
    bool isModified = false;
    // 查询被嵌入文档编辑状态
    errCode = OH_ContentEmbed_Proxy_GetEditStatus(proxy, &isEditing, &isModified);
    OH_PixelmapNative* pixelMap;
    // 获取被嵌入文档快照
    errCode = OH_ContentEmbed_Proxy_GetSnapshot(proxy, &pixelMap);
    // 当proxy不需要和服务端交互时
    OH_ContentEmbed_Proxy_StopWork(proxy);
}
```