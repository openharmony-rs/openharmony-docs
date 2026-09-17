# OppTransferInformation (System API)

Describes the transferred file information.

**Since:** 16

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { opp } from '@kit.ConnectivityKit';
```

## currentBytes

```TypeScript
currentBytes: number
```

Number of bytes of the file that have been transferred currently

**Type:** number

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## currentCount

```TypeScript
currentCount: number
```

Number of files currently transferred

**Type:** number

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## direction

```TypeScript
direction: DirectionType
```

File Transfer Direction

**Type:** [DirectionType](arkts-connectivity-opp-directiontype-e-sys.md)

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## filePath

```TypeScript
filePath: string
```

Path of the file to be transferred.

**Type:** string

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## remoteDeviceId

```TypeScript
remoteDeviceId: string
```

Device Address of the peer transmission object

**Type:** string

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## remoteDeviceName

```TypeScript
remoteDeviceName: string
```

Device name of the peer transmission object

**Type:** string

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## result

```TypeScript
result: TransferResult
```

File transfer result

**Type:** [TransferResult](arkts-connectivity-opp-transferresult-e-sys.md)

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## status

```TypeScript
status: TransferStatus
```

File transfer status

**Type:** [TransferStatus](arkts-connectivity-opp-transferstatus-e-sys.md)

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## totalBytes

```TypeScript
totalBytes: number
```

Total number of file bytes to transfer

**Type:** number

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## totalCount

```TypeScript
totalCount: number
```

Total number of transferred files

**Type:** number

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.
