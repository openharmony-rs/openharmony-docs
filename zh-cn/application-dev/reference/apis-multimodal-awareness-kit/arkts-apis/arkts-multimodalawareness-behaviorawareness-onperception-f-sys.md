# onPerception（系统接口）

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## onPerception

```TypeScript
export function onPerception(
    info: SubscribeInfo,
    callback: Callback<PerceptionEvent<BehaviorAwarenessPayload>>
  ): Promise<void>
```

发起订阅。业务侧向 MSDP 注册订阅关系，同时注册感知事件回调。

当用户执行动作时，MSDP 从感知事件表过滤匹配项并通过回调实时推送。同一订阅目标重复订阅时，后传入的回调覆盖之前的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-behaviorAwareness-export function onPerception(    info: SubscribeInfo,    callback: Callback<PerceptionEvent<BehaviorAwarenessPayload>>  ): Promise<void>--><!--Device-behaviorAwareness-export function onPerception(    info: SubscribeInfo,    callback: Callback<PerceptionEvent<BehaviorAwarenessPayload>>  ): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [SubscribeInfo](arkts-multimodalawareness-behaviorawareness-subscribeinfo-i-sys.md) | 是 | 订阅选项。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PerceptionEvent](arkts-multimodalawareness-behaviorawareness-perceptionevent-i-sys.md)&lt;[BehaviorAwarenessPayload](arkts-multimodalawareness-behaviorawareness-behaviorawarenesspayload-i-sys.md)&gt;&gt; | 是 | 用于返回感知事件的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回值的 Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application uses the system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [32500001](../errorcode-deviceStatus.md#32500001-服务异常) | Service exception. |
