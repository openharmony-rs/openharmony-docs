# NetConnection

网络连接对象类型。 > **说明：** > > （1）设备从无网络状态转变为有网络状态时，将触发netAvailable事件、netCapabilitiesChange事件和netConnectionPropertiesChange事件； > > （2）接收到netAvailable事件后，若设备从有网络状态转变为无网络状态，将触发netLost事件； > > （3）若未接收到netAvailable事件，则将直接接收到netUnavailable事件； > > （4）设备从WiFi网络切换至蜂窝网络时，将先触发netLost事件（WiFi丢失），随后触发netAvailable事件（蜂窝可用）。

**起始版本：** 23

<!--Device-connection-export interface NetConnection--><!--Device-connection-export interface NetConnection-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## onNetBlockStatusChange

```TypeScript
onNetBlockStatusChange(callback: Callback<NetBlockStatusInfo>): void
```

Registers a listener for netBlockStatusChange events.

**起始版本：** 23

<!--Device-NetConnection-onNetBlockStatusChange(callback: Callback<NetBlockStatusInfo>): void--><!--Device-NetConnection-onNetBlockStatusChange(callback: Callback<NetBlockStatusInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NetBlockStatusInfo](arkts-network-connection-netblockstatusinfo-i.md)&gt; | 是 | the callback used to return the result. |

## onNetLost

```TypeScript
onNetLost(callback: Callback<NetHandle>): void
```

Registers a listener for **netLost** events.

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NetConnection-onNetLost(callback: Callback<NetHandle>): void--><!--Device-NetConnection-onNetLost(callback: Callback<NetHandle>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;NetHandle&gt; | 是 | the callback used to return the result. |

**示例**

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建NetConnection对象。
let netCon: connection.NetConnection = connection.createNetConnection();

// 先使用on接口订阅网络丢失事件。
netCon.on('netLost', (data: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
});

// 使用unregister接口取消订阅网络丢失事件。
netCon.unregister((error: BusinessError) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
});
```

## onNetUnavailable

```TypeScript
onNetUnavailable(callback: Callback<void>): void
```

Registers a listener for netUnavailable events.

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NetConnection-onNetUnavailable(callback: Callback<void>): void--><!--Device-NetConnection-onNetUnavailable(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | the callback used to return the result. |

**示例**

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建NetConnection对象。
let netCon: connection.NetConnection = connection.createNetConnection();

// 先使用on接口订阅网络不可用事件。
netCon.on('netUnavailable', () => {
  console.info("Succeeded to get unavailable net event");
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  console.error(`Failed to get register.Code:${error.code}, message:${error.message}`);
});

// 使用unregister接口取消订阅网络不可用事件。
netCon.unregister((error: BusinessError) => {
  console.error(`Failed to get unregister.Code:${error.code}, message:${error.message}`);
});
```

## on('netAvailable')

```TypeScript
on(type: 'netAvailable', callback: Callback<NetHandle>): void
```

