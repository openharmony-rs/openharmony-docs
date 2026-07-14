# ArrayFromMapFn

```TypeScript
type ArrayFromMapFn<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType
```

ArkTS Array归约函数类型，被Array类的'from'接口使用。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | FromElementType | 是 | 当前正在处理的元素。 |
| index | number | 是 | 当前遍历的ArkTS Array元素索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ToElementType | 归约函数的结果，该结果会作为数组的新元素。 |

