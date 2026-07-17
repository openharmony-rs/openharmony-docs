# BindInfo

数据库的绑定信息。当前版本只支持关系型数据库的绑定。

**起始版本：** 11

<!--Device-distributedDataObject-interface BindInfo--><!--Device-distributedDataObject-interface BindInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## 导入模块

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## assetName

```TypeScript
assetName: string
```

待绑定资产在所属的数据库中的资产名。

**类型：** string

**起始版本：** 11

<!--Device-BindInfo-assetName: string--><!--Device-BindInfo-assetName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## field

```TypeScript
field: string
```

待绑定资产在所属的数据库中的列名。

**类型：** string

**起始版本：** 11

<!--Device-BindInfo-field: string--><!--Device-BindInfo-field: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## primaryKey

```TypeScript
primaryKey: commonType.ValuesBucket
```

待绑定资产在所属的数据库中的主键。

**类型：** commonType.ValuesBucket

**起始版本：** 11

<!--Device-BindInfo-primaryKey: commonType.ValuesBucket--><!--Device-BindInfo-primaryKey: commonType.ValuesBucket-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## storeName

```TypeScript
storeName: string
```

待绑定资产在所属的数据库中的库名。

**类型：** string

**起始版本：** 11

<!--Device-BindInfo-storeName: string--><!--Device-BindInfo-storeName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## tableName

```TypeScript
tableName: string
```

待绑定资产在所属的数据库中的表名。

**类型：** string

**起始版本：** 11

<!--Device-BindInfo-tableName: string--><!--Device-BindInfo-tableName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

