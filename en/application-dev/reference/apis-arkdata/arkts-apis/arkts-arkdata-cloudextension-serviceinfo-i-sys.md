# ServiceInfo (System API)

```TypeScript
export interface ServiceInfo
```

Represents the cloud service information.

**Since:** 11

<!--Device-cloudExtension-export interface ServiceInfo--><!--Device-cloudExtension-export interface ServiceInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## enableCloud

```TypeScript
enableCloud: boolean
```

Whether the cloud service is enabled. The value true means that the cloud service is enabled, and the value false means the opposite.

**Type:** boolean

**Since:** 11

<!--Device-ServiceInfo-enableCloud: boolean--><!--Device-ServiceInfo-enableCloud: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## id

```TypeScript
id: string
```

Cloud account ID generated using SHA-256.

**Type:** string

**Since:** 11

<!--Device-ServiceInfo-id: string--><!--Device-ServiceInfo-id: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## remainingSpace

```TypeScript
remainingSpace: number
```

Available account space on the server, in KB.

**Type:** number

**Since:** 11

<!--Device-ServiceInfo-remainingSpace: long--><!--Device-ServiceInfo-remainingSpace: long-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## totalSpace

```TypeScript
totalSpace: number
```

Total account space on the server, in KB.

**Type:** number

**Since:** 11

<!--Device-ServiceInfo-totalSpace: long--><!--Device-ServiceInfo-totalSpace: long-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## user

```TypeScript
user: number
```

Current user ID of the device.

**Type:** number

**Since:** 11

<!--Device-ServiceInfo-user: int--><!--Device-ServiceInfo-user: int-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
