# LengthMetrics

```TypeScript
declare class LengthMetrics
```

Defines the length attribute. When the length unit is PERCENT, the value **1** indicates 100%.

**Since:** 12

<!--Device-unnamed-declare class LengthMetrics--><!--Device-unnamed-declare class LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoRefresh

```TypeScript
autoRefresh?(value: boolean): LengthMetrics
```

Sets whether the **LengthMetrics** object automatically updates with system configuration changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LengthMetrics-autoRefresh?(value: boolean): LengthMetrics--><!--Device-LengthMetrics-autoRefresh?(value: boolean): LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the **LengthMetrics** object constructed using [resource](#resource) automatically refreshes the value when the system configuration changes. <br>**true**: The object proactively listens to the system configuration changes, and refreshes the value to the resource value corresponding to the configuration when the configuration changes. <br>**false**: The object does not proactively listen to the system configuration changes. |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | **LengthMetrics** object after the auto-refresh property is set. |

**Examples**

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct MyStateSample {
  @State lengthMetrics: LengthMetrics = LengthMetrics.resource($r('sys.float.ohos_id_button_min_width')).autoRefresh!(true);

  build() {
    Column() {
      Button('Test LengthMetrics')
        .padding({ top: this.lengthMetrics })
    }
  }
}
```

## constructor

```TypeScript
constructor(value: number, unit?:LengthUnit)
```

A constructor used to create a **LengthMetrics** instance. If the **unit** parameter is omitted or explicitly set to **undefined**, the default unit VP is used. If it is set to a value that is not of the LengthUnit type, the default value 0 VP is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LengthMetrics-constructor(value: number, unit?:LengthUnit)--><!--Device-LengthMetrics-constructor(value: number, unit?:LengthUnit)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: (-∞, +∞). |
| unit | [LengthUnit](arkts-arkui-graphics-lengthunit-e.md) | No | Unit of the length property. The default value is vp. |

## fp

```TypeScript
static fp(value: number): LengthMetrics
```

Creates a length property in fp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LengthMetrics-static fp(value: number): LengthMetrics--><!--Device-LengthMetrics-static fp(value: number): LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Length property object in units of fp. |

## lpx

```TypeScript
static lpx(value: number): LengthMetrics
```

Creates a length property in lpx.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LengthMetrics-static lpx(value: number): LengthMetrics--><!--Device-LengthMetrics-static lpx(value: number): LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Length property object in units of lpx. |

## percent

```TypeScript
static percent(value: number): LengthMetrics
```

Creates a length property in percent. The value **1** indicates 100%.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LengthMetrics-static percent(value: number): LengthMetrics--><!--Device-LengthMetrics-static percent(value: number): LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: [0, 1]. <br>A value out of range is treated as a boundary value. |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Length property object in units of percentage, where a value of **1** indicates 100%. |

## px

```TypeScript
static px(value: number): LengthMetrics
```

Creates a length property in px.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LengthMetrics-static px(value: number): LengthMetrics--><!--Device-LengthMetrics-static px(value: number): LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Length property object in units of px. |

## resource

```TypeScript
static resource(value: Resource): LengthMetrics
```

Represents the length of a resource of the Resource type.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LengthMetrics-static resource(value: Resource): LengthMetrics--><!--Device-LengthMetrics-static resource(value: Resource): LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Value of the length property. |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Length property object of a Resource-type resource. |

**Examples**

Use LengthMetrics to set the padding and margin attributes of Row.

```TypeScript
import { LengthMetrics, LengthUnit } from '@kit.ArkUI';

@Entry
@Component
struct SizeExample {
  build() {
    Column({ space: 10 }) {
      Text('margin and padding:')
        .fontSize(12)
        .fontColor(0xCCCCCC)
        .width('90%')
      Row() {
        Row() {
          Row()
            .size({ width: '100%', height: '100%' })
            .backgroundColor('#ffd5d5d5')
        }
        .width(80)
        .height(80)
        .padding({
          top: new LengthMetrics(20, LengthUnit.VP),
          bottom: LengthMetrics.px(15),
          start: LengthMetrics.vp(10),
          end: LengthMetrics.fp(20)
        })
        .margin({
          top: LengthMetrics.percent(0.1),
          bottom: LengthMetrics.lpx(20),
          start: LengthMetrics.resource($r('app.float.row_margin_start')),
          end: LengthMetrics.vp(10)
        })
        .backgroundColor(Color.White)
      }
      .backgroundColor('#ff2787d9')
    }
    .width('100%')
    .margin({ top: 5 })
  }
}
```

## vp

```TypeScript
static vp(value: number): LengthMetrics
```

Creates a length property in vp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LengthMetrics-static vp(value: number): LengthMetrics--><!--Device-LengthMetrics-static vp(value: number): LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Length property object in units of vp. |

## unit

```TypeScript
public unit: LengthUnit
```

Unit of the length property. The default value is VP.

**Type:** [LengthUnit](arkts-arkui-graphics-lengthunit-e.md)

**Default:** VP

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LengthMetrics-public unit: LengthUnit--><!--Device-LengthMetrics-public unit: LengthUnit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
public value: number
```

Value of the length property.

Value range: (-∞, +∞).

When **unit** is set to **PERCENT**, **value** indicates a percentage (1 indicates 100%), and the reference size depends on the specific usage scenario; for other units, **value** indicates the absolute length in the corresponding unit.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LengthMetrics-public value: number--><!--Device-LengthMetrics-public value: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
