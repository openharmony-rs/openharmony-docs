# BatchUpdateFn（系统接口）

```TypeScript
type BatchUpdateFn = (
  operations: Record<string, Array<UpdateOperation>>,
  callback: AsyncCallback<Record<string, Array<int>>>
) => void
```

批量更新操作的属性类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type BatchUpdateFn = (  operations: Record<string, Array<UpdateOperation>>,  callback: AsyncCallback<Record<string, Array<int>>>) => void--><!--Device-unnamed-type BatchUpdateFn = (  operations: Record<string, Array<UpdateOperation>>,  callback: AsyncCallback<Record<string, Array<int>>>) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operations | Record&lt;string, Array&lt;[UpdateOperation](arkts-arkdata-updateoperation-t-sys.md)&gt;&gt; | 是 | Indicates the data to update. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Record&lt;string, Array&lt;int&gt;&gt;&gt; | 是 | Callback used to return the result. |

