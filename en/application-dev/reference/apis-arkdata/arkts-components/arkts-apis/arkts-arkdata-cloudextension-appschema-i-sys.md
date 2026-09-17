# AppSchema (System API)

Represents the application database schema.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## databases

```TypeScript
databases: Array<Database>
```

Database information of the application.

**Type:** Array&lt;[Database](arkts-arkdata-cloudextension-database-i-sys.md)&gt;

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## version

```TypeScript
version: number
```

Version of the database schema.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
