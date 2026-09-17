# HistoricalPoint

Provides historical touch point information.

**Since:** 10

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: number
```

Size of the contact area size between the finger and screen in the touch event corresponding to the historical point.

Default value: **0**

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## touchObject

```TypeScript
touchObject: TouchObject
```

Basic touch event information for the historical point.

**Type:** [TouchObject](arkts-arkui-touchobject-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
