# ClearConfig (System API)

```TypeScript
interface ClearConfig
```

Defines the database-level clearing rules for device-cloud synergy.

**Since:** 23

<!--Device-cloudData-interface ClearConfig--><!--Device-cloudData-interface ClearConfig-End-->

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

Information about the database whose data is to be cleared and the clearing rules. The key is the database name, and the value is the clearing rule of the database.

**Type:** Record&lt;string, [DBActionInfo](arkts-arkdata-clouddata-dbactioninfo-i-sys.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ClearConfig-dbInfo: Record<string, DBActionInfo>--><!--Device-ClearConfig-dbInfo: Record<string, DBActionInfo>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
