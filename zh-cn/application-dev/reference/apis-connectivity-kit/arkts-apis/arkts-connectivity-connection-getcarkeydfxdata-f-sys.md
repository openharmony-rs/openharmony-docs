# getCarKeyDfxData（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## getCarKeyDfxData

```TypeScript
function getCarKeyDfxData(): string
```

获取车钥匙维测数据，例如蓝牙车钥匙连接、配对等维测数据。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 以字符串格式返回车钥匙维测数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API when the short-range chip is not inserted on the 2in1 device. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
try {
    let dfxData = connection.getCarKeyDfxData();
} catch (err) {
    console.error(`Failed to get car key dfx data. Code: ${err.code}, message: ${err.message}`);
}
```
