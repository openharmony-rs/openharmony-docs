# ColorMetrics

提供颜色的统一表示与封装，支持颜色混合以及 RGB、Alpha 分量的获取。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare class ColorMetrics--><!--Device-unnamed-declare class ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoRefresh

```TypeScript
autoRefresh?(value: boolean): ColorMetrics
```

设置ColorMetrics对象是否跟随系统配置变化自动更新。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-autoRefresh?(value: boolean): ColorMetrics--><!--Device-ColorMetrics-autoRefresh?(value: boolean): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 使用[resourceColor](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md#resourceColor)方法构造的ColorMetrics对象是否在系统配置变化时自动刷新颜色值。 &lt;br&gt;true表示主动监听系统配置变化，变化时值刷新为对应配置下的资源值。 &lt;br&gt;false表示不主动监听系统配置变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | 返回设置自动刷新属性后的ColorMetrics对象。 |

## blendColor

```TypeScript
blendColor(overlayColor: ColorMetrics): ColorMetrics
```

在当前颜色的上方叠加上一层指定的颜色（overlayColor），并返回混合后的新颜色。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-blendColor(overlayColor: ColorMetrics): ColorMetrics--><!--Device-ColorMetrics-blendColor(overlayColor: ColorMetrics): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| overlayColor | [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | 是 | 要叠加在上方的颜色对象。alpha属性决定叠加强度。1.0表示完全覆盖，0.0表示完全透明，混合结果为原色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | 新的颜色对象，其red、green、blue和alpha通道均为当前颜色与叠加颜色混合后的结果值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. The type of the input parameter is not ColorMetrics. |

## colorWithSpace

```TypeScript
static colorWithSpace(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

使用ColorSpace和rgba格式颜色实例化ColorMetrics类。仅red、green、blue属性支持在display-p3色彩空间中设置颜色，alpha属性不受色彩空间影响。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-static colorWithSpace(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics--><!--Device-ColorMetrics-static colorWithSpace(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | ColorSpace | 是 | 色彩空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要对应窗口调用 [setWindowColorSpace](arkts-arkui-window-window-i.md#setWindowColorSpace)接口，将当前窗口设置为广色 域模式。 |
| red | number | 是 | 颜色的R分量（红色），值是0~1的浮点数。超出范围时按边界值处理。 |
| green | number | 是 | 颜色的G分量（绿色），值是0~1的浮点数。超出范围时按边界值处理。 |
| blue | number | 是 | 颜色的B分量（蓝色），值是0~1的浮点数。超出范围时按边界值处理。 |
| alpha | number | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。 &lt;br&gt; **说明：** alpha小于0为全透明，大于1为不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | 指定色彩空间下rgba格式颜色对应的颜色对象。 |

## numeric

```TypeScript
static numeric(value: number): ColorMetrics
```

使用HEX格式颜色实例化 ColorMetrics 类。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-static numeric(value: number): ColorMetrics--><!--Device-ColorMetrics-static numeric(value: number): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | HEX格式颜色，支持RGB或者ARGB。 &lt;br&gt;取值范围：[0, 0xffffffff] &lt;br&gt;超出范围时按边界值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | HEX格式颜色对应的颜色对象。 |

## resourceColor

```TypeScript
static resourceColor(color: ResourceColor): ColorMetrics
```

使用资源格式颜色实例化 ColorMetrics 类。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-static resourceColor(color: ResourceColor): ColorMetrics--><!--Device-ColorMetrics-static resourceColor(color: ResourceColor): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ResourceColor | 是 | 资源格式颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | 资源格式颜色对应的颜色对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [180003](../errorcode-event.md#180003-该事件不是克隆事件) | Failed to obtain the color resource. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. The type of the input color parameter is not ResourceColor. 2. The format of the input color string is not RGB or RGBA. |

## rgba

```TypeScript
static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

使用rgb或者rgba格式颜色实例化 ColorMetrics 类。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetrics-static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics--><!--Device-ColorMetrics-static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| red | number | 是 | 颜色的R分量（红色），值是0~255的整数。超出范围时按边界值处理。 |
| green | number | 是 | 颜色的G分量（绿色），值是0~255的整数。超出范围时按边界值处理。 |
| blue | number | 是 | 颜色的B分量（蓝色），值是0~255的整数。超出范围时按边界值处理。 |
| alpha | number | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。 &lt;br&gt; **说明：** alpha小于0为全透明，大于1为不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md) | rgb或rgba格式颜色对应的颜色对象。 |

