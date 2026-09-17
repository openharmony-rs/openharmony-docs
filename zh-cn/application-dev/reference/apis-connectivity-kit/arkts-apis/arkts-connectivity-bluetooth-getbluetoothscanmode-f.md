# getBluetoothScanMode

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getBluetoothScanMode

```TypeScript
function getBluetoothScanMode(): ScanMode
```

获取蓝牙扫描模式。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getBluetoothScanMode](arkts-connectivity-bluetoothmanager-getbluetoothscanmode-f.md)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScanMode](arkts-connectivity-bluetooth-scanmode-e.md) | 蓝牙扫描模式。 |

**示例**

```TypeScript
let scanMode : bluetooth.ScanMode = bluetooth.getBluetoothScanMode();
```
