# ColorMetrics

```TypeScript
declare class ColorMetrics
```

Used to mix colors.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoRefresh

```TypeScript
autoRefresh?(value: boolean): ColorMetrics
```

Sets whether the **ColorMetrics** object automatically updates with system configuration changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the **ColorMetrics** object constructed using [resourceColor](#resourcecolor) automatically refreshes the color value when the system configuration changes. <br>**true**: The object proactively listens to the system configuration changes, and refreshes the value to the resource value corresponding to the configuration when the configuration changes. <br>**false**: The object does not proactively listen to the system configuration changes. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | **ColorMetrics** object. |

**Examples**

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

Blends a specified color (**overlayColor**) with the current color and returns the resulting color.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| overlayColor | [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Yes | Color to overlay. The alpha value determines the blending strength: **1.0** indicates complete opacity (fully covers the base color), and **0.0** indicates complete transparency (returns the original color). |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | New color object with red, green, blue, and alpha channels representing the blended result of the current color and overlay color. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. The type of the input parameter is not ColorMetrics. |

## colorWithSpace

```TypeScript
static colorWithSpace(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

Creates a **ColorMetrics** instance using specified ColorSpace and RGBA values. Only certain attributes support color configuration in the display-p3 color space.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorSpace | ColorSpace | Yes | Color space used to specify the color. If ColorSpace.DISPLAY_P3 is used, the [setWindowColorSpace](arkts-arkui-window-window-i.md#setwindowcolorspace) API must be called to set the current window to the wide color gamut mode. |
| red | number | Yes | Red component of the color. The value is a floating point number ranging from 0 to 1. |
| green | number | Yes | Green component of the color. The value is a floating point number ranging from 0 to 1. |
| blue | number | Yes | Blue component of the color. The value is a floating point number ranging from 0 to 1. |
| alpha | number | No | Alpha component of the color. The value is a floating point number ranging from 0.0 to 1.0. The default value is **1.0** (fully opaque). |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Instance of the **ColorMetrics** class. |

## numeric

```TypeScript
static numeric(value: number): ColorMetrics
```

Instantiates the **ColorMetrics** class using a color in HEX format.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Color in HEX format.<br>RGB and ARGB color values are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Instance of the **ColorMetrics** class. |

## resourceColor

```TypeScript
static resourceColor(color: ResourceColor): ColorMetrics
```

Instantiates the **ColorMetrics** class using a color in resource reference format.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Color in resource reference format. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Instance of the **ColorMetrics** class. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [180003](../errorcode-event.md#180003-input-event-is-not-a-cloned-event) | Failed to obtain the color resource. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. The type of the input color parameter is not ResourceColor. 2. The format of the input color string is not RGB or RGBA. |

## rgba

```TypeScript
static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics
```

Instantiates the **ColorMetrics** class using colors in RGB or RGBA format.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| red | number | Yes | Red component of the color. The value is an integer ranging from 0 to 255. |
| green | number | Yes | Green component of the color. The value is an integer ranging from 0 to 255. |
| blue | number | Yes | Blue component of the color. The value is an integer ranging from 0 to 255. |
| alpha | number | No | Alpha component of the color. The value is a floating point number ranging from 0.0 to 1. 0. The default value is **1.0** (fully opaque).<br> Note: If alpha is less than 0, the color is fully transparent. If alpha is greater than 1, the color is opaque. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Instance of the **ColorMetrics** class. |

## alpha

```TypeScript
get alpha(): number
```

Obtains the alpha component of the ColorMetrics color.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { ColorMetrics } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

function getBlendColor(baseColor: ResourceColor): ColorMetrics {
  let sourceColor: ColorMetrics;
  try {
    // When resourceColor and blendColor of ColorMetrics are used, add exception handling.
    // Error codes 401 and 180003 of the ArkUI subsystem may be returned.
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

Obtains the blue component of the ColorMetrics color.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
get color(): string
```

Obtains the color of **ColorMetrics**. The return value is a string indicating an RGBA color value.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## green

```TypeScript
get green(): number
```

Obtains the green component of the ColorMetrics color.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## red

```TypeScript
get red(): number
```

Obtains the red component of the ColorMetrics color.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
