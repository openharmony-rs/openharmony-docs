# Graphics (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sun-xinyan-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

自定义节点相关属性定义的详细信息。

> **说明：**
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 本文仅介绍当前模块的系统接口，其他公开接口参见[Graphics](js-apis-arkui-graphics.md)。

## ColorMetrics

用于混合颜色。

### createHDRColorWithLinearExposure<sup>24+</sup>

static createHDRColorWithLinearExposure(linearExposure: number, colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

使用[ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20)、线性曝光系数和rgba格式颜色实例化支持HDR的ColorMetrics类。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型          | 必填 | 说明         |
| ------ | ------------- | ---- | ------------ |
| linearExposure | number | 是 | 线性曝光系数，取值范围：[1, +∞)。1.0表示标准曝光系数，大于1.0的值表示线性增加的曝光程度。 |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | 是   | 颜色空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要对应窗口调用[setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1)接口，将当前窗口设置为广色域模式。 |
| red   | number | 是   | 颜色的R分量（红色），值是0~1的浮动数值。 |
| green | number | 是   | 颜色的G分量（绿色），值是0~1的浮动数值。 |
| blue  | number | 是   | 颜色的B分量（蓝色），值是0~1的浮动数值。 |
| alpha | number | 否   | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。|

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | ColorMetrics类的实例。|

### createHDRColorWithLogExposure<sup>24+</sup>

static createHDRColorWithLogExposure(exposure: number, colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

使用[ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20)、指数型曝光系数和rgba格式颜色实例化支持HDR的ColorMetrics类。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型          | 必填 | 说明         |
| ------ | ------------- | ---- | ------------ |
| exposure | number | 是 | 指数型曝光系数，取值范围：[0, +∞)。0.0表示标准曝光系数，大于0.0的值表示指数级增加的曝光程度。 |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | 是   | 颜色空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要对应窗口调用[setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1)接口，将当前窗口设置为广色域模式。 |
| red   | number | 是   | 颜色的R分量（红色），值是0~1的浮动数值。 |
| green | number | 是   | 颜色的G分量（绿色），值是0~1的浮动数值。 |
| blue  | number | 是   | 颜色的B分量（蓝色），值是0~1的浮动数值。 |
| alpha | number | 否   | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。|

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | ColorMetrics类的实例。|

### createHDRColor<sup>24+</sup>

static createHDRColorWithLogExposure(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

使用[ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20)和rgba格式颜色实例化支持HDR的ColorMetrics类。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型          | 必填 | 说明         |
| ------ | ------------- | ---- | ------------ |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | 是   | 颜色空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要对应窗口调用[setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1)接口，将当前窗口设置为广色域模式。 |
| red   | number | 是   | 颜色的R分量（红色），取值范围：[0, +∞)。大于1.0的值会使能HDR特性。 |
| green | number | 是   | 颜色的G分量（绿色），取值范围：[0, +∞)。大于1.0的值会使能HDR特性。 |
| blue  | number | 是   | 颜色的B分量（蓝色），取值范围：[0, +∞)。大于1.0的值会使能HDR特性。 |
| alpha | number | 否   | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。|

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | ColorMetrics类的实例。|

### getColorSpace<sup>24+</sup>

getColorSpace(): ColorSpace

获取ColorMetrics的色彩空间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | 色彩空间。 |

### isHDR<sup>24+</sup>

isHDR(): boolean

获取ColorMetrics是否呈现了HDR色彩。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| boolean | ColorMetrics是否呈现了HDR色彩。当色彩是通过createHDRColorWithXx方法，如[createHDRColorWithLinearExposure](#createhdrcolorwithlinearexposure24)创建，或任意RGB分量值大于1.0时，将返回true；否则返回false，表示ColorMetrics未呈现HDR色彩。 |

### getRedValue<sup>24+</sup>

getRedValue(): number

获取ColorMetrics颜色的R分量（红色）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| number | 颜色的R分量（红色），值是大于等于0的浮点数。 |

### getGreenValue<sup>24+</sup>

getGreenValue(): number

获取ColorMetrics颜色的G分量（绿色）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| number | 颜色的G分量（绿色），值是大于等于0的浮点数。 |

### getBlueValue<sup>24+</sup>

getBlueValue(): number

获取ColorMetrics颜色的B分量（蓝色）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| number | 颜色的B分量（蓝色），值是大于等于0的浮点数。 |