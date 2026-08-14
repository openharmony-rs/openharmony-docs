# SubscribeOnBodyStateOptions

用于设置设备佩戴状态订阅的参数，包括回调函数。佩戴状态分为已穿戴和未穿戴两种。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [WEAR_DETECTION](arkts-sensorservice-sensor-sensorid-e.md#WEAR_DETECTION)

<!--Device-unnamed-export interface SubscribeOnBodyStateOptions--><!--Device-unnamed-export interface SubscribeOnBodyStateOptions-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。回调参数为(data: string, code: number)，其中data为错误信息，code为错误码。不填写时，接口调用失败无回调通知。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_SensorId.COLOR)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeOnBodyStateOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeOnBodyStateOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## success

```TypeScript
success: (data: OnBodyStateResponse) => void
```

传感器所在设备穿戴状态改变后的回调函数，回调参数为OnBodyStateResponse对象。

**类型：** (data: OnBodyStateResponse) =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_SensorId.COLOR)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeOnBodyStateOptions-success: (data: OnBodyStateResponse) => void--><!--Device-SubscribeOnBodyStateOptions-success: (data: OnBodyStateResponse) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

