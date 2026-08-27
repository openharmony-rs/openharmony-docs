# ColorMetrics

提供颜色的统一表示与封装，支持颜色混合以及 RGB、Alpha 分量的获取。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoRefresh

```TypeScript
autoRefresh?(value: boolean): ColorMetrics
```

设置ColorMetrics对象是否跟随系统配置变化自动更新。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 使用[resourceColor](#resourcecolor)方法构造的ColorMetrics对象是否在系统配置变化时自动刷新颜色值。 true表示主动监听系统配置变化，变化时值刷新为对应配置下的资源值。 false表示不主动监听系统配置变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | 返回设置自动刷新属性后的ColorMetrics对象。 |

**示例**

```TypeScript
import { ColorMetrics } from '@kit.ArkUI';

@Entry
@Component
struct MyStateSample {
  @State colorMetrics: ColorMetrics = ColorMetrics.resourceColor($r('sys.color.font_primary')).autoRefresh!(true);

  build() {
    Column() {
      Text('Test ColorMetrics')
    }
    .width('100%')
    .height('100%')
    .backgroundColor(this.colorMetrics)
  }
}
```

## blendColor

```TypeScript
blendColor(overlayColor: ColorMetrics): ColorMetrics
```

在当前颜色的上方叠加上一层指定的颜色（overlayColor），并返回混合后的新颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. The type of the input parameter is not ColorMetrics. |

## colorWithSpace

```TypeScript
static colorWithSpace(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

使用ColorSpace和rgba格式颜色实例化ColorMetrics类。仅red、green、blue属性支持在display-p3色彩空间中设置颜色，alpha属性不受色彩空间影响。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | ColorSpace | 是 | 色彩空间，用于指定颜色的色彩空间。使用ColorSpace.DISPLAY_P3，需要对应窗口调用 [setWindowColorSpace](arkts-arkui-window-window-i.md#setwindowcolorspace)接口，将当前窗口设置为广色 域模式。 |
| red | number | 是 | 颜色的R分量（红色），值是0~1的浮点数。超出范围时按边界值处理。 |
| green | number | 是 | 颜色的G分量（绿色），值是0~1的浮点数。超出范围时按边界值处理。 |
| blue | number | 是 | 颜色的B分量（蓝色），值是0~1的浮点数。超出范围时按边界值处理。 |
| alpha | number | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。    **说明：** alpha小于0为全透明，大于1为不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | 指定色彩空间下rgba格式颜色对应的颜色对象。 |

## numeric

```TypeScript
static numeric(value: number): ColorMetrics
```

使用HEX格式颜色实例化 ColorMetrics 类。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | HEX格式颜色，支持RGB或者ARGB。 取值范围：[0, 0xffffffff] 超出范围时按边界值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | HEX格式颜色对应的颜色对象。 |

## resourceColor

```TypeScript
static resourceColor(color: ResourceColor): ColorMetrics
```

使用资源格式颜色实例化 ColorMetrics 类。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 资源格式颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | 资源格式颜色对应的颜色对象。 |

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

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| red | number | 是 | 颜色的R分量（红色），值是0~255的整数。超出范围时按边界值处理。 |
| green | number | 是 | 颜色的G分量（绿色），值是0~255的整数。超出范围时按边界值处理。 |
| blue | number | 是 | 颜色的B分量（蓝色），值是0~255的整数。超出范围时按边界值处理。 |
| alpha | number | 否 | 颜色的A分量（透明度），值是0.0~1.0的浮点数，默认值为1.0，不透明。    **说明：** alpha小于0为全透明，大于1为不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | rgb或rgba格式颜色对应的颜色对象。 |

## alpha

```TypeScript
get alpha(): number
```

获取ColorMetrics颜色的A分量（透明度）。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { ColorMetrics } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

function getBlendColor(baseColor: ResourceColor): ColorMetrics {
  let sourceColor: ColorMetrics;
  try {
    // 在使用ColorMetrics的resourceColor和blendColor需要追加捕获异常处理
    // 可能返回的arkui子系统错误码有401和180003
    // 61 157 180
    sourceColor = ColorMetrics.resourceColor(baseColor).blendColor(ColorMetrics.resourceColor('#083d9db4'));
    console.info(`current color is ${sourceColor.color} r:${sourceColor.red} g:${sourceColor.green} b:${sourceColor.blue} a :${sourceColor.alpha}`);
  } catch (error) {
    console.error(`getBlendColor failed. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
    sourceColor = ColorMetrics.resourceColor('#19000000');
  }
  return sourceColor;
}

@Entry
@Component
struct ColorMetricsSample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('ColorMetrics blendColor')
        .width('80%')
        .align(Alignment.Center)
        .height(50)
        .backgroundColor(getBlendColor('#ff3d9db4').color)
        .margin(10)
      Button('ColorMetrics numeric')
        .width('80%')
        .align(Alignment.Center)
        .height(50)
        .backgroundColor(ColorMetrics.numeric(0xff707070).color)
        .margin(10)
      Button('ColorMetrics rgba')
        .width('80%')
        .align(Alignment.Center)
        .height(50)
        .backgroundColor(ColorMetrics.rgba(0, 74, 175, 1.0).color)
        .margin(10)
      Button('ColorMetrics colorWithSpace')
        .width('80%')
        .align(Alignment.Center)
        .height(50)
        .backgroundColor(ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0.4392, 0.4392, 0.4392).color)
        .margin(10)
    }
    .width('100%')
    .height('100%')
  }
}
```

## blue

```TypeScript
get blue(): number
```

获取ColorMetrics颜色的B分量（蓝色）。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
