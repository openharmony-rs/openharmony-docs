# AlertDialogButtonOptions

继承自[AlertDialogButtonBaseOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** AlertDialogButtonOptions extends [AlertDialogButtonBaseOptions](alertdialog-alertdialogbuttonbaseoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface AlertDialogButtonOptions extends AlertDialogButtonBaseOptions--><!--Device-unnamed-export declare interface AlertDialogButtonOptions extends AlertDialogButtonBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
primary?: boolean
```

在弹窗获焦且未进行tab键走焦时，按钮是否默认响应Enter键。多个Button时，只允许一个Button的该字段配置为true，否则所有Button均不响应。多重弹窗可自动获焦连续响应。在defaultFocus为true时 不生效。值为true表示按钮默认响应Enter键，值为false时，按钮不默认响应Enter键。 默认值：false **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlertDialogButtonOptions-primary?: boolean--><!--Device-AlertDialogButtonOptions-primary?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

