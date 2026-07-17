# ColorMetrics

用于混合颜色。

**起始版本：** 12

<!--Device-unnamed-declare class ColorMetrics--><!--Device-unnamed-declare class ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoRefresh

```TypeScript
autoRefresh?(value: boolean): ColorMetrics
```

设置ColorMetrics对象的自动刷新。启用时，当系统配置发生变化时，使用ColorMetrics.resourceColor()创建的对象的颜色值将自动更新

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-autoRefresh?(value: boolean): ColorMetrics--><!--Device-ColorMetrics-autoRefresh?(value: boolean): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当系统配置发生变化时，是否自动刷新颜色值。<br>如果设置为true，则使用ColorMetrics.resourceColor()创建的对象的颜色值会在系统配置发生变化时自动更新。如果设置为false，则对象的颜色值由ColorMetrics.resourceColor()创建的，不会自动更新。默认值为false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | 返回用于链接的ColorMetrics对象。 |

## blendColor

```TypeScript
blendColor(overlayColor: ColorMetrics): ColorMetrics
```

在当前颜色的上方叠加上一层指定的颜色（overlayColor），并返回混合后的新颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-blendColor(overlayColor: ColorMetrics): ColorMetrics--><!--Device-ColorMetrics-blendColor(overlayColor: ColorMetrics): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| overlayColor | [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | 是 | 要叠加在上方的颜色对象。alpha属性决定叠加强度。1.0表示完全覆盖，0.0表示完全透明，混合结果为原色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | 新的颜色对象，其red、green、blue和alpha通道均为当前颜色与叠加颜色混合后的结果值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. The type of the input parameter is not ColorMetrics. |

## colorWithSpace

```TypeScript
static colorWithSpace(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

使用[ColorSpace](arkts-arkui-enums-colorspace-e.md)和rgba格式颜色实例化ColorMetrics类。仅部分属性支持在display-p3色彩空间中设置颜色。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-static colorWithSpace(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics--><!--Device-ColorMetrics-static colorWithSpace(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | [ColorSpace](arkts-arkui-window-colorspace-e.md) | 是 | 颜色空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要对应窗口调用[setWindowColorSpace](../../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowcolorspace9-1)接口，将当前窗口设置为广色域模式。 |
| red | number | 是 | 颜色的R分量（红色），值是0~1的浮动数值。 |
| green | number | 是 | 颜色的G分量（绿色），值是0~1的浮动数值。 |
| blue | number | 是 | 颜色的B分量（蓝色），值是0~1的浮动数值。 |
| alpha | number | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics类的实例。 |

## numeric

```TypeScript
static numeric(value: number): ColorMetrics
```

使用HEX格式颜色实例化 ColorMetrics 类。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-static numeric(value: number): ColorMetrics--><!--Device-ColorMetrics-static numeric(value: number): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | HEX格式颜色。<br/>取值范围：支持rgb或者argb |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics 类的实例。 |

## resourceColor

```TypeScript
static resourceColor(color: ResourceColor): ColorMetrics
```

使用资源格式颜色实例化 ColorMetrics 类。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-static resourceColor(color: ResourceColor): ColorMetrics--><!--Device-ColorMetrics-static resourceColor(color: ResourceColor): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 资源格式颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics 类的实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [180003](../errorcode-event.md#180003-该事件不是克隆事件) | Failed to obtain the color resource. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause:1. The type of the input color parameter is not ResourceColor.2. The format of the input color string is not RGB or RGBA. |

## rgba

```TypeScript
static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

使用rgb或者rgba格式颜色实例化 ColorMetrics 类。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics--><!--Device-ColorMetrics-static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| red | number | 是 | 颜色的R分量（红色），值是0~255的整数。 |
| green | number | 是 | 颜色的G分量（绿色），值是0~255的整数。 |
| blue | number | 是 | 颜色的B分量（蓝色），值是0~255的整数。 |
| alpha | number | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。<br/> **说明：** alpha小于0为全透明，大于1为不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics 类的实例。 |

## alpha

```TypeScript
get alpha(): number
```

获取ColorMetrics颜色的A分量（透明度）。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-get alpha(): number--><!--Device-ColorMetrics-get alpha(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blue

```TypeScript
get blue(): number
```

获取ColorMetrics颜色的B分量（蓝色）。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-get blue(): number--><!--Device-ColorMetrics-get blue(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
get color(): string
```

获取ColorMetrics的颜色，返回的是rgba字符串的格式。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-get color(): string--><!--Device-ColorMetrics-get color(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## green

```TypeScript
get green(): number
```

获取ColorMetrics颜色的G分量（绿色）。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-get green(): number--><!--Device-ColorMetrics-get green(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## red

```TypeScript
get red(): number
```

获取ColorMetrics颜色的R分量（红色）。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-get red(): number--><!--Device-ColorMetrics-get red(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

