# off（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## off('streamChange')

```TypeScript
function off(type: 'streamChange', callback?: Callback<number>): void
```

取消注册Wi-Fi流变更事件。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_WIFI_CONNECTION

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'streamChange' | 是 | 固定填"streamChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数，返回0:无，1:向下，2:向上，3:双向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

let recvStreamChangeFunc = (result:number) => {
    console.info("Receive stream change event: " + result);
}

// Register event
wifiManager.on("streamChange", recvStreamChangeFunc);

// Unregister event
wifiManager.off("streamChange", recvStreamChangeFunc);
```


## off('deviceConfigChange')

```TypeScript
function off(type: 'deviceConfigChange', callback?: Callback<number>): void
```

取消注册Wi-Fi设备配置更改事件。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceConfigChange' | 是 | 固定填"deviceConfigChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数，返回值为 0: 添加配置。1: 更改配置。2: 删除配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

let recvDeviceConfigChangeFunc = (result:number) => {
    console.info("Receive device config change event: " + result);
}

// Register event
wifiManager.on("deviceConfigChange", recvDeviceConfigChangeFunc);

// Unregister event
wifiManager.off("deviceConfigChange", recvDeviceConfigChangeFunc);
```


## off('hotspotStaJoin')

```TypeScript
function off(type: 'hotspotStaJoin', callback?: Callback<StationInfo>): void
```

取消注册Wi-Fi热点的STA加入事件。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStaJoin' | 是 | 固定填"hotspotStaJoin"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md)&gt; | 否 | 状态改变回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

let recvHotspotStaJoinFunc = (result:wifiManager.StationInfo) => {
    console.info("Receive hotspot sta join event: " + result);
}

// Register event
wifiManager.on("hotspotStaJoin", recvHotspotStaJoinFunc);

// Unregister event
wifiManager.off("hotspotStaJoin", recvHotspotStaJoinFunc);
```


## off('hotspotStaLeave')

```TypeScript
function off(type: 'hotspotStaLeave', callback?: Callback<StationInfo>): void
```

取消注册Wi-Fi热点STA离开事件。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStaLeave' | 是 | 固定填"hotspotStaLeave"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md)&gt; | 否 | 状态改变回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

let recvHotspotStaLeaveFunc = (result:wifiManager.StationInfo) => {
    console.info("Receive hotspot sta leave event: " + result);
}

// Register event
wifiManager.on("hotspotStaLeave", recvHotspotStaLeaveFunc);

// Unregister event
wifiManager.off("hotspotStaLeave", recvHotspotStaLeaveFunc);
```
