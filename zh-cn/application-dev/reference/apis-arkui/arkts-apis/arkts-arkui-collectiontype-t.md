# CollectionType

```TypeScript
export declare type CollectionType<S> = Array<S> | Map<string | number, S> |
  Set<S> | collections.Array<S> | collections.Map<string | number, S> | collections.Set<S>
```

globalConnect的入参泛型，用于定义globalConnect支持的持久化集合数据类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare type CollectionType<S> = Array<S> | Map<string | number, S> |
  Set<S> | collections.Array<S> | collections.Map<string | number, S> | collections.Set<S>--><!--Device-unnamed-export declare type CollectionType<S> = Array<S> | Map<string | number, S> |
  Set<S> | collections.Array<S> | collections.Map<string | number, S> | collections.Set<S>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| Array&lt;S&gt; | 表示值类型为Array类型。 |
| Map&lt;string |  |
| number, S&gt; |  |
| Set&lt;S&gt; | 表示值类型为Set类型。 |
| collections.Array&lt;S&gt; | 表示值类型为collections.Array类型。 |
| collections.Map&lt;string |  |
| number, S&gt; |  |
| collections.Set&lt;S&gt; | 表示值类型为collections.Set类型。 |

