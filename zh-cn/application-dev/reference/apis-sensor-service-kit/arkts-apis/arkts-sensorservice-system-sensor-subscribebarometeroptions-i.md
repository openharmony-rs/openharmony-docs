# SubscribeBarometerOptions

用于设置气压计传感器订阅的参数，包括回调函数。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [BAROMETER](arkts-sensorservice-sensor-sensorid-e.md#BAROMETER)

<!--Device-unnamed-export interface SubscribeBarometerOptions--><!--Device-unnamed-export interface SubscribeBarometerOptions-End-->

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

<!--Device-SubscribeBarometerOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeBarometerOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## success

```TypeScript
success: (data: BarometerResponse) => void
```

气压计传感器数据改变后的回调函数，回调参数为BarometerResponse对象。

**类型：** (data: BarometerResponse) =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_SensorId.COLOR)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeBarometerOptions-success: (data: BarometerResponse) => void--><!--Device-SubscribeBarometerOptions-success: (data: BarometerResponse) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

