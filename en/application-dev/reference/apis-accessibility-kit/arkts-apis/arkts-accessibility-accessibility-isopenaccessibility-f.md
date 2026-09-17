# isOpenAccessibility

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## isOpenAccessibility

```TypeScript
function isOpenAccessibility(callback: AsyncCallback<boolean>): void
```

Checks whether an accessibility application is enabled. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [isOpenAccessibilitySync](arkts-accessibility-accessibility-isopenaccessibilitysync-f.md)

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates the accessibility app is enabled, and **false** indicates the accessibility app is not enabled. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility().then((data: boolean) => {
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to isOpenAccessibility. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`Failed to isOpenAccessibility. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`);
});
```


## isOpenAccessibility

```TypeScript
function isOpenAccessibility(): Promise<boolean>
```

Checks whether an accessibility application is enabled. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [isOpenAccessibilitySync](arkts-accessibility-accessibility-isopenaccessibilitysync-f.md)

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates the accessibility app is enabled, and **false** indicates the accessibility app is disabled. |

**Examples**

See [isOpenAccessibility](#isopenaccessibility)
