# AlertDialogParamWithConfirm

继承自[AlertDialogParam](arkts-arkui-alertdialogparam-i.md)。

confirm参数优先级：fontColor、backgroundColor > style > defaultFocus

**继承/实现关系：** AlertDialogParamWithConfirm extends [AlertDialogParam](arkts-arkui-alertdialogparam-i.md)

**起始版本：** 7

<!--Device-unnamed-declare interface AlertDialogParamWithConfirm extends AlertDialogParam--><!--Device-unnamed-declare interface AlertDialogParamWithConfirm extends AlertDialogParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## confirm

```TypeScript
confirm?: AlertDialogButtonBaseOptions
```

确认Button的使能状态、默认焦点、按钮风格、文本内容、文本色、按钮背景色和点击回调。在弹窗获焦且未进行tab键走焦时，该按钮默认响应Enter键。多重弹窗情况下，可自动获焦并连续响应。默认响应Enter键能力在defaultFocus为true时不生效。

**类型：** AlertDialogButtonBaseOptions

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogParamWithConfirm-confirm?: AlertDialogButtonBaseOptions--><!--Device-AlertDialogParamWithConfirm-confirm?: AlertDialogButtonBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

