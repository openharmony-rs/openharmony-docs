# Graphics (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sun-xinyan-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3cd7a88aa48788902d0133e2f69247ba0fd6a00d translatedAt=2026-07-29T09:26:01.246Z pushedAt=2026-07-31T10:52:56.254Z -->

The **Graphics** module provides APIs for defining attributes of a custom node, which supports HDR color creation, color space management and query, and color component retrieval. It is applicable to scenarios requiring HDR color processing and custom node attribute configuration in the stage model.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This document describes only the system APIs of this module. For details about other public APIs, see [Graphics](./js-apis-arkui-graphics.md).

## ColorMetrics

Represents a color that supports HDR. It provides capabilities such as creating HDR colors through exposure coefficients, querying color spaces, and obtaining RGB color components. It is applicable to HDR color processing and color attribute configuration scenarios.

### createHDRColorWithLinearExposure

static createHDRColorWithLinearExposure(linearExposure: number, colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

Instantiates the HDR-supported **ColorMetrics** class using the [color space](./arkui-ts/ts-appendix-enums.md#colorspace20), linear exposure coefficient, and RGBA color. If adjustment by exposure coefficient is not needed, [createHDRColor](#createhdrcolor) can be used to directly set RGB component values greater than 1.0 to present HDR effects. This API is applicable to scenarios requiring balanced HDR brightness adjustment in linear proportion, such as HDR image preview and video player color adjustment.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| linearExposure | number | Yes | Linear exposure coefficient. Value range: [1, +∞). The value **1.0** indicates the standard exposure coefficient, and a value greater than 1.0 indicates the exposure degree that increases linearly. Values less than 1.0 are automatically clamped to 1.0. |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | Yes   | Color space used to specify the color space of the color. To use **ColorSpace.DISPLAY_P3**, call [setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1) in the current window to set the current window to the wide color gamut mode. |
| red   | number | Yes   | Red component of the color, which is a floating-point number ranging from 0.0 to 1.0. Values out of range are automatically clamped to [0.0, 1.0]. |
| green | number | Yes   | Green component of the color, which is a floating-point number ranging from 0.0 to 1.0. Values out of range are automatically clamped to [0.0, 1.0]. |
| blue  | number | Yes   | Blue component of the color, which is a floating-point number ranging from 0.0 to 1.0. Values out of range are automatically clamped to [0.0, 1.0]. |
| alpha | number | No   | Alpha component of the color, which is a floating-point number ranging from 0.0 to 1.0. The default value is **1.0**, indicating opaque. Values out of range are automatically clamped to [0.0, 1.0]. |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | Instance of the HDR-supported **ColorMetrics** class, which is used to represent a HDR color and perform subsequent operations such as color space query, HDR state determination, and RGB component retrieval.|

### createHDRColorWithLogExposure

static createHDRColorWithLogExposure(exposure: number, colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

Instantiates the HDR-supported **ColorMetrics** class using the [color space](./arkui-ts/ts-appendix-enums.md#colorspace20), logarithmic exposure coefficient, and RGBA color. Compared with [createHDRColorWithLinearExposure](#createhdrcolorwithlinearexposure), both APIs create HDR colors through exposure coefficients. The difference is that this API uses a logarithmic exposure coefficient (indicating the exposure degree increases exponentially), while the latter uses a linear exposure coefficient (indicating the exposure degree increases linearly). You can choose either of them based on the desired exposure adjustment. If exposure coefficient adjustment is not needed, [createHDRColor](#createhdrcolor) can be used to directly set RGB component values greater than 1.0 to present HDR effects. This API is applicable to scenarios requiring HDR brightness adjustment in logarithmic relation (closer to human eye perception), such as HDR photo editing and film and television post-production color grading.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| exposure | number | Yes | Logarithmic exposure coefficient. Value range: [0, +∞). **0.0** indicates the standard exposure coefficient, and a value greater than 0.0 indicates the exposure degree that increases exponentially. Negative values are automatically clamped to 0.0. |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | Yes   | Color space used to specify the color space of the color. To use **ColorSpace.DISPLAY_P3**, call [setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1) in the current window to set the current window to the wide color gamut mode. |
| red   | number | Yes   | Red component of the color, which is a floating-point number ranging from 0.0 to 1.0. Values outside this range are automatically clamped to [0.0, 1.0]. |
| green | number | Yes   | Green component of the color, which is a floating-point number ranging from 0.0 to 1.0. Values outside this range are automatically clamped to [0.0, 1.0]. |
| blue  | number | Yes   | Blue component of the color, which is a floating-point number ranging from 0.0 to 1.0. Values outside this range are automatically clamped to [0.0, 1.0]. |
| alpha | number | No   | Alpha component of the color, which is a floating-point number ranging from 0.0 to 1.0. The default value is **1.0**, indicating opaque. Values outside this range are automatically clamped to [0.0, 1.0]. |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | Instance of the HDR-supported **ColorMetrics** class, which is used to represent HDR colors and perform subsequent operations such as color space query, HDR state determination, and RGB component retrieval.|

### createHDRColor

static createHDRColor(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

Instantiates the HDR-supported **ColorMetrics** class using the [color space](./arkui-ts/ts-appendix-enums.md#colorspace20) and RGBA color. This API is applicable to scenarios where exposure coefficient adjustment is not needed and HDR color components are directly specified, such as HDR solid color background drawing and fixed HDR color configuration.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | Yes   | Color space used to specify the color space of the color. To use **ColorSpace.DISPLAY_P3**, call [setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1) in the current window to set the current window to the wide color gamut mode. |
| red   | number | Yes   | Red component of the color. Value range: [0, +∞). A value greater than 1.0 enables the HDR feature. Negative numbers are automatically clamped to 0.0. |
| green | number | Yes   | Green component of the color. Value range: [0, +∞). A value greater than 1.0 enables the HDR feature. Negative numbers are automatically clamped to 0.0. |
| blue  | number | Yes   | Blue component of the color. Value range: [0, +∞). A value greater than 1.0 enables the HDR feature. Negative numbers are automatically clamped to 0.0. |
| alpha | number | No   | Alpha component of the color, which is a floating-point number ranging from 0.0 to 1.0. The default value is **1.0**, indicating opaque. Values out of this range are automatically clamped to the range [0.0, 1.0]. |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | Instance of the HDR-supported **ColorMetrics**, which is used to represent HDR colors and perform operations such as color space query, HDR state determination, and RGB component retrieval.|

### getColorSpace

getColorSpace(): ColorSpace

Obtains the color space of the **ColorMetrics** object.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | Color space configured for the current **ColorMetrics** object, which is used to determine the type of the color space used by the current color. |

### isHDR

isHDR(): boolean

Checks whether the HDR color is displayed for the **ColorMetrics** object.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| boolean | Whether the HDR color is displayed for the **ColorMetrics** object. If the color is created using the **createHDRColorWithXx** API, for example, [createHDRColorWithLinearExposure](#createhdrcolorwithlinearexposure), or any RGB component value is greater than 1.0, **true** is returned. Otherwise, **false** is returned, indicating that the HDR color is not displayed for the **ColorMetrics** object. |

### getRedValue

getRedValue(): number

Obtains the red component of the **ColorMetrics** object.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Red component of the color. The value is a floating point number greater than or equal to 0.|

### getGreenValue

getGreenValue(): number

Obtains the green component of the **ColorMetrics** object.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Green component of the color. The value is a floating point number greater than or equal to 0.|

### getBlueValue

getBlueValue(): number

Obtains the blue component of the **ColorMetrics** object.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Blue component of the color. The value is a floating point number greater than or equal to 0.|