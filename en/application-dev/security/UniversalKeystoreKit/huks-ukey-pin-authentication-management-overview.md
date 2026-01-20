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

> **NOTE**
> HUKS provides the PIN authentication and authentication status query capabilities. Before the PIN authentication, you can query its authentication status. If PIN authentication is required, the [certificate management for applications](../DeviceCertificateKit/certManager-overview.md) needs to be started.
