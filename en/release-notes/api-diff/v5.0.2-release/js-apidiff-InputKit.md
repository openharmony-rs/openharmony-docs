| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace inputConsumer<br>DIfferences: declare namespace inputConsumer|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: inputConsumer;<br>API declaration: interface HotkeyOptions<br>DIfferences: interface HotkeyOptions|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: HotkeyOptions;<br>API declaration: preKeys: Array\<number>;<br>DIfferences: preKeys: Array\<number>;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: HotkeyOptions;<br>API declaration: finalKey: number;<br>DIfferences: finalKey: number;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: HotkeyOptions;<br>API declaration: isRepeat?: boolean;<br>DIfferences: isRepeat?: boolean;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: inputConsumer;<br>API declaration: function getAllSystemHotkeys(): Promise\<Array\<HotkeyOptions>>;<br>DIfferences: function getAllSystemHotkeys(): Promise\<Array\<HotkeyOptions>>;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: inputConsumer;<br>API declaration: function on(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback: Callback\<HotkeyOptions>): void;<br>DIfferences: function on(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback: Callback\<HotkeyOptions>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: inputConsumer;<br>API declaration: function off(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback?: Callback\<HotkeyOptions>): void;<br>DIfferences: function off(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback?: Callback\<HotkeyOptions>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: inputDevice;<br>API declaration: function getIntervalSinceLastInput(): Promise\<number>;<br>DIfferences: function getIntervalSinceLastInput(): Promise\<number>;|api/@ohos.multimodalInput.inputDevice.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: api\@ohos.multimodalInput.inputConsumer.d.ts<br>DIfferences: InputKit|api/@ohos.multimodalInput.inputConsumer.d.ts|
