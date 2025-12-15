| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API废弃版本变更|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>差异内容：18|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|api/@ohos.inputMethod.d.ts|
|API废弃版本变更|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(): Promise\<boolean>;<br>差异内容：18|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(): Promise\<boolean>;<br>差异内容：NA|api/@ohos.inputMethod.d.ts|
|删除错误码|类名：Panel；<br>API声明：startMoving(): void;<br>差异内容：801|类名：Panel；<br>API声明：startMoving(): void;<br>差异内容：NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：inputMethod；<br>API声明：function setSimpleKeyboardEnabled(enable: boolean): void;<br>差异内容：function setSimpleKeyboardEnabled(enable: boolean): void;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：InputMethodController；<br>API声明：discardTypingText(): Promise\<void>;<br>差异内容：discardTypingText(): Promise\<void>;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：InputMethodController；<br>API声明：on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;<br>差异内容：on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：InputMethodController；<br>API声明：off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;<br>差异内容：off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：InputMethodController；<br>API声明：on(type: 'finishTextPreview', callback: Callback\<void>): void;<br>差异内容：on(type: 'finishTextPreview', callback: Callback\<void>): void;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：InputMethodController；<br>API声明：off(type: 'finishTextPreview', callback?: Callback\<void>): void;<br>差异内容：off(type: 'finishTextPreview', callback?: Callback\<void>): void;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：InputMethodProperty；<br>API声明：readonly enabledState?: EnabledState;<br>差异内容：readonly enabledState?: EnabledState;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：TextInputType；<br>API声明：SCREEN_LOCK_PASSWORD<br>差异内容：SCREEN_LOCK_PASSWORD|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：TextInputType；<br>API声明：USER_NAME<br>差异内容：USER_NAME|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：TextInputType；<br>API声明：NEW_PASSWORD<br>差异内容：NEW_PASSWORD|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：TextInputType；<br>API声明：NUMBER_DECIMAL<br>差异内容：NUMBER_DECIMAL|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：TextInputType；<br>API声明：ONE_TIME_CODE<br>差异内容：ONE_TIME_CODE|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：InputAttribute；<br>API声明：placeholder?: string;<br>差异内容：placeholder?: string;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：InputAttribute；<br>API声明：abilityName?: string;<br>差异内容：abilityName?: string;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：TextConfig；<br>API声明：newEditBox?: boolean;<br>差异内容：newEditBox?: boolean;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：TextConfig；<br>API声明：capitalizeMode?: CapitalizeMode;<br>差异内容：capitalizeMode?: CapitalizeMode;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：inputMethod；<br>API声明：export type SetPreviewTextCallback = (text: string, range: Range) => void;<br>差异内容：export type SetPreviewTextCallback = (text: string, range: Range) => void;|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：inputMethod；<br>API声明：export enum CapitalizeMode<br>差异内容：export enum CapitalizeMode|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：CapitalizeMode；<br>API声明：NONE = 0<br>差异内容：NONE = 0|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：CapitalizeMode；<br>API声明：SENTENCES<br>差异内容：SENTENCES|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：CapitalizeMode；<br>API声明：WORDS<br>差异内容：WORDS|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：CapitalizeMode；<br>API声明：CHARACTERS<br>差异内容：CHARACTERS|NA|api/@ohos.inputMethod.d.ts|
|删除API|类名：inputMethodEngine；<br>API声明：const PATTERN_USER_NAME: number = 10;<br>差异内容：const PATTERN_USER_NAME: number = 10;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：inputMethodEngine；<br>API声明：const PATTERN_NEW_PASSWORD: number = 11;<br>差异内容：const PATTERN_NEW_PASSWORD: number = 11;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：inputMethodEngine；<br>API声明：const PATTERN_NUMBER_DECIMAL: number = 12;<br>差异内容：const PATTERN_NUMBER_DECIMAL: number = 12;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：inputMethodEngine；<br>API声明：const PATTERN_ONE_TIME_CODE: number = 13;<br>差异内容：const PATTERN_ONE_TIME_CODE: number = 13;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：InputMethodAbility；<br>API声明：on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;<br>差异内容：on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：InputMethodAbility；<br>API声明：off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;<br>差异内容：off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：InputMethodAbility；<br>API声明：on(type: 'discardTypingText', callback: Callback\<void>): void;<br>差异内容：on(type: 'discardTypingText', callback: Callback\<void>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：InputMethodAbility；<br>API声明：off(type: 'discardTypingText', callback?: Callback\<void>): void;<br>差异内容：off(type: 'discardTypingText', callback?: Callback\<void>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：InputClient；<br>API声明：getAttachOptions(): AttachOptions;<br>差异内容：getAttachOptions(): AttachOptions;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：InputClient；<br>API声明：on(type: 'attachOptionsDidChange', callback: Callback\<AttachOptions>): void;<br>差异内容：on(type: 'attachOptionsDidChange', callback: Callback\<AttachOptions>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：InputClient；<br>API声明：off(type: 'attachOptionsDidChange', callback?: Callback\<AttachOptions>): void;<br>差异内容：off(type: 'attachOptionsDidChange', callback?: Callback\<AttachOptions>): void;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：inputMethodEngine；<br>API声明：export enum GradientMode<br>差异内容：export enum GradientMode|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：GradientMode；<br>API声明：NONE = 0<br>差异内容：NONE = 0|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：GradientMode；<br>API声明：LINEAR_GRADIENT = 1<br>差异内容：LINEAR_GRADIENT = 1|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：inputMethodEngine；<br>API声明：interface ImmersiveEffect<br>差异内容：interface ImmersiveEffect|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：ImmersiveEffect；<br>API声明：gradientHeight: number;<br>差异内容：gradientHeight: number;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：ImmersiveEffect；<br>API声明：gradientMode: GradientMode;<br>差异内容：gradientMode: GradientMode;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：inputMethodEngine；<br>API声明：export enum RequestKeyboardReason<br>差异内容：export enum RequestKeyboardReason|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：RequestKeyboardReason；<br>API声明：NONE = 0<br>差异内容：NONE = 0|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：RequestKeyboardReason；<br>API声明：MOUSE = 1<br>差异内容：MOUSE = 1|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：RequestKeyboardReason；<br>API声明：TOUCH = 2<br>差异内容：TOUCH = 2|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：RequestKeyboardReason；<br>API声明：OTHER = 20<br>差异内容：OTHER = 20|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：Panel；<br>API声明：setImmersiveEffect(effect: ImmersiveEffect): void;<br>差异内容：setImmersiveEffect(effect: ImmersiveEffect): void;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：Panel；<br>API声明：setKeepScreenOn(isKeepScreenOn: boolean): Promise\<void>;<br>差异内容：setKeepScreenOn(isKeepScreenOn: boolean): Promise\<void>;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：EditorAttribute；<br>API声明：readonly windowId?: number;<br>差异内容：readonly windowId?: number;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：EditorAttribute；<br>API声明：readonly displayId?: number;<br>差异内容：readonly displayId?: number;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：EditorAttribute；<br>API声明：readonly placeholder?: string;<br>差异内容：readonly placeholder?: string;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：EditorAttribute；<br>API声明：readonly abilityName?: string;<br>差异内容：readonly abilityName?: string;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：EditorAttribute；<br>API声明：readonly capitalizeMode?: CapitalizeMode;<br>差异内容：readonly capitalizeMode?: CapitalizeMode;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：EditorAttribute；<br>API声明：readonly gradientMode?: GradientMode;<br>差异内容：readonly gradientMode?: GradientMode;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：inputMethodEngine；<br>API声明：export interface AttachOptions<br>差异内容：export interface AttachOptions|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：AttachOptions；<br>API声明：requestKeyboardReason?: RequestKeyboardReason;<br>差异内容：requestKeyboardReason?: RequestKeyboardReason;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：AttachOptions；<br>API声明：isSimpleKeyboardEnabled?: boolean;<br>差异内容：isSimpleKeyboardEnabled?: boolean;|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：inputMethodEngine；<br>API声明：export enum CapitalizeMode<br>差异内容：export enum CapitalizeMode|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：CapitalizeMode；<br>API声明：NONE = 0<br>差异内容：NONE = 0|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：CapitalizeMode；<br>API声明：SENTENCES<br>差异内容：SENTENCES|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：CapitalizeMode；<br>API声明：WORDS<br>差异内容：WORDS|NA|api/@ohos.inputMethodEngine.d.ts|
|删除API|类名：CapitalizeMode；<br>API声明：CHARACTERS<br>差异内容：CHARACTERS|NA|api/@ohos.inputMethodEngine.d.ts|
