# registerFont

## registerFont

```TypeScript
function registerFont(options: FontOptions): void
```

在字体管理中注册自定义字体。 该接口为异步接口，不支持并发调用。 > **说明：** > > -registerFont需要先通过[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_方法获取 > [Font]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_对象，然后通过该对象进行调用。且直接使用registerFont可能导致 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_的问题。 > > - 从API version 10开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_方法获取当前UI上下文关联的 > [Font]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_对象。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 18

**替代接口：** ohos.arkui.UIContext.Font#registerFont

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-font-function registerFont(options: FontOptions): void--><!--Device-font-function registerFont(options: FontOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 注册的自定义字体信息。 |

