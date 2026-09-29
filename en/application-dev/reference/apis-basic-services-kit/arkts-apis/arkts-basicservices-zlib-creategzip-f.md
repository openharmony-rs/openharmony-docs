# createGZip

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## createGZip

```TypeScript
function createGZip(): Promise<GZip>
```

Creates this **GZip** object. This API uses a promise to return the result.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-zlib-function createGZip(): Promise<GZip>--><!--Device-zlib-function createGZip(): Promise<GZip>-End-->

**System capability:** SystemCapability.BundleManager.Zlib

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[GZip](arkts-basicservices-zlib-gzip-i.md)&gt; | Promise used to return the **GZip** object created. |

**Examples**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

zlib.createGZip().then((data) => {
  console.info('createGZip success');
})
```
