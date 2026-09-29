# createChecksum

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## createChecksum

```TypeScript
function createChecksum(): Promise<Checksum>
```

Creates this checksum object. This API uses a promise to return the result.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-zlib-function createChecksum(): Promise<Checksum>--><!--Device-zlib-function createChecksum(): Promise<Checksum>-End-->

**System capability:** SystemCapability.BundleManager.Zlib

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Checksum](arkts-basicservices-zlib-checksum-i.md)&gt; | Promise used to return the created checksum object. |

**Examples**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

zlib.createChecksum().then((data) => {
  console.info('createChecksum success');
})
```
