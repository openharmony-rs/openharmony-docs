# off

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## off('wifiStateChange')

```TypeScript
function off(type: 'wifiStateChange', callback?: Callback<number>): void
```

取消订阅WLAN状态改变事件。<p>如果没有指定callback参数，将取消注册该事件关联的所有回调函数。</p>

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wifiStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiStateChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。0:未激活，1:已激活，2:激活中，3:去激活中 |

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

取消订阅WLAN连接状态改变事件。<p>如果没有指定callback参数，将取消注册该事件关联的所有回调函数。</p>

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wifiConnectionChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiConnectionChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。0:已断开，1:已连接 |

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

取消订阅WLAN扫描状态改变事件。<p>如果没有指定callback参数，将取消注册该事件关联的所有回调函数。</p>

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wifiScanStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiScanStateChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。0:扫描失败，1:扫描成功 |

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

取消订阅WLAN RSSI改变事件。<p>如果没有指定callback参数，将取消注册该事件关联的所有回调函数。</p>

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wifiRssiChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wifiRssiChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数 |

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

取消订阅WLAN热点状态改变事件。<p>如果没有指定callback参数，将取消注册该事件关联的所有回调函数。</p>

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hotspotStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStateChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。0:未激活，1:已激活，2:激活中，3:去激活中 |


## off('p2pStateChange')

```TypeScript
function off(type: 'p2pStateChange', callback?: Callback<number>): void
```

取消订阅P2P状态改变事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pStateChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pStateChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。1:空闲，2:打开中，3:已打开，4:关闭中，5:已关闭 |

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

取消订阅P2P连接改变事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pConnectionChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pConnectionChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;WifiP2pLinkedInfo&gt; | 否 | 状态改变回调函数 |

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

取消订阅P2P本地设备改变事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pDeviceChange

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pDeviceChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;WifiP2pDevice&gt; | 否 | 状态改变回调函数 |

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

取消订阅P2P对端设备改变事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pPeerDeviceChange

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pPeerDeviceChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;WifiP2pDevice[]&gt; | 否 | 状态改变回调函数 |

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

取消订阅P2P持久群组改变事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pPersistentGroupChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pPersistentGroupChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 状态改变回调函数 |

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

取消订阅P2P发现事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** p2pDiscoveryChange

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pDiscoveryChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数 |

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
