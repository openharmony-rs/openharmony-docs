# getParams

## getParams

```TypeScript
function getParams(): Object
```

获取发起跳转的页面往当前页传入的参数。 > **说明：** > > - 从API version 8开始支持，从API version 18开始废弃，建议使用[getParams]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_替代。 > getParams需先通过[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_获取 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_实例，然后通过该实例进行调用。 > > - 从API version 10开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_方法获取当前UI上下文关联的 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_对象。 > > getParams只获取当前页面的参数，并不会清除页面关联的参数。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 18

**替代接口：** [@ohos.arkui.UIContext:Router#getParams](arkts-arkui-arkui-uicontext-router-c.md#getparams)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function getParams(): Object--><!--Device-router-function getParams(): Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 发起跳转的页面往当前页传入的参数。 |

**示例：**

```TypeScript
this.getUIContext().getRouter().getParams();
```