订阅网络可用事件。此接口需在调用register接口之前调用。若无需接收网络状态变化的回调通知，应使用unregister取消订阅默认的网络状态变化通知。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetConnection-on(type: 'netAvailable', callback: Callback<NetHandle>): void--><!--Device-NetConnection-on(type: 'netAvailable', callback: Callback<NetHandle>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netAvailable' | 是 | 订阅事件，固定为'netAvailable'。 <br>netAvailable：数据网络可用事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;NetHandle&gt; | 是 | 回调函数，返回数据网络句柄。 |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建NetConnection对象。
let netCon: connection.NetConnection = connection.createNetConnection();

// 先使用on接口订阅网络可用事件。
netCon.on('netAvailable', (data: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  console.error(`Failed to register.Code:${error.code}, message:${error.message}`);
});

// 使用unregister接口取消订阅网络可用事件。
netCon.unregister((error: BusinessError) => {
  console.error(`Failed to unregister.Code:${error.code}, message:${error.message}`);
});
```

## on('netBlockStatusChange')

```TypeScript
on(type: 'netBlockStatusChange', callback: Callback<NetBlockStatusInfo>): void
```

订阅网络阻塞状态事件。此接口需要在调用register接口之前调用。若无需接收网络状态变化的回调通知，应使用unregister取消订阅默认的网络状态变化通知。

**起始版本：** 8

<!--Device-NetConnection-on(type: 'netBlockStatusChange', callback: Callback<NetBlockStatusInfo>): void--><!--Device-NetConnection-on(type: 'netBlockStatusChange', callback: Callback<NetBlockStatusInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netBlockStatusChange' | 是 | 订阅事件，固定为'netBlockStatusChange'。<br/>netBlockStatusChange：网络阻塞状态事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NetBlockStatusInfo](arkts-network-connection-netblockstatusinfo-i.md)&gt; | 是 | 回调函数，获取网络阻塞状态信息。<br>**起始版本：** 11 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建NetConnection对象。
let netCon: connection.NetConnection = connection.createNetConnection();

// 先使用on接口订阅网络阻塞状态事件。
netCon.on('netBlockStatusChange', (data: connection.NetBlockStatusInfo) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
});

// 使用unregister接口取消订阅网络阻塞状态事件。
netCon.unregister((error: BusinessError) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
});
```

## on('netCapabilitiesChange')

```TypeScript
on(type: 'netCapabilitiesChange', callback: Callback<NetCapabilityInfo>): void
```

订阅网络能力变化事件。此接口要在register接口调用前调用，不需要网络状态变化回调通知时，使用unregister取消订阅默认网络状态变化的通知。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetConnection-on(type: 'netCapabilitiesChange', callback: Callback<NetCapabilityInfo>): void--><!--Device-NetConnection-on(type: 'netCapabilitiesChange', callback: Callback<NetCapabilityInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netCapabilitiesChange' | 是 | 订阅事件，固定为'netCapabilitiesChange'。<br/>netCapabilitiesChange：网络能力变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NetCapabilityInfo](arkts-network-connection-netcapabilityinfo-i.md)&gt; | 是 | 回调函数，返回数据网络句柄(netHandle)和网络的能力信息(netCap)。 |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建NetConnection对象。
let netCon: connection.NetConnection = connection.createNetConnection();

// 先使用on接口订阅网络能力变化事件。
netCon.on('netCapabilitiesChange', (data: connection.NetCapabilityInfo) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
});

// 使用unregister接口取消订阅网络能力变化事件。
netCon.unregister((error: BusinessError) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
});
```

## on('netConnectionPropertiesChange')

```TypeScript
on(type: 'netConnectionPropertiesChange', callback: Callback<NetConnectionPropertyInfo>): void
```

订阅网络连接信息变化事件。此接口要在register接口调用前调用，不需要网络状态变化回调通知时，使用unregister取消订阅默认网络状态变化的通知。

**起始版本：** 8

<!--Device-NetConnection-on(type: 'netConnectionPropertiesChange', callback: Callback<NetConnectionPropertyInfo>): void--><!--Device-NetConnection-on(type: 'netConnectionPropertiesChange', callback: Callback<NetConnectionPropertyInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netConnectionPropertiesChange' | 是 | 订阅事件，固定为'netConnectionPropertiesChange'。<br/> netConnectionPropertiesChange：网络连接信息变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NetConnectionPropertyInfo](arkts-network-connection-netconnectionpropertyinfo-i.md)&gt; | 是 | 回调函数，获取网络连接属性信息。<br>**起始版本：** 11 |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建NetConnection对象。
let netCon: connection.NetConnection = connection.createNetConnection();

// 先使用on接口订阅网络连接信息变化事件。
netCon.on('netConnectionPropertiesChange', (data: connection.NetConnectionPropertyInfo) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
});

// 使用unregister接口取消订阅网络连接信息变化事件。
netCon.unregister((error: BusinessError) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
});
```

