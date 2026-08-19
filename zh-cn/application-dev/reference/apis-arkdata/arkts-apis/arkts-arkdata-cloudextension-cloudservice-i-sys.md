# CloudService（系统接口）

提供对接同步云服务的类。开发者需要继承此类并实现类的接口，系统内部通过该类的接口连接并使用同步云服务。

**起始版本：** 23

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

**起始版本：** 23

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

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import cloudExtension from '@ohos.data.cloudExtension';
class MyAssetLoader implements cloudExtension.AssetLoader {
  // ...
  async download(table: string, gid: string, prefix: string, assets: cloudExtension.CloudAsset[]): Promise<cloudExtension.Result<cloudExtension.CloudAsset>[]> {
    return [] as cloudExtension.Result<cloudExtension.CloudAsset>[];
  }
  async upload(table: string, gid: string, assets: cloudExtension.CloudAsset[]): Promise<cloudExtension.Result<cloudExtension.CloudAsset>[]> {
    return [] as cloudExtension.Result<cloudExtension.CloudAsset>[];
  }
}

export default class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  async connectAssetLoader(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    // ...
    console.info(`connect asset loader, bundle: ${bundleName}`);
    return cloudExtension.createAssetLoaderStub(new MyAssetLoader());
  }
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new EmptyRemoteObj();
  }
  async unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int> {
    return 0;
  }
  async getAppBriefInfo(): Promise<Record<string, cloudExtension.AppBriefInfo>> {
    return {};
  }
  async getAppSchema(bundleName: string): Promise<cloudExtension.Result<cloudExtension.AppSchema>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.AppSchema>;
  }
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    return { remainingSpace: 0, totalSpace: 0, id: "", user: 0, enableCloud: false } as cloudExtension.ServiceInfo;
  }
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.SubscribeInfo>;
  }
}
class EmptyRemoteObj extends rpc.RemoteObject {
  constructor() {
    super("EmptyRemoteObj");
  }
}
```

## connectDB

```TypeScript
connectDB(bundleName: string, database: Database): Promise<rpc.RemoteObject>
```

系统内部通过该接口获取CloudDB的RemoteObject对象，可以通过createCloudDBStub接口进行创建，使用Promise异步回调。

**起始版本：** 23

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

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import cloudExtension from '@ohos.data.cloudExtension';

class MyCloudDB implements cloudExtension.CloudDB {
  // ...
  async generateId(count: int): Promise<cloudExtension.Result<string[]>> {
    return { code: 0, value: [] };
  }
  async query(table: string, fields: string[], queryCount: int, queryCursor: string): Promise<cloudExtension.Result<cloudExtension.CloudData>> {
    return { code: 0, value: { values: [], hasMore: false, nextCursor: "" } as cloudExtension.CloudData };
  }
  async insert(table: string, values: Array<Record<string, cloudExtension.CloudType>>, extValues: Array<Record<string, cloudExtension.CloudType>>): Promise<Array<cloudExtension.Result<Record<string, cloudExtension.CloudType>>>> {
    return [{ code: 0, value: {} } as cloudExtension.Result<Record<string, cloudExtension.CloudType>>];
  }
  async update(table: string, values: Array<Record<string, cloudExtension.CloudType>>, extValues: Array<Record<string, cloudExtension.CloudType>>): Promise<Array<cloudExtension.Result<Record<string, cloudExtension.CloudType>>>> {
    return [{ code: 0, value: {} } as cloudExtension.Result<Record<string, cloudExtension.CloudType>>];
  }
  async delete(table: string, values: Array<Record<string, cloudExtension.CloudType>>): Promise<Array<cloudExtension.Result<Record<string, cloudExtension.CloudType>>>> {
    return [{ code: 0, value: {} } as cloudExtension.Result<Record<string, cloudExtension.CloudType>>];
  }
  async lock(): Promise<cloudExtension.Result<cloudExtension.LockInfo>> {
    return { code: 0, value: { lockId: 0, interval: 0 } };
  }
  async unlock(sessionId: int): Promise<cloudExtension.Result<boolean>> {
    return { code: 0, value: true };
  }
  async heartbeat(sessionId: int): Promise<cloudExtension.Result<cloudExtension.LockInfo>> {
    return { code: 0, value: { lockId: 0, interval: 0 } };
  }
}

export default class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  // ...
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    console.info(`connect DB, bundleName: ${bundleName}`);
    return cloudExtension.createCloudDBStub(new MyCloudDB());
  }
  async unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int> {
    return 0;
  }
  async getAppBriefInfo(): Promise<Record<string, cloudExtension.AppBriefInfo>> {
    return {};
  }
  async getAppSchema(bundleName: string): Promise<cloudExtension.Result<cloudExtension.AppSchema>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.AppSchema>;
  }
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    return { remainingSpace: 0, totalSpace: 0, id: "", user: 0, enableCloud: false } as cloudExtension.ServiceInfo;
  }
  async connectAssetLoader(bundleName: string, dbInfo: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.SubscribeInfo>;
  }
}
```

