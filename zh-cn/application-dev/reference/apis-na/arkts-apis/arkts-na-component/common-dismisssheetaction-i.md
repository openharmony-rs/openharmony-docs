# DismissSheetAction

控制半模态的关闭。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface DismissSheetAction--><!--Device-unnamed-export declare interface DismissSheetAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss(): void
```

半模态面板关闭回调函数。开发者需要退出时调用，不需要退出时无需调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DismissSheetAction-dismiss(): void--><!--Device-DismissSheetAction-dismiss(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

返回本次半模态页面退出的操作类型。 **说明：** DismissReason.SLIDE只生效半模态侧边弹窗形态，表示右滑退出。若镜像场景则表示左滑退出。 DismissReason.SLIDE\_DOWN生效半模态底部弹窗形态和居中弹窗形态，表示下滑退出。 半模态气泡弹窗形态无滑动退出能力。

**类型：** DismissReason

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DismissSheetAction-reason: DismissReason--><!--Device-DismissSheetAction-reason: DismissReason-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

