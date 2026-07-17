# AlertDialogButtonOptions

继承自[AlertDialogButtonBaseOptions](arkts-arkui-alert-dialog-alertdialogbuttonbaseoptions-i.md)。

**继承/实现关系：** AlertDialogButtonOptions extends [AlertDialogButtonBaseOptions](arkts-arkui-alert-dialog-alertdialogbuttonbaseoptions-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface AlertDialogButtonOptions extends AlertDialogButtonBaseOptions--><!--Device-unnamed-declare interface AlertDialogButtonOptions extends AlertDialogButtonBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
primary?: boolean
```

在弹窗获焦且未进行tab键走焦时，按钮是否默认响应Enter键。多个Button时，只允许一个Button的该字段配置为true，否则所有Button均不响应。多重弹窗可自动获焦连续响应。在defaultFocus为true时不生效。值为true表示按钮默认响应Enter键，值为false时，按钮不默认响应Enter键。

默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogButtonOptions-primary?: boolean--><!--Device-AlertDialogButtonOptions-primary?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

