# CloudService (System API)

```TypeScript
export interface CloudService
```

Provides APIs for interacting with the cloud sync service. You need to inherit this class and implement APIs of this class. The system calls these APIs to connect to the cloud and use the cloud sync service.

**Since:** 11

<!--Device-cloudExtension-export interface CloudService--><!--Device-cloudExtension-export interface CloudService-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## connectAssetLoader

```TypeScript
connectAssetLoader(bundleName: string, database: Database): Promise<rpc.RemoteObject>
```

Connects to an asset loader by obtaining a RemoteObject instance of AssetLoader, which is created by using createAssetLoaderStub. This API uses a promise to return the result.

**Since:** 11

<!--Device-CloudService-connectAssetLoader(bundleName: string, database: Database): Promise<rpc.RemoteObject>--><!--Device-CloudService-connectAssetLoader(bundleName: string, database: Database): Promise<rpc.RemoteObject>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| database | [Database](arkts-arkdata-cloudextension-database-i-sys.md) | Yes | Database to connect. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)&gt; | Promise used to return the RemoteObject instance of AssetLoader. |

<!--Del-->
**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';

class MyAssetLoader implements cloudExtension.AssetLoader {
  // ...
}

class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  async connectAssetLoader(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    // ...
    console.info(`connect asset loader, bundle: ${bundleName}`);
    return cloudExtension.createAssetLoaderStub(new MyAssetLoader());
  }
}
```

<!--DelEnd-->

## connectDB

```TypeScript
connectDB(bundleName: string, database: Database): Promise<rpc.RemoteObject>
```

Connects to a cloud database by obtaining a RemoteObject instance of CloudDB, which is created by using createCloudDBStub. This API uses a promise to return the result.

**Since:** 11

<!--Device-CloudService-connectDB(bundleName: string, database: Database): Promise<rpc.RemoteObject>--><!--Device-CloudService-connectDB(bundleName: string, database: Database): Promise<rpc.RemoteObject>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| database | [Database](arkts-arkdata-cloudextension-database-i-sys.md) | Yes | Database to connect. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)&gt; | Promise used to return the RemoteObject instance of CloudDB. |

<!--Del-->
**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';

class MyCloudDB implements cloudExtension.CloudDB {
  // ...
}

class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
    // ...
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    console.info(`connect DB, bundleName: ${bundleName}`);
    return cloudExtension.createCloudDBStub(new MyCloudDB());
  }
}
```

<!--DelEnd-->

## connectShareCenter

```TypeScript
connectShareCenter(userId: number, bundleName: string): Promise<rpc.RemoteObject>
```

Connects to ShareCenter by obtaining a RemoteObject instance of ShareCenter, which is created by using createShareServiceStub. This API uses a promise to return the result.

**Since:** 11

<!--Device-CloudService-connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject>--><!--Device-CloudService-connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| bundleName | string | Yes | Bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)&gt; | Promise used to return the RemoteObject instance of ShareCenter. |

<!--Del-->
**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';

class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  // ...
}

