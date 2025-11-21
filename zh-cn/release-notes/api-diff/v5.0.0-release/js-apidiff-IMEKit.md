| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除错误码|类名：InputMethodExtensionAbility；<br>API声明：onCreate(want: Want): void;<br>差异内容：401|类名：InputMethodExtensionAbility；<br>API声明：onCreate(want: Want): void;<br>差异内容：NA|api/@ohos.InputMethodExtensionAbility.d.ts|
|删除错误码|类名：InputMethodExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：401|类名：InputMethodExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：NA|api/@ohos.InputMethodExtensionAbility.d.ts|
|新增API|NA|类名：EnterKeyType；<br>API声明：NEWLINE<br>差异内容：NEWLINE|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const ENTER_KEY_TYPE_NEWLINE: 8;<br>差异内容：const ENTER_KEY_TYPE_NEWLINE: 8;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：type CommandDataType = number \| string \| boolean;<br>差异内容：type CommandDataType = number \| string \| boolean;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'privateCommand', callback: Callback\<Record\<string, CommandDataType>>): void;<br>差异内容：on(type: 'privateCommand', callback: Callback\<Record\<string, CommandDataType>>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'privateCommand', callback?: Callback\<Record\<string, CommandDataType>>): void;<br>差异内容：off(type: 'privateCommand', callback?: Callback\<Record\<string, CommandDataType>>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：sendPrivateCommand(commandData: Record\<string, CommandDataType>): Promise\<void>;<br>差异内容：sendPrivateCommand(commandData: Record\<string, CommandDataType>): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getCallingWindowInfo(): Promise\<WindowInfo>;<br>差异内容：getCallingWindowInfo(): Promise\<WindowInfo>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：setPreviewText(text: string, range: Range): Promise\<void>;<br>差异内容：setPreviewText(text: string, range: Range): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：setPreviewTextSync(text: string, range: Range): void;<br>差异内容：setPreviewTextSync(text: string, range: Range): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：finishTextPreview(): Promise\<void>;<br>差异内容：finishTextPreview(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：finishTextPreviewSync(): void;<br>差异内容：finishTextPreviewSync(): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：adjustPanelRect(flag: PanelFlag, rect: PanelRect): void;<br>差异内容：adjustPanelRect(flag: PanelFlag, rect: PanelRect): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：on(type: 'sizeChange', callback: Callback\<window.Size>): void;<br>差异内容：on(type: 'sizeChange', callback: Callback\<window.Size>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：off(type: 'sizeChange', callback?: Callback\<window.Size>): void;<br>差异内容：off(type: 'sizeChange', callback?: Callback\<window.Size>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：isTextPreviewSupported: boolean;<br>差异内容：isTextPreviewSupported: boolean;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export interface WindowInfo<br>差异内容：export interface WindowInfo|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：WindowInfo；<br>API声明：rect: window.Rect;<br>差异内容：rect: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：WindowInfo；<br>API声明：status: window.WindowStatusType;<br>差异内容：status: window.WindowStatusType;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export interface PanelRect<br>差异内容：export interface PanelRect|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：PanelRect；<br>API声明：landscapeRect: window.Rect;<br>差异内容：landscapeRect: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：PanelRect；<br>API声明：portraitRect: window.Rect;<br>差异内容：portraitRect: window.Rect;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodExtensionContext；<br>API声明：startAbility(want: Want): Promise\<void>;<br>差异内容：startAbility(want: Want): Promise\<void>;|api/@ohos.InputMethodExtensionContext.d.ts|
