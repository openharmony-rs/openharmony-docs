# off

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## off('wifiStateChange')

```TypeScript
function off(type: 'wifiStateChange', callback?: Callback<number>): void
```

取消注册Wi-Fi状态改变事件。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wifiStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiStateChange' | 是 | 固定填"wifiStateChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvPowerNotifyFunc = (result:number) => {
    console.info("Receive power state change event: " + result);
}

// Register event
wifi.on("wifiStateChange", recvPowerNotifyFunc);

// Unregister event
wifi.off("wifiStateChange", recvPowerNotifyFunc);
```


## off('wifiConnectionChange')

```TypeScript
function off(type: 'wifiConnectionChange', callback?: Callback<number>): void
```

取消注册Wi-Fi连接状态改变事件。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wifiConnectionChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiConnectionChange' | 是 | 固定填"wifiConnectionChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 连接状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvWifiConnectionChangeFunc = (result:number) => {
    console.info("Receive wifi connection change event: " + result);
}

// Register event
wifi.on("wifiConnectionChange", recvWifiConnectionChangeFunc);

// Unregister event
wifi.off("wifiConnectionChange", recvWifiConnectionChangeFunc);
```


## off('wifiScanStateChange')

```TypeScript
function off(type: 'wifiScanStateChange', callback?: Callback<number>): void
```

取消注册扫描状态改变事件。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wifiScanStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiScanStateChange' | 是 | 固定填"wifiScanStateChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvWifiScanStateChangeFunc = (result:number) => {
    console.info("Receive Wifi scan state change event: " + result);
}

// Register event
wifi.on("wifiScanStateChange", recvWifiScanStateChangeFunc);

// Unregister event
wifi.off("wifiScanStateChange", recvWifiScanStateChangeFunc);
```


## off('wifiRssiChange')

```TypeScript
function off(type: 'wifiRssiChange', callback?: Callback<number>): void
```

取消注册RSSI状态改变事件。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wifiRssiChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiRssiChange' | 是 | 固定填"wifiRssiChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvWifiRssiChangeFunc = (result:number) => {
    console.info("Receive wifi rssi change event: " + result);
}

// Register event
wifi.on("wifiRssiChange", recvWifiRssiChangeFunc);

// Unregister event
wifi.off("wifiRssiChange", recvWifiRssiChangeFunc);
```


## off('hotspotStateChange')

```TypeScript
function off(type: 'hotspotStateChange', callback?: Callback<number>): void
```

取消注册热点状态改变事件。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hotspotStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStateChange' | 是 | 固定填"hotspotStateChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |


## off('p2pStateChange')

```TypeScript
function off(type: 'p2pStateChange', callback?: Callback<number>): void
```

取消注册P2P开关状态改变事件。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pStateChange' | 是 | 固定填"p2pStateChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pStateChangeFunc = (result:number) => {
    console.info("Receive p2p state change event: " + result);
}

// Register event
wifi.on("p2pStateChange", recvP2pStateChangeFunc);

// Unregister event
wifi.off("p2pStateChange", recvP2pStateChangeFunc);
```


## off('p2pConnectionChange')

```TypeScript
function off(type: 'p2pConnectionChange', callback?: Callback<WifiP2pLinkedInfo>): void
```

取消注册P2P连接状态改变事件。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pConnectionChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pConnectionChange' | 是 | 固定填"p2pConnectionChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WifiP2pLinkedInfo](arkts-connectivity-wifi-wifip2plinkedinfo-i.md)&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pConnectionChangeFunc = (result:wifi.WifiP2pLinkedInfo) => {
    console.info("Receive p2p connection change event: " + result);
}

// Register event
wifi.on("p2pConnectionChange", recvP2pConnectionChangeFunc);

// Unregister event
wifi.off("p2pConnectionChange", recvP2pConnectionChangeFunc);
```


## off('p2pDeviceChange')

```TypeScript
function off(type: 'p2pDeviceChange', callback?: Callback<WifiP2pDevice>): void
```

取消注册P2P设备状态改变事件。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pDeviceChange

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pDeviceChange' | 是 | 固定填"p2pDeviceChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md)&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pDeviceChangeFunc = (result:wifi.WifiP2pDevice) => {
    console.info("Receive p2p device change event: " + result);
}

// Register event
wifi.on("p2pDeviceChange", recvP2pDeviceChangeFunc);

// Unregister event
wifi.off("p2pDeviceChange", recvP2pDeviceChangeFunc);
```


## off('p2pPeerDeviceChange')

```TypeScript
function off(type: 'p2pPeerDeviceChange', callback?: Callback<WifiP2pDevice[]>): void
```

取消注册P2P对端设备状态改变事件。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pPeerDeviceChange

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pPeerDeviceChange' | 是 | 固定填"p2pPeerDeviceChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md)[]&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pPeerDeviceChangeFunc = (result:wifi.WifiP2pDevice[]) => {
    console.info("Receive p2p peer device change event: " + result);
}

// Register event
wifi.on("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);

// Unregister event
wifi.off("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);
```


## off('p2pPersistentGroupChange')

```TypeScript
function off(type: 'p2pPersistentGroupChange', callback?: Callback<void>): void
```

取消注册P2P永久组状态改变事件。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pPersistentGroupChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pPersistentGroupChange' | 是 | 固定填"p2pPersistentGroupChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pPersistentGroupChangeFunc = (result:void) => {
    console.info("Receive p2p persistent group change event: " + result);
}

// Register event
wifi.on("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);

// Unregister event
wifi.off("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);
```


## off('p2pDiscoveryChange')

```TypeScript
function off(type: 'p2pDiscoveryChange', callback?: Callback<number>): void
```

取消注册发现设备状态改变事件。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pDiscoveryChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pDiscoveryChange' | 是 | 固定填"p2pDiscoveryChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。如果callback不填，将取消注册该事件关联的所有回调函数。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

let recvP2pDiscoveryChangeFunc = (result:number) => {
    console.info("Receive p2p discovery change event: " + result);
}

// Register event
wifi.on("p2pDiscoveryChange", recvP2pDiscoveryChangeFunc);

// Unregister event
wifi.off("p2pDiscoveryChange", recvP2pDiscoveryChangeFunc);
```
