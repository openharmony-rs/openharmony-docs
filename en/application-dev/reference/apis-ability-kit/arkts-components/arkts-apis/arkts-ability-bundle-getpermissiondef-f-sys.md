# getPermissionDef (System API)

## Modules to Import

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string, callback: AsyncCallback<PermissionDef>): void
```

Obtains the permission details by permission name. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permissionName | string | Yes | Name of the permission. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PermissionDef](arkts-ability-permissiondef-depr-i-sys.md)&gt; | Yes | Callback used to return the permission details. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';

let permission: string = "ohos.permission.GET_BUNDLE_INFO";
bundle.getPermissionDef(permission, (err, data) => {
  if (err) {
    console.error('getPermissionDef failed:' + err.message);
  } else {
    console.info('getPermissionDef successfully:' + JSON.stringify(data));
  }
});
```

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let permissionName: string = "ohos.permission.GET_BUNDLE_INFO";
bundle.getPermissionDef(permissionName).then((data) => {
  console.info('getPermissionDef successfully. Data: ' + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error('getPermissionDef failed. Cause: ' + error.message);
});
```


## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string): Promise<PermissionDef>
```

Obtains the permission details by permission name. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permissionName | string | Yes | Name of the permission. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PermissionDef](arkts-ability-permissiondef-depr-i-sys.md)&gt; | Promise used to return the permission details. |

**Examples**

See [getPermissionDef](#getpermissiondef)
