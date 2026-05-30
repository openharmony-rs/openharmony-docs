| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API废弃版本变更|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>差异内容：18|api/@ohos.inputMethod.d.ts|
|API废弃版本变更|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(): Promise\<boolean>;<br>差异内容：NA|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(): Promise\<boolean>;<br>差异内容：18|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function setSimpleKeyboardEnabled(enable: boolean): void;<br>差异内容：function setSimpleKeyboardEnabled(enable: boolean): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：getInputMethodState(): Promise\<EnabledState>;<br>差异内容：getInputMethodState(): Promise\<EnabledState>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：discardTypingText(): Promise\<void>;<br>差异内容：discardTypingText(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise\<void>;<br>差异内容：sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：recvMessage(msgHandler?: MessageHandler): void;<br>差异内容：recvMessage(msgHandler?: MessageHandler): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;<br>差异内容：on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;<br>差异内容：off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'finishTextPreview', callback: Callback\<void>): void;<br>差异内容：on(type: 'finishTextPreview', callback: Callback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'finishTextPreview', callback?: Callback\<void>): void;<br>差异内容：off(type: 'finishTextPreview', callback?: Callback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：readonly enabledState?: EnabledState;<br>差异内容：readonly enabledState?: EnabledState;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：SCREEN_LOCK_PASSWORD<br>差异内容：SCREEN_LOCK_PASSWORD|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：USER_NAME<br>差异内容：USER_NAME|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：NEW_PASSWORD<br>差异内容：NEW_PASSWORD|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：NUMBER_DECIMAL<br>差异内容：NUMBER_DECIMAL|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：ONE_TIME_CODE<br>差异内容：ONE_TIME_CODE|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputAttribute；<br>API声明：placeholder?: string;<br>差异内容：placeholder?: string;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputAttribute；<br>API声明：abilityName?: string;<br>差异内容：abilityName?: string;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextConfig；<br>API声明：newEditBox?: boolean;<br>差异内容：newEditBox?: boolean;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextConfig；<br>API声明：capitalizeMode?: CapitalizeMode;<br>差异内容：capitalizeMode?: CapitalizeMode;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：interface MessageHandler<br>差异内容：interface MessageHandler|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：MessageHandler；<br>API声明：onMessage(msgId: string, msgParam?: ArrayBuffer): void;<br>差异内容：onMessage(msgId: string, msgParam?: ArrayBuffer): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：MessageHandler；<br>API声明：onTerminated(): void;<br>差异内容：onTerminated(): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export enum EnabledState<br>差异内容：export enum EnabledState|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnabledState；<br>API声明：DISABLED = 0<br>差异内容：DISABLED = 0|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnabledState；<br>API声明：BASIC_MODE<br>差异内容：BASIC_MODE|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnabledState；<br>API声明：FULL_EXPERIENCE_MODE<br>差异内容：FULL_EXPERIENCE_MODE|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export enum RequestKeyboardReason<br>差异内容：export enum RequestKeyboardReason|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：RequestKeyboardReason；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：RequestKeyboardReason；<br>API声明：MOUSE = 1<br>差异内容：MOUSE = 1|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：RequestKeyboardReason；<br>API声明：TOUCH = 2<br>差异内容：TOUCH = 2|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：RequestKeyboardReason；<br>API声明：OTHER = 20<br>差异内容：OTHER = 20|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export type SetPreviewTextCallback = (text: string, range: Range) => void;<br>差异内容：export type SetPreviewTextCallback = (text: string, range: Range) => void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export enum CapitalizeMode<br>差异内容：export enum CapitalizeMode|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：CapitalizeMode；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：CapitalizeMode；<br>API声明：SENTENCES<br>差异内容：SENTENCES|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：CapitalizeMode；<br>API声明：WORDS<br>差异内容：WORDS|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：CapitalizeMode；<br>API声明：CHARACTERS<br>差异内容：CHARACTERS|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：Panel；<br>API声明：adjustPanelRect(flag: PanelFlag, rect: EnhancedPanelRect): void;<br>差异内容：adjustPanelRect(flag: PanelFlag, rect: EnhancedPanelRect): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_USER_NAME: number = 10;<br>差异内容：const PATTERN_USER_NAME: number = 10;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_NEW_PASSWORD: number = 11;<br>差异内容：const PATTERN_NEW_PASSWORD: number = 11;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_NUMBER_DECIMAL: number = 12;<br>差异内容：const PATTERN_NUMBER_DECIMAL: number = 12;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_ONE_TIME_CODE: number = 13;<br>差异内容：const PATTERN_ONE_TIME_CODE: number = 13;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export type SizeChangeCallback = (size: window.Size, keyboardArea?: KeyboardArea) => void;<br>差异内容：export type SizeChangeCallback = (size: window.Size, keyboardArea?: KeyboardArea) => void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;<br>差异内容：on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;<br>差异内容：off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'discardTypingText', callback: Callback\<void>): void;<br>差异内容：on(type: 'discardTypingText', callback: Callback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'discardTypingText', callback?: Callback\<void>): void;<br>差异内容：off(type: 'discardTypingText', callback?: Callback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise\<void>;<br>差异内容：sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：recvMessage(msgHandler?: MessageHandler): void;<br>差异内容：recvMessage(msgHandler?: MessageHandler): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getAttachOptions(): AttachOptions;<br>差异内容：getAttachOptions(): AttachOptions;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：on(type: 'attachOptionsDidChange', callback: Callback\<AttachOptions>): void;<br>差异内容：on(type: 'attachOptionsDidChange', callback: Callback\<AttachOptions>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：off(type: 'attachOptionsDidChange', callback?: Callback\<AttachOptions>): void;<br>差异内容：off(type: 'attachOptionsDidChange', callback?: Callback\<AttachOptions>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export enum ImmersiveMode<br>差异内容：export enum ImmersiveMode|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ImmersiveMode；<br>API声明：NONE_IMMERSIVE = 0<br>差异内容：NONE_IMMERSIVE = 0|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ImmersiveMode；<br>API声明：IMMERSIVE<br>差异内容：IMMERSIVE|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ImmersiveMode；<br>API声明：LIGHT_IMMERSIVE<br>差异内容：LIGHT_IMMERSIVE|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ImmersiveMode；<br>API声明：DARK_IMMERSIVE<br>差异内容：DARK_IMMERSIVE|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export enum GradientMode<br>差异内容：export enum GradientMode|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：GradientMode；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：GradientMode；<br>API声明：LINEAR_GRADIENT = 1<br>差异内容：LINEAR_GRADIENT = 1|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface ImmersiveEffect<br>差异内容：interface ImmersiveEffect|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ImmersiveEffect；<br>API声明：gradientHeight: number;<br>差异内容：gradientHeight: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ImmersiveEffect；<br>API声明：gradientMode: GradientMode;<br>差异内容：gradientMode: GradientMode;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export enum RequestKeyboardReason<br>差异内容：export enum RequestKeyboardReason|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：RequestKeyboardReason；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：RequestKeyboardReason；<br>API声明：MOUSE = 1<br>差异内容：MOUSE = 1|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：RequestKeyboardReason；<br>API声明：TOUCH = 2<br>差异内容：TOUCH = 2|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：RequestKeyboardReason；<br>API声明：OTHER = 20<br>差异内容：OTHER = 20|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：startMoving(): void;<br>差异内容：startMoving(): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：getDisplayId(): Promise\<number>;<br>差异内容：getDisplayId(): Promise\<number>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：updateRegion(inputRegion: Array\<window.Rect>): void;<br>差异内容：updateRegion(inputRegion: Array\<window.Rect>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：setImmersiveMode(mode: ImmersiveMode): void;<br>差异内容：setImmersiveMode(mode: ImmersiveMode): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：getImmersiveMode(): ImmersiveMode;<br>差异内容：getImmersiveMode(): ImmersiveMode;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：setImmersiveEffect(effect: ImmersiveEffect): void;<br>差异内容：setImmersiveEffect(effect: ImmersiveEffect): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：setKeepScreenOn(isKeepScreenOn: boolean): Promise\<void>;<br>差异内容：setKeepScreenOn(isKeepScreenOn: boolean): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly immersiveMode?: ImmersiveMode;<br>差异内容：readonly immersiveMode?: ImmersiveMode;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly windowId?: number;<br>差异内容：readonly windowId?: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly displayId?: number;<br>差异内容：readonly displayId?: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly placeholder?: string;<br>差异内容：readonly placeholder?: string;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly abilityName?: string;<br>差异内容：readonly abilityName?: string;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly capitalizeMode?: CapitalizeMode;<br>差异内容：readonly capitalizeMode?: CapitalizeMode;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly gradientMode?: GradientMode;<br>差异内容：readonly gradientMode?: GradientMode;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：PanelFlag；<br>API声明：FLAG_CANDIDATE<br>差异内容：FLAG_CANDIDATE|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface MessageHandler<br>差异内容：interface MessageHandler|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：MessageHandler；<br>API声明：onMessage(msgId: string, msgParam?: ArrayBuffer): void;<br>差异内容：onMessage(msgId: string, msgParam?: ArrayBuffer): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：MessageHandler；<br>API声明：onTerminated(): void;<br>差异内容：onTerminated(): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export interface EnhancedPanelRect<br>差异内容：export interface EnhancedPanelRect|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EnhancedPanelRect；<br>API声明：landscapeRect?: window.Rect;<br>差异内容：landscapeRect?: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EnhancedPanelRect；<br>API声明：portraitRect?: window.Rect;<br>差异内容：portraitRect?: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EnhancedPanelRect；<br>API声明：landscapeAvoidY?: number;<br>差异内容：landscapeAvoidY?: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EnhancedPanelRect；<br>API声明：landscapeInputRegion?: Array\<window.Rect>;<br>差异内容：landscapeInputRegion?: Array\<window.Rect>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EnhancedPanelRect；<br>API声明：portraitAvoidY?: number;<br>差异内容：portraitAvoidY?: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EnhancedPanelRect；<br>API声明：portraitInputRegion?: Array\<window.Rect>;<br>差异内容：portraitInputRegion?: Array\<window.Rect>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EnhancedPanelRect；<br>API声明：fullScreenMode?: boolean;<br>差异内容：fullScreenMode?: boolean;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export interface KeyboardArea<br>差异内容：export interface KeyboardArea|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardArea；<br>API声明：top: number;<br>差异内容：top: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardArea；<br>API声明：bottom: number;<br>差异内容：bottom: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardArea；<br>API声明：left: number;<br>差异内容：left: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardArea；<br>API声明：right: number;<br>差异内容：right: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export interface AttachOptions<br>差异内容：export interface AttachOptions|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：AttachOptions；<br>API声明：requestKeyboardReason?: RequestKeyboardReason;<br>差异内容：requestKeyboardReason?: RequestKeyboardReason;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：AttachOptions；<br>API声明：isSimpleKeyboardEnabled?: boolean;<br>差异内容：isSimpleKeyboardEnabled?: boolean;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export enum CapitalizeMode<br>差异内容：export enum CapitalizeMode|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：CapitalizeMode；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：CapitalizeMode；<br>API声明：SENTENCES<br>差异内容：SENTENCES|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：CapitalizeMode；<br>API声明：WORDS<br>差异内容：WORDS|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：CapitalizeMode；<br>API声明：CHARACTERS<br>差异内容：CHARACTERS|api/@ohos.inputMethodEngine.d.ts|
|函数变更|类名：Panel；<br>API声明：on(type: 'sizeChange', callback: Callback\<window.Size>): void;<br>差异内容：callback: Callback\<window.Size>|类名：Panel；<br>API声明：on(type: 'sizeChange', callback: SizeChangeCallback): void;<br>差异内容：callback: SizeChangeCallback|api/@ohos.inputMethodEngine.d.ts|
|函数变更|类名：Panel；<br>API声明：off(type: 'sizeChange', callback?: Callback\<window.Size>): void;<br>差异内容：callback?: Callback\<window.Size>|类名：Panel；<br>API声明：off(type: 'sizeChange', callback?: SizeChangeCallback): void;<br>差异内容：callback?: SizeChangeCallback|api/@ohos.inputMethodEngine.d.ts|
