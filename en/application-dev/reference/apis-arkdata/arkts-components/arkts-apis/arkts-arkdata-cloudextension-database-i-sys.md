# Database (System API)

```TypeScript
export interface Database
```

Represents the database information.

**Since:** 11

<!--Device-cloudExtension-export interface Database--><!--Device-cloudExtension-export interface Database-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## alias

```TypeScript
alias: string
```

Alias of the database on the server.

**Type:** string

**Since:** 11

<!--Device-Database-alias: string--><!--Device-Database-alias: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Name of the database.

**Type:** string

**Since:** 11

<!--Device-Database-name: string--><!--Device-Database-name: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## tables

```TypeScript
tables: Array<Table>
```

Table in the database, including the detailed data information.

**Type:** Array&lt;[Table](arkts-arkdata-cloudextension-table-i-sys.md)&gt;

**Since:** 11

<!--Device-Database-tables: Array<Table>--><!--Device-Database-tables: Array<Table>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
