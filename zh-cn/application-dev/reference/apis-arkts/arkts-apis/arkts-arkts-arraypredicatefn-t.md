# ArrayPredicateFn

```TypeScript
type ArrayPredicateFn<ElementType, ArrayType> =
    (value: ElementType, index: number, array: ArrayType) => boolean
```

ArkTS Array归约函数类型，被Array类的'some'和'every'接口使用，用来判断数组元素是否满足测试条件。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ElementType | 是 | 当前正在处理的元素。 |
| index | number | 是 | 当前遍历的ArkTS Array元素索引。 |
| array | ArrayType | 是 | 当前遍历的ArkTS Array本身。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 归约函数的结果，该结果作为判断当前元素是否通过测试条件。为true时表示当前或之前的某个元素已满足条件，为false时表示尚未找到符合条件的元素。 |

