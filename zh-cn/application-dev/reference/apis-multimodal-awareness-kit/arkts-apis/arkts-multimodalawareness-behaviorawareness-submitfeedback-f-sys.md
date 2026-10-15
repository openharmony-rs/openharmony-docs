# submitFeedback（系统接口）

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## submitFeedback

```TypeScript
export function submitFeedback(feedback: FeedbackData): Promise<void>
```

提交用户反馈。业务侧将用户对感知事件的反馈传递给 MSDP。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-behaviorAwareness-export function submitFeedback(feedback: FeedbackData): Promise<void>--><!--Device-behaviorAwareness-export function submitFeedback(feedback: FeedbackData): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| feedback | [FeedbackData](arkts-multimodalawareness-behaviorawareness-feedbackdata-i-sys.md) | 是 | 反馈数据。如果为 undefined 或 null，抛出 401 错误。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异步返回，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | 权限校验失败。非系统应用使用系统接口；32500001 - 服务异常； |
