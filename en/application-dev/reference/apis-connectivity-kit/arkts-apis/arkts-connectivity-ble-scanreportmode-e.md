# ScanReportMode

```TypeScript
enum ScanReportMode
```

Report mode used during scan.

**Since:** 15

<!--Device-ble-enum ScanReportMode--><!--Device-ble-enum ScanReportMode-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## NORMAL

```TypeScript
NORMAL = 1
```

In normal mode, the advertisement packet is reported immediately after being scanned.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ScanReportMode-NORMAL = 1--><!--Device-ScanReportMode-NORMAL = 1-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## BATCH

```TypeScript
BATCH = 2
```

Enables delayed sending of advertising packets in batch mode by the interval specified by [interval](arkts-connectivity-ble-scanoptions-i.md#interval).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-ScanReportMode-BATCH = 2--><!--Device-ScanReportMode-BATCH = 2-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## FENCE_SENSITIVITY_LOW

```TypeScript
FENCE_SENSITIVITY_LOW = 10
```

In low sensitivity fence mode, the advertisement packets are reported only when they are received for the first time and lost for the last time. The reception sensitivity is low.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ScanReportMode-FENCE_SENSITIVITY_LOW = 10--><!--Device-ScanReportMode-FENCE_SENSITIVITY_LOW = 10-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## FENCE_SENSITIVITY_HIGH

```TypeScript
FENCE_SENSITIVITY_HIGH = 11
```

In high sensitivity fence mode, the advertisement packets are reported only when they are received for the first time and lost for the last time. The reception sensitivity is high.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ScanReportMode-FENCE_SENSITIVITY_HIGH = 11--><!--Device-ScanReportMode-FENCE_SENSITIVITY_HIGH = 11-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
