# AlertDialogParamWithButtons

继承自[AlertDialogParam](arkts-arkui-alertdialogparam-i.md)。

**继承/实现关系：** AlertDialogParamWithButtons extends [AlertDialogParam](arkts-arkui-alertdialogparam-i.md)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## primaryButton

```TypeScript
primaryButton: AlertDialogButtonBaseOptions
```

主要Button的使能状态、默认焦点、按钮风格、文本内容、文本色、按钮背景色和点击回调。在弹窗获焦且未进行tab键走焦时，该按钮默认响应Enter键，且多重弹窗可自动获焦连续响应。默认响应Enter键能力在defaultFocus 为true时不生效。 具体使用方式请参考[示例7](arkts-arkui-alertdialog-c.md) 。

**类型：** [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton: AlertDialogButtonBaseOptions
```

次要Button的使能状态、默认焦点、按钮风格、文本内容、文本色、按钮背景色和点击回调。

**类型：** [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
