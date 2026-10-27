# @ohos.multimodalAwareness.behaviorAwareness(行为感知)

**behaviorAwareness** 本模块提供 MSDP 设备状态感知能力，支持用户行为数据采集、序列模式聚类、感知事件判断。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace behaviorAwareness--><!--Device-unnamed-declare namespace behaviorAwareness-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offPerception](arkts-multimodalawareness-behaviorawareness-offperception-f-sys.md#offperception-1) | 取消订阅。业务侧向 MSDP 注销订阅关系。 |
| [onPerception](arkts-multimodalawareness-behaviorawareness-onperception-f-sys.md#onperception-1) | 发起订阅。业务侧向 MSDP 注册订阅关系，同时注册感知事件回调。 |
| [submitFeedback](arkts-multimodalawareness-behaviorawareness-submitfeedback-f-sys.md#submitfeedback-1) | 提交用户反馈。业务侧将用户反馈发送给 MSDP。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionData](arkts-multimodalawareness-behaviorawareness-actiondata-i-sys.md) | 操作动作数据。 |
| [BehaviorAwarenessPayload](arkts-multimodalawareness-behaviorawareness-behaviorawarenesspayload-i-sys.md) | 习惯感知领域 payload。HABIT_AWARENESS 领域的具体数据。 |
| [Coordinates](arkts-multimodalawareness-behaviorawareness-coordinates-i-sys.md) | 地理坐标。 |
| [EventData](arkts-multimodalawareness-behaviorawareness-eventdata-i-sys.md) | 事件数据。 |
| [FeedbackData](arkts-multimodalawareness-behaviorawareness-feedbackdata-i-sys.md) | 反馈数据。 |
| [LocationAttributes](arkts-multimodalawareness-behaviorawareness-locationattributes-i-sys.md) | 位置类场景属性。 |
| [PerceptionEvent](arkts-multimodalawareness-behaviorawareness-perceptionevent-i-sys.md) | 感知事件数据。MSDP 融合感知聚类后生成的事件，推送给业务侧。 |
| [SubscribeInfo](arkts-multimodalawareness-behaviorawareness-subscribeinfo-i-sys.md) | 订阅选项。定义订阅的过滤条件。 |
| [SystemActionAttributes](arkts-multimodalawareness-behaviorawareness-systemactionattributes-i-sys.md) | 系统控制类场景属性。 |
| [SystemEventAttributes](arkts-multimodalawareness-behaviorawareness-systemeventattributes-i-sys.md) | 系统事件类场景属性。 |
| [TimeAttributes](arkts-multimodalawareness-behaviorawareness-timeattributes-i-sys.md) | 时间类场景属性。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionType](arkts-multimodalawareness-behaviorawareness-actiontype-e-sys.md) | 动作类型枚举。 |
| [AdjustmentDirection](arkts-multimodalawareness-behaviorawareness-adjustmentdirection-e-sys.md) | 调节方向枚举。 |
| [BluetoothDeviceType](arkts-multimodalawareness-behaviorawareness-bluetoothdevicetype-e-sys.md) | 蓝牙设备类型枚举。 |
| [EventType](arkts-multimodalawareness-behaviorawareness-eventtype-e-sys.md) | 事件类型枚举。 |
| [FeedbackType](arkts-multimodalawareness-behaviorawareness-feedbacktype-e-sys.md) | 事件推送后用户反馈事件状态类型枚举。 |
| [LocationStatusType](arkts-multimodalawareness-behaviorawareness-locationstatustype-e-sys.md) | 位置状态类型枚举。用于区分进入或离开地理围栏。 |
| [LocationType](arkts-multimodalawareness-behaviorawareness-locationtype-e-sys.md) | 位置类型枚举。 |
| [Operation](arkts-multimodalawareness-behaviorawareness-operation-e-sys.md) | 操作目标枚举。 |
| [PatternType](arkts-multimodalawareness-behaviorawareness-patterntype-e-sys.md) | 感知模式类型。 |
| [PerceptionDomain](arkts-multimodalawareness-behaviorawareness-perceptiondomain-e-sys.md) | 感知领域类型。用于区分不同的感知领域，每个领域有独立的 payload 结构。 |
| [RecurrenceType](arkts-multimodalawareness-behaviorawareness-recurrencetype-e-sys.md) | 重复周期枚举。 |
| [SoundMode](arkts-multimodalawareness-behaviorawareness-soundmode-e-sys.md) | 声音模式枚举。 |
<!--DelEnd-->
