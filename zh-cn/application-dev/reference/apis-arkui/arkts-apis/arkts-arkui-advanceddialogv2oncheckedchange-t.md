# AdvancedDialogV2OnCheckedChange

```TypeScript
export declare type AdvancedDialogV2OnCheckedChange = (checked: boolean) => void
```

选择框选中状态改变事件。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare type AdvancedDialogV2OnCheckedChange = (checked: boolean) => void--><!--Device-unnamed-export declare type AdvancedDialogV2OnCheckedChange = (checked: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| checked | boolean | 是 | 表示选择框选中状态。<br />checked为true时，表示选择框已选中。checked为false时，表示选择框未选中。  |

