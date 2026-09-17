# setSeniorModeStateForSelf

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## setSeniorModeStateForSelf

```TypeScript
function setSeniorModeStateForSelf(state: boolean): Promise<void>
```

Sets whether the app has "senior mode" enabled. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | boolean | Yes | Whether to enable "senior mode" for the app. The value **true** indicates that "senior mode" is enabled, and **false** indicates that "senior mode" is disabled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9300000](../errorcode-accessibility.md#9300000-accessibility-system-service-abnormal) | System abnormality. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.setSeniorModeStateForSelf(true).then(() => {
      console.info(`Succeeded in setting seniorModeStateForSelf`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to call setSeniorModeStateForSelf. Code:${err.code}, message:${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```
