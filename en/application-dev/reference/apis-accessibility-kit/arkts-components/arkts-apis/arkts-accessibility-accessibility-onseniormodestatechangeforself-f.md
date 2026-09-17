# onSeniorModeStateChangeForSelf

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## onSeniorModeStateChangeForSelf

```TypeScript
function onSeniorModeStateChangeForSelf(callback: Callback<boolean>): void
```

Subscribes to the "senior mode" change event of the app itself. This API uses an asynchronous callback to return the result.

Unlike [accessibility.onSeniorModeStateChange](arkts-accessibility-accessibility-onseniormodestatechange-f.md), which listens for system-level senior mode state changes, this API only monitors the state of the app itself.

> **NOTE:** 
> 
> - The callback parameter for registering a listener must use a named function instead of an anonymous function.Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> 
> - After calling this method, ensure that [accessibility.offSeniorModeStateChangeForSelf](arkts-accessibility-accessibility-offseniormodestatechangeforself-f.md) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the app's own senior mode is enabled, and **false** indicates that the app's own senior mode is disabled. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChangeForSelf(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChangeForSelf(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```
