# getBtConnectionState

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getBtConnectionState

```TypeScript
function getBtConnectionState(): ProfileConnectionState
```

获取蓝牙本端的Profile连接状态，例如：任意一个支持的Profile连接状态为已连接，则此接口返回状态为已连接。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getBtConnectionState](arkts-connectivity-bluetoothmanager-getbtconnectionstate-f.md)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md) | 表示蓝牙设备的Profile连接状态。 |

**示例**

```TypeScript
let connectionState : bluetooth.ProfileConnectionState = bluetooth.getBtConnectionState();
```
