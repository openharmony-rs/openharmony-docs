# @ohos.stationary

设备状态感知框架提供设备状态感知能力，包括绝对静止和相对静止，可检测设备是否处于静止或相对静止状态，适用于需要根据设备静止状态优化应用性能、智能省电、场景识别等场景。 > **说明：** > > 本模块不支持在x86平台上运行。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-unnamed-declare namespace stationary--><!--Device-unnamed-declare namespace stationary-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Stationary

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off_ActivityType](arkts-multimodalawareness-stationary-offactivitytype-f.md#off_ActivityType) | 设备状态管理，取消订阅设备状态服务。取消订阅后，将停止接收该状态相关的回调函数调用。调用off()时需要使用与on()相同的activity和event参数，才能正确取消对应的订阅。 |
| [on_ActivityType](arkts-multimodalawareness-stationary-onactivitytype-f.md#on_ActivityType) | 设备状态管理，订阅设备状态变化事件。当设备满足指定状态条件时，系统会触发回调函数上报状态变化事件，用于持续监听设备状态变化事件。调用on()后，必须在不使用时调用off()取消订阅，避免多余的性能功耗开销。 |
| [once_ActivityType](arkts-multimodalawareness-stationary-onceactivitytype-f.md#once_ActivityType) | 设备状态管理，查询设备状态。仅执行一次回调，用于一次性查询当前状态。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ActivityResponse](arkts-multimodalawareness-stationary-activityresponse-i.md) | 服务响应抽象接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ActivityEvent](arkts-multimodalawareness-stationary-activityevent-e.md) | 设备状态事件。 |
| [ActivityState](arkts-multimodalawareness-stationary-activitystate-e.md) | 设备状态返回值。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ActivityType](arkts-multimodalawareness-stationary-activitytype-t.md) | 设备状态类型。 |

