# IDataSourcePrefetching

用于实现具有预加载能力的LazyForEach数据源。

**继承/实现关系：** IDataSourcePrefetching extends IDataSource<T>

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface IDataSourcePrefetching--><!--Device-unnamed-export declare interface IDataSourcePrefetching-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel(index: int): Promise<void> | undefined
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-IDataSourcePrefetching-cancel(index: int): Promise<void> | undefined--><!--Device-IDataSourcePrefetching-cancel(index: int): Promise<void> | undefined-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; |  |

## prefetch

```TypeScript
prefetch(index: int): Promise<void> | undefined
```

预加载数据源中的指定项。 该方法可以为同步，也可以为异步。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IDataSourcePrefetching-prefetch(index: int): Promise<void> | undefined--><!--Device-IDataSourcePrefetching-prefetch(index: int): Promise<void> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 指定项的序号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; |  |

## default

```TypeScript
default
```

取消指定数据项的预加载。 该方法可以为同步，也可以为异步。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IDataSourcePrefetching-default--><!--Device-IDataSourcePrefetching-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

