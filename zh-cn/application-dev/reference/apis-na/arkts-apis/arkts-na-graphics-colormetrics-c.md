# ColorMetrics

用于混合颜色。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ColorMetrics--><!--Device-unnamed-export declare class ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blendColor

```TypeScript
blendColor(overlayColor: ColorMetrics): ColorMetrics
```

在当前颜色的上方叠加上一层指定的颜色（overlayColor），并返回混合后的新颜色。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-blendColor(overlayColor: ColorMetrics): ColorMetrics--><!--Device-ColorMetrics-blendColor(overlayColor: ColorMetrics): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| overlayColor | [ColorMetrics](../../apis-arkui/arkts-apis/arkts-arkui-graphics-colormetrics-c.md) | 是 | 要叠加在上方的颜色对象。alpha属性决定叠加强度。1.0表示完全覆盖，0.0表示完全透明，混合结果为原色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-arkui/arkts-apis/arkts-arkui-graphics-colormetrics-c.md) | 新的颜色对象，其red、green、blue和alpha通道均为当前颜色与叠加颜色混合后的结果值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. The type of the input parameter is not ColorMetrics. |

## colorWithSpace

```TypeScript
static colorWithSpace(colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics
```

使用colorSpace和rgba实例化ColorMetrics类。 只有部分属性支持在display-p3 colorSpace中设置颜色。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static colorWithSpace(colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics--><!--Device-ColorMetrics-static colorWithSpace(colorSpace: ColorSpace, red: double, green: double, blue: double, alpha?: double): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | ColorSpace | 是 | 颜色空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要对应窗口调用 [setWindowColorSpace](../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowcolorspace9-1)接口，将当前窗 口设置为广色域模式。 |
| red | double | 是 | 颜色的R分量（红色），值是0~1的浮动数值。 |
| green | double | 是 | 颜色的G分量（绿色），值是0~1的浮动数值。 |
| blue | double | 是 | 颜色的B分量（蓝色），值是0~1的浮动数值。 |
| alpha | double | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-arkui/arkts-apis/arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics类的实例。 |

## numeric

```TypeScript
static numeric(value: int): ColorMetrics
```

使用颜色编号实例化ColorMetrics类

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static numeric(value: int): ColorMetrics--><!--Device-ColorMetrics-static numeric(value: int): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 | HEX格式颜色。<br/>取值范围：支持rgb或者argb。 <br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-arkui/arkts-apis/arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics 类的实例。 |

## resourceColor

```TypeScript
static resourceColor(color: ResourceColor): ColorMetrics
```

使用资源格式颜色实例化 ColorMetrics 类。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static resourceColor(color: ResourceColor): ColorMetrics--><!--Device-ColorMetrics-static resourceColor(color: ResourceColor): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ResourceColor | 是 | 资源格式颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-arkui/arkts-apis/arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics 类的实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [180003](../../apis-arkui/errorcode-event.md#180003-该事件不是克隆事件) | Failed to obtain the color resource. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. The type of the input color parameter is not ResourceColor. 2. The format of the input color string is not RGB or RGBA. |

## rgba

```TypeScript
static rgba(red: double, green: double, blue: double, alpha?: double): ColorMetrics
```

使用颜色rgb实例化ColorMetrics类

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-static rgba(red: double, green: double, blue: double, alpha?: double): ColorMetrics--><!--Device-ColorMetrics-static rgba(red: double, green: double, blue: double, alpha?: double): ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| red | double | 是 | 颜色的R分量（红色），值是0~255的整数。 |
| green | double | 是 | 颜色的G分量（绿色），值是0~255的整数。 |
| blue | double | 是 | 颜色的B分量（蓝色），值是0~255的整数。 |
| alpha | double | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。<br/> **说明：** alpha小于0为全透明，大于1为不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](../../apis-arkui/arkts-apis/arkts-arkui-graphics-colormetrics-c.md) | ColorMetrics 类的实例。 |

## BLACK

```TypeScript
public static readonly BLACK: int
```

黑色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly BLACK: int--><!--Device-ColorMetrics-public static readonly BLACK: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BLUE

```TypeScript
public static readonly BLUE: int
```

蓝色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly BLUE: int--><!--Device-ColorMetrics-public static readonly BLUE: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BROWN

```TypeScript
public static readonly BROWN: int
```

棕色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly BROWN: int--><!--Device-ColorMetrics-public static readonly BROWN: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## GRAY

```TypeScript
public static readonly GRAY: int
```

灰色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly GRAY: int--><!--Device-ColorMetrics-public static readonly GRAY: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## GREEN

```TypeScript
public static readonly GREEN: int
```

绿色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly GREEN: int--><!--Device-ColorMetrics-public static readonly GREEN: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## GREY

```TypeScript
public static readonly GREY: int
```

灰色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly GREY: int--><!--Device-ColorMetrics-public static readonly GREY: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ORANGE

```TypeScript
public static readonly ORANGE: int
```

橘色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly ORANGE: int--><!--Device-ColorMetrics-public static readonly ORANGE: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PINK

```TypeScript
public static readonly PINK: int
```

粉色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly PINK: int--><!--Device-ColorMetrics-public static readonly PINK: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RED

```TypeScript
public static readonly RED: int
```

红色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly RED: int--><!--Device-ColorMetrics-public static readonly RED: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TRANSPARENT

```TypeScript
public static readonly TRANSPARENT: string
```

透明度。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly TRANSPARENT: string--><!--Device-ColorMetrics-public static readonly TRANSPARENT: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WHITE

```TypeScript
public static readonly WHITE: int
```

白色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly WHITE: int--><!--Device-ColorMetrics-public static readonly WHITE: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## YELLOW

```TypeScript
public static readonly YELLOW: int
```

黄色。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorMetrics-public static readonly YELLOW: int--><!--Device-ColorMetrics-public static readonly YELLOW: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

