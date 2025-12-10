| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API废弃版本变更|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>差异内容：18|api/@ohos.inputMethod.d.ts|
|API废弃版本变更|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(): Promise\<boolean>;<br>差异内容：NA|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(): Promise\<boolean>;<br>差异内容：18|api/@ohos.inputMethod.d.ts|
|新增错误码|类名：Panel；<br>API声明：startMoving(): void;<br>差异内容：NA|类名：Panel；<br>API声明：startMoving(): void;<br>差异内容：801|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;<br>差异内容：on(type: 'setPreviewText', callback: SetPreviewTextCallback): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;<br>差异内容：off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'finishTextPreview', callback: Callback\<void>): void;<br>差异内容：on(type: 'finishTextPreview', callback: Callback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'finishTextPreview', callback?: Callback\<void>): void;<br>差异内容：off(type: 'finishTextPreview', callback?: Callback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export type SetPreviewTextCallback = (text: string, range: Range) => void;<br>差异内容：export type SetPreviewTextCallback = (text: string, range: Range) => void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;<br>差异内容：on(type: 'callingDisplayDidChange', callback: Callback\<number>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;<br>差异内容：off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly windowId?: number;<br>差异内容：readonly windowId?: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly displayId?: number;<br>差异内容：readonly displayId?: number;|api/@ohos.inputMethodEngine.d.ts|
