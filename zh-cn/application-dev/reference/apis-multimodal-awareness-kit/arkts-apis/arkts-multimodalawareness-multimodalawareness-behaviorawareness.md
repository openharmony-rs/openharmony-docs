# @ohos.multimodalAwareness.behaviorAwareness(行为感知)

**行为感知**本模块提供MSDP设备状态感知能力，支持用户行为数据采集、序列模式聚类、感知事件判断。

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
| [offPerception](arkts-multimodalawareness-behaviorawareness-offperception-f-sys.md#offperception-1) | 取消订阅。业务侧向MSDP注销订阅关系。 |
| [onPerception](arkts-multimodalawareness-behaviorawareness-onperception-f-sys.md#onperception-1) | 发起订阅。业务侧向MSDP注册订阅关系，同时注册感知事件回调。 |
| [submitFeedback](arkts-multimodalawareness-behaviorawareness-submitfeedback-f-sys.md#submitfeedback-1) | 提交用户反馈。业务侧将用户对感知事件的反馈传递给MSDP。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionData](arkts-multimodalawareness-behaviorawareness-actiondata-i-sys.md) | 操作动作数据。 |
| [BehaviorAwarenessPayload](arkts-multimodalawareness-behaviorawareness-behaviorawarenesspayload-i-sys.md) | 行为感知负载。HABIT_AWARENESS领域的具体数据。 |
| [Coordinates](arkts-multimodalawareness-behaviorawareness-coordinates-i-sys.md) | 经纬度坐标。 |
| [EventData](arkts-multimodalawareness-behaviorawareness-eventdata-i-sys.md) | 事件数据。 |
| [FeedbackData](arkts-multimodalawareness-behaviorawareness-feedbackdata-i-sys.md) | 反馈数据。 |
| [LocationAttributes](arkts-multimodalawareness-behaviorawareness-locationattributes-i-sys.md) | 位置类场景属性。 |
| [PerceptionEvent](arkts-multimodalawareness-behaviorawareness-perceptionevent-i-sys.md) | 感知事件数据。MSDP融合感知聚类后生成的事件，推送给业务侧。 |
| [SubscribeInfo](arkts-multimodalawareness-behaviorawareness-subscribeinfo-i-sys.md) | 订阅选项。定义订阅的过滤条件。 |
| [SystemActionAttributes](arkts-multimodalawareness-behaviorawareness-systemactionattributes-i-sys.md) | 系统控制类场景属性。 |
| [SystemEventAttributes](arkts-multimodalawareness-behaviorawareness-systemeventattributes-i-sys.md) | 系统事件类场景属性。 |
| [TimeAttributes](arkts-multimodalawareness-behaviorawareness-timeattributes-i-sys.md) | 时间类场景属性。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionType](arkts-multimodalawareness-behaviorawareness-actiontype-e-sys.md) | 操作类型枚举。 |
| [AdjustmentDirection](arkts-multimodalawareness-behaviorawareness-adjustmentdirection-e-sys.md) | 调节方向枚举。 |
| [BluetoothDeviceType](arkts-multimodalawareness-behaviorawareness-bluetoothdevicetype-e-sys.md) | 蓝牙设备类型枚举。 |
| [EventType](arkts-multimodalawareness-behaviorawareness-eventtype-e-sys.md) | 事件类型枚举。 |
| [FeedbackType](arkts-multimodalawareness-behaviorawareness-feedbacktype-e-sys.md) | 反馈类型枚举。 |
| [LocationStatusType](arkts-multimodalawareness-behaviorawareness-locationstatustype-e-sys.md) | 位置状态类型。用于区分进入或退出地理围栏。 |
| [LocationType](arkts-multimodalawareness-behaviorawareness-locationtype-e-sys.md) | 位置类型枚举。 |
| [Operation](arkts-multimodalawareness-behaviorawareness-operation-e-sys.md) | 操作目标枚举。 |
| [PatternType](arkts-multimodalawareness-behaviorawareness-patterntype-e-sys.md) | 感知模式类型。 |
| [PerceptionDomain](arkts-multimodalawareness-behaviorawareness-perceptiondomain-e-sys.md) | 感知领域类型。用于区分不同的感知领域，每个领域有独立的有效载荷结构。 |
| [RecurrenceType](arkts-multimodalawareness-behaviorawareness-recurrencetype-e-sys.md) | 重复周期枚举。 |
| [SoundMode](arkts-multimodalawareness-behaviorawareness-soundmode-e-sys.md) | 声音模式枚举。 |
<!--DelEnd-->
