# ArrayElementPredicateFn

```TypeScript
type ArrayElementPredicateFn<ElementType> = (value: ElementType) => boolean
```

ArkTS Array判定函数类型，被Array类的'retainAll'接口使用，用来判断数组元素是否满足测试条件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ElementType | 是 | 当前正在处理的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判定函数的结果，若当前元素满足判定函数则为真，否则为假。 |
