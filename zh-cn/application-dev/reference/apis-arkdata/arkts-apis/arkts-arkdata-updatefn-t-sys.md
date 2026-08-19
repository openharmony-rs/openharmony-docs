# UpdateFn（系统接口）

```TypeScript
type UpdateFn = (
  uri: string,
  predicates: dataSharePredicates.DataSharePredicates,
  valueBucket: ValuesBucket,
  callback: AsyncCallback<int>
) => void
```

更新操作的属性类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type UpdateFn = (  uri: string,  predicates: dataSharePredicates.DataSharePredicates,  valueBucket: ValuesBucket,  callback: AsyncCallback<int>) => void--><!--Device-unnamed-type UpdateFn = (  uri: string,  predicates: dataSharePredicates.DataSharePredicates,  valueBucket: ValuesBucket,  callback: AsyncCallback<int>) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Indicates the database table storing the data to update. |
| predicates | dataSharePredicates.DataSharePredicates | 是 | Indicates filter criteria. If this parameter is null, all data records will be updated by default. |
| valueBucket | [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | 是 | Indicates the data to update. This parameter can be null. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | Returns the number of data records updated. |

