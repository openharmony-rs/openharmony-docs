# unbind

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## unbind

```TypeScript
function unbind(floatViewController: FloatViewController,
    floatingBallController: floatingBall.FloatingBallController): Promise<void>
```

Unbinds the float view and floating ball. The unbinding can be performed only after both the [float view controller](arkts-arkui-floatview-floatviewcontroller-i.md) and [floating ball controller](arkts-arkui-floatingball-floatingballcontroller-i.md) are stopped. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| floatViewController | [FloatViewController](arkts-arkui-floatview-floatviewcontroller-i.md) | Yes | Float view controller. |
| floatingBallController | [floatingBall.FloatingBallController](arkts-arkui-floatingball-floatingballcontroller-i.md) | Yes | Floating ball controller. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported on this device. Possible cause: Call api on unsupported device. |
| [1300025](../errorcode-window.md#1300025-unsupported-operation-in-the-current-floating-ball-state) | The floating ball state does not support this operation. Possible cause: 1. The floating ball has started but not stopped yet. 2. The floatingBallController has not been bound. |
| [1300031](../errorcode-window.md#1300031-operation-not-supported-in-the-current-float-view-state) | The floatView state does not support this operation. Possible cause: 1. The float view has started but not stopped yet. 2. The floatViewController has not been bound. 3. The floatViewController and the floatingBallController are not bound together. |

**Examples**

```TypeScript
// Entry.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { floatingBall, floatView } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private floatingBallController: floatingBall.FloatingBallController | undefined = undefined;
  private floatViewController: floatView.FloatViewController | undefined = undefined;
  // Create a controller.
  // ...
  public unbindController(): void {
    try {
      // Use the float view controller and floating ball controller passed during the binding.
      if (this.floatViewController && this.floatingBallController) {
        // Unbind the float view and the floating ball.
        floatView.unbind(this.floatViewController!, this.floatingBallController!).then(() => {
          console.info('Succeeded in unbinding float view and floating ball.');
        }).catch((err: BusinessError): void => {
          console.error(`Failed to unbind float view and floating ball. Cause:${err.code}, message:${err.message}`);
        });
      }
    } catch (e) {
      console.error(`Failed to unbind float view and floating ball. Cause:${e.code}, message:${e.message}`);
    }
  }
}
```
