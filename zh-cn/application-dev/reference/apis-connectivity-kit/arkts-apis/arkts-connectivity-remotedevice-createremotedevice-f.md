# createRemoteDevice

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## createRemoteDevice

```TypeScript
function createRemoteDevice(address: string): RemoteDevice
```

创建远端设备实例。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-remoteDevice-function createRemoteDevice(address: string): RemoteDevice--><!--Device-remoteDevice-function createRemoteDevice(address: string): RemoteDevice-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string | 是 | 远端设备地址。地址格式参考：11:22:33:AA:BB:FF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i.md) | 远端设备实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100041](../errorcode-nearlink-service.md#36100041-无效地址) | Invalid address. |
