# isKeyExist

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## isKeyExist

```TypeScript
function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void
```

Checks whether a key exists. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isKeyItemExist](arkts-universalkeystore-huks-iskeyitemexist-f.md)(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;boolean&gt;)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key to check. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Options for checking the key. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the key exists; the value **false** means the opposite. |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Set options to emptyOptions. */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.isKeyExist(keyAlias, emptyOptions, (err, data) => {
});
```

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Set options to emptyOptions. */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.isKeyExist(keyAlias, emptyOptions);
```


## isKeyExist

```TypeScript
function isKeyExist(keyAlias: string, options: HuksOptions): Promise<boolean>
```

Checks whether a key exists. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isKeyItemExist](arkts-universalkeystore-huks-iskeyitemexist-f.md)(keyAlias: string, options: HuksOptions)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key to check. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Options for checking the key. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the key exists; the value **false** means the opposite. |

**Examples**

See [isKeyExist](#iskeyexist)
