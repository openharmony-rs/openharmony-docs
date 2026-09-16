# ImageData

ImageData对象用于存储Canvas渲染的像素数据，支持对像素进行读取、修改和操作，适用于图像处理、像素级编辑、特效滤镜等场景。通过ImageData可以精确控制图像的每个像素点，实现自定义图像处理算法，为Canvas绘图提供灵活的像素级数据访问能力。

> **说明：** 
> 
> 创建ImageData时，宽高不超过16384px，最大面积不超过16000px*16000px，超过最大面积则无法正常绘制。
> 当创建面积超过536870911px时，返回值的width和height均为0px，data为undefined。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(width: number, height: number, data?: Uint8ClampedArray)
```

创建宽为width，高为height，像素为data的ImageData，如果data未定义，则填充值全为0的一维数组。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 矩形区域宽度，单位由unit参数决定，默认单位为vp。宽高不超过16384px，最大面积不超过16000px*16000px，超过最大面积则无法正常绘制。当创建面积超过536870911平方像素时，返回对象的width和height为0，data为undefined。<br>异常值NaN、Infinity、负数和0按0处理。 |
| height | number | 是 | 矩形区域高度，单位由unit参数决定，默认单位为vp。宽高不超过16384px，最大面积不超过16000px*16000px，超过最大面积则无法正常绘制。当创建面积超过536870911平方像素时，返回对象的width和height为0，data为undefined。<br>异常值NaN、Infinity、负数和0按0处理。 |
| data | [Uint8ClampedArray](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8clampedarray-c.md) | 否 | 一维数组，保存了RGBA格式的像素数据，每个像素占4字节，依次为R、G、B、A，数据值范围为0到255。当需要自定义ImageData的像素数据时传入此参数，如需要对图像进行像素级别的处理或修改。<br>传入异常值undefined时，data为undefined。<br>默认值：值全为0的一维数组。 |

## constructor

```TypeScript
constructor(width: number, height: number, data?: Uint8ClampedArray, unit?: LengthMetricsUnit)
```

创建宽为width，高为height，像素为data的ImageData，如果data未定义，则填充值全为0的一维数组，支持使用unit配置ImageData对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 矩形区域宽度，单位由unit参数决定，默认单位为vp。宽高不超过16384px，最大面积不超过16000px*16000px，超过最大面积则无法正常绘制。当创建面积超过536870911平方像素时，返回对象的width和height为0，data为undefined。<br>异常值NaN、Infinity、负数和0按0处理。 |
| height | number | 是 | 矩形区域高度，单位由unit参数决定，默认单位为vp。宽高不超过16384px，最大面积不超过16000px*16000px，超过最大面积则无法正常绘制。当创建面积超过536870911平方像素时，返回对象的width和height为0，data为undefined。<br>异常值NaN、Infinity、负数和0按0处理。 |
| data | [Uint8ClampedArray](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8clampedarray-c.md) | 否 | 一维数组，保存了RGBA格式的像素数据，每个像素占4字节，依次为R、G、B、A，数据值范围为0到255。当需要自定义ImageData的像素数据时传入此参数，如需要对图像进行像素级别的处理或修改。 |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | 否 | 用来配置ImageData对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md)。当需要使用vp单位实现响应式布局或适配不同屏幕密度时传入此参数。<br>异常值undefined、NaN和Infinity按默认值处理。<br>默认值：DEFAULT。 |

## data

```TypeScript
readonly data: Uint8ClampedArray
```

一维数组，保存了RGBA格式的像素数据，每个像素占4字节，依次为R、G、B、A，数据值范围为0到255。  
> **说明：** 
> 
> 可使用px2vp
> 接口进行单位转换。

**类型：** [Uint8ClampedArray](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8clampedarray-c.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
readonly height: number
```

矩形区域实际像素高度。<br>单位为px。  
> **说明：** 
> 
> 可使用px2vp
> 接口进行单位转换。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
readonly width: number
```

矩形区域实际像素宽度。<br>单位为px。

> **说明：** 
> 
> 可使用px2vp
> 接口进行单位转换。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
