# setLocalName

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## setLocalName

```TypeScript
function setLocalName(name: string): boolean
```

设置蓝牙本地设备名称。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setLocalName](arkts-connectivity-bluetoothmanager-setlocalname-f.md)

**需要权限：** ohos.permission.DISCOVER_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要设置的蓝牙名称，最大长度为248字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 设置蓝牙本地设备名称，成功返回true，否则返回false。 |

**示例**

```TypeScript
let ret : boolean = bluetooth.setLocalName('device_name');
```
