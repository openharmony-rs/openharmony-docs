# createKVManager

## 导入模块

```TypeScript
```

## createKVManager

```TypeScript
function createKVManager(config: KVManagerConfig, callback: AsyncCallback<KVManager>): void
```

创建一个KVManager对象实例，用于管理数据库对象，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** createKVManager

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [KVManagerConfig](arkts-arkdata-distributeddata-kvmanagerconfig-i.md) | 是 | 提供KVManager实例的配置信息，包括调用方的Bundle名称和用户信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KVManager](arkts-arkdata-distributeddata-kvmanager-i.md)&gt; | 是 | 回调函数。返回创建的KVManager对象实例。 |

**示例**

```TypeScript
let kvManager;
try {
    const kvManagerConfig = {
        bundleName : 'com.example.datamanagertest',
        userInfo : {
            userId : '0',
            userType : distributedData.UserType.SAME_USER_ID
        }
    }
    distributedData.createKVManager(kvManagerConfig, function (err, manager) {
        if (err) {
            console.error("Failed to create KVManager: "  + JSON.stringify(err));
            return;
        }
        console.info("Succeeded in creating KVManager");
        kvManager = manager;
    });
} catch (e) {
    console.error("An unexpected error occurred. Error:" + e);
}
```

```TypeScript
try {
  const kvManagerConfig = {
    bundleName: 'com.example.datamanagertest',
    userInfo: {
      userId: '0',
      userType: distributedData.UserType.SAME_USER_ID
    }
  }
  distributedData.createKVManager(kvManagerConfig).then((manager) => {
    console.info("Succeeded in creating KVManager");
    kvManager = manager;
  }).catch((err) => {
    console.error("Failed to create KVManager: " + JSON.stringify(err));
  });
} catch (e) {
  console.error("An unexpected error occurred. Error:" + e);
}
```


## createKVManager

```TypeScript
function createKVManager(config: KVManagerConfig): Promise<KVManager>
```

创建一个KVManager对象实例，用于管理数据库对象，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** createKVManager

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [KVManagerConfig](arkts-arkdata-distributeddata-kvmanagerconfig-i.md) | 是 | 提供KVManager实例的配置信息，包括调用方的包名和用户信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[KVManager](arkts-arkdata-distributeddata-kvmanager-i.md)&gt; | Promise对象。返回创建的KVManager对象实例。 |

**示例**

参见 [createKVManager](#createkvmanager)
