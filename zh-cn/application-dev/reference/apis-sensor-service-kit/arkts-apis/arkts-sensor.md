# @system.sensor

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Sensor](arkts-sensorservice-sensor-sensor-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccelerometerResponse](arkts-sensorservice-sensor-accelerometerresponse-i.md) | 感应到加速度数据变化后的回调函数的响应对象，包含设备在x、y、z三轴方向上的加速度数据。 |
| [BarometerResponse](arkts-sensorservice-sensor-barometerresponse-i.md) | 气压计传感器数据改变后的回调函数的响应对象，包含气压值数据。 |
| [CompassResponse](arkts-sensorservice-sensor-compassresponse-i.md) | 罗盘数据改变后的回调函数的响应对象，包含设备面对的方向度数。 |
| [DeviceOrientationResponse](arkts-sensorservice-sensor-deviceorientationresponse-i.md) | 设备方向传感器数据变化后的回调函数的响应对象，包含设备方向的三个旋转角度数据。 |
| [GetOnBodyStateOptions](arkts-sensorservice-sensor-getonbodystateoptions-i.md) | 用于设置设备佩戴状态订阅的参数，包括回调函数。佩戴状态分为已穿戴和未穿戴两种。 |
| [GyroscopeResponse](arkts-sensorservice-sensor-gyroscoperesponse-i.md) | 陀螺仪传感器数据变化后的回调函数的响应对象，包含设备在x、y、z三轴方向的旋转角速度数据。 |
| [HeartRateResponse](arkts-sensorservice-sensor-heartrateresponse-i.md) | 心率传感器数据改变后的回调函数的响应对象，包含心率值数据。 |
| [LightResponse](arkts-sensorservice-sensor-lightresponse-i.md) | 光线感应数据改变后的回调函数的响应对象，包含环境光线强度数据。 |
| [OnBodyStateResponse](arkts-sensorservice-sensor-onbodystateresponse-i.md) | 设备佩戴状态的响应对象，包含设备是否已佩戴的状态数据。 |
| [ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md) | 距离感应数据改变后的回调函数的响应对象，包含可见物体相对于设备显示屏的接近或远离状态数据。 |
| [StepCounterResponse](arkts-sensorservice-sensor-stepcounterresponse-i.md) | 计步传感器数据改变后的回调函数的响应对象，包含计步传感器重启后累计记录的步数数据。 |
| [SubscribeBarometerOptions](arkts-sensorservice-sensor-subscribebarometeroptions-i.md) | 用于设置气压计传感器订阅的参数，包括回调函数。 |
| [SubscribeCompassOptions](arkts-sensorservice-sensor-subscribecompassoptions-i.md) | 用于设置罗盘传感器订阅的参数，包括回调函数。 |
| [SubscribeDeviceOrientationOptions](arkts-sensorservice-sensor-subscribedeviceorientationoptions-i.md) | 用于设置设备方向传感器订阅的参数，包括回调频率和回调函数。 |
| [SubscribeGyroscopeOptions](arkts-sensorservice-sensor-subscribegyroscopeoptions-i.md) | 用于设置陀螺仪传感器订阅的参数，包括回调频率和回调函数。 |
| [SubscribeHeartRateOptions](arkts-sensorservice-sensor-subscribeheartrateoptions-i.md) | 用于设置心率传感器订阅的参数，包括回调函数。心率数据回调频率固定为5秒/次，不支持通过interval参数配置。 |
| [SubscribeLightOptions](arkts-sensorservice-sensor-subscribelightoptions-i.md) | 用于设置环境光传感器订阅的参数，包括回调函数。 |
| [SubscribeOnBodyStateOptions](arkts-sensorservice-sensor-subscribeonbodystateoptions-i.md) | 用于设置设备佩戴状态订阅的参数，包括回调函数。佩戴状态分为已穿戴和未穿戴两种。 |
| [SubscribeProximityOptions](arkts-sensorservice-sensor-subscribeproximityoptions-i.md) | 用于设置距离传感器订阅的参数，包括回调函数。 |
| [SubscribeStepCounterOptions](arkts-sensorservice-sensor-subscribestepcounteroptions-i.md) | 用于设置计步传感器订阅的参数，包括回调函数。 |
| [subscribeAccelerometerOptions](arkts-sensorservice-sensor-subscribeaccelerometeroptions-i.md) | 用于设置加速度传感器订阅的参数，包括回调频率和回调函数。 |

