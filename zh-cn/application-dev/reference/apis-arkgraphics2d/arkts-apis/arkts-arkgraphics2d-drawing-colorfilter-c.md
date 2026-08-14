# ColorFilter

颜色滤波器，用于对图像或图形的颜色进行变换和处理，支持创建混合模式颜色滤波器、组合颜色滤波器、矩阵颜色滤波器、伽马颜色空间转换滤波器、亮度颜色滤波器和光照颜色滤波器等多种类型。 > **说明：** > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-drawing-class ColorFilter--><!--Device-drawing-class ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## createBlendModeColorFilter

```TypeScript
static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter
```

创建指定的颜色和混合模式的颜色滤波器。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-ColorFilter-static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter--><!--Device-ColorFilter-static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color | 是 | ARGB格式的颜色，每个颜色通道的值是[0, 255]的整数。 |
| mode | BlendMode | 是 | 混合模式，用于指定两个着色器叠加时的颜色混合算法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回基于指定颜色和混合模式创建的颜色滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## createBlendModeColorFilter

```TypeScript
static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter | undefined
```

创建指定的颜色和混合模式的颜色滤波器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorFilter-static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter | undefined--><!--Device-ColorFilter-static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color | 是 | ARGB格式的颜色，每个颜色通道的值是[0, 255]的整数。 |
| mode | BlendMode | 是 | 混合模式，用于指定两个着色器叠加时的颜色混合算法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回基于指定颜色和混合模式创建的颜色滤波器。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## createBlendModeColorFilter

```TypeScript
static createBlendModeColorFilter(color: common2D.Color | number, mode: BlendMode): ColorFilter
```

创建指定的颜色和混合模式的颜色滤波器。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-ColorFilter-static createBlendModeColorFilter(color: common2D.Color | number, mode: BlendMode): ColorFilter--><!--Device-ColorFilter-static createBlendModeColorFilter(color: common2D.Color | number, mode: BlendMode): ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color \| number | 是 | 颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，用16进制ARGB格式的无符号整 数表示，取值范围为[0, 0xFFFFFFFF]。 |
| mode | BlendMode | 是 | 混合模式，用于指定两个着色器叠加时的颜色混合算法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回基于指定颜色和混合模式创建的颜色滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## createBlendModeColorFilter

```TypeScript
static createBlendModeColorFilter(color: common2D.Color | int, mode: BlendMode): ColorFilter | undefined
```

创建指定的颜色和混合模式的颜色滤波器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorFilter-static createBlendModeColorFilter(color: common2D.Color | int, mode: BlendMode): ColorFilter | undefined--><!--Device-ColorFilter-static createBlendModeColorFilter(color: common2D.Color | int, mode: BlendMode): ColorFilter | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color \| int | 是 | 颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，用16进制ARGB格式的无符号整 数表示，取值范围为[0, 0xFFFFFFFF]。 |
| mode | BlendMode | 是 | 混合模式，用于指定两个着色器叠加时的颜色混合算法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回基于指定颜色和混合模式创建的颜色滤波器。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## createComposeColorFilter

```TypeScript
static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter
```

创建一个先应用inner进行滤波，再应用outer进行滤波的组合颜色滤波器。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-ColorFilter-static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter--><!--Device-ColorFilter-static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outer | ColorFilter | 是 | 组合滤波器中后生效的颜色滤波器。 |
| inner | ColorFilter | 是 | 组合滤波器中先生效的颜色滤波器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的组合颜色滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## createComposeColorFilter

```TypeScript
static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter | undefined
```

创建一个先应用inner进行滤波，再应用outer进行滤波的组合颜色滤波器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorFilter-static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter | undefined--><!--Device-ColorFilter-static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outer | ColorFilter | 是 | 组合滤波器中后生效的颜色滤波器。 |
| inner | ColorFilter | 是 | 组合滤波器中先生效的颜色滤波器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的组合颜色滤波器。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## createLightingColorFilter

```TypeScript
static createLightingColorFilter(mutColor: common2D.Color | number, addColor: common2D.Color | number): ColorFilter
```

创建一个光照颜色滤波器，此滤波器会将RGB通道的颜色值乘以乘法颜色（mutColor）并加上加法颜色（addColor），计算结果会被限制在0到255范围内。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-ColorFilter-static createLightingColorFilter(mutColor: common2D.Color | number, addColor: common2D.Color | number): ColorFilter--><!--Device-ColorFilter-static createLightingColorFilter(mutColor: common2D.Color | number, addColor: common2D.Color | number): ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mutColor | common2D.Color \| number | 是 | 用来进行乘法运算的颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，用16进 制ARGB格式的无符号整数表示，取值范围为[0, 0xFFFFFFFF]。 |
| addColor | common2D.Color \| number | 是 | 用来进行加法运算的颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，用16进 制ARGB格式的无符号整数表示，取值范围为[0, 0xFFFFFFFF]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的光照颜色滤波器。 |

