# DismissContentCoverAction

```TypeScript
declare interface DismissContentCoverAction
```

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss: Callback<void>
```

全屏模态页面关闭回调函数。须在onWillDismiss回调中调用此方法以关闭全屏模态页面；未调用时，全屏模态页面将保持打开状态不关闭。

**类型：** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

返回本次拦截全屏模态页面退出的事件原因。

**类型：** [DismissReason](arkts-arkui-common-comp-dismissreason-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
