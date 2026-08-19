# RecordData

```TypeScript
type RecordData = undefined | null | Object | Record<string, RecordData> | Array<RecordData>
```

RecordData is used for input parameter obj of the equal function

**起始版本：** 23

<!--Device-preferences-type RecordData = undefined | null | Object | Record<string, RecordData> | Array<RecordData>--><!--Device-preferences-type RecordData = undefined | null | Object | Record<string, RecordData> | Array<RecordData>-End-->

**系统能力：** 
- API版本23+：SystemCapability.DistributedDataManager.Preferences.Core

| 类型 | 说明 |
| --- | --- |
| undefined | 表示类型为未定义。 |
| null | 表示类型为空。 |
| Object | 表示类型为对象。 |
| Record&lt;string, RecordData&gt; | 表示类型为键值对类型。键的类型为string，值的类型为RecordData。 |
| Array&lt;RecordData&gt; | 表示类型为RecordData类型的数组。 |

