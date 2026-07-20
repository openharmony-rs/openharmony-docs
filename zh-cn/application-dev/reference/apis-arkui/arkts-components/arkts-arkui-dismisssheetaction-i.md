# DismissSheetAction

半模态关闭前的回调。

**起始版本：** 12

<!--Device-unnamed-declare interface DismissSheetAction--><!--Device-unnamed-declare interface DismissSheetAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss: Callback<void>
```

半模态页面关闭回调函数。开发者需要退出页面时调用。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DismissSheetAction-dismiss: Callback<void>--><!--Device-DismissSheetAction-dismiss: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

返回本次半模态页面退出的操作类型。

**说明：**

DismissReason.SLIDE只生效半模态侧边弹窗形态，表示右滑退出。若镜像场景则表示左滑退出。

DismissReason.SLIDE_DOWN生效半模态底部弹窗形态和居中弹窗形态，表示下滑退出。

半模态气泡弹窗形态无滑动退出能力。

**类型：** DismissReason

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DismissSheetAction-reason: DismissReason--><!--Device-DismissSheetAction-reason: DismissReason-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

