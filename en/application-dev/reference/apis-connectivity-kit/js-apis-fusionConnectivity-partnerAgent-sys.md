# @ohos.FusionConnectivity.partnerAgent (Device Status Notification Module) (System API)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

This module uses Bluetooth communication technology to provide device discovery and device offline notification features for applications. The module can:

- Dynamically listen to and discovers Bluetooth devices pre-registered by the applications.
- Leverage the process startup mechanism to automatically start the [PartnerAgentExtensionAbility](js-apis-fusionConnectivity-partnerAgentExtensionAbility.md) process of the applications when the target devices appear.
- Use the process destruction mechanism to automatically destroy the [PartnerAgentExtensionAbility](js-apis-fusionConnectivity-partnerAgentExtensionAbility.md) process of the applications when all the devices go offline.
- Notify the applications of registered devices through the [PartnerAgentExtensionAbility](js-apis-fusionConnectivity-partnerAgentExtensionAbility.md) API.

> **NOTE**
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { partnerAgent } from '@kit.ConnectivityKit';
```

## partnerAgent.enableDeviceControl

enableDeviceControl(deviceAddress: PartnerDeviceAddress): Promise&lt;void&gt;

Enables peripheral interconnection. This API uses a promise to return the result.

- This API takes effect only for devices registered by an application using [BindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentbinddevice). After being called, this API will provide the [device interconnection capability](js-apis-fusionConnectivity-partnerAgent.md) for the application.
- You can call [isDeviceControlEnabled](js-apis-fusionConnectivity-partnerAgent.md#partneragentisdevicecontrolenabled) to check whether the peripheral interconnection feature is enabled. If the feature has been enabled, the repeated calling does not take effect.
- You can call [disableDeviceControl](#partneragentdisabledevicecontrol) to disable the peripheral interconnection feature.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.FusionConnectivity.Core

**Parameters**

| **Name**    | **Type**                                    | **Mandatory**  | **Description**                                 |
| ------- | -------------------------------------- | ---- | ----------------------------------- |
| deviceAddress | [PartnerDeviceAddress](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartnerdeviceaddress) | Yes   | Address information of the device registered by the application.<br>The application must be configured with the **bluetoothAddress** option of the **PartnerDeviceAddress** type.|

**Return value**

| **Type**                 | **Description**                 |
| ------------------- | ------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Error Codes of the Converged Short-Range Service Subsystem](../apis-connectivity-kit/errorcode-fusionConnectivity.md).

| **ID**| **Error Message**|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs.                 |
|801 | Capability not supported.          |
|34900001 | The device is not bound.                         |
|34900099 | Internal error. |

**Example**

```js
import { partnerAgent, common } from '@kit.ConnectivityKit';
try {
  let btAddr: common.BluetoothAddress = {
    "address": "11:22:33:44:55:66",
    "addressType": common.BluetoothAddressType.REAL,
  };
  let deviceAddress: partnerAgent.PartnerDeviceAddress = {
    "bluetoothAddress": btAddr,
  };
  partnerAgent.enableDeviceControl(deviceAddress)
    .then(() => {
      console.info(`enable device control success: ${btAddr.address}`);
    })
    .catch((err: BusinessError) => {
      console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## partnerAgent.disableDeviceControl

disableDeviceControl(deviceAddress: PartnerDeviceAddress): Promise&lt;void&gt;

Disables peripheral interconnection. This API uses a promise to return the result.

- This API takes effect only for devices registered by an application using [BindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentbinddevice). After being called, this API will not provide the [device interconnection capability](js-apis-fusionConnectivity-partnerAgent.md) for the application.
- You can call [isDeviceControlEnabled](js-apis-fusionConnectivity-partnerAgent.md#partneragentisdevicecontrolenabled) to check whether the peripheral interconnection feature is enabled. If the feature has been disabled, the repeated calling does not take effect.
- After the feature is disabled, the [PartnerAgentExtensionAbility](js-apis-fusionConnectivity-partnerAgentExtensionAbility.md) process registered by the application will not be started when the devices that are registered by other applications using [BindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentbinddevice) are discovered. You can call [enableDeviceControl](#partneragentenabledevicecontrol) to enable the feature again.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.FusionConnectivity.Core

**Parameters**

| **Name**    | **Type**                                    | **Mandatory**  | **Description**                                 |
| ------- | -------------------------------------- | ---- | ----------------------------------- |
| deviceAddress | [PartnerDeviceAddress](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartnerdeviceaddress) | Yes| Address information of the device registered by the application.<br>The application must be configured with the **bluetoothAddress** option of the **PartnerDeviceAddress** type.|

**Return value**

| **Type**                 | **Description**                 |
| ------------------- | ------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Error Codes of the Converged Short-Range Service Subsystem](../apis-connectivity-kit/errorcode-fusionConnectivity.md).

| **ID**| **Error Message**|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs.                 |
|801 | Capability not supported.          |
|34900001 | The device is not bound.                         |
|34900099 | Internal error. |

**Example**

```js
import { partnerAgent, common } from '@kit.ConnectivityKit';
try {
  let btAddr: common.BluetoothAddress = {
    "address": "11:22:33:44:55:66",
    "addressType": common.BluetoothAddressType.REAL,
  };
  let deviceAddress: partnerAgent.PartnerDeviceAddress = {
    "bluetoothAddress": btAddr,
  };
  partnerAgent.disableDeviceControl(deviceAddress)
    .then(() => {
      console.info(`disable device control success: ${btAddr.address}`);
    })
    .catch((err: BusinessError) => {
      console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
