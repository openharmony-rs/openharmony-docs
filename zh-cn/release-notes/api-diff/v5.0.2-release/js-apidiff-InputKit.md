| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace inputConsumer<br>差异内容：declare namespace inputConsumer|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：interface HotkeyOptions<br>差异内容：interface HotkeyOptions|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：HotkeyOptions；<br>API声明：preKeys: Array\<number>;<br>差异内容：preKeys: Array\<number>;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：HotkeyOptions；<br>API声明：finalKey: number;<br>差异内容：finalKey: number;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：HotkeyOptions；<br>API声明：isRepeat?: boolean;<br>差异内容：isRepeat?: boolean;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：function getAllSystemHotkeys(): Promise\<Array\<HotkeyOptions>>;<br>差异内容：function getAllSystemHotkeys(): Promise\<Array\<HotkeyOptions>>;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：function on(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback: Callback\<HotkeyOptions>): void;<br>差异内容：function on(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback: Callback\<HotkeyOptions>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：function off(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback?: Callback\<HotkeyOptions>): void;<br>差异内容：function off(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback?: Callback\<HotkeyOptions>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputDevice；<br>API声明：function getIntervalSinceLastInput(): Promise\<number>;<br>差异内容：function getIntervalSinceLastInput(): Promise\<number>;|api/@ohos.multimodalInput.inputDevice.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimodalInput.inputConsumer.d.ts<br>差异内容：InputKit|api/@ohos.multimodalInput.inputConsumer.d.ts|
