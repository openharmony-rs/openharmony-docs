# NativeEmbedTouchInfo

提供手指触摸同层标签的详细信息，包括标签ID和触摸事件。适用于需要处理同层元素触摸交互的场景，提升触摸体验的定制性和灵活性。@interface NativeEmbedTouchInfo [since 11 - 11]

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

## result

```TypeScript
result?: EventResult
```

通知Web组件手势事件的消费结果。

**类型：** [EventResult](arkts-arkweb-eventresult-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## touchEvent

```TypeScript
touchEvent?: TouchEvent
```

手指触摸动作信息。

**类型：** TouchEvent

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
