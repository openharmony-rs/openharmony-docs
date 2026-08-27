# startBluetoothSearch

## 导入模块

```TypeScript
```

## startBluetoothSearch

```TypeScript
function startBluetoothSearch(
      request: BluetoothSearchRequestParams, callback: Callback<BluetoothScanResult>): void
```

启动蓝牙扫描并查找指定的蓝牙设备，仅当扫描到的蓝牙设备满足入参BluetoothSearchRequestParams指定的条件时，才通过callback异步返回该蓝牙设备信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [BluetoothSearchRequestParams](arkts-location-geolocationmanager-bluetoothsearchrequestparams-i.md) | 是 | 设置蓝牙扫描请求参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BluetoothScanResult](arkts-location-geolocationmanager-bluetoothscanresult-i.md)&gt; | 是 | 回调函数，用于返回蓝牙扫描结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.startBluetoothSearch} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301800](../errorcode-geoLocationManager.md#3301800-启动wi-fi或蓝牙扫描失败) | Failed to start Bluetooth scanning. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

private callback = (bluetoothScanResult: geoLocationManager.BluetoothScanResult) => {
  if (bluetoothScanResult) {
    console.info('bluetoothScanResult: deviceId=' + bluetoothScanResult.deviceId);
      try {
         // 开发者需要考虑在合适的时机调用stopBluetoothSearch停止蓝牙扫描以节省功耗，本代码仅作为参考
         geoLocationManager.stopBluetoothSearch(this.callback);
      } catch (err) {
         console.error("errCode:" + err.code + ", message:" + err.message);
      }
  }
};
let request: geoLocationManager.BluetoothSearchRequestParams = {
  'rssiThreshold': -100,
  'deviceIdArray': ['98:56:07:E6:AA:46','4E:E6:D2:02:27:F9']
};
 
try {
  geoLocationManager.startBluetoothSearch(request, this.callback);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
