# createCloudDBStub（系统接口）

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## createCloudDBStub

```TypeScript
function createCloudDBStub(instance: CloudDB): Promise<rpc.RemoteObject>
```

根据CloudDB类的实例创建对应的RemoteObject对象，系统内部通过该对象调用CloudDB的实现接口，使用Promise异步回调。

**起始版本：** 23

<!--Device-cloudExtension-function createCloudDBStub(instance: CloudDB): Promise<rpc.RemoteObject>--><!--Device-cloudExtension-function createCloudDBStub(instance: CloudDB): Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | [CloudDB](arkts-arkdata-cloudextension-clouddb-i-sys.md) | 是 | CloudDB类的实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;rpc.RemoteObject&gt; | Promise对象，返回CloudDB的rpc.RemoteObject对象。 |

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
    return {
      code: 0,
      value: {
        values: [],
        hasMore: false,
        nextCursor: ""
      } as cloudExtension.CloudData
    };
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

