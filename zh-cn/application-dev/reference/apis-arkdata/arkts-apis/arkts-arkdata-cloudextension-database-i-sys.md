# Database（系统接口）

数据库结构信息。

**起始版本：** 11

<!--Device-cloudExtension-export interface Database--><!--Device-cloudExtension-export interface Database-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## alias

```TypeScript
alias: string
```

该数据库在服务器中的别名。

**类型：** string

**起始版本：** 11

<!--Device-Database-alias: string--><!--Device-Database-alias: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

数据库名称。

**类型：** string

**起始版本：** 11

<!--Device-Database-name: string--><!--Device-Database-name: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## tables

```TypeScript
tables: Array<Table>
```

数据库中的表，包含数据详细信息。

**类型：** Array<Table>

**起始版本：** 11

<!--Device-Database-tables: Array<Table>--><!--Device-Database-tables: Array<Table>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

