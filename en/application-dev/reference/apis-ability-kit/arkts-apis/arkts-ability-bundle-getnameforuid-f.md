# getNameForUid

## Modules to Import

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getNameForUid

```TypeScript
function getNameForUid(uid: number, callback: AsyncCallback<string>): void
```

Obtains bundle name by the given uid.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getBundleNameByUid](arkts-ability-bundlemanager-getbundlenamebyuid-f.md)

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Indicates the UID of an application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes |  |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';

let uid: number = 20010005;

bundle.getNameForUid(uid, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


<a id="getnameforuid-1"></a>

## getNameForUid

```TypeScript
function getNameForUid(uid: number): Promise<string>
```

Obtains the bundle name based on a UID. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | UID based on which the bundle name is to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the bundle name. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let uid: number = 20010005;

bundle.getNameForUid(uid)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```
