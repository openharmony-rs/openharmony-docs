| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|自定义类型变更|类名：vibrator；<br>API声明：type VibrateEffect = VibrateTime \| VibratePreset \| VibrateFromFile;<br>差异内容：VibrateTime \| VibratePreset \| VibrateFromFile|类名：vibrator；<br>API声明：type VibrateEffect = VibrateTime \| VibratePreset \| VibrateFromFile \| VibrateFromPattern;<br>差异内容：VibrateTime \| VibratePreset \| VibrateFromFile \| VibrateFromPattern|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFeedback；<br>API声明：EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'<br>差异内容：EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFeedback；<br>API声明：EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'<br>差异内容：EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'|api/@ohos.vibrator.d.ts|
|新增API|NA|类名：HapticFeedback；<br>API声明：EFFECT_NOTICE_WARNING = 'haptic.notice.warning'<br>差异内容：EFFECT_NOTICE_WARNING = 'haptic.notice.warning'|api/@ohos.vibrator.d.ts|
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
