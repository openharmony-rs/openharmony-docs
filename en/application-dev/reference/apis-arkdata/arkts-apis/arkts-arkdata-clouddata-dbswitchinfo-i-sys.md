# DBSwitchInfo (System API)

Defines the switch information of a device-cloud synergy database.

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## enable

```TypeScript
enable: boolean
```

Whether to enable device-cloud synergy for the database. The value **true** indicates that device-cloud synergy is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## tableInfo

```TypeScript
tableInfo?: Record<string, boolean>
```

Device-cloud synergy configuration of a table. The key is the table name, and the value is the switch status of the table. The value **true** indicates that device-cloud synergy is enabled for the table, and the value **false** indicates the opposite. If this parameter is not set, the device-cloud synergy is enabled for the database by default.

**Type:** Record&lt;string, boolean&gt;

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
