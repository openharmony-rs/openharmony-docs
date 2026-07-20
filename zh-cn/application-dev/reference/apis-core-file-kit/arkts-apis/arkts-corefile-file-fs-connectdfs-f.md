# connectDfs

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="connectdfs"></a>
## connectDfs

```TypeScript
declare function connectDfs(networkId: string, listeners: DfsListeners): Promise<void>
```

业务调用connectDfs接口，触发建链。如果对端设备出现异常，业务执行回调DfsListeners内[onStatus](docroot://reference/apis-core-file-kit/js-apis-file-fs.md#onstatus12)通知应用。

**起始版本：** 12

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-unnamed-declare function connectDfs(networkId: string, listeners: DfsListeners): Promise<void>--><!--Device-unnamed-declare function connectDfs(networkId: string, listeners: DfsListeners): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络Id。通过[distributedDeviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributeddevicemanager.md)接口调用[DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md)获得。 |
| listeners | [DfsListeners](arkts-corefile-file-fs-dfslisteners-i.md) | 是 | 分布式文件系统状态监听器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900045 | Connection failed. |
| 13900046 | Software caused connection abort. |

