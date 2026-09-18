# getState

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getState

```TypeScript
function getState(): BluetoothState
```

获取蓝牙开关状态。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getState](arkts-connectivity-bluetoothmanager-getstate-f.md)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BluetoothState](arkts-connectivity-bluetooth-bluetoothstate-e.md) | 表示蓝牙开关状态。 |

**示例**

```TypeScript
let state : bluetooth.BluetoothState = bluetooth.getState();
```
