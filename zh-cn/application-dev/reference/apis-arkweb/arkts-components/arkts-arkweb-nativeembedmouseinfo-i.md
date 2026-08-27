# NativeEmbedMouseInfo

提供鼠标/触摸板在同层标签上点击或长按的详细信息，包括标签ID和鼠标事件。适用于需要处理同层元素鼠标交互的场景，提升鼠标体验的定制性和灵活性。

**起始版本：** 20

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

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## mouseEvent

```TypeScript
mouseEvent?: MouseEvent
```

鼠标/触摸板点击/长按信息。

**类型：** MouseEvent

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## result

```TypeScript
result?: EventResult
```

通知Web组件鼠标事件的消费结果。

**类型：** [EventResult](arkts-arkweb-eventresult-c.md)

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core
