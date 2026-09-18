# ClearConfig (System API)

Defines the clearance configuration of a device-cloud synergy database.

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## dbInfo

```TypeScript
dbInfo: Record<string, DBActionInfo>
```

Information about the database whose data is to be cleared and the clearance rules. The key is the database name, and the value is the clearance configuration of the database.

**Type:** Record&lt;string, [DBActionInfo](arkts-arkdata-clouddata-dbactioninfo-i-sys.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
