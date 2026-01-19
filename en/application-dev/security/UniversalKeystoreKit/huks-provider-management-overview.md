# Provider Management Overview and Specifications

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

HUKS provides APIs for registering and unregistering an external key management extension provider (called Provider). When detecting that any Ukey device exists, the third-party driver HAP calls the Provider registration API to register the external key management capability provided by the driver HAP application with the system. When detecting that all Ukey devices are removed, the third-party driver HAP calls the Provider deregistration API to deregister the external key management capability provided by the driver HAP application from the system.

> **NOTE**
> 1. It is recommended that a Provider name contain the vendor information and be globally unique.
> 2. A Provider name can contain a maximum of 128 bytes.
> 3. The registration and deregistration of a Provider are under permission control. You need to apply for the [ohos.permission.CRYPTO_EXTENSION_REGISTER](../AccessToken/restricted-permissions.md#ohospermissioncrypto_extension_register) permission.
> 4. A Provider can be associated with multiple Abilities. Generally, a Provider is the name of a vendor driver, and an Ability is the name of the extended capability customized by the vendor for each service. The vendor can also determine the names of the Provider and Ability.

**Supported function specifications**

| Function| Description| API Version|
| -------- | -------- | -------- |
| Provider registration| Registers an external key management extension provider to the system.| 22+ |
| Provider unregistration| Unregisters an external key management extension provider from the system.| 22+ |
