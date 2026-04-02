# Error Codes of the Converged Short-Range Service Subsystem

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 34900001 Device Not Registered

**Error Message**

The device is not bound.

**Description**

The device is not registered.

**Possible Causes**

The application does not call [bindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentbinddevice) to register the device.

**Solution**

Call [bindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentbinddevice) to register the device.

## 34900003 Device Not Paired

**Error Message**

The device is not paired.

**Description**

The device is not paired.

**Possible Causes**

The device registered by the application is not paired via Bluetooth.

**Solution**

Perform the Bluetooth pairing process.

## 34900004 Device Address Registered

**Error Message**

The device address has already been bound with PartnerAgentExtensionAbility.

**Description**

The device address has been registered with [PartnerAgentExtensionAbility](js-apis-fusionConnectivity-partnerAgentExtensionAbility.md).

**Possible Causes**

The application registers the same address again.

**Solution**

Call [unbindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentunbinddevice) to deregister the current device and then registers the new ability of [bindDevice](js-apis-fusionConnectivity-partnerAgent.md#partneragentbinddevice).

## 34900005 Bluetooth Disabled

**Error Message**

Bluetooth disabled.

**Description**

Bluetooth is disabled.

**Possible Causes**

Bluetooth is disabled.

**Solution**

Enable Bluetooth.

## 34900099 Operation Failed

**Error Message**

Operation failed.

**Description**

The operation fails.

**Possible Causes**

The current operation fails due to system reasons.

**Solution**

Retry the operation.
