# DecimalConfig

提供Decimal的配置属性，可使用Decimal.set方法进行配置。

**起始版本：** 12

<!--Device-unnamed-export interface DecimalConfig--><!--Device-unnamed-export interface DecimalConfig-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { Decimal } from '@kit.ArkTS';
```

## crypto

```TypeScript
crypto?: boolean
```

确定是否使用加密安全伪随机数生成的值。默认值：false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecimalConfig-crypto?: boolean--><!--Device-DecimalConfig-crypto?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## defaults

```TypeScript
defaults?: boolean
```

表示未指定的属性是否被设置为默认值，true表示使用默认值。默认值：false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecimalConfig-defaults?: boolean--><!--Device-DecimalConfig-defaults?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## maxE

```TypeScript
maxE?: number
```

正指数极限，若Decimal的指数值大于该值，会溢出至无穷大。默认值：9e15。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecimalConfig-maxE?: double--><!--Device-DecimalConfig-maxE?: double-End-->

**系统能力：** SystemCapability.Utils.Lang

## minE

```TypeScript
minE?: number
```

负指数极限，若Decimal的指数值小于该值，会下溢到零。默认值：-9e15。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecimalConfig-minE?: double--><!--Device-DecimalConfig-minE?: double-End-->

**系统能力：** SystemCapability.Utils.Lang

## modulo

```TypeScript
modulo?: Modulo
```

模计算时使用的舍入模式，即计算a mod n时的舍入模式。默认值：1（ROUND_DOWN）。

**类型：** Modulo

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecimalConfig-modulo?: Modulo--><!--Device-DecimalConfig-modulo?: Modulo-End-->

**系统能力：** SystemCapability.Utils.Lang

## precision

```TypeScript
precision?: number
```

运算结果的最大有效位数。默认值：20。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecimalConfig-precision?: double--><!--Device-DecimalConfig-precision?: double-End-->

**系统能力：** SystemCapability.Utils.Lang

## rounding

```TypeScript
rounding?: Rounding
```

舍入模式，用于将运算结果舍入到precision位有效数字，以及作为round、toBinary、toDecimalPlaces、toExponential、toFixed、toHexadecimal、toNearest、toOctal、toPrecision和toSignificantDigits方法返回值的默认舍入模式。默认值：4（ROUND_HALF_UP）。

**类型：** Rounding

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecimalConfig-rounding?: Rounding--><!--Device-DecimalConfig-rounding?: Rounding-End-->

**系统能力：** SystemCapability.Utils.Lang

## toExpNeg

```TypeScript
toExpNeg?: number
```

指数表示法的负指数值的极限值，若Decimal的负指数小于等于该值时，使用科学计数法表示。默认值：-7。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecimalConfig-toExpNeg?: double--><!--Device-DecimalConfig-toExpNeg?: double-End-->

**系统能力：** SystemCapability.Utils.Lang

## toExpPos

```TypeScript
toExpPos?: number
```

指数表示法的正指数值的极限值，若Decimal的正指数大于等于该值时，使用科学计数法表示。默认值：21。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecimalConfig-toExpPos?: double--><!--Device-DecimalConfig-toExpPos?: double-End-->

**系统能力：** SystemCapability.Utils.Lang

