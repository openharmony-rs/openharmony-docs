# getPairedDevices

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getPairedDevices

```TypeScript
function getPairedDevices(): Array<string>
```

获取蓝牙配对列表。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getPairedDevices](arkts-connectivity-bluetoothmanager-getpaireddevices-f.md)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 已配对蓝牙设备的地址列表。 |

**示例**

```TypeScript
let devices : Array<string> = bluetooth.getPairedDevices();
```
