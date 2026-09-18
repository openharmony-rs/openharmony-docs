# createShareServiceStub (System API)

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## createShareServiceStub

```TypeScript
function createShareServiceStub(instance: ShareCenter): Promise<rpc.RemoteObject>
```

Creates a RemoteObject instance based on a ShareCenter instance. The system uses this object to call the APIs of the ShareCenter instance. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | [ShareCenter](arkts-arkdata-cloudextension-sharecenter-i-sys.md) | Yes | Instance of the ShareCenter class. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)&gt; | Promise used to return the RemoteObject instance of ShareCenter. |

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
