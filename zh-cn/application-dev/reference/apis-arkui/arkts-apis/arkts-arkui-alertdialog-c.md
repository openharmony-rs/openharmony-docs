# AlertDialog

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 26.0.0

**替代接口：** ohos.arkui.UIContext.UIContext#showAlertDialog

<!--Device-unnamed-declare class AlertDialog--><!--Device-unnamed-declare class AlertDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(value: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions)
```

定义警告弹窗并弹出。 > **说明：** showAlertDialog需先获取[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_实例后再进行调用。 > 从API version 10开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_中的 > [showAlertDialog]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_来明确UI的执行上下文。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 18

**替代接口：** ohos.arkui.UIContext.UIContext#showAlertDialog

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialog-static show(value: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions)--><!--Device-AlertDialog-static show(value: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| AlertDialogParamWithButtons \| AlertDialogParamWithOptions | 是 | 定义并显示AlertDialog组件。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 10 |

