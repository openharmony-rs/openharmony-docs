# ColorMetrics

```TypeScript
declare class ColorMetrics
```

Used to mix colors.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## createHDRColor

```TypeScript
static createHDRColor(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

Create ColorMetrics class using HDR color with default exposure. Create an HDR color value with default exposure (0.0 for logarithmic, 1.0 for linear). When no exposure value is specified, RGB channel values can exceed 1.0 to achieve HDR brightness. This matches iOS UIColor behavior where RGB values &gt; 1.0 enable HDR rendering.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorSpace | ColorSpace | Yes | Color space of color. Supports SRGB, DISPLAY_P3, and BT2020 color spaces. |
| red | number | Yes | Red component value. Valid range: [0, +∞). Values greater than 1.0 enable HDR brightness. |
| green | number | Yes | Green component value. Valid range: [0, +∞). Values greater than 1.0 enable HDR brightness. |
| blue | number | Yes | Blue component value. Valid range: [0, +∞). Values greater than 1.0 enable HDR brightness. |
| alpha | number | No | Alpha (opacity) component value. Valid range: [0, 1]. The default value is 1.0 (fully opaque). |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics class instance with HDR color. |

## createHDRColorWithLinearExposure

```TypeScript
static createHDRColorWithLinearExposure(linearExposure: number, colorSpace: ColorSpace,
    red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

Create ColorMetrics class using HDR color with linear exposure. Create an HDR color value with specified linear exposure. The exposure value controls the brightness of the color in a linear color space. When using linear exposure, RGB channel values are typically in the range [0, 1].

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| linearExposure | number | Yes | Linear exposure value in exposure value. Valid range: [1, +∞). A value of 1.0 represents standard exposure. Values greater than 1.0 increase brightness linearly. |
| colorSpace | ColorSpace | Yes | Color space of color. Supports SRGB, DISPLAY_P3, and BT2020 color spaces. |
| red | number | Yes | Red component value. Valid range: [0, 1]. |
| green | number | Yes | Green component value. Valid range: [0, 1]. |
| blue | number | Yes | Blue component value. Valid range: [0, 1]. |
| alpha | number | No | Alpha (opacity) component value. Valid range: [0, 1]. The default value is 1.0 (fully opaque). |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics class instance with HDR color. |

## createHDRColorWithLogExposure

```TypeScript
static createHDRColorWithLogExposure(exposure: number, colorSpace: ColorSpace,
    red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

Create ColorMetrics class using HDR color with linear exposure. Create an HDR color value with specified logarithmic exposure (stops). The exposure value controls the brightness in a logarithmic (perceptual) color space. When using logarithmic exposure, RGB channel values are typically in the range [0, 1].

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| exposure | number | Yes | Logarithmic exposure value in stops. Valid range: [0, +∞). A value of 0.0 represents standard exposure. Each increment of 1.0 doubles the brightness (one stop). |
| colorSpace | ColorSpace | Yes | Color space of color. Supports SRGB, DISPLAY_P3, and BT2020 color spaces. |
| red | number | Yes | Red component value. Valid range: [0, 1]. |
| green | number | Yes | Green component value. Valid range: [0, 1]. |
| blue | number | Yes | Blue component value. Valid range: [0, 1]. |
| alpha | number | No | Alpha (opacity) component value. Valid range: [0, 1]. The default value is 1.0 (fully opaque). |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics class instance with HDR color. |

## getBlueValue

```TypeScript
getBlueValue(): number
```

Get blue value. Returns blue channel value as a floating-point number.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | The blue value. Valid range: For SDR colors: [0.0, 1.0]. Fro HDR colors: [0.0, +∞), values &gt; 1.0 indicate HDR brightness. |

## getColorSpace

```TypeScript
getColorSpace(): ColorSpace
```

Get color space of the ColorMetrics. Returns the color space used when creating this color.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| ColorSpace | The color space of the ColorMetrics. Possible value: ColorSpace.SRGB, ColorSpace.DISPLAY_P3, ColorSpace.BT2020. |

## getGreenValue

```TypeScript
getGreenValue(): number
```

Get green value. Returns green channel value as a floating-point number.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | The green value. Valid range: For SDR colors: [0.0, 1.0]. Fro HDR colors: [0.0, +∞), values &gt; 1.0 indicate HDR brightness. |

## getRedValue

```TypeScript
getRedValue(): number
```

Get red value. Returns red channel value as a floating-point number.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | The red value. Valid range: For SDR colors: [0.0, 1.0]. Fro HDR colors: [0.0, +∞), values &gt; 1.0 indicate HDR brightness. |

## isHDR

```TypeScript
isHDR(): boolean
```

Check if ColorMetrics represents an HDR color. Returns true if color was created using createHDRColorWithXx or has RGB values &gt; 1.0.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether ColorMetrics is an HDR color. Returns true if:   - The color was created using createHDRColorWithXx() method.   - Any RGB channel value is greater than 1.0. |
