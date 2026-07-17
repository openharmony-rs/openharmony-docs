# IndexChangedHandler

```TypeScript
declare type IndexChangedHandler = (index: number) => void
```

当前显示元素的索引变化时，告知应用。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type IndexChangedHandler = (index: number) => void--><!--Device-unnamed-declare type IndexChangedHandler = (index: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 当前显示元素的索引。index序列从0开始。 |

