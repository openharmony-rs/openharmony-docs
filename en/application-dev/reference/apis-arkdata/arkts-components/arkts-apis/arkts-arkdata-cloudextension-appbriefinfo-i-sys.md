# AppBriefInfo (System API)

Represents the brief application information.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## appId

```TypeScript
appId: string
```

Application ID.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## cloudSwitch

```TypeScript
cloudSwitch: boolean
```

Whether the cloud service is enabled for the application. The value true means the cloud service is enabled; the value false means the opposite.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## instanceId

```TypeScript
instanceId: number
```

Application twin ID. The value 0 indicates the application itself, and the twin ID increases in ascending order.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
