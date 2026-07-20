# AlertDialogParamWithOptions

继承自[AlertDialogParam](arkts-arkui-alertdialogparam-i.md)。

**继承/实现关系：** AlertDialogParamWithOptions extends [AlertDialogParam](arkts-arkui-alertdialogparam-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface AlertDialogParamWithOptions extends AlertDialogParam--><!--Device-unnamed-declare interface AlertDialogParamWithOptions extends AlertDialogParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonDirection

```TypeScript
buttonDirection?: DialogButtonDirection
```

按钮排布方向默认为DialogButtonDirection.AUTO。建议3个以上按钮使用Auto模式（两个以上按钮会切换为纵向模式，通常能显示更多按钮）。非Auto模式下，3个以上按钮可能会显示不全，超出显示范围的按钮会被截断。

**类型：** DialogButtonDirection

**默认值：** DialogButtonDirection.AUTO

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogParamWithOptions-buttonDirection?: DialogButtonDirection--><!--Device-AlertDialogParamWithOptions-buttonDirection?: DialogButtonDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons: Array<AlertDialogButtonOptions>
```

弹窗容器中的多个按钮。

**类型：** Array&lt;AlertDialogButtonOptions&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogParamWithOptions-buttons: Array<AlertDialogButtonOptions>--><!--Device-AlertDialogParamWithOptions-buttons: Array<AlertDialogButtonOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

