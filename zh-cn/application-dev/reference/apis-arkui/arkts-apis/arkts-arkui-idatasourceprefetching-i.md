# IDataSourcePrefetching

继承自[IDataSource](../arkts-components/arkts-arkui-idatasource-i.md)。实现该接口，提供具备预取能力的DataSource。

**继承/实现关系：** IDataSourcePrefetching extends [IDataSource](../arkts-components/arkts-arkui-idatasource-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel?(index: number): Promise<void> | void
```

取消从数据集中预取指定的元素。该方法可以为同步，也可为异步。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 取消预取数据项索引值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise when this API is executed asynchronously; no return value when this APIis executed synchronously. The promise only indicates that the operation is completed and contains no actualreturn content. |

## prefetch

```TypeScript
prefetch(index: number): Promise<void> | void
```

从数据集中预取指定的元素。该方法可以为同步，也可为异步。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 预取数据项索引值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise when this API is executed asynchronously; no return value when this APIis executed synchronously. The promise only indicates that the operation is completed and contains no actualreturn content. |

