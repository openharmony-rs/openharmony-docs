# bind

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## bind

```TypeScript
function bind(floatViewController: FloatViewController, floatingBallController: floatingBall.FloatingBallController,
    floatingBallParams: floatingBall.FloatingBallParams): Promise<void>
```

Binds the float view and floating ball. You need to create the [float view controller](arkts-arkui-floatview-floatviewcontroller-i.md) and [floating ball controller](arkts-arkui-floatingball-floatingballcontroller-i.md) first, and neither of them has been started. This API uses a promise to return the result.

> **NOTE:** 
> 
> - After the binding is successful, calling [start()](arkts-arkui-floatview-floatviewcontroller-i.md#start) or [startFloatingBall()](arkts-arkui-floatingball-floatingballcontroller-i.md#startfloatingball) will create both a float view and the floating ball window, and trigger the status callback registered for the corresponding window. However, only one window is displayed at a time, and the display sequence depends on which controller's start API is called first.
> 
> - After the binding is successful, users can switch between the float view and the floating ball window by clicking.
> 
> - After the binding is successful, calling the stop API ([stop()](arkts-arkui-floatview-floatviewcontroller-i.md#stop) or [stopFloatingBall()](arkts-arkui-floatingball-floatingballcontroller-i.md#stopfloatingball)) of either controller will destroy both the float view and the floating ball window, and trigger the status callback registered for the corresponding window.

**Since:** 26.0.0

**Required permissions:** ohos.permission.USE_FLOAT_BALL and ohos.permission.FLOAT_VIEW

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| floatViewController | [FloatViewController](arkts-arkui-floatview-floatviewcontroller-i.md) | Yes | Float view controller. |
| floatingBallController | [floatingBall.FloatingBallController](arkts-arkui-floatingball-floatingballcontroller-i.md) | Yes | Floating ball controller. |
| floatingBallParams | [floatingBall.FloatingBallParams](arkts-arkui-floatingball-floatingballparams-i.md) | Yes | Floating ball parameters. The parameters set during binding will overwrite the parameters saved when the floating ball controller is started. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. Possible cause: The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported on this device. Possible cause: Call api on unsupported device. |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible cause: Invalid floating ball params. |
| [1300025](../errorcode-window.md#1300025-unsupported-operation-in-the-current-floating-ball-state) | The floating ball state does not support this operation. Possible cause: 1. The floating ball has started but not stopped yet. 2. The floating ball controller has been bound. |
| [1300031](../errorcode-window.md#1300031-operation-not-supported-in-the-current-float-view-state) | The floatView state does not support this operation. Possible cause: 1. The float view has started but not stopped yet. 2. The float view controller has been bound. |

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
  public bindController(): void {
    let floatingBallParams: floatingBall.FloatingBallParams = {
      template: floatingBall.FloatingBallTemplate.EMPHATIC,
      title: 'title',
      content: 'content'
    };

    try {
      if (this.floatViewController && this.floatingBallController) {
        // Bind the float view and the floating ball.
        floatView.bind(this.floatViewController!, this.floatingBallController!, floatingBallParams).then(() => {
          console.info('Succeeded in binding float view and floating ball.');
        }).catch((err: BusinessError): void => {
          console.error(`Failed to bind float view and floating ball. Cause:${err.code}, message:${err.message}`);
        });
      }
    } catch (e) {
      console.error(`Failed to bind float view and floating ball. Cause:${e.code}, message:${e.message}`);
    }
  }
}
```
