# cancelPairedDevice（系统接口）

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## cancelPairedDevice

```TypeScript
function cancelPairedDevice(deviceId: string): boolean
```

删除配对的远程设备。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [cancelPairedDevice](arkts-connectivity-bluetoothmanager-cancelpaireddevice-f-sys.md)

**需要权限：** ohos.permission.DISCOVER_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示要删除的远程设备的地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 启动取消配对，成功返回true，否则返回false。 |

**示例**

```TypeScript
let result : boolean = bluetooth.cancelPairedDevice("XX:XX:XX:XX:XX:XX");
```
