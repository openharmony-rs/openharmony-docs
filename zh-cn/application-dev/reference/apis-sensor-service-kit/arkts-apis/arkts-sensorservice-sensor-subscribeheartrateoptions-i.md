# SubscribeHeartRateOptions

用于设置心率传感器订阅的参数，包括回调函数。心率数据回调频率固定为5秒/次，不支持通过interval参数配置。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor.SensorId#HEART_RATE

**需要权限：** ohos.permission.READ_HEALTH_DATA

<!--Device-unnamed-export interface SubscribeHeartRateOptions--><!--Device-unnamed-export interface SubscribeHeartRateOptions-End-->

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

**替代接口：** ohos.sensor/sensor#on

**需要权限：** ohos.permission.READ_HEALTH_DATA

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeHeartRateOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeHeartRateOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## success

```TypeScript
success: (data: HeartRateResponse) => void
```

心率传感器数据改变后的回调函数，回调参数为HeartRateResponse对象。回调频率固定为5s/次。

**类型：** (data: HeartRateResponse) =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor#on

**需要权限：** ohos.permission.READ_HEALTH_DATA

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeHeartRateOptions-success: (data: HeartRateResponse) => void--><!--Device-SubscribeHeartRateOptions-success: (data: HeartRateResponse) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

