# createBleScanner

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## createBleScanner

```TypeScript
function createBleScanner(): BleScanner
```

创建一个[BleScanner](arkts-connectivity-ble-blescanner-i.md)实例对象，可用于发起或停止BLE扫描等流程。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BleScanner](arkts-connectivity-ble-blescanner-i.md) | 返回一个BleScanner的实例。 |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { ble } from '@kit.ConnectivityKit';
let bleScanner: ble.BleScanner = ble.createBleScanner();
console.info('create bleScanner success');
```
