# connectDfs

## connectDfs

```TypeScript
declare function connectDfs(networkId: string, listeners: DfsListeners): Promise<void>
```

业务调用connectDfs接口，触发建链。如果对端设备出现异常，业务执行回调DfsListeners内
[onStatus](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#onstatus12)通知应用。

**起始版本：** 12

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络Id。通过<br/>[distributedDeviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributeddevicemanager.md#distributedDeviceManager)接口调用<br/>[DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md#DeviceBasicInfo)获得。 |
| listeners | DfsListeners | 是 | 分布式文件系统状态监听器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-The) | The parameter check failed.Possible causes:<br/>1.Mandatory parameters are left unspecified;<br/><br/>2.Incorrect parameter types. |
| [13900045](../../errorcode-universal.md#13900045-Connection) | Connection failed. |
| [13900046](../../errorcode-universal.md#13900046-Software) | Software caused connection abort. |

