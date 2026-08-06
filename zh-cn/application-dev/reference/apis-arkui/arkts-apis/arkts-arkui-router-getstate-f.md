# getState

## getState

```TypeScript
function getState(): RouterState
```

获取栈顶页面的状态信息。 > **说明：** > > - 从API version 8开始支持，从API version 18开始废弃，建议使用[getState]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_替代。getLength需 > 先通过[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_获取 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_实例，然后通过该实例进行调用。 > > - 从API version 10开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_方法获取当前UI上下文关联的 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_对象。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 18

**替代接口：** [@ohos.arkui.UIContext:Router#getState](arkts-arkui-arkui-uicontext-router-c.md#getstate)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function getState(): RouterState--><!--Device-router-function getState(): RouterState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 栈顶页面的状态信息，包含页面索引、名称、路径和参数。 |

**示例：**

```TypeScript
let page = this.getUIContext().getRouter().getState();
console.info('current index = ' + page.index);
console.info('current name = ' + page.name);
console.info('current path = ' + page.path);
```

