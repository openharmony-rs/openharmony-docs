# getLocalName

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getLocalName

```TypeScript
function getLocalName(): string
```

获取蓝牙本地设备名称。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getLocalName](arkts-connectivity-bluetoothmanager-getlocalname-f.md)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 蓝牙本地设备名称。 |

**示例**

```TypeScript
let localName : string = bluetooth.getLocalName();
```
