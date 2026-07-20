# ActionSheet

**起始版本：** 8

**废弃版本：** 26.0.0

**替代接口：** showActionSheet

<!--Device-unnamed-declare class ActionSheet--><!--Device-unnamed-declare class ActionSheet-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="show"></a>
## show

```TypeScript
static show(value: ActionSheetOptions)
```

定义列表弹窗并弹出。

> **说明：**

showActionSheet需先获取[UIContext](arkts-arkui-uicontext.md)实例后再进行调用。

> 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [showActionSheet](arkts-arkui-arkui-uicontext-uicontext-c.md#showactionsheet-1)来明确UI的执行上下文。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** showActionSheet

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ActionSheet-static show(value: ActionSheetOptions)--><!--Device-ActionSheet-static show(value: ActionSheetOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) | 是 | 配置列表选择弹窗的参数。 |

