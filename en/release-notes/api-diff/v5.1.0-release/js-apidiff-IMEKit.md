| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|API deprecated version change|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>DIfferences: 18|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>DIfferences: NA|api/@ohos.inputMethod.d.ts|
|API deprecated version change|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(): Promise\<boolean>;<br>DIfferences: 18|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(): Promise\<boolean>;<br>DIfferences: NA|api/@ohos.inputMethod.d.ts|
|Deleted error code|Class name: Panel;<br>API declaration: startMoving(): void;<br>DIfferences: 801|Class name: Panel;<br>API declaration: startMoving(): void;<br>DIfferences: NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: inputMethod;<br>API declaration: function setSimpleKeyboardEnabled(enable: boolean): void;<br>DIfferences: function setSimpleKeyboardEnabled(enable: boolean): void;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: InputMethodController;<br>API declaration: discardTypingText(): Promise\<void>;<br>DIfferences: discardTypingText(): Promise\<void>;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: InputMethodController;<br>API declaration: on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;<br>DIfferences: on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: InputMethodController;<br>API declaration: off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;<br>DIfferences: off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: InputMethodController;<br>API declaration: on(type: 'finishTextPreview', callback: Callback\<void>): void;<br>DIfferences: on(type: 'finishTextPreview', callback: Callback\<void>): void;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: InputMethodController;<br>API declaration: off(type: 'finishTextPreview', callback?: Callback\<void>): void;<br>DIfferences: off(type: 'finishTextPreview', callback?: Callback\<void>): void;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: InputMethodProperty;<br>API declaration: readonly enabledState?: EnabledState;<br>DIfferences: readonly enabledState?: EnabledState;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: TextInputType;<br>API declaration: SCREEN_LOCK_PASSWORD<br>DIfferences: SCREEN_LOCK_PASSWORD|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: TextInputType;<br>API declaration: USER_NAME<br>DIfferences: USER_NAME|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: TextInputType;<br>API declaration: NEW_PASSWORD<br>DIfferences: NEW_PASSWORD|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: TextInputType;<br>API declaration: NUMBER_DECIMAL<br>DIfferences: NUMBER_DECIMAL|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: TextInputType;<br>API declaration: ONE_TIME_CODE<br>DIfferences: ONE_TIME_CODE|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: InputAttribute;<br>API declaration: placeholder?: string;<br>DIfferences: placeholder?: string;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: InputAttribute;<br>API declaration: abilityName?: string;<br>DIfferences: abilityName?: string;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: TextConfig;<br>API declaration: newEditBox?: boolean;<br>DIfferences: newEditBox?: boolean;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: TextConfig;<br>API declaration: capitalizeMode?: CapitalizeMode;<br>DIfferences: capitalizeMode?: CapitalizeMode;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: inputMethod;<br>API declaration: export type SetPreviewTextCallback = (text: string, range: Range) => void;<br>DIfferences: export type SetPreviewTextCallback = (text: string, range: Range) => void;|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: inputMethod;<br>API declaration: export enum CapitalizeMode<br>DIfferences: export enum CapitalizeMode|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: CapitalizeMode;<br>API declaration: NONE = 0<br>DIfferences: NONE = 0|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: CapitalizeMode;<br>API declaration: SENTENCES<br>DIfferences: SENTENCES|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: CapitalizeMode;<br>API declaration: WORDS<br>DIfferences: WORDS|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: CapitalizeMode;<br>API declaration: CHARACTERS<br>DIfferences: CHARACTERS|NA|api/@ohos.inputMethod.d.ts|
| Deleted API|Class name: inputMethodEngine;<br>API declaration: const PATTERN_USER_NAME: number = 10;<br>DIfferences: const PATTERN_USER_NAME: number = 10;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: inputMethodEngine;<br>API declaration: const PATTERN_NEW_PASSWORD: number = 11;<br>DIfferences: const PATTERN_NEW_PASSWORD: number = 11;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: inputMethodEngine;<br>API declaration: const PATTERN_NUMBER_DECIMAL: number = 12;<br>DIfferences: const PATTERN_NUMBER_DECIMAL: number = 12;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: inputMethodEngine;<br>API declaration: const PATTERN_ONE_TIME_CODE: number = 13;<br>DIfferences: const PATTERN_ONE_TIME_CODE: number = 13;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: InputMethodAbility;<br>API declaration: on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;<br>DIfferences: on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: InputMethodAbility;<br>API declaration: off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;<br>DIfferences: off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: InputMethodAbility;<br>API declaration: on(type: 'discardTypingText', callback: Callback\<void>): void;<br>DIfferences: on(type: 'discardTypingText', callback: Callback\<void>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: InputMethodAbility;<br>API declaration: off(type: 'discardTypingText', callback?: Callback\<void>): void;<br>DIfferences: off(type: 'discardTypingText', callback?: Callback\<void>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: InputClient;<br>API declaration: getAttachOptions(): AttachOptions;<br>DIfferences: getAttachOptions(): AttachOptions;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: InputClient;<br>API declaration: on(type: 'attachOptionsDidChange', callback: Callback\<AttachOptions>): void;<br>DIfferences: on(type: 'attachOptionsDidChange', callback: Callback\<AttachOptions>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: InputClient;<br>API declaration: off(type: 'attachOptionsDidChange', callback?: Callback\<AttachOptions>): void;<br>DIfferences: off(type: 'attachOptionsDidChange', callback?: Callback\<AttachOptions>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: inputMethodEngine;<br>API declaration: export enum GradientMode<br>DIfferences: export enum GradientMode|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: GradientMode;<br>API declaration: NONE = 0<br>DIfferences: NONE = 0|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: GradientMode;<br>API declaration: LINEAR_GRADIENT = 1<br>DIfferences: LINEAR_GRADIENT = 1|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: inputMethodEngine;<br>API declaration: interface ImmersiveEffect<br>DIfferences: interface ImmersiveEffect|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: ImmersiveEffect;<br>API declaration: gradientHeight: number;<br>DIfferences: gradientHeight: number;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: ImmersiveEffect;<br>API declaration: gradientMode: GradientMode;<br>DIfferences: gradientMode: GradientMode;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: inputMethodEngine;<br>API declaration: export enum RequestKeyboardReason<br>DIfferences: export enum RequestKeyboardReason|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: RequestKeyboardReason;<br>API declaration: NONE = 0<br>DIfferences: NONE = 0|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: RequestKeyboardReason;<br>API declaration: MOUSE = 1<br>DIfferences: MOUSE = 1|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: RequestKeyboardReason;<br>API declaration: TOUCH = 2<br>DIfferences: TOUCH = 2|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: RequestKeyboardReason;<br>API declaration: OTHER = 20<br>DIfferences: OTHER = 20|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: Panel;<br>API declaration: setImmersiveEffect(effect: ImmersiveEffect): void;<br>DIfferences: setImmersiveEffect(effect: ImmersiveEffect): void;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: Panel;<br>API declaration: setKeepScreenOn(isKeepScreenOn: boolean): Promise\<void>;<br>DIfferences: setKeepScreenOn(isKeepScreenOn: boolean): Promise\<void>;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: EditorAttribute;<br>API declaration: readonly windowId?: number;<br>DIfferences: readonly windowId?: number;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: EditorAttribute;<br>API declaration: readonly displayId?: number;<br>DIfferences: readonly displayId?: number;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: EditorAttribute;<br>API declaration: readonly placeholder?: string;<br>DIfferences: readonly placeholder?: string;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: EditorAttribute;<br>API declaration: readonly abilityName?: string;<br>DIfferences: readonly abilityName?: string;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: EditorAttribute;<br>API declaration: readonly capitalizeMode?: CapitalizeMode;<br>DIfferences: readonly capitalizeMode?: CapitalizeMode;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: EditorAttribute;<br>API declaration: readonly gradientMode?: GradientMode;<br>DIfferences: readonly gradientMode?: GradientMode;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: inputMethodEngine;<br>API declaration: export interface AttachOptions<br>DIfferences: export interface AttachOptions|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: AttachOptions;<br>API declaration: requestKeyboardReason?: RequestKeyboardReason;<br>DIfferences: requestKeyboardReason?: RequestKeyboardReason;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: AttachOptions;<br>API declaration: isSimpleKeyboardEnabled?: boolean;<br>DIfferences: isSimpleKeyboardEnabled?: boolean;|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: inputMethodEngine;<br>API declaration: export enum CapitalizeMode<br>DIfferences: export enum CapitalizeMode|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: CapitalizeMode;<br>API declaration: NONE = 0<br>DIfferences: NONE = 0|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: CapitalizeMode;<br>API declaration: SENTENCES<br>DIfferences: SENTENCES|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: CapitalizeMode;<br>API declaration: WORDS<br>DIfferences: WORDS|NA|api/@ohos.inputMethodEngine.d.ts|
| Deleted API|Class name: CapitalizeMode;<br>API declaration: CHARACTERS<br>DIfferences: CHARACTERS|NA|api/@ohos.inputMethodEngine.d.ts|
