# isBluetoothSupported

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## isBluetoothSupported

```TypeScript
function isBluetoothSupported(): boolean
```

查询本机是否支持蓝牙能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询本机是否支持蓝牙能力。true 表示本机支持蓝牙能力，false 表示本机不支持蓝牙能力。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
try {
    let isSupported: boolean = access.isBluetoothSupported();
    console.info("isSupported: " + isSupported);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
