# DismissDialogAction

Dialog关闭的信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface DismissDialogAction--><!--Device-unnamed-export declare interface DismissDialogAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss(): void
```

Dialog关闭回调函数。开发者需要退出时调用，不需要退出时无需调用此函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DismissDialogAction-dismiss(): void--><!--Device-DismissDialogAction-dismiss(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

Reason why the dialog box cannot be dismissed. You must specify whether to close the dialog box for each of the listed actions.

**类型：** [DismissReason](../../apis-arkui/arkts-components/arkts-arkui-dismissreason-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DismissDialogAction-reason: DismissReason--><!--Device-DismissDialogAction-reason: DismissReason-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

