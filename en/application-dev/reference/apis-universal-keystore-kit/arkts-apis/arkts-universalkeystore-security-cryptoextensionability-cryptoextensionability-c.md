# CryptoExtensionAbility

```TypeScript
declare class CryptoExtensionAbility
```

Class to be override for external crypto extension ability.

**Since:** 22

<!--Device-unnamed-declare class CryptoExtensionAbility--><!--Device-unnamed-declare class CryptoExtensionAbility-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## ExtensionAbility Usage Restrictions

To ensure system security and stability, CryptoExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult, HuksCryptoExtensionResultCode, HuksCryptoExtensionParam, HuksCryptoExtensionParams } from '@kit.UniversalKeystoreKit';
```

## onAuthUkeyPin

```TypeScript
onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to be called to verify PIN of the provider handle.

**Since:** 22

<!--Device-CryptoExtensionAbility-onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800006 - The UKey PIN is not correct. Please check the PIN you entered. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Perform PIN authentication and maintain the PIN authentication state of the application.
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      authState: 1
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onClearUkeyPinAuthState

```TypeScript
onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to clear the PIN auth state of the provider handle.

**Since:** 22

<!--Device-CryptoExtensionAbility-onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onCloseResource

```TypeScript
onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to be called to close the resource handle.

**Since:** 22

<!--Device-CryptoExtensionAbility-onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Close the handle. If the underlying handle needs to be closed, close it.
    const result: HuksCryptoExtensionResult = {
        resultCode: 0,
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onEnumCertificates

```TypeScript
onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]):
      Promise<HuksCryptoExtensionResult>
```

Callback to list all certificates of the provider.

**Since:** 22

<!--Device-CryptoExtensionAbility-onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]):      Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | No | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800001 - The UKey does not exist. Possible causes:         1. The UKey has been removed.         2. The crypto extension maintained an error UKey state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      certs: certInfoSetArray
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onExportCertificate

```TypeScript
onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to export certificates specified by the resource id.

**Since:** 22

<!--Device-CryptoExtensionAbility-onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | resourceId indicates the resource id of the extension. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | No | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800001 - The UKey does not exist. Possible causes:         1. The UKey has been removed.         2. The crypto extension maintained an error UKey state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The resourceId does not exist. This indicates that the resourceId has an incorrect device name, application name, or container name. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      certs: certInfoSetArray
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onExportKeyItem

```TypeScript
onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to export the public key specified by the resource handle.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CryptoExtensionAbility-onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | Indicates the resource handle of the key to be exported. |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | Indicates the needed properties of the export public key operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. If the function execution fails, the extension needs to set the detailed error information in HuksCryptoExtensionResult.errInfo. HuksCryptoExtensionResult.resultCode may have the following values. 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

**Examples**

```TypeScript
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onExportKeyItem(handle: string, params: huks.HuksParam[]): Promise<HuksCryptoExtensionResult> {
    // Parse the optional parameters. It is recommended that the key purpose be passed.
    let purpose: huks.HuksKeyPurpose | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value as huks.HuksKeyPurpose;

    // If the purpose parameter is not passed, set the default value. (The default signing purpose is recommended.)
    if (purpose === undefined) {
      purpose = huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN;
    }

    let pubKey: Uint8Array = new Uint8Array(1024);
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      outData: pubKey
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onFinishSession

```TypeScript
onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):
      Promise<HuksCryptoExtensionResult>
