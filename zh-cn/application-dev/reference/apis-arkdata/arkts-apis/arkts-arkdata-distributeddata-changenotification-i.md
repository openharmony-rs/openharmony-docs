# ChangeNotification

数据变更时通知的对象，包括数据插入的数据、更新的数据、删除的数据和设备ID。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** ChangeNotification

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## 导入模块

```TypeScript
```

## deleteEntries

```TypeScript
deleteEntries: Entry[]
```

数据删除记录。

**类型：** Entry[]

**起始版本：** 7

**废弃版本：** 9

**替代接口：** deleteEntries

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## deviceId

```TypeScript
deviceId: string
```

设备ID，此处为设备UUID。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** deviceId

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**示例**

```TypeScript
try {
    let query = new distributedData.Query();
    query.deviceId("deviceId");
    console.log("query is " + query.getSqlLike());
} catch (e) {
    console.log("should be ok on Method Chaining : " + e);
}
```

## insertEntries

```TypeScript
insertEntries: Entry[]
```

数据添加记录。

**类型：** Entry[]

**起始版本：** 7

**废弃版本：** 9

**替代接口：** insertEntries

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## updateEntries

```TypeScript
updateEntries: Entry[]
```

数据更新记录。

**类型：** Entry[]

**起始版本：** 7

**废弃版本：** 9

**替代接口：** updateEntries

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core
