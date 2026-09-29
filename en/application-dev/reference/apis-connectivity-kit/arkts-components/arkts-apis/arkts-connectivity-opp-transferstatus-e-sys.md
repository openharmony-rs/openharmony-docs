# TransferStatus (System API)

```TypeScript
enum TransferStatus
```

Enum for the file transfer status.

**Since:** 16

<!--Device-opp-enum TransferStatus--><!--Device-opp-enum TransferStatus-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## PENDING

```TypeScript
PENDING = 0
```

The file is waiting next operate.

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

<!--Device-TransferStatus-PENDING = 0--><!--Device-TransferStatus-PENDING = 0-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## RUNNING

```TypeScript
RUNNING = 1
```

The file is transfering.

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

<!--Device-TransferStatus-RUNNING = 1--><!--Device-TransferStatus-RUNNING = 1-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## FINISH

```TypeScript
FINISH = 2
```

The file is transfer finished.

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

<!--Device-TransferStatus-FINISH = 2--><!--Device-TransferStatus-FINISH = 2-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.
