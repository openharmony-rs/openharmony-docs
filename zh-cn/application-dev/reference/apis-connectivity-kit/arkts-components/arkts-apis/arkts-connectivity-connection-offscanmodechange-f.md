# offScanModeChange

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## offScanModeChange

```TypeScript
function offScanModeChange(callback?: Callback<ScanMode>): void
```

取消订阅蓝牙扫描模式变更事件。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScanMode](arkts-connectivity-connection-scanmode-e.md)&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[connection.onScanModeChange](arkts-connectivity-connection-onscanmodechange-f.md)中的回调函数一致；若无传参，则取消订阅所有蓝牙扫描模式变更的回调函数通知。 |

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
    connection.offScanModeChange(ScanModeChangeEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
