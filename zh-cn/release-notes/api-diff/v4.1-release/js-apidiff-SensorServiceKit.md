| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace sensor<br>差异内容：declare namespace sensor|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：enum SensorId<br>差异内容：enum SensorId|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：ACCELEROMETER = 1<br>差异内容：ACCELEROMETER = 1|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：GYROSCOPE = 2<br>差异内容：GYROSCOPE = 2|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：AMBIENT_LIGHT = 5<br>差异内容：AMBIENT_LIGHT = 5|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：MAGNETIC_FIELD = 6<br>差异内容：MAGNETIC_FIELD = 6|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：BAROMETER = 8<br>差异内容：BAROMETER = 8|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：HALL = 10<br>差异内容：HALL = 10|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：PROXIMITY = 12<br>差异内容：PROXIMITY = 12|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：HUMIDITY = 13<br>差异内容：HUMIDITY = 13|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：ORIENTATION = 256<br>差异内容：ORIENTATION = 256|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：GRAVITY = 257<br>差异内容：GRAVITY = 257|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：LINEAR_ACCELEROMETER = 258<br>差异内容：LINEAR_ACCELEROMETER = 258|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：ROTATION_VECTOR = 259<br>差异内容：ROTATION_VECTOR = 259|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：AMBIENT_TEMPERATURE = 260<br>差异内容：AMBIENT_TEMPERATURE = 260|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：MAGNETIC_FIELD_UNCALIBRATED = 261<br>差异内容：MAGNETIC_FIELD_UNCALIBRATED = 261|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：GYROSCOPE_UNCALIBRATED = 263<br>差异内容：GYROSCOPE_UNCALIBRATED = 263|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：SIGNIFICANT_MOTION = 264<br>差异内容：SIGNIFICANT_MOTION = 264|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：PEDOMETER_DETECTION = 265<br>差异内容：PEDOMETER_DETECTION = 265|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：PEDOMETER = 266<br>差异内容：PEDOMETER = 266|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：HEART_RATE = 278<br>差异内容：HEART_RATE = 278|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：WEAR_DETECTION = 280<br>差异内容：WEAR_DETECTION = 280|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorId；<br>API声明：ACCELEROMETER_UNCALIBRATED = 281<br>差异内容：ACCELEROMETER_UNCALIBRATED = 281|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.ACCELEROMETER, callback: Callback\<AccelerometerResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.ACCELEROMETER, callback: Callback\<AccelerometerResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback\<AccelerometerUncalibratedResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback\<AccelerometerUncalibratedResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.AMBIENT_LIGHT, callback: Callback\<LightResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.AMBIENT_LIGHT, callback: Callback\<LightResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback\<AmbientTemperatureResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback\<AmbientTemperatureResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.BAROMETER, callback: Callback\<BarometerResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.BAROMETER, callback: Callback\<BarometerResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.GRAVITY, callback: Callback\<GravityResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.GRAVITY, callback: Callback\<GravityResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.GYROSCOPE, callback: Callback\<GyroscopeResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.GYROSCOPE, callback: Callback\<GyroscopeResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback\<GyroscopeUncalibratedResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback\<GyroscopeUncalibratedResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.HALL, callback: Callback\<HallResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.HALL, callback: Callback\<HallResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.HEART_RATE, callback: Callback\<HeartRateResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.HEART_RATE, callback: Callback\<HeartRateResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.HUMIDITY, callback: Callback\<HumidityResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.HUMIDITY, callback: Callback\<HumidityResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback\<LinearAccelerometerResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback\<LinearAccelerometerResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.MAGNETIC_FIELD, callback: Callback\<MagneticFieldResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.MAGNETIC_FIELD, callback: Callback\<MagneticFieldResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback\<MagneticFieldUncalibratedResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback\<MagneticFieldUncalibratedResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.ORIENTATION, callback: Callback\<OrientationResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.ORIENTATION, callback: Callback\<OrientationResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.PEDOMETER, callback: Callback\<PedometerResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.PEDOMETER, callback: Callback\<PedometerResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.PEDOMETER_DETECTION, callback: Callback\<PedometerDetectionResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.PEDOMETER_DETECTION, callback: Callback\<PedometerDetectionResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.PROXIMITY, callback: Callback\<ProximityResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.PROXIMITY, callback: Callback\<ProximityResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.ROTATION_VECTOR, callback: Callback\<RotationVectorResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.ROTATION_VECTOR, callback: Callback\<RotationVectorResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.SIGNIFICANT_MOTION, callback: Callback\<SignificantMotionResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.SIGNIFICANT_MOTION, callback: Callback\<SignificantMotionResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorId.WEAR_DETECTION, callback: Callback\<WearDetectionResponse>, options?: Options): void;<br>差异内容：function on(type: SensorId.WEAR_DETECTION, callback: Callback\<WearDetectionResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.ACCELEROMETER, callback: Callback\<AccelerometerResponse>): void;<br>差异内容：function once(type: SensorId.ACCELEROMETER, callback: Callback\<AccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback\<AccelerometerUncalibratedResponse>): void;<br>差异内容：function once(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback\<AccelerometerUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.AMBIENT_LIGHT, callback: Callback\<LightResponse>): void;<br>差异内容：function once(type: SensorId.AMBIENT_LIGHT, callback: Callback\<LightResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback\<AmbientTemperatureResponse>): void;<br>差异内容：function once(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback\<AmbientTemperatureResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.BAROMETER, callback: Callback\<BarometerResponse>): void;<br>差异内容：function once(type: SensorId.BAROMETER, callback: Callback\<BarometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.GRAVITY, callback: Callback\<GravityResponse>): void;<br>差异内容：function once(type: SensorId.GRAVITY, callback: Callback\<GravityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.GYROSCOPE, callback: Callback\<GyroscopeResponse>): void;<br>差异内容：function once(type: SensorId.GYROSCOPE, callback: Callback\<GyroscopeResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback\<GyroscopeUncalibratedResponse>): void;<br>差异内容：function once(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback\<GyroscopeUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.HALL, callback: Callback\<HallResponse>): void;<br>差异内容：function once(type: SensorId.HALL, callback: Callback\<HallResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.HEART_RATE, callback: Callback\<HeartRateResponse>): void;<br>差异内容：function once(type: SensorId.HEART_RATE, callback: Callback\<HeartRateResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.HUMIDITY, callback: Callback\<HumidityResponse>): void;<br>差异内容：function once(type: SensorId.HUMIDITY, callback: Callback\<HumidityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback\<LinearAccelerometerResponse>): void;<br>差异内容：function once(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback\<LinearAccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.MAGNETIC_FIELD, callback: Callback\<MagneticFieldResponse>): void;<br>差异内容：function once(type: SensorId.MAGNETIC_FIELD, callback: Callback\<MagneticFieldResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback\<MagneticFieldUncalibratedResponse>): void;<br>差异内容：function once(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback\<MagneticFieldUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.ORIENTATION, callback: Callback\<OrientationResponse>): void;<br>差异内容：function once(type: SensorId.ORIENTATION, callback: Callback\<OrientationResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.PEDOMETER, callback: Callback\<PedometerResponse>): void;<br>差异内容：function once(type: SensorId.PEDOMETER, callback: Callback\<PedometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.PEDOMETER_DETECTION, callback: Callback\<PedometerDetectionResponse>): void;<br>差异内容：function once(type: SensorId.PEDOMETER_DETECTION, callback: Callback\<PedometerDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.PROXIMITY, callback: Callback\<ProximityResponse>): void;<br>差异内容：function once(type: SensorId.PROXIMITY, callback: Callback\<ProximityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.ROTATION_VECTOR, callback: Callback\<RotationVectorResponse>): void;<br>差异内容：function once(type: SensorId.ROTATION_VECTOR, callback: Callback\<RotationVectorResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.SIGNIFICANT_MOTION, callback: Callback\<SignificantMotionResponse>): void;<br>差异内容：function once(type: SensorId.SIGNIFICANT_MOTION, callback: Callback\<SignificantMotionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorId.WEAR_DETECTION, callback: Callback\<WearDetectionResponse>): void;<br>差异内容：function once(type: SensorId.WEAR_DETECTION, callback: Callback\<WearDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.ACCELEROMETER, callback?: Callback\<AccelerometerResponse>): void;<br>差异内容：function off(type: SensorId.ACCELEROMETER, callback?: Callback\<AccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback?: Callback\<AccelerometerUncalibratedResponse>): void;<br>差异内容：function off(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback?: Callback\<AccelerometerUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.AMBIENT_LIGHT, callback?: Callback\<LightResponse>): void;<br>差异内容：function off(type: SensorId.AMBIENT_LIGHT, callback?: Callback\<LightResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.AMBIENT_TEMPERATURE, callback?: Callback\<AmbientTemperatureResponse>): void;<br>差异内容：function off(type: SensorId.AMBIENT_TEMPERATURE, callback?: Callback\<AmbientTemperatureResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.BAROMETER, callback?: Callback\<BarometerResponse>): void;<br>差异内容：function off(type: SensorId.BAROMETER, callback?: Callback\<BarometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.GRAVITY, callback?: Callback\<GravityResponse>): void;<br>差异内容：function off(type: SensorId.GRAVITY, callback?: Callback\<GravityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.GYROSCOPE, callback?: Callback\<GyroscopeResponse>): void;<br>差异内容：function off(type: SensorId.GYROSCOPE, callback?: Callback\<GyroscopeResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.GYROSCOPE_UNCALIBRATED, callback?: Callback\<GyroscopeUncalibratedResponse>): void;<br>差异内容：function off(type: SensorId.GYROSCOPE_UNCALIBRATED, callback?: Callback\<GyroscopeUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.HALL, callback?: Callback\<HallResponse>): void;<br>差异内容：function off(type: SensorId.HALL, callback?: Callback\<HallResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.HEART_RATE, callback?: Callback\<HeartRateResponse>): void;<br>差异内容：function off(type: SensorId.HEART_RATE, callback?: Callback\<HeartRateResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.HUMIDITY, callback?: Callback\<HumidityResponse>): void;<br>差异内容：function off(type: SensorId.HUMIDITY, callback?: Callback\<HumidityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.LINEAR_ACCELEROMETER, callback?: Callback\<LinearAccelerometerResponse>): void;<br>差异内容：function off(type: SensorId.LINEAR_ACCELEROMETER, callback?: Callback\<LinearAccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.MAGNETIC_FIELD, callback?: Callback\<MagneticFieldResponse>): void;<br>差异内容：function off(type: SensorId.MAGNETIC_FIELD, callback?: Callback\<MagneticFieldResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback\<MagneticFieldUncalibratedResponse>): void;<br>差异内容：function off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback\<MagneticFieldUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.ORIENTATION, callback?: Callback\<OrientationResponse>): void;<br>差异内容：function off(type: SensorId.ORIENTATION, callback?: Callback\<OrientationResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.PEDOMETER, callback?: Callback\<PedometerResponse>): void;<br>差异内容：function off(type: SensorId.PEDOMETER, callback?: Callback\<PedometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.PEDOMETER_DETECTION, callback?: Callback\<PedometerDetectionResponse>): void;<br>差异内容：function off(type: SensorId.PEDOMETER_DETECTION, callback?: Callback\<PedometerDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.PROXIMITY, callback?: Callback\<ProximityResponse>): void;<br>差异内容：function off(type: SensorId.PROXIMITY, callback?: Callback\<ProximityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.ROTATION_VECTOR, callback?: Callback\<RotationVectorResponse>): void;<br>差异内容：function off(type: SensorId.ROTATION_VECTOR, callback?: Callback\<RotationVectorResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.SIGNIFICANT_MOTION, callback?: Callback\<SignificantMotionResponse>): void;<br>差异内容：function off(type: SensorId.SIGNIFICANT_MOTION, callback?: Callback\<SignificantMotionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.WEAR_DETECTION, callback?: Callback\<WearDetectionResponse>): void;<br>差异内容：function off(type: SensorId.WEAR_DETECTION, callback?: Callback\<WearDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback\<AccelerometerResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback\<AccelerometerResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback\<AccelerometerUncalibratedResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback\<AccelerometerUncalibratedResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback\<LightResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback\<LightResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback\<AmbientTemperatureResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback\<AmbientTemperatureResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback\<BarometerResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback\<BarometerResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback\<GravityResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback\<GravityResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback\<GyroscopeResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback\<GyroscopeResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback: Callback\<GyroscopeUncalibratedResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback: Callback\<GyroscopeUncalibratedResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback\<HallResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback\<HallResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback\<HeartRateResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback\<HeartRateResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback\<HumidityResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback\<HumidityResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback\<LinearAccelerometerResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback\<LinearAccelerometerResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback\<MagneticFieldResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback\<MagneticFieldResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback\<MagneticFieldUncalibratedResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback\<MagneticFieldUncalibratedResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback\<OrientationResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback\<OrientationResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback\<PedometerResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback\<PedometerResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback\<PedometerDetectionResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback\<PedometerDetectionResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback\<ProximityResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback\<ProximityResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback\<RotationVectorResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback\<RotationVectorResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback\<SignificantMotionResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback\<SignificantMotionResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback\<WearDetectionResponse>, options?: Options): void;<br>差异内容：function on(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback\<WearDetectionResponse>, options?: Options): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback\<AccelerometerResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback\<AccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback\<AccelerometerUncalibratedResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback\<AccelerometerUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback\<LightResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback\<LightResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback\<AmbientTemperatureResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback\<AmbientTemperatureResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback\<BarometerResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback\<BarometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback\<GravityResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback\<GravityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback\<GyroscopeResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback\<GyroscopeResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback: Callback\<GyroscopeUncalibratedResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback: Callback\<GyroscopeUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback\<HallResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback\<HallResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback\<HeartRateResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback\<HeartRateResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback\<HumidityResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback\<HumidityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback\<LinearAccelerometerResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback\<LinearAccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback\<MagneticFieldResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback\<MagneticFieldResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback\<MagneticFieldUncalibratedResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback\<MagneticFieldUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback\<OrientationResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback\<OrientationResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback\<PedometerResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback\<PedometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback\<PedometerDetectionResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback\<PedometerDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback\<ProximityResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback\<ProximityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback\<RotationVectorResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback\<RotationVectorResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback\<SignificantMotionResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback\<SignificantMotionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function once(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback\<WearDetectionResponse>): void;<br>差异内容：function once(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback\<WearDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback\<AccelerometerResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback\<AccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback?: Callback\<AccelerometerUncalibratedResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback?: Callback\<AccelerometerUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback?: Callback\<LightResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback?: Callback\<LightResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback?: Callback\<AmbientTemperatureResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback?: Callback\<AmbientTemperatureResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback?: Callback\<BarometerResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback?: Callback\<BarometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback?: Callback\<GravityResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback?: Callback\<GravityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback?: Callback\<GyroscopeResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback?: Callback\<GyroscopeResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback?: Callback\<GyroscopeUncalibratedResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback?: Callback\<GyroscopeUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_HALL, callback?: Callback\<HallResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_HALL, callback?: Callback\<HallResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback\<HeartRateResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback\<HeartRateResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback?: Callback\<HumidityResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback?: Callback\<HumidityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback?: Callback\<LinearAccelerometerResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback?: Callback\<LinearAccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback?: Callback\<MagneticFieldResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback?: Callback\<MagneticFieldResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback\<MagneticFieldUncalibratedResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback\<MagneticFieldUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback?: Callback\<OrientationResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback?: Callback\<OrientationResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback?: Callback\<PedometerResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback?: Callback\<PedometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback?: Callback\<PedometerDetectionResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback?: Callback\<PedometerDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback?: Callback\<ProximityResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback?: Callback\<ProximityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback?: Callback\<RotationVectorResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback?: Callback\<RotationVectorResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback?: Callback\<SignificantMotionResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback?: Callback\<SignificantMotionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback?: Callback\<WearDetectionResponse>): void;<br>差异内容：function off(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback?: Callback\<WearDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface Sensor<br>差异内容：interface Sensor|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：sensorName: string;<br>差异内容：sensorName: string;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：vendorName: string;<br>差异内容：vendorName: string;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：firmwareVersion: string;<br>差异内容：firmwareVersion: string;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：hardwareVersion: string;<br>差异内容：hardwareVersion: string;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：sensorId: number;<br>差异内容：sensorId: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：maxRange: number;<br>差异内容：maxRange: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：minSamplePeriod: number;<br>差异内容：minSamplePeriod: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：maxSamplePeriod: number;<br>差异内容：maxSamplePeriod: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：precision: number;<br>差异内容：precision: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：power: number;<br>差异内容：power: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getSingleSensor(type: SensorId, callback: AsyncCallback\<Sensor>): void;<br>差异内容：function getSingleSensor(type: SensorId, callback: AsyncCallback\<Sensor>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getSingleSensor(type: SensorId): Promise\<Sensor>;<br>差异内容：function getSingleSensor(type: SensorId): Promise\<Sensor>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getSensorList(callback: AsyncCallback\<Array\<Sensor>>): void;<br>差异内容：function getSensorList(callback: AsyncCallback\<Array\<Sensor>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getSensorList(): Promise\<Array\<Sensor>>;<br>差异内容：function getSensorList(): Promise\<Array\<Sensor>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface GeomagneticResponse<br>差异内容：interface GeomagneticResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GeomagneticResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GeomagneticResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GeomagneticResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GeomagneticResponse；<br>API声明：geomagneticDip: number;<br>差异内容：geomagneticDip: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GeomagneticResponse；<br>API声明：deflectionAngle: number;<br>差异内容：deflectionAngle: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GeomagneticResponse；<br>API声明：levelIntensity: number;<br>差异内容：levelIntensity: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GeomagneticResponse；<br>API声明：totalIntensity: number;<br>差异内容：totalIntensity: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface LocationOptions<br>差异内容：interface LocationOptions|api/@ohos.sensor.d.ts|
|新增API|NA|类名：LocationOptions；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：LocationOptions；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：LocationOptions；<br>API声明：altitude: number;<br>差异内容：altitude: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getGeomagneticField(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback\<GeomagneticResponse>): void;<br>差异内容：function getGeomagneticField(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback\<GeomagneticResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getGeomagneticField(locationOptions: LocationOptions, timeMillis: number): Promise\<GeomagneticResponse>;<br>差异内容：function getGeomagneticField(locationOptions: LocationOptions, timeMillis: number): Promise\<GeomagneticResponse>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback\<GeomagneticResponse>): void;<br>差异内容：function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback\<GeomagneticResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number): Promise\<GeomagneticResponse>;<br>差异内容：function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number): Promise\<GeomagneticResponse>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback\<number>): void;<br>差异内容：function getAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback\<number>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getAltitude(seaPressure: number, currentPressure: number): Promise\<number>;<br>差异内容：function getAltitude(seaPressure: number, currentPressure: number): Promise\<number>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getDeviceAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback\<number>): void;<br>差异内容：function getDeviceAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback\<number>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getDeviceAltitude(seaPressure: number, currentPressure: number): Promise\<number>;<br>差异内容：function getDeviceAltitude(seaPressure: number, currentPressure: number): Promise\<number>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getGeomagneticDip(inclinationMatrix: Array\<number>, callback: AsyncCallback\<number>): void;<br>差异内容：function getGeomagneticDip(inclinationMatrix: Array\<number>, callback: AsyncCallback\<number>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getGeomagneticDip(inclinationMatrix: Array\<number>): Promise\<number>;<br>差异内容：function getGeomagneticDip(inclinationMatrix: Array\<number>): Promise\<number>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getInclination(inclinationMatrix: Array\<number>, callback: AsyncCallback\<number>): void;<br>差异内容：function getInclination(inclinationMatrix: Array\<number>, callback: AsyncCallback\<number>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getInclination(inclinationMatrix: Array\<number>): Promise\<number>;<br>差异内容：function getInclination(inclinationMatrix: Array\<number>): Promise\<number>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getAngleModify(currentRotationMatrix: Array\<number>, preRotationMatrix: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function getAngleModify(currentRotationMatrix: Array\<number>, preRotationMatrix: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getAngleModify(currentRotationMatrix: Array\<number>, preRotationMatrix: Array\<number>): Promise\<Array\<number>>;<br>差异内容：function getAngleModify(currentRotationMatrix: Array\<number>, preRotationMatrix: Array\<number>): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getAngleVariation(currentRotationMatrix: Array\<number>, preRotationMatrix: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function getAngleVariation(currentRotationMatrix: Array\<number>, preRotationMatrix: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getAngleVariation(currentRotationMatrix: Array\<number>, preRotationMatrix: Array\<number>): Promise\<Array\<number>>;<br>差异内容：function getAngleVariation(currentRotationMatrix: Array\<number>, preRotationMatrix: Array\<number>): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function createRotationMatrix(rotationVector: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function createRotationMatrix(rotationVector: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function createRotationMatrix(rotationVector: Array\<number>): Promise\<Array\<number>>;<br>差异内容：function createRotationMatrix(rotationVector: Array\<number>): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function createRotationMatrix(gravity: Array\<number>, geomagnetic: Array\<number>, callback: AsyncCallback\<RotationMatrixResponse>): void;<br>差异内容：function createRotationMatrix(gravity: Array\<number>, geomagnetic: Array\<number>, callback: AsyncCallback\<RotationMatrixResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function createRotationMatrix(gravity: Array\<number>, geomagnetic: Array\<number>): Promise\<RotationMatrixResponse>;<br>差异内容：function createRotationMatrix(gravity: Array\<number>, geomagnetic: Array\<number>): Promise\<RotationMatrixResponse>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getRotationMatrix(rotationVector: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function getRotationMatrix(rotationVector: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getRotationMatrix(rotationVector: Array\<number>): Promise\<Array\<number>>;<br>差异内容：function getRotationMatrix(rotationVector: Array\<number>): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getRotationMatrix(gravity: Array\<number>, geomagnetic: Array\<number>, callback: AsyncCallback\<RotationMatrixResponse>): void;<br>差异内容：function getRotationMatrix(gravity: Array\<number>, geomagnetic: Array\<number>, callback: AsyncCallback\<RotationMatrixResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getRotationMatrix(gravity: Array\<number>, geomagnetic: Array\<number>): Promise\<RotationMatrixResponse>;<br>差异内容：function getRotationMatrix(gravity: Array\<number>, geomagnetic: Array\<number>): Promise\<RotationMatrixResponse>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface CoordinatesOptions<br>差异内容：interface CoordinatesOptions|api/@ohos.sensor.d.ts|
|新增API|NA|类名：CoordinatesOptions；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：CoordinatesOptions；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function transformCoordinateSystem(inRotationVector: Array\<number>, coordinates: CoordinatesOptions, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function transformCoordinateSystem(inRotationVector: Array\<number>, coordinates: CoordinatesOptions, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function transformCoordinateSystem(inRotationVector: Array\<number>, coordinates: CoordinatesOptions): Promise\<Array\<number>>;<br>差异内容：function transformCoordinateSystem(inRotationVector: Array\<number>, coordinates: CoordinatesOptions): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function transformRotationMatrix(inRotationVector: Array\<number>, coordinates: CoordinatesOptions, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function transformRotationMatrix(inRotationVector: Array\<number>, coordinates: CoordinatesOptions, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function transformRotationMatrix(inRotationVector: Array\<number>, coordinates: CoordinatesOptions): Promise\<Array\<number>>;<br>差异内容：function transformRotationMatrix(inRotationVector: Array\<number>, coordinates: CoordinatesOptions): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function createQuaternion(rotationVector: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function createQuaternion(rotationVector: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function createQuaternion(rotationVector: Array\<number>): Promise\<Array\<number>>;<br>差异内容：function createQuaternion(rotationVector: Array\<number>): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getQuaternion(rotationVector: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function getQuaternion(rotationVector: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getQuaternion(rotationVector: Array\<number>): Promise\<Array\<number>>;<br>差异内容：function getQuaternion(rotationVector: Array\<number>): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getDirection(rotationMatrix: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function getDirection(rotationMatrix: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getDirection(rotationMatrix: Array\<number>): Promise\<Array\<number>>;<br>差异内容：function getDirection(rotationMatrix: Array\<number>): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getOrientation(rotationMatrix: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：function getOrientation(rotationMatrix: Array\<number>, callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getOrientation(rotationMatrix: Array\<number>): Promise\<Array\<number>>;<br>差异内容：function getOrientation(rotationMatrix: Array\<number>): Promise\<Array\<number>>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface RotationMatrixResponse<br>差异内容：interface RotationMatrixResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：RotationMatrixResponse；<br>API声明：rotation: Array\<number>;<br>差异内容：rotation: Array\<number>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：RotationMatrixResponse；<br>API声明：inclination: Array\<number>;<br>差异内容：inclination: Array\<number>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface Options<br>差异内容：interface Options|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Options；<br>API声明：interval?: number \| SensorFrequency;<br>差异内容：interval?: number \| SensorFrequency;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：type SensorFrequency = 'game' \| 'ui' \| 'normal';<br>差异内容：type SensorFrequency = 'game' \| 'ui' \| 'normal';|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：enum SensorType<br>差异内容：enum SensorType|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_ACCELEROMETER = 1<br>差异内容：SENSOR_TYPE_ID_ACCELEROMETER = 1|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_GYROSCOPE = 2<br>差异内容：SENSOR_TYPE_ID_GYROSCOPE = 2|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_AMBIENT_LIGHT = 5<br>差异内容：SENSOR_TYPE_ID_AMBIENT_LIGHT = 5|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_MAGNETIC_FIELD = 6<br>差异内容：SENSOR_TYPE_ID_MAGNETIC_FIELD = 6|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_BAROMETER = 8<br>差异内容：SENSOR_TYPE_ID_BAROMETER = 8|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_HALL = 10<br>差异内容：SENSOR_TYPE_ID_HALL = 10|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_PROXIMITY = 12<br>差异内容：SENSOR_TYPE_ID_PROXIMITY = 12|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_HUMIDITY = 13<br>差异内容：SENSOR_TYPE_ID_HUMIDITY = 13|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_ORIENTATION = 256<br>差异内容：SENSOR_TYPE_ID_ORIENTATION = 256|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_GRAVITY = 257<br>差异内容：SENSOR_TYPE_ID_GRAVITY = 257|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_LINEAR_ACCELERATION = 258<br>差异内容：SENSOR_TYPE_ID_LINEAR_ACCELERATION = 258|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_ROTATION_VECTOR = 259<br>差异内容：SENSOR_TYPE_ID_ROTATION_VECTOR = 259|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_AMBIENT_TEMPERATURE = 260<br>差异内容：SENSOR_TYPE_ID_AMBIENT_TEMPERATURE = 260|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED = 261<br>差异内容：SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED = 261|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED = 263<br>差异内容：SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED = 263|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_SIGNIFICANT_MOTION = 264<br>差异内容：SENSOR_TYPE_ID_SIGNIFICANT_MOTION = 264|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_PEDOMETER_DETECTION = 265<br>差异内容：SENSOR_TYPE_ID_PEDOMETER_DETECTION = 265|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_PEDOMETER = 266<br>差异内容：SENSOR_TYPE_ID_PEDOMETER = 266|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_HEART_RATE = 278<br>差异内容：SENSOR_TYPE_ID_HEART_RATE = 278|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_WEAR_DETECTION = 280<br>差异内容：SENSOR_TYPE_ID_WEAR_DETECTION = 280|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorType；<br>API声明：SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED = 281<br>差异内容：SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED = 281|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：enum SensorAccuracy<br>差异内容：enum SensorAccuracy|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorAccuracy；<br>API声明：ACCURACY_UNRELIABLE = 0<br>差异内容：ACCURACY_UNRELIABLE = 0|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorAccuracy；<br>API声明：ACCURACY_LOW = 1<br>差异内容：ACCURACY_LOW = 1|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorAccuracy；<br>API声明：ACCURACY_MEDIUM = 2<br>差异内容：ACCURACY_MEDIUM = 2|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorAccuracy；<br>API声明：ACCURACY_HIGH = 3<br>差异内容：ACCURACY_HIGH = 3|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface Response<br>差异内容：interface Response|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Response；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Response；<br>API声明：accuracy: SensorAccuracy;<br>差异内容：accuracy: SensorAccuracy;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface AccelerometerResponse<br>差异内容：interface AccelerometerResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AccelerometerResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AccelerometerResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AccelerometerResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface LinearAccelerometerResponse<br>差异内容：interface LinearAccelerometerResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：LinearAccelerometerResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：LinearAccelerometerResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：LinearAccelerometerResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface AccelerometerUncalibratedResponse<br>差异内容：interface AccelerometerUncalibratedResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AccelerometerUncalibratedResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AccelerometerUncalibratedResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AccelerometerUncalibratedResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AccelerometerUncalibratedResponse；<br>API声明：biasX: number;<br>差异内容：biasX: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AccelerometerUncalibratedResponse；<br>API声明：biasY: number;<br>差异内容：biasY: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AccelerometerUncalibratedResponse；<br>API声明：biasZ: number;<br>差异内容：biasZ: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface GravityResponse<br>差异内容：interface GravityResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GravityResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GravityResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GravityResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface OrientationResponse<br>差异内容：interface OrientationResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：OrientationResponse；<br>API声明：alpha: number;<br>差异内容：alpha: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：OrientationResponse；<br>API声明：beta: number;<br>差异内容：beta: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：OrientationResponse；<br>API声明：gamma: number;<br>差异内容：gamma: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface RotationVectorResponse<br>差异内容：interface RotationVectorResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：RotationVectorResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：RotationVectorResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：RotationVectorResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：RotationVectorResponse；<br>API声明：w: number;<br>差异内容：w: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface GyroscopeResponse<br>差异内容：interface GyroscopeResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GyroscopeResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GyroscopeResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GyroscopeResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface GyroscopeUncalibratedResponse<br>差异内容：interface GyroscopeUncalibratedResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GyroscopeUncalibratedResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GyroscopeUncalibratedResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GyroscopeUncalibratedResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GyroscopeUncalibratedResponse；<br>API声明：biasX: number;<br>差异内容：biasX: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GyroscopeUncalibratedResponse；<br>API声明：biasY: number;<br>差异内容：biasY: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：GyroscopeUncalibratedResponse；<br>API声明：biasZ: number;<br>差异内容：biasZ: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface SignificantMotionResponse<br>差异内容：interface SignificantMotionResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SignificantMotionResponse；<br>API声明：scalar: number;<br>差异内容：scalar: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface ProximityResponse<br>差异内容：interface ProximityResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：ProximityResponse；<br>API声明：distance: number;<br>差异内容：distance: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface LightResponse<br>差异内容：interface LightResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：LightResponse；<br>API声明：intensity: number;<br>差异内容：intensity: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface HallResponse<br>差异内容：interface HallResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：HallResponse；<br>API声明：status: number;<br>差异内容：status: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface MagneticFieldResponse<br>差异内容：interface MagneticFieldResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：MagneticFieldResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：MagneticFieldResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：MagneticFieldResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface MagneticFieldUncalibratedResponse<br>差异内容：interface MagneticFieldUncalibratedResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：MagneticFieldUncalibratedResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：MagneticFieldUncalibratedResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：MagneticFieldUncalibratedResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：MagneticFieldUncalibratedResponse；<br>API声明：biasX: number;<br>差异内容：biasX: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：MagneticFieldUncalibratedResponse；<br>API声明：biasY: number;<br>差异内容：biasY: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：MagneticFieldUncalibratedResponse；<br>API声明：biasZ: number;<br>差异内容：biasZ: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface PedometerResponse<br>差异内容：interface PedometerResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：PedometerResponse；<br>API声明：steps: number;<br>差异内容：steps: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface HumidityResponse<br>差异内容：interface HumidityResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：HumidityResponse；<br>API声明：humidity: number;<br>差异内容：humidity: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface PedometerDetectionResponse<br>差异内容：interface PedometerDetectionResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：PedometerDetectionResponse；<br>API声明：scalar: number;<br>差异内容：scalar: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface AmbientTemperatureResponse<br>差异内容：interface AmbientTemperatureResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：AmbientTemperatureResponse；<br>API声明：temperature: number;<br>差异内容：temperature: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface BarometerResponse<br>差异内容：interface BarometerResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：BarometerResponse；<br>API声明：pressure: number;<br>差异内容：pressure: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface HeartRateResponse<br>差异内容：interface HeartRateResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：HeartRateResponse；<br>API声明：heartRate: number;<br>差异内容：heartRate: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface WearDetectionResponse<br>差异内容：interface WearDetectionResponse|api/@ohos.sensor.d.ts|
|新增API|NA|类名：WearDetectionResponse；<br>API声明：value: number;<br>差异内容：value: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace vibrator<br>差异内容：declare namespace vibrator|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function vibrate(duration: number, callback?: AsyncCallback\<void>): void;<br>差异内容：function vibrate(duration: number, callback?: AsyncCallback\<void>): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function vibrate(duration: number): Promise\<void>;<br>差异内容：function vibrate(duration: number): Promise\<void>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function vibrate(effectId: EffectId): Promise\<void>;<br>差异内容：function vibrate(effectId: EffectId): Promise\<void>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function vibrate(effectId: EffectId, callback?: AsyncCallback\<void>): void;<br>差异内容：function vibrate(effectId: EffectId, callback?: AsyncCallback\<void>): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function startVibration(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback\<void>): void;<br>差异内容：function startVibration(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback\<void>): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function startVibration(effect: VibrateEffect, attribute: VibrateAttribute): Promise\<void>;<br>差异内容：function startVibration(effect: VibrateEffect, attribute: VibrateAttribute): Promise\<void>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function stopVibration(stopMode: VibratorStopMode): Promise\<void>;<br>差异内容：function stopVibration(stopMode: VibratorStopMode): Promise\<void>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function stopVibration(stopMode: VibratorStopMode, callback: AsyncCallback\<void>): void;<br>差异内容：function stopVibration(stopMode: VibratorStopMode, callback: AsyncCallback\<void>): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function stopVibration(callback: AsyncCallback\<void>): void;<br>差异内容：function stopVibration(callback: AsyncCallback\<void>): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function stopVibration(): Promise\<void>;<br>差异内容：function stopVibration(): Promise\<void>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function isSupportEffect(effectId: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isSupportEffect(effectId: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function isSupportEffect(effectId: string): Promise\<boolean>;<br>差异内容：function isSupportEffect(effectId: string): Promise\<boolean>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function stop(stopMode: VibratorStopMode): Promise\<void>;<br>差异内容：function stop(stopMode: VibratorStopMode): Promise\<void>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function stop(stopMode: VibratorStopMode, callback?: AsyncCallback\<void>): void;<br>差异内容：function stop(stopMode: VibratorStopMode, callback?: AsyncCallback\<void>): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：enum EffectId<br>差异内容：enum EffectId|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：EffectId；<br>API声明：EFFECT_CLOCK_TIMER = 'haptic.clock.timer'<br>差异内容：EFFECT_CLOCK_TIMER = 'haptic.clock.timer'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：enum VibratorStopMode<br>差异内容：enum VibratorStopMode|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorStopMode；<br>API声明：VIBRATOR_STOP_MODE_TIME = 'time'<br>差异内容：VIBRATOR_STOP_MODE_TIME = 'time'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorStopMode；<br>API声明：VIBRATOR_STOP_MODE_PRESET = 'preset'<br>差异内容：VIBRATOR_STOP_MODE_PRESET = 'preset'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：type Usage = 'unknown' \| 'alarm' \| 'ring' \| 'notification' \| 'communication' \| 'touch' \| 'media' \| 'physicalFeedback' \| 'simulateReality';<br>差异内容：type Usage = 'unknown' \| 'alarm' \| 'ring' \| 'notification' \| 'communication' \| 'touch' \| 'media' \| 'physicalFeedback' \| 'simulateReality';|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibrateAttribute<br>差异内容：interface VibrateAttribute|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibrateAttribute；<br>API声明：id?: number;<br>差异内容：id?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibrateAttribute；<br>API声明：usage: Usage;<br>差异内容：usage: Usage;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：type VibrateEffect = VibrateTime \| VibratePreset \| VibrateFromFile;<br>差异内容：type VibrateEffect = VibrateTime \| VibratePreset \| VibrateFromFile;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibrateTime<br>差异内容：interface VibrateTime|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibrateTime；<br>API声明：type: 'time';<br>差异内容：type: 'time';|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibrateTime；<br>API声明：duration: number;<br>差异内容：duration: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibratePreset<br>差异内容：interface VibratePreset|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratePreset；<br>API声明：type: 'preset';<br>差异内容：type: 'preset';|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratePreset；<br>API声明：effectId: string;<br>差异内容：effectId: string;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratePreset；<br>API声明：count: number;<br>差异内容：count: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibrateFromFile<br>差异内容：interface VibrateFromFile|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibrateFromFile；<br>API声明：type: 'file';<br>差异内容：type: 'file';|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibrateFromFile；<br>API声明：hapticFd: HapticFileDescriptor;<br>差异内容：hapticFd: HapticFileDescriptor;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface HapticFileDescriptor<br>差异内容：interface HapticFileDescriptor|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFileDescriptor；<br>API声明：fd: number;<br>差异内容：fd: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFileDescriptor；<br>API声明：offset?: number;<br>差异内容：offset?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFileDescriptor；<br>API声明：length?: number;<br>差异内容：length?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface AccelerometerResponse<br>差异内容：export interface AccelerometerResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：AccelerometerResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：AccelerometerResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：AccelerometerResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface subscribeAccelerometerOptions<br>差异内容：export interface subscribeAccelerometerOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：subscribeAccelerometerOptions；<br>API声明：interval: string;<br>差异内容：interval: string;|api/@system.sensor.d.ts|
|新增API|NA|类名：subscribeAccelerometerOptions；<br>API声明：success: (data: AccelerometerResponse) => void;<br>差异内容：success: (data: AccelerometerResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：subscribeAccelerometerOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface CompassResponse<br>差异内容：export interface CompassResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：CompassResponse；<br>API声明：direction: number;<br>差异内容：direction: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeCompassOptions<br>差异内容：export interface SubscribeCompassOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeCompassOptions；<br>API声明：success: (data: CompassResponse) => void;<br>差异内容：success: (data: CompassResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeCompassOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ProximityResponse<br>差异内容：export interface ProximityResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：ProximityResponse；<br>API声明：distance: number;<br>差异内容：distance: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeProximityOptions<br>差异内容：export interface SubscribeProximityOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeProximityOptions；<br>API声明：success: (data: ProximityResponse) => void;<br>差异内容：success: (data: ProximityResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeProximityOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface LightResponse<br>差异内容：export interface LightResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：LightResponse；<br>API声明：intensity: number;<br>差异内容：intensity: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeLightOptions<br>差异内容：export interface SubscribeLightOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeLightOptions；<br>API声明：success: (data: LightResponse) => void;<br>差异内容：success: (data: LightResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeLightOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface StepCounterResponse<br>差异内容：export interface StepCounterResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：StepCounterResponse；<br>API声明：steps: number;<br>差异内容：steps: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeStepCounterOptions<br>差异内容：export interface SubscribeStepCounterOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeStepCounterOptions；<br>API声明：success: (data: StepCounterResponse) => void;<br>差异内容：success: (data: StepCounterResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeStepCounterOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BarometerResponse<br>差异内容：export interface BarometerResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：BarometerResponse；<br>API声明：pressure: number;<br>差异内容：pressure: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeBarometerOptions<br>差异内容：export interface SubscribeBarometerOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeBarometerOptions；<br>API声明：success: (data: BarometerResponse) => void;<br>差异内容：success: (data: BarometerResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeBarometerOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface HeartRateResponse<br>差异内容：export interface HeartRateResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：HeartRateResponse；<br>API声明：heartRate: number;<br>差异内容：heartRate: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeHeartRateOptions<br>差异内容：export interface SubscribeHeartRateOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeHeartRateOptions；<br>API声明：success: (data: HeartRateResponse) => void;<br>差异内容：success: (data: HeartRateResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeHeartRateOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface OnBodyStateResponse<br>差异内容：export interface OnBodyStateResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：OnBodyStateResponse；<br>API声明：value: boolean;<br>差异内容：value: boolean;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeOnBodyStateOptions<br>差异内容：export interface SubscribeOnBodyStateOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeOnBodyStateOptions；<br>API声明：success: (data: OnBodyStateResponse) => void;<br>差异内容：success: (data: OnBodyStateResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeOnBodyStateOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GetOnBodyStateOptions<br>差异内容：export interface GetOnBodyStateOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：GetOnBodyStateOptions；<br>API声明：success: (data: OnBodyStateResponse) => void;<br>差异内容：success: (data: OnBodyStateResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：GetOnBodyStateOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：GetOnBodyStateOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface DeviceOrientationResponse<br>差异内容：export interface DeviceOrientationResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：DeviceOrientationResponse；<br>API声明：alpha: number;<br>差异内容：alpha: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：DeviceOrientationResponse；<br>API声明：beta: number;<br>差异内容：beta: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：DeviceOrientationResponse；<br>API声明：gamma: number;<br>差异内容：gamma: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeDeviceOrientationOptions<br>差异内容：export interface SubscribeDeviceOrientationOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeDeviceOrientationOptions；<br>API声明：interval: string;<br>差异内容：interval: string;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeDeviceOrientationOptions；<br>API声明：success: (data: DeviceOrientationResponse) => void;<br>差异内容：success: (data: DeviceOrientationResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeDeviceOrientationOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GyroscopeResponse<br>差异内容：export interface GyroscopeResponse|api/@system.sensor.d.ts|
|新增API|NA|类名：GyroscopeResponse；<br>API声明：x: number;<br>差异内容：x: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：GyroscopeResponse；<br>API声明：y: number;<br>差异内容：y: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：GyroscopeResponse；<br>API声明：z: number;<br>差异内容：z: number;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubscribeGyroscopeOptions<br>差异内容：export interface SubscribeGyroscopeOptions|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeGyroscopeOptions；<br>API声明：interval: string;<br>差异内容：interval: string;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeGyroscopeOptions；<br>API声明：success: (data: GyroscopeResponse) => void;<br>差异内容：success: (data: GyroscopeResponse) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：SubscribeGyroscopeOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Sensor<br>差异内容：export default class Sensor|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeAccelerometer(options: subscribeAccelerometerOptions): void;<br>差异内容：static subscribeAccelerometer(options: subscribeAccelerometerOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeAccelerometer(): void;<br>差异内容：static unsubscribeAccelerometer(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeCompass(options: SubscribeCompassOptions): void;<br>差异内容：static subscribeCompass(options: SubscribeCompassOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeCompass(): void;<br>差异内容：static unsubscribeCompass(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeProximity(options: SubscribeProximityOptions): void;<br>差异内容：static subscribeProximity(options: SubscribeProximityOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeProximity(): void;<br>差异内容：static unsubscribeProximity(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeLight(options: SubscribeLightOptions): void;<br>差异内容：static subscribeLight(options: SubscribeLightOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeLight(): void;<br>差异内容：static unsubscribeLight(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeStepCounter(options: SubscribeStepCounterOptions): void;<br>差异内容：static subscribeStepCounter(options: SubscribeStepCounterOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeStepCounter(): void;<br>差异内容：static unsubscribeStepCounter(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeBarometer(options: SubscribeBarometerOptions): void;<br>差异内容：static subscribeBarometer(options: SubscribeBarometerOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeBarometer(): void;<br>差异内容：static unsubscribeBarometer(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeHeartRate(options: SubscribeHeartRateOptions): void;<br>差异内容：static subscribeHeartRate(options: SubscribeHeartRateOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeHeartRate(): void;<br>差异内容：static unsubscribeHeartRate(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void;<br>差异内容：static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeOnBodyState(): void;<br>差异内容：static unsubscribeOnBodyState(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static getOnBodyState(options: GetOnBodyStateOptions): void;<br>差异内容：static getOnBodyState(options: GetOnBodyStateOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void;<br>差异内容：static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeDeviceOrientation(): void;<br>差异内容：static unsubscribeDeviceOrientation(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static subscribeGyroscope(options: SubscribeGyroscopeOptions): void;<br>差异内容：static subscribeGyroscope(options: SubscribeGyroscopeOptions): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：static unsubscribeGyroscope(): void;<br>差异内容：static unsubscribeGyroscope(): void;|api/@system.sensor.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface VibrateOptions<br>差异内容：export interface VibrateOptions|api/@system.vibrator.d.ts|
|新增API|NA|类名：VibrateOptions；<br>API声明：mode?: 'long' \| 'short';<br>差异内容：mode?: 'long' \| 'short';|api/@system.vibrator.d.ts|
|新增API|NA|类名：VibrateOptions；<br>API声明：success: () => void;<br>差异内容：success: () => void;|api/@system.vibrator.d.ts|
|新增API|NA|类名：VibrateOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.vibrator.d.ts|
|新增API|NA|类名：VibrateOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.vibrator.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Vibrator<br>差异内容：export default class Vibrator|api/@system.vibrator.d.ts|
|新增API|NA|类名：Vibrator；<br>API声明：static vibrate(options?: VibrateOptions): void;<br>差异内容：static vibrate(options?: VibrateOptions): void;|api/@system.vibrator.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.sensor.d.ts<br>差异内容：SensorServiceKit|api/@ohos.sensor.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.vibrator.d.ts<br>差异内容：SensorServiceKit|api/@ohos.vibrator.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.sensor.d.ts<br>差异内容：SensorServiceKit|api/@system.sensor.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.vibrator.d.ts<br>差异内容：SensorServiceKit|api/@system.vibrator.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.SensorServiceKit.d.ts<br>差异内容：SensorServiceKit|kits/@kit.SensorServiceKit.d.ts|