class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  async connectShareCenter(userId: number, bundleName: string): Promise<rpc.RemoteObject> {
    console.info(`connect share center, bundle: ${bundleName}`);
    return cloudExtension.createShareServiceStub(new MyShareCenter());
  }
}
```

<!--DelEnd-->

## getAppBriefInfo

```TypeScript
getAppBriefInfo(): Promise<Record<string, AppBriefInfo>>
```

Obtains brief application information. This API uses a promise to return the result.

**Since:** 11

<!--Device-CloudService-getAppBriefInfo(): Promise<Record<string, AppBriefInfo>>--><!--Device-CloudService-getAppBriefInfo(): Promise<Record<string, AppBriefInfo>>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Record&lt;string, [AppBriefInfo](arkts-arkdata-cloudextension-appbriefinfo-i-sys.md)&gt;&gt; | Promise used to return a key-value pair, where the key is **bundleName** and the value is AppBriefInfo. |

<!--Del-->
**Examples**

```TypeScript
class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  // ...
  async getAppBriefInfo(): Promise<Record<string, cloudExtension.AppBriefInfo>> {
    console.info(`get app brief info`);
    // ...
    return {
      "test_bundle":
      {
        appId: "test_appID",
        bundleName: "test_bundlename",
        cloudSwitch: true,
        instanceId: 0,
      }
    };
  }
}
```

<!--DelEnd-->

## getAppSchema

```TypeScript
getAppSchema(bundleName: string): Promise<Result<AppSchema>>
```

Obtains the application database schema information. This API uses a promise to return the result.

**Since:** 11

<!--Device-CloudService-getAppSchema(bundleName: string): Promise<Result<AppSchema>>--><!--Device-CloudService-getAppSchema(bundleName: string): Promise<Result<AppSchema>>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;[AppSchema](arkts-arkdata-cloudextension-appschema-i-sys.md)&gt;&gt; | Promise used to return the schema information obtained. |

<!--Del-->
**Examples**

```TypeScript
class MyCloudService implements cloudExtension.CloudService {
  constructor() {
  }
  // ...
  async getAppSchema(bundleName: string): Promise<cloudExtension.Result<cloudExtension.AppSchema>> {
    console.info(`get app schema, bundleName:${bundleName}`);
    // ...
    return {
      code: cloudExtension.ErrorCode.SUCCESS,
      description: "get app schema success",
      value: {
        bundleName: "test_bundleName",
        version: 1,
        databases: []
      }
    };
  }
}
```

<!--DelEnd-->

## getServiceInfo

```TypeScript
getServiceInfo(): Promise<ServiceInfo>
```

Obtains the server information. This API uses a promise to return the result.

**Since:** 11

<!--Device-CloudService-getServiceInfo(): Promise<ServiceInfo>--><!--Device-CloudService-getServiceInfo(): Promise<ServiceInfo>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ServiceInfo](arkts-arkdata-cloudextension-serviceinfo-i-sys.md)&gt; | Promise used to return the server information obtained. |

<!--Del-->
**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';

let testSpace: number = 100;
let testUserId: number = 1;

class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  // ...
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    console.info(`get service info`);
    // ...
    return {
      enableCloud: true,
      id: "test_id",
      totalSpace: testSpace,
      remainingSpace: testSpace,
      user: testUserId,
    };
  }
}
```

<!--DelEnd-->

## subscribe

```TypeScript
subscribe(
      subInfo: Record<string, Array<Database>>,
      expirationTime: number
    ): Promise<Result<SubscribeInfo>>
```

Subscribes to the cloud database change notification. This API uses a promise to return the result.

**Since:** 11

<!--Device-CloudService-subscribe(      subInfo: Record<string, Array<Database>>,      expirationTime: long    ): Promise<Result<SubscribeInfo>>--><!--Device-CloudService-subscribe(      subInfo: Record<string, Array<Database>>,      expirationTime: long    ): Promise<Result<SubscribeInfo>>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subInfo | Record&lt;string, Array&lt;[Database](arkts-arkdata-cloudextension-database-i-sys.md)&gt;&gt; | Yes | Data to be subscribed to, in KV pairs of the application bundle name and database information. |
| expirationTime | number | Yes | Subscription expiration time, in ms. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;[SubscribeInfo](arkts-arkdata-cloudextension-subscribeinfo-i-sys.md)&gt;&gt; | Promise used to return the result, including the subscription expiration time and subscription information. |

<!--Del-->
**Examples**

```TypeScript
let testTime: number = 10;
class MyCloudService implements cloudExtension.CloudService {
  constructor() {
  }
  // ...
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: number): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    console.info(`subscribe expirationTime: ${expirationTime}`);
    // ...
    return {
      code: cloudExtension.ErrorCode.SUCCESS,
      description: "subscribe success",
      value: {
        expirationTime: testTime,
        subscribe: {}
      }
    };
  }
}
```

<!--DelEnd-->

## unsubscribe

```TypeScript
unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<number>
```

Unsubscribes from the cloud data change notification. This API uses a promise to return the result.

**Since:** 11

<!--Device-CloudService-unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int>--><!--Device-CloudService-unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| unsubscribeInfo | Record&lt;string, Array&lt;string&gt;&gt; | Yes | Data to be unsubscribed from, in an array of KV pairs consisting of the application bundle name and database name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. |

<!--Del-->
**Examples**

```TypeScript
class MyCloudService implements cloudExtension.CloudService {
  constructor() {
  }
  // ...
  async unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<number> {
    console.info(`unsubscribe`);
    // ...
    return cloudExtension.ErrorCode.SUCCESS;
  }
}
```

<!--DelEnd-->
