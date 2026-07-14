# createRemoteDevice

## createRemoteDevice

```TypeScript
function createRemoteDevice(address: string): RemoteDevice
```

创建远端设备实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string | 是 | 设备地址。例如，“11:22:33:AA:BB:FF”<br>长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RemoteDevice | 返回近链路远程设备实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| 36100041 | Invalid address. |

