# createAssetLoaderStub（系统接口）

## createAssetLoaderStub

```TypeScript
function createAssetLoaderStub(instance: AssetLoader): Promise<rpc.RemoteObject>
```

根据AssetLoader类的实例创建对应的RemoteObject对象，系统内部通过该对象调用AssetLoader的实现接口，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cloudExtension-function createAssetLoaderStub(instance: AssetLoader): Promise<rpc.RemoteObject>--><!--Device-cloudExtension-function createAssetLoaderStub(instance: AssetLoader): Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | [AssetLoader](arkts-arkdata-cloudextension-assetloader-i-sys.md) | 是 | 表示一个AssetLoader类型的实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;rpc.RemoteObject&gt; | Promise对象，返回AssetLoader的rpc.RemoteObject对象。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';

class MyAssetLoader implements cloudExtension.AssetLoader {
  // ...
}

class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  // ...   
  async connectAssetLoader(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
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
class EmptyRemoteObj extends rpc.RemoteObject {
  constructor() {
    super("EmptyRemoteObj");
  }
}
export default class MyCloudService implements cloudExtension.CloudService {
  constructor() {}
  // ...
  async connectAssetLoader(bundleName: string, database: cloudExtension.Database): Promise<rpc.RemoteObject> {
    console.info(`connect asset loader, bundle: ${bundleName}`);
    return cloudExtension.createAssetLoaderStub(new MyAssetLoader());
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
    return new EmptyRemoteObj();
  }
  async subscribe(subInfo: Record<string, Array<cloudExtension.Database>>, expirationTime: long): Promise<cloudExtension.Result<cloudExtension.SubscribeInfo>> {
    return { code: 0 } as cloudExtension.Result<cloudExtension.SubscribeInfo>;
  }
  async connectShareCenter(userId: int, bundleName: string): Promise<rpc.RemoteObject> {
    return new rpc.RemoteObject('');
  }
}
```

