# AnimatableArithmetic

该接口定义非number数据类型的动画运算规则。对非number类型的数据（如数组、结构体、颜色等）做动画，需要实现AnimatableArithmetic\<T\>接口中加法、减法、乘法和判断相等函数，使得该数据能参与动画的插值运算和识别该数据是否发生改变。即定义它们为实现了AnimatableArithmetic\<T\>接口的类型。

**起始版本：** 10

<!--Device-unnamed-declare interface AnimatableArithmetic<T>--><!--Device-unnamed-declare interface AnimatableArithmetic<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## equals

```TypeScript
equals(rhs: AnimatableArithmetic<T>): boolean
```

定义该数据类型的相等判断规则。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatableArithmetic-equals(rhs: AnimatableArithmetic<T>): boolean--><!--Device-AnimatableArithmetic-equals(rhs: AnimatableArithmetic<T>): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rhs | [AnimatableArithmetic](arkts-arkui-common-animatablearithmetic-i.md)<T> | 是 | 和自身比较相等的另一个数据对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否相等。返回true表示相等，返回false表示不相等。 |

## multiply

```TypeScript
multiply(scale: number): AnimatableArithmetic<T>
```

定义该数据类型的乘法运算规则。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatableArithmetic-multiply(scale: number): AnimatableArithmetic<T>--><!--Device-AnimatableArithmetic-multiply(scale: number): AnimatableArithmetic<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | 乘法运算的系数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatableArithmetic](arkts-arkui-common-animatablearithmetic-i.md)<T> | 乘法运算的结果。 |

## plus

```TypeScript
plus(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>
```

定义数据类型的加法运算规则。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatableArithmetic-plus(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>--><!--Device-AnimatableArithmetic-plus(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rhs | [AnimatableArithmetic](arkts-arkui-common-animatablearithmetic-i.md)<T> | 是 | 加法运算的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatableArithmetic](arkts-arkui-common-animatablearithmetic-i.md)<T> | 加法运算的结果。 |

## subtract

```TypeScript
subtract(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>
```

定义该数据类型的减法运算规则。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatableArithmetic-subtract(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>--><!--Device-AnimatableArithmetic-subtract(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rhs | [AnimatableArithmetic](arkts-arkui-common-animatablearithmetic-i.md)<T> | 是 | 减法运算的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatableArithmetic](arkts-arkui-common-animatablearithmetic-i.md)<T> | 减法运算的结果。 |

