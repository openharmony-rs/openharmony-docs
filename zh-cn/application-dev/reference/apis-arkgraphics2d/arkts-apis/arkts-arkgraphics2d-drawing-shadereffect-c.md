# ShaderEffect

着色器。画刷和画笔设置着色器后，会使用着色器效果而不是颜色属性去绘制，但此时画笔和画刷的透明度属性仍然生效。 > **说明：** > > - 本Class首批接口从API version 12开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-drawing-class ShaderEffect--><!--Device-drawing-class ShaderEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## createColorShader

```TypeScript
static createColorShader(color: number): ShaderEffect
```

创建具有单一颜色的着色器。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-ShaderEffect-static createColorShader(color: number): ShaderEffect--><!--Device-ShaderEffect-static createColorShader(color: number): ShaderEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | number | 是 | 表示着色器的ARGB格式颜色，该参数为32位无符号整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回具有单一颜色的着色器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## createColorShader

```TypeScript
static createColorShader(color: int): ShaderEffect | undefined
```

Creates a ShaderEffect object with a single color.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ShaderEffect-static createColorShader(color: int): ShaderEffect | undefined--><!--Device-ShaderEffect-static createColorShader(color: int): ShaderEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | int | 是 | Color in the ARGB format. The value is a 32-bit unsigned integer. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the shader with single color ShaderEffect object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## createComposeShader

```TypeScript
static createComposeShader(dstShaderEffect: ShaderEffect, srcShaderEffect: ShaderEffect,
        blendMode: BlendMode): ShaderEffect
```

按照指定的混合模式对两个着色器进行叠加，生成一个新的着色器。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-ShaderEffect-static createComposeShader(dstShaderEffect: ShaderEffect, srcShaderEffect: ShaderEffect,        blendMode: BlendMode): ShaderEffect--><!--Device-ShaderEffect-static createComposeShader(dstShaderEffect: ShaderEffect, srcShaderEffect: ShaderEffect,        blendMode: BlendMode): ShaderEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dstShaderEffect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 在混合模式中作为目标色的着色器。 |
| srcShaderEffect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 在混合模式中作为源色的着色器。 |
| blendMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 混合模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回创建的着色器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## createComposeShader

```TypeScript
static createComposeShader(dstShaderEffect: ShaderEffect, srcShaderEffect: ShaderEffect,
        blendMode: BlendMode): ShaderEffect | undefined
```

Creates an ShaderEffect object that generates a blend ShaderEffect object by two shaders.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-ShaderEffect-static createComposeShader(dstShaderEffect: ShaderEffect, srcShaderEffect: ShaderEffect,        blendMode: BlendMode): ShaderEffect | undefined--><!--Device-ShaderEffect-static createComposeShader(dstShaderEffect: ShaderEffect, srcShaderEffect: ShaderEffect,        blendMode: BlendMode): ShaderEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dstShaderEffect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates a destination ShaderEffect pointer. |
| srcShaderEffect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates a source ShaderEffect pointer. |
| blendMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | BlendMode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns a blend ShaderEffect object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## createConicalGradient

```TypeScript
static createConicalGradient(startPt: common2D.Point, startRadius: number, endPt: common2D.Point,
        endRadius: number, colors: Array<number>, mode: TileMode,
        pos?: Array<number> | null, matrix?: Matrix | null): ShaderEffect
```

创建着色器，在给定两个圆之间生成径向渐变。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-ShaderEffect-static createConicalGradient(startPt: common2D.Point, startRadius: number, endPt: common2D.Point,        endRadius: number, colors: Array<number>, mode: TileMode,        pos?: Array<number> | null, matrix?: Matrix | null): ShaderEffect--><!--Device-ShaderEffect-static createConicalGradient(startPt: common2D.Point, startRadius: number, endPt: common2D.Point,        endRadius: number, colors: Array<number>, mode: TileMode,        pos?: Array<number> | null, matrix?: Matrix | null): ShaderEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startPt | common2D.Point | 是 | 表示渐变的起始圆的圆心。 |
| startRadius | number | 是 | 表示渐变的起始圆的半径，小于0时无效。该参数为浮点数。 |
| endPt | common2D.Point | 是 | 表示渐变的结束圆的圆心。 |
| endRadius | number | 是 | 表示渐变的结束圆的半径，小于0时无效。该参数为浮点数。 |
| colors | Array&lt;number&gt; | 是 | 表示在起始圆和结束圆之间分布的颜色数组，数组中的值为32位（ARGB）无符号整数。 |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 着色器效果平铺模式。 |
| pos | Array&lt;number&gt; \| null | 否 | 表示每种对应颜色在颜色数组中的相对位置。数组长度需和colors保持一致，数组的首个元素应当是0.0，末尾元素应当是1.0，中间的元素应当在0与1之间并且逐下标递增，表示colors中每个对应颜色的相对位置。默认为null，表示颜色均匀分布在起始圆和结束圆之间。 |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | 矩阵对象，用于对着色器做矩阵变换。默认为null，表示单位矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回创建的着色器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## createConicalGradient

