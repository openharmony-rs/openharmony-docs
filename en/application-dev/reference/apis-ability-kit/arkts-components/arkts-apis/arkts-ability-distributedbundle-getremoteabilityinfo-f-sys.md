# getRemoteAbilityInfo (System API)

## Modules to Import

```TypeScript
import { distributedBundle } from '@kit.AbilityKit';
```

## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, callback: AsyncCallback<RemoteAbilityInfo>): void
```

Obtains the information about the remote ability that matches the given element name. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-elementname-depr-i.md) | Yes | **ElementName**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RemoteAbilityInfo](arkts-ability-remoteabilityinfo-remoteabilityinfo-depr-i-sys.md)&gt; | Yes | Callback used to return the remote ability information. |


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName): Promise<RemoteAbilityInfo>
```

Obtains the information about the remote ability that matches the given element name. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-elementname-depr-i.md) | Yes | **ElementName**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RemoteAbilityInfo](arkts-ability-remoteabilityinfo-remoteabilityinfo-depr-i-sys.md)&gt; | Promise used to return the remote ability information. |
