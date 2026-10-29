# ExtraData (System API)

```TypeScript
interface ExtraData
```

Represents the transparently transmitted data, which contains information required for a data change notification.

**Since:** 11

<!--Device-cloudData-interface ExtraData--><!--Device-cloudData-interface ExtraData-End-->

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

Event ID. Currently, only the value **cloud_data_change** is supported, indicating cloud data change. Other values are invalid.

**Type:** string

**Since:** 11

<!--Device-ExtraData-eventId: string--><!--Device-ExtraData-eventId: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## extraData

```TypeScript
extraData: string
```

Data to be transmitted transparently. **extraData** is a JSON string that must contain the **data** field. The **data** field contains information required for a change notification, including the account ID, application bundle name, database name, database type, and database table name. None of the fields can be empty.

**Type:** string

**Since:** 11

<!--Device-ExtraData-extraData: string--><!--Device-ExtraData-extraData: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