```TypeScript
static createConicalGradient(startPt: common2D.Point, startRadius: double, endPt: common2D.Point,
        endRadius: double, colors: Array<int>, mode: TileMode,
        pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect | undefined
```

Creates a ShaderEffect object that generates a conical gradient between two given circles.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ShaderEffect-static createConicalGradient(startPt: common2D.Point, startRadius: double, endPt: common2D.Point,        endRadius: double, colors: Array<int>, mode: TileMode,        pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect | undefined--><!--Device-ShaderEffect-static createConicalGradient(startPt: common2D.Point, startRadius: double, endPt: common2D.Point,        endRadius: double, colors: Array<int>, mode: TileMode,        pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startPt | common2D.Point | 是 | Center of the start circle of the gradient. |
| startRadius | double | 是 | Radius of the start circle of the gradient. A negative number is invalid.The value is a floating point number. |
| endPt | common2D.Point | 是 | Center of the end circle of the gradient. |
| endRadius | double | 是 | Radius of the end circle of the gradient. A negative value is invalid.The value is a floating point number. |
| colors | Array&lt;int&gt; | 是 | Array of colors to distribute between the start circle and end circle.The values in the array are 32-bit (ARGB) unsigned integers. |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Tile mode of the shader effect. |
| pos | Array&lt;double&gt; \| null | 否 | Relative position of each color in the color array.The array length must be the same as that of colors.The first element in the array must be 0.0, the last element must be 1.0,and the middle elements must be between 0.0 and 1.0 and increase by index.The default value is null, indicating that colors are evenly distributed between the two circles. |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | Matrix object used to perform matrix transformation on the shader effect.The default value is null, indicating the identity matrix. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns a conical gradient ShaderEffect object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## createImageShader

```TypeScript
static createImageShader(pixelmap: image.PixelMap, tileX: TileMode, tileY: TileMode,
        samplingOptions: SamplingOptions, matrix?: Matrix | null): ShaderEffect
```

基于图片创建一个着色器。此接口不建议用于录制类型的画布，会影响性能。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-ShaderEffect-static createImageShader(pixelmap: image.PixelMap, tileX: TileMode, tileY: TileMode,        samplingOptions: SamplingOptions, matrix?: Matrix | null): ShaderEffect--><!--Device-ShaderEffect-static createImageShader(pixelmap: image.PixelMap, tileX: TileMode, tileY: TileMode,        samplingOptions: SamplingOptions, matrix?: Matrix | null): ShaderEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | 进行采样的图片对象。 |
| tileX | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 水平方向的平铺模式。 |
| tileY | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 竖直方向的平铺模式。 |
| samplingOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 图片采样参数。 |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | 可选参数，对图片施加的矩阵变换，如果为空，则不施加任何变换。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回创建的着色器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## createImageShader

```TypeScript
static createImageShader(pixelmap: image.PixelMap, tileX: TileMode, tileY: TileMode,
        samplingOptions: SamplingOptions, matrix?: Matrix | null): ShaderEffect | undefined
```

Creates an ShaderEffect object that generates a shader with single image.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-ShaderEffect-static createImageShader(pixelmap: image.PixelMap, tileX: TileMode, tileY: TileMode,        samplingOptions: SamplingOptions, matrix?: Matrix | null): ShaderEffect | undefined--><!--Device-ShaderEffect-static createImageShader(pixelmap: image.PixelMap, tileX: TileMode, tileY: TileMode,        samplingOptions: SamplingOptions, matrix?: Matrix | null): ShaderEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | PixelMap. |
| tileX | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates the type of tile mode for horizontal shader effect. |
| tileY | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates the type of tile mode for vertical shader effect. |
| samplingOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | SamplingOptions used to describe the sampling mode. |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | Indicates the Matrix object. The default value is null. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the shader with single image ShaderEffect object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## createLinearGradient

```TypeScript
static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array<int>,
        mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect
```

创建着色器，在两个指定点之间生成线性渐变。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-ShaderEffect-static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array<int>,        mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect--><!--Device-ShaderEffect-static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array<int>,        mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startPt | common2D.Point | 是 | 表示渐变的起点。 |
| endPt | common2D.Point | 是 | 表示渐变的终点。 |
| colors | Array&lt;int&gt; | 是 | 表示在两个点之间分布的颜色数组，数组中的值为32位（ARGB）无符号整数。 |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 着色器效果平铺模式。 |
| pos | Array&lt;double&gt; \| null | 否 | 表示每种对应颜色在颜色数组中的相对位置。数组长度需和colors保持一致，数组的首个元素应当是0.0，末尾元素应当是1.0，中间的元素应当在0与1之间并且逐下标递增，表示colors中每个对应颜色的相对位置。默认为null，表示颜色均匀分布在起点和终点之间。 |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | 矩阵对象，用于对着色器做矩阵变换。默认为null，表示单位矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回创建的着色器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## createLinearGradient

```TypeScript
static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array<int>,
        mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect | undefined
```

Creates a ShaderEffect object that generates a linear gradient between two points.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ShaderEffect-static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array<int>,        mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect | undefined--><!--Device-ShaderEffect-static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array<int>,        mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startPt | common2D.Point | 是 | Start point. |
| endPt | common2D.Point | 是 | End point. |
| colors | Array&lt;int&gt; | 是 | Array of colors to distribute between the two points.The values in the array are 32-bit (ARGB) unsigned integers. |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Tile mode of the shader effect. |
| pos | Array&lt;double&gt; \| null | 否 | Relative position of each color in the color array.The array length must be the same as that of colors. The first element in the array must be 0.0,the last element must be 1.0, and the middle elements must be between 0.0 and 1.0 and increase by index.The default value is null, indicating that colors are evenly distributed between the two points. |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | Matrix object used to perform matrix transformation on the shader effect.The default value is null, indicating the identity matrix. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns a linear gradient ShaderEffect object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## createRadialGradient

```TypeScript
static createRadialGradient(centerPt: common2D.Point, radius: double, colors: Array<int>,
      mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect
```

创建着色器，使用给定的圆心和半径生成径向渐变。径向渐变是指颜色从圆心逐渐向外扩散形成的渐变。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-ShaderEffect-static createRadialGradient(centerPt: common2D.Point, radius: double, colors: Array<int>,      mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect--><!--Device-ShaderEffect-static createRadialGradient(centerPt: common2D.Point, radius: double, colors: Array<int>,      mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| centerPt | common2D.Point | 是 | 表示渐变的圆心。 |
| radius | double | 是 | 表示渐变的半径，小于等于0时无效，该参数为浮点数。 |
| colors | Array&lt;int&gt; | 是 | 表示在圆心和圆边界之间分布的颜色数组，数组中的值为32位（ARGB）无符号整数。 |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 着色器效果平铺模式。 |
| pos | Array&lt;double&gt; \| null | 否 | 表示每种对应颜色在颜色数组中的相对位置。数组长度需和colors保持一致，数组的首个元素应当是0.0，末尾元素应当是1.0，中间的元素应当在0与1之间并且逐下标递增，表示colors中每个对应颜色的相对位置。默认为null，表示颜色均匀分布在圆心和圆边界之间。 |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | 矩阵对象，用于对着色器做矩阵变换。默认为null，表示单位矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回创建的着色器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## createRadialGradient

```TypeScript
static createRadialGradient(centerPt: common2D.Point, radius: double, colors: Array<int>,
      mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect | undefined
```

Creates a ShaderEffect object that generates a radial gradient based on the center and radius of a circle. A radial gradient refers to the color transition that spreads out gradually from the center of a circle.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ShaderEffect-static createRadialGradient(centerPt: common2D.Point, radius: double, colors: Array<int>,      mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect | undefined--><!--Device-ShaderEffect-static createRadialGradient(centerPt: common2D.Point, radius: double, colors: Array<int>,      mode: TileMode, pos?: Array<double> | null, matrix?: Matrix | null): ShaderEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| centerPt | common2D.Point | 是 | Center of the circle. |
| radius | double | 是 | Radius of the gradient. A negative number is invalid.The value is a floating point number. |
| colors | Array&lt;int&gt; | 是 | Array of colors to distribute between the center and ending shape of the circle.The values in the array are 32-bit (ARGB) unsigned integers. |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Tile mode of the shader effect. |
| pos | Array&lt;double&gt; \| null | 否 | Relative position of each color in the color array.The array length must be the same as that of colors. The first element in the array must be 0.0,the last element must be 1.0,and the middle elements must be between 0.0 and 1.0 and increase by index.The default value is null, indicating that colors are evenly distributed between the center and ending shape of the circle. |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | Matrix object used to perform matrix transformation on the shader effect.The default value is null, indicating the identity matrix. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns a radial gradient ShaderEffect object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## createSweepGradient

```TypeScript
static createSweepGradient(centerPt: common2D.Point, colors: Array<number>,
        mode: TileMode, startAngle: number, endAngle: number, pos?: Array<number> | null,
        matrix?: Matrix | null): ShaderEffect
```

创建着色器。该着色器以给定中心点为圆心，在顺时针或逆时针方向上生成颜色扫描渐变。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-ShaderEffect-static createSweepGradient(centerPt: common2D.Point, colors: Array<number>,        mode: TileMode, startAngle: number, endAngle: number, pos?: Array<number> | null,        matrix?: Matrix | null): ShaderEffect--><!--Device-ShaderEffect-static createSweepGradient(centerPt: common2D.Point, colors: Array<number>,        mode: TileMode, startAngle: number, endAngle: number, pos?: Array<number> | null,        matrix?: Matrix | null): ShaderEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| centerPt | common2D.Point | 是 | 表示渐变的圆心。 |
| colors | Array&lt;number&gt; | 是 | 表示在起始角度和结束角度之间分布的颜色数组，数组中的值为32位（ARGB）无符号整数。 |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 着色器效果平铺模式。 |
| startAngle | number | 是 | 表示扇形渐变的起始角度，单位为度。0度时为x轴正方向，正数往顺时针方向偏移，负数往逆时针方向偏移。该参数为浮点数。 |
| endAngle | number | 是 | 表示扇形渐变的结束角度，单位为度。0度时为x轴正方向，正数往顺时针方向偏移，负数往逆时针方向偏移。小于起始角度时无效。该参数为浮点数。 |
| pos | Array&lt;number&gt; \| null | 否 | 表示每种对应颜色在颜色数组中的相对位置。数组长度需和colors保持一致，数组的首个元素应当是0.0，末尾元素应当是1.0，中间的元素应当在0与1之间并且逐下标递增，表示colors中每个对应颜色的相对位置。默认为null，表示颜色均匀分布在起始角度和结束角度之间。 |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | 矩阵对象，用于对着色器做矩阵变换。默认为null，表示单位矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回创建的着色器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## createSweepGradient

```TypeScript
static createSweepGradient(centerPt: common2D.Point, colors: Array<int>,
      mode: TileMode, startAngle: double, endAngle: double, pos?: Array<double> | null,
      matrix?: Matrix | null): ShaderEffect | undefined
```

Creates a ShaderEffect object that generates a color sweep gradient around a given center point, either in a clockwise or counterclockwise direction.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ShaderEffect-static createSweepGradient(centerPt: common2D.Point, colors: Array<int>,      mode: TileMode, startAngle: double, endAngle: double, pos?: Array<double> | null,      matrix?: Matrix | null): ShaderEffect | undefined--><!--Device-ShaderEffect-static createSweepGradient(centerPt: common2D.Point, colors: Array<int>,      mode: TileMode, startAngle: double, endAngle: double, pos?: Array<double> | null,      matrix?: Matrix | null): ShaderEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| centerPt | common2D.Point | 是 | Center of the circle. |
| colors | Array&lt;int&gt; | 是 | Array of colors to distribute between the start angle and end angle.The values in the array are 32-bit (ARGB) unsigned integers. |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Tile mode of the shader effect. |
| startAngle | double | 是 | Start angle of the sweep gradient, in degrees.The value 0 indicates the positive direction of the X axis.A positive number indicates an offset towards the positive direction,and a negative number indicates an offset towards the negative direction.The value is a floating point number. |
| endAngle | double | 是 | End angle of the sweep gradient, in degrees.The value 0 indicates the positive direction of the X axis.A positive number indicates an offset towards the positive direction,and a negative number indicates an offset towards the negative direction.A value less than the start angle is invalid.The value is a floating point number. |
| pos | Array&lt;double&gt; \| null | 否 | Relative position of each color in the color array.The array length must be the same as that of colors.The first element in the array must be 0.0, the last element must be 1.0,and the middle elements must be between 0.0 and 1.0 and increase by index.The default value is null, indicating that the colors are evenly distributed between the start angle and end angle. |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | Matrix object used to perform matrix transformation on the shader effect.The default value is null, indicating the identity matrix. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns a sweep gradient ShaderEffect object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

