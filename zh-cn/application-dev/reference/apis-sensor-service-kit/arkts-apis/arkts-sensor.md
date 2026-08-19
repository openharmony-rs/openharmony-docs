# @ohos.sensor

**起始版本：** 23

<!--Device-unnamed-declare namespace sensor--><!--Device-unnamed-declare namespace sensor-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createQuaternion](arkts-sensorservice-sensor-createquaternion-f.md) | 将旋转矢量转换为四元数。使用callback异步回调。 |
| [createQuaternion](arkts-sensorservice-sensor-createquaternion-f.md) | 将旋转矢量转换为四元数。使用Promise异步回调。 |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md) | 将旋转矢量转换为旋转矩阵。使用callback异步回调。 |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md) | 将旋转矢量转换为旋转矩阵。使用Promise异步回调。 |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md) | 根据重力矢量和地磁矢量计算旋转矩阵。使用callback异步回调。 |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md) | 根据重力矢量和地磁矢量计算旋转矩阵。使用Promise异步回调。 |
| [getAltitude](arkts-sensorservice-sensor-getaltitude-f.md) | 根据气压值获取设备所在的海拔高度。使用callback异步回调。 |
| [getAltitude](arkts-sensorservice-sensor-getaltitude-f.md) | 根据气压值获取设备所在的海拔高度。使用Promise异步回调。 |
| [getAngleModify](arkts-sensorservice-sensor-getanglemodify-f.md) | Obtains the angle change between two rotation matrices. This API uses an asynchronous callback to return the result. |
| [getAngleModify](arkts-sensorservice-sensor-getanglemodify-f.md) | Obtains the angle change between two rotation matrices. This API uses a promise to return the result. |
| [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md) | 计算两个旋转矩阵之间的角度变化。使用callback异步回调。 |
| [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md) | 得到两个旋转矩阵之间的角度变化。使用Promise异步回调。 |
| [getDeviceAltitude](arkts-sensorservice-sensor-getdevicealtitude-f.md) | 根据气压值获取海拔高度。使用callback异步回调。 |
| [getDeviceAltitude](arkts-sensorservice-sensor-getdevicealtitude-f.md) | 根据气压值获取海拔高度。使用Promise异步回调。 |
| [getDirection](arkts-sensorservice-sensor-getdirection-f.md) | 根据旋转矩阵计算设备的方向。使用callback异步回调。 |
| [getDirection](arkts-sensorservice-sensor-getdirection-f.md) | 根据旋转矩阵计算设备的方向。使用Promise异步回调。 |
| [getGeomagneticDip](arkts-sensorservice-sensor-getgeomagneticdip-f.md) | 根据倾斜矩阵计算地磁倾斜角。使用callback异步回调。 |
| [getGeomagneticDip](arkts-sensorservice-sensor-getgeomagneticdip-f.md) | 根据倾斜矩阵计算地磁倾斜角。使用Promise异步回调。 |
| [getGeomagneticField](arkts-sensorservice-sensor-getgeomagneticfield-f.md) | 获取地球上特定位置的地磁场。使用callback异步回调。 |
| [getGeomagneticField](arkts-sensorservice-sensor-getgeomagneticfield-f.md) | 获取地球上特定位置的地磁场。使用Promise异步回调。 |
| [getGeomagneticInfo](arkts-sensorservice-sensor-getgeomagneticinfo-f.md) | 获取某时刻地球上特定位置的地磁场信息。使用callback异步回调。 |
| [getGeomagneticInfo](arkts-sensorservice-sensor-getgeomagneticinfo-f.md) | 获取某时刻地球上特定位置的地磁场信息。使用Promise异步回调。 |
| [getInclination](arkts-sensorservice-sensor-getinclination-f.md) | 根据倾斜矩阵计算地磁倾角。使用callback异步回调。 |
| [getInclination](arkts-sensorservice-sensor-getinclination-f.md) | 根据倾斜矩阵计算地磁倾角。使用Promise异步回调。 |
| [getOrientation](arkts-sensorservice-sensor-getorientation-f.md) | 根据旋转矩阵计算设备方向。使用callback异步回调。 |
| [getOrientation](arkts-sensorservice-sensor-getorientation-f.md) | 根据旋转矩阵计算设备的方向。使用Promise异步回调。 |
| [getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md) | 根据旋转向量计算归一化四元数。使用callback异步回调。 |
| [getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md) | 根据旋转向量计算归一化四元数。使用Promise异步回调。 |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md) | 根据旋转矢量获取旋转矩阵。使用callback异步回调。 |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md) | 根据旋转矢量获取旋转矩阵。使用Promise异步回调。 |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md) | 根据重力矢量和地磁矢量计算旋转矩阵。使用callback异步回调。 |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md) | 根据重力矢量和地磁矢量计算旋转矩阵。使用Promise异步回调。 |
| [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md) | 获取设备上的所有传感器信息。使用callback异步回调。如果需要同步获取传感器列表，请使用getSensorListSync。 |
| [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md) | 获取设备上的所有传感器信息。使用Promise异步回调。 |
| [getSensorListByDeviceSync](arkts-sensorservice-sensor-getsensorlistbydevicesync-f.md) | 同步获取设备的所有传感器信息。getSensorListByDeviceSync返回设备上所有传感器信息，getSingleSensorByDeviceSync返回指定单个传感器信息。 |
| [getSensorListSync](arkts-sensorservice-sensor-getsensorlistsync-f.md) | 获取设备上的所有传感器信息，使用同步方式返回结果。 |
| [getSingleSensor](arkts-sensorservice-sensor-getsinglesensor-f.md) | 获取指定传感器类型的属性信息。使用callback异步回调。 |
| [getSingleSensor](arkts-sensorservice-sensor-getsinglesensor-f.md) | 获取指定类型的传感器信息。使用Promise异步回调。 |
| [getSingleSensorByDeviceSync](arkts-sensorservice-sensor-getsinglesensorbydevicesync-f.md) | 同步获取指定设备和类型的传感器信息。如果存在外设且未指定设备ID，获取到的传感器将是所有符合指定传感器类型的本地和外设传感器。如果不存在外设，则仅获取本地的传感器。 |
| [getSingleSensorSync](arkts-sensorservice-sensor-getsinglesensorsync-f.md) | 获取指定类型的传感器信息，使用同步方式返回结果。 |
| [offAccelerometerChange](arkts-sensorservice-sensor-offaccelerometerchange-f.md) | Unsubscribe to accelerometer sensor data, {@code SensorId.ACCELEROMETER}. |
| [offAccelerometerUncalibratedChange](arkts-sensorservice-sensor-offaccelerometeruncalibratedchange-f.md) | Unsubscribe to uncalibrated accelerometer sensor data, {@code SensorId.ACCELEROMETER_UNCALIBRATED}. |
| [offAmbientLightChange](arkts-sensorservice-sensor-offambientlightchange-f.md) | Unsubscribe to ambient light sensor data, {@code SensorId.AMBIENT_LIGHT}. |
| [offAmbientTemperatureChange](arkts-sensorservice-sensor-offambienttemperaturechange-f.md) | Unsubscribe to ambient temperature sensor data， {@code SensorId.AMBIENT_TEMPERATURE}. |
| [offBarometerChange](arkts-sensorservice-sensor-offbarometerchange-f.md) | Unsubscribe to barometer sensor data, {@code SensorId.BAROMETER}. |
| [offFusionPressureChange](arkts-sensorservice-sensor-offfusionpressurechange-f.md) | Unsubscribe to fusion pressure sensor data, {@code SensorId.FUSION_PRESSURE}. |
| [offGravityChange](arkts-sensorservice-sensor-offgravitychange-f.md) | Unsubscribe to gravity sensor data, {@code SensorId.GRAVITY}. |
| [offGyroscopeChange](arkts-sensorservice-sensor-offgyroscopechange-f.md) | Unsubscribe to gyroscope sensor data, {@code SensorId.GYROSCOPE}. |
| [offGyroscopeUncalibratedChange](arkts-sensorservice-sensor-offgyroscopeuncalibratedchange-f.md) | Unsubscribe to uncalibrated gyroscope sensor data, {@code SensorId.GYROSCOPE_UNCALIBRATED}. |
| [offHallChange](arkts-sensorservice-sensor-offhallchange-f.md) | Unsubscribe to hall sensor data, {@code SensorId.HALL}. |
| [offHeartRateChange](arkts-sensorservice-sensor-offheartratechange-f.md) | Unsubscribe to heart rate sensor data, {@code SensorId.HEART_RATE}. |
| [offHumidityChange](arkts-sensorservice-sensor-offhumiditychange-f.md) | Unsubscribe to humidity sensor data, {@code SensorId.HUMIDITY}. |
| [offLinearAccelerometerChange](arkts-sensorservice-sensor-offlinearaccelerometerchange-f.md) | Unsubscribe to linear acceleration sensor data, {@code SensorId.LINEAR_ACCELEROMETER}. |
| [offMagneticFieldChange](arkts-sensorservice-sensor-offmagneticfieldchange-f.md) | Unsubscribe to magnetic field sensor data, {@code SensorId.MAGNETIC_FIELD}. |
| [offMagneticFieldUncalibratedChange](arkts-sensorservice-sensor-offmagneticfielduncalibratedchange-f.md) | Unsubscribe to uncalibrated magnetic field sensor data, {@code SensorId.MAGNETIC_FIELD_UNCALIBRATED}. |
| [offOrientationChange](arkts-sensorservice-sensor-offorientationchange-f.md) | Unsubscribe to orientation sensor data, {@code SensorId.ORIENTATION}. |
| [offPedometerChange](arkts-sensorservice-sensor-offpedometerchange-f.md) | Unsubscribe to pedometer sensor data, {@code SensorId.PEDOMETER}. |
| [offPedometerDetectionChange](arkts-sensorservice-sensor-offpedometerdetectionchange-f.md) | Unsubscribe to pedometer detection sensor data, {@code SensorId.PEDOMETER_DETECTION}. |
| [offProximityChange](arkts-sensorservice-sensor-offproximitychange-f.md) | Unsubscribe to proximity sensor data, {@code SensorId.PROXIMITY}. |
| [offRotationVectorChange](arkts-sensorservice-sensor-offrotationvectorchange-f.md) | Unsubscribe to rotation vector sensor data, {@code SensorId.ROTATION_VECTOR}. |
| [offSensorStatusChange](arkts-sensorservice-sensor-offsensorstatuschange-f.md) | Stop listening on device status changes. |
| [offSignificantMotionChange](arkts-sensorservice-sensor-offsignificantmotionchange-f.md) | Unsubscribe to significant motion sensor data, {@code SensorId.SIGNIFICANT_MOTION}. |
| [offWearDetectionChange](arkts-sensorservice-sensor-offweardetectionchange-f.md) | Unsubscribe to wear detection sensor data, {@code SensorId.WEAR_DETECTION}. |
| [off_SensorId.ACCELEROMETER](arkts-sensorservice-sensor-offsensoridaccelerometer-f.md#off_sensoridaccelerometer) | 取消订阅加速度传感器数据。当不再需要接收加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.ACCELEROMETER](arkts-sensorservice-sensor-offsensoridaccelerometer-f.md#off_sensoridaccelerometer-1) | 取消订阅加速度传感器数据。当不再需要接收加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-offsensoridaccelerometeruncalibrated-f.md#off_sensoridaccelerometer_uncalibrated) | 取消订阅未校准加速度传感器数据。当不再需要接收未校准加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-offsensoridaccelerometeruncalibrated-f.md#off_sensoridaccelerometer_uncalibrated-1) | 取消订阅未校准加速度传感器数据。当不再需要接收未校准加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.AMBIENT_LIGHT](arkts-sensorservice-sensor-offsensoridambientlight-f.md#off_sensoridambient_light) | 取消订阅环境光传感器数据。当不再需要接收环境光传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.AMBIENT_LIGHT](arkts-sensorservice-sensor-offsensoridambientlight-f.md#off_sensoridambient_light-1) | 取消订阅环境光传感器数据。当不再需要接收环境光传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-offsensoridambienttemperature-f.md#off_sensoridambient_temperature) | 取消订阅温度传感器数据。当不再需要接收温度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-offsensoridambienttemperature-f.md#off_sensoridambient_temperature-1) | 取消订阅温度传感器数据。当不再需要接收温度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.BAROMETER](arkts-sensorservice-sensor-offsensoridbarometer-f.md#off_sensoridbarometer) | 取消订阅气压计传感器数据。当不再需要接收气压计传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.BAROMETER](arkts-sensorservice-sensor-offsensoridbarometer-f.md#off_sensoridbarometer-1) | 取消订阅气压计传感器数据。当不再需要接收气压计传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.FUSION_PRESSURE](arkts-sensorservice-sensor-offsensoridfusionpressure-f.md#off_sensoridfusion_pressure) | 取消订阅融合压力传感器数据。当不再需要接收融合压力传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.GRAVITY](arkts-sensorservice-sensor-offsensoridgravity-f.md#off_sensoridgravity) | 取消订阅重力传感器数据。当不再需要接收重力传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.GRAVITY](arkts-sensorservice-sensor-offsensoridgravity-f.md#off_sensoridgravity-1) | 取消订阅重力传感器数据。当不再需要接收重力传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.GYROSCOPE](arkts-sensorservice-sensor-offsensoridgyroscope-f.md#off_sensoridgyroscope) | 取消订阅陀螺仪传感器数据。当不再需要接收陀螺仪传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.GYROSCOPE](arkts-sensorservice-sensor-offsensoridgyroscope-f.md#off_sensoridgyroscope-1) | 取消订阅陀螺仪传感器数据。当不再需要接收陀螺仪传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-offsensoridgyroscopeuncalibrated-f.md#off_sensoridgyroscope_uncalibrated) | 取消订阅未校准陀螺仪传感器数据。当不再需要接收未校准陀螺仪传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-offsensoridgyroscopeuncalibrated-f.md#off_sensoridgyroscope_uncalibrated-1) | 取消订阅未校准陀螺仪传感器数据。 |
| [off_SensorId.HALL](arkts-sensorservice-sensor-offsensoridhall-f.md#off_sensoridhall) | 取消订阅霍尔传感器数据。当不再需要接收霍尔传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.HALL](arkts-sensorservice-sensor-offsensoridhall-f.md#off_sensoridhall-1) | 取消订阅霍尔传感器数据。当不再需要接收霍尔传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.HEART_RATE](arkts-sensorservice-sensor-offsensoridheartrate-f.md#off_sensoridheart_rate) | 取消订阅心率传感器数据。当不再需要接收心率传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.HEART_RATE](arkts-sensorservice-sensor-offsensoridheartrate-f.md#off_sensoridheart_rate-1) | 取消订阅心率传感器数据。当不再需要接收心率传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.HUMIDITY](arkts-sensorservice-sensor-offsensoridhumidity-f.md#off_sensoridhumidity) | 取消订阅湿度传感器数据。当不再需要接收湿度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.HUMIDITY](arkts-sensorservice-sensor-offsensoridhumidity-f.md#off_sensoridhumidity-1) | 取消订阅湿度传感器数据。当不再需要接收湿度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.LINEAR_ACCELEROMETER](arkts-sensorservice-sensor-offsensoridlinearaccelerometer-f.md#off_sensoridlinear_accelerometer) | 取消订阅线性加速度传感器数据。当不再需要接收线性加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.LINEAR_ACCELEROMETER](arkts-sensorservice-sensor-offsensoridlinearaccelerometer-f.md#off_sensoridlinear_accelerometer-1) | 取消订阅线性加速度传感器数据。当不再需要接收线性加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.MAGNETIC_FIELD](arkts-sensorservice-sensor-offsensoridmagneticfield-f.md#off_sensoridmagnetic_field) | 取消订阅磁场传感器数据。当不再需要接收磁场传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.MAGNETIC_FIELD](arkts-sensorservice-sensor-offsensoridmagneticfield-f.md#off_sensoridmagnetic_field-1) | 取消订阅磁场传感器数据。当不再需要接收磁场传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-offsensoridmagneticfielduncalibrated-f.md#off_sensoridmagnetic_field_uncalibrated) | 取消订阅未校准的磁场传感器数据。当不再需要接收未校准磁场传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-offsensoridmagneticfielduncalibrated-f.md#off_sensoridmagnetic_field_uncalibrated-1) | 取消订阅未校准的磁场传感器数据。当不再需要接收未校准磁场传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.ORIENTATION](arkts-sensorservice-sensor-offsensoridorientation-f.md#off_sensoridorientation) | 取消订阅方向传感器数据。当不再需要接收方向传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.ORIENTATION](arkts-sensorservice-sensor-offsensoridorientation-f.md#off_sensoridorientation-1) | 取消订阅方向传感器数据。当不再需要接收方向传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.PEDOMETER](arkts-sensorservice-sensor-offsensoridpedometer-f.md#off_sensoridpedometer) | 取消订阅计步器传感器数据。当不再需要接收计步器传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.PEDOMETER](arkts-sensorservice-sensor-offsensoridpedometer-f.md#off_sensoridpedometer-1) | 取消订阅计步器传感器数据。当不再需要接收计步器传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.PEDOMETER_DETECTION](arkts-sensorservice-sensor-offsensoridpedometerdetection-f.md#off_sensoridpedometer_detection) | 取消订阅计步检测器传感器数据。当不再需要接收计步检测器传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.PEDOMETER_DETECTION](arkts-sensorservice-sensor-offsensoridpedometerdetection-f.md#off_sensoridpedometer_detection-1) | 取消订阅计步检测器传感器数据。当不再需要接收计步检测器传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.PROXIMITY](arkts-sensorservice-sensor-offsensoridproximity-f.md#off_sensoridproximity) | 取消订阅接近光传感器数据。当不再需要接收接近光传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.PROXIMITY](arkts-sensorservice-sensor-offsensoridproximity-f.md#off_sensoridproximity-1) | 取消订阅接近光传感器数据。当不再需要接收接近光传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.ROTATION_VECTOR](arkts-sensorservice-sensor-offsensoridrotationvector-f.md#off_sensoridrotation_vector) | 取消订阅旋转矢量传感器数据。当不再需要接收旋转矢量传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.ROTATION_VECTOR](arkts-sensorservice-sensor-offsensoridrotationvector-f.md#off_sensoridrotation_vector-1) | 取消订阅旋转矢量传感器数据。当不再需要接收旋转矢量传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.SIGNIFICANT_MOTION](arkts-sensorservice-sensor-offsensoridsignificantmotion-f.md#off_sensoridsignificant_motion) | 取消订阅有效运动传感器数据。当不再需要接收有效运动传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.SIGNIFICANT_MOTION](arkts-sensorservice-sensor-offsensoridsignificantmotion-f.md#off_sensoridsignificant_motion-1) | 取消订阅有效运动传感器数据。当不再需要接收有效运动传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.WEAR_DETECTION](arkts-sensorservice-sensor-offsensoridweardetection-f.md#off_sensoridwear_detection) | 取消订阅佩戴检测传感器数据。当不再需要接收佩戴检测传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorId.WEAR_DETECTION](arkts-sensorservice-sensor-offsensoridweardetection-f.md#off_sensoridwear_detection-1) | 取消订阅佩戴检测传感器数据。当不再需要接收佩戴检测传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_ACCELEROMETER](arkts-sensorservice-sensor-offsensortypesensortypeidaccelerometer-f.md#off_sensortypesensor_type_id_accelerometer) | 取消订阅加速度传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-offsensortypesensortypeidaccelerometeruncalibrated-f.md#off_sensortypesensor_type_id_accelerometer_uncalibrated) | 取消订阅未校准加速度传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT](arkts-sensorservice-sensor-offsensortypesensortypeidambientlight-f.md#off_sensortypesensor_type_id_ambient_light) | 取消订阅环境光传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-offsensortypesensortypeidambienttemperature-f.md#off_sensortypesensor_type_id_ambient_temperature) | 取消订阅环境温度传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_BAROMETER](arkts-sensorservice-sensor-offsensortypesensortypeidbarometer-f.md#off_sensortypesensor_type_id_barometer) | 取消订阅气压计传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_GRAVITY](arkts-sensorservice-sensor-offsensortypesensortypeidgravity-f.md#off_sensortypesensor_type_id_gravity) | 取消订阅重力传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_GYROSCOPE](arkts-sensorservice-sensor-offsensortypesensortypeidgyroscope-f.md#off_sensortypesensor_type_id_gyroscope) | 取消订阅陀螺仪传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-offsensortypesensortypeidgyroscopeuncalibrated-f.md#off_sensortypesensor_type_id_gyroscope_uncalibrated) | 取消订阅未校准陀螺仪传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_HALL](arkts-sensorservice-sensor-offsensortypesensortypeidhall-f.md#off_sensortypesensor_type_id_hall) | 取消订阅霍尔传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_HEART_RATE](arkts-sensorservice-sensor-offsensortypesensortypeidheartrate-f.md#off_sensortypesensor_type_id_heart_rate) | 取消订阅心率传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_HUMIDITY](arkts-sensorservice-sensor-offsensortypesensortypeidhumidity-f.md#off_sensortypesensor_type_id_humidity) | 取消订阅湿度传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION](arkts-sensorservice-sensor-offsensortypesensortypeidlinearacceleration-f.md#off_sensortypesensor_type_id_linear_acceleration) | 取消订阅线性加速度传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD](arkts-sensorservice-sensor-offsensortypesensortypeidmagneticfield-f.md#off_sensortypesensor_type_id_magnetic_field) | 取消订阅磁场传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-offsensortypesensortypeidmagneticfielduncalibrated-f.md#off_sensortypesensor_type_id_magnetic_field_uncalibrated) | 取消订阅未校准磁场传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_ORIENTATION](arkts-sensorservice-sensor-offsensortypesensortypeidorientation-f.md#off_sensortypesensor_type_id_orientation) | 取消订阅方向传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_PEDOMETER](arkts-sensorservice-sensor-offsensortypesensortypeidpedometer-f.md#off_sensortypesensor_type_id_pedometer) | 取消订阅计步传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION](arkts-sensorservice-sensor-offsensortypesensortypeidpedometerdetection-f.md#off_sensortypesensor_type_id_pedometer_detection) | 取消订阅计步检测传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_PROXIMITY](arkts-sensorservice-sensor-offsensortypesensortypeidproximity-f.md#off_sensortypesensor_type_id_proximity) | 取消订阅接近光传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR](arkts-sensorservice-sensor-offsensortypesensortypeidrotationvector-f.md#off_sensortypesensor_type_id_rotation_vector) | 取消订阅旋转矢量传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION](arkts-sensorservice-sensor-offsensortypesensortypeidsignificantmotion-f.md#off_sensortypesensor_type_id_significant_motion) | 取消订阅有效运动传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_SensorType.SENSOR_TYPE_ID_WEAR_DETECTION](arkts-sensorservice-sensor-offsensortypesensortypeidweardetection-f.md#off_sensortypesensor_type_id_wear_detection) | 取消订阅佩戴检测传感器数据。off取消订阅必须与on订阅成对出现。 |
| [off_sensorStatusChange](arkts-sensorservice-sensor-offsensorstatuschange-f.md) | 取消监听传感器上线下线状态的变化。当不再需要感知传感器上下线状态时调用此接口取消监听。off取消监听必须与on监听成对出现。 |
| [onAccelerometerChange](arkts-sensorservice-sensor-onaccelerometerchange-f.md) | Subscribe to accelerometer sensor data, {@code SensorId.ACCELEROMETER}. |
| [onAccelerometerUncalibratedChange](arkts-sensorservice-sensor-onaccelerometeruncalibratedchange-f.md) | Subscribe to uncalibrated accelerometer sensor data, {@code SensorId.ACCELEROMETER_UNCALIBRATED}. |
| [onAmbientLightChange](arkts-sensorservice-sensor-onambientlightchange-f.md) | Subscribe to ambient light sensor data, {@code SensorId.AMBIENT_LIGHT}. |
| [onAmbientTemperatureChange](arkts-sensorservice-sensor-onambienttemperaturechange-f.md) | Subscribe to ambient temperature sensor data, {@code SensorId.AMBIENT_TEMPERATURE}. |
| [onBarometerChange](arkts-sensorservice-sensor-onbarometerchange-f.md) | Subscribe to barometer sensor data, {@code SensorId.BAROMETER}. |
| [onFusionPressureChange](arkts-sensorservice-sensor-onfusionpressurechange-f.md) | Subscribe to fusion pressure sensor data, {@code SensorId.FUSION_PRESSURE}. |
| [onGravityChange](arkts-sensorservice-sensor-ongravitychange-f.md) | Subscribe to gravity sensor data, {@code SensorId.GRAVITY}. |
| [onGyroscopeChange](arkts-sensorservice-sensor-ongyroscopechange-f.md) | Subscribe to gyroscope sensor data, {@code SensorId.GYROSCOPE}. |
| [onGyroscopeUncalibratedChange](arkts-sensorservice-sensor-ongyroscopeuncalibratedchange-f.md) | Subscribe to uncalibrated gyroscope sensor data, {@code SensorId.GYROSCOPE_UNCALIBRATED}. |
| [onHallChange](arkts-sensorservice-sensor-onhallchange-f.md) | Subscribe to hall sensor data, {@code SensorId.HALL}. |
| [onHeartRateChange](arkts-sensorservice-sensor-onheartratechange-f.md) | Subscribe to heart rate sensor data, {@code SensorId.HEART_RATE}. |
| [onHumidityChange](arkts-sensorservice-sensor-onhumiditychange-f.md) | Subscribe to humidity sensor data, {@code SensorId.HUMIDITY}. |
| [onLinearAccelerometerChange](arkts-sensorservice-sensor-onlinearaccelerometerchange-f.md) | Subscribe to linear acceleration sensor data, {@code SensorId.LINEAR_ACCELEROMETER}. |
| [onMagneticFieldChange](arkts-sensorservice-sensor-onmagneticfieldchange-f.md) | Subscribe to magnetic field sensor data, {@code SensorId.MAGNETIC_FIELD}. |
| [onMagneticFieldUncalibratedChange](arkts-sensorservice-sensor-onmagneticfielduncalibratedchange-f.md) | Subscribe to uncalibrated magnetic field sensor data, {@code SensorId.MAGNETIC_FIELD_UNCALIBRATED}. |
| [onOrientationChange](arkts-sensorservice-sensor-onorientationchange-f.md) | Subscribe to orientation sensor data, {@code SensorId.ORIENTATION}. |
| [onPedometerChange](arkts-sensorservice-sensor-onpedometerchange-f.md) | Subscribe to pedometer sensor data, {@code SensorId.PEDOMETER}. |
| [onPedometerDetectionChange](arkts-sensorservice-sensor-onpedometerdetectionchange-f.md) | Subscribe to pedometer detection sensor data, {@code SensorId.PEDOMETER_DETECTION}. |
| [onProximityChange](arkts-sensorservice-sensor-onproximitychange-f.md) | Subscribe to proximity sensor data, {@code SensorId.PROXIMITY}. |
| [onRotationVectorChange](arkts-sensorservice-sensor-onrotationvectorchange-f.md) | Subscribe to rotation vector sensor data, {@code SensorId.ROTATION_VECTOR}. |
| [onSensorStatusChange](arkts-sensorservice-sensor-onsensorstatuschange-f.md) | Start listening on device status changes. |
| [onSignificantMotionChange](arkts-sensorservice-sensor-onsignificantmotionchange-f.md) | Subscribe to significant motion sensor data, {@code SensorId.SIGNIFICANT_MOTION}. |
| [onWearDetectionChange](arkts-sensorservice-sensor-onweardetectionchange-f.md) | Subscribe to wear detection sensor data, {@code SensorId.WEAR_DETECTION}. |
| [on_SensorId.ACCELEROMETER](arkts-sensorservice-sensor-onsensoridaccelerometer-f.md#on_sensoridaccelerometer) | 订阅加速度传感器数据。加速度传感器用于测量设备在X、Y、Z三个方向上的加速度，包含重力加速度分量。适用于需要感知设备运动状态、实现屏幕旋转、游戏操控、计步等场景。 调用后，系统会按设定频率通过callback持续上报加速度数据。 |
| [on_SensorId.ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-onsensoridaccelerometeruncalibrated-f.md#on_sensoridaccelerometer_uncalibrated) | 订阅未校准加速度传感器数据。未校准加速度传感器与加速度传感器的区别在于，其上报的偏移值(biasX/biasY/biasZ)未经系统校准补偿，适用于需要获取原始加速度数据或自行实现校准算法的场景。 与sensor.on('SensorId.ACCELEROMETER')相比，本接口额外提供偏移值信息，适用于需要分析设备校准偏差的场景。 |
| [on_SensorId.AMBIENT_LIGHT](arkts-sensorservice-sensor-onsensoridambientlight-f.md#on_sensoridambient_light) | 订阅环境光传感器数据。环境光传感器用于测量周围环境的光照强度，适用于自动调节屏幕亮度、判断环境明暗等场景。调用后，系统会按设定频率通过callback持续上报环境光强度数据。 |
| [on_SensorId.AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-onsensoridambienttemperature-f.md#on_sensoridambient_temperature) | 订阅环境温度传感器数据。温度传感器用于测量设备周围的环境温度，适用于环境温度监测、温度补偿等场景。调用后，系统会按设定频率通过callback持续上报温度数据。 |
| [on_SensorId.BAROMETER](arkts-sensorservice-sensor-onsensoridbarometer-f.md#on_sensoridbarometer) | 订阅气压计传感器数据。气压计传感器用于测量大气压强，适用于海拔估算、天气预报辅助等场景。调用后，系统会按设定频率通过callback持续上报气压数据。 |
| [on_SensorId.FUSION_PRESSURE](arkts-sensorservice-sensor-onsensoridfusionpressure-f.md#on_sensoridfusion_pressure) | 订阅融合压力传感器数据。融合压力传感器用于获取经融合算法处理的压力数据，仅适用于智能手表设备。适用于需要获取手腕压力数据的健康监测场景。调用后，系统会按设定频率通过callback持续上报融合压力数据。 |
| [on_SensorId.GRAVITY](arkts-sensorservice-sensor-onsensoridgravity-f.md#on_sensoridgravity) | 订阅重力传感器数据。重力传感器用于测量设备在X、Y、Z三个方向上受到的重力加速度分量，适用于需要分离重力分量进行运动分析的场景，如游戏操控、运动检测。 调用后，系统会按设定频率通过callback持续上报重力分量数据。 |
| [on_SensorId.GYROSCOPE](arkts-sensorservice-sensor-onsensoridgyroscope-f.md#on_sensoridgyroscope) | 订阅校准的陀螺仪传感器数据。陀螺仪传感器用于测量设备绕X、Y、Z轴的旋转角速度，适用于设备旋转检测、姿态跟踪、游戏操控等场景。调用后，系统会按设定频率通过callback持续上报角速度数据。 |
| [on_SensorId.GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-onsensoridgyroscopeuncalibrated-f.md#on_sensoridgyroscope_uncalibrated) | 订阅未校准陀螺仪传感器数据。未校准陀螺仪传感器与陀螺仪传感器的区别在于，其上报的偏移值(biasX/biasY/biasZ)未经系统校准补偿，适用于需要获取原始陀螺仪数据或自行实现校准算法的场景。 与sensor.on('SensorId.GYROSCOPE')相比，本接口额外提供偏移值信息，适用于需要分析设备陀螺仪校准偏差的场景。 |
| [on_SensorId.HALL](arkts-sensorservice-sensor-onsensoridhall-f.md#on_sensoridhall) | 订阅霍尔传感器数据。霍尔传感器用于检测磁场变化，常用于检测翻盖手机或皮套的开合状态。当霍尔事件被触发得较为频繁时，可通过options参数限定事件上报频率。 调用后，系统会通过callback持续上报霍尔状态数据。 |
| [on_SensorId.HEART_RATE](arkts-sensorservice-sensor-onsensoridheartrate-f.md#on_sensoridheart_rate) | 订阅心率传感器数据。心率传感器用于测量用户的心率值，适用于健康监测、运动辅助等场景。调用后，系统会按设定频率通过callback持续上报心率数据。 |
| [on_SensorId.HUMIDITY](arkts-sensorservice-sensor-onsensoridhumidity-f.md#on_sensoridhumidity) | 订阅湿度传感器数据。湿度传感器用于测量周围环境的相对湿度，适用于环境湿度监测、智能家居联动等场景。调用后，系统会按设定频率通过callback持续上报湿度数据。 |
| [on_SensorId.LINEAR_ACCELEROMETER](arkts-sensorservice-sensor-onsensoridlinearaccelerometer-f.md#on_sensoridlinear_accelerometer) | 订阅线性加速度传感器数据。线性加速度传感器用于测量设备在X、Y、Z三个方向上的加速度（不含重力加速度分量），适用于需要感知设备纯粹运动加速度的场景，如运动追踪、碰撞检测。 与sensor.on('SensorId.ACCELEROMETER')相比，本接口已去除重力分量，适用于仅需设备运动加速度的场景。 |
| [on_SensorId.MAGNETIC_FIELD](arkts-sensorservice-sensor-onsensoridmagneticfield-f.md#on_sensoridmagnetic_field) | 订阅地磁传感器数据。地磁传感器用于测量设备周围的磁场强度在X、Y、Z三个方向上的分量，适用于指南针、方向检测、金属检测等场景。调用后，系统会按设定频率通过callback持续上报磁场分量数据。 |
| [on_SensorId.MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-onsensoridmagneticfielduncalibrated-f.md#on_sensoridmagnetic_field_uncalibrated) | 订阅未校准地磁传感器数据。未校准地磁传感器与地磁传感器的区别在于，其上报的偏移值(biasX/biasY/biasZ)未经系统校准补偿，适用于需要获取原始磁场数据或自行实现校准算法的场景。 与sensor.on('SensorId.MAGNETIC_FIELD')相比，本接口额外提供偏移值信息，适用于需要分析设备地磁校准偏差的场景。 |
| [on_SensorId.ORIENTATION](arkts-sensorservice-sensor-onsensoridorientation-f.md#on_sensoridorientation) | 订阅方向传感器数据。方向传感器用于测量设备绕Z轴旋转的角度(alpha)、绕X轴旋转的角度(beta)和绕Y轴旋转的角度(gamma)，适用于屏幕旋转、指南针、姿态感知等场景。 调用后，系统会按设定频率通过callback持续上报方向数据。调用本接口的应用或服务可以通过提示用户使用8字校准法来提高应用获取的方向传感器的精度，此传感器理论误差正负5度，具体的精度根据不同的驱动及算法实现可能存在差异。 |
| [on_SensorId.PEDOMETER](arkts-sensorservice-sensor-onsensoridpedometer-f.md#on_sensoridpedometer) | 订阅计步器传感器数据。计步器传感器用于统计用户的步行步数，适用于运动追踪、健康管理等场景。计步传感器数据上报有一定延迟，延迟时间由具体的实现产品决定。调用后，系统会按设定频率通过callback持续上报步数数据。 |
| [on_SensorId.PEDOMETER_DETECTION](arkts-sensorservice-sensor-onsensoridpedometerdetection-f.md#on_sensoridpedometer_detection) | 订阅计步检测器传感器数据。计步检测器传感器用于检测用户是否发生了计步事件（如迈步动作），适用于需要实时检测步行状态的场景。与sensor.on('SensorId.PEDOMETER')相比，本接口上报的是计步事件标量而非累计步数， 适用于需要检测单步事件的场景。 |
| [on_SensorId.PROXIMITY](arkts-sensorservice-sensor-onsensoridproximity-f.md#on_sensoridproximity) | 订阅接近光传感器数据。接近光传感器用于检测物体与设备的距离状态，常用于通话时自动关闭屏幕以防止误触。当接近光事件被触发得较为频繁时，可通过options参数限定事件上报频率。 调用后，系统会通过callback持续上报接近状态数据。 |
| [on_SensorId.ROTATION_VECTOR](arkts-sensorservice-sensor-onsensoridrotationvector-f.md#on_sensoridrotation_vector) | 订阅旋转矢量传感器数据。旋转矢量传感器用于表示设备的姿态旋转，数据由X、Y、Z分量和标量W组成，可用于设备姿态估计、AR/VR场景等。调用后，系统会按设定频率通过callback持续上报旋转矢量数据。 |
| [on_SensorId.SIGNIFICANT_MOTION](arkts-sensorservice-sensor-onsensoridsignificantmotion-f.md#on_sensoridsignificant_motion) | 订阅有效运动传感器数据，用于检测用户拿起设备、明显移动或剧烈摇晃等有效运动事件。适用于需要根据用户活动状态唤醒设备、启动应用或切换模式的场景。调用后，系统会通过callback持续上报有效运动事件数据。 |
| [on_SensorId.WEAR_DETECTION](arkts-sensorservice-sensor-onsensoridweardetection-f.md#on_sensoridwear_detection) | 订阅佩戴检测传感器数据。佩戴检测传感器用于检测设备是否被用户佩戴，适用于智能手表等可穿戴设备的佩戴状态检测，以便自动切换工作模式。调用后，系统会按设定频率通过callback持续上报佩戴状态数据。 |
| [on_SensorType.SENSOR_TYPE_ID_ACCELEROMETER](arkts-sensorservice-sensor-onsensortypesensortypeidaccelerometer-f.md#on_sensortypesensor_type_id_accelerometer) | 监听加速度传感器的数据变化。适用于需要感知设备运动状态、实现屏幕旋转或游戏操控的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-onsensortypesensortypeidaccelerometeruncalibrated-f.md#on_sensortypesensor_type_id_accelerometer_uncalibrated) | 监听未校准加速度传感器的数据变化。适用于需要获取包含偏差校准数据的加速度原始数据的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT](arkts-sensorservice-sensor-onsensortypesensortypeidambientlight-f.md#on_sensortypesensor_type_id_ambient_light) | 监听环境光传感器的数据变化。适用于需要感知环境光照强度的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-onsensortypesensortypeidambienttemperature-f.md#on_sensortypesensor_type_id_ambient_temperature) | 监听环境温度传感器的数据变化。适用于需要感知环境温度的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_BAROMETER](arkts-sensorservice-sensor-onsensortypesensortypeidbarometer-f.md#on_sensortypesensor_type_id_barometer) | 监听气压计传感器的数据变化。适用于需要感知环境气压的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_GRAVITY](arkts-sensorservice-sensor-onsensortypesensortypeidgravity-f.md#on_sensortypesensor_type_id_gravity) | 监听重力传感器的数据变化。适用于需要感知设备重力方向的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_GYROSCOPE](arkts-sensorservice-sensor-onsensortypesensortypeidgyroscope-f.md#on_sensortypesensor_type_id_gyroscope) | 监听陀螺仪传感器的数据变化。适用于需要感知设备旋转角速度的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-onsensortypesensortypeidgyroscopeuncalibrated-f.md#on_sensortypesensor_type_id_gyroscope_uncalibrated) | 监听未校准陀螺仪传感器的数据变化。适用于需要获取包含偏差校准数据的陀螺仪原始数据的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_HALL](arkts-sensorservice-sensor-onsensortypesensortypeidhall-f.md#on_sensortypesensor_type_id_hall) | 监听霍尔传感器的数据变化。适用于需要检测设备翻盖或磁铁状态的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_HEART_RATE](arkts-sensorservice-sensor-onsensortypesensortypeidheartrate-f.md#on_sensortypesensor_type_id_heart_rate) | 监听心率传感器的数据变化。适用于需要获取用户心率数据的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_HUMIDITY](arkts-sensorservice-sensor-onsensortypesensortypeidhumidity-f.md#on_sensortypesensor_type_id_humidity) | 监听湿度传感器的数据变化。适用于需要感知环境湿度的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION](arkts-sensorservice-sensor-onsensortypesensortypeidlinearacceleration-f.md#on_sensortypesensor_type_id_linear_acceleration) | 监听线性加速度传感器的数据变化。适用于需要获取排除重力影响的线性加速度数据的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD](arkts-sensorservice-sensor-onsensortypesensortypeidmagneticfield-f.md#on_sensortypesensor_type_id_magnetic_field) | 监听磁场传感器的数据变化。适用于需要感知设备周围磁场强度与方向的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-onsensortypesensortypeidmagneticfielduncalibrated-f.md#on_sensortypesensor_type_id_magnetic_field_uncalibrated) | 监听未校准磁场传感器的数据变化。适用于需要获取包含偏差校准数据的磁场原始数据的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_ORIENTATION](arkts-sensorservice-sensor-onsensortypesensortypeidorientation-f.md#on_sensortypesensor_type_id_orientation) | 监听方向传感器的数据变化。适用于需要感知设备姿态方向的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_PEDOMETER](arkts-sensorservice-sensor-onsensortypesensortypeidpedometer-f.md#on_sensortypesensor_type_id_pedometer) | 监听计步传感器的数据变化。适用于需要获取用户步数数据的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION](arkts-sensorservice-sensor-onsensortypesensortypeidpedometerdetection-f.md#on_sensortypesensor_type_id_pedometer_detection) | 监听计步检测传感器的数据变化。适用于需要检测用户是否在行走的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_PROXIMITY](arkts-sensorservice-sensor-onsensortypesensortypeidproximity-f.md#on_sensortypesensor_type_id_proximity) | 监听接近光传感器的数据变化。适用于需要感知设备前方是否有物体靠近的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR](arkts-sensorservice-sensor-onsensortypesensortypeidrotationvector-f.md#on_sensortypesensor_type_id_rotation_vector) | 监听旋转矢量传感器的数据变化。适用于需要感知设备三维空间旋转状态的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION](arkts-sensorservice-sensor-onsensortypesensortypeidsignificantmotion-f.md#on_sensortypesensor_type_id_significant_motion) | 监听有效运动传感器数据变化。适用于需要检测设备是否有显著运动的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_SensorType.SENSOR_TYPE_ID_WEAR_DETECTION](arkts-sensorservice-sensor-onsensortypesensortypeidweardetection-f.md#on_sensortypesensor_type_id_wear_detection) | 监听所佩戴的检测传感器的数据变化。适用于需要检测设备是否被佩戴的场景。如果多次调用该接口，仅最后一次调用生效。 |
| [on_sensorStatusChange](arkts-sensorservice-sensor-onsensorstatuschange-f.md) | 监听传感器上线下线状态的变化，callback返回传感器状态事件数据。适用于需要感知传感器设备动态上下线的场景，如远程传感器连接或断开时自动更新传感器列表或订阅状态。 |
| [onceAccelerometerChange](arkts-sensorservice-sensor-onceaccelerometerchange-f.md) | Subscribe to accelerometer sensor data once, {@code SensorId.ACCELEROMETER}. |
| [onceAccelerometerUncalibratedChange](arkts-sensorservice-sensor-onceaccelerometeruncalibratedchange-f.md) | Subscribe to uncalibrated accelerometer sensor data once, {@code SensorId.ACCELEROMETER_UNCALIBRATED}. |
| [onceAmbientLightChange](arkts-sensorservice-sensor-onceambientlightchange-f.md) | Subscribe to ambient light sensor data once, {@code SensorId.AMBIENT_LIGHT}. |
| [onceAmbientTemperatureChange](arkts-sensorservice-sensor-onceambienttemperaturechange-f.md) | Subscribe to ambient temperature sensor data once, {@code SensorId.AMBIENT_TEMPERATURE}. |
| [onceBarometerChange](arkts-sensorservice-sensor-oncebarometerchange-f.md) | Subscribe to barometer sensor data once, {@code SensorId.BAROMETER}. |
| [onceGravityChange](arkts-sensorservice-sensor-oncegravitychange-f.md) | Subscribe to gravity sensor data once, {@code SensorId.GRAVITY}. |
| [onceGyroscopeChange](arkts-sensorservice-sensor-oncegyroscopechange-f.md) | Subscribe to gyroscope sensor data once, {@code SensorId.GYROSCOPE}. |
| [onceGyroscopeUncalibratedChange](arkts-sensorservice-sensor-oncegyroscopeuncalibratedchange-f.md) | Subscribe to uncalibrated gyroscope sensor data once, {@code SensorId.GYROSCOPE_UNCALIBRATED}. |
| [onceHallChange](arkts-sensorservice-sensor-oncehallchange-f.md) | Subscribe to hall sensor data once, {@code SensorId.HALL}. |
| [onceHeartRateChange](arkts-sensorservice-sensor-onceheartratechange-f.md) | Subscribe to heart rate sensor data once, {@code SensorId.HEART_RATE}. |
| [onceHumidityChange](arkts-sensorservice-sensor-oncehumiditychange-f.md) | Subscribe to humidity sensor data once, {@code SensorId.HUMIDITY}. |
| [onceLinearAccelerometerChange](arkts-sensorservice-sensor-oncelinearaccelerometerchange-f.md) | Subscribe to linear acceleration sensor data once, {@code SensorId.LINEAR_ACCELEROMETER}. |
| [onceMagneticFieldChange](arkts-sensorservice-sensor-oncemagneticfieldchange-f.md) | Subscribe to magnetic field sensor data once, {@code SensorId.MAGNETIC_FIELD}. |
| [onceMagneticFieldUncalibratedChange](arkts-sensorservice-sensor-oncemagneticfielduncalibratedchange-f.md) | Subscribe to uncalibrated magnetic field sensor data once, {@code SensorId.MAGNETIC_FIELD_UNCALIBRATED}. |
| [onceOrientationChange](arkts-sensorservice-sensor-onceorientationchange-f.md) | Subscribe to orientation sensor data once, {@code SensorId.ORIENTATION}. |
| [oncePedometerChange](arkts-sensorservice-sensor-oncepedometerchange-f.md) | Subscribe to pedometer sensor data once, {@code SensorId.PEDOMETER}. |
| [oncePedometerDetectionChange](arkts-sensorservice-sensor-oncepedometerdetectionchange-f.md) | Subscribe to pedometer detection sensor data once, {@code SensorId.PEDOMETER_DETECTION}. |
| [onceProximityChange](arkts-sensorservice-sensor-onceproximitychange-f.md) | Subscribe to proximity sensor data once, {@code SensorId.PROXIMITY}. |
| [onceRotationVectorChange](arkts-sensorservice-sensor-oncerotationvectorchange-f.md) | Subscribe to rotation vector sensor data once, {@code SensorId.ROTATION_VECTOR}. |
| [onceSignificantMotionChange](arkts-sensorservice-sensor-oncesignificantmotionchange-f.md) | Subscribe to significant motion sensor data once, {@code SensorId.SIGNIFICANT_MOTION}. |
| [onceWearDetectionChange](arkts-sensorservice-sensor-onceweardetectionchange-f.md) | Subscribe to wear detection sensor data once, {@code SensorId.WEAR_DETECTION}. |
| [once_SensorId.ACCELEROMETER](arkts-sensorservice-sensor-oncesensoridaccelerometer-f.md#once_sensoridaccelerometer) | 获取一次加速度传感器数据。适用于无需持续监听、仅需一次性获取当前加速度数据的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-oncesensoridaccelerometeruncalibrated-f.md#once_sensoridaccelerometer_uncalibrated) | 获取一次未校准加速度传感器数据。适用于仅需一次性获取原始加速度及偏移数据的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.AMBIENT_LIGHT](arkts-sensorservice-sensor-oncesensoridambientlight-f.md#once_sensoridambient_light) | 获取一次环境光传感器数据。适用于仅需一次性获取当前环境光强度的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-oncesensoridambienttemperature-f.md#once_sensoridambient_temperature) | 获取一次温度传感器数据。适用于仅需一次性获取当前环境温度的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.BAROMETER](arkts-sensorservice-sensor-oncesensoridbarometer-f.md#once_sensoridbarometer) | 获取一次气压计传感器数据。适用于仅需一次性获取当前气压值的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.GRAVITY](arkts-sensorservice-sensor-oncesensoridgravity-f.md#once_sensoridgravity) | 获取一次重力传感器数据。适用于仅需一次性获取当前重力分量的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.GYROSCOPE](arkts-sensorservice-sensor-oncesensoridgyroscope-f.md#once_sensoridgyroscope) | 获取一次陀螺仪传感器数据。适用于仅需一次性获取当前旋转角速度的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-oncesensoridgyroscopeuncalibrated-f.md#once_sensoridgyroscope_uncalibrated) | 获取一次未校准陀螺仪传感器数据。适用于仅需一次性获取原始角速度及偏移数据的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.HALL](arkts-sensorservice-sensor-oncesensoridhall-f.md#once_sensoridhall) | 获取一次霍尔传感器数据。适用于仅需一次性检测当前霍尔状态的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.HEART_RATE](arkts-sensorservice-sensor-oncesensoridheartrate-f.md#once_sensoridheart_rate) | 获取一次心率传感器数据。适用于仅需一次性获取当前心率值的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.HUMIDITY](arkts-sensorservice-sensor-oncesensoridhumidity-f.md#once_sensoridhumidity) | 获取一次湿度传感器数据。适用于仅需一次性获取当前环境湿度的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.LINEAR_ACCELEROMETER](arkts-sensorservice-sensor-oncesensoridlinearaccelerometer-f.md#once_sensoridlinear_accelerometer) | 获取一次线性加速度传感器数据。适用于仅需一次性获取当前线性加速度（不含重力分量）的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.MAGNETIC_FIELD](arkts-sensorservice-sensor-oncesensoridmagneticfield-f.md#once_sensoridmagnetic_field) | 获取一次磁场传感器数据。适用于仅需一次性获取当前磁场分量的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-oncesensoridmagneticfielduncalibrated-f.md#once_sensoridmagnetic_field_uncalibrated) | 获取一次未经校准的磁场传感器数据。适用于仅需一次性获取原始磁场及偏移数据的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.ORIENTATION](arkts-sensorservice-sensor-oncesensoridorientation-f.md#once_sensoridorientation) | 获取一次方向传感器数据。适用于仅需一次性获取当前设备方向的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.PEDOMETER](arkts-sensorservice-sensor-oncesensoridpedometer-f.md#once_sensoridpedometer) | 获取一次计步器传感器数据。计步传感器数据上报有一定延迟，延迟时间由具体的实现产品决定。适用于仅需一次性获取当前步数的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.PEDOMETER_DETECTION](arkts-sensorservice-sensor-oncesensoridpedometerdetection-f.md#once_sensoridpedometer_detection) | 获取一次计步检测器传感器数据。适用于仅需一次性检测计步事件的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.PROXIMITY](arkts-sensorservice-sensor-oncesensoridproximity-f.md#once_sensoridproximity) | 获取一次接近光传感器数据。适用于仅需一次性检测当前接近状态的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.ROTATION_VECTOR](arkts-sensorservice-sensor-oncesensoridrotationvector-f.md#once_sensoridrotation_vector) | 获取一次旋转矢量传感器数据。适用于仅需一次性获取当前设备姿态的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.SIGNIFICANT_MOTION](arkts-sensorservice-sensor-oncesensoridsignificantmotion-f.md#once_sensoridsignificant_motion) | 获取一次有效运动传感器数据。适用于仅需一次性检测有效运动的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorId.WEAR_DETECTION](arkts-sensorservice-sensor-oncesensoridweardetection-f.md#once_sensoridwear_detection) | 获取一次佩戴检测传感器数据。适用于仅需一次性检测佩戴状态的场景。调用后，callback仅触发一次，自动取消订阅。 |
| [once_SensorType.SENSOR_TYPE_ID_ACCELEROMETER](arkts-sensorservice-sensor-oncesensortypesensortypeidaccelerometer-f.md#once_sensortypesensor_type_id_accelerometer) | 监听加速度传感器的数据变化一次。适用于仅需一次性获取当前加速度数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-oncesensortypesensortypeidaccelerometeruncalibrated-f.md#once_sensortypesensor_type_id_accelerometer_uncalibrated) | 监听未校准加速度传感器的数据变化一次。适用于仅需一次性获取当前未校准加速度数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT](arkts-sensorservice-sensor-oncesensortypesensortypeidambientlight-f.md#once_sensortypesensor_type_id_ambient_light) | 监听环境光传感器数据变化一次。适用于仅需一次性获取当前环境光数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-oncesensortypesensortypeidambienttemperature-f.md#once_sensortypesensor_type_id_ambient_temperature) | 监听环境温度传感器数据变化一次。适用于仅需一次性获取当前环境温度数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_BAROMETER](arkts-sensorservice-sensor-oncesensortypesensortypeidbarometer-f.md#once_sensortypesensor_type_id_barometer) | 监听气压计传感器数据变化一次。适用于仅需一次性获取当前气压数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_GRAVITY](arkts-sensorservice-sensor-oncesensortypesensortypeidgravity-f.md#once_sensortypesensor_type_id_gravity) | 监听重力传感器的数据变化一次。适用于仅需一次性获取当前重力数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_GYROSCOPE](arkts-sensorservice-sensor-oncesensortypesensortypeidgyroscope-f.md#once_sensortypesensor_type_id_gyroscope) | 监听陀螺仪传感器的数据变化一次。适用于仅需一次性获取当前陀螺仪数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-oncesensortypesensortypeidgyroscopeuncalibrated-f.md#once_sensortypesensor_type_id_gyroscope_uncalibrated) | 监听未校准陀螺仪传感器的数据变化一次。适用于仅需一次性获取当前未校准陀螺仪数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_HALL](arkts-sensorservice-sensor-oncesensortypesensortypeidhall-f.md#once_sensortypesensor_type_id_hall) | 监听霍尔传感器数据变化一次。适用于仅需一次性获取当前霍尔数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_HEART_RATE](arkts-sensorservice-sensor-oncesensortypesensortypeidheartrate-f.md#once_sensortypesensor_type_id_heart_rate) | 监听心率传感器数据变化一次。适用于仅需一次性获取当前心率数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_HUMIDITY](arkts-sensorservice-sensor-oncesensortypesensortypeidhumidity-f.md#once_sensortypesensor_type_id_humidity) | 监听湿度传感器数据变化一次。适用于仅需一次性获取当前湿度数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION](arkts-sensorservice-sensor-oncesensortypesensortypeidlinearacceleration-f.md#once_sensortypesensor_type_id_linear_acceleration) | 监听线性加速度传感器数据变化一次。适用于仅需一次性获取当前线性加速度数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD](arkts-sensorservice-sensor-oncesensortypesensortypeidmagneticfield-f.md#once_sensortypesensor_type_id_magnetic_field) | 监听磁场传感器数据变化一次。适用于仅需一次性获取当前磁场数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-oncesensortypesensortypeidmagneticfielduncalibrated-f.md#once_sensortypesensor_type_id_magnetic_field_uncalibrated) | 监听未校准磁场传感器数据变化一次。适用于仅需一次性获取当前未校准磁场数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_ORIENTATION](arkts-sensorservice-sensor-oncesensortypesensortypeidorientation-f.md#once_sensortypesensor_type_id_orientation) | 监听方向传感器数据变化一次。适用于仅需一次性获取当前方向数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_PEDOMETER](arkts-sensorservice-sensor-oncesensortypesensortypeidpedometer-f.md#once_sensortypesensor_type_id_pedometer) | 监听计步器传感器数据变化一次。适用于仅需一次性获取当前计步数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION](arkts-sensorservice-sensor-oncesensortypesensortypeidpedometerdetection-f.md#once_sensortypesensor_type_id_pedometer_detection) | 监听计步检测传感器数据变化一次。适用于仅需一次性获取当前计步检测数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_PROXIMITY](arkts-sensorservice-sensor-oncesensortypesensortypeidproximity-f.md#once_sensortypesensor_type_id_proximity) | 监听接近光传感器数据变化一次。适用于仅需一次性获取当前接近光数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR](arkts-sensorservice-sensor-oncesensortypesensortypeidrotationvector-f.md#once_sensortypesensor_type_id_rotation_vector) | 监听旋转矢量传感器数据变化一次。适用于仅需一次性获取当前旋转矢量数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION](arkts-sensorservice-sensor-oncesensortypesensortypeidsignificantmotion-f.md#once_sensortypesensor_type_id_significant_motion) | 监听有效运动传感器的数据变化一次。适用于仅需一次性获取当前有效运动数据的场景。 |
| [once_SensorType.SENSOR_TYPE_ID_WEAR_DETECTION](arkts-sensorservice-sensor-oncesensortypesensortypeidweardetection-f.md#once_sensortypesensor_type_id_wear_detection) | 监听所佩戴的检测传感器的数据变化一次。适用于仅需一次性获取当前佩戴检测数据的场景。 |
| [transformCoordinateSystem](arkts-sensorservice-sensor-transformcoordinatesystem-f.md) | 旋转提供的旋转矩阵，使其可以以不同的方式表示坐标系。使用callback异步回调。 |
| [transformCoordinateSystem](arkts-sensorservice-sensor-transformcoordinatesystem-f.md) | 旋转提供的旋转矩阵，使其可以以不同的方式表示坐标系。使用Promise异步回调。 |
| [transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md) | 根据指定坐标系映射旋转矩阵。使用callback异步回调。 |
| [transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md) | 根据指定坐标系映射旋转矩阵。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offColorChange](arkts-sensorservice-sensor-offcolorchange-f-sys.md) | Unsubscribe to color sensor data, {@code SensorId.COLOR}. |
| [offSarChange](arkts-sensorservice-sensor-offsarchange-f-sys.md) | Unsubscribe to sar sensor data, {@code SensorId.SAR}. |
| [off_SensorId.COLOR](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) | 取消订阅颜色传感器数据。调用后，颜色传感器的回调函数将不再触发。 <br>当开发者不再需要颜色传感器数据时（如页面切换、应用退出），使用此接口取消订阅，以减少系统资源占用。 <br>调用此接口后，之前通过sensor.on(sensor.SensorId.COLOR)注册的回调函数将不再被触发。若传入callback参数，仅取消该指定回调函数的订阅；若不传入callback参数，则取消当前SensorId.COLOR类型的所有回调函数。 需先调用sensor.on(sensor.SensorId.COLOR)订阅后，再调用此接口取消订阅。 |
| [off_SensorId.COLOR](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor-1) | 取消订阅颜色传感器数据。与API version 10的off接口相比，新增sensorInfoParam参数，支持通过指定deviceId和sensorIndex来精确取消订阅某一设备上的特定传感器回调，适用于多设备场景。 <br>当开发者需要取消订阅特定设备上的颜色传感器数据时（如多设备连接场景），使用此接口。不传入sensorInfoParam时，默认取消本地设备（deviceId为-1）上的回调。 <br>调用此接口后，指定设备上的颜色传感器回调函数将不再被触发。若传入callback参数，仅取消该指定回调函数的订阅；若不传入callback参数，则取消指定设备上SensorId.COLOR类型的所有回调函数。 |
| [off_SensorId.SAR](arkts-sensorservice-sensor-offsensoridsar-f-sys.md#off_sensoridsar) | 取消订阅吸收比率传感器数据。调用后，SAR传感器的回调函数将不再触发。 <br>当开发者不再需要SAR传感器数据时（如页面切换、应用退出），使用此接口取消订阅，以减少系统资源占用。 <br>调用此接口后，之前通过sensor.on(sensor.SensorId.SAR)注册的回调函数将不再被触发。若传入callback参数，仅取消该指定回调函数的订阅；若不传入callback参数，则取消当前SensorId.SAR类型的所有回调函数。 需先调用sensor.on(sensor.SensorId.SAR)订阅后，再调用此接口取消订阅。 |
| [off_SensorId.SAR](arkts-sensorservice-sensor-offsensoridsar-f-sys.md#off_sensoridsar-1) | 取消订阅吸收比率传感器数据。与API version 10的off接口相比，新增sensorInfoParam参数，支持通过指定deviceId和sensorIndex来精确取消订阅某一设备上的特定传感器回调，适用于多设备场景。 <br>当开发者需要取消订阅特定设备上的SAR传感器数据时（如多设备连接场景），使用此接口。不传入sensorInfoParam时，默认取消本地设备（deviceId为-1）上的回调。 <br>调用此接口后，指定设备上的SAR传感器回调函数将不再被触发。若传入callback参数，仅取消该指定回调函数的订阅；若不传入callback参数，则取消指定设备上SensorId.SAR类型的所有回调函数。 |
| [onColorChange](arkts-sensorservice-sensor-oncolorchange-f-sys.md) | Subscribe to color sensor data, {@code SensorId.COLOR}. |
| [onSarChange](arkts-sensorservice-sensor-onsarchange-f-sys.md) | Subscribe to SAR sensor data, {@code SensorId.SAR}. |
| [on_SensorId.COLOR](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) | 订阅颜色传感器数据变化。通过回调函数异步上报颜色传感器数据，数据格式为ColorResponse对象，包含lightIntensity（光照强度）和colorTemperature（色温）两个number类型字段。 <br>当开发者需要获取环境光照强度和色温信息以实现屏幕自动亮度调节、拍照色温补偿、环境光线监测等功能时，使用此接口。 <br>该接口为异步回调方式，传感器数据变化时通过callback回调上报，无Promise返回值。 |
| [on_SensorId.SAR](arkts-sensorservice-sensor-onsensoridsar-f-sys.md#on_sensoridsar) | 订阅吸收比率传感器数据变化。通过回调函数异步上报SAR传感器数据，数据格式为SarResponse对象，包含absorptionRatio（吸收率）一个number类型字段。 <br>当开发者需要监测设备电磁波吸收率以实现通信安全监测、辐射检测等功能时，使用此接口。 <br>该接口为异步回调方式，传感器数据变化时通过callback回调上报，无Promise返回值。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccelerometerResponse](arkts-sensorservice-sensor-accelerometerresponse-i.md) | 加速度传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md) | 未校准加速度传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md) | 温度传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [BarometerResponse](arkts-sensorservice-sensor-barometerresponse-i.md) | 气压计传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [CoordinatesOptions](arkts-sensorservice-sensor-coordinatesoptions-i.md) | 设置坐标选项对象，用于指定坐标系的变换方向。 |
| [FusionPressureResponse](arkts-sensorservice-sensor-fusionpressureresponse-i.md) | 融合压力传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [GeomagneticResponse](arkts-sensorservice-sensor-geomagneticresponse-i.md) | 设置地磁响应对象，用于描述指定地理位置的地磁场信息。 |
| [GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md) | 重力传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [GyroscopeResponse](arkts-sensorservice-sensor-gyroscoperesponse-i.md) | 陀螺仪传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md) | 未校准陀螺仪传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [HallResponse](arkts-sensorservice-sensor-hallresponse-i.md) | 霍尔传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [HeartRateResponse](arkts-sensorservice-sensor-heartrateresponse-i.md) | 心率传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md) | 湿度传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [LightResponse](arkts-sensorservice-sensor-lightresponse-i.md) | 环境光传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md) | 线性加速度传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [LocationOptions](arkts-sensorservice-sensor-locationoptions-i.md) | 指示地理位置，用于传入经纬度和海拔信息以计算地磁场。 |
| [MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md) | 磁场传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md) | 未校准磁场传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [Options](arkts-sensorservice-sensor-options-i.md) | 设置传感器上报频率及传感器选择参数。 |
| [OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md) | 方向传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md) | 计步检测传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md) | 计步传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md) | 接近光传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [Response](arkts-sensorservice-sensor-response-i.md) | 传感器数据的时间戳与精度信息基类，所有传感器Response类型均继承于此。 |
| [RotationMatrixResponse](arkts-sensorservice-sensor-rotationmatrixresponse-i.md) | 设置旋转矩阵响应对象，用于描述旋转矩阵和倾斜矩阵的计算结果。 |
| [RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md) | 旋转矢量传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [Sensor](arkts-sensorservice-sensor-sensor-i.md) | 指示传感器信息。 |
| [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 传感器传入设置参数，多传感器情况下通过deviceId、sensorIndex控制指定传感器。 |
| [SensorStatusEvent](arkts-sensorservice-sensor-sensorstatusevent-i.md) | 设备状态变化事件数据，用于描述传感器上下线事件的信息。 |
| [SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md) | 有效运动传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |
| [WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md) | 佩戴检测传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ColorResponse](arkts-sensorservice-sensor-colorresponse-i-sys.md) | 颜色传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。用于表示颜色传感器上报的响应数据，包含光照强度和色温信息。 |
| [SarResponse](arkts-sensorservice-sensor-sarresponse-i-sys.md) | 吸收比率传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。用于表示吸收比率传感器上报的响应数据，包含电磁波吸收率信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SensorAccuracy](arkts-sensorservice-sensor-sensoraccuracy-e.md) | 传感器数据的精度挡位。 |
| [SensorId](arkts-sensorservice-sensor-sensorid-e.md) | 表示当前支持订阅或取消订阅的传感器类型。 |
| [SensorType](arkts-sensorservice-sensor-sensortype-e.md) | 表示要订阅或取消订阅的传感器类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SensorId](arkts-sensorservice-sensor-sensorid-e-sys.md) | 表示当前支持订阅或取消订阅的传感器类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [SensorFrequency](arkts-sensorservice-sensor-sensorfrequency-t.md) | 传感器上报频率模式，提供预定义的频率档位，方便开发者快速设置常用的上报频率。 |

