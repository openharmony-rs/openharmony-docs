# getFreeBytes

## Modules to Import

```TypeScript
```

## getFreeBytes

```TypeScript
function getFreeBytes(path: string, callback: AsyncCallback<number>): void
```

Obtains the free size of the specified file system, in bytes. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getFreeBytes

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the file system. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the free size obtained, in bytes. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
let path = "/dev";
statfs.getFreeBytes(path).then((number: number) => {
  console.info("getFreeBytes promise successfully:" + number);
}).catch((err: BusinessError) => {
  console.error("getFreeBytes failed with error:" + JSON.stringify(err));
});
```

```TypeScript
import common from '@ohos.app.ability.common';
import { BusinessError } from '@ohos.base';
let context = getContext(this) as common.UIAbilityContext;
let path = context.filesDir;
statfs.getFreeBytes(path, (err: BusinessError, freeBytes:Number) => {
    if (err) {
        console.error('getFreeBytes callback failed');
    } else {
        console.info('getFreeBytes callback success' + freeBytes);
    }
});
```


## getFreeBytes

```TypeScript
function getFreeBytes(path: string): Promise<number>
```

Obtains the free size of the specified file system, in bytes. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getFreeBytes

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the file system. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the free size obtained, in bytes. |

**Examples**

See [getFreeBytes](#getfreebytes)
