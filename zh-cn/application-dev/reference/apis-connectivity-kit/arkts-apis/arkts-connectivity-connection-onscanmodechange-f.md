# onScanModeChange

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## onScanModeChange

```TypeScript
function onScanModeChange(callback: Callback<ScanMode>): void
```

订阅蓝牙扫描模式变更事件。使用Callback异步回调。当调用[setBluetoothScanMode](arkts-connectivity-connection-setbluetoothscanmode-f.md)更改当前蓝牙扫描模式后，如订阅此事件，则会收到携带最新扫描模式的回调函数。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScanMode](arkts-connectivity-connection-scanmode-e.md)&gt; | 是 | 指定订阅的回调函数，会携带变更后最新的蓝牙扫描模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
function ScanModeChangeEvent(scanMode: connection.ScanMode) {
    console.info(`Scan mode has changed, new mode: ${scanMode}`);
}
try {
    connection.onScanModeChange(ScanModeChangeEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
