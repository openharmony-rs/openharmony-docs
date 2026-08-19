# createShareServiceStub（系统接口）

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## createShareServiceStub

```TypeScript
function createShareServiceStub(instance: ShareCenter): Promise<rpc.RemoteObject>
```

根据ShareCenter类的实例创建对应的RemoteObject对象，系统内部通过该对象调用ShareCenter的实现接口，使用Promise异步回调。

**起始版本：** 23

<!--Device-cloudExtension-function createShareServiceStub(instance: ShareCenter): Promise<rpc.RemoteObject>--><!--Device-cloudExtension-function createShareServiceStub(instance: ShareCenter): Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | [ShareCenter](arkts-arkdata-cloudextension-sharecenter-i-sys.md) | 是 | ShareCenter类的实例。 |

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

