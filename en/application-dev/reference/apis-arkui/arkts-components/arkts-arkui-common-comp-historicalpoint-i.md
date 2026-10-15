# HistoricalPoint

```TypeScript
declare interface HistoricalPoint
```

Provides historical touch point information.

**Since:** 10

<!--Device-unnamed-declare interface HistoricalPoint--><!--Device-unnamed-declare interface HistoricalPoint-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## force

```TypeScript
force: number
```

Touch pressure value of the historical point.

Default value: **0**

Value range: [0, 65535), where higher values indicate stronger pressure.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HistoricalPoint-force: number--><!--Device-HistoricalPoint-force: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: number
```

Size of the touch area between the finger and the screen in the touch event corresponding to the historical point.

Default value: **0**

Value range: [0, +∞).

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HistoricalPoint-size: number--><!--Device-HistoricalPoint-size: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

Timestamp of the touch event corresponding to the historical point, representing the time interval from system boot when the event is triggered.

Unit: ns

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HistoricalPoint-timestamp: number--><!--Device-HistoricalPoint-timestamp: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## touchObject

```TypeScript
touchObject: TouchObject
```

Basic touch event information for the historical point.

**Type:** [TouchObject](arkts-arkui-common-comp-touchobject-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HistoricalPoint-touchObject: TouchObject--><!--Device-HistoricalPoint-touchObject: TouchObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
