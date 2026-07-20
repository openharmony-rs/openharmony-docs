# DismissContentCoverAction

Component content cover dismiss

**起始版本：** 12

<!--Device-unnamed-declare interface DismissContentCoverAction--><!--Device-unnamed-declare interface DismissContentCoverAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss: Callback<void>
```

全屏模态页面关闭回调函数。开发者需要退出页面时调用。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DismissContentCoverAction-dismiss: Callback<void>--><!--Device-DismissContentCoverAction-dismiss: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

返回本次拦截全屏模态页面退出的事件原因。

**类型：** DismissReason

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DismissContentCoverAction-reason: DismissReason--><!--Device-DismissContentCoverAction-reason: DismissReason-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

