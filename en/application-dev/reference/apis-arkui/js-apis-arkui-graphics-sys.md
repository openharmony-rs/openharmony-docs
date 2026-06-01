# Graphics (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sun-xinyan-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **Graphics** module provides APIs for defining attributes of a custom node.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This topic describes only system APIs provided by the module. For details about other public APIs, see [Graphics](js-apis-arkui-graphics.md).

## ColorMetrics

Mixes colors.

### createHDRColorWithLinearExposure<sup>24+</sup>

static createHDRColorWithLinearExposure(linearExposure: number, colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

Instantiates the HDR-supported **ColorMetrics** class using the [color space](./arkui-ts/ts-appendix-enums.md#colorspace20), linear exposure coefficient, and RGBA color.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| linearExposure | number | Yes| Linear exposure coefficient. Value range: [1, +∞). The value **1.0** indicates the standard exposure coefficient, and a value greater than **1.0** indicates the exposure degree that increases linearly.|
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | Yes  | Color space used to specify the color. If **ColorSpace.DISPLAY_P3** is used, the [setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1) API must be called to set the current window to the wide color gamut mode.|
| red   | number | Yes  | Red component of the color. The value is a floating point number ranging from 0 to 1.|
| green | number | Yes  | Green component of the color. The value is a floating point number ranging from 0 to 1.|
| blue  | number | Yes  | Blue component of the color. The value is a floating point number ranging from 0 to 1.|
| alpha | number | No  | Alpha component of the color. The value is a floating point number ranging from 0.0 to 1.0. The default value is **1.0** (fully opaque).|

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | Instance of the **ColorMetrics** class.|

### createHDRColorWithLogExposure<sup>24+</sup>

static createHDRColorWithLogExposure(exposure: number, colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

Instantiates the HDR-supported **ColorMetrics** class using the [color space](./arkui-ts/ts-appendix-enums.md#colorspace20), exponential exposure coefficient, and RGBA color.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| exposure | number | Yes| Exponential exposure coefficient. Value range: [0, +∞). The value **0.0** indicates the standard exposure coefficient, and a value greater than **0.0** indicates the exposure degree that increases exponentially.|
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | Yes  | Color space used to specify the color. If **ColorSpace.DISPLAY_P3** is used, the [setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1) API must be called to set the current window to the wide color gamut mode.|
| red   | number | Yes  | Red component of the color. The value is a floating point number ranging from 0 to 1.|
| green | number | Yes  | Green component of the color. The value is a floating point number ranging from 0 to 1.|
| blue  | number | Yes  | Blue component of the color. The value is a floating point number ranging from 0 to 1.|
| alpha | number | No  | Alpha component of the color. The value is a floating point number ranging from 0.0 to 1.0. The default value is **1.0** (fully opaque).|

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | Instance of the **ColorMetrics** class.|

### createHDRColor<sup>24+</sup>

static createHDRColorWithLogExposure(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

Instantiates the HDR-supported **ColorMetrics** class using the [color space](./arkui-ts/ts-appendix-enums.md#colorspace20) and RGBA color.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | Yes  | Color space used to specify the color. If **ColorSpace.DISPLAY_P3** is used, the [setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1) API must be called to set the current window to the wide color gamut mode.|
| red   | number | Yes  | Red component of the color. The value range is [0, +∞). A value greater than **1.0** enables the HDR feature.|
| green | number | Yes  | Green component of the color. The value range is [0, +∞). A value greater than **1.0** enables the HDR feature.|
| blue  | number | Yes  | Blue component of the color. The value range is [0, +∞). A value greater than **1.0** enables the HDR feature.|
| alpha | number | No  | Alpha component of the color. The value is a floating point number ranging from 0.0 to 1.0. The default value is **1.0** (fully opaque).|

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | Instance of the **ColorMetrics** class.|

### getColorSpace<sup>24+</sup>

getColorSpace(): ColorSpace

Obtains the color space of the **ColorMetrics** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | Color space.|

### isHDR<sup>24+</sup>

isHDR(): boolean

Checks whether the HDR color is displayed for the **ColorMetrics** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| boolean | Whether the HDR color is displayed for the **ColorMetrics** object. If the color is created using the **createHDRColorWithXx** method, for example, [createHDRColorWithLinearExposure](#createhdrcolorwithlinearexposure24), or any RGB component value is greater than 1.0, **true** is returned. Otherwise, **false** is returned, indicating that the HDR color is not displayed for the **ColorMetrics** object.|

### getRedValue<sup>24+</sup>

getRedValue(): number

Obtains the red component of the **ColorMetrics** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Red component of the color. The value is a floating point number greater than or equal to 0.|

### getGreenValue<sup>24+</sup>

getGreenValue(): number

Obtains the green component of the **ColorMetrics** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Green component of the color. The value is a floating point number greater than or equal to 0.|

### getBlueValue<sup>24+</sup>

getBlueValue(): number

Obtains the blue component of the **ColorMetrics** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Blue component of the color. The value is a floating point number greater than or equal to 0.|
