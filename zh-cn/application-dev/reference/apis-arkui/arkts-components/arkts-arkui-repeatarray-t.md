# RepeatArray

```TypeScript
declare type RepeatArray<T> = Array<T> | ReadonlyArray<T> | Readonly<Array<T>>
```

Repeat数据源参数联合类型。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | Regular Regular Regular 常规数组类型。 |
| ReadonlyArray&lt;T&gt; | Read-only Read-only Read-only 只读数组类型，不允许数组对象变更。 |
| Readonly&lt;Array&lt;T&gt;&gt; | Read-only Read-only Read-only 只读数组类型，不允许数组对象变更。 |

