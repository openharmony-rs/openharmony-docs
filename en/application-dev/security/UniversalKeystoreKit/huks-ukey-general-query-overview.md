# General Query Overview and Specifications

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

HUKS provides a property query API to support general query operations (such as querying Ukey device and PIN information) from external key management.

> **NOTE**
>
> 1. **resourceId** of the [OH_Huks_GetProperty](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getproperty) and [getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty) APIs indicates the resource ID of the provider, which is used to identify the remote resource to be queried. The value must contain 1 to 1,024 bytes. The API property ID is the SKF function name defined in the GMT 0016-2023 standard. The length must be 1 to 100 bytes.
> 2. Output parameters are carried by [HUKS_EXT_CRYPTO_TAG_EXTRA_DATA](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag). The application can extract the found property data and parse the data according to the agreement with the driver application (external key management extension provider).

## Supported Property Function Names (Example)

The following are examples of property function names for reference (for more detailed and authoritative function names, see GMT 0016-2023):

| Function Name| Description|
| -------- | -------- |
| SKF_GetDevInfo | Obtains device information.|
| SKF_EnumDev | Enumerates devices.|
| SKF_EnumContainer | Enumerates containers.|
| SKF_EnumApplication | Enumerates applications.|

> **NOTE**
> The actual implementation must be the same as the function name specified in GMT 0016-2023. All parties (the caller and CryptoExtension implementation) must agree on the function name set and the parameter/return format.
