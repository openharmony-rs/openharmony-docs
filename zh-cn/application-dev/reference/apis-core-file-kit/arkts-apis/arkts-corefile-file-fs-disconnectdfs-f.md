# disconnectDfs

## disconnectDfs

```TypeScript
declare function disconnectDfs(networkId: string): Promise<void>
```

业务调用disconnectDfs接口，传入networkId参数，触发断链。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-unnamed-declare function disconnectDfs(networkId: string): Promise<void>--><!--Device-unnamed-declare function disconnectDfs(networkId: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络Id。通过 [distributedDeviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributeddevicemanager.md#@ohos.distributedDeviceManager)接口调用 [DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md#DeviceBasicInfo)获得。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed.Possible causes: 1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 13600004 | Unmount failed. |

