# RecordData

```TypeScript
export type RecordData = undefined | null | Object | Record<string, RecordData> | Array<RecordData>
```

RecordData 是一个联合类型，用于层级和每层数量都不确定的对象结构。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type RecordData = undefined | null | Object | Record<string, RecordData> | Array<RecordData>--><!--Device-unnamed-export type RecordData = undefined | null | Object | Record<string, RecordData> | Array<RecordData>-End-->

**系统能力：** SystemCapability.Base

| 类型 | 说明 |
| --- | --- |
| undefined | 未定义类型。 |
| null | 空类型。 |
| Object | 对象类型。 |
| Record&lt;string, RecordData&gt; | 带有字符串键和RecordData值的记录类型。 |
| Array&lt;RecordData&gt; | 包含RecordData元素的数组类型。 |

