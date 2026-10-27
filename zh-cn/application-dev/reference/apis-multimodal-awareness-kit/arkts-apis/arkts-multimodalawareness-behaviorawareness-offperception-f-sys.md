# offPerception（系统接口）

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## offPerception

```TypeScript
export function offPerception(
    callback?: Callback<PerceptionEvent<BehaviorAwarenessPayload>>
  ): Promise<void>
```

取消订阅。业务侧向 MSDP 注销订阅关系。

如果传入回调，则仅取消与该回调匹配的订阅；如果不传回调，则取消当前包名下的所有订阅。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-behaviorAwareness-export function offPerception(    callback?: Callback<PerceptionEvent<BehaviorAwarenessPayload>>  ): Promise<void>--><!--Device-behaviorAwareness-export function offPerception(    callback?: Callback<PerceptionEvent<BehaviorAwarenessPayload>>  ): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PerceptionEvent](arkts-multimodalawareness-behaviorawareness-perceptionevent-i-sys.md)&lt;[BehaviorAwarenessPayload](arkts-multimodalawareness-behaviorawareness-behaviorawarenesspayload-i-sys.md)&gt;&gt; | 否 | 用于返回感知事件的回调。用于清除所有订阅的感知事件。<br>默认值：不指定时，取消当前包的所有订阅。 |

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
| [32500003](../errorcode-deviceStatus.md#32500003-取消订阅失败) | Unsubscription failed. |
