# @ohos.distributedDeviceManager (Device Management) (System API)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedHardware-->
<!--Owner: @hwzhangchuang-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=90c70cf06c9952154d1cb4fd34561983f513eab3 translatedAt=2026-11-04T05:27:12.818Z pushedAt=2026-11-04T10:12:33.564Z nl=1 -->

The **deviceManager** module provides APIs for distributed device management.

Applications can call the APIs to:

- Subscribe to or unsubscribe from device state changes.
- Discover devices nearby.
- Authenticate or deauthenticate a device.
- Query the trusted device list.
- Queries local device information, including the device name, type, and ID.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version. This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.distributedDeviceManager](js-apis-distributedDeviceManager.md).

## Modules to Import

```ts
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## StrategyForHeartbeat<sup>15+</sup>

Defines the heartbeat broadcast policy.

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

| Name         | Value  | Description              |
| ----------- | ---- | --------------- |
| TEMP_STOP_HEARTBEAT      | 100    | Temporarily stops the heartbeat broadcast and automatically resumes it after a timeout.             |
| START_HEARTBEAT          | 101    | Starts the heartbeat broadcast.                               |

## DeviceProfileInfoFilterOptions<sup>15+</sup>

Defines device profile information filter options.

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

| Name         | Type  | Read-Only | Optional             |  Description    |
| ----------- | ---- | -- | --- |--------------- | 
| isCloud      | boolean    |  No | No           | Whether to obtain the device list from the cloud in real time.<br />- false: obtains the list from the device.<br />- true: obtains the list from the cloud.       |
| deviceIdList  | Array&lt;string&gt;  | No | Yes    | Device information of the specified deviceId. The deviceId is generally the UDID of the device. If the device has no UDID, its MAC or SN is used as the deviceId. Default value is empty.       |


## ServiceProfileInfo<sup>15+</sup>

Defines the service profile information. It is populated based on the data returned from the cloud.

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

| Name           | Type  | Read-Only| Optional              |  Description    |
| -------------- | ---- | --------| ------- | --------|
| deviceId       | string  | No | No   |  ID of the peripheral device.          |
| serviceId       | string  | No |No   | Service ID.           |
| serviceType     | string   | No | No   | Service type.           |
| data       | string  | No | Yes   |  Service data. The character length cannot exceed 1000 characters. Default value is empty.          |

## DeviceProfileInfo<sup>15+</sup>

Defines device information.

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

| Name           | Type  | Read-Only   |Optional              |  Description    |
| -------------- | ---- | ---| --------------- | --------|
|  deviceId      | string  |  No    | No   |  ID of the peripheral device.          |
|  deviceSn      | string  |  No    | No   |  Device serial number.      |
|  mac           | string  |  No    | No   |  MAC address.         |
|  model         | string  |  No    | No   |  Device model.         |
|  deviceType    | string  |  No    | No   |  Device type.         |
|  manufacturer  | string  |  No    | No   |  Manufacturer.           |
|  deviceName    | string  |  No    | No   |  Device name.         |
|  productId     | string  |  No    | No   |  Product ID of the device.    |
|  subProductId  | string  |  No    | Yes   |  Sub-product ID of the device. Default value is empty.         |
|  sdkVersion    | string  |  No    | No   |  SDK version.          |
|  bleMac        | string  |  No    | No   |  MAC address of Bluetooth BLE.  |
|  brMac         | string  |  No    | No   |  MAC address of Bluetooth BR.  |
|  sleMac        | string  |  No    | No   |  MAC address of Starflash. |
|  firmwareVersion | string |  No   | No  |  Firmware version.          |
|  hardwareVersion | string |  No   | No  |  Hardware version.          |
|  softwareVersion | string |  No  | No  |  Software version.          |
|  protocolType    | number |  No   | No  |  Protocol type.          |
|  setupType       | number |  No   | No  |  Device type.          |
|  wiseDeviceId    | string |  No   | No  |  Registered device identifier.        |
|  wiseUserId      | string |  No   | No  |  Registered user identifier.        |
|  registerTime    | string |  No   | No  |  Registration time.          |
|  modifyTime      | string |  No   | No  |  Modification time.          |
|  shareTime       | string |  No   | No  |  Sharing time.          |
|  isLocalDevice   | boolean | No   | No |  Whether the device is a local device.<br />- false: indicates a non-local device, that is, another queried device.<br />- true: indicates a local device, that is, the device currently using this API.     |
|  services        | Array&lt;[ServiceProfileInfo](#serviceprofileinfo15)&gt; | No  | Yes  | List of service profile information. Default value is empty. |
|  productName<sup>18+</sup>     | string  | No   | Yes |  Product name of the device. Default value is empty.    |
|  internalModel<sup>18+</sup>   | string  | No   | Yes |  Internal model of the product to which the device belongs. Default value is empty. |


## DeviceIconInfoFilterOptions<sup>18+</sup>

Defines the device icon information filter options.

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

| Name           | Type  | Read-Only | Optional              |  Description    |
| -------------- | ---- | -------| -------- | --------|
|  productId      | string  | No | No   |  Product ID of the device.          |
|  subProductId   | string  | No | Yes   |  Sub-product ID of the device. Default value is empty.      |
|  imageType      | string  | No | No   |  Image type. The fixed value is "ID", indicating the physical image of the product. |
|  specName       | string  | No | No   |  Image specification name. Value range:<br />- lg: large image, with a size of 1016064px.<br />- sm: small image, with a size of 65536px.         |
|  internalModel  | string  | No | Yes   |  Internal model of the product to which the device belongs. Default value is empty.        |

## DeviceIconInfo<sup>18+</sup>

Defines the device icon information.

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

| Name           | Type  | Read-Only  |Optional              |  Description    |
| -------------- | ---- | ------| --------- | --------|
|  productId      | string  | No | No   |  Product ID of the device.          |
|  subProductId   | string  | No | Yes   |  Sub-product ID of the device. Default value is empty.     |
|  imageType      | string  | No | No   |  Image type. The fixed value is "ID", indicating the physical image of the product.        |
|  specName       | string  | No | No   |  Image specification name. Value range:<br />- lg: large image, with a size of 1016064 px.<br />- sm: small image, with a size of 65536 px.         |
|  url            | string  | No | No   |  URL.          |
|  icon           | ArrayBuffer | No| No | Icon.         |
|  internalModel  | string  | No | Yes   |  Internal model of the product to which the device belongs. Default value is empty.         |

## NetworkIdQueryFilter<sup>18+</sup>

Defines the network ID filter options.

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

| Name           | Type  | Read-Only | Optional              |  Description    |
| -------------- | ---- | ------ | --------- | --------|
|  wiseDeviceId       | string  | No | No   |  Registered device identifier.          |
|  onlineStatus    | number  | No | No   |  Device online status, including<br />- 0: the device is offline.<br />- 1: the device is online.      |

## DeviceIdentification<sup>24+</sup>

Defines a struct to identify a distributed device.

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

| Name     | Type  | Read-Only | Optional | Description |
|----------| ---- | --------- | -------- |-------------|
| deviceId | string  | No | No   | Anonymous device ID obtained by the application. |
| udid     | string  | No | No   | Unique device identifier. **Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC, ohos.permission.ACCESS_SERVICE_DM, and ohos.permission.sec.ACCESS_UDID.     |

## DeviceManager

Provides APIs to obtain information about trusted devices and local devices. Before calling any API in **DeviceManager**, you must use **createDeviceManager** to create a **DeviceManager** instance, for example, **dmInstance**.

### replyUiAction

replyUiAction(action: number, actionResult: string): void

Replies to the user's UI operation. This API can be used only by the PIN HAP of the **deviceManager**.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name | Type | Mandatory | Description |
  | ------------- | --------------- | ---- | ------------------- |
  | action | number | Yes | User operation.<br>- **0**: Grant the permission.<br>- **1**: Remove the permission.<br>- **2**: Time out the user operation in the permission request dialog.<br>- **3**: Cancel the display of the PIN box.<br>- **4**: Cancel the display of the PIN input box.<br>- **5**: Confirm the input in the PIN input box. |
  | actionResult | string | Yes | User operation result. The value ranges from 1 to 255 characters. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified actionResult is greater than 255. |

**Example**

<!--code_no_check-->
  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    /**
     * action = 0 - Grant the permission.
     * action = 1 - Remove the permission.
     * action = 2 - Time out the user operation in the permission request dialog.
     * action = 3 - Cancel the display of the PIN box.
     * action = 4 - Cancel the display of the PIN input box.
     * action = 5 - Confirm the input in the PIN input box.
     */
    let operation = 0;
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    dmInstance.replyUiAction(operation, 'extra');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('replyUiAction errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### on('replyResult')

on(type: 'replyResult', callback: Callback&lt;{ param: string;}&gt;): void

Subscribes to the reply to the UI operation result. This API returns the result asynchronously through a callback.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name      | Type                             | Mandatory | Description                            |
  | -------- | ------------------------------------ | ---- | ------------------------------ |
  | type     | string                                | Yes  | Device manager UI status callback to be registered, which notifies the application when the status changes. The value is fixed at replyResult. |
  | callback | Callback&lt;{&nbsp;param:&nbsp;string;}&gt; | Yes  | Callback used to return the UI status.        |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.    |
| 202 | Permission verification failed. A non-system application calls a system API.                            |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**Example**

<!--code_no_check-->
  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  class Data {
    param: string = '';
  }

  interface TmpStr {
    verifyFailed: boolean;
  }

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    dmInstance.on('replyResult', (data: Data) => {
      console.info('replyResult executed, dialog closed' + JSON.stringify(data));
      let tmpStr: TmpStr = JSON.parse(data.param);
      let isShow = tmpStr.verifyFailed;
      console.info('replyResult executed, dialog closed' + isShow);
    });
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('replyResult errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### off('replyResult')

off(type: 'replyResult', callback?: Callback&lt;{ param: string;}&gt;): void

Unsubscribes from the reply to the UI operation result. This API returns the result asynchronously through a callback.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name      | Type                              | Mandatory | Description                            |
  | -------- | ------------------------------------- | ---- | ------------------------------ |
  | type     | string                                | Yes   | Device manager UI status callback to unregister. The value is fixed to **replyResult**. |
  | callback | Callback&lt;{&nbsp;param:&nbsp;string;}&gt; | No   | Callback for the device manager UI status event. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.    |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**Example**

<!--code_no_check-->
  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    dmInstance.off('replyResult');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('replyResult errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### setHeartbeatPolicy<sup>15+</sup>

setHeartbeatPolicy(policy: StrategyForHeartbeat, delayTime: number): void

Sets the heartbeat broadcast policy.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name       | Type            | Mandatory  | Description                |
  | ------------- | --------------- | ---- | ------------------- |
  | policy        |  &nbsp;[StrategyForHeartbeat](#strategyforheartbeat15)&nbsp;         | Yes    | Heartbeat broadcast strategy.       |
  | delayTime     | number          | Yes    | Duration for temporarily disabling the heartbeat broadcast, in ms. The value range is 1000 ms to 15000 ms.            |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 11600102 | Failed to obtain service.                                 |

**Example**

<!--code_no_check-->
  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let policy = distributedDeviceManager.StrategyForHeartbeat.TEMP_STOP_HEARTBEAT;
    let delayTime = 1000;
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    dmInstance.setHeartbeatPolicy(policy, delayTime);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('setHeartbeatPolicy errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### getDeviceProfileInfoList<sup>15+</sup>

getDeviceProfileInfoList(filterOptions: DeviceProfileInfoFilterOptions): Promise&lt;Array&lt;DeviceProfileInfo&gt;&gt;

Obtains the list of devices under the same account. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name       | Type            | Mandatory  | Description                |
  | ------------- | --------------- | ---- | ------------------- |
  | filterOptions        |  &nbsp;[DeviceProfileInfoFilterOptions](#deviceprofileinfofilteroptions15)&nbsp;         | Yes    | Filter condition used during the query.     |

**Return value**

  | Type                                                       | Description                               |
  | ---------------------------------------------------------- | ---------------------------------- |
  | Promise&lt;Array&lt;[DeviceProfileInfo](#deviceprofileinfo15)&gt;&gt; | Promise instance used to return the device list. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 500. |
| 11600102 | Failed to obtain service.                                 |
| 11600106 | Get data from cloud fail. |
| 11600107 | A login account is required.  |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    dmInstance.getDeviceProfileInfoList({"isCloud": false}).then((data: Array<distributedDeviceManager.DeviceProfileInfo>) => {
      console.info('getDeviceProfileInfoList' + JSON.stringify(data));
    }).catch((e: BusinessError) => {
      console.error('getDeviceProfileInfoList errCode:' + e.code + ',errMessage:' + e.message);
    });
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('getDeviceProfileInfoList errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### putDeviceProfileInfoList<sup>18+</sup>

putDeviceProfileInfoList(deviceProfileInfoList: Array&lt;DeviceProfileInfo&gt;): Promise&lt;number&gt;

Updates the device list. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name       | Type            | Mandatory  | Description                |
  | ------------- | --------------- | ---- | ------------------- |
  |  deviceProfileInfoList       |  Array&lt;[DeviceProfileInfo](#deviceprofileinfo15)&gt;        |  Yes   |  List of devices to be updated.    |

**Return value**

  | Type                                                       | Description                               |
  | ---------------------------------------------------------- | ---------------------------------- |
  | Promise&lt;number&gt; | Operation result. The value 0 indicates that the call is successful.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 500. |
| 11600102 | Failed to obtain service.                                 |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    let deviceProfileInfoList:Array<distributedDeviceManager.DeviceProfileInfo> = [];
    dmInstance.putDeviceProfileInfoList(deviceProfileInfoList).then((data:number) => {
      console.info('put device profile info:' + JSON.stringify(data));
    }).catch((e: BusinessError) => {
      console.error('putDeviceProfileInfoList errCode:' + e.code + ',errMessage:' + e.message);
    });
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('putDeviceProfileInfoList errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### getDeviceIconInfo<sup>18+</sup>

getDeviceIconInfo(filterOptions: DeviceIconInfoFilterOptions): Promise&lt;DeviceIconInfo&gt;

Obtains the device icon. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name       | Type            | Mandatory  | Description                |
  | ------------- | --------------- | ---- | ------------------- |
  |  filterOptions       | [DeviceIconInfoFilterOptions](#deviceiconinfofilteroptions18)         | Yes    |  Filter condition used during the query.    |

**Return value**

  | Type                                                       | Description                               |
  | ---------------------------------------------------------- | ---------------------------------- |
  |  Promise&lt;[DeviceIconInfo](#deviceiconinfo18)&gt; | Promise instance used to return the device icon information.                                    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; |
| 11600102 | Failed to obtain service.                                 |
| 11600106 | Get data from cloud fail. |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    let productIds:Array<string> = ['M0D2', 'M0D3', 'M0D5', 'M0AB', 'M0BD', 'M0E9', 'M0BC', 'M0EA'];
    let options:distributedDeviceManager.DeviceIconInfoFilterOptions = {
      productId: 'P14U',
      imageType: 'ID',
      specName: 'lg',
    };
    if (productIds.indexOf(options.productId) != -1) {
      options.internalModel = '';
    } else {
      options.subProductId = '';
    }
    dmInstance.getDeviceIconInfo(options).then((data: distributedDeviceManager.DeviceIconInfo) => {
      console.info('getDeviceIconInfo' + JSON.stringify(data));
    }).catch((e : BusinessError) => {
      console.error('getDeviceIconInfo errCode:' + e.code + ',errMessage:' + e.message);
    });
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('getDeviceIconInfo errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### getLocalDisplayDeviceName<sup>18+</sup>

getLocalDisplayDeviceName(maxNameLength: number): Promise&lt;string&gt;

Obtains the local device's display name with the specified length. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name       | Type            | Mandatory  | Description                |
  | ------------- | --------------- | ---- | ------------------- |
  |  maxNameLength       |  number        |  Yes  | Length (in bytes) of the displayable device name. The value range is [18, 100]. The value 0 indicates no limit.     |

**Return value**

  | Type                                                       | Description                               |
  | ---------------------------------------------------------- | ---------------------------------- |
  | Promise&lt;string&gt; | Display name of the local device with the specified maximum name length in bytes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; |
| 11600102 | Failed to obtain service.                                 |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    let maxNameLength:number = 21;
    dmInstance.getLocalDisplayDeviceName(maxNameLength).then((data:string)=>{
      console.info('getLocalDisplayDeviceName name:' + JSON.stringify(data));
    }).catch((e: BusinessError)=>{
      console.error('getLocalDisplayDeviceName errCode:' + e.code + ',errMessage:' + e.message);
    });
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('getLocalDisplayDeviceName errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### setLocalDeviceName<sup>18+</sup>

setLocalDeviceName(deviceName: string): Promise&lt;number&gt;

Sets the local device name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name       | Type            | Mandatory  | Description                |
  | ------------- | --------------- | ---- | ------------------- |
  |  deviceName       | string         |  Yes   | Custom device name. The string length ranges from 1 to 255.     |

**Return value**

  | Type                                                       | Description                               |
  | ---------------------------------------------------------- | ---------------------------------- |
  | Promise&lt;number&gt; | Operation result. The value 0 indicates that the call is successful. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; |
| 11600102 | Failed to obtain service.                                 |
| 11600106 | Failed to get data from the cloud. |
| 11600107 | A login account is required.  |
| 11600108 | The device name contains non-compliant content. |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    let deviceName:string = 'xxx';
    dmInstance.setLocalDeviceName(deviceName).then((data:number)=>{
      console.info('setLocalDeviceName name:' + JSON.stringify(data));
    }).catch((e: BusinessError)=>{
      console.error('setLocalDeviceName errCode:' + e.code + ',errMessage:' + e.message);
    });
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('setLocalDeviceName errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### setRemoteDeviceName<sup>18+</sup>

setRemoteDeviceName(deviceId: string, deviceName: string): Promise&lt;number&gt;

Sets the remote device name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name       | Type            | Mandatory  | Description                |
  | ------------- | --------------- | ---- | ------------------- |
  |  deviceId       | string         | Yes    | UDID of the accessory device. For a device without a UDID, the MAC or SN is used, with the SN preferred.     |
  |  deviceName       | string         | Yes    | Custom device name. The string length ranges from 1 to 255.    |

**Return value**

  | Type                                                       | Description                               |
  | ---------------------------------------------------------- | ---------------------------------- |
  | Promise&lt;number&gt; | Operation result. 0 indicates that the call is successful. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; |
| 11600102 | Failed to obtain service.                                 |
| 11600106 | Failed to get data from the cloud. |
| 11600107 | A login account is required.  |
| 11600108 | The device name contains non-compliant content. |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    let deviceId:string = 'xxx';
    let deviceName:string = 'xxx';
    dmInstance.setRemoteDeviceName(deviceId, deviceName).then((data:number)=>{
      console.info('setRemoteDeviceName name:' + JSON.stringify(data));
    }).catch((e: BusinessError)=>{
      console.error('setRemoteDeviceName errCode:' + e.code + ',errMessage:' + e.message);
    });
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('setRemoteDeviceName errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### getDeviceNetworkIdList<sup>18+</sup>

getDeviceNetworkIdList(filterOptions: NetworkIdQueryFilter): Promise&lt;Array&lt;string&gt;&gt;

Obtains the list of network devices according to the specified filter options. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Parameters**

  | Name       | Type            | Mandatory  | Description                |
  | ------------- | --------------- | ---- | ------------------- |
  |   filterOptions      | [NetworkIdQueryFilter](#networkidqueryfilter18)         |  Yes   |   Filter condition used during the query.   |

**Return value**

  | Type                                                       | Description                               |
  | ---------------------------------------------------------- | ---------------------------------- |
  | Promise&lt;Array&lt;string&gt;&gt; |  Promise instance used to return the list of device network IDs.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed; |
| 11600102 | Failed to obtain service.                                 |
| 11600107 | A login account is required.  |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let queryFiler: distributedDeviceManager.NetworkIdQueryFilter = {
      wiseDeviceId: '',
      onlineStatus: 1,
    }
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    dmInstance.getDeviceNetworkIdList(queryFiler).then((data:Array<string>) => {
      console.info('getDeviceNetworkIdList name:' + JSON.stringify(data));
    }).catch((e: BusinessError) => {
      console.error('getDeviceNetworkIdList errCode:' + e.code + ',errMessage:' + e.message);
    })
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('getDeviceNetworkIdList errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```
### getIdentificationByDeviceIds<sup>24+</sup>

