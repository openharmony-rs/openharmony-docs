# OnTouchIconUrlReceivedEvent

定义接收到apple-touch-icon URL时触发的回调信息，包括URL和预合成状态。适用于需要获取网页图标的场景，提升图标管理的灵活性和用户体验。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## precomposed

```TypeScript
precomposed: boolean
```

对应apple-touch-icon是否为预合成。true表示对应apple-touch-icon为预合成，false表示对应apple-touch-icon不是预合成。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

接收到的apple-touch-icon url地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
