# getRemoteAbilityInfos (System API)

## Modules to Import

```TypeScript
import { distributedBundle } from '@kit.AbilityKit';
```

## getRemoteAbilityInfos

```TypeScript
function getRemoteAbilityInfos(elementNames: Array<ElementName>,
    callback: AsyncCallback<Array<RemoteAbilityInfo>>): void
```

Obtains the information about remote abilities that match the given element names. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementNames | Array&lt;[ElementName](arkts-ability-elementname-elementname-depr-i.md)&gt; | Yes | **ElementName** array, whose maximum length is 10. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[RemoteAbilityInfo](arkts-ability-remoteabilityinfo-remoteabilityinfo-depr-i-sys.md)&gt;&gt; | Yes | Callback used to return an array of the remote ability information. |


## getRemoteAbilityInfos

```TypeScript
function getRemoteAbilityInfos(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>
```

Obtains the information about remote abilities that match the given element names. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementNames | Array&lt;[ElementName](arkts-ability-elementname-elementname-depr-i.md)&gt; | Yes | **ElementName** array, whose maximum length is 10. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[RemoteAbilityInfo](arkts-ability-remoteabilityinfo-remoteabilityinfo-depr-i-sys.md)&gt;&gt; | Promise used to return an array of the remote ability information. |