## createLightingColorFilter

```TypeScript
static createLightingColorFilter(mutColor: common2D.Color | int, addColor: common2D.Color | int): ColorFilter | undefined
```

创建一个光照颜色滤波器，此滤波器会将RGB通道的颜色值乘以乘法颜色（mutColor）并加上加法颜色（addColor），计算结果会被限制在0到255范围内。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-ColorFilter-static createLightingColorFilter(mutColor: common2D.Color | int, addColor: common2D.Color | int): ColorFilter | undefined--><!--Device-ColorFilter-static createLightingColorFilter(mutColor: common2D.Color | int, addColor: common2D.Color | int): ColorFilter | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mutColor | common2D.Color \| int | 是 | 用来进行乘法运算的颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，用16进 制ARGB格式的无符号整数表示，取值范围为[0, 0xFFFFFFFF]。 |
| addColor | common2D.Color \| int | 是 | 用来进行加法运算的颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，用16进 制ARGB格式的无符号整数表示，取值范围为[0, 0xFFFFFFFF]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的光照颜色滤波器。创建失败时返回undefined。 |

## createLinearToSRGBGamma

```TypeScript
static createLinearToSRGBGamma(): ColorFilter
```

创建一个从线性颜色空间转换到SRGB颜色空间的颜色滤波器。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-ColorFilter-static createLinearToSRGBGamma(): ColorFilter--><!--Device-ColorFilter-static createLinearToSRGBGamma(): ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的颜色滤波器。 |

## createLinearToSRGBGamma

```TypeScript
static createLinearToSRGBGamma(): ColorFilter | undefined
```

创建一个从线性颜色空间转换到SRGB颜色空间的颜色滤波器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorFilter-static createLinearToSRGBGamma(): ColorFilter | undefined--><!--Device-ColorFilter-static createLinearToSRGBGamma(): ColorFilter | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的颜色滤波器。创建失败时返回undefined。 |

## createLumaColorFilter

```TypeScript
static createLumaColorFilter(): ColorFilter
```

创建一个颜色滤波器将其输入的亮度值乘以透明度通道的值，并将红色、绿色和蓝色通道设置为零。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-ColorFilter-static createLumaColorFilter(): ColorFilter--><!--Device-ColorFilter-static createLumaColorFilter(): ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的颜色滤波器。 |

## createLumaColorFilter

```TypeScript
static createLumaColorFilter(): ColorFilter | undefined
```

创建一个颜色滤波器将其输入的亮度值乘以透明度通道的值，并将红色、绿色和蓝色通道设置为零。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorFilter-static createLumaColorFilter(): ColorFilter | undefined--><!--Device-ColorFilter-static createLumaColorFilter(): ColorFilter | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的颜色滤波器。创建失败时返回undefined。 |

## createMatrixColorFilter

```TypeScript
static createMatrixColorFilter(matrix: Array<double>): ColorFilter
```

创建颜色滤波器，通过4×5颜色矩阵变换颜色。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ColorFilter-static createMatrixColorFilter(matrix: Array<double>): ColorFilter--><!--Device-ColorFilter-static createMatrixColorFilter(matrix: Array<double>): ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | Array&lt;double&gt; | 是 | 长度为20的数组，表示用于颜色变换的4×5矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的颜色滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## createMatrixColorFilter

```TypeScript
static createMatrixColorFilter(matrix: Array<double>): ColorFilter | undefined
```

创建颜色滤波器，通过4×5颜色矩阵变换颜色。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorFilter-static createMatrixColorFilter(matrix: Array<double>): ColorFilter | undefined--><!--Device-ColorFilter-static createMatrixColorFilter(matrix: Array<double>): ColorFilter | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | Array&lt;double&gt; | 是 | 长度为20的数组，表示用于颜色变换的4×5矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的颜色滤波器。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## createSRGBGammaToLinear

```TypeScript
static createSRGBGammaToLinear(): ColorFilter
```

创建一个从SRGB颜色空间转换到线性颜色空间的颜色滤波器。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-ColorFilter-static createSRGBGammaToLinear(): ColorFilter--><!--Device-ColorFilter-static createSRGBGammaToLinear(): ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的颜色滤波器。 |

## createSRGBGammaToLinear

```TypeScript
static createSRGBGammaToLinear(): ColorFilter | undefined
```

创建一个从SRGB颜色空间转换到线性颜色空间的颜色滤波器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorFilter-static createSRGBGammaToLinear(): ColorFilter | undefined--><!--Device-ColorFilter-static createSRGBGammaToLinear(): ColorFilter | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回创建的颜色滤波器。创建失败时返回undefined。 |

