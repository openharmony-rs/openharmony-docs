# pairDevice

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## pairDevice

```TypeScript
function pairDevice(deviceId: string): boolean
```

发起蓝牙配对。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [pairDevice](arkts-connectivity-bluetoothmanager-pairdevice-f.md)

**需要权限：** ohos.permission.DISCOVER_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示配对的远端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 发起蓝牙配对，成功返回true，否则返回false。 |

**示例**

```TypeScript
// 实际的地址可由扫描流程获取
let result : boolean = bluetooth.pairDevice("XX:XX:XX:XX:XX:XX");
```
