# CloudService（系统接口）

提供对接同步云服务的类。开发者需要继承此类并实现类的接口，系统内部通过该类的接口连接并使用同步云服务。

**起始版本：** 11

<!--Device-cloudExtension-export interface CloudService--><!--Device-cloudExtension-export interface CloudService-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## connectAssetLoader

```TypeScript
connectAssetLoader(bundleName: string, database: Database): Promise<rpc.RemoteObject>
```

系统内部通过该接口获取AssetLoader的RemoteObject对象，可以通过createAssetLoaderStub接口进行创建，使用Promise异步回调。

**起始版本：** 11

<!--Device-CloudService-connectAssetLoader(bundleName: string, database: Database): Promise<rpc.RemoteObject>--><!--Device-CloudService-connectAssetLoader(bundleName: string, database: Database): Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。 |
| database | [Database](arkts-arkdata-cloudextension-database-i-sys.md) | 是 | 需要连接的数据库。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;rpc.RemoteObject&gt; | Promise对象，返回AssetLoader的RemoteObject对象。 |

**示例：**

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

## connectDB

```TypeScript
connectDB(bundleName: string, database: Database): Promise<rpc.RemoteObject>
```

系统内部通过该接口获取CloudDB的RemoteObject对象，可以通过createCloudDBStub接口进行创建，使用Promise异步回调。

**起始版本：** 11

<!--Device-CloudService-connectDB(bundleName: string, database: Database): Promise<rpc.RemoteObject>--><!--Device-CloudService-connectDB(bundleName: string, database: Database): Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。 |
| database | [Database](arkts-arkdata-cloudextension-database-i-sys.md) | 是 | 需要连接的数据库。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;rpc.RemoteObject&gt; | Promise对象，返回CloudDB的RemoteObject对象。 |

**示例：**

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

## connectShareCenter

```TypeScript
connectShareCenter(userId: number, bundleName: string): Promise<rpc.RemoteObject>
```

系统内部通过该接口获取ShareCenter的RemoteObject对象，可以通过createShareServiceStub接口进行创建，使用Promise异步回调。

**起始版本：** 11

<!--Device-CloudService-connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject>--><!--Device-CloudService-connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;rpc.RemoteObject&gt; | Promise对象，返回ShareCenter的RemoteObject对象。 |

**示例：**

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

## getAppBriefInfo

```TypeScript
getAppBriefInfo(): Promise<Record<string, AppBriefInfo>>
```

获取简要应用信息。使用Promise异步回调。

**起始版本：** 11

<!--Device-CloudService-getAppBriefInfo(): Promise<Record<string, AppBriefInfo>>--><!--Device-CloudService-getAppBriefInfo(): Promise<Record<string, AppBriefInfo>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, AppBriefInfo&gt;&gt; | Promise对象，返回以bundleName为键、AppBriefInfo为值的键值对。in KV pairs. |

**示例：**

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

## getAppSchema

```TypeScript
getAppSchema(bundleName: string): Promise<Result<AppSchema>>
```

获取应用Schema（数据库模式）信息。使用Promise异步回调。

**起始版本：** 11

<!--Device-CloudService-getAppSchema(bundleName: string): Promise<Result<AppSchema>>--><!--Device-CloudService-getAppSchema(bundleName: string): Promise<Result<AppSchema>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;AppSchema&gt;&gt; | Promise对象，返回数据库的schema信息。 |

**示例：**

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

## getServiceInfo

```TypeScript
getServiceInfo(): Promise<ServiceInfo>
```

获取服务器上的信息。使用Promise异步回调。

**起始版本：** 11

<!--Device-CloudService-getServiceInfo(): Promise<ServiceInfo>--><!--Device-CloudService-getServiceInfo(): Promise<ServiceInfo>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ServiceInfo&gt; | Promise对象，返回获取的服务器信息。 |

**示例：**

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

## subscribe

```TypeScript
subscribe(
      subInfo: Record<string, Array<Database>>,
      expirationTime: number
    ): Promise<Result<SubscribeInfo>>
```

订阅云数据库的变化通知。使用Promise异步回调。

**起始版本：** 11

<!--Device-CloudService-subscribe(      subInfo: Record<string, Array<Database>>,      expirationTime: long    ): Promise<Result<SubscribeInfo>>--><!--Device-CloudService-subscribe(      subInfo: Record<string, Array<Database>>,      expirationTime: long    ): Promise<Result<SubscribeInfo>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subInfo | Record&lt;string, Array&lt;Database&gt;&gt; | 是 | 需要订阅的数据，由应用包名称和数据库信息组成的键值对。 |
| expirationTime | number | 是 | 表示订阅到期时间（ms）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;SubscribeInfo&gt;&gt; | Promise对象，返回订阅的结果，包含订阅的过期时间和订阅信息。 |

**示例：**

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

## unsubscribe

```TypeScript
unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<number>
```

取消已订阅的云数据变化通知。使用Promise异步回调。

**起始版本：** 11

<!--Device-CloudService-unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int>--><!--Device-CloudService-unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unsubscribeInfo | Record&lt;string, Array&lt;string&gt;&gt; | 是 | 需要取消订阅的数据信息，由应用包名和数据库名组成的键值对。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回取消订阅结果的错误码。 |

**示例：**

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

