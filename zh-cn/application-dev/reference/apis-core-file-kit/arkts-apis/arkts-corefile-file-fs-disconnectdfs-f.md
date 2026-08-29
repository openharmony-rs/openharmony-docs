# disconnectDfs

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## disconnectDfs

```TypeScript
declare function disconnectDfs(networkId: string): Promise<void>
```

业务调用disconnectDfs接口，传入networkId参数，触发断链。

**起始版本：** 12

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络Id。通过 distributedDeviceManager接口调用 DeviceBasicInfo获得。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed.Possible causes: 1.Mandatory parameters are left unspecified;  2.Incorrect parameter types. |
| 13600004 | Unmount failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { distributedDeviceManager } from '@kit.DistributedServiceKit';

let dmInstance = distributedDeviceManager.createDeviceManager("com.example.filesync");
let deviceInfoList: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
if (deviceInfoList && deviceInfoList.length > 0) {
  console.info(`Succeeded in getting available device list.`);
  let networkId = deviceInfoList[0].networkId;
  fileIo.disconnectDfs(networkId).then(() => {
    console.info("Succeeded in disconnecting dfs.");
  }).catch((err: BusinessError) => {
    console.error(`Failed to disconnect dfs. Code: ${err.code}, message: ${err.message}`);
  })
}
```