## connectShareCenter

```TypeScript
connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject>
```

系统内部通过该接口获取ShareCenter的RemoteObject对象，可以通过createShareServiceStub接口进行创建，使用Promise异步回调。

**起始版本：** 23

<!--Device-CloudService-connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject>--><!--Device-CloudService-connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | int | 是 | 表示用户账号ID。 |
| bundleName | string | 是 | 应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;rpc.RemoteObject&gt; | Promise对象，返回ShareCenter的RemoteObject对象。 |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import cloudExtension from '@ohos.data.cloudExtension';
import cloudData from '@ohos.data.cloudData';
type Participant = cloudData.sharing.Participant;
class EmptyRemoteObj extends rpc.RemoteObject {
  constructor() {
    super("EmptyRemoteObj");
  }
}
class MyShareCenter implements cloudExtension.ShareCenter {
  constructor() {}
  // ...
  async share(userId: int, bundleName: string, sharingResource: string, participants: Array<Participant>):
    Promise<cloudExtension.Result<Array<cloudExtension.Result<Participant>>>> {
    return { code: 0, value: [] as Array<cloudExtension.Result<Participant>> };
  }
  async unshare(userId: int, bundleName: string, sharingResource: string, participants: Array<Participant>):
    Promise<cloudExtension.Result<Array<cloudExtension.Result<Participant>>>> {
    return { code: 0, value: [] as Array<cloudExtension.Result<Participant>> };
  }
  async exit(userId: int, bundleName: string, sharingResource: string): Promise<cloudExtension.Result<void>> {
    return { code: 0 };
  }
  async queryParticipants(userId: int, bundleName: string, sharingResource: string): Promise<cloudExtension.Result<Array<Participant>>> {
    return { code: 0, value: [] as Array<Participant> };
  }
  async queryParticipantsByInvitation(userId: int, bundleName: string, invitationCode: string): Promise<cloudExtension.Result<Array<Participant>>> {
    return { code: 0, value: [] as Array<Participant> };
  }
  async changePrivilege(userId: int, bundleName: string, sharingResource: string, participants: Array<Participant>): Promise<cloudExtension.Result<Array<cloudExtension.Result<Participant>>>> {
    return { code: 0, value: [] as Array<cloudExtension.Result<Participant>> };
  }
  async changeConfirmation(userId: int, bundleName: string, sharingResource: string, state: cloudData.sharing.State): Promise<cloudExtension.Result<void>> {
    return { code: 0 };
  }
  async confirmInvitation(userId: int, bundleName: string, invitationCode: string, state: cloudData.sharing.State): Promise<cloudExtension.Result<string>> {
    return { code: 0, value: '' };
  }
}

