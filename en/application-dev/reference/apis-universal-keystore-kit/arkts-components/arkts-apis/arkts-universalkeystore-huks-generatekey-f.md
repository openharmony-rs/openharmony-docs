# generateKey

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## generateKey

```TypeScript
function generateKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

Generates a key. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [generateKeyItem](arkts-universalkeystore-huks-generatekeyitem-f.md)(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key. The value can contain up to 128 bytes and should not include sensitive data such as personal information. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Tags required for generating the key. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the obtained **HuksResult**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Generate an RSA key of 512 bits. */

let keyAlias = 'keyAlias';
let properties: Array<huks.HuksParam> = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_512
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_OAEP
  },
  {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }
];
let options: huks.HuksOptions = {
  properties: properties
};
huks.generateKey(keyAlias, options, (err, data) => {
});
```


<a id="generatekey-1"></a>

## generateKey

```TypeScript
function generateKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

Generates a key. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [generateKeyItem](arkts-universalkeystore-huks-generatekeyitem-f.md#generatekeyitem-1)(keyAlias: string, options: HuksOptions)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key. The value can contain up to 128 bytes and should not include sensitive data such as personal information. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Tags required for generating the key. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Promise that returns **HuksResult**. |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Generate a 256-bit ECC key. */

let keyAlias = 'keyAlias';
let properties: Array<huks.HuksParam> = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_ECC
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_ECC_KEY_SIZE_256
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
  },
  {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }
];
let options: huks.HuksOptions = {
  properties: properties
};
let result = huks.generateKey(keyAlias, options);
```
