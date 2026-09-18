# ScanReportMode

Report mode used during scan.

**Since:** 15

**System capability:** SystemCapability.Communication.Bluetooth.Core

## NORMAL

```TypeScript
NORMAL = 1
```

In normal mode, the advertisement packet is reported immediately after being scanned.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## BATCH

```TypeScript
BATCH = 2
```

Enables delayed sending of advertising packets in batch mode by the interval specified by [interval](arkts-connectivity-ble-scanoptions-i.md#interval).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## FENCE_SENSITIVITY_LOW

```TypeScript
FENCE_SENSITIVITY_LOW = 10
```

In low sensitivity fence mode, the advertisement packets are reported only when they are received for the first time and lost for the last time. The reception sensitivity is low.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## FENCE_SENSITIVITY_HIGH

```TypeScript
FENCE_SENSITIVITY_HIGH = 11
```

In high sensitivity fence mode, the advertisement packets are reported only when they are received for the first time and lost for the last time. The reception sensitivity is high.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.Bluetooth.Core