getIdentificationByDeviceIds(deviceIds: Array&lt;string&gt;): Array&lt;DeviceIdentification&gt;;

Queries the device identification based on the device ID.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM, ohos.permission.DISTRIBUTED_DATASYNC, and ohos.permission.sec.ACCESS_UDID

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

  | Name       | Type                  | Mandatory  | Description               |
  | ------------- |---------------------| ---- |------------------|
  |   deviceIds      | Array&lt;string&gt; |  Yes   | List of device IDs that the application can obtain. |

**Return value**

  | Type                                                           | Description            |
  |--------------------------------------------------------------| --------------- |
  | Array&lt;[DeviceIdentification](#deviceidentification24)&gt; |  List of DeviceIdentification objects.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID    | Error Message                                                                                                              |
|----------|-------------------------------------------------------------------------------------------------------------------|
| 201      | Permission verification failed. The application does not have the permission required to call the API.            |
| 202      | Permission verification failed. A non-system application calls a system API.                                    |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types;3. Parameter verification failed; |
| 11600101 | Failed to execute the function.                                                                        |

**Example**

  ```ts

  let idsLists: undefined|Array<distributedDeviceManager.DeviceIdentification> = [];
  let deviceIds: Array<string> = [];
  try {
    let deviceManager = distributedDeviceManager.createDeviceManager('com.example.myapplication');
    idsLists = deviceManager?.getIdentificationByDeviceIds(deviceIds);
    console.info("Successfully retrieved UDID list");
  } catch (error) {
    console.error('Get device UDID failed:', error);
    idsLists = [];
  }
  ```

### restoreLocalDeviceName<sup>24+</sup>

restoreLocalDeviceName(): void

Restores the local device name by resetting the network settings.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 11600102 | Failed to obtain the service.                                 |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    dmInstance.restoreLocalDeviceName();
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('restoreLocalDeviceName errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### restoreLocalDeivceName<sup>(deprecated)</sup>

restoreLocalDeivceName(): void

Restores the local device name by resetting the network settings.

> **NOTE**
>
> This API is supported since API version 18 and deprecated since API version 24. You are advised to use [restoreLocalDeviceName](#restorelocaldevicename24) instead.

**Required permissions**: ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**System API**: This is a system API.

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 11600102 | Failed to obtain the service.                                 |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    dmInstance.restoreLocalDeivceName();
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('restoreLocalDeivceName errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```

### getOsTypeByNetworkId

getOsTypeByNetworkId(networkId: string): number

Queries the OS type of a device based on the device network ID.

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.ACCESS_SERVICE_DM

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Device behavior difference**: Calling this API on a Wearable device that does not support distributed services returns error code 801.

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Since:** 26.0.1

**Parameters**

  | Name       | Type            | Mandatory  | Description                |
  | ------------- | --------------- | ---- | ------------------- |
  |  networkId       | string         | Yes    | Device network ID.     |

**Return value**

  | Type                                                       | Description                               |
  | ---------------------------------------------------------- | ---------------------------------- |
  | number | OS type of the device.<br>- 10: OpenHarmony-based OS.<br>- 11: non-OpenHarmony-based OS.<br>- -1: unknown. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Management Error Codes](errorcode-device-manager.md).

| ID | Error Message                                                        |
| -------- | --------------------------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.                                            |
| 202 | Permission verification failed. A non-system application calls a system API.                              |
| 11600102 | Failed to obtain service.                                 |
| 11600110 | Invalid network ID.                                 |

**Example**

  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
    let networkId: string = 'test_network_id';
    let osType: number = dmInstance.getOsTypeByNetworkId(networkId);
    console.info('getOsTypeByNetworkId result: ' + osType);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('getOsTypeByNetworkId errCode:' + e.code + ',errMessage:' + e.message);
  }
  ```
