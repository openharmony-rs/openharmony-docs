# ColorMetrics

用于混合颜色。

**起始版本：** 12

<!--Device-unnamed-declare class ColorMetrics--><!--Device-unnamed-declare class ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## createHDRColor

```TypeScript
static createHDRColor(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

使用默认曝光的HDR颜色创建ColorMetrics类。使用默认曝光（0.0表示对数，1.0表示线性）创建HDR颜色值。当没有指定曝光值时，RGB通道值可以超过1.0以实现HDR亮度。这与iOS UIColor行为匹配，其中RGB值> 1.0启用HDR渲染。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static createHDRColor(colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics--><!--Device-ColorMetrics-static createHDRColor(colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | [ColorSpace](arkts-arkui-window-colorspace-e.md) | 是 | 颜色的颜色空间。支持SRGB、Display_P3、BT2020颜色空间。 |
| red | number | 是 | 红色分量值。有效范围：[0, +∞)。大于1.0的值启用HDR亮度。 |
| green | number | 是 | 绿色分量值。有效范围：[0, +∞)。大于1.0的值启用HDR亮度。 |
| blue | number | 是 | 蓝色分量值。有效范围：[0, +∞)。大于1.0的值启用HDR亮度。 |
| alpha | number | 否 | Alpha（不透明度）分量值。有效范围：【0,1】。默认值为1.0（完全不透明）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c-sys.md) | ColorMetrics class instance with HDR color. |

## createHDRColorWithLinearExposure

```TypeScript
static createHDRColorWithLinearExposure(linearExposure: number, colorSpace: ColorSpace,
    red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

使用具有线性曝光的HDR颜色创建ColorMetrics类。创建具有指定线性曝光的HDR颜色值。曝光值控制线性色彩空间中颜色的亮度。使用线性曝光时，RGB通道值通常在【0,1】范围内。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static createHDRColorWithLinearExposure(linearExposure: double, colorSpace: ColorSpace,
    red: double, green: double, blue: double, alpha?: double): ColorMetrics--><!--Device-ColorMetrics-static createHDRColorWithLinearExposure(linearExposure: double, colorSpace: ColorSpace,
    red: double, green: double, blue: double, alpha?: double): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| linearExposure | number | 是 | 曝光值中的线性曝光值。值为1.0表示标准曝光。大于1.0的值会线性增加亮度。 |
| colorSpace | [ColorSpace](arkts-arkui-window-colorspace-e.md) | 是 | 颜色的颜色空间。支持SRGB、Display_P3、BT2020颜色空间。 |
| red | number | 是 | 红色分量值。有效范围：【0,1】。 |
| green | number | 是 | 绿色分量值。有效范围：【0,1】。 |
| blue | number | 是 | 蓝色分量值。有效范围：【0,1】。 |
| alpha | number | 否 | Alpha（不透明度）分量值。有效范围：【0,1】。默认值为1.0（完全不透明）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c-sys.md) | 带有HDR颜色的ColorMetrics类实例。 |

## createHDRColorWithLogExposure

```TypeScript
static createHDRColorWithLogExposure(exposure: number, colorSpace: ColorSpace,
    red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

使用具有对数曝光的HDR颜色创建ColorMetrics类。使用指定的对数曝光（色度）创建HDR颜色值。曝光值控制对数（感知）色彩空间中的亮度。使用对数曝光时，RGB通道值通常在【0,1】范围内。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static createHDRColorWithLogExposure(exposure: double, colorSpace: ColorSpace,
    red: double, green: double, blue: double, alpha?: double): ColorMetrics--><!--Device-ColorMetrics-static createHDRColorWithLogExposure(exposure: double, colorSpace: ColorSpace,
    red: double, green: double, blue: double, alpha?: double): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exposure | number | 是 | 对数曝光值，单位为秒。有效范围：[0, +∞)。值0.0表示标准曝光。每增加1.0将使亮度加倍（一次停止）。 |
| colorSpace | [ColorSpace](arkts-arkui-window-colorspace-e.md) | 是 | 颜色的颜色空间。支持SRGB、Display_P3、BT2020颜色空间。 |
| red | number | 是 | 红色分量值。有效范围：【0,1】。 |
| green | number | 是 | 绿色分量值。有效范围：【0,1】。 |
| blue | number | 是 | 蓝色分量值。有效范围：【0,1】。 |
| alpha | number | 否 | Alpha（不透明度）分量值。有效范围：【0,1】。默认值为1.0（完全不透明）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c-sys.md) | ColorMetrics class instance with HDR color. |

## getBlueValue

```TypeScript
getBlueValue(): number
```

获取蓝色值。以浮点数形式返回蓝色通道值。对于SDR颜色，值在【0,1】范围内。对于HDR颜色，值可以大于1.0以表示扩展亮度。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-getBlueValue(): double--><!--Device-ColorMetrics-getBlueValue(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 蓝色值。有效范围：对于SDR颜色：【0,1】。HDR颜色：[0,+∞),&gt;1.0表示HDR亮度。 |

## getColorSpace

```TypeScript
getColorSpace(): ColorSpace
```

获取ColorMetrics的颜色空间。返回创建此颜色时使用的颜色空间。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-getColorSpace(): ColorSpace--><!--Device-ColorMetrics-getColorSpace(): ColorSpace-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorSpace](arkts-arkui-window-colorspace-e.md) | The color space of the ColorMetrics.Possible value: ColorSpace.SRGB, ColorSpace.DISPLAY_P3, ColorSpace.BT2020. |

## getGreenValue

```TypeScript
getGreenValue(): number
```

获取绿色值。以浮点数形式返回绿色通道值。对于SDR颜色，值在【0,1】范围内。对于HDR颜色，值可以大于1.0以表示扩展亮度。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-getGreenValue(): double--><!--Device-ColorMetrics-getGreenValue(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 绿色的值。有效范围：对于SDR颜色：【0,1】。HDR颜色：[0,+∞),&gt;1.0表示HDR亮度。 |

## getRedValue

```TypeScript
getRedValue(): number
```

获取红色值。以浮点数形式返回红色通道值。对于SDR颜色，值在【0,1】范围内。对于HDR颜色，值可以大于1.0以表示扩展亮度。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-getRedValue(): double--><!--Device-ColorMetrics-getRedValue(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 红色的值。有效范围：对于SDR颜色：【0,1】。HDR颜色：[0,+∞),&gt;1.0表示HDR亮度。 |

## isHDR

```TypeScript
isHDR(): boolean
```

检查ColorMetrics是否代表HDR颜色。如果颜色是使用createHDRColorWithXx创建的，或者RGB值> 1.0，则返回true。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-isHDR(): boolean--><!--Device-ColorMetrics-isHDR(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ColorMetrics是否是HDR颜色。如果满足以下条件，则返回true：  -颜色是使用createHDRColorWithXx()方法创建的。  -任何RGB通道值都大于1.0。 |

