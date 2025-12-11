| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|API deprecated version change|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>DIfferences: NA|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>DIfferences: 18|api/@ohos.inputMethod.d.ts|
|API deprecated version change|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(): Promise\<boolean>;<br>DIfferences: NA|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(): Promise\<boolean>;<br>DIfferences: 18|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: inputMethod;<br>API declaration: function setSimpleKeyboardEnabled(enable: boolean): void;<br>DIfferences: function setSimpleKeyboardEnabled(enable: boolean): void;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputMethodSetting;<br>API declaration: getInputMethodState(): Promise\<EnabledState>;<br>DIfferences: getInputMethodState(): Promise\<EnabledState>;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputMethodController;<br>API declaration: discardTypingText(): Promise\<void>;<br>DIfferences: discardTypingText(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputMethodController;<br>API declaration: sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise\<void>;<br>DIfferences: sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputMethodController;<br>API declaration: recvMessage(msgHandler?: MessageHandler): void;<br>DIfferences: recvMessage(msgHandler?: MessageHandler): void;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputMethodController;<br>API declaration: on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;<br>DIfferences: on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputMethodController;<br>API declaration: off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;<br>DIfferences: off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputMethodController;<br>API declaration: on(type: 'finishTextPreview', callback: Callback\<void>): void;<br>DIfferences: on(type: 'finishTextPreview', callback: Callback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputMethodController;<br>API declaration: off(type: 'finishTextPreview', callback?: Callback\<void>): void;<br>DIfferences: off(type: 'finishTextPreview', callback?: Callback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputMethodProperty;<br>API declaration: readonly enabledState?: EnabledState;<br>DIfferences: readonly enabledState?: EnabledState;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: TextInputType;<br>API declaration: SCREEN_LOCK_PASSWORD<br>DIfferences: SCREEN_LOCK_PASSWORD|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: TextInputType;<br>API declaration: USER_NAME<br>DIfferences: USER_NAME|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: TextInputType;<br>API declaration: NEW_PASSWORD<br>DIfferences: NEW_PASSWORD|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: TextInputType;<br>API declaration: NUMBER_DECIMAL<br>DIfferences: NUMBER_DECIMAL|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: TextInputType;<br>API declaration: ONE_TIME_CODE<br>DIfferences: ONE_TIME_CODE|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputAttribute;<br>API declaration: placeholder?: string;<br>DIfferences: placeholder?: string;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: InputAttribute;<br>API declaration: abilityName?: string;<br>DIfferences: abilityName?: string;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: TextConfig;<br>API declaration: newEditBox?: boolean;<br>DIfferences: newEditBox?: boolean;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: TextConfig;<br>API declaration: capitalizeMode?: CapitalizeMode;<br>DIfferences: capitalizeMode?: CapitalizeMode;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: inputMethod;<br>API declaration: interface MessageHandler<br>DIfferences: interface MessageHandler|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: MessageHandler;<br>API declaration: onMessage(msgId: string, msgParam?: ArrayBuffer): void;<br>DIfferences: onMessage(msgId: string, msgParam?: ArrayBuffer): void;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: MessageHandler;<br>API declaration: onTerminated(): void;<br>DIfferences: onTerminated(): void;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: inputMethod;<br>API declaration: export enum EnabledState<br>DIfferences: export enum EnabledState|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: EnabledState;<br>API declaration: DISABLED = 0<br>DIfferences: DISABLED = 0|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: EnabledState;<br>API declaration: BASIC_MODE<br>DIfferences: BASIC_MODE|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: EnabledState;<br>API declaration: FULL_EXPERIENCE_MODE<br>DIfferences: FULL_EXPERIENCE_MODE|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: inputMethod;<br>API declaration: export enum RequestKeyboardReason<br>DIfferences: export enum RequestKeyboardReason|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: RequestKeyboardReason;<br>API declaration: NONE = 0<br>DIfferences: NONE = 0|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: RequestKeyboardReason;<br>API declaration: MOUSE = 1<br>DIfferences: MOUSE = 1|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: RequestKeyboardReason;<br>API declaration: TOUCH = 2<br>DIfferences: TOUCH = 2|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: RequestKeyboardReason;<br>API declaration: OTHER = 20<br>DIfferences: OTHER = 20|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: inputMethod;<br>API declaration: export type SetPreviewTextCallback = (text: string, range: Range) => void;<br>DIfferences: export type SetPreviewTextCallback = (text: string, range: Range) => void;|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: inputMethod;<br>API declaration: export enum CapitalizeMode<br>DIfferences: export enum CapitalizeMode|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: CapitalizeMode;<br>API declaration: NONE = 0<br>DIfferences: NONE = 0|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: CapitalizeMode;<br>API declaration: SENTENCES<br>DIfferences: SENTENCES|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: CapitalizeMode;<br>API declaration: WORDS<br>DIfferences: WORDS|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: CapitalizeMode;<br>API declaration: CHARACTERS<br>DIfferences: CHARACTERS|api/@ohos.inputMethod.d.ts|
|New API |NA|Class name: Panel;<br>API declaration: adjustPanelRect(flag: PanelFlag, rect: EnhancedPanelRect): void;<br>DIfferences: adjustPanelRect(flag: PanelFlag, rect: EnhancedPanelRect): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_USER_NAME: number = 10;<br>DIfferences: const PATTERN_USER_NAME: number = 10;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_NEW_PASSWORD: number = 11;<br>DIfferences: const PATTERN_NEW_PASSWORD: number = 11;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_NUMBER_DECIMAL: number = 12;<br>DIfferences: const PATTERN_NUMBER_DECIMAL: number = 12;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_ONE_TIME_CODE: number = 13;<br>DIfferences: const PATTERN_ONE_TIME_CODE: number = 13;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: export type SizeChangeCallback = (size: window.Size, keyboardArea?: KeyboardArea) => void;<br>DIfferences: export type SizeChangeCallback = (size: window.Size, keyboardArea?: KeyboardArea) => void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;<br>DIfferences: on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;<br>DIfferences: off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'discardTypingText', callback: Callback\<void>): void;<br>DIfferences: on(type: 'discardTypingText', callback: Callback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'discardTypingText', callback?: Callback\<void>): void;<br>DIfferences: off(type: 'discardTypingText', callback?: Callback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: InputClient;<br>API declaration: sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise\<void>;<br>DIfferences: sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: InputClient;<br>API declaration: recvMessage(msgHandler?: MessageHandler): void;<br>DIfferences: recvMessage(msgHandler?: MessageHandler): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: InputClient;<br>API declaration: getAttachOptions(): AttachOptions;<br>DIfferences: getAttachOptions(): AttachOptions;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: InputClient;<br>API declaration: on(type: 'attachOptionsDidChange', callback: Callback\<AttachOptions>): void;<br>DIfferences: on(type: 'attachOptionsDidChange', callback: Callback\<AttachOptions>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: InputClient;<br>API declaration: off(type: 'attachOptionsDidChange', callback?: Callback\<AttachOptions>): void;<br>DIfferences: off(type: 'attachOptionsDidChange', callback?: Callback\<AttachOptions>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: export enum ImmersiveMode<br>DIfferences: export enum ImmersiveMode|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: ImmersiveMode;<br>API declaration: NONE_IMMERSIVE = 0<br>DIfferences: NONE_IMMERSIVE = 0|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: ImmersiveMode;<br>API declaration: IMMERSIVE<br>DIfferences: IMMERSIVE|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: ImmersiveMode;<br>API declaration: LIGHT_IMMERSIVE<br>DIfferences: LIGHT_IMMERSIVE|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: ImmersiveMode;<br>API declaration: DARK_IMMERSIVE<br>DIfferences: DARK_IMMERSIVE|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: export enum GradientMode<br>DIfferences: export enum GradientMode|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: GradientMode;<br>API declaration: NONE = 0<br>DIfferences: NONE = 0|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: GradientMode;<br>API declaration: LINEAR_GRADIENT = 1<br>DIfferences: LINEAR_GRADIENT = 1|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: interface ImmersiveEffect<br>DIfferences: interface ImmersiveEffect|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: ImmersiveEffect;<br>API declaration: gradientHeight: number;<br>DIfferences: gradientHeight: number;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: ImmersiveEffect;<br>API declaration: gradientMode: GradientMode;<br>DIfferences: gradientMode: GradientMode;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: export enum RequestKeyboardReason<br>DIfferences: export enum RequestKeyboardReason|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: RequestKeyboardReason;<br>API declaration: NONE = 0<br>DIfferences: NONE = 0|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: RequestKeyboardReason;<br>API declaration: MOUSE = 1<br>DIfferences: MOUSE = 1|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: RequestKeyboardReason;<br>API declaration: TOUCH = 2<br>DIfferences: TOUCH = 2|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: RequestKeyboardReason;<br>API declaration: OTHER = 20<br>DIfferences: OTHER = 20|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: Panel;<br>API declaration: startMoving(): void;<br>DIfferences: startMoving(): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: Panel;<br>API declaration: getDisplayId(): Promise\<number>;<br>DIfferences: getDisplayId(): Promise\<number>;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: Panel;<br>API declaration: updateRegion(inputRegion: Array\<window.Rect>): void;<br>DIfferences: updateRegion(inputRegion: Array\<window.Rect>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: Panel;<br>API declaration: setImmersiveMode(mode: ImmersiveMode): void;<br>DIfferences: setImmersiveMode(mode: ImmersiveMode): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: Panel;<br>API declaration: getImmersiveMode(): ImmersiveMode;<br>DIfferences: getImmersiveMode(): ImmersiveMode;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: Panel;<br>API declaration: setImmersiveEffect(effect: ImmersiveEffect): void;<br>DIfferences: setImmersiveEffect(effect: ImmersiveEffect): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: Panel;<br>API declaration: setKeepScreenOn(isKeepScreenOn: boolean): Promise\<void>;<br>DIfferences: setKeepScreenOn(isKeepScreenOn: boolean): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EditorAttribute;<br>API declaration: readonly immersiveMode?: ImmersiveMode;<br>DIfferences: readonly immersiveMode?: ImmersiveMode;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EditorAttribute;<br>API declaration: readonly windowId?: number;<br>DIfferences: readonly windowId?: number;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EditorAttribute;<br>API declaration: readonly displayId?: number;<br>DIfferences: readonly displayId?: number;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EditorAttribute;<br>API declaration: readonly placeholder?: string;<br>DIfferences: readonly placeholder?: string;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EditorAttribute;<br>API declaration: readonly abilityName?: string;<br>DIfferences: readonly abilityName?: string;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EditorAttribute;<br>API declaration: readonly capitalizeMode?: CapitalizeMode;<br>DIfferences: readonly capitalizeMode?: CapitalizeMode;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EditorAttribute;<br>API declaration: readonly gradientMode?: GradientMode;<br>DIfferences: readonly gradientMode?: GradientMode;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: PanelFlag;<br>API declaration: FLAG_CANDIDATE<br>DIfferences: FLAG_CANDIDATE|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: interface MessageHandler<br>DIfferences: interface MessageHandler|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: MessageHandler;<br>API declaration: onMessage(msgId: string, msgParam?: ArrayBuffer): void;<br>DIfferences: onMessage(msgId: string, msgParam?: ArrayBuffer): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: MessageHandler;<br>API declaration: onTerminated(): void;<br>DIfferences: onTerminated(): void;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: export interface EnhancedPanelRect<br>DIfferences: export interface EnhancedPanelRect|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EnhancedPanelRect;<br>API declaration: landscapeRect?: window.Rect;<br>DIfferences: landscapeRect?: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EnhancedPanelRect;<br>API declaration: portraitRect?: window.Rect;<br>DIfferences: portraitRect?: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EnhancedPanelRect;<br>API declaration: landscapeAvoidY?: number;<br>DIfferences: landscapeAvoidY?: number;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EnhancedPanelRect;<br>API declaration: landscapeInputRegion?: Array\<window.Rect>;<br>DIfferences: landscapeInputRegion?: Array\<window.Rect>;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EnhancedPanelRect;<br>API declaration: portraitAvoidY?: number;<br>DIfferences: portraitAvoidY?: number;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EnhancedPanelRect;<br>API declaration: portraitInputRegion?: Array\<window.Rect>;<br>DIfferences: portraitInputRegion?: Array\<window.Rect>;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: EnhancedPanelRect;<br>API declaration: fullScreenMode?: boolean;<br>DIfferences: fullScreenMode?: boolean;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: export interface KeyboardArea<br>DIfferences: export interface KeyboardArea|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: KeyboardArea;<br>API declaration: top: number;<br>DIfferences: top: number;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: KeyboardArea;<br>API declaration: bottom: number;<br>DIfferences: bottom: number;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: KeyboardArea;<br>API declaration: left: number;<br>DIfferences: left: number;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: KeyboardArea;<br>API declaration: right: number;<br>DIfferences: right: number;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: export interface AttachOptions<br>DIfferences: export interface AttachOptions|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: AttachOptions;<br>API declaration: requestKeyboardReason?: RequestKeyboardReason;<br>DIfferences: requestKeyboardReason?: RequestKeyboardReason;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: AttachOptions;<br>API declaration: isSimpleKeyboardEnabled?: boolean;<br>DIfferences: isSimpleKeyboardEnabled?: boolean;|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: inputMethodEngine;<br>API declaration: export enum CapitalizeMode<br>DIfferences: export enum CapitalizeMode|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: CapitalizeMode;<br>API declaration: NONE = 0<br>DIfferences: NONE = 0|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: CapitalizeMode;<br>API declaration: SENTENCES<br>DIfferences: SENTENCES|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: CapitalizeMode;<br>API declaration: WORDS<br>DIfferences: WORDS|api/@ohos.inputMethodEngine.d.ts|
|New API |NA|Class name: CapitalizeMode;<br>API declaration: CHARACTERS<br>DIfferences: CHARACTERS|api/@ohos.inputMethodEngine.d.ts|
|Function change|Class name: Panel;<br>API declaration: on(type: 'sizeChange', callback: Callback\<window.Size>): void;<br>DIfferences: callback: Callback\<window.Size>|Class name: Panel;<br>API declaration: on(type: 'sizeChange', callback: SizeChangeCallback): void;<br>DIfferences: callback: SizeChangeCallback|api/@ohos.inputMethodEngine.d.ts|
|Function change|Class name: Panel;<br>API declaration: off(type: 'sizeChange', callback?: Callback\<window.Size>): void;<br>DIfferences: callback?: Callback\<window.Size>|Class name: Panel;<br>API declaration: off(type: 'sizeChange', callback?: SizeChangeCallback): void;<br>DIfferences: callback?: SizeChangeCallback|api/@ohos.inputMethodEngine.d.ts|
