# exportKey

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## exportKey

```TypeScript
function exportKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

Exports a key. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [exportKeyItem](arkts-universalkeystore-huks-exportkeyitem-f.md)(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;HuksReturnResult&gt;)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Key alias, which must be the same as the alias used when the key was generated. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Empty object (leave this parameter empty). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the obtained **HuksResult**. Otherwise, **err** is an error object. **outData** of **HuksResult** returns the public key exported. |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Set options to emptyOptions. */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.exportKey(keyAlias, emptyOptions, (err, data) => {
});
```

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Set options to emptyOptions. */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.exportKey(keyAlias, emptyOptions);
```


## exportKey

```TypeScript
function exportKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

Exports a key. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [exportKeyItem](arkts-universalkeystore-huks-exportkeyitem-f.md)(keyAlias: string, options: HuksOptions)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Key alias, which must be the same as the alias used when the key was generated. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Empty object (leave this parameter empty). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Promise that returns **HuksResult**. **outData** of **HuksResult** returns the public key exported from HUKS. |

**Examples**

See [exportKey](#exportkey)
