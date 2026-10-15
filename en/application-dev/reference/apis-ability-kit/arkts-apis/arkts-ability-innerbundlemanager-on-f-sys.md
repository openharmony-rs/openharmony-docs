# on (System API)

## Modules to Import

```TypeScript
import { innerBundleManager, BundleStatusCallback } from '@kit.AbilityKit';
```

## on('BundleStatusChange')

```TypeScript
function on(type: 'BundleStatusChange',
    bundleStatusCallback: BundleStatusCallback, callback: AsyncCallback<string>): void
```

Registers a callback to receive bundle status changes. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use
> [on](arkts-ability-bundlemonitor-on-f-sys.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-ability-bundlemonitor-on-f-sys.md)

**Required permissions:** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-innerBundleManager-function on(type: 'BundleStatusChange',    bundleStatusCallback: BundleStatusCallback, callback: AsyncCallback<string>): void--><!--Device-innerBundleManager-function on(type: 'BundleStatusChange',    bundleStatusCallback: BundleStatusCallback, callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BundleStatusChange' | Yes | Event type. Only **BundleStatusChange** is supported. |
| bundleStatusCallback | [BundleStatusCallback](arkts-ability-bundlestatuscallback-t-sys.md) | Yes | Callback to register. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return a successful result or error Callback to register. |


## on('BundleStatusChange')

```TypeScript
function on(type: 'BundleStatusChange', bundleStatusCallback: BundleStatusCallback): Promise<string>
```

Registers a callback to receive bundle status changes. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use
> [on](arkts-ability-bundlemonitor-on-f-sys.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-ability-bundlemonitor-on-f-sys.md)

**Required permissions:** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-innerBundleManager-function on(type: 'BundleStatusChange', bundleStatusCallback: BundleStatusCallback): Promise<string>--><!--Device-innerBundleManager-function on(type: 'BundleStatusChange', bundleStatusCallback: BundleStatusCallback): Promise<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BundleStatusChange' | Yes | Event type. Only **BundleStatusChange** is supported. |
| bundleStatusCallback | [BundleStatusCallback](arkts-ability-bundlestatuscallback-t-sys.md) | Yes | Callback to register. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return a successful result or error information. |
