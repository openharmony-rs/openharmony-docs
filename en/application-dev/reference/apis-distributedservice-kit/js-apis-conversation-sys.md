# @ohos.distributedSoftbus.conversation (Cross-Device Wakeup and Message Transfer) (System API)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wangrui7-->
<!--Designer: @yangyang2-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->

Based on the DSoftBus, the **conversation** module provides APIs for cross-device interaction of apps, including obtaining the trusted device list, and sending and receiving session data. With this module, your app can obtain trusted devices under the same account, register a listener to receive cross-device data, and send data to a specified device through a session channel. This module is applicable to scenarios that require cross-device collaboration and multi-device data transfer, simplifying the development of cross-device interaction.

**Since:** 26.1.0

> **NOTE**
>
> The APIs provided by this module are system APIs and can be used only in the stage model.

## Modules to Import

```js
import { conversation } from '@kit.DistributedServiceKit';
```

## conversation.getTrustedDevices

getTrustedDevices(): DeviceNodeInfo[]

Obtains information about all trusted devices under the same account. Typical use scenarios include querying available target devices before sending data across devices.

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| [DeviceNodeInfo[]](#devicenodeinfo) | Device node information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Cross-Device Wakeup and Message Transfer Error Codes](errorcode-conversation.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|

**Example**

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'conversationDemo';

try {
  let devices: conversation.DeviceNodeInfo[] = conversation.getTrustedDevices();
  hilog.info(0x0000, TAG, 'trusted devices count = ' + devices.length);
  for (let device of devices) {
    hilog.info(0x0000, TAG, 'device name = ' + device.deviceName + ', networkId = ' + device.networkId);
  }
} catch (err) {
  hilog.error(0x0000, TAG, 'getTrustedDevices errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## conversation.postConversationData

postConversationData(deviceId:&nbsp;string,&nbsp;bundleName:&nbsp;string,&nbsp;abilityName:&nbsp;string,&nbsp;msg:&nbsp;ArrayBuffer):&nbsp;Promise&lt;void&gt;

Sends session data to the target device. The target device must be a trusted device under the same account. Data is sent through the DSoftBus session channel. The network ID or UDID of the target device is used for device addressing. After data is routed to the remote device, it will be sent to the app with the registered listener based on the specified bundle name and ability name. Typical use scenarios include sending collaboration commands across devices.

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| deviceId  | string  | Yes   | Network ID or UDID of the target device, which can be obtained by calling [getTrustedDevices()](#conversationgettrusteddevices). If an invalid value is passed, error code 401 is returned. |
| bundleName | string  | Yes   | Name of the target bundle to which data is sent. The value must be the same as the name of the bundle registered with a listener on the remote device by calling [registerConversationListener](#conversationregisterconversationlistener). If this requirement is not met, data cannot be sent to the target app. If an invalid or empty value is passed, error code 401 is returned. |
| abilityName | string  | Yes   | Name of the target ability to which data is sent. The value must be the same as the name of the ability registered with the listener on the remote device. If this requirement is not met, data cannot be sent to the target app. If an invalid or empty value is passed, error code 401 is returned. |
| msg | ArrayBuffer  | Yes   | Message to be sent, which is binary data in **ArrayBuffer** format and cannot be empty. The data structure is defined by the application layer protocol. If empty or invalid data is passed, error code 401 is returned. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise used to return the result. The value **resolve** indicates that the session data is sent successfully; **reject** indicates that the session data fails to be sent and an error message is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Cross-Device Wakeup and Message Transfer Error Codes](errorcode-conversation.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 401      | Invalid parameter. The deviceId, bundleName, abilityName or msg is invalid or empty.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|
| 2004001  | Remote not supported.|
| 2004002  | Duplicate calls, previous call still in progress.|
| 2004003  | Send data failed.|
| 2004004  | Wait remote ack timeout.|

**Example**

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'conversationDemo';

try {
  let deviceId: string = "device_network_id_or_udid"; // deviceId is the network ID or UDID of the target device obtained by calling conversation.getTrustedDevices().
  let bundleName: string = "com.example.demo";
  let abilityName: string = "EntryAbility";
  let msg: ArrayBuffer = new ArrayBuffer(10);
  let view = new Uint8Array(msg);
  view[0] = 1;

  conversation.postConversationData(deviceId, bundleName, abilityName, msg).then(() => {
    hilog.info(0x0000, TAG, 'postConversationData success');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, TAG, 'postConversationData errCode: ' + err.code + ', errMessage: ' + err.message);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'postConversationData errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## conversation.registerConversationListener

registerConversationListener(bundleName:&nbsp;string,&nbsp;abilityName:&nbsp;string,&nbsp;dataCallback:&nbsp;DataCallback):&nbsp;void

Registers a listener to receive data from trusted devices under the same account. When the remote device sends data to the local device through the DSoftBus session channel, the DSoftBus distributes the data to the registered callback based on the specified bundle name and ability name. Only one listener can be registered for the same bundle name and ability name. Duplicate registration will overwrite the previously registered listener.

**API called in pairs:** This API must be used in pairs with [unregisterConversationListener](#conversationunregisterconversationlistener), which is called to unregister the listener to release resources.

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| bundleName  | string  | Yes   | Name of the bundle that receives data. The value must be the same as the bundle name of the app. If this requirement is not met, the listener may fail to receive data correctly. If an invalid or empty value is passed, error code 401 is returned. |
| abilityName | string  | Yes   | Name of the ability that receives data. The value must be the same as the ability name of the app. If this requirement is not met, the listener may fail to receive data correctly. If an invalid or empty value is passed, error code 401 is returned. |
| dataCallback | [DataCallback](#datacallback)  | Yes   | Callback function used to receive data transferred across devices. If an invalid value is passed, error code 401 is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Cross-Device Wakeup and Message Transfer Error Codes](errorcode-conversation.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 401      | Invalid parameter. The bundleName, abilityName or dataCallback is invalid or empty.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|

**Example**

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'conversationDemo';

try {
  let bundleName: string = "com.example.demo";
  let abilityName: string = "EntryAbility";

  conversation.registerConversationListener(bundleName, abilityName, (deviceId: string, msg: ArrayBuffer) => {
    hilog.info(0x0000, TAG, 'received message from deviceId = ' + deviceId + ', msg length = ' + msg.byteLength);
  });
  hilog.info(0x0000, TAG, 'registerConversationListener success');
} catch (err) {
  hilog.error(0x0000, TAG, 'registerConversationListener errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## conversation.unregisterConversationListener

unregisterConversationListener(bundleName:&nbsp;string,&nbsp;abilityName:&nbsp;string):&nbsp;void

Unregisters the listener with the specified bundle name and ability name. This API must be used in pairs with [registerConversationListener](#conversationregisterconversationlistener) to unregister a registered listener. Only one listener can be registered for the same bundle name and ability name. Duplicate registration will overwrite the previously registered listener. After the listener is unregistered, the listener that is currently in effect will be removed. After this API is called, the app will no longer receive session data of the specified bundle name and ability name. If no listener has been registered for the specified bundle name and ability name, this API returns a success message.

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| bundleName  | string  | Yes   | Name of the bundle whose listener is to be canceled. The value must be the same as the bundle name used for registering the listener. If an invalid or empty value is passed, error code 401 is returned. |
| abilityName | string  | Yes   | Name of the ability whose listener is to be canceled. The value must be the same as the ability name used for registering the listener. If an invalid or empty value is passed, error code 401 is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Cross-Device Wakeup and Message Transfer Error Codes](errorcode-conversation.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 401      | Invalid parameter. The bundleName or abilityName is invalid or empty.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|

**Example**

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'conversationDemo';

try {
  let bundleName: string = "com.example.demo";
  let abilityName: string = "EntryAbility";

  conversation.unregisterConversationListener(bundleName, abilityName);
  hilog.info(0x0000, TAG, 'unregisterConversationListener success');
} catch (err) {
  hilog.error(0x0000, TAG, 'unregisterConversationListener errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## DeviceNodeInfo

Defines the device node information, including the network ID, device name, device type ID, near-field status, and UDID.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name                   | Type      |Read-Only  | Optional  | Description                |
| ----------------- | ------ | ----  | ---- | ------------------ |
| networkId          | string | No   |No   | Network ID of the device, which uniquely identifies a device on a distributed network and is used for device addressing during data sending. It is an alternative ID to UDID. Either of them can be used for data sending.    |
| deviceName           | string | No   |No  | Device name.|
| deviceTypeId            | number | No   |No   | Device type ID, which indicates the device type. The value is an integer, for example, the type ID of the mobile phone, tablet, TV, or wearable.|
| nearby            | boolean | No   |No   | Whether the device is in the near field. The value **true** indicates that the device is in the near field, and the value **false** indicates that the device is not in the near field.|
| udid            | string | No   |No   | UDID of the device, which uniquely identifies a device and is used for device addressing during data sending. Different from the network ID, the UDID is a permanent and unique ID of a device and does not change with the network topology. They are alternative IDs and either of them can be used for data sending.|

## DataCallback

Defines a callback for receiving data.

**(deviceId: string, msg: ArrayBuffer): void**

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| deviceId  | string  | Yes   | Network ID or UDID of the source device that sends data. |
| msg | ArrayBuffer  | Yes   | Message received, which is binary data in **ArrayBuffer** format. The data format is the same as that of the data sent and is defined by the application layer protocol. |
