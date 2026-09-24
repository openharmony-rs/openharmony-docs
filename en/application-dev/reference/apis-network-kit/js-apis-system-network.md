# @system.network (Network State)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=108aa11c2ceb50c68f8417aa3c60f1dcb55dabdd translatedAt=2026-09-23T02:39:52.644Z pushedAt=2026-09-24T06:00:14.222Z -->

> **NOTE**
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Since API version 8, this API is no longer maintained. You are advised to use [@ohos.net.connection](js-apis-net-connection.md).

## Modules to Import


```js
import network from '@system.network';
```


## Required Permissions

ohos.permission.GET_WIFI_INFO

ohos.permission.GET_NETWORK_INFO


## network.getType<sup>3+</sup>

getType(options?: {<br>
&nbsp;&nbsp;success?: (data: NetworkResponse) => void;<br>
&nbsp;&nbsp;fail?: (data: any, code: number) => void;<br>
&nbsp;&nbsp;complete?: () => void;<br>
}): void

Obtains the network type of this device.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| success | Function | No| Called when the API call is successful. The return value is defined by [NetworkResponse](#networkresponse3).|
| fail | Function | No| Called when an API call fails.|
| complete | Function | No| Called when an API call is complete.|

Error codes:

| Error Code| Description|
| -------- | -------- |
| 602 | The current permission is not declared.|

**Example**

```js
export default class Network {
  getType() {
    network.getType({
      success: (data) => {
        console.info('success get network type:' + data.type);
      }
    });
  }
}
```


## network.subscribe<sup>3+</sup>

subscribe(options?: {<br>
&nbsp;&nbsp;success?: (data: NetworkResponse) => void;<br>
&nbsp;&nbsp;fail?: (data: any, code: number) => void;<br>
  }): void

Listens to the network connection state of this device. If this API is called multiple times, the last call takes effect.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| success | Function | No| Called when the network connection state changes The return value is defined by [NetworkResponse](#networkresponse3).|
| fail | Function | No| Called when an API call fails.|

Error codes:

| Error Code| Description|
| -------- | -------- |
| 602 | The current permission is not declared.|
| 200 | Subscription failed.|

**Example**

```js
export default class Network {
  subscribe() {
    network.subscribe({
      success: (data) => {
        console.info('success get network type:' + data.type);
      }
    });
  }
}
```


## network.unsubscribe<sup>3+</sup>

unsubscribe(): void

Cancels listening to the network connection state of this device.

**System capability**: SystemCapability.Communication.NetManager.Core

**Example**

```js
import network from '@system.network';

network.unsubscribe();
```


## NetworkResponse<sup>3+</sup>

**System capability**: SystemCapability.Communication.NetManager.Core

| Name  | Type                                          | Read-Only| Optional|Description                   |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
| metered | boolean | No | No | Whether the network is metered. **true**: metered; **false**: not metered. |
| type | string | No| No|Network type. The value can be **2G**, **3G**, **4G**, **5G**, **WiFi**, or **none**.|
