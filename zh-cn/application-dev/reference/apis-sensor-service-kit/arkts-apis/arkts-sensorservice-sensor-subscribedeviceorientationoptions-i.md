# SubscribeDeviceOrientationOptions

用于设置设备方向传感器订阅的参数，包括回调频率和回调函数。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor.SensorId#ORIENTATION

<!--Device-unnamed-export interface SubscribeDeviceOrientationOptions--><!--Device-unnamed-export interface SubscribeDeviceOrientationOptions-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。回调参数为(data: string, code: number)，其中data为错误信息，code为错误码。不填写时，接口调用失败无回调通知。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor#on

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeDeviceOrientationOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeDeviceOrientationOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## interval

```TypeScript
interval: string
```

频率参数，设备方向传感器的回调函数执行频率。 默认值：'normal'。 可选值： -'game'：极高的回调频率，20ms/次，适用于游戏场景。 -'ui'：较高的回调频率，60ms/次，适用于UI更新场景。 -'normal'：普通的回调频率，200ms/次，适用于低功耗场景。

**类型：** string

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor#Options.interval

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeDeviceOrientationOptions-interval: string--><!--Device-SubscribeDeviceOrientationOptions-interval: string-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## success

```TypeScript
success: (data: DeviceOrientationResponse) => void
```

感应到设备方向传感器数据变化后的回调函数，回调参数为DeviceOrientationResponse对象。

**类型：** (data: DeviceOrientationResponse) =&gt; void

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor#on

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-SubscribeDeviceOrientationOptions-success: (data: DeviceOrientationResponse) => void--><!--Device-SubscribeDeviceOrientationOptions-success: (data: DeviceOrientationResponse) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

