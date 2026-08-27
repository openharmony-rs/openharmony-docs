# OnTitleReceiveEvent

定义网页标题更改时触发的回调信息，包括标题内容和来源。适用于需要监控页面标题变化的场景，提升页面信息的实时性和用户体验。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## isRealTitle

```TypeScript
isRealTitle?: boolean
```

document标题来源，true表示来自网页的title标签，false表示该title是根据url自动生成。默认值：false

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## title

```TypeScript
title: string
```

document标题内容。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
