# deleteKey

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## deleteKey

```TypeScript
function deleteKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

Deletes a key. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteKeyItem](arkts-universalkeystore-huks-deletekeyitem-f.md)(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key to delete. It must be the key alias passed in when the key was generated. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Options for deleting the key. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the obtained **HuksResult**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Set options to emptyOptions. */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.deleteKey(keyAlias, emptyOptions, (err, data) => {
});
```


<a id="deletekey-1"></a>

## deleteKey

```TypeScript
function deleteKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

Deletes a key. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteKeyItem](arkts-universalkeystore-huks-deletekeyitem-f.md#deletekeyitem-1)(keyAlias: string, options: HuksOptions)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key to delete. It must be the key alias passed in when the key was generated. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Options for deleting the key. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Promise that returns **HuksResult**. |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit"

/* Set options to emptyOptions. */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.deleteKey(keyAlias, emptyOptions).then((data) => {
  console.info('delete key success');
}).catch((err: BusinessError) => {
  console.error("Failed to delete the key. Error code: " + err.code + " Error message: " + err.message);
});
```
