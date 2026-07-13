# ColorFilter

颜色滤波器。

> **说明：**
>
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

## createBlendModeColorFilter

```TypeScript
static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter
```

创建指定的颜色和混合模式的颜色滤波器。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color | 是 | ARGB格式的颜色，每个颜色通道的值是0到255之间的整数。 |
| mode | BlendMode | 是 | 颜色的混合模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回颜色滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createBlendModeColorFilter

```TypeScript
static createBlendModeColorFilter(color: common2D.Color | number, mode: BlendMode): ColorFilter
```

使用指定的颜色和混合模式创建颜色滤波器。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color \| number | 是 | 颜色，可以用16进制ARGB格式的无符号整数表示。 |
| mode | BlendMode | 是 | 颜色的混合模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回颜色滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createComposeColorFilter

```TypeScript
static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter
```

创建一个先应用inner进行滤波，再应用outer进行滤波的组合颜色滤波器。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outer | ColorFilter | 是 | 组合滤波器中后生效的颜色滤波器。 |
| inner | ColorFilter | 是 | 组合滤波器中先生效的颜色滤波器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回颜色滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## createLightingColorFilter

```TypeScript
static createLightingColorFilter(mutColor: common2D.Color | number, addColor: common2D.Color | number): ColorFilter
```

创建一个光照颜色滤波器，此滤波器会将RGB通道的颜色值乘以一种颜色值并加上另一种颜色值，计算结果会被限制在0到255范围内。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mutColor | common2D.Color \| number | 是 | 用来进行乘法运算的颜色，ARGB格式的颜色，每个颜色通道是0到255之间的整数。为number类型时必须是16进制ARGB格式的无符号整数。 |
| addColor | common2D.Color \| number | 是 | 用来进行加法运算的颜色，ARGB格式的颜色，每个颜色通道是0到255之间的整数。为number类型时必须是16进制ARGB格式的无符号整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回一个颜色滤波器。 |

## createLinearToSRGBGamma

```TypeScript
static createLinearToSRGBGamma(): ColorFilter
```

创建一个从线性颜色空间转换到SRGB颜色空间的颜色滤波器。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回颜色滤波器。 |

## createLumaColorFilter

```TypeScript
static createLumaColorFilter(): ColorFilter
```

创建一个颜色滤波器将其输入的亮度值乘以透明度通道，并将红色、绿色和蓝色通道设置为零。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回颜色滤波器。 |

## createMatrixColorFilter

```TypeScript
static createMatrixColorFilter(matrix: Array<number>): ColorFilter
```

创建颜色滤波器，通过4x5颜色矩阵变换颜色。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | Array&lt;number&gt; | 是 | 长度为20的数组，表示用于颜色变换的4*5矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回颜色滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createSRGBGammaToLinear

```TypeScript
static createSRGBGammaToLinear(): ColorFilter
```

创建一个从SRGB颜色空间转换到线性颜色空间的颜色滤波器。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回颜色滤波器。 |

