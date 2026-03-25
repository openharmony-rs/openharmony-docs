# 客户端应用开发
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @zhaotianyu-->
<!--Adviser: @jinqiuheng-->

## 场景介绍

[OH_ContentEmbed](../reference/apis-content-embed-kit/capi-contentembed.md)内容嵌入模块提供对象编辑框架与技术，支持应用间文档嵌入与协同编辑。

OE客户端应用：指作为被嵌入文档的宿主、面向终端用户的应用。通过调用[OE框架层接口](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md)实现业务逻辑，如嵌入外部文档、展示文档快照，以及按需拉起OE服务端应用以触发文档编辑操作。

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
| OH_ContentEmbed_CreateDocumentByFile | 通过被嵌入文档路径创建OE文档 |
| OH_ContentEmbed_CreateDocumentByOEId | 通过OEID创建OE文档 |
| OH_ContentEmbed_LoadDocumentFromFile | 通过已存在的OE格式文件加载OE文档 |
| OH_ContentEmbed_CreateExtensionProxy | 创建客户端OE对象 |
| OH_ContentEmbed_DestroyExtensionProxy | 销毁客户端OE对象，释放相关资源 |
| OH_ContentEmbed_Proxy_RegisterOnUpdateFunc | 向客户端OE对象注册OE文档更新时的回调函数 |
| OH_ContentEmbed_Proxy_RegisterOnErrorFunc | 向客户端OE对象注册OE文档触发错误时回调函数 |
| OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc | 向客户端OE对象注册OE文档编辑完成时的回调函数 |
| OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc | 向客户端OE对象注册OE Extension停止时的回调函数 |
| OH_ContentEmbed_Proxy_StartWork | 客户端通过客户端OE对象与Object Editor服务跨进程通信，拉起OE Extension组件，并创建服务端OE对象 |
| OH_ContentEmbed_Proxy_StopWork | 客户端通过客户端OE对象与Object Editor服务跨进程通信，销毁服务端OE对象，释放资源 |
| OH_ContentEmbed_Proxy_GetSnapshot | 从客户端OE对象获取当前OE文档的快照图像，用于预览或缩略图显示 |
| OH_ContentEmbed_Proxy_DoEdit | 客户端通过客户端OE对象与OE Extension组件跨进程通信，通知服务端拉起UIAbility编辑OE文档 |
| OH_ContentEmbed_Proxy_GetDocument | 从客户端OE对象获取其关联的OE文档对象 |
| OH_ContentEmbed_Document_Read | 从OE文档中读取OE格式文件数据，存入buffer |
| OH_ContentEmbed_Document_GetNativeFilePath | 从OE文档中获取客户端沙箱目录下存储的被嵌入源文件路径 |
| OH_ContentEmbed_Document_GetRootStorage | 从OE文档中获取OE格式文件根目录 |
| OH_ContentEmbed_Document_Flush | 将OE文档中数据落盘至OE格式文件 |
| OH_ContentEmbed_DestroyDocument | 销毁OE文档对象，释放资源 |

## 开发步骤

OE客户端开发的步骤包括：
1. 创建OE文档：通过文件路径或OEID创建OE文档对象。
2. 创建客户端OE对象：通过OE文档创建客户端OE对象，实现OE文档与客户端OE对象的关联。并用于与服务端通信。
3. 注册回调：注册文档更新、错误、编辑结束等回调函数。
4. 拉起OE Extension：启动OE Extension组件，获取文档快照。
5. 编辑文档：通知OE服务端拉起UIAbility编辑文档。
6. 资源释放：销毁OE文档和OE Extension代理，释放资源。

以下演示使用 Native API 开发OE客户端应用的完整流程。

### 添加动态链接库
CMakeLists.txt中添加以下lib。

```sh
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
        ContentEmbed_Format* ceFormat;
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
    ContentEmbed_Format* ceFormat;
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

1. 基于OEID对象创建OE文档

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
ContentEmbed_ErrorCode ret = OH_ContentEmbed_CreateDocumentByFile(filePath.c_str(), filePath.size(), false, &ceDocument);
```

3. 基于OE格式文件加载OE文档

```cpp
// OE 文件格式路径
std::string filePath;
ContentEmbed_Document *ceDocument;
ContentEmbed_ErrorCode ret = OH_ContentEmbed_LoadDocumentFromFile(filePath.c_str(), filePath.size(), &ceDocument);
```

### 创建客户端OE对象

基于OE文档和当前上下文实例创建客户端OE对象

```cpp
void ClientCallBack_OnUpdateFunc(ContentEmbed_ExtensionProxy *proxy)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallBack_OnUpdateFunc");
}

void ClientCallBack_OnErrorFunc(ContentEmbed_ExtensionProxy *proxy, ContentEmbed_ErrorCode error)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallBack_OnErrorFunc, error: %{public}d", error);
}

void ClientCallback_OnEditingFinishedFunc(ContentEmbed_ExtensionProxy *proxy, bool dataModified)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallback_OnEditingFinishedFunc, dataModified: %{public}d", dataModified);
}

void ClientCallback_OnExtensionStoppedFunc(ContentEmbed_ExtensionProxy *proxy)
{
    OH_LOG_INFO(LOG_APP, "Enter ClientCallback_OnExtensionStoppedFunc");
}

// contextPtr: 当前上下文实例
// oeDocument: OE文档
void ContentEmbedManager::CreateProxy(void* contextPtr, ContentEmbed_Document *oeDocument)
{
    ContentEmbed_ExtensionProxy* proxy;
    // 创建Proxy对象
    ContentEmbed_ErrorCode errCode = OH_ContentEmbed_CreateExtensionProxy(oeDocument, &proxy, contextPtr);
    // 注册OE文档更新回调
    errCode = OH_ContentEmbed_Proxy_RegisterOnUpdateFunc(proxy, ClientCallBack_OnUpdateFunc);
    // 注册OE文档发生错误回调
    errCode = OH_ContentEmbed_Proxy_RegisterOnErrorFunc(proxy, ClientCallBack_OnErrorFunc);
    // 注册OE文档编辑结束回调
    errCode = OH_ContentEmbed_Proxy_RegisterOnEditingFinishedFunc(proxy, ClientCallback_OnEditingFinishedFunc);
    // 注册Extension实例关闭回调
    errCode = OH_ContentEmbed_Proxy_RegisterOnExtensionStoppedFunc(proxy, ClientCallback_OnExtensionStoppedFunc);
}
```

### OE对象和OE Extension交互

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