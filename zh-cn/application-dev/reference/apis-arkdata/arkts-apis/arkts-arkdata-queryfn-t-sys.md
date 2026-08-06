# QueryFn（系统接口）

```TypeScript
type QueryFn = (
  uri: string,
  predicates: dataSharePredicates.DataSharePredicates,
  columns: Array<string>,
  callback: AsyncCallback<Object>
) => void
```

查询操作的属性类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type QueryFn = (  uri: string,  predicates: dataSharePredicates.DataSharePredicates,  columns: Array<string>,  callback: AsyncCallback<Object>) => void--><!--Device-unnamed-type QueryFn = (  uri: string,  predicates: dataSharePredicates.DataSharePredicates,  columns: Array<string>,  callback: AsyncCallback<Object>) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Indicates the database table storing the data to query.  |
| predicates | dataSharePredicates.DataSharePredicates | 是 | Indicates filter criteria. If this parameter is null, all data records will be queried by default.  |
| columns | Array&lt;string&gt; | 是 | Indicates the columns to be queried, in array, for example, {"name","age"}. You should define the processing logic when this parameter is null.  |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Object&gt; | 是 | Returns the queried data, only support result set of rdb or kvstore.  |

