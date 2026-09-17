# isOpenTouchGuide

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## isOpenTouchGuide

```TypeScript
function isOpenTouchGuide(callback: AsyncCallback<boolean>): void
```

Checks whether touch guide mode is enabled. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [isOpenTouchGuideSync](arkts-accessibility-accessibility-isopentouchguidesync-f.md)

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the touch browsing mode is enabled, and **false** indicates the opposite. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide().then((data: boolean) => {
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to isOpenTouchGuide. Code:${err.code}, message:${err.message}`);
});
```

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`Failed to isOpenTouchGuide. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
});
```


## isOpenTouchGuide

```TypeScript
function isOpenTouchGuide(): Promise<boolean>
```

Checks whether touch guide mode is enabled. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [isOpenTouchGuideSync](arkts-accessibility-accessibility-isopentouchguidesync-f.md)

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the touch browsing mode is enabled, and **false** indicates that the touch browsing mode is not enabled. |

**Examples**

See [isOpenTouchGuide](#isopentouchguide)
