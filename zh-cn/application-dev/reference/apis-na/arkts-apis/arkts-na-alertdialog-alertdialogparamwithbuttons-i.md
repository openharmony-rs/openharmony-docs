# AlertDialogParamWithButtons

继承自[AlertDialogParam](arkts-na-alertdialog-alertdialogparam-i.md)。

**继承/实现关系：** AlertDialogParamWithButtons extends [AlertDialogParam](arkts-na-alertdialog-alertdialogparam-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface AlertDialogParamWithButtons--><!--Device-unnamed-export declare interface AlertDialogParamWithButtons-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton: AlertDialogButtonBaseOptions
```

主要Button的使能状态、默认焦点、按钮风格、文本内容、文本色、按钮背景色和点击回调。在弹窗获焦且未进行tab键走焦时，该按钮默认响应Enter键，且多重弹窗可自动获焦连续响应。默认响应Enter键能力在 defaultFocus为true时不生效。 具体使用方式请参考 示例7 。

**类型：** [AlertDialogButtonBaseOptions](arkts-na-alertdialog-alertdialogbuttonbaseoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlertDialogParamWithButtons-primaryButton: AlertDialogButtonBaseOptions--><!--Device-AlertDialogParamWithButtons-primaryButton: AlertDialogButtonBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton: AlertDialogButtonBaseOptions
```

次要Button的使能状态、默认焦点、按钮风格、文本内容、文本色、按钮背景色和点击回调。

**类型：** [AlertDialogButtonBaseOptions](arkts-na-alertdialog-alertdialogbuttonbaseoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlertDialogParamWithButtons-secondaryButton: AlertDialogButtonBaseOptions--><!--Device-AlertDialogParamWithButtons-secondaryButton: AlertDialogButtonBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

