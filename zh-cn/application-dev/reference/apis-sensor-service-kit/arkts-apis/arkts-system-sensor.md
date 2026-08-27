# @system.sensor

本模块帮助应用实时获取传感器数据变化通知，实现运动监测、健康追踪、环境感知、方向识别、屏幕自适应等功能。每种传感器提供subscribe/unsubscribe配对接口，佩戴状态传感器额外提供getOnBodyState单次查询接口。
 非轻量穿戴设备从API version 8起不再维护本模块，建议使用[@ohos.sensor](arkts-sensor.md)模块替代。
 本模块采用"订阅-取消订阅"模式：通过subscribe订阅数据，数据变化时回调上报；通过unsubscribe取消订阅。subscribe与unsubscribe需配对使用，同一应用对同一传感器多次subscribe仅最后一次生效。
 加速度传感器、设备方向传感器和陀螺仪传感器的subscribe支持通过interval配置回调频率，默认为"normal"（200ms/次）。
 所有接口均需硬件支持，仅支持真机调试。部分接口存在设备行为差异，具体见各接口说明。
 > **说明：**
 > - 模块维护策略：
 > >     - 对于Lite Wearable设备类型，该模块长期维护，正常使用。
 > >     - 对于支持该模块的其他设备类型，该模块从API version 8开始不再维护，建议使用新接口[@ohos.sensor](arkts-sensor.md)替代。
 > - 该功能使用需要对应硬件支持，仅支持真机调试。
 > - 建议在页面销毁时（即onDestroy回调中），取消数据订阅，避免不必要的性能开销。


## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Sensor](arkts-sensorservice-system-sensor-sensor-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccelerometerResponse](arkts-sensorservice-system-sensor-accelerometerresponse-i.md) | 感应到加速度数据变化后的回调函数的响应对象，包含设备在x、y、z三轴方向上的加速度数据。 |
| [BarometerResponse](arkts-sensorservice-system-sensor-barometerresponse-i.md) | 气压计传感器数据改变后的回调函数的响应对象，包含气压值数据。 |
| [CompassResponse](arkts-sensorservice-system-sensor-compassresponse-i.md) | 罗盘数据改变后的回调函数的响应对象，包含设备面对的方向度数。 |
| [DeviceOrientationResponse](arkts-sensorservice-system-sensor-deviceorientationresponse-i.md) | 设备方向传感器数据变化后的回调函数的响应对象，包含设备方向的三个旋转角度数据。  **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。 |
| [GetOnBodyStateOptions](arkts-sensorservice-system-sensor-getonbodystateoptions-i.md) | 获取传感器所在设备佩戴状态时的参数，包括回调函数。此接口为一次性获取，不会持续监听状态变化。 |
| [GyroscopeResponse](arkts-sensorservice-system-sensor-gyroscoperesponse-i.md) | 陀螺仪传感器数据变化后的回调函数的响应对象，包含设备在x、y、z三轴方向的旋转角速度数据。 |
| [HeartRateResponse](arkts-sensorservice-system-sensor-heartrateresponse-i.md) | 心率传感器数据改变后的回调函数的响应对象，包含心率值数据。 |
| [LightResponse](arkts-sensorservice-system-sensor-lightresponse-i.md) | 光线感应数据改变后的回调函数的响应对象，包含环境光线强度数据。  **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。 |
| [OnBodyStateResponse](arkts-sensorservice-system-sensor-onbodystateresponse-i.md) | 设备佩戴状态的响应对象，包含设备是否已佩戴的状态数据。 |
| [ProximityResponse](arkts-sensorservice-system-sensor-proximityresponse-i.md) | 距离感应数据改变后的回调函数的响应对象，包含可见物体相对于设备显示屏的接近或远离状态数据。  **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。 |
| [StepCounterResponse](arkts-sensorservice-system-sensor-stepcounterresponse-i.md) | 计步传感器数据改变后的回调函数的响应对象，包含计步传感器重启后累计记录的步数数据。 |
| [subscribeAccelerometerOptions](arkts-sensorservice-system-sensor-subscribeaccelerometeroptions-i.md) | 用于设置加速度传感器订阅的参数，包括回调频率和回调函数。 |
| [SubscribeBarometerOptions](arkts-sensorservice-system-sensor-subscribebarometeroptions-i.md) | 用于设置气压计传感器订阅的参数，包括回调函数。 |
| [SubscribeCompassOptions](arkts-sensorservice-system-sensor-subscribecompassoptions-i.md) | 用于设置罗盘传感器订阅的参数，包括回调函数。 |
| [SubscribeDeviceOrientationOptions](arkts-sensorservice-system-sensor-subscribedeviceorientationoptions-i.md) | 用于设置设备方向传感器订阅的参数，包括回调频率和回调函数。  **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。 |
| [SubscribeGyroscopeOptions](arkts-sensorservice-system-sensor-subscribegyroscopeoptions-i.md) | 用于设置陀螺仪传感器订阅的参数，包括回调频率和回调函数。 |
| [SubscribeHeartRateOptions](arkts-sensorservice-system-sensor-subscribeheartrateoptions-i.md) | 用于设置心率传感器订阅的参数，包括回调函数。心率数据回调频率固定为5秒/次，不支持通过interval参数配置。 |
| [SubscribeLightOptions](arkts-sensorservice-system-sensor-subscribelightoptions-i.md) | 用于设置环境光传感器订阅的参数，包括回调函数。  **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。 |
| [SubscribeOnBodyStateOptions](arkts-sensorservice-system-sensor-subscribeonbodystateoptions-i.md) | 用于设置设备佩戴状态订阅的参数，包括回调函数。佩戴状态分为已佩戴和未佩戴两种。 |
| [SubscribeProximityOptions](arkts-sensorservice-system-sensor-subscribeproximityoptions-i.md) | 用于设置距离传感器订阅的参数，包括回调函数。  **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。 |
| [SubscribeStepCounterOptions](arkts-sensorservice-system-sensor-subscribestepcounteroptions-i.md) | 用于设置计步传感器订阅的参数，包括回调函数。 |
