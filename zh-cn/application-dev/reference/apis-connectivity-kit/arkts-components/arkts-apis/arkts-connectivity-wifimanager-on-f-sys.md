# on（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## on('streamChange')

```TypeScript
function on(type: 'streamChange', callback: Callback<number>): void
```

注册Wi-Fi流变更事件，在业务退出时，要调用off(type: 'streamChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_WIFI_CONNECTION

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'streamChange' | 是 | 固定填"streamChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 状态改变回调函数，返回0:无，1:向下，2:向上，3:双向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |


## on('deviceConfigChange')

```TypeScript
function on(type: 'deviceConfigChange', callback: Callback<number>): void
```

注册Wi-Fi设备配置更改事件，在业务退出时，要调用off(type: 'deviceConfigChange', callback?: Callback&lt;number&gt;)接口去掉之前的注册回调。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceConfigChange' | 是 | 固定填"deviceConfigChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 状态改变回调函数，返回值为 0: 添加配置。1: 更改配置。2: 删除配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |


## on('hotspotStaJoin')

```TypeScript
function on(type: 'hotspotStaJoin', callback: Callback<StationInfo>): void
```

注册Wi-Fi热点STA加入事件，在业务退出时，要调用off(type: 'hotspotStaJoin', callback?: Callback&lt;StationInfo&gt;)接口去掉之前的注册回调。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStaJoin' | 是 | 固定填"hotspotStaJoin"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md)&gt; | 是 | 状态改变回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |


## on('hotspotStaLeave')

```TypeScript
function on(type: 'hotspotStaLeave', callback: Callback<StationInfo>): void
```

注册Wi-Fi热点STA离开事件，在业务退出时，要调用off(type: 'hotspotStaLeave', callback?: Callback&lt;StationInfo&gt;)接口去掉之前的注册回调。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStaLeave' | 是 | 固定填"hotspotStaLeave"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md)&gt; | 是 | 状态改变回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |
