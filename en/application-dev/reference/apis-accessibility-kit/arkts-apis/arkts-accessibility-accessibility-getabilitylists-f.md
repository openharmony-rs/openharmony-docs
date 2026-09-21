# getAbilityLists

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## getAbilityLists

```TypeScript
function getAbilityLists(
    abilityType: AbilityType,
    stateType: AbilityState,
    callback: AsyncCallback<Array<AccessibilityAbilityInfo>>
  ): void
```

Obtains the accessibility application list. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md#getaccessibilityextensionlist-1)(abilityType: AbilityType, stateType: AbilityState, callback: AsyncCallback&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt;)

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abilityType | [AbilityType](arkts-accessibility-accessibility-abilitytype-t.md) | Yes | Accessibility application type. |
| stateType | [AbilityState](arkts-accessibility-accessibility-abilitystate-t.md) | Yes | Accessibility application status. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AccessibilityAbilityInfo](arkts-accessibility-accessibility-accessibilityabilityinfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the list of accessibility applications is obtained successfully, **err** is **undefined** and **data** is the list of accessibility application information; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState, (err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
});
```


<a id="getabilitylists-1"></a>

## getAbilityLists

```TypeScript
function getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise<Array<AccessibilityAbilityInfo>>
```

Obtains the accessibility application list. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md)(abilityType: AbilityType, stateType: AbilityState)

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abilityType | [AbilityType](arkts-accessibility-accessibility-abilitytype-t.md) | Yes | Accessibility application type. |
| stateType | [AbilityState](arkts-accessibility-accessibility-abilitystate-t.md) | Yes | Accessibility application status. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityAbilityInfo](arkts-accessibility-accessibility-accessibilityabilityinfo-i.md)&gt;&gt; | Promise used to return the accessibility application list. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
});
```
