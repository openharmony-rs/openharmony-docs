# SubscribeLightOptions

用于设置环境光传感器订阅的参数，包括回调函数。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor.SensorId#AMBIENT_LIGHT

<!--Device-unnamed-export interface SubscribeLightOptions--><!--Device-unnamed-export interface SubscribeLightOptions-End-->

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

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeLightOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeLightOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## success

```TypeScript
success: (data: LightResponse) => void
```

光线感应数据改变后的回调函数，回调参数为LightResponse对象。

**类型：** (data: LightResponse) =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor#on

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeLightOptions-success: (data: LightResponse) => void--><!--Device-SubscribeLightOptions-success: (data: LightResponse) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

