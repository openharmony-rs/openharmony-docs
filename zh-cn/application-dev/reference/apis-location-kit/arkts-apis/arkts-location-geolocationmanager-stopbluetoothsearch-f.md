# stopBluetoothSearch

## 导入模块

```TypeScript
```

## stopBluetoothSearch

```TypeScript
function stopBluetoothSearch(callback?: Callback<BluetoothScanResult>): void
```

停止蓝牙扫描，该回调函数需要与startBluetoothSearch接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BluetoothScanResult](arkts-location-geolocationmanager-bluetoothscanresult-i.md)&gt; | 否 | 取消订阅的回调函数。该回调函数需要与on接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.stopBluetoothSearch} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
 
let request: geoLocationManager.BluetoothSearchRequestParams = {
  'rssiThreshold': -100,
  'deviceIdArray': ['98:56:07:E6:AA:46','4E:E6:D2:02:27:F9']
};
let callback = (bluetoothScanResult: geoLocationManager.BluetoothScanResult) => {
  if (bluetoothScanResult) {
    console.info('bluetoothScanResult: deviceId=' + bluetoothScanResult.deviceId);
  }
};
try {
  geoLocationManager.startBluetoothSearch(request, callback);
  geoLocationManager.stopBluetoothSearch(callback);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