export default class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    console.info(`connect share center, bundle: ${bundleName}`);
    return cloudExtension.createShareServiceStub(new MyShareCenter());
  }
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new EmptyRemoteObj();
  }
  async unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int> {
    return 0;
  }
  async getAppBriefInfo(): Promise<Record<string, cloudExtension.AppBriefInfo>> {
    return {};
  }
  async getAppSchema(bundleName: string): Promise<cloudExtension.Result<cloudExtension.AppSchema>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.AppSchema>;
  }
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    return { remainingSpace: 0, totalSpace: 0, id: "", user: 0, enableCloud: false } as cloudExtension.ServiceInfo;
  }
  async connectAssetLoader(bundleName: string, dbInfo: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.SubscribeInfo>;
  }
}
```

## getAppBriefInfo

```TypeScript
getAppBriefInfo(): Promise<Record<string, AppBriefInfo>>
```

获取简要应用信息。使用Promise异步回调。

**起始版本：** 23

<!--Device-CloudService-getAppBriefInfo(): Promise<Record<string, AppBriefInfo>>--><!--Device-CloudService-getAppBriefInfo(): Promise<Record<string, AppBriefInfo>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, [AppBriefInfo](arkts-arkdata-cloudextension-appbriefinfo-i-sys.md)&gt;&gt; | Promise对象，返回以bundleName为键、AppBriefInfo为值的键值对。 in KV pairs. |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import cloudExtension from '@ohos.data.cloudExtension';
import rpc from '@ohos.rpc';
class EmptyRemoteObj extends rpc.RemoteObject {
  constructor() {
    super("EmptyRemoteObj");
  }
}
export default class MyCloudService implements cloudExtension.CloudService {
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
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new EmptyRemoteObj();
  }
  async unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int> {
    return 0;
  }
  async getAppSchema(bundleName: string): Promise<cloudExtension.Result<cloudExtension.AppSchema>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.AppSchema>;
  }
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    return { remainingSpace: 0, totalSpace: 0, id: "", user: 0, enableCloud: false } as cloudExtension.ServiceInfo;
  }
  async connectAssetLoader(bundleName: string, dbInfo: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.SubscribeInfo>;
  }
}
```

## getAppSchema

```TypeScript
getAppSchema(bundleName: string): Promise<Result<AppSchema>>
```

获取应用Schema（数据库模式）信息。使用Promise异步回调。

**起始版本：** 23

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
| Promise&lt;Result&lt;[AppSchema](arkts-arkdata-cloudextension-appschema-i-sys.md)&gt;&gt; | Promise对象，返回数据库的schema信息。 |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import cloudExtension from '@ohos.data.cloudExtension';
import rpc from '@ohos.rpc';
class EmptyRemoteObj extends rpc.RemoteObject {
  constructor() {
    super("EmptyRemoteObj");
  }
}
export default class MyCloudService implements cloudExtension.CloudService {
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
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new EmptyRemoteObj();
  }
  async unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int> {
    return 0;
  }
  async getAppBriefInfo(): Promise<Record<string, cloudExtension.AppBriefInfo>> {
    return {};
  }
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    return { remainingSpace: 0, totalSpace: 0, id: "", user: 0, enableCloud: false } as cloudExtension.ServiceInfo;
  }
  async connectAssetLoader(bundleName: string, dbInfo: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.SubscribeInfo>;
  }
}
```

## getServiceInfo

```TypeScript
getServiceInfo(): Promise<ServiceInfo>
```

获取服务器上的信息。使用Promise异步回调。

**起始版本：** 23

<!--Device-CloudService-getServiceInfo(): Promise<ServiceInfo>--><!--Device-CloudService-getServiceInfo(): Promise<ServiceInfo>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ServiceInfo](arkts-arkdata-cloudextension-serviceinfo-i-sys.md)&gt; | Promise对象，返回获取的服务器信息。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';

let test_space: number = 100;
let test_userId: number = 1;

class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  // ...
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    console.info(`get service info`);
    // ...
    return {
      enableCloud: true,
      id: "test_id",
      totalSpace: test_space,
      remainingSpace: test_space,
      user: test_userId,
    };
  }
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import cloudExtension from '@ohos.data.cloudExtension';
let test_space: int = 100;
let test_userId: int = 1;
class EmptyRemoteObj extends rpc.RemoteObject {
  constructor() {
    super("EmptyRemoteObj");
  }
}
export default class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  // ...
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    console.info(`get service info`);
    // ...
    return {
      enableCloud: true,
      id: "test_id",
      totalSpace: test_space,
      remainingSpace: test_space,
      user: test_userId,
    };
  }
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new EmptyRemoteObj();
  }
  async unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int> {
    return 0;
  }
  async getAppBriefInfo(): Promise<Record<string, cloudExtension.AppBriefInfo>> {
    return {};
  }
  async getAppSchema(bundleName: string): Promise<cloudExtension.Result<cloudExtension.AppSchema>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.AppSchema>;
  }
  async connectAssetLoader(bundleName: string, dbInfo: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.SubscribeInfo>;
  }
}
```

