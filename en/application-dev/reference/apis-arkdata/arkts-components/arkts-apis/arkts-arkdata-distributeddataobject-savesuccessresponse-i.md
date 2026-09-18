# SaveSuccessResponse

Represents the information returned by the callback of save..

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## Modules to Import

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## deviceId

```TypeScript
deviceId: string
```

ID of the device where the distributed data object is stored. The value local indicates a local device.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## sessionId

```TypeScript
sessionId: string
```

Unique ID for multi-device collaboration.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## version

```TypeScript
version: number
```

Version of the saved object, which is a non-negative integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject
