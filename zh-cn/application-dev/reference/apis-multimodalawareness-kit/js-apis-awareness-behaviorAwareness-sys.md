# @ohos.multimodalAwareness.behaviorAwareness (行为感知)(系统接口)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @krzngon-->
<!--Designer: @kevin_lau-->
<!--Tester: @chenwan188-->
<!--Adviser: @hu-zhiqiong-->

本模块提供MSDP设备状态感知能力，支持用户行为数据采集、序列模式聚类、感知事件判断。

**起始版本：** 26.1.0

> **说明：**
>
> 本模块为系统接口。

## 导入模块

```ts
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## PerceptionDomain

表示感知领域类型。用于区分不同的感知领域，每个领域有独立的有效载荷结构。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| HABIT_AWARENESS | 'habitAwareness' | 习惯感知领域类型能力。用于识别用户日常使用习惯，如应用使用习惯、设备操作习惯等。|

## PatternType

表示感知模式类型。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| TIME_PATTERN | 'timePattern' | 时间模式：时间到动作组合。|
| LOCATION_PATTERN | 'locationPattern' | 位置模式：位置到动作组合。|
| EVENT_PATTERN | 'eventPattern' | 动作序列模式：动作到动作组合。|

## EventType

表示事件类型枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| DAILY_TIME | 'dailyTime' | 每天的时间点。|
| WEEKLY_TIME | 'weeklyTime' | 每周的时间点。|
| MONTHLY_TIME | 'monthlyTime' | 每月的时间点。|
| WORKDAY_TIME | 'workdayTime' | 法定工作日的时间点。|
| LOCATION | 'location' | 位置信息，包括位置、围栏进出状态。|
| APP_LAUNCH | 'appLaunch' | 打开应用。|
| APP_EXIT | 'appExit' | 退出应用。|
| APP_USAGE_SINGLE | 'appUsageSingle' | 单次使用应用。|
| APP_USAGE_DAILY | 'appUsageDaily' | 当日使用应用。|
| ALARM_DISMISS | 'alarmDismiss' | 关闭闹钟。|
| CHARGE_START | 'chargeStart' | 开始充电。|
| CHARGE_END | 'chargeEnd' | 结束充电。|
| CHARGE_FULL | 'chargeFull' | 充满电。|
| BATTERY_ABOVE | 'batteryAbove' | 电量高于指定值。|
| BATTERY_BELOW | 'batteryBelow' | 电量低于指定值。|
| BLUETOOTH_CONNECT | 'bluetoothConnect' | 连接蓝牙。|
| BLUETOOTH_DISCONNECT | 'bluetoothDisconnect' | 断开蓝牙。|
| PHONE_RING | 'phoneRing' | 本机来电。|

## ActionType

表示操作类型枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| APP_CLOSE | 'appClose' | 关闭应用。|
| APP_OPEN | 'appOpen' | 打开应用。|
| EYE_PROTECT_MODE | 'eyeProtectMode' | 护眼模式。|
| DARK_MODE | 'darkMode' | 深色模式。|
| PERSONAL_HOTSPOT | 'personalHotspot' | 个人热点。|
| MOBILE_DATA | 'mobileData' | 移动数据。|
| WIFI | 'wifi' | 无线网络。|
| AIRPLANE_MODE | 'airplaneMode' | 飞行模式。|
| BLUETOOTH | 'bluetooth' | 蓝牙。|
| NFC | 'nfc' | NFC。|
| ROTATION_LOCK | 'rotationLock' | 旋转锁定。|
| POWER_SAVING | 'powerSaving' | 省电模式。|
| SOUND_MODE | 'soundMode' | 声音模式。|
| SCREEN_BRIGHTNESS | 'screenBrightness' | 屏幕亮度。|
| VOLUME | 'volume' | 音量。|
| SHUTDOWN | 'shutdown' | 关机。|
| REBOOT | 'reboot' | 重启。|

## SoundMode

表示声音模式枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| VIBRATE | 'vibrate' | 振动模式。|
| SILENT | 'silent' | 静音模式。|
| RING | 'ring' | 响铃模式。|

## BluetoothDeviceType

表示蓝牙设备类型枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| DEFAULT | 0 | 默认/未分类设备。|
| CAR | 1 | 车载设备。|
| HEADSET | 2 | 耳机。|
| HEARING | 3 | 助听器。|
| GLASSES | 4 | 眼镜。|
| WATCH | 5 | 手表。|
| SPEAKER | 6 | 音箱。|
| OTHERS | 7 | 其他。|

## FeedbackType

表示反馈类型枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| ACCEPT | 0 | 接受事件。|
| IGNORE | 1 | 忽略事件。|
| REJECT | 2 | 拒绝事件。|
| EDIT | 3 | 编辑事件。|
| NOT_PUSHED | 4 | 未推送事件。|

## RecurrenceType

表示重复周期枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| DAILY | 'daily' | 每天。|
| WEEKLY | 'weekly' | 每周。|
| MONTHLY | 'monthly' | 每月。|
| WORKDAY | 'workday' | 法定工作日。|

## LocationType

表示位置类型枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| HOME | 'home' | 家。|
| COMPANY | 'company' | 公司。|
| CUSTOM | 'custom' | 自定义。|

## LocationStatusType

表示位置状态类型。用于区分进入或退出地理围栏。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| ENTER | 'enter' | 进入地理围栏。|
| EXIT | 'exit' | 退出地理围栏。|

## Operation

表示操作目标枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| ON | 'on' | 开启。|
| OFF | 'off' | 关闭。|
| TOGGLE | 'toggle' | 切换。|

## AdjustmentDirection

表示调节方向枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| UP | 'up' | 增大。|
| DOWN | 'down' | 减小。|

## TimeAttributes

时间类场景属性接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| kind | 'time' | 否 | 否 | 判别字段，固定为 'time'。 |
| timePoint | string | 否 | 否 | 时间点（HH:mm格式，如"08:30"）。 |
| recurrence | [RecurrenceType](#recurrencetype) | 否 | 否 | 重复周期。 |
| dayOfWeek | number | 否 | 是 | 星期几（适用于每周重复）。取值范围：[1,7]。取值应为[1,7]内的整数。默认值：空。 |
| dayOfMonth | number | 否 | 是 | 月中的第几天（适用于每月重复）。取值范围：[1,31]。取值应为[1,31]内的整数。默认值：空。 |

## Coordinates

经纬度坐标接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| latitude | number | 否 | 否 | 纬度。单位：degree。取值范围：[-90,90]。 |
| longitude | number | 否 | 否 | 经度。单位：degree。取值范围：[-180,180]。 |

## LocationAttributes

位置类场景属性接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| kind | 'location' | 否 | 否 | 判别字段，固定为 'location'。 |
| locationType | [LocationType](#locationtype) | 否 | 是 | 位置类型（预定义位置，可选）。默认值：空。 |
| locationName | string | 否 | 是 | 位置名称。默认值：空。 |
| coordinates | [Coordinates](#coordinates) | 否 | 否 | 经纬度坐标。纬度取值范围：[-90,90]；经度取值范围：[-180,180]。 |

## SystemEventAttributes

系统事件类场景属性接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| kind | 'systemEvent' | 否 | 否 | 判别字段，固定为 'systemEvent'。 |
| packageName | string | 否 | 是 | 应用包名（应用类事件）。默认值：空。 |
| appName | string | 否 | 是 | 应用名称。默认值：空。 |
| appId | string | 否 | 是 | 应用ID（应用类事件）。默认值：空。 |
| durationThreshold | number | 否 | 是 | 单次使用时长阈值。单位：min。取值限定为整数。默认值：空。 |
| dailyDurationThreshold | number | 否 | 是 | 日使用时长阈值（应用时长事件）。单位：min。取值应为[0,1440]内的整数。默认值：空。 |
| batteryThreshold | number | 否 | 是 | 电池阈值。单位：%。取值应为[0,100]内的整数。默认值：空。 |
| level | number | 否 | 是 | 电池百分比。单位：%。取值应为[0,100]内的整数。默认值：空。 |
| bluetoothDeviceType | [BluetoothDeviceType](#bluetoothdevicetype) | 否 | 是 | 蓝牙设备类型（蓝牙类事件）。默认值：空。 |
| bluetoothDeviceName | string | 否 | 是 | 蓝牙设备名称。默认值：空。 |

## SystemActionAttributes

系统控制类场景属性接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| kind | 'systemAction' | 否 | 否 | 判别字段，固定为 'systemAction'。 |
| operation | [Operation](#operation) | 否 | 否 | 操作目标（开/关/切换）。 |
| packageName | string | 否 | 是 | 应用包名。默认值：空。 |
| appName | string | 否 | 是 | 应用名称。默认值：空。 |
| adjustment | [AdjustmentDirection](#adjustmentdirection) | 否 | 是 | 调节方向（brightness/volume增量调节时用）。默认值：空。 |
| value | number | 否 | 是 | 绝对值表示亮度或音量的固定值。单位：%。取值应为[0,100]内的整数。默认值：空。 |
| soundMode | [SoundMode](#soundmode) | 否 | 是 | 声音模式。默认值：空。 |

## EventData

事件数据接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| eventId | string | 否 | 否 | 事件标识。 |
| eventType | [EventType](#eventtype) | 否 | 否 | 事件类型。 |
| name | string | 否 | 否 | 事件名称。 |
| timestamp | number | 否 | 否 | 发生时间戳。单位：ms。 |
| params | Record\<string, string \| number \| boolean\> | 否 | 是 | 附加参数。默认值：空。 |
| attributes | [TimeAttributes](#timeattributes) \| [LocationAttributes](#locationattributes) \| [SystemEventAttributes](#systemeventattributes) | 否 | 是 | 场景属性。默认值：空。 |

## ActionData

操作动作数据接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| actionId | string | 否 | 否 | 动作ID。取值为[onPerception](#behaviorawarenessonperception)回调入参中[PerceptionEvent](#perceptionevent)的perceptionEventId，调用[submitFeedback](#behaviorawarenesssubmitfeedback)时需传入该值。前缀为habitAwareness_。 |
| actionType | [ActionType](#actiontype) | 否 | 否 | 动作类型。 |
| name | string | 否 | 否 | 动作名称。 |
| params | Record\<string, string \| number \| boolean\> | 否 | 是 | 附加参数。默认值：空。 |
| attributes | [SystemActionAttributes](#systemactionattributes) | 否 | 是 | 场景属性。默认值：空。 |

## BehaviorAwarenessPayload

行为感知负载。HABIT_AWARENESS领域的具体数据。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| patternType | [PatternType](#patterntype) | 否 | 否 | 感知模式类型。 |
| triggerEvent | [EventData](#eventdata)[] | 否 | 否 | 触发事件。 |
| action | [ActionData](#actiondata)[] | 否 | 否 | 关联动作。 |

## PerceptionEvent

感知事件数据。MSDP融合感知聚类后生成的事件，推送给业务侧。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| perceptionEventId | string | 否 | 否 | 感知事件唯一标识。 |
| domain | [PerceptionDomain](#perceptiondomain) | 否 | 否 | 感知领域类型。 |
| confidence | number | 否 | 否 | 置信度，0表示无置信度，100表示置信度完全置信。单位：%。取值应为[0,100]内的整数。 |
| generateTime | number | 否 | 否 | 生成时间戳。单位：ms。 |
| payload | [BehaviorAwarenessPayload](#behaviorawarenesspayload) | 否 | 否 | 领域特定数据。 |

## SubscribeInfo

订阅选项。定义订阅的过滤条件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| domain | [PerceptionDomain](#perceptiondomain) | 否 | 否 | 感知领域类型（必填）。 |
| patternTypes | [PatternType](#patterntype)[] | 否 | 是 | 子类型过滤（可选，不填则订阅该领域下所有模式）。默认值：空。 |

## FeedbackData

反馈数据。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| perceptionEventId | string | 否 | 否 | 感知事件ID。 |
| feedbackType | [FeedbackType](#feedbacktype) | 否 | 否 | 反馈类型。 |
| feedbackTime | number | 否 | 否 | 反馈时间戳。单位：ms。 |

## behaviorAwareness.onPerception

onPerception(info: SubscribeInfo, callback: Callback\<PerceptionEvent\<BehaviorAwarenessPayload\>\>): Promise\<void\>

发起订阅。业务侧向MSDP注册订阅关系，同时注册感知事件回调。

当用户执行操作时，MSDP从感知事件表过滤匹配项并通过回调实时推送。同一订阅目标重复订阅时，后传入的回调覆盖之前的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| info | [SubscribeInfo](#subscribeinfo) | 是 | 订阅选项。 |
| callback | Callback\<[PerceptionEvent](#perceptionevent)\<[BehaviorAwarenessPayload](#behaviorawarenesspayload)\>\> | 是 | 用于返回感知事件的回调。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<void\> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[设备状态感知错误码](errorcode-deviceStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| 32500001 | Service exception. |

**示例：**

```ts
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'BehaviorAwareness';

const subscribeInfo: behaviorAwareness.SubscribeInfo = {
  domain: behaviorAwareness.PerceptionDomain.HABIT_AWARENESS
};

const callback = (event: behaviorAwareness.PerceptionEvent<behaviorAwareness.BehaviorAwarenessPayload>) => {
  hilog.info(DOMAIN, TAG, 'Receive perception event, id: %{public}s', event.perceptionEventId);
};

try {
  behaviorAwareness.onPerception(subscribeInfo, callback)
    .then(() => {
      hilog.info(DOMAIN, TAG, 'Subscribe perception succeed');
    })
    .catch((err: BusinessError) => {
      hilog.error(DOMAIN, TAG, 'Subscribe perception failed, error code: %{public}d, message: %{public}s', err.code, err.message);
    });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe perception failed, error code: %{public}d, message: %{public}s', e.code, e.message);
}
```

## behaviorAwareness.offPerception

offPerception(callback?: Callback\<PerceptionEvent\<BehaviorAwarenessPayload\>\>): Promise\<void\>

取消订阅。业务侧向MSDP注销订阅关系。

如果传入回调，则仅取消与该回调匹配的订阅；如果不传回调，则取消当前包名下的所有订阅。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| callback | Callback\<[PerceptionEvent](#perceptionevent)\<[BehaviorAwarenessPayload](#behaviorawarenesspayload)\>\> | 否 | 用于返回感知事件的回调。用于清除所有订阅的感知事件。默认值：不传则取消当前包名下的所有订阅。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<void\> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[设备状态感知错误码](errorcode-deviceStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| 32500001 | Service exception. |
| 32500003 | Unsubscription failed. |

**示例：**

```ts
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'BehaviorAwareness';

const callback = (event: behaviorAwareness.PerceptionEvent<behaviorAwareness.BehaviorAwarenessPayload>) => {
  hilog.info(DOMAIN, TAG, 'Receive perception event');
};

const subscribeInfo: behaviorAwareness.SubscribeInfo = {
  domain: behaviorAwareness.PerceptionDomain.HABIT_AWARENESS
};

try {
  await behaviorAwareness.onPerception(subscribeInfo, callback);
  hilog.info(DOMAIN, TAG, 'Subscribe perception succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe perception failed, error code: %{public}d, message: %{public}s', e.code, e.message);
}

try {
  behaviorAwareness.offPerception(callback)
    .then(() => {
      hilog.info(DOMAIN, TAG, 'Unsubscribe perception succeed');
    })
    .catch((err: BusinessError) => {
      hilog.error(DOMAIN, TAG, 'Unsubscribe perception failed, error code: %{public}d, message: %{public}s', err.code, err.message);
    });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe perception failed, error code: %{public}d, message: %{public}s', e.code, e.message);
}
```

## behaviorAwareness.submitFeedback

submitFeedback(feedback: FeedbackData): Promise\<void\>

提交用户反馈。业务侧将用户对感知事件的反馈传递给MSDP。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| feedback | [FeedbackData](#feedbackdata) | 是 | 反馈数据。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<void\> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[设备状态感知错误码](errorcode-deviceStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| 32500001 | Service exception. |

**示例：**

```ts
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'BehaviorAwareness';

const feedbackData: behaviorAwareness.FeedbackData = {
  perceptionEventId: 'habitAwareness_1',
  feedbackType: behaviorAwareness.FeedbackType.ACCEPT,
  feedbackTime: Date.now()
};

try {
  behaviorAwareness.submitFeedback(feedbackData)
    .then(() => {
      hilog.info(DOMAIN, TAG, 'Submit feedback succeed');
    })
    .catch((err: BusinessError) => {
      hilog.error(DOMAIN, TAG, 'Submit feedback failed, error code: %{public}d, message: %{public}s', err.code, err.message);
    });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Submit feedback failed, error code: %{public}d, message: %{public}s', e.code, e.message);
}
```
