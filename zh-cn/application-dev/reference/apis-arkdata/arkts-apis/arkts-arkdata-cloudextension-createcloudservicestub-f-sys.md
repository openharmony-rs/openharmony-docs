# createCloudServiceStub（系统接口）

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## createCloudServiceStub

```TypeScript
function createCloudServiceStub(instance: CloudService): Promise<rpc.RemoteObject>
```

根据CloudService类的实例创建对应的RemoteObject对象，系统内部通过该对象调用CloudService的实现接口。使用Promise异步回调。

**起始版本：** 23

<!--Device-cloudExtension-function createCloudServiceStub(instance: CloudService): Promise<rpc.RemoteObject>--><!--Device-cloudExtension-function createCloudServiceStub(instance: CloudService): Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | [CloudService](arkts-arkdata-cloudextension-cloudservice-i-sys.md) | 是 | CloudService类的实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;rpc.RemoteObject&gt; | Promise对象，返回CloudService的RemoteObject对象。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { Want, ServiceExtensionAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  async connectShareCenter(userId: number, bundleName: string): Promise<rpc.RemoteObject> {
    // ...
  }
}

export default class MyServiceExtension extends ServiceExtensionAbility {
  onCreate(want: Want) {
    console.info(`onCreate: ${want}`);
  }
  onRequest(want: Want, startId: number) {
    console.info(`onRequest: ${want} ${startId}`);
  }
  onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject> {
    console.info(`onConnect: ${want}`);
    return cloudExtension.createCloudServiceStub(new MyCloudService());
  }
  onDisconnect(want: Want) {
    console.info(`onDisconnect: ${want}`);
  }
  onDestroy() {
    console.info('onDestroy');
  }
}
```

ArkTS-Sta示例：

```TypeScript
import ServiceExtensionAbility from '@ohos.app.ability.ServiceExtensionAbility';
import Want from '@ohos.app.ability.Want';
import rpc from '@ohos.rpc';
import cloudExtension from '@ohos.data.cloudExtension';
class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
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
  async connectDB(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async connectAssetLoader(bundleName: string, dbInfo: cloudExtension.Database): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.SubscribeInfo>;
  }
}

export default class MyServiceExtension extends ServiceExtensionAbility {
  onCreate(want: Want) {
    console.info(`onCreate: ${want}`);
  }
  onRequest(want: Want, startId: int) {
    console.info(`onRequest: ${want} ${startId}`);
  }
  onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject> {
    console.info(`onConnect: ${want}`);
    return cloudExtension.createCloudServiceStub(new MyCloudService());
  }
  async onDisconnect(want: Want) {
    console.info(`onDisconnect: ${want}`);
  }
  onDestroy() {
    console.info('onDestroy');
  }
}
```

