# CryptoExtensionAbility

Class to be override for external crypto extension ability.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800006 - The UKey PIN is not correct. Please check the PIN you entered. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | No | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800001 - The UKey does not exist. Possible causes: 1. The UKey has been removed. 2. The crypto extension maintained an error UKey state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | resourceId indicates the resource id of the extension. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | No | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800001 - The UKey does not exist. Possible causes: 1. The UKey has been removed. 2. The crypto extension maintained an error UKey state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The resourceId does not exist. This indicates that the resourceId has an incorrect device name, application name, or container name. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | Indicates the resource handle of the key to be exported. |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | Indicates the needed properties of the export public key operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. If the function execution fails, the extension needs to set the detailed error information in HuksCryptoExtensionResult.errInfo. HuksCryptoExtensionResult.resultCode may have the following values. 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| initHandle | string | Yes | initHandle indicates the handle returned by onInitSession. |
| params | [huks.HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) &#124; [HuksCryptoExtensionParams](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparams-i.md) | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | Indicates the resource handle of the key to be generated. |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | Indicates the properties of the key generation operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

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
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | Indicates the needed properties of the get resource ID operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. If the function execution fails, the extension needs to set the detailed error information in HuksCryptoExtensionResult.errInfo. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

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
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. If the function execution fails, the extension needs to set the detailed error information in HuksCryptoExtensionResult.errInfo. HuksCryptoExtensionResult.resultCode may have the following values. 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

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
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. If the function execution fails, the extension needs to set the detailed error information in HuksCryptoExtensionResult.errInfo. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey's connection and driver status. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of HUKS service and crypto extension are inconsistent. Due to an exception, the handle held by HUKS service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | string | Yes | handle indicates the handle opened by onOpenResource. |
| params | [huks.HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) &#124; [HuksCryptoExtensionParams](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparams-i.md) | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | resourceId indicates the resource id of the provider. |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800001 - The UKey does not exist. Possible causes: 1. The UKey has been removed. 2. The crypto extension maintained an error UKey state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800004 - The resourceId does not exist. This indicates that the resourceId has an incorrect device name, application name, or container name. |

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
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful. 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - Failed to call the UKey driver interface. Please check the UKey connection and driver status. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of HUKS service and crypto extension are inconsistent. Due to an exception, the handle held by HUKS service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

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

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| initHandle | string | Yes | initHandle indicates the handle returned by onInitSession. |
| params | [huks.HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) &#124; [HuksCryptoExtensionParams](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparams-i.md) | Yes | params indicates the properties of the operation<br>**Since:** 26.0.0 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise used to return HuksCryptoExtensionResult. HuksCryptoExtensionResult.resultCode may have the following values: 0 - The operation is successful 34800000 - An error occurred in the crypto extension. Possible causes: 1. The input parameter is invalid. 2. The crypto extension encountered an unresolvable error state. 34800002 - The UKey driver error. This means an unknown error has occurred in the UKey driver. 34800003 - The UKey PIN is not authenticated. Please verify the UKey PIN first. 34800004 - The handle does not exist. Possible causes: 1. The handle you entered is invalid. 2. The states of huks service and crypto extension are inconsistent. Due to an exception, the handle held by huks service was not released. 34800005 - The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey. 34800007 - The UKey PIN is locked because the maximum allowed number of attempts has been exceeded. |

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
