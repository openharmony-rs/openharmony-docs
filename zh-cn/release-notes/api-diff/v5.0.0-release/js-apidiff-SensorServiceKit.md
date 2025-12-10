| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：sensor；<br>API声明：function getSingleSensor(type: SensorId, callback: AsyncCallback\<Sensor>): void;<br>差异内容：NA|类名：sensor；<br>API声明：function getSingleSensor(type: SensorId, callback: AsyncCallback\<Sensor>): void;<br>差异内容：14500102|api/@ohos.sensor.d.ts|
|新增错误码|类名：sensor；<br>API声明：function getSingleSensor(type: SensorId): Promise\<Sensor>;<br>差异内容：NA|类名：sensor；<br>API声明：function getSingleSensor(type: SensorId): Promise\<Sensor>;<br>差异内容：14500102|api/@ohos.sensor.d.ts|
|属性变更|类名：VibratePreset；<br>API声明：count: number;<br>差异内容：count: number;|类名：VibratePreset；<br>API声明：count?: number;<br>差异内容：count?: number;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getSingleSensorSync(type: SensorId): Sensor;<br>差异内容：function getSingleSensorSync(type: SensorId): Sensor;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：sensor；<br>API声明：function getSensorListSync(): Array\<Sensor>;<br>差异内容：function getSensorListSync(): Array\<Sensor>;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：LightResponse；<br>API声明：colorTemperature?: number;<br>差异内容：colorTemperature?: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：LightResponse；<br>API声明：infraredLuminance?: number;<br>差异内容：infraredLuminance?: number;|api/@ohos.sensor.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function stopVibrationSync(): void;<br>差异内容：function stopVibrationSync(): void;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function isSupportEffectSync(effectId: string): boolean;<br>差异内容：function isSupportEffectSync(effectId: string): boolean;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：function isHdHapticSupported(): boolean;<br>差异内容：function isHdHapticSupported(): boolean;|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：vibrator；<br>API声明：enum HapticFeedback<br>差异内容：enum HapticFeedback|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFeedback；<br>API声明：EFFECT_SOFT = 'haptic.effect.soft'<br>差异内容：EFFECT_SOFT = 'haptic.effect.soft'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFeedback；<br>API声明：EFFECT_HARD = 'haptic.effect.hard'<br>差异内容：EFFECT_HARD = 'haptic.effect.hard'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFeedback；<br>API声明：EFFECT_SHARP = 'haptic.effect.sharp'<br>差异内容：EFFECT_SHARP = 'haptic.effect.sharp'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：VibratePreset；<br>API声明：intensity?: number;<br>差异内容：intensity?: number;|api/@ohos.vibrator.d.ts|
