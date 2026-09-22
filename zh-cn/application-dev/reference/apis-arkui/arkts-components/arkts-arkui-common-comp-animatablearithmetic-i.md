# AnimatableArithmetic

```TypeScript
declare interface AnimatableArithmetic<T>
```

该接口定义非number数据类型的动画运算规则。对非number类型的数据（如数组、结构体、颜色等）做动画，需要实现AnimatableArithmetic\&lt;T\&gt;接口中加法、减法、乘法和判断相等函数，使得该数据能参与动画的插值运算和识别该数据是否发生改变。即定义它们为实现了AnimatableArithmetic\&lt;T\&gt;接口的类型。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## equals

```TypeScript
equals(rhs: AnimatableArithmetic<T>): boolean
```

定义该数据类型的相等判断规则，在动画过程中用于识别数据是否发生改变，若当前值与目标值相等则不再触发动画过渡。需与AnimatableArithmetic\&lt;T\&gt;接口的其他方法一同实现，才能使自定义数据类型参与动画的插值运算。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rhs | [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | 是 | 与当前对象判断是否相等的另一个数据对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否相等。返回true表示相等，返回false表示不相等。 |

## multiply

```TypeScript
multiply(scale: number): AnimatableArithmetic<T>
```

定义该数据类型的乘法运算规则，在动画插值运算中用于按动画进度比例（0到1之间）对差值进行缩放，缩放后的差值将通过plus运算加到起始值上。需与AnimatableArithmetic\&lt;T\&gt;接口的其他方法一同实现，才能使自定义数据类型参与动画的插值运算。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | 乘法运算的系数，取值范围为[0, +∞)，动画插值时典型取值范围为[0, 1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | 乘法运算的结果，用于动画插值过程中按系数缩放数据以计算中间帧数据。 |

## plus

```TypeScript
plus(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>
```

定义该数据类型的加法运算规则。需与AnimatableArithmetic\&lt;T\&gt;接口的其他方法一同实现，才能使自定义数据类型参与动画的插值运算。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rhs | [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | 是 | 与自身进行加法运算的另一个数据对象，应与当前对象为相同的具体类型实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | 加法运算的结果，用于动画插值过程中计算两个数据之间的中间值。 |

## subtract

```TypeScript
subtract(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>
```

定义该数据类型的减法运算规则，在动画插值运算中用于计算起始值与目标值之间的差值，差值将作为乘法运算的输入。需与AnimatableArithmetic\&lt;T\&gt;接口的其他方法一同实现，才能使自定义数据类型参与动画的插值运算。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rhs | [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | 是 | 与自身进行减法运算的另一个数据对象，应与当前对象为相同的具体类型实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | 减法运算的结果，用于动画插值过程中计算数据差值以得到中间帧数据。 |
