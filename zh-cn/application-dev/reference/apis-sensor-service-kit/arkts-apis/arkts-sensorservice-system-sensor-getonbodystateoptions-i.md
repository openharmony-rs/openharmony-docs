# GetOnBodyStateOptions

用于设置设备佩戴状态订阅的参数，包括回调函数。佩戴状态分为已穿戴和未穿戴两种。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [WEAR_DETECTION](arkts-sensorservice-sensor-sensorid-e.md#WEAR_DETECTION)

<!--Device-unnamed-export interface GetOnBodyStateOptions--><!--Device-unnamed-export interface GetOnBodyStateOptions-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。无论调用成功或失败，此回调都会被执行。不填写时，接口调用结束无回调通知。

**类型：** () =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** once

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GetOnBodyStateOptions-complete?: () => void--><!--Device-GetOnBodyStateOptions-complete?: () => void-End-->

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

**替代接口：** once

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GetOnBodyStateOptions-fail?: (data: string, code: number) => void--><!--Device-GetOnBodyStateOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## success

```TypeScript
success: (data: OnBodyStateResponse) => void
```

接口调用成功的回调函数，回调参数为OnBodyStateResponse对象。

**类型：** (data: OnBodyStateResponse) =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** once

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GetOnBodyStateOptions-success: (data: OnBodyStateResponse) => void--><!--Device-GetOnBodyStateOptions-success: (data: OnBodyStateResponse) => void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