## on('netLost')

```TypeScript
on(type: 'netLost', callback: Callback<NetHandle>): void
```

订阅网络丢失事件。此接口要在register接口调用前调用，不需要网络状态变化回调通知时，使用unregister取消订阅默认网络状态变化的通知。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetConnection-on(type: 'netLost', callback: Callback<NetHandle>): void--><!--Device-NetConnection-on(type: 'netLost', callback: Callback<NetHandle>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netLost' | 是 | 订阅事件，固定为'netLost'。<br/>netLost：网络严重中断或正常断开事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;NetHandle&gt; | 是 | 回调函数，数据网络句柄(netHandle)。 |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建NetConnection对象。
let netCon: connection.NetConnection = connection.createNetConnection();

// 先使用on接口订阅网络丢失事件。
netCon.on('netLost', (data: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  console.error(JSON.stringify(error));
});

// 使用unregister接口取消订阅网络丢失事件。
netCon.unregister((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## on('netUnavailable')

```TypeScript
on(type: 'netUnavailable', callback: Callback<void>): void
```

订阅网络不可用事件。此接口要在register接口调用前调用，不需要网络状态变化回调通知时，使用unregister取消订阅默认网络状态变化的通知。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetConnection-on(type: 'netUnavailable', callback: Callback<void>): void--><!--Device-NetConnection-on(type: 'netUnavailable', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netUnavailable' | 是 | 订阅事件，固定为'netUnavailable'。<br/>netUnavailable：网络不可用事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，无返回结果。 |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建NetConnection对象。
let netCon: connection.NetConnection = connection.createNetConnection();

// 先使用on接口订阅网络不可用事件。
netCon.on('netUnavailable', () => {
  console.info("Succeeded to get unavailable net event");
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  console.error(`Failed to get register.Code:${error.code}, message:${error.message}`);
});

// 使用unregister接口取消订阅网络不可用事件。
netCon.unregister((error: BusinessError) => {
  console.error(`Failed to get unregister.Code:${error.code}, message:${error.message}`);
});
```

## register

```TypeScript
register(callback: AsyncCallback<void>): void
```

订阅指定网络状态变化的通知。如需监听特定事件，确保调用on监听事件后再调用register进行注册。 > **注意：** > > 使用完register接口后需要及时调用unregister取消注册。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetConnection-register(callback: AsyncCallback<void>): void--><!--Device-NetConnection-register(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当订阅指定网络状态变化的通知成功，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2101008](../errorcode-net-connection.md#2101008-已存在相同的callback) | The callback already exists. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2101022](../errorcode-net-connection.md#2101022-请求数量超过最大值) | The number of requests exceeded the maximum allowed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netCon: connection.NetConnection = connection.createNetConnection();
netCon.register((error: BusinessError) => {
  console.error(`Failed to register.Code:${error.code}, message:${error.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netCon: connection.NetConnection = connection.createNetConnection();
netCon.register((error: BusinessError | null) => {
  console.error(`Failed to register.Code:${error.code}, message:${error.message}`);
});
```

## unregister

```TypeScript
unregister(callback: AsyncCallback<void>): void
```

取消订阅默认网络状态变化的通知。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetConnection-unregister(callback: AsyncCallback<void>): void--><!--Device-NetConnection-unregister(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当取消订阅指定网络状态变化的通知成功，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 8 - 11 |
| [2101007](../errorcode-net-connection.md#2101007-callback不存在) | The callback does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netCon: connection.NetConnection = connection.createNetConnection();
netCon.unregister((error: BusinessError) => {
  console.error(`Failed to unregister.Code:${error.code}, message:${error.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netCon: connection.NetConnection = connection.createNetConnection();
netCon.unregister((error: BusinessError|null) => {
  console.error(`Failed to unregister.Code:${error.code}, message:${error.message}`);
});
```