## subscribe

```TypeScript
subscribe(
      subInfo: Record<string, Array<Database>>,
      expirationTime: long
    ): Promise<Result<SubscribeInfo>>
```

订阅云数据库的变化通知。使用Promise异步回调。

**起始版本：** 23

<!--Device-CloudService-subscribe(      subInfo: Record<string, Array<Database>>,      expirationTime: long    ): Promise<Result<SubscribeInfo>>--><!--Device-CloudService-subscribe(      subInfo: Record<string, Array<Database>>,      expirationTime: long    ): Promise<Result<SubscribeInfo>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subInfo | Record&lt;string, Array&lt;[Database](arkts-arkdata-cloudextension-database-i-sys.md)&gt;&gt; | 是 | 需要订阅的数据，由应用包名称和数据库信息组成的键值对。 |
| expirationTime | long | 是 | 表示订阅到期时间（ms）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;SubscribeInfo&gt;&gt; | Promise对象，返回订阅的结果，包含订阅的过期时间和订阅信息。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
let test_time: number = 10;
class MyCloudService implements cloudExtension.CloudService {
  constructor() {
  }
  // ...
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: number): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    console.info
    (`subscribe expirationTime: ${expirationTime}`);
    // ...
    return {
      code: cloudExtension.ErrorCode.SUCCESS,
      description: "subscribe success",
      value: {
        expirationTime: test_time,
        subscribe: {}
      }
    };
  }
}
```

ArkTS-Sta示例：

```TypeScript
import cloudExtension from '@ohos.data.cloudExtension';
import rpc from '@ohos.rpc';
let test_time: int = 10;
class EmptyRemoteObj extends rpc.RemoteObject {
  constructor() {
    super("EmptyRemoteObj");
  }
}
export default class MyCloudService implements cloudExtension.CloudService {
  constructor() {
  }
  // ...
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    console.info
    (`subscribe expirationTime: ${expirationTime}`);
    // ...
    return {
      code: cloudExtension.ErrorCode.SUCCESS,
      description: "subscribe success",
      value: {
        expirationTime: test_time,
        subscribe: {}
      }
    };
  }
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new EmptyRemoteObj();
  }
  async unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int> {
    return 0;
  }
  async getAppBriefInfo(): Promise<Record<string, cloudExtension.AppBriefInfo>> {
    return {};
  }
  async getAppSchema(bundleName: string): Promise<cloudExtension.Result<cloudExtension.AppSchema>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.AppSchema>;
  }
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    return { remainingSpace: 0, totalSpace: 0, id: "", user: 0, enableCloud: false } as cloudExtension.ServiceInfo;
  }
  async connectAssetLoader(bundleName: string, dbInfo: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
}
```

## unsubscribe

```TypeScript
unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int>
```

取消已订阅的云数据变化通知。使用Promise异步回调。

**起始版本：** 23

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
| Promise&lt;int&gt; | Promise对象，返回取消订阅结果的错误码。 |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import cloudExtension from '@ohos.data.cloudExtension';
class EmptyRemoteObj extends rpc.RemoteObject {
  constructor() {
    super("EmptyRemoteObj");
  }
}
export default class MyCloudService implements cloudExtension.CloudService {
  constructor() {
  }
  // ...
  async unsubscribe(unsubscribeInfo: Record<string, Array<string>>): Promise<int> {
    console.info(`unsubscribe`);
    // ...
    return cloudExtension.ErrorCode.SUCCESS;
  }
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new EmptyRemoteObj();
  }
  async getAppBriefInfo(): Promise<Record<string, cloudExtension.AppBriefInfo>> {
    return {};
  }
  async getAppSchema(bundleName: string): Promise<cloudExtension.Result<cloudExtension.AppSchema>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.AppSchema>;
  }
  async getServiceInfo(): Promise<cloudExtension.ServiceInfo> {
    return { remainingSpace: 0, totalSpace: 0, id: "", user: 0, enableCloud: false } as cloudExtension.ServiceInfo;
  }
  async connectAssetLoader(bundleName: string, dbInfo: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.SubscribeInfo>;
  }
}
```

