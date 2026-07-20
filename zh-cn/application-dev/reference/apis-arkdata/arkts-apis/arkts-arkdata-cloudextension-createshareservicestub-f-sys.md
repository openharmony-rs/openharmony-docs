# createShareServiceStub（系统接口）

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

<a id="createshareservicestub"></a>
## createShareServiceStub

```TypeScript
function createShareServiceStub(instance: ShareCenter): Promise<rpc.RemoteObject>
```

根据ShareCenter类的实例创建对应的RemoteObject对象，系统内部通过该对象调用ShareCenter的实现接口，使用Promise异步回调。

**起始版本：** 11

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

