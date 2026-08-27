# ExtraData（系统接口）

透传数据，携带通知数据变更所需要的信息。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## eventId

```TypeScript
eventId: string
```

事件标识。当前仅支持"cloud_data_change"，表示云数据变更，传入其他值视为无效参数。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## extraData

```TypeScript
extraData: string
```

透传数据，extraData为JSON结构的字符串，其中必须包括"data"字段，"data"中是通知变更所需要的信息，包含账号、应用包名、数据库名、数据库类型和数据库表名，所有字段均不能为空。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
// accountId: 用户打开的云账号ID
// bundleName: 应用包名
// containerName: 云上数据库名称
// databaseScopes: 云上数据库类型
// recordTypes: 云上数据库表名

let extraData: cloudData.ExtraData = {
  eventId: "cloud_data_change",
  extraData: '{"data": "{"accountId": "aaa", "bundleName": "com.bbb.xxx", "containerName": "alias", "databaseScopes": ["private", "shared"], "recordTypes": ["xxx", "yyy", "zzz"]}"}',
};
```
