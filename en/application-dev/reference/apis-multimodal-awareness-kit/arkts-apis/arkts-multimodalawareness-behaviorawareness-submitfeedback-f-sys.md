# submitFeedback (System API)

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## submitFeedback

```TypeScript
export function submitFeedback(feedback: FeedbackData): Promise<void>
```

Submit user feedback. The service side sends the user feedback to the MSDP.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-behaviorAwareness-export function submitFeedback(feedback: FeedbackData): Promise<void>--><!--Device-behaviorAwareness-export function submitFeedback(feedback: FeedbackData): Promise<void>-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| feedback | [FeedbackData](arkts-multimodalawareness-behaviorawareness-feedbackdata-i-sys.md) | Yes | Feedback data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application uses the system API. |
| [32500001](../errorcode-deviceStatus.md#32500001-abnormal-service) | Service exception. |
