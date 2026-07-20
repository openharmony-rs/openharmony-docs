# OnSelectedIndexesChange

```TypeScript
export type OnSelectedIndexesChange = (selectedIndexes: number[]) => void
```

多选分段按钮选中项变更时调用的回调函数类型。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type OnSelectedIndexesChange = (selectedIndexes: number[]) => void--><!--Device-unnamed-export type OnSelectedIndexesChange = (selectedIndexes: number[]) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedIndexes | number[] | 是 | 分段按钮选项下标集合。  |

