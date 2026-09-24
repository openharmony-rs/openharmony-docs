# createKVManager

## Modules to Import

```TypeScript
```

## createKVManager

```TypeScript
function createKVManager(config: KVManagerConfig, callback: AsyncCallback<KVManager>): void
```

Creates a **KVManager** instance to manage KV stores. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** createKVManager

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [KVManagerConfig](arkts-arkdata-distributeddata-kvmanagerconfig-i.md) | Yes | Configuration of the **KVManager** instance, including the bundle name and user information of the caller. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KVManager](arkts-arkdata-distributeddata-kvmanager-i.md)&gt; | Yes | Callback used to return the **KVManager** instance created. |

**Examples**

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


<a id="createkvmanager-1"></a>

## createKVManager

```TypeScript
function createKVManager(config: KVManagerConfig): Promise<KVManager>
```

Creates a **KVManager** instance to manage KV stores. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** createKVManager

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [KVManagerConfig](arkts-arkdata-distributeddata-kvmanagerconfig-i.md) | Yes | Configuration of the **KVManager** instance, including the bundle name and user information of the caller. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[KVManager](arkts-arkdata-distributeddata-kvmanager-i.md)&gt; | Promise used to return the **KVManager** instance created. |

**Examples**

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
