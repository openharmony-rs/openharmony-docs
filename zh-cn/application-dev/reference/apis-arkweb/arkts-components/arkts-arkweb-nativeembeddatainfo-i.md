# NativeEmbedDataInfo

提供同层标签生命周期变化的详细信息，包括状态和标签信息。适用于需要监控同层元素生命周期的场景，提升渲染状态管理的准确性和用户体验。@interface NativeEmbedDataInfo [since 11 - 11]

**起始版本：** 11

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## embedId

```TypeScript
embedId?: string
```

同层标签的唯一id。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## info

```TypeScript
info?: NativeEmbedInfo
```

同层标签的详细信息。

**类型：** [NativeEmbedInfo](arkts-arkweb-nativeembedinfo-i.md)

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## status

```TypeScript
status?: NativeEmbedStatus
```

同层标签生命周期状态。

**类型：** [NativeEmbedStatus](arkts-arkweb-nativeembedstatus-e.md)

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## surfaceId

```TypeScript
surfaceId?: string
```

NativeImage的surfaceId。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
