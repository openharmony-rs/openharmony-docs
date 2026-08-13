# ConnectionEvent

```TypeScript
type ConnectionEvent = (state: ConnectionState, device: OutputDeviceInfo) => void
```

The connection event supplied by system to indicate device state and information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-avSession-type ConnectionEvent = (state: ConnectionState, device: OutputDeviceInfo) => void--><!--Device-avSession-type ConnectionEvent = (state: ConnectionState, device: OutputDeviceInfo) => void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | ConnectionState | 是 | 设备连接状态。 |
| device | [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md) | 是 | device information |

