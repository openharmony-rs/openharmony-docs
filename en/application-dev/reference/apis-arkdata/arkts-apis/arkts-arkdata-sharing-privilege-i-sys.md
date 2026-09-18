# Privilege (System API)

Defines the privilege (permissions) on the shared data.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## creatable

```TypeScript
creatable?: boolean
```

Whether the participant can create data to share. The value true means the participant can create data; the value false means the opposite. The default value is false.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## deletable

```TypeScript
deletable?: boolean
```

Whether the participant can delete the shared data. The value true means the participant can delete the data; the value false means the opposite. The default value is false.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## readable

```TypeScript
readable?: boolean
```

Whether the participant can read the shared data. The value true means the participant can read the data; the value false means the opposite. The default value is false.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## shareable

```TypeScript
shareable?: boolean
```

Whether the participant can share the data to others. The value true means the participant can share the data; the value false means the opposite. The default value is false.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## writable

```TypeScript
writable?: boolean
```

Whether the participant can modify the shared data. The value true means the participant can modify the data; the value false means the opposite. The default value is false.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.
