# getTotalBytes

## Modules to Import

```TypeScript
```

## getTotalBytes

```TypeScript
function getTotalBytes(path: string, callback: AsyncCallback<number>): void
```

Obtains the total size of the specified file system, in bytes. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getTotalBytes

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the file system. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the total size obtained, in bytes. |

**Examples**

```TypeScript
import common from '@ohos.app.ability.common';
import { BusinessError } from '@ohos.base';
let context = getContext(this) as common.UIAbilityContext;
let path = context.filesDir;
statfs.getTotalBytes(path, (err: BusinessError, totalBytes:Number) => {
    if (err) {
        console.error('getTotalBytes callback failed');
    } else {
        console.info('getTotalBytes callback success' + totalBytes);
    }
});
```


<a id="gettotalbytes-1"></a>

## getTotalBytes

```TypeScript
function getTotalBytes(path: string): Promise<number>
```

Obtains the total size of the specified file system, in byte. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getTotalBytes

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the file system. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the total size obtained, in bytes. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
let path = "/dev";
statfs.getTotalBytes(path).then((number: number) => {
  console.info("getTotalBytes promise successfully:" + number);
}).catch((err: BusinessError) => {
  console.error("getTotalBytes failed with error:" + JSON.stringify(err));
});
```
