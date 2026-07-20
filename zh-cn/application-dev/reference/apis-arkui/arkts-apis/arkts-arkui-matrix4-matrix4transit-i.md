# Matrix4Transit

矩阵对象。

**起始版本：** 7

<!--Device-matrix4-interface Matrix4Transit--><!--Device-matrix4-interface Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

<a id="combine"></a>
## combine

```TypeScript
combine(options: Matrix4Transit): Matrix4Transit
```

Matrix的叠加函数，可以将两个矩阵的效果叠加起来生成一个新的矩阵对象。会改变调用该函数的原始矩阵。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Matrix4Transit-combine(options: Matrix4Transit): Matrix4Transit--><!--Device-Matrix4Transit-combine(options: Matrix4Transit): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 是 | 待叠加的矩阵对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 矩阵叠加后的对象。 |

<a id="copy"></a>
## copy

```TypeScript
copy(): Matrix4Transit
```

Matrix的拷贝函数，可以拷贝一份当前的矩阵对象。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Matrix4Transit-copy(): Matrix4Transit--><!--Device-Matrix4Transit-copy(): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 当前矩阵的拷贝对象。 |

<a id="invert"></a>
## invert

```TypeScript
invert(): Matrix4Transit
```

Matrix的逆函数，可以返回一个当前矩阵对象的逆矩阵，即效果正好相反。会改变调用该函数的原始矩阵。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Matrix4Transit-invert(): Matrix4Transit--><!--Device-Matrix4Transit-invert(): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 当前矩阵的逆矩阵对象。 |

<a id="rotate"></a>
## rotate

```TypeScript
rotate(options: RotateOption): Matrix4Transit
```

Matrix的旋转函数，可以为当前矩阵增加x轴/y轴/z轴旋转效果。会改变调用该函数的原始矩阵。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Matrix4Transit-rotate(options: RotateOption): Matrix4Transit--><!--Device-Matrix4Transit-rotate(options: RotateOption): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RotateOption](arkts-arkui-matrix4-rotateoption-i.md) | 是 | 设置旋转参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 旋转效果后的矩阵对象。 |

<a id="scale"></a>
## scale

```TypeScript
scale(options: ScaleOption): Matrix4Transit
```

Matrix的缩放函数，可以为当前矩阵增加x轴/y轴/z轴缩放效果。会改变调用该函数的原始矩阵。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Matrix4Transit-scale(options: ScaleOption): Matrix4Transit--><!--Device-Matrix4Transit-scale(options: ScaleOption): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ScaleOption](arkts-arkui-matrix4-scaleoption-i.md) | 是 | 设置缩放参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 缩放效果后的矩阵对象。 |

<a id="setpolytopoly"></a>
## setPolyToPoly

```TypeScript
setPolyToPoly(options: PolyToPolyOptions): Matrix4Transit
```

将一个多边形的顶点坐标映射到另外一个多边形的顶点坐标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Matrix4Transit-setPolyToPoly(options: PolyToPolyOptions): Matrix4Transit--><!--Device-Matrix4Transit-setPolyToPoly(options: PolyToPolyOptions): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolyToPolyOptions](arkts-arkui-matrix4-polytopolyoptions-i.md) | 是 | 映射相关的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 当前矩阵变换后的对象。 |

<a id="skew"></a>
## skew

```TypeScript
skew(x: number, y: number): Matrix4Transit
```

Matrix的倾斜函数，可以为当前矩阵增加x轴/y轴倾斜效果。会改变调用该函数的原始矩阵。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Matrix4Transit-skew(x: number, y: number): Matrix4Transit--><!--Device-Matrix4Transit-skew(x: number, y: number): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 设置x轴倾斜参数。 |
| y | number | 是 | 设置y轴倾斜参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 倾斜效果后的矩阵对象。 |

<a id="transformpoint"></a>
## transformPoint

```TypeScript
transformPoint(options: [number, number]): [number, number]
```

Matrix的坐标点转换函数，可以将当前的变换效果作用到一个坐标点上。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Matrix4Transit-transformPoint(options: [number, number]): [number, number]--><!--Device-Matrix4Transit-transformPoint(options: [number, number]): [number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [number, number] | 是 | 需要转换的坐标点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [number, number] | 返回矩阵变换后的Point对象。 |

<a id="translate"></a>
## translate

```TypeScript
translate(options: TranslateOption): Matrix4Transit
```

Matrix的平移函数，可以为当前矩阵增加x轴/y轴/z轴平移效果。会改变调用该函数的原始矩阵。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Matrix4Transit-translate(options: TranslateOption): Matrix4Transit--><!--Device-Matrix4Transit-translate(options: TranslateOption): Matrix4Transit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TranslateOption](arkts-arkui-matrix4-translateoption-i.md) | 是 | 设置平移参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 平移效果后的矩阵对象。 |

