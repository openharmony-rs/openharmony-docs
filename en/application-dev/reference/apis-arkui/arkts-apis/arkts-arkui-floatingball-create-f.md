# create

## Modules to Import

```TypeScript
import { floatingBall } from '@kit.ArkUI';
```

## create

```TypeScript
function create(config: FloatingBallConfiguration): Promise<FloatingBallController>
```

Creates a floating ball controller. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [FloatingBallConfiguration](arkts-arkui-floatingball-floatingballconfiguration-i.md) | Yes | Parameters for creating the floating ball controller. This parameter cannot be empty, and **context** that is used to construct this parameter cannot be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FloatingBallController](arkts-arkui-floatingball-floatingballcontroller-i.md)&gt; | Promise used to return the floating ball controller. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible causes:<br>1.The context parameter is null. <br>2.The FloatingBallConfiguration parameter is null. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible causes:<br>1.The application context or main window is invalid. <br>2.System internal error, such as null pointer or insufficient memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Declare the floating ball controller instance.
let floatingBallController: floatingBall.FloatingBallController | undefined = undefined;
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let ctx = this.getUIContext().getHostContext() as common.UIAbilityContext; 
// Configure the floating ball controller.
let config: floatingBall.FloatingBallConfiguration = {
  context: ctx,
};
try {
  // Create a floating ball controller.
  floatingBall.create(config).then((data: floatingBall.FloatingBallController) => {
    // Save the controller instance.
    floatingBallController = data;
    console.info(`Succeeded in creating floating ball controller. Data: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create floating ball controller. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to create floating ball controller. Cause:${e.code}, message:${e.message}`);
}
```
