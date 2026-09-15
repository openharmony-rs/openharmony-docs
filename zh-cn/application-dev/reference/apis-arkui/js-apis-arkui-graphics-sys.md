# Graphics (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sun-xinyan-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

Graphics模块提供自定义节点相关属性定义，支持HDR色彩创建、色彩空间管理与查询、颜色分量获取等能力，适用于需要在Stage模型下进行HDR色彩处理及自定义节点属性配置的场景。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 本文仅介绍当前模块的系统接口，其他公开接口参见[Graphics](./js-apis-arkui-graphics.md)。

## ColorMetrics

用于表示支持HDR的颜色，提供通过曝光系数创建HDR色彩、查询色彩空间及获取RGB颜色分量等能力，适用于HDR色彩处理与颜色属性配置的场景。

### createHDRColorWithLinearExposure

ArkTS-Dyn: static createHDRColorWithLinearExposure(linearExposure: number, colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

ArkTS-Sta: static createHDRColorWithLinearExposure(linearExposure: double, colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics

使用[ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20)、线性曝光系数和rgba格式颜色实例化支持HDR的ColorMetrics类。如不需要通过曝光系数调节，可使用[createHDRColor](#createhdrcolor)直接设置RGB分量值大于1.0来呈现HDR效果。适用于需要按线性比例均匀调整HDR亮度的场景，如HDR图像预览、视频播放器色彩调节。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型          | 必填 | 说明         |
| ------ | ------------- | ---- | ------------ |
| linearExposure | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是 | 线性曝光系数，取值范围：[1, +∞)。1.0表示标准曝光系数，大于1.0的值表示线性增加的曝光程度。传入小于1.0的值时将被自动钳位到1.0。 |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | 是   | 色彩空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要在当前窗口调用[setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1)接口，将当前窗口设置为广色域模式。 |
| red   | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是   | 颜色的R分量（红色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| green | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是   | 颜色的G分量（绿色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| blue  | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是   | 颜色的B分量（蓝色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| alpha | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 否   | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。超出范围时将被自动钳位到[0.0, 1.0]范围内。|

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | 支持HDR的ColorMetrics类的实例，可用于表示HDR颜色及进行后续色彩空间查询、HDR状态判断和RGB分量获取等操作。|

### createHDRColorWithLogExposure

ArkTS-Dyn: static createHDRColorWithLogExposure(exposure: number, colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

ArkTS-Sta: static createHDRColorWithLogExposure(exposure: double, colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics

使用[ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20)、对数型曝光系数和rgba格式颜色实例化支持HDR的ColorMetrics类。与[createHDRColorWithLinearExposure](#createhdrcolorwithlinearexposure)相比，两者均通过曝光系数创建HDR色彩，区别在于本方法使用对数型曝光系数（指数级增加曝光程度），后者使用线性曝光系数（线性增加曝光程度），开发者可根据所需的曝光调节方式选择。如不需要通过曝光系数调节，可使用[createHDRColor](#createhdrcolor)直接设置RGB分量值大于1.0来呈现HDR效果。适用于需要按对数关系调整HDR亮度（更贴近人眼感知）的场景，如HDR照片编辑、影视后期调色。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型          | 必填 | 说明         |
| ------ | ------------- | ---- | ------------ |
| exposure | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是 | 对数型曝光系数，取值范围：[0, +∞)。0.0表示标准曝光系数，大于0.0的值表示指数级增加的曝光程度。传入负数时将被自动钳位到0.0。 |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | 是   | 色彩空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要在当前窗口调用[setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1)接口，将当前窗口设置为广色域模式。 |
| red   | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是   | 颜色的R分量（红色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| green | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是   | 颜色的G分量（绿色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| blue  | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是   | 颜色的B分量（蓝色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| alpha | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 否   | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。超出范围时将被自动钳位到[0.0, 1.0]范围内。|

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | 支持HDR的ColorMetrics类的实例，可用于表示HDR颜色及进行后续色彩空间查询、HDR状态判断和RGB分量获取等操作。|

### createHDRColor

ArkTS-Dyn: static createHDRColorWithLogExposure(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

ArkTS-Sta: static createHDRColorWithLogExposure(colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics

使用[ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20)和rgba格式颜色实例化支持HDR的ColorMetrics类。适用于无需调整曝光系数、直接指定HDR颜色分量的场景，如HDR纯色背景绘制、固定HDR色彩配置。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型          | 必填 | 说明         |
| ------ | ------------- | ---- | ------------ |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | 是   | 色彩空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要在当前窗口调用[setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1)接口，将当前窗口设置为广色域模式。 |
| red   | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是   | 颜色的R分量（红色），取值范围：[0, +∞)。大于1.0的值会使能HDR特性。传入负数时将被自动钳位到0.0。 |
| green | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是   | 颜色的G分量（绿色），取值范围：[0, +∞)。大于1.0的值会使能HDR特性。传入负数时将被自动钳位到0.0。 |
| blue  | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 是   | 颜色的B分量（蓝色），取值范围：[0, +∞)。大于1.0的值会使能HDR特性。传入负数时将被自动钳位到0.0。 |
| alpha | ArkTS-Dyn: number <br/>ArkTS-Sta: double | 否   | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。超出范围时将被自动钳位到[0.0, 1.0]范围内。|

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics) | 支持HDR的ColorMetrics类的实例，可用于表示HDR颜色及进行后续色彩空间查询、HDR状态判断和RGB分量获取等操作。|

### getColorSpace

getColorSpace(): ColorSpace

获取ColorMetrics的色彩空间。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | 当前ColorMetrics对象所配置的色彩空间，可用于判断当前颜色使用的色彩空间类型。 |

### isHDR

isHDR(): boolean

获取ColorMetrics是否呈现了HDR色彩。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| boolean | ColorMetrics是否呈现了HDR色彩。当色彩是通过createHDRColorWith系列方法（如[createHDRColorWithLinearExposure](#createhdrcolorwithlinearexposure)）创建，或任意RGB分量值大于1.0时，将返回true；否则返回false，表示ColorMetrics未呈现HDR色彩。 |

### getRedValue

ArkTS-Dyn: getRedValue(): number

ArkTS-Sta: getRedValue(): double

获取ColorMetrics颜色的R分量（红色）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| ArkTS-Dyn: number <br/>ArkTS-Sta: double | 颜色的R分量（红色），值是大于等于0的浮点数。 |

### getGreenValue

ArkTS-Dyn: getGreenValue(): number

ArkTS-Sta: getGreenValue(): double

获取ColorMetrics颜色的G分量（绿色）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| ArkTS-Dyn: number <br/>ArkTS-Sta: double | 颜色的G分量（绿色），值是大于等于0的浮点数。 |

### getBlueValue

ArkTS-Dyn: getBlueValue(): number

ArkTS-Sta: getBlueValue(): double

获取ColorMetrics颜色的B分量（蓝色）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型          | 说明             |
| ------------- | ---------------- |
| ArkTS-Dyn: number <br/>ArkTS-Sta: double | 颜色的B分量（蓝色），值是大于等于0的浮点数。 |