# LengthMetrics

Defines the length attribute. When the length unit is PERCENT, the value **1** indicates 100%.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoRefresh

```TypeScript
autoRefresh?(value: boolean): LengthMetrics
```

Sets whether the **LengthMetrics** object automatically updates with system configuration changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the **LengthMetrics** object constructed using [resource](#resource) automatically refreshes the value when the system configuration changes. <br>**true**: The object proactively listens to the system configuration changes, and refreshes the value to the resource value corresponding to the configuration when the configuration changes. <br>**false**: The object does not proactively listen to the system configuration changes. |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | **LengthMetrics** object. |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: [0, +∞). |
| unit | [LengthUnit](arkts-arkui-graphics-lengthunit-e.md) | No | Unit of the length property. |

## fp

```TypeScript
static fp(value: number): LengthMetrics
```

Creates a length property in fp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Instance of the **LengthMetrics** class. |

## lpx

```TypeScript
static lpx(value: number): LengthMetrics
```

Creates a length property in lpx.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Instance of the **LengthMetrics** class. |

## percent

```TypeScript
static percent(value: number): LengthMetrics
```

Creates a length property in percent. The value **1** indicates 100%.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: [0, 1]. |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Instance of the **LengthMetrics** class. |

## px

```TypeScript
static px(value: number): LengthMetrics
```

Creates a length property in px.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Instance of the **LengthMetrics** class. |

## resource

```TypeScript
static resource(value: Resource): LengthMetrics
```

Represents the length of a resource of the Resource type.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Value of the length property. |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Instance of the **LengthMetrics** class. |

**Examples**

```TypeScript
Use LengthMetrics to set the padding and margin attributes of Row.
```

## vp

```TypeScript
static vp(value: number): LengthMetrics
```

Creates a length property in vp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value of the length property.<br>Value range: (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Instance of the **LengthMetrics** class. |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
public value: number
```

Value of the length property.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
