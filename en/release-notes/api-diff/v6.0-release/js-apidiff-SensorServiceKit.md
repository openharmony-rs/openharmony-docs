| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|Custom type change|Class name: vibrator;<br>API declaration: type VibrateEffect = VibrateTime \| VibratePreset \| VibrateFromFile;<br>DIfferences: VibrateTime \| VibratePreset \| VibrateFromFile|Class name: vibrator;<br>API declaration: type VibrateEffect = VibrateTime \| VibratePreset \| VibrateFromFile \| VibrateFromPattern;<br>DIfferences: VibrateTime \| VibratePreset \| VibrateFromFile \| VibrateFromPattern|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: HapticFeedback;<br>API declaration: EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'<br>DIfferences: EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: HapticFeedback;<br>API declaration: EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'<br>DIfferences: EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: HapticFeedback;<br>API declaration: EFFECT_NOTICE_WARNING = 'haptic.notice.warning'<br>DIfferences: EFFECT_NOTICE_WARNING = 'haptic.notice.warning'|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: enum VibratorEventType<br>DIfferences: enum VibratorEventType|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorEventType;<br>API declaration: CONTINUOUS = 0<br>DIfferences: CONTINUOUS = 0|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorEventType;<br>API declaration: TRANSIENT = 1<br>DIfferences: TRANSIENT = 1|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: interface VibratorCurvePoint<br>DIfferences: interface VibratorCurvePoint|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorCurvePoint;<br>API declaration: time: number;<br>DIfferences: time: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorCurvePoint;<br>API declaration: intensity?: number;<br>DIfferences: intensity?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorCurvePoint;<br>API declaration: frequency?: number;<br>DIfferences: frequency?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: interface VibratorEvent<br>DIfferences: interface VibratorEvent|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorEvent;<br>API declaration: eventType: VibratorEventType;<br>DIfferences: eventType: VibratorEventType;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorEvent;<br>API declaration: time: number;<br>DIfferences: time: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorEvent;<br>API declaration: duration?: number;<br>DIfferences: duration?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorEvent;<br>API declaration: intensity?: number;<br>DIfferences: intensity?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorEvent;<br>API declaration: frequency?: number;<br>DIfferences: frequency?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorEvent;<br>API declaration: index?: number;<br>DIfferences: index?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorEvent;<br>API declaration: points?: Array\<VibratorCurvePoint>;<br>DIfferences: points?: Array\<VibratorCurvePoint>;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: interface VibratorPattern<br>DIfferences: interface VibratorPattern|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorPattern;<br>API declaration: time: number;<br>DIfferences: time: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorPattern;<br>API declaration: events: Array\<VibratorEvent>;<br>DIfferences: events: Array\<VibratorEvent>;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: interface ContinuousParam<br>DIfferences: interface ContinuousParam|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: ContinuousParam;<br>API declaration: intensity?: number;<br>DIfferences: intensity?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: ContinuousParam;<br>API declaration: frequency?: number;<br>DIfferences: frequency?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: ContinuousParam;<br>API declaration: points?: VibratorCurvePoint[];<br>DIfferences: points?: VibratorCurvePoint[];|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: ContinuousParam;<br>API declaration: index?: number;<br>DIfferences: index?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: interface TransientParam<br>DIfferences: interface TransientParam|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: TransientParam;<br>API declaration: intensity?: number;<br>DIfferences: intensity?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: TransientParam;<br>API declaration: frequency?: number;<br>DIfferences: frequency?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: TransientParam;<br>API declaration: index?: number;<br>DIfferences: index?: number;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: class VibratorPatternBuilder<br>DIfferences: class VibratorPatternBuilder|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorPatternBuilder;<br>API declaration: addContinuousEvent(time: number, duration: number, options?: ContinuousParam): VibratorPatternBuilder;<br>DIfferences: addContinuousEvent(time: number, duration: number, options?: ContinuousParam): VibratorPatternBuilder;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorPatternBuilder;<br>API declaration: addTransientEvent(time: number, options?: TransientParam): VibratorPatternBuilder;<br>DIfferences: addTransientEvent(time: number, options?: TransientParam): VibratorPatternBuilder;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibratorPatternBuilder;<br>API declaration: build(): VibratorPattern;<br>DIfferences: build(): VibratorPattern;|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: vibrator;<br>API declaration: interface VibrateFromPattern<br>DIfferences: interface VibrateFromPattern|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibrateFromPattern;<br>API declaration: type: 'pattern';<br>DIfferences: type: 'pattern';|api/@ohos.vibrator.d.ts|
|New API |NA|Class name: VibrateFromPattern;<br>API declaration: pattern: VibratorPattern;<br>DIfferences: pattern: VibratorPattern;|api/@ohos.vibrator.d.ts|
