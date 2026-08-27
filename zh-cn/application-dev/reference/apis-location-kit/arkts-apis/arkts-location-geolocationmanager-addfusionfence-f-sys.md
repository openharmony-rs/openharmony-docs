# addFusionFence（系统接口）

## 导入模块

```TypeScript
```

## addFusionFence

```TypeScript
function addFusionFence(fenceRequestParams: FusionFenceRequestParams): Promise<void>
```

添加一个融合围栏，并订阅围栏事件。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.LOCATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fenceRequestParams | [FusionFenceRequestParams](arkts-location-geolocationmanager-fusionfencerequestparams-i-sys.md) | 是 | 融合围栏请求信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.addFusionFence} due to limited device. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3501603](../errorcode-geoLocationManager.md#3501603-由于存在重复的beacon围栏导致添加围栏失败) | Duplicate fusion fence identifier. |
| [3301601](../errorcode-geoLocationManager.md#3301601-地理围栏个数超过最大值限制导致添加围栏失败) | The number of geofences exceeds the maximum. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
// 创建围栏请求信息
let latitude = 30.07;
let longitude = 119.98;
// 多边形围栏位置信息
let point: geoLocationManager.Point = {
  latitude:latitude,
  longitude:longitude
}
// 圆形围栏信息，包括经纬度、半径、存活时间
let geofence: geoLocationManager.Geofence = {
  "latitude": latitude, "longitude": longitude, "radius": 2000, "expiration": 500000000
}
// 多边形围栏位置信息集合
let polygon: Array<geoLocationManager.Point> = [point];
// GNSS围栏请求信息
let gnssFence: geoLocationManager.GnssFence = {
  gnssFenceType: geoLocationManager.GnssFenceType.CIRCULAR, // GnssFenceType
  circularFence: geofence,
  polygon: polygon
}
// GNSS围栏请求信息集合
let gnssFences: Array<geoLocationManager.GnssFence> = [gnssFence];
// CELL围栏信息扩展字段，可选字段，可传空
let additionsMap: Map<string, string> = new Map<string, string>();
// CELL信息
let cellInfo: geoLocationManager.CellInfo = {
  timeSinceBoot:1781062881671, cellId:9999, lac:1024, mcc: 460, mnc: 1, rat: 13, signalIntensity: -75, arfcn: 1850, pci: 256, tac: 888,
  additionsMap: additionsMap
}
// CELL信息集合
let cellInfos: Array<geoLocationManager.CellInfo> = [cellInfo];
// CELL围栏请求信息
let cellFence: geoLocationManager.CellFence = {
  cellInfos: cellInfos,
};
// CELL围栏请求信息集合
let cellFences: Array<geoLocationManager.CellFence> = [cellFence];
// MAC地址
let mac: Array<string> = ["FA:C4:D0:0E:BF:DF"];
// Wi-Fi指纹信息
let wifiFeature: geoLocationManager.WirelessSignalFeature = {
  rssiAvg: 1,
  rssiStandardDeviation:2.0,
  mac:mac
};
// Wi-Fi指纹信息集合
let wifiFeatures: Array<geoLocationManager.WirelessSignalFeature> = [wifiFeature];
// Wi-Fi围栏请求信息
let wifiFence: geoLocationManager.WifiFence = {
  type: geoLocationManager.WifiFingerprintType.LOCATION,
  wifiFeatures:wifiFeatures
};
// Wi-Fi围栏请求信息集合
let wifiFences: Array<geoLocationManager.WifiFence> = [wifiFence];
// 构造围栏请求参数fenceRequestParams
let fenceRequestParams: geoLocationManager.FusionFenceRequestParams = {
  // 融合围栏唯一标识
  identifier: "123456789",
  // 融合围栏场景
  scene: geoLocationManager.FusionFenceScene.AIRPORT,
  // 融合围栏类型,可参考FusionFenceType
  fenceType: 1,
  // POI类型,参数为可选
  poiType: "1",
  // POI位置信息
  poiLocation: point,
  // 监听的围栏事件,可参考GeofenceTransitionEvent,每个bit位表示一种围栏事件，比如3，代表同时监听围栏进入和围栏退出两种事件。
  monitorTransitionEvents: 63,
  // 表示徘徊时间，单位为毫秒
  loiterTimeMs: 10000,
  // GNSS围栏信息集合,参数为可选。若fenceType选择GNSS，则必须填写
  gnssFences: gnssFences,
  // CELL围栏信息集合,参数为可选。若fenceType选择CELLULAR，则必须填写
  cellFences: cellFences,
  // Wi-Fi围栏信息集合,参数为可选。若fenceType选择WIFI，则必须填写
  wifiFences: wifiFences,
  // 表示围栏存活时间，单位是毫秒
  expirationMs: 100000000,
  // 用于接收围栏事件的回调函数
  fenceTransitionCallback: (transition : geoLocationManager.FusionFenceTransition) => {
    if (transition) {
      console.info("GeofenceTransition: ", JSON.stringify(transition));
    }
  },
}
try {
  // 添加围栏
  await geoLocationManager.addFusionFence(fenceRequestParams).then(() => {
    // 围栏添加成功
    console.info("addFusionFence success");
  }).catch((error : BusinessError) => {
    console.error("addFusionFence: BusinessError=" + JSON.stringify(error));
  });
} catch(error) {
  console.error("addFusionFence: error=" + JSON.stringify(error));
}
```
