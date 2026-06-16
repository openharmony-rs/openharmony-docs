# Ukey PIN Authentication Overview and Specifications

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

A personal identification number (PIN) is the security access credential of a Ukey device. The two-factor authentication mode of "hardware device + PIN" is used, which means that users must have both physical Ukey device and correct PINs to access the key materials in the devices.

The PIN provides the following functions:

1. Anti-brute force cracking: If the number of consecutive incorrect PINs reaches a certain value (related to the external key management extension capability implemented by the driver application), the device is automatically locked.

2. Hardware-level security: PIN verification is performed in the Ukey device, so that sensitive information is not leaked out of the device.

The Ukey device uses **resourceId** to identify its resources. After an ecosystem application opens the resource, if the application needs to perform signing operations on the private key corresponding to **resourceId**, the PIN must be verified first.

## PIN Authentication Status Management

HUKS provides the following PIN authentication status management capabilities:

- **Querying the authentication status**: Call [getUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetukeypinauthstate) to query the current PIN authentication status.
- **Clearing the authentication status**: Since API version 26.0.0, you can use [clearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoclearukeypinauthstate) to clear the PIN authentication status of a specified resource.

### Scenarios for Clearing the Authentication Status

The PIN authentication status may need to be cleared in the following scenarios:

- After a key operation is complete, the authentication status is proactively cleared to avoid residual authentication status.
- Clear the authentication status when the application exits or the user is switched.
- Reset the authentication status when it is abnormal.

For details about the development example, see [Clearing the PIN Authentication Status (ArkTS)](huks-clear-pin-auth-state-arkts.md).

> **NOTE**
>
> HUKS provides the PIN authentication and authentication status query capabilities. Before the PIN authentication, you can query its authentication status. If PIN authentication is required, the [certificate management for applications](../DeviceCertificateKit/certManager-overview.md) needs to be started.
<!--no_check-->