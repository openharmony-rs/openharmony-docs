| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|Deleted error code|Class name: InputMethodExtensionAbility;<br>API declaration: onCreate(want: Want): void;<br>Differences: 401|Class name: InputMethodExtensionAbility;<br>API declaration: onCreate(want: Want): void;<br>Differences: NA|api/@ohos.InputMethodExtensionAbility.d.ts|
|Deleted error code|Class name: InputMethodExtensionAbility;<br>API declaration: onDestroy(): void;<br>Differences: 401|Class name: InputMethodExtensionAbility;<br>API declaration: onDestroy(): void;<br>Differences: NA|api/@ohos.InputMethodExtensionAbility.d.ts|
|New API|NA|Class name: EnterKeyType;<br>API declaration: NEWLINE<br>Differences: NEWLINE|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const ENTER_KEY_TYPE_NEWLINE: 8;<br>Differences: const ENTER_KEY_TYPE_NEWLINE: 8;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: type CommandDataType = number \| string \| boolean;<br>Differences: type CommandDataType = number \| string \| boolean;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'privateCommand', callback: Callback\<Record\<string, CommandDataType>>): void;<br>Differences: on(type: 'privateCommand', callback: Callback\<Record\<string, CommandDataType>>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'privateCommand', callback?: Callback\<Record\<string, CommandDataType>>): void;<br>Differences: off(type: 'privateCommand', callback?: Callback\<Record\<string, CommandDataType>>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: sendPrivateCommand(commandData: Record\<string, CommandDataType>): Promise\<void>;<br>Differences: sendPrivateCommand(commandData: Record\<string, CommandDataType>): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getCallingWindowInfo(): Promise\<WindowInfo>;<br>Differences: getCallingWindowInfo(): Promise\<WindowInfo>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: setPreviewText(text: string, range: Range): Promise\<void>;<br>Differences: setPreviewText(text: string, range: Range): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: setPreviewTextSync(text: string, range: Range): void;<br>Differences: setPreviewTextSync(text: string, range: Range): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: finishTextPreview(): Promise\<void>;<br>Differences: finishTextPreview(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: finishTextPreviewSync(): void;<br>Differences: finishTextPreviewSync(): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: adjustPanelRect(flag: PanelFlag, rect: PanelRect): void;<br>Differences: adjustPanelRect(flag: PanelFlag, rect: PanelRect): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: on(type: 'sizeChange', callback: Callback\<window.Size>): void;<br>Differences: on(type: 'sizeChange', callback: Callback\<window.Size>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: off(type: 'sizeChange', callback?: Callback\<window.Size>): void;<br>Differences: off(type: 'sizeChange', callback?: Callback\<window.Size>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: EditorAttribute;<br>API declaration: isTextPreviewSupported: boolean;<br>Differences: isTextPreviewSupported: boolean;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export interface WindowInfo<br>Differences: export interface WindowInfo|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: WindowInfo;<br>API declaration: rect: window.Rect;<br>Differences: rect: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: WindowInfo;<br>API declaration: status: window.WindowStatusType;<br>Differences: status: window.WindowStatusType;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export interface PanelRect<br>Differences: export interface PanelRect|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: PanelRect;<br>API declaration: landscapeRect: window.Rect;<br>Differences: landscapeRect: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: PanelRect;<br>API declaration: portraitRect: window.Rect;<br>Differences: portraitRect: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodExtensionContext;<br>API declaration: startAbility(want: Want): Promise\<void>;<br>Differences: startAbility(want: Want): Promise\<void>;|api/@ohos.InputMethodExtensionContext.d.ts|
