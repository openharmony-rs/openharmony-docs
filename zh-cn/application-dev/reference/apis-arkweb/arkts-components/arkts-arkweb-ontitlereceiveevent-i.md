# OnTitleReceiveEvent

定义网页document标题更改时触发该回调。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## isRealTitle

```TypeScript
isRealTitle?: boolean
```

document标题来源，true表示来自网页的title标签，false表示该title是根据url自动生成。
默认值：false

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

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

