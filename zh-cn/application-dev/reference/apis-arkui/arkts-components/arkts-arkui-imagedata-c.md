# ImageData

ImageData对象可以存储canvas渲染的像素数据。

> **说明：**  
>  
> 创建ImageData时，宽高不超过16384px，最大面积不超过16000px*16000px，超过最大面积则无法正常绘制。  
> 当创建面积超过536870911px时，返回值的width和height均为0px，data为undefined。

**起始版本：** 8

<!--Device-unnamed-declare class ImageData--><!--Device-unnamed-declare class ImageData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(width: number, height: number, data?: Uint8ClampedArray)
```

创建宽为width，高为height，像素为data的ImageData，如果data未定义，则填充值全为0的一维数组。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageData-constructor(width: number, height: number, data?: Uint8ClampedArray)--><!--Device-ImageData-constructor(width: number, height: number, data?: Uint8ClampedArray)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 矩形区域宽度，默认单位为vp。<br>异常值NaN和Infinity按0处理。 |
| height | number | 是 | 矩形区域高度，默认单位为vp。<br>异常值NaN和Infinity按0处理。 |
| data | [Uint8ClampedArray](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8clampedarray-c.md) | 否 | 一维数组，保存了相应的颜色数据，数据值范围为0到255。<br>传入异常值undefined时，data为undefined。<br/>默认值：值全为0的一维数组。 |

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(width: number, height: number, data?: Uint8ClampedArray, unit?: LengthMetricsUnit)
```

创建宽为width，高为height，像素为data的ImageData，如果data未定义，则填充值全为0的一维数组，支持使用unit配置ImageData对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageData-constructor(width: number, height: number, data?: Uint8ClampedArray, unit?: LengthMetricsUnit)--><!--Device-ImageData-constructor(width: number, height: number, data?: Uint8ClampedArray, unit?: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 矩形区域宽度，默认单位为vp。<br>异常值NaN和Infinity按0处理。 |
| height | number | 是 | 矩形区域高度，默认单位为vp。<br>异常值NaN和Infinity按0处理。 |
| data | [Uint8ClampedArray](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8clampedarray-c.md) | 否 | 一维数组，保存了相应的颜色数据，数据值范围为0到255。<br>传入异常值undefined时，data为undefined。<br/>默认值：值全为0的一维数组。 |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-graphics-lengthmetricsunit-e.md) | 否 | 用来配置ImageData对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](docroot://reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。<br>异常值undefined、NaN和Infinity按默认值处理。<br>默认值：DEFAULT。 |

## data

```TypeScript
readonly data: Uint8ClampedArray
```

一维数组，保存了相应的颜色数据，数据值范围为0到255。

**类型：** Uint8ClampedArray

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageData-readonly data: Uint8ClampedArray--><!--Device-ImageData-readonly data: Uint8ClampedArray-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
readonly height: number
```

矩形区域实际像素高度。<br>单位为px。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageData-readonly height: number--><!--Device-ImageData-readonly height: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
readonly width: number
```

矩形区域实际像素宽度。<br>单位为px。

> **说明：**  
>  
> 可使用[px2vp](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#px2vp12)  
> 接口进行单位转换。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageData-readonly width: number--><!--Device-ImageData-readonly width: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

