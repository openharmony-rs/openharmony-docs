# @ohos.security.huksExternalCrypto(External Key Management)

Provides the functionalities such as registration and deregistration of external key management extension, PIN authentication, and acquisition of authentication state.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [clearUkeyPinAuthState](arkts-universalkeystore-huksexternalcrypto-clearukeypinauthstate-f.md) | Clear the PIN auth state of the specified resource ID. |
| [closeResource](arkts-universalkeystore-huksexternalcrypto-closeresource-f.md) | Close the resource with a specific resource ID. |
| [getErrorInfo](arkts-universalkeystore-huksexternalcrypto-geterrorinfo-f.md) | Get the detailed error information. |
| [getProperty](arkts-universalkeystore-huksexternalcrypto-getproperty-f.md) | Obtains a property value. This API uses a promise to return the result. |
| [getResourceId](arkts-universalkeystore-huksexternalcrypto-getresourceid-f.md) | Obtain the resource ID of the provider. |
| [getUkeyPinAuthState](arkts-universalkeystore-huksexternalcrypto-getukeypinauthstate-f.md) | Obtains the PIN authentication state. This API uses a promise to return the result. |
| [openResource](arkts-universalkeystore-huksexternalcrypto-openresource-f.md) | Open resource by specific resource ID. NOTE: The opened resource must be closed using closeResource. |
| [registerProvider](arkts-universalkeystore-huksexternalcrypto-registerprovider-f.md) | Registers a specified external Provider. This API uses a promise to return the result. |
| [setProperty](arkts-universalkeystore-huksexternalcrypto-setproperty-f.md) | The set-type operations of the external crypto extension support calling custom interfaces. However, the custom interface must be registered with the provider. |
| [unregisterProvider](arkts-universalkeystore-huksexternalcrypto-unregisterprovider-f.md) | Unregisters a specified external Provider. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [authUkeyPin](arkts-universalkeystore-huksexternalcrypto-authukeypin-f-sys.md) | Authenticates a UKey PIN. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md) | Defines the type of the param array used for calling the API. |
| [HuksExternalErrorInfo](arkts-universalkeystore-huksexternalcrypto-huksexternalerrorinfo-i.md) | Defines detailed error information. |

### Enums

| Name | Description |
| --- | --- |
| [HuksExternalCryptoTag](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotag-e.md) | Enumerates the tags used to invoke parameters. |
| [HuksExternalCryptoTagType](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md) | Enumerates the external encrypted data types. |
| [HuksExternalPinAuthState](arkts-universalkeystore-huksexternalcrypto-huksexternalpinauthstate-e.md) | Enumerates the UKey PIN authentication states. |
