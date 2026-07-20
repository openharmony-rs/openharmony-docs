# createCloudServiceStub（系统接口）

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

<a id="createcloudservicestub"></a>
## createCloudServiceStub

```TypeScript
function createCloudServiceStub(instance: CloudService): Promise<rpc.RemoteObject>
```

根据CloudService类的实例创建对应的RemoteObject对象，系统内部通过该对象调用CloudService的实现接口。使用Promise异步回调。

**起始版本：** 11

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

**示例：**

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

