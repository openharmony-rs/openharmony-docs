# onAnimationReduceStateChange

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## onAnimationReduceStateChange

```TypeScript
function onAnimationReduceStateChange(callback: Callback<boolean>): void
```

Subscribes to the state changes of animation reduction mode. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - The callback parameter for registering a listener must use a named function instead of an anonymous function.Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> 
> - After calling this method, ensure that [accessibility.offAnimationReduceStateChange](arkts-accessibility-accessibility-offanimationreducestatechange-f.md) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback invoked when the reduced motion mode status changes. The value **true** indicates that the reduced motion mode is enabled, and **false** indicates that the reduced motion mode is disabled. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe animationReduce state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAnimationReduceStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAnimationReduceStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```
