# ColorMetrics

提供颜色的统一表示与封装，支持颜色混合以及 RGB、Alpha 分量的获取。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare class ColorMetrics--><!--Device-unnamed-declare class ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## createHDRColor

```TypeScript
static createHDRColor(colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics
```

使用ColorSpace和rgba格式颜色实例化支持HDR的ColorMetrics类。适用于无需调整曝光系数、直接指定HDR颜色分量的场景，如HDR纯色背景绘制、固定HDR色彩配置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static createHDRColor(colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics--><!--Device-ColorMetrics-static createHDRColor(colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | ColorSpace | 是 | 色彩空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要在当前窗口调用 [setWindowColorSpace](arkts-arkui-window-window-i.md#setWindowColorSpace)接口，将当前窗口设置为广色 域模式。 |
| red | double | 是 | 颜色的R分量（红色），取值范围：[0, +∞)。大于1.0的值会使能HDR特性。传入负数时将被自动钳位到0.0。 |
| green | double | 是 | 颜色的G分量（绿色），取值范围：[0, +∞)。大于1.0的值会使能HDR特性。传入负数时将被自动钳位到0.0。 |
| blue | double | 是 | 颜色的B分量（蓝色），取值范围：[0, +∞)。大于1.0的值会使能HDR特性。传入负数时将被自动钳位到0.0。 |
| alpha | double | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | 支持HDR的ColorMetrics类的实例，可用于表示HDR颜色及进行后续色彩空间查询、HDR状态判断和RGB分量获取等操作。 |

## createHDRColorWithLinearExposure

```TypeScript
static createHDRColorWithLinearExposure(linearExposure: double, colorSpace: ColorSpace,
    red: double, green: double, blue: double, alpha?: double): ColorMetrics
```

使用ColorSpace、线性曝光系数和rgba格式颜色实例化支持HDR的ColorMetrics类。如不需要通过曝光系数调节，可使用 [createHDRColor](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c-sys.md#createHDRColor)直接设置RGB分量值大于1.0来呈现HDR效果。适用于需要按线性比例均匀调整HDR亮度的场景，如HDR图像预览、视频播放器色彩调 节。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static createHDRColorWithLinearExposure(linearExposure: double, colorSpace: ColorSpace,    red: double, green: double, blue: double, alpha?: double): ColorMetrics--><!--Device-ColorMetrics-static createHDRColorWithLinearExposure(linearExposure: double, colorSpace: ColorSpace,    red: double, green: double, blue: double, alpha?: double): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| linearExposure | double | 是 | 线性曝光系数，取值范围：[1, +∞)。1.0表示标准曝光系数，大于1.0的值表示线性增加的曝光程度。传入小于1.0的值时将被自动钳位到1.0。 |
| colorSpace | ColorSpace | 是 | 色彩空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要在当前窗口调用 [setWindowColorSpace](arkts-arkui-window-window-i.md#setWindowColorSpace)接口，将当前窗口设置为广色 域模式。 |
| red | double | 是 | 颜色的R分量（红色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| green | double | 是 | 颜色的G分量（绿色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| blue | double | 是 | 颜色的B分量（蓝色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| alpha | double | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | 支持HDR的ColorMetrics类的实例，可用于表示HDR颜色及进行后续色彩空间查询、HDR状态判断和RGB分量获取等操作。 |

## createHDRColorWithLogExposure

```TypeScript
static createHDRColorWithLogExposure(exposure: double, colorSpace: ColorSpace,
    red: double, green: double, blue: double, alpha?: double): ColorMetrics
```

使用ColorSpace、对数型曝光系数和rgba格式颜色实例化支持HDR的ColorMetrics类。与 [createHDRColorWithLinearExposure](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c-sys.md#createHDRColorWithLinearExposure)相比，两者均通过曝光系数创建HDR色彩，区别在于本方法使 用对数型曝光系数（指数级增加曝光程度），后者使用线性曝光系数（线性增加曝光程度），开发者可根据所需的曝光调节方式选择。如不需要通过曝光系数调节，可使用 [createHDRColor](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c-sys.md#createHDRColor)直接设置RGB分量值大于1.0来呈现HDR效果。适用于需要按对数关系调整HDR亮度（更贴近人眼感知）的场景，如HDR照片编辑、影 视后期调色。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static createHDRColorWithLogExposure(exposure: double, colorSpace: ColorSpace,    red: double, green: double, blue: double, alpha?: double): ColorMetrics--><!--Device-ColorMetrics-static createHDRColorWithLogExposure(exposure: double, colorSpace: ColorSpace,    red: double, green: double, blue: double, alpha?: double): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exposure | double | 是 | 对数型曝光系数，取值范围：[0, +∞)。0.0表示标准曝光系数，大于0.0的值表示指数级增加的曝光程度。传入负数时将被自动钳位到0.0。 |
| colorSpace | ColorSpace | 是 | 色彩空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要在当前窗口调用 [setWindowColorSpace](arkts-arkui-window-window-i.md#setWindowColorSpace)接口，将当前窗口设置为广色 域模式。 |
| red | double | 是 | 颜色的R分量（红色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| green | double | 是 | 颜色的G分量（绿色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| blue | double | 是 | 颜色的B分量（蓝色），值是0.0~1.0的浮点数。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |
| alpha | double | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。超出范围时将被自动钳位到[0.0, 1.0]范围内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | 支持HDR的ColorMetrics类的实例，可用于表示HDR颜色及进行后续色彩空间查询、HDR状态判断和RGB分量获取等操作。 |

## getBlueValue

```TypeScript
getBlueValue(): double
```

获取ColorMetrics颜色的B分量（蓝色）。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-getBlueValue(): double--><!--Device-ColorMetrics-getBlueValue(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 颜色的B分量（蓝色），值是大于等于0的浮点数。 |

## getColorSpace

```TypeScript
getColorSpace(): ColorSpace
```

获取ColorMetrics的色彩空间。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-getColorSpace(): ColorSpace--><!--Device-ColorMetrics-getColorSpace(): ColorSpace-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorSpace | 当前ColorMetrics对象所配置的色彩空间，可用于判断当前颜色使用的色彩空间类型。 |

## getGreenValue

```TypeScript
getGreenValue(): double
```

获取ColorMetrics颜色的G分量（绿色）。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-getGreenValue(): double--><!--Device-ColorMetrics-getGreenValue(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 颜色的G分量（绿色），值是大于等于0的浮点数。 |

## getRedValue

```TypeScript
getRedValue(): double
```

获取ColorMetrics颜色的R分量（红色）。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-getRedValue(): double--><!--Device-ColorMetrics-getRedValue(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 颜色的R分量（红色），值是大于等于0的浮点数。 |

## isHDR

```TypeScript
isHDR(): boolean
```

获取ColorMetrics是否呈现了HDR色彩。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-isHDR(): boolean--><!--Device-ColorMetrics-isHDR(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ColorMetrics是否呈现了HDR色彩。当色彩是通过createHDRColorWith系列方法（如 [createHDRColorWithLinearExposure]{ |

