# getAccessibilityExtensionListSync

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## getAccessibilityExtensionListSync

```TypeScript
function getAccessibilityExtensionListSync(
    abilityType: AbilityType,
    stateType: AbilityState
  ): Array<AccessibilityAbilityInfo>
```

Query the list of accessibility applications in the current system, which can be queried by criteria.

This API is the synchronous version of [accessibility.getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md) (asynchronous version). They have the same functionality. Use this API if you need to obtain the result immediately. Use the asynchronous version if you need to query in non-blocking scenarios.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abilityType | [AbilityType](arkts-accessibility-accessibility-abilitytype-t.md) | Yes | Accessibility application type. |
| stateType | [AbilityState](arkts-accessibility-accessibility-abilitystate-t.md) | Yes | Accessibility application status. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[AccessibilityAbilityInfo](arkts-accessibility-accessibility-accessibilityabilityinfo-i.md)&gt; | Promise used to return the accessibility application list. |

**Examples**

Query all installed accessibility applications.

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'all'; // The accessibility app type is all.
let abilityState: accessibility.AbilityState = 'install'; // The accessibility app state is installed.
let data: accessibility.AccessibilityAbilityInfo[];

try {
  data = accessibility.getAccessibilityExtensionListSync(abilityType, abilityState);
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
}

// For example, an accessibility app with the bundle name com.example.myaccessibilityapp is installed in the system.
// The log output is as follows:
// [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
// "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
// "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
// "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
// "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
// "announceForAccessibility","announceForAccessibilityNotInterrupt",
// "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
```

Query all enabled accessibility applications with voice feedback.

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken'; // The accessibility app type is spoken feedback.
let abilityState: accessibility.AbilityState = 'enable'; // The accessibility app state is enabled.
let data: accessibility.AccessibilityAbilityInfo[];

try {
  data = accessibility.getAccessibilityExtensionListSync(abilityType, abilityState);
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
}
```
