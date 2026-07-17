# DismissPopupAction

气泡关闭的信息。

**起始版本：** 12

<!--Device-unnamed-declare interface DismissPopupAction--><!--Device-unnamed-declare interface DismissPopupAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss: Callback<void>
```

Popup关闭回调函数。开发者需要退出时调用，不需要退出时无需调用。

**类型：** Callback<void>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DismissPopupAction-dismiss: Callback<void>--><!--Device-DismissPopupAction-dismiss: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

关闭原因，返回本次拦截Popup消失的事件原因。

**类型：** DismissReason

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DismissPopupAction-reason: DismissReason--><!--Device-DismissPopupAction-reason: DismissReason-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

