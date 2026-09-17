# SwitchConfig (System API)

Defines the switch configuration of a device-cloud synergy database.

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## dbInfo

```TypeScript
dbInfo: Record<string, DBSwitchInfo>
```

Switch configuration information of a database. The key is the database name, and the value is the configuration information of the database.

**Type:** Record&lt;string, [DBSwitchInfo](arkts-arkdata-clouddata-dbswitchinfo-i-sys.md)&gt;

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
