# InsertFn（系统接口）

```TypeScript
type InsertFn = (uri: string, valueBucket: ValuesBucket, callback: AsyncCallback<int>) => void
```

插入操作的属性类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type InsertFn = (uri: string, valueBucket: ValuesBucket, callback: AsyncCallback<int>) => void--><!--Device-unnamed-type InsertFn = (uri: string, valueBucket: ValuesBucket, callback: AsyncCallback<int>) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Indicates the position where the data is to insert.  |
| valueBucket | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates the data to insert.  |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | Returns the index of the newly inserted data record.  |

