| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|自定义类型变更|类名：vibrator；<br>API声明：type VibrateEffect = VibrateTime \| VibratePreset \| VibrateFromFile;<br>差异内容：VibrateTime \| VibratePreset \| VibrateFromFile|类名：vibrator；<br>API声明：type VibrateEffect = VibrateTime \| VibratePreset \| VibrateFromFile \| VibrateFromPattern;<br>差异内容：VibrateTime \| VibratePreset \| VibrateFromFile \| VibrateFromPattern|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback\<AccelerometerResponse>): void;<br>差异内容：function off(type: SensorId.ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback\<AccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.ACCELEROMETER_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback\<AccelerometerUncalibratedResponse>): void;<br>差异内容：function off(type: SensorId.ACCELEROMETER_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback\<AccelerometerUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.AMBIENT_LIGHT, sensorInfoParam?: SensorInfoParam, callback?: Callback\<LightResponse>): void;<br>差异内容：function off(type: SensorId.AMBIENT_LIGHT, sensorInfoParam?: SensorInfoParam, callback?: Callback\<LightResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.AMBIENT_TEMPERATURE, sensorInfoParam?: SensorInfoParam, callback?: Callback\<AmbientTemperatureResponse>): void;<br>差异内容：function off(type: SensorId.AMBIENT_TEMPERATURE, sensorInfoParam?: SensorInfoParam, callback?: Callback\<AmbientTemperatureResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.BAROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback\<BarometerResponse>): void;<br>差异内容：function off(type: SensorId.BAROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback\<BarometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.GRAVITY, sensorInfoParam?: SensorInfoParam, callback?: Callback\<GravityResponse>): void;<br>差异内容：function off(type: SensorId.GRAVITY, sensorInfoParam?: SensorInfoParam, callback?: Callback\<GravityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.GYROSCOPE, sensorInfoParam?: SensorInfoParam, callback?: Callback\<GyroscopeResponse>): void;<br>差异内容：function off(type: SensorId.GYROSCOPE, sensorInfoParam?: SensorInfoParam, callback?: Callback\<GyroscopeResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.GYROSCOPE_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback\<GyroscopeUncalibratedResponse>): void;<br>差异内容：function off(type: SensorId.GYROSCOPE_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback\<GyroscopeUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.HALL, sensorInfoParam?: SensorInfoParam, callback?: Callback\<HallResponse>): void;<br>差异内容：function off(type: SensorId.HALL, sensorInfoParam?: SensorInfoParam, callback?: Callback\<HallResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.HEART_RATE, sensorInfoParam?: SensorInfoParam, callback?: Callback\<HeartRateResponse>): void;<br>差异内容：function off(type: SensorId.HEART_RATE, sensorInfoParam?: SensorInfoParam, callback?: Callback\<HeartRateResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.HUMIDITY, sensorInfoParam?: SensorInfoParam, callback?: Callback\<HumidityResponse>): void;<br>差异内容：function off(type: SensorId.HUMIDITY, sensorInfoParam?: SensorInfoParam, callback?: Callback\<HumidityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.LINEAR_ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback\<LinearAccelerometerResponse>): void;<br>差异内容：function off(type: SensorId.LINEAR_ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback\<LinearAccelerometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.MAGNETIC_FIELD, sensorInfoParam?: SensorInfoParam, callback?: Callback\<MagneticFieldResponse>): void;<br>差异内容：function off(type: SensorId.MAGNETIC_FIELD, sensorInfoParam?: SensorInfoParam, callback?: Callback\<MagneticFieldResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback\<MagneticFieldUncalibratedResponse>): void;<br>差异内容：function off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback\<MagneticFieldUncalibratedResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.ORIENTATION, sensorInfoParam?: SensorInfoParam, callback?: Callback\<OrientationResponse>): void;<br>差异内容：function off(type: SensorId.ORIENTATION, sensorInfoParam?: SensorInfoParam, callback?: Callback\<OrientationResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.PEDOMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback\<PedometerResponse>): void;<br>差异内容：function off(type: SensorId.PEDOMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback\<PedometerResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.PEDOMETER_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback\<PedometerDetectionResponse>): void;<br>差异内容：function off(type: SensorId.PEDOMETER_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback\<PedometerDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.PROXIMITY, sensorInfoParam?: SensorInfoParam, callback?: Callback\<ProximityResponse>): void;<br>差异内容：function off(type: SensorId.PROXIMITY, sensorInfoParam?: SensorInfoParam, callback?: Callback\<ProximityResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.ROTATION_VECTOR, sensorInfoParam?: SensorInfoParam, callback?: Callback\<RotationVectorResponse>): void;<br>差异内容：function off(type: SensorId.ROTATION_VECTOR, sensorInfoParam?: SensorInfoParam, callback?: Callback\<RotationVectorResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.SIGNIFICANT_MOTION, sensorInfoParam?: SensorInfoParam, callback?: Callback\<SignificantMotionResponse>): void;<br>差异内容：function off(type: SensorId.SIGNIFICANT_MOTION, sensorInfoParam?: SensorInfoParam, callback?: Callback\<SignificantMotionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: SensorId.WEAR_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback\<WearDetectionResponse>): void;<br>差异内容：function off(type: SensorId.WEAR_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback\<WearDetectionResponse>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：sensorIndex?: number;<br>差异内容：sensorIndex?: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：deviceId?: number;<br>差异内容：deviceId?: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：deviceName?: string;<br>差异内容：deviceName?: string;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Sensor；<br>API声明：isLocalSensor?: boolean;<br>差异内容：isLocalSensor?: boolean;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getSingleSensorByDeviceSync(type: SensorId, deviceId?: number): Array\<Sensor>;<br>差异内容：function getSingleSensorByDeviceSync(type: SensorId, deviceId?: number): Array\<Sensor>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getSensorListByDeviceSync(deviceId?: number): Array\<Sensor>;<br>差异内容：function getSensorListByDeviceSync(deviceId?: number): Array\<Sensor>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：Options；<br>API声明：sensorInfoParam?: SensorInfoParam;<br>差异内容：sensorInfoParam?: SensorInfoParam;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function on(type: 'sensorStatusChange', callback: Callback\<SensorStatusEvent>): void;<br>差异内容：function on(type: 'sensorStatusChange', callback: Callback\<SensorStatusEvent>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function off(type: 'sensorStatusChange', callback?: Callback\<SensorStatusEvent>): void;<br>差异内容：function off(type: 'sensorStatusChange', callback?: Callback\<SensorStatusEvent>): void;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface SensorStatusEvent<br>差异内容：interface SensorStatusEvent|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorStatusEvent；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorStatusEvent；<br>API声明：sensorId: number;<br>差异内容：sensorId: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorStatusEvent；<br>API声明：sensorIndex: number;<br>差异内容：sensorIndex: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorStatusEvent；<br>API声明：isSensorOnline: boolean;<br>差异内容：isSensorOnline: boolean;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorStatusEvent；<br>API声明：deviceId: number;<br>差异内容：deviceId: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorStatusEvent；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：interface SensorInfoParam<br>差异内容：interface SensorInfoParam|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorInfoParam；<br>API声明：deviceId?: number;<br>差异内容：deviceId?: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：SensorInfoParam；<br>API声明：sensorIndex?: number;<br>差异内容：sensorIndex?: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function stopVibration(param?: VibratorInfoParam): Promise\<void>;<br>差异内容：function stopVibration(param?: VibratorInfoParam): Promise\<void>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function getEffectInfoSync(effectId: string, param?: VibratorInfoParam): EffectInfo;<br>差异内容：function getEffectInfoSync(effectId: string, param?: VibratorInfoParam): EffectInfo;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface EffectInfo<br>差异内容：interface EffectInfo|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：EffectInfo；<br>API声明：isEffectSupported: boolean;<br>差异内容：isEffectSupported: boolean;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFeedback；<br>API声明：EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'<br>差异内容：EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFeedback；<br>API声明：EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'<br>差异内容：EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFeedback；<br>API声明：EFFECT_NOTICE_WARNING = 'haptic.notice.warning'<br>差异内容：EFFECT_NOTICE_WARNING = 'haptic.notice.warning'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibrateAttribute；<br>API声明：deviceId?: number;<br>差异内容：deviceId?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：enum VibratorEventType<br>差异内容：enum VibratorEventType|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorEventType；<br>API声明：CONTINUOUS = 0<br>差异内容：CONTINUOUS = 0|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorEventType；<br>API声明：TRANSIENT = 1<br>差异内容：TRANSIENT = 1|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibratorCurvePoint<br>差异内容：interface VibratorCurvePoint|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorCurvePoint；<br>API声明：time: number;<br>差异内容：time: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorCurvePoint；<br>API声明：intensity?: number;<br>差异内容：intensity?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorCurvePoint；<br>API声明：frequency?: number;<br>差异内容：frequency?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibratorEvent<br>差异内容：interface VibratorEvent|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorEvent；<br>API声明：eventType: VibratorEventType;<br>差异内容：eventType: VibratorEventType;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorEvent；<br>API声明：time: number;<br>差异内容：time: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorEvent；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorEvent；<br>API声明：intensity?: number;<br>差异内容：intensity?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorEvent；<br>API声明：frequency?: number;<br>差异内容：frequency?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorEvent；<br>API声明：index?: number;<br>差异内容：index?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorEvent；<br>API声明：points?: Array\<VibratorCurvePoint>;<br>差异内容：points?: Array\<VibratorCurvePoint>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibratorPattern<br>差异内容：interface VibratorPattern|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorPattern；<br>API声明：time: number;<br>差异内容：time: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorPattern；<br>API声明：events: Array\<VibratorEvent>;<br>差异内容：events: Array\<VibratorEvent>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface ContinuousParam<br>差异内容：interface ContinuousParam|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：ContinuousParam；<br>API声明：intensity?: number;<br>差异内容：intensity?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：ContinuousParam；<br>API声明：frequency?: number;<br>差异内容：frequency?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：ContinuousParam；<br>API声明：points?: VibratorCurvePoint[];<br>差异内容：points?: VibratorCurvePoint[];|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：ContinuousParam；<br>API声明：index?: number;<br>差异内容：index?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface TransientParam<br>差异内容：interface TransientParam|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：TransientParam；<br>API声明：intensity?: number;<br>差异内容：intensity?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：TransientParam；<br>API声明：frequency?: number;<br>差异内容：frequency?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：TransientParam；<br>API声明：index?: number;<br>差异内容：index?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：class VibratorPatternBuilder<br>差异内容：class VibratorPatternBuilder|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorPatternBuilder；<br>API声明：addContinuousEvent(time: number, duration: number, options?: ContinuousParam): VibratorPatternBuilder;<br>差异内容：addContinuousEvent(time: number, duration: number, options?: ContinuousParam): VibratorPatternBuilder;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorPatternBuilder；<br>API声明：addTransientEvent(time: number, options?: TransientParam): VibratorPatternBuilder;<br>差异内容：addTransientEvent(time: number, options?: TransientParam): VibratorPatternBuilder;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorPatternBuilder；<br>API声明：build(): VibratorPattern;<br>差异内容：build(): VibratorPattern;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibrateFromPattern<br>差异内容：interface VibrateFromPattern|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibrateFromPattern；<br>API声明：type: 'pattern';<br>差异内容：type: 'pattern';|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibrateFromPattern；<br>API声明：pattern: VibratorPattern;<br>差异内容：pattern: VibratorPattern;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibratorInfoParam<br>差异内容：interface VibratorInfoParam|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorInfoParam；<br>API声明：deviceId?: number;<br>差异内容：deviceId?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorInfoParam；<br>API声明：vibratorId?: number;<br>差异内容：vibratorId?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibratorInfo<br>差异内容：interface VibratorInfo|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorInfo；<br>API声明：deviceId: number;<br>差异内容：deviceId: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorInfo；<br>API声明：vibratorId: number;<br>差异内容：vibratorId: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorInfo；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorInfo；<br>API声明：isHdHapticSupported: boolean;<br>差异内容：isHdHapticSupported: boolean;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorInfo；<br>API声明：isLocalVibrator: boolean;<br>差异内容：isLocalVibrator: boolean;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function getVibratorInfoSync(param?: VibratorInfoParam): Array\<VibratorInfo>;<br>差异内容：function getVibratorInfoSync(param?: VibratorInfoParam): Array\<VibratorInfo>;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function on(type: 'vibratorStateChange', callback: Callback\<VibratorStatusEvent>): void;<br>差异内容：function on(type: 'vibratorStateChange', callback: Callback\<VibratorStatusEvent>): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function off(type: 'vibratorStateChange', callback?: Callback\<VibratorStatusEvent>): void;<br>差异内容：function off(type: 'vibratorStateChange', callback?: Callback\<VibratorStatusEvent>): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：interface VibratorStatusEvent<br>差异内容：interface VibratorStatusEvent|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorStatusEvent；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorStatusEvent；<br>API声明：deviceId: number;<br>差异内容：deviceId: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorStatusEvent；<br>API声明：vibratorCount: number;<br>差异内容：vibratorCount: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratorStatusEvent；<br>API声明：isVibratorOnline: boolean;<br>差异内容：isVibratorOnline: boolean;|api/@ohos.vibrator.d.ts|
