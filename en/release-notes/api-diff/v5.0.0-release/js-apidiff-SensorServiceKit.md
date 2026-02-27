| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New error code|Class name: sensor;<br>API declaration: function getSingleSensor(type: SensorId, callback: AsyncCallback\<Sensor>): void;<br>Differences: NA|Class name: sensor;<br>API declaration: function getSingleSensor(type: SensorId, callback: AsyncCallback\<Sensor>): void;<br>Differences: 14500102|api/@ohos.sensor.d.ts|
|New error code|Class name: sensor;<br>API declaration: function getSingleSensor(type: SensorId): Promise\<Sensor>;<br>Differences: NA|Class name: sensor;<br>API declaration: function getSingleSensor(type: SensorId): Promise\<Sensor>;<br>Differences: 14500102|api/@ohos.sensor.d.ts|
|Property change|Class name: VibratePreset;<br>API declaration: count: number;<br>Differences: count: number;|Class name: VibratePreset;<br>API declaration: count?: number;<br>Differences: count?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: sensor;<br>API declaration: function getSingleSensorSync(type: SensorId): Sensor;<br>Differences: function getSingleSensorSync(type: SensorId): Sensor;|api/@ohos.sensor.d.ts|
|New API |NA|Class name: sensor;<br>API declaration: function getSensorListSync(): Array\<Sensor>;<br>Differences: function getSensorListSync(): Array\<Sensor>;|api/@ohos.sensor.d.ts|
|New API |NA|Class name: LightResponse;<br>API declaration: colorTemperature?: number;<br>Differences: colorTemperature?: number;|api/@ohos.sensor.d.ts|
|New API |NA|Class name: LightResponse;<br>API declaration: infraredLuminance?: number;<br>Differences: infraredLuminance?: number;|api/@ohos.sensor.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: function stopVibrationSync(): void;<br>Differences: function stopVibrationSync(): void;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: function isSupportEffectSync(effectId: string): boolean;<br>Differences: function isSupportEffectSync(effectId: string): boolean;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: function isHdHapticSupported(): boolean;<br>Differences: function isHdHapticSupported(): boolean;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: enum HapticFeedback<br>Differences: enum HapticFeedback|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: HapticFeedback;<br>API declaration: EFFECT_SOFT = 'haptic.effect.soft'<br>Differences: EFFECT_SOFT = 'haptic.effect.soft'|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: HapticFeedback;<br>API declaration: EFFECT_HARD = 'haptic.effect.hard'<br>Differences: EFFECT_HARD = 'haptic.effect.hard'|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: HapticFeedback;<br>API declaration: EFFECT_SHARP = 'haptic.effect.sharp'<br>Differences: EFFECT_SHARP = 'haptic.effect.sharp'|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratePreset;<br>API declaration: intensity?: number;<br>Differences: intensity?: number;|api/@ohos.vibrator.d.ts|
