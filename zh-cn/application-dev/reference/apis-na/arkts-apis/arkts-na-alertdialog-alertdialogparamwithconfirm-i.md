# AlertDialogParamWithConfirm

继承自[AlertDialogParam](arkts-na-alertdialog-alertdialogparam-i.md#AlertDialogParam)。

**继承/实现关系：** AlertDialogParamWithConfirm extends [AlertDialogParam](arkts-na-alertdialog-alertdialogparam-i.md#AlertDialogParam)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface AlertDialogParamWithConfirm--><!--Device-unnamed-export declare interface AlertDialogParamWithConfirm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## confirm

```TypeScript
confirm?: AlertDialogButtonBaseOptions
```

确认Button的使能状态、默认焦点、按钮风格、文本内容、文本色、按钮背景色和点击回调。在弹窗获焦且未进行tab键走焦时，该按钮默认响应Enter键。多重弹窗情况下，可自动获焦并连续响应。默认响应Enter键能力在 defaultFocus为true时不生效。

**类型：** [AlertDialogButtonBaseOptions](arkts-na-alertdialog-alertdialogbuttonbaseoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlertDialogParamWithConfirm-confirm?: AlertDialogButtonBaseOptions--><!--Device-AlertDialogParamWithConfirm-confirm?: AlertDialogButtonBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

