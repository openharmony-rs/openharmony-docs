# getRemoteDeviceName

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getRemoteDeviceName

```TypeScript
function getRemoteDeviceName(deviceId: string): string
```

获取对端蓝牙设备的名称。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getRemoteDeviceName](arkts-connectivity-bluetoothmanager-getremotedevicename-f.md)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示远程设备的地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 以字符串格式返回设备名称。 |

**示例**

```TypeScript
let remoteDeviceName : string = bluetooth.getRemoteDeviceName("XX:XX:XX:XX:XX:XX");
```
