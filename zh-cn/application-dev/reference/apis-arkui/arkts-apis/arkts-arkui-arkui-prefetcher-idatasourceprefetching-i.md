# IDataSourcePrefetching(Prefetching)

继承自IDataSource。实现该接口，提供具备预取能力的数据源。

**继承/实现关系：** IDataSourcePrefetching extends IDataSource

**起始版本：** 12

<!--Device-unnamed-export interface IDataSourcePrefetching--><!--Device-unnamed-export interface IDataSourcePrefetching-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IDataSourcePrefetching, IPrefetcher, BasicPrefetcher } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel?(index: number): Promise<void> | void
```

取消从数据集中预取指定的数据项。该方法可以为同步，也可为异步。该方法为可选方法，若数据源未实现该方法，则不执行取消预取操作。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IDataSourcePrefetching-cancel?(index: number): Promise<void> | void--><!--Device-IDataSourcePrefetching-cancel?(index: number): Promise<void> | void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 取消预取数据项索引值，取值范围为[0, totalCount()-1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异步执行时返回Promise对象，同步执行时无返回值。Promise仅表示操作完成，无实际返回内容。 |

## prefetch

```TypeScript
prefetch(index: number): Promise<void> | void
```

从数据集中预取指定的数据项。该方法可以为同步，也可为异步。当可见区域发生变化时，预取算法判断即将进入可见区域的数据项需要预取时，会调用该方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IDataSourcePrefetching-prefetch(index: number): Promise<void> | void--><!--Device-IDataSourcePrefetching-prefetch(index: number): Promise<void> | void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 预取数据项索引值，取值范围为[0, totalCount()-1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异步执行时返回Promise对象，同步执行时无返回值。Promise仅表示操作完成，无实际返回内容。 |

