# sendControlEvent (System API)

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## sendControlEvent

```TypeScript
function sendControlEvent(event: ControlEvent): Promise<void>
```

If the target window is displayed on the screen, you can use this API to send screen control events based on the paragraph information obtained via [onScreen.getPageContent](arkts-multimodalawareness-onscreen-getpagecontent-f-sys.md).

**Since:** 20

**Required permissions:** ohos.permission.SIMULATE_USER_INPUT

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [ControlEvent](arkts-multimodalawareness-onscreen-controlevent-i-sys.md) | Yes | Onscreen control event. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to get page content forbidden by<br> permission: ohos.permission.SIMULATE_USER_INPUT. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission check failed. A non-system application uses the system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to limited<br> device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
| [34000005](../errorcode-onScreen.md#34000005-target-not-found) | The target is not found. |

**Examples**

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

let options: onScreen.ContentOptions = {
   contentUnderstand: true,
   textOnly: true
};
let event: onScreen.ControlEvent | undefined = undefined;
try {
   onScreen.getPageContent(options).then((pageContent: onScreen.PageContent) => {
      if (pageContent.paragraphs != undefined && pageContent.paragraphs.length > 0 &&
         pageContent.paragraphs[0].hookId != undefined) {
         event = {
            windowId: pageContent.windowId,
            sessionId: pageContent.sessionId,
            hookId: pageContent.paragraphs[0].hookId,
            eventType: onScreen.EventType.SCROLL_TO_HOOK
         };
      }
   }).catch((err: BusinessError) => {
      console.error("get page content failed, errCode = " + err.code);
   });
} catch (err) {
   console.error('invoke failed, errCode = ' + err.code);
}
if (event != undefined) {
   try {
      onScreen.sendControlEvent(event).catch((err: BusinessError) => {
         console.error("send control event failed, errCode =" + err.code);
      })
   } catch (err) {
      console.error('invoke failed, errCode = ' + err.code);
   }
}
```
