# getShortcutInfos (System API)

## Modules to Import

```TypeScript
import { innerBundleManager, BundleStatusCallback } from '@kit.AbilityKit';
```

## getShortcutInfos

```TypeScript
function getShortcutInfos(bundleName: string, callback: AsyncCallback<Array<ShortcutInfo>>): void
```

Obtains an array of the shortcut information based on a given bundle name. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use
> [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md)(bundleName :string, callback: AsyncCallback&lt;Array&lt;ShortcutInfo&gt;&gt;)

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ShortcutInfo](arkts-ability-shortcutinfo-shortcutinfo-depr-i.md)&gt;&gt; | Yes | Callback used to return an array of the shortcut information. |


## getShortcutInfos

```TypeScript
function getShortcutInfos(bundleName: string): Promise<Array<ShortcutInfo>>
```

Obtains an array of the shortcut information based on a given bundle name. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use
> [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md)(bundleName :string, callback: AsyncCallback&lt;Array&lt;ShortcutInfo&gt;&gt;)

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ShortcutInfo](arkts-ability-shortcutinfo-shortcutinfo-depr-i.md)&gt;&gt; | Promise used to return an array of the shortcut information. |
