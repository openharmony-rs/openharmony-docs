# ExtraData (System API)

Represents the transparently transmitted data, which contains information required for a data change notification.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## eventId

```TypeScript
eventId: string
```

Event ID. The value **cloud_data_change** indicates cloud data changes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## extraData

```TypeScript
extraData: string
```

Data to be transmitted transparently. **extraData** is a JSON string that must contain the **data** field. The **data** field contains information required for a change notification, including the account ID, application name, database name, database type, and database table name. All the fields cannot be empty.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