```

Callback to do the finish operation.

**Since:** 22

<!--Device-CryptoExtensionAbility-onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| initHandle | string | Yes | initHandle indicates the handle returned by onInitSession. |
| params | [huks.HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) &#124; [HuksCryptoExtensionParams](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparams-i.md) | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

**Examples**

```TypeScript
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onFinishSession(initHandle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
    let outBuffer: Uint8Array = new Uint8Array(1024);
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      outData: outBuffer
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onGenerateKeyItem

```TypeScript
onGenerateKeyItem(handle: string, params:HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to generate a key pair specified by the resource handle.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CryptoExtensionAbility-onGenerateKeyItem(handle: string, params:HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onGenerateKeyItem(handle: string, params:HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | Indicates the resource handle of the key to be generated. |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | Indicates the properties of the key generation operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

**Examples**

```TypeScript
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGenerateKeyItem(handle: string, params: huks.HuksParam[]): Promise<HuksCryptoExtensionResult> {
    // Parse optional parameters.
    let algorithm: huks.HuksKeyAlg | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_ALGORITHM)?.value as huks.HuksKeyAlg;
    let keySize: huks.HuksKeySize | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_KEY_SIZE)?.value as huks.HuksKeySize;
    let purpose: huks.HuksKeyPurpose | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value as huks.HuksKeyPurpose;

    // If there is no input parameter, set the default value.
    if (algorithm === undefined) {
      algorithm = huks.HuksKeyAlg.HUKS_ALG_RSA; // RSA is used by default.
    }
    if (keySize === undefined) {
      keySize = huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048; // The default value is 2048 bits.
    }
    if (purpose === undefined) {
      purpose = huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN; // The default purpose is signing.
    }

    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onGetProperty

