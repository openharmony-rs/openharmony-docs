# AlertDialogParamWithOptions

继承自[AlertDialogParam]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** AlertDialogParamWithOptions extends [AlertDialogParam](alertdialog-alertdialogparam-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface AlertDialogParamWithOptions extends AlertDialogParam--><!--Device-unnamed-export declare interface AlertDialogParamWithOptions extends AlertDialogParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonDirection

```TypeScript
buttonDirection?: DialogButtonDirection
```

按钮排布方向默认为DialogButtonDirection.AUTO。建议3个以上按钮使用Auto模式（两个以上按钮会切换为纵向模式，通常能显示更多按钮）。非Auto模式下，3个以上按钮可能会显示不全，超出显示范围的按钮会被 截断。

**类型：** DialogButtonDirection

**默认值：** DialogButtonDirection.AUTO

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlertDialogParamWithOptions-buttonDirection?: DialogButtonDirection--><!--Device-AlertDialogParamWithOptions-buttonDirection?: DialogButtonDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons: Array<AlertDialogButtonOptions>
```

弹窗容器中的多个按钮。

**类型：** Array&lt;AlertDialogButtonOptions&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlertDialogParamWithOptions-buttons: Array<AlertDialogButtonOptions>--><!--Device-AlertDialogParamWithOptions-buttons: Array<AlertDialogButtonOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

