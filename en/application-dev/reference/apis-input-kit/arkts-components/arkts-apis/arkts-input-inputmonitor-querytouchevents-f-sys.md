# queryTouchEvents (System API)

## Modules to Import

```TypeScript
import { inputMonitor } from '@kit.InputKit';
```

## queryTouchEvents

```TypeScript
function queryTouchEvents(count: number) : Promise<Array<TouchEvent>>
```

Queries recent touchscreen input events. A maximum of 100 events can be queried. Since API version 26.0.0, a maximum of 60 events can be queried. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.INPUT_MONITORING

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of touchscreen input events to query. The value range is an integer from 0 to 100. If the value is less than 0, the value **0** is used. If the value is greater than 100, the value **100** is used. Since API version 26.0.0, if the value is greater than 60, the value **60** is used. If there are only 30 actual touchscreen input events but this parameter is set to **50**, only 30 touchscreen input events can be queried. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[TouchEvent](arkts-input-multimodalinput-touchevent-touchevent-i.md)&gt;&gt; | Promise used to return the queried touchscreen input events. It contains the following valid information; all other information is invalid:<br>- **actionTime**: Time when the touchscreen input event occurred, in microseconds (μs) since system startup.<br>- [SourceType](arkts-input-multimodalinput-touchevent-sourcetype-e.md): Device type of the touch source.<br>- [isInject](arkts-input-multimodalinput-touchevent-touchevent-i.md): Whether the touchscreen input event is an injected event.<br>- **pressure**: Pressure value, with a value range of [0.0, 1.0], where **0.0** indicates not supported.<br>- **tiltX**: Angle relative to the YZ plane, with a value range of [-90, 90], where a positive value indicates tilting to the right.<br>- **tiltY**: Angle relative to the XZ plane, with a value range of [-90, 90], where a positive value indicates tilting downward.<br>Since API version 23, the following additional valid information can be obtained:<br>- [Action](arkts-input-multimodalinput-touchevent-action-e.md): Touchscreen input event type.<br>- **screenX**: X-axis coordinate relative to the upper left corner of the screen, in pixels, with a value range of [0, screen width], increasing to the right. It is available only for specified applications.<br>- **screenY**: Y-axis coordinate relative to the upper left corner of the screen, in pixels, with a value range of [0, screen height], increasing downward. It is available only for specified applications.<br>Since API version 26.0.0, a maximum of 60 events can be queried, and events of the MOVE and PULL_MOVE types will not be returned. **screenX** and **screenY** are no longer restricted to specified applications and can be obtained by all system applications. Additionally, the following valid information can be obtained:<br>- **screenId**: Target screen ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |

**Examples**

```TypeScript
import { inputMonitor, TouchEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Querying the Number of Touchscreen Events
  inputMonitor.queryTouchEvents(10).then((events: Array<TouchEvent>) => {
    events.forEach((event, index) => {
      console.info(`Succeeded in querying touch event ${index}, actionTime=${event.actionTime}, sourceType=${event.sourceType}.`);
    });
  }).catch((error: BusinessError) => {
    console.error(`Failed to query touch events promise, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
  });
} catch (error) {
  const code = (error as BusinessError).code;
  const message = (error as BusinessError).message;
  console.error(`Failed to query touch events, Code: ${code}, message: ${message}.`);
}
```
