# PopoverDialogV2OnVisibleChange

```TypeScript
export declare type PopoverDialogV2OnVisibleChange = (visible: boolean) => void
```

跟手弹出框显示状态改变事件。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare type PopoverDialogV2OnVisibleChange = (visible: boolean) => void--><!--Device-unnamed-export declare type PopoverDialogV2OnVisibleChange = (visible: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| visible | boolean | 是 | 表示跟手弹出框显示状态。<br />值为true时跟手弹出框显示，为false时隐藏。  |