```TypeScript
onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to be called to do general get operations of the provider.

**Since:** 22

<!--Device-CryptoExtensionAbility-onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| propertyId | string | Yes | propertyId indicates the name of the property function to be operated as defined in GMT 0016-2023. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Execute the related function based on propertyId. The function parameters are obtained from params. The output data is encapsulated in the property field of the return value and carried by HUKS_EXT_CRYPTO_TAG_EXTRA_DATA.
    const emptyArray: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      property: emptyArray
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onGetResourceId

```TypeScript
onGetResourceId(params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to get the resource ID of the crypto extension.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CryptoExtensionAbility-onGetResourceId(params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onGetResourceId(params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | Indicates the needed properties of the get resource ID operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. If the function execution fails, the extension needs to set the detailed error information in HuksCryptoExtensionResult.errInfo. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetResourceId(params: huksExternalCrypto.HuksExternalCryptoParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      resourceId: "test resourceId"
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onGetUkeyPinAuthState

```TypeScript
onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to get the PIN auth state of the provider handle.

**Since:** 22

<!--Device-CryptoExtensionAbility-onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Query the PIN authentication state.
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      authState: 1
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onImportCertificate

```TypeScript
onImportCertificate(handle: string, params: HuksCryptoExtensionParam[],
      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult>
```

Callback to import a certificate specified by the resource handle.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CryptoExtensionAbility-onImportCertificate(handle: string, params: HuksCryptoExtensionParam[],      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onImportCertificate(handle: string, params: HuksCryptoExtensionParam[],      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | Indicates the import certificate's resource handle. |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | Indicates the needed properties for the import certificate operation. |
| certInfo | [HuksCryptoExtensionCertInfo](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensioncertinfo-i.md) | Yes | Indicates the certificate information to be imported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. If the function execution fails, the extension needs to set the detailed error information in HuksCryptoExtensionResult.errInfo. HuksCryptoExtensionResult.resultCode may have the following values. 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onImportCertificate(handle: string, params: huksExternalCrypto.HuksExternalCryptoParam[],
      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onImportWrappedKeyItem

```TypeScript
onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[],
      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult>
```

Callback to import the wrapped key pair specified by the resource handle.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CryptoExtensionAbility-onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[],      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[],      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | Indicates the resource handle of the wrapped key to be imported. |
| wrappingHandle | string | Yes | Indicates the resource handle of the key used to unwrap the imported key. |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | Indicates the needed properties for the import wrapped key operation. |
| wrappedKey | Uint8Array | Yes | Indicates the wrapped key data, which format is defined by the crypto extension. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. If the function execution fails, the extension needs to set the detailed error information in HuksCryptoExtensionResult.errInfo. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of HUKS service and crypto extension are inconsistent. Due to an exception, the handle held by HUKS service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

**Examples**

```TypeScript
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onImportWrappedKeyItem(handle: string, wrappedHandle: string, params: huks.HuksParam[],
      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult> {
    // Parse optional parameters.
    let algorithm: huks.HuksKeyAlg | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_ALGORITHM)?.value as huks.HuksKeyAlg;
    let keySize: huks.HuksKeySize | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_KEY_SIZE)?.value as huks.HuksKeySize;
    let purpose: huks.HuksKeyPurpose | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value as huks.HuksKeyPurpose;

    // If there is no input parameter, set the default value.
    if (algorithm === undefined) {
      algorithm = huks.HuksKeyAlg.HUKS_ALG_RSA;
    }
    if (keySize === undefined) {
      keySize = huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048;
    }
    if (purpose === undefined) {
      purpose = huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT;
    }

    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onInitSession

```TypeScript
onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):
      Promise<HuksCryptoExtensionResult>
```

Callback to do the initialize operation.

**Since:** 22

<!--Device-CryptoExtensionAbility-onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | [huks.HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) &#124; [HuksCryptoExtensionParams](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparams-i.md) | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

**Examples**

```TypeScript
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onInitSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      handle: "test handle"
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onOpenResource

```TypeScript
onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
     HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

Callback to be called to open the resource handle before crypto operations. NOTE: the handle returned must be closed by onCloseResource.

**Since:** 22

<!--Device-CryptoExtensionAbility-onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |     HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |     HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | resourceId indicates the resource id of the provider. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800001 - The UKey does not exist. Possible causes:         1. The UKey has been removed.         2. The crypto extension maintained an error UKey state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The resourceId does not exist. This indicates that the resourceId has an incorrect device name, application name, or container name. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Parse resourceId, open the underlying handle, and map it to a new handle for return.
    let result: HuksCryptoExtensionResult = {
      resultCode: 0,
      handle: "test handle"
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onSetProperty

```TypeScript
onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]):
      Promise<HuksCryptoExtensionResult>
```

Callback to perform set operations of the provider.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CryptoExtensionAbility-onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]):      Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | Indicates the resource handle for the set operation. |
| propertyId | string | Yes | Indicates the ID of the property needed to set. Currently supports part of the method names defined in GMT 0016-2023 and self-defined methods. |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | Indicates the operation parameters. This parameter contains parameters related to the property ID needed to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey connection and driver status. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of HUKS service and crypto extension are inconsistent. Due to an exception, the handle held by HUKS service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

**Examples**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onSetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Perform related setting operations based on propertyId. The operation parameters are obtained from params.
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## onUpdateSession

```TypeScript
onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):
      Promise<HuksCryptoExtensionResult>
```

Callback to do update operation.

**Since:** 22

<!--Device-CryptoExtensionAbility-onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| initHandle | string | Yes | initHandle indicates the handle returned by onInitSession. |
| params | [huks.HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) &#124; [HuksCryptoExtensionParams](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparams-i.md) | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes:         1. The input parameter is invalid.         2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes:         1. The handle you entered is invalid.         2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

**Examples**

```TypeScript
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onUpdateSession(initHandle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
    let outBuffer: Uint8Array = new Uint8Array(1024);
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      outData: outBuffer
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## Appendix

CryptoExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Ads Kit | [@ohos.advertising.AdComponent](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-adcomponent.md) |
| Ads Kit | [@ohos.advertising.AdsServiceExtensionAbility](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-adsserviceextensionability.md) |
| Ads Kit | [@ohos.advertising.AutoAdComponent](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-autoadcomponent.md) |
| Ads Kit | [@ohos.advertising](../../apis-ads-kit/arkts-apis/arkts-ads-advertising.md) |
| Basic Services Kit | [@ohos.ai.intelligentVoice](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-ai-intelligentvoice.md) |
| MindSpore Lite Kit | [@ohos.ai.mindSporeLite](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-ai-mindsporelite.md) |
| Form Kit | [@ohos.app.form.formAgent](../../apis-form-kit/arkts-apis/arkts-form-app-form-formagent.md) |
| Form Kit | [@ohos.app.form.formBindingData](../../apis-form-kit/arkts-apis/arkts-form-app-form-formbindingdata.md) |
| Form Kit | [@ohos.app.form.FormEditExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formeditextensionability.md) |
| Form Kit | [@ohos.app.form.FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability.md) |
| Form Kit | [@ohos.app.form.formHost](../../apis-form-kit/arkts-apis/arkts-form-app-form-formhost.md) |
| Form Kit | [@ohos.app.form.formInfo](../../apis-form-kit/arkts-apis/arkts-form-app-form-forminfo.md) |
| Form Kit | [@ohos.app.form.formObserver](../../apis-form-kit/arkts-apis/arkts-form-app-form-formobserver.md) |
| Form Kit | [@ohos.app.form.formProvider](../../apis-form-kit/arkts-apis/arkts-form-app-form-formprovider.md) |
| Form Kit | [@ohos.app.form.LiveFormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-liveformextensionability.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceNavigation](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicenavigation.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceSearch](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicesearch.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceTabs](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicetabs.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceWeb](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicserviceweb.md) |
| ArkUI | [@ohos.atomicservice.HalfScreenLaunchComponent](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-halfscreenlaunchcomponent.md) |
| ArkUI | [@ohos.atomicservice.InterstitialDialogAction](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-interstitialdialogaction.md) |
| ArkUI | [@ohos.atomicservice.NavPushPathHelper](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-navpushpathhelper.md) |
| Connectivity Kit | [@ohos.bluetooth.a2dp](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-a2dp.md) |
| Connectivity Kit | [@ohos.bluetooth.access](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-access.md) |
| Connectivity Kit | [@ohos.bluetooth.baseProfile](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-baseprofile.md) |
| Connectivity Kit | [@ohos.bluetooth.ble](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-ble.md) |
| Connectivity Kit | [@ohos.bluetooth.common](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-common.md) |
| Connectivity Kit | [@ohos.bluetooth.connection](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-connection.md) |
| Connectivity Kit | [@ohos.bluetooth.constant](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-constant.md) |
| Connectivity Kit | [@ohos.bluetooth](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth.md) |
| Connectivity Kit | [@ohos.bluetooth.hfp](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-hfp.md) |
| Connectivity Kit | [@ohos.bluetooth.hid](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-hid.md) |
| Connectivity Kit | [@ohos.bluetoothManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetoothmanager.md) |
| Connectivity Kit | [@ohos.bluetooth.map](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-map.md) |
| Connectivity Kit | [@ohos.bluetooth.opp](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-opp.md) |
| Connectivity Kit | [@ohos.bluetooth.pan](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-pan.md) |
| Connectivity Kit | [@ohos.bluetooth.pbap](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-pbap.md) |
| Connectivity Kit | [@ohos.bluetooth.socket](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-socket.md) |
| Connectivity Kit | [@ohos.bluetooth.wearDetection](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-weardetection.md) |
| Calendar Kit | [@ohos.calendarManager](../../apis-calendar-kit/arkts-apis/arkts-calendar-calendarmanager.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Ability Kit | [@ohos.distributedBundle](../../apis-ability-kit/arkts-apis/arkts-ability-distributedbundle.md) |
| Distributed Service Kit | [@ohos.distributedDeviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager.md) |
| Distributed Service Kit | [@ohos.distributedHardware.deviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedhardware-devicemanager.md) |
| Distributed Service Kit | [@ohos.distributedHardware.hardwareManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedhardware-hardwaremanager.md) |
| Mechanic Kit | [@ohos.distributedHardware.mechanicManager](../../apis-mechanic-kit/arkts-apis/arkts-mechanic-distributedhardware-mechanicmanager.md) |
| Ability Kit | [@ohos.distributedMissionManager](../../apis-ability-kit/arkts-apis/arkts-ability-distributedmissionmanager.md) |
| Distributed Service Kit | [@ohos.distributedsched.abilityConnectionManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedsched-abilityconnectionmanager.md) |
| Distributed Service Kit | [@ohos.distributedsched.linkEnhance](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedsched-linkenhance.md) |
| Distributed Service Kit | [@ohos.distributedsched.proxyChannelManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedsched-proxychannelmanager.md) |
| Data Protection Kit | [@ohos.dlpPermission](../../apis-data-protection-kit/arkts-apis/arkts-dataprotection-dlppermission.md) |
| MDM Kit | [@ohos.enterprise.accountManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-accountmanager.md) |
| MDM Kit | [@ohos.enterprise.adminManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-adminmanager.md) |
| MDM Kit | [@ohos.enterprise.applicationManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-applicationmanager.md) |
| MDM Kit | [@ohos.enterprise.bluetoothManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-bluetoothmanager.md) |
| MDM Kit | [@ohos.enterprise.browser](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-browser.md) |
| MDM Kit | [@ohos.enterprise.bundleManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-bundlemanager.md) |
| MDM Kit | [@ohos.enterprise.common](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-common.md) |
| MDM Kit | [@ohos.enterprise.dateTimeManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-datetimemanager.md) |
| MDM Kit | [@ohos.enterprise.deviceControl](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-devicecontrol.md) |
| MDM Kit | [@ohos.enterprise.deviceInfo](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-deviceinfo.md) |
| MDM Kit | [@ohos.enterprise.deviceSettings](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-devicesettings.md) |
| MDM Kit | [@ohos.enterprise.EnterpriseAdminExtensionAbility](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-enterpriseadminextensionability.md) |
| MDM Kit | [@ohos.enterprise.locationManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-locationmanager.md) |
| MDM Kit | [@ohos.enterprise.networkManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-networkmanager.md) |
| MDM Kit | [@ohos.enterprise.restrictions](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-restrictions.md) |
| MDM Kit | [@ohos.enterprise.securityManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-securitymanager.md) |
| MDM Kit | [@ohos.enterprise.systemManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-systemmanager.md) |
| MDM Kit | [@ohos.enterprise.telephonyManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-telephonymanager.md) |
| MDM Kit | [@ohos.enterprise.usbManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-usbmanager.md) |
| MDM Kit | [@ohos.enterprise.wifiManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-wifimanager.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md) |
| ArkUI | [@ohos.mediaquery](../../apis-arkui/arkts-apis/arkts-arkui-mediaquery.md) |
| arkui | [mediaquery.static](../../apis-arkui/arkts-apis/arkts-mediaquery-static.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Audio Kit | [@ohos.multimedia.audioHaptic](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audiohaptic.md) |
| AVSession Kit | [@ohos.multimedia.avCastPicker](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avcastpicker.md) |
| AVSession Kit | [@ohos.multimedia.avCastPickerParam](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avcastpickerparam.md) |
| Avsession Kit | [multimedia.avCastPicker.static](../../apis-avsession-kit/arkts-apis/arkts-multimedia-avcastpicker-static.md) |
| AVSession Kit | [@ohos.multimedia.avInputCastPicker](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avinputcastpicker.md) |
| Avsession Kit | [multimedia.avInputCastPicker.static](../../apis-avsession-kit/arkts-apis/arkts-multimedia-avinputcastpicker-static.md) |
| AVSession Kit | [@ohos.multimedia.avsession](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avsession.md) |
| Audio Kit | [@ohos.multimedia.avVolumePanel](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-avvolumepanel.md) |
| Audio Kit | [multimedia.avVolumePanel.static](../../apis-audio-kit/arkts-apis/arkts-multimedia-avvolumepanel-static.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camerapicker.md) |
| DRM Kit | [@ohos.multimedia.drm](../../apis-drm-kit/arkts-apis/arkts-drm-multimedia-drm.md) |
| Image Kit | [@ohos.multimedia.image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Media Library Kit | [@ohos.multimedia.movingphotoview](../../apis-media-library-kit/arkts-components/arkts-medialibrary-multimedia-movingphotoview.md) |
| Image Kit | [@ohos.multimedia.sendableImage](../../apis-image-kit/arkts-apis/arkts-image-multimedia-sendableimage.md) |
| Audio Kit | [@ohos.multimedia.systemSoundManager](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-systemsoundmanager.md) |
| Image Kit | [@ohos.multimedia.videoProcessingEngine](../../apis-image-kit/arkts-apis/arkts-image-multimedia-videoprocessingengine.md) |
| Network Kit | [@ohos.net.connection](../../apis-network-kit/arkts-apis/arkts-network-net-connection.md) |
| Network Kit | [@ohos.net.eap](../../apis-network-kit/arkts-apis/arkts-network-net-eap.md) |
| Network Kit | [@ohos.net.ethernet](../../apis-network-kit/arkts-apis/arkts-network-net-ethernet.md) |
| Network Kit | [@ohos.net.http](../../apis-network-kit/arkts-apis/arkts-network-net-http.md) |
| Network Kit | [@ohos.net.mdns](../../apis-network-kit/arkts-apis/arkts-network-net-mdns.md) |
| Network Kit | [@ohos.net.netFirewall](../../apis-network-kit/arkts-apis/arkts-network-net-netfirewall.md) |
| Network Kit | [@ohos.net.networkSecurity](../../apis-network-kit/arkts-apis/arkts-network-net-networksecurity.md) |
| Network Kit | [@ohos.net.policy](../../apis-network-kit/arkts-apis/arkts-network-net-policy.md) |
| Network Kit | [@ohos.net.sharing](../../apis-network-kit/arkts-apis/arkts-network-net-sharing.md) |
| Network Kit | [@ohos.net.statistics](../../apis-network-kit/arkts-apis/arkts-network-net-statistics.md) |
| Network Kit | [@ohos.net.vpn](../../apis-network-kit/arkts-apis/arkts-network-net-vpn.md) |
| Network Kit | [@ohos.net.vpnExtension](../../apis-network-kit/arkts-apis/arkts-network-net-vpnextension.md) |
| Network Kit | [@ohos.net.webSocket](../../apis-network-kit/arkts-apis/arkts-network-net-websocket.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Basic Services Kit | [@ohos.pasteboard](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-pasteboard.md) |
| ArkUI | [@ohos.PiPWindow](../../apis-arkui/arkts-apis/arkts-arkui-pipwindow.md) |
| Basic Services Kit | [@ohos.scan](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-scan.md) |
| Basic Services Kit | [@ohos.screenLock](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-screenlock.md) |
| ArkUI | [@ohos.screenshot](../../apis-arkui/arkts-apis/arkts-arkui-screenshot.md) |
| Basic Services Kit | [@ohos.settings](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-settings.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.data](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-data.md) |
| Telephony Kit | [@ohos.telephony.esim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-esim.md) |
| Telephony Kit | [@ohos.telephony.observer](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-observer.md) |
| Telephony Kit | [@ohos.telephony.radio](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-radio.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Telephony Kit | [@ohos.telephony.vcard](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-vcard.md) |
| ArkTS | [@ohos.transfer](../../apis-arkts/arkts-apis/arkts-arkts-transfer.md) |
| Basic Services Kit | [@ohos.wallpaper](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaper.md) |
| Basic Services Kit | [@ohos.WallpaperExtensionAbility](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaperextensionability.md) |
| Ability Kit | [@ohos.wantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent.md) |
| ArkWeb | [@ohos.web.netErrorList](../../apis-arkweb/arkts-apis/arkts-arkweb-web-neterrorlist.md) |
| arkweb | [web.netErrorList.static](../../apis-arkweb/arkts-apis/arkts-web-neterrorlist-static.md) |
| ArkWeb | [@ohos.web.WebNativeMessagingExtensionAbility](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensionability.md) |
| arkweb | [web.WebNativeMessagingExtensionAbility.static](../../apis-arkweb/arkts-apis/arkts-web-webnativemessagingextensionability-static.md) |
| ArkWeb | [@ohos.web.WebNativeMessagingExtensionContext](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensioncontext.md) |
| arkweb | [web.WebNativeMessagingExtensionContext.static](../../apis-arkweb/arkts-apis/arkts-web-webnativemessagingextensioncontext-static.md) |
| ArkWeb | [@ohos.web.webNativeMessagingExtensionManager](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensionmanager.md) |
| arkweb | [web.webNativeMessagingExtensionManager.static](../../apis-arkweb/arkts-apis/arkts-web-webnativemessagingextensionmanager-static.md) |
| ArkWeb | [@ohos.web.webview](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webview.md) |
| arkweb | [web.webview.static](../../apis-arkweb/arkts-apis/arkts-web-webview-static.md) |
| Connectivity Kit | [@ohos.wifi](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifi.md) |
| Connectivity Kit | [@ohos.wifiext](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifiext.md) |
| Connectivity Kit | [@ohos.wifiManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanager.md) |
| Connectivity Kit | [@ohos.wifiManagerExt](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanagerext.md) |
