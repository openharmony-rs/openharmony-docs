# hideAlertBeforeBackPage

## hideAlertBeforeBackPage

```TypeScript
function hideAlertBeforeBackPage(): void
```

禁用页面返回询问对话框。调用此方法后，将关闭由\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 开启的返回询问对话框，\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_操作将不再弹出确认对话框，直接执行页面返回。 > **说明：** > > - 从API version 9开始支持，从API version 18开始废弃，建议使用 > [hideAlertBeforeBackPage]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_替代。hideAlertBeforeBackPage需先 > 通过[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_获取 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_实例，然后通过该实例进行调用。 > > - 从API version 10开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_方法获取当前UI上下文关联的 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_对象。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 18

**替代接口：** [@ohos.arkui.UIContext:Router#hideAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#hidealertbeforebackpage)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function hideAlertBeforeBackPage(): void--><!--Device-router-function hideAlertBeforeBackPage(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```TypeScript
this.getUIContext().getRouter().hideAlertBeforeBackPage();
```

