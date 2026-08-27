# ArrayFromMapFn

```TypeScript
type ArrayFromMapFn<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType
```

ArkTS Array映射函数类型，被Array类的'from'接口使用。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | FromElementType | 是 | 当前遍历的ArkTS Array元素，用于映射转换为新的数组元素。 |
| index | number | 是 | 当前遍历的ArkTS Array元素索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ToElementType | 映射函数的结果，该结果会作为数组的新元素。 |
