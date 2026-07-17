# Field（系统接口）

数据库中的字段结构。

**起始版本：** 11

<!--Device-cloudExtension-export interface Field--><!--Device-cloudExtension-export interface Field-End-->

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

该字段在服务器表中的别名。

**类型：** string

**起始版本：** 11

<!--Device-Field-alias: string--><!--Device-Field-alias: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## colName

```TypeScript
colName: string
```

列名。

**类型：** string

**起始版本：** 11

<!--Device-Field-colName: string--><!--Device-Field-colName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## nullable

```TypeScript
nullable: boolean
```

当前列是否允许为空值。true表示允许为空，false表示不允许为空。

**类型：** boolean

**起始版本：** 11

<!--Device-Field-nullable: boolean--><!--Device-Field-nullable: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## primary

```TypeScript
primary: boolean
```

当前列是否为主键。true表示是主键，false表示不是主键。

**类型：** boolean

**起始版本：** 11

<!--Device-Field-primary: boolean--><!--Device-Field-primary: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: FieldType
```

字段类型。

**类型：** FieldType

**起始版本：** 11

<!--Device-Field-type: FieldType--><!--Device-Field-type: FieldType-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

