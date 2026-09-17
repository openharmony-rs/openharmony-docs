# TouchController

Provides the capability of simulating touch operations. The simulated touch operation sequence must meet the following requirements:

1. All touch points must share the same **displayId**.
2. Each touch point must begin with a **touchDown()** call, followed by zero or more **touchMove()** calls, and end
with an **touchUp()** call.

**Since:** 26.0.0

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## touchDown

```TypeScript
touchDown(touch: TouchPoint): Promise<void>
```

Presses down a touch point. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONTROL_DEVICE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| touch | [TouchPoint](arkts-input-inputeventclient-touchpoint-i.md) | Yes | Information about the touch point that is in contact with the display. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [4300001](../errorcode-inputeventclient.md#4300001-status-error) | Invalid input event sequence. Possible causes:<br> 1. The touch point is touching the display; 2. The touch point ID is not within the valid range [0,9]. |
| [4300002](../errorcode-inputeventclient.md#4300002-display-does-not-exist) | The display does not exist. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. |

**Examples**

```TypeScript
import { inputEventClient } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createTouchController()
            .then((touchController: inputEventClient.TouchController) => {
              const touchPoint: inputEventClient.TouchPoint = {
                id: 0,
                displayId: 0,
                displayX: 600,
                displayY: 1200
              };
              touchController.touchDown(touchPoint);
              return touchController;
            })
            .then((touchController: inputEventClient.TouchController) => {
              touchController.touchMove({
                id: 0,
                displayId: 0,
                displayX: 720,
                displayY: 1200
              });
              return touchController;
            })
            .then((touchController: inputEventClient.TouchController) => {
              touchController.touchUp({
                id: 0,
                displayId: 0,
                displayX: 720,
                displayY: 1200
              });
            })
            .then(() => {
              console.info('Succeeded in touch up');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to simulate touch. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}
```

## touchMove

```TypeScript
touchMove(touch: TouchPoint): Promise<void>
```

Moves a touch point. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONTROL_DEVICE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| touch | [TouchPoint](arkts-input-inputeventclient-touchpoint-i.md) | Yes | Information about the touch point to be moved. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [4300001](../errorcode-inputeventclient.md#4300001-status-error) | Invalid input event sequence. Possible causes:<br> 1. The touch point is not touching the display; 2. The touch point ID is not within the valid range [0,9]. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. |

**Examples**

```TypeScript
For details, see [touchDown](#touchdown).
```

## touchUp

```TypeScript
touchUp(touch: TouchPoint): Promise<void>
```

Releases a touch point. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONTROL_DEVICE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| touch | [TouchPoint](arkts-input-inputeventclient-touchpoint-i.md) | Yes | Information about the touch point to be released. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [4300001](../errorcode-inputeventclient.md#4300001-status-error) | Invalid input event sequence. Possible causes:<br> 1. The touch point is not touching the display; 2. The touch point ID is not within the valid range [0,9]. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. |

**Examples**

```TypeScript
For details, see [touchDown](#touchdown).
```
