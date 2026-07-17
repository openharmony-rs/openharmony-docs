# AlertDialogParamWithButtons

继承自[AlertDialogParam](arkts-arkui-alert-dialog-alertdialogparam-i.md)。

**继承/实现关系：** AlertDialogParamWithButtons extends [AlertDialogParam](arkts-arkui-alert-dialog-alertdialogparam-i.md)

**起始版本：** 7

<!--Device-unnamed-declare interface AlertDialogParamWithButtons extends AlertDialogParam--><!--Device-unnamed-declare interface AlertDialogParamWithButtons extends AlertDialogParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton: AlertDialogButtonBaseOptions
```

主要Button的使能状态、默认焦点、按钮风格、文本内容、文本色、按钮背景色和点击回调。在弹窗获焦且未进行tab键走焦时，该按钮默认响应Enter键，且多重弹窗可自动获焦连续响应。默认响应Enter键能力在defaultFocus为true时不生效。 具体使用方式请参考[示例7](../../../../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md#示例7自定义背景模糊效果参数) 。

**类型：** AlertDialogButtonBaseOptions

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogParamWithButtons-primaryButton: AlertDialogButtonBaseOptions--><!--Device-AlertDialogParamWithButtons-primaryButton: AlertDialogButtonBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton: AlertDialogButtonBaseOptions
```

次要Button的使能状态、默认焦点、按钮风格、文本内容、文本色、按钮背景色和点击回调。

**类型：** AlertDialogButtonBaseOptions

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogParamWithButtons-secondaryButton: AlertDialogButtonBaseOptions--><!--Device-AlertDialogParamWithButtons-secondaryButton: AlertDialogButtonBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

