# TransferMode

Enumerates the data transfer modes with a remote device.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## BASIC

```TypeScript
BASIC = 0
```

Basic mode, without a data retransfer mechanism. This mode is applicable to services sensitive to latency and throughput.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## RELIABLE

```TypeScript
RELIABLE = 1
```

Reliable mode, with a data retransfer mechanism. This mode is applicable to services that require high data integrity.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base
