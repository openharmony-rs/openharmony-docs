| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New error code|Class name: pointer;<br>API declaration: function setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void;<br>DIfferences: NA|Class name: pointer;<br>API declaration: function setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void;<br>DIfferences: 801|api/@ohos.multimodalInput.pointer.d.ts|
|New error code|Class name: pointer;<br>API declaration: function setPointerVisible(visible: boolean): Promise\<void>;<br>DIfferences: NA|Class name: pointer;<br>API declaration: function setPointerVisible(visible: boolean): Promise\<void>;<br>DIfferences: 801|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: PointerStyle;<br>API declaration: MIDDLE_BTN_EAST_WEST<br>DIfferences: MIDDLE_BTN_EAST_WEST|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: PointerStyle;<br>API declaration: SCREENRECORDER_CURSOR = 48<br>DIfferences: SCREENRECORDER_CURSOR = 48|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: RightClickType;<br>API declaration: TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON = 4<br>DIfferences: TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON = 4|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: RightClickType;<br>API declaration: TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON = 5<br>DIfferences: TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON = 5|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: pointer;<br>API declaration: interface CustomCursor<br>DIfferences: interface CustomCursor|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: CustomCursor;<br>API declaration: pixelMap: image.PixelMap;<br>DIfferences: pixelMap: image.PixelMap;|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: CustomCursor;<br>API declaration: focusX?: number;<br>DIfferences: focusX?: number;|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: CustomCursor;<br>API declaration: focusY?: number;<br>DIfferences: focusY?: number;|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: pointer;<br>API declaration: interface CursorConfig<br>DIfferences: interface CursorConfig|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: CursorConfig;<br>API declaration: followSystem: boolean;<br>DIfferences: followSystem: boolean;|api/@ohos.multimodalInput.pointer.d.ts|
|New API |NA|Class name: infraredEmitter;<br>API declaration: interface InfraredFrequency<br>DIfferences: interface InfraredFrequency|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|New API |NA|Class name: InfraredFrequency;<br>API declaration: max: number;<br>DIfferences: max: number;|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|New API |NA|Class name: InfraredFrequency;<br>API declaration: min: number;<br>DIfferences: min: number;|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|New API |NA|Class name: infraredEmitter;<br>API declaration: function transmitInfrared(infraredFrequency: number, pattern: Array\<number>): void;<br>DIfferences: function transmitInfrared(infraredFrequency: number, pattern: Array\<number>): void;|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|New API |NA|Class name: infraredEmitter;<br>API declaration: function getInfraredFrequencies(): Array\<InfraredFrequency>;<br>DIfferences: function getInfraredFrequencies(): Array\<InfraredFrequency>;|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|New API |NA|Class name: inputConsumer;<br>API declaration: interface KeyPressedConfig<br>DIfferences: interface KeyPressedConfig|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: KeyPressedConfig;<br>API declaration: key: number;<br>DIfferences: key: number;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: KeyPressedConfig;<br>API declaration: action: number;<br>DIfferences: action: number;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: KeyPressedConfig;<br>API declaration: isRepeat: boolean;<br>DIfferences: isRepeat: boolean;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: inputConsumer;<br>API declaration: function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback\<KeyEvent>): void;<br>DIfferences: function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback\<KeyEvent>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: inputConsumer;<br>API declaration: function off(type: 'keyPressed', callback?: Callback\<KeyEvent>): void;<br>DIfferences: function off(type: 'keyPressed', callback?: Callback\<KeyEvent>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|New API |NA|Class name: inputDevice;<br>API declaration: enum FunctionKey<br>DIfferences: enum FunctionKey|api/@ohos.multimodalInput.inputDevice.d.ts|
|New API |NA|Class name: FunctionKey;<br>API declaration: CAPS_LOCK = 1<br>DIfferences: CAPS_LOCK = 1|api/@ohos.multimodalInput.inputDevice.d.ts|
|New API |NA|Class name: inputDevice;<br>API declaration: function setFunctionKeyEnabled(functionKey: FunctionKey, enabled: boolean): Promise\<void>;<br>DIfferences: function setFunctionKeyEnabled(functionKey: FunctionKey, enabled: boolean): Promise\<void>;|api/@ohos.multimodalInput.inputDevice.d.ts|
|New API |NA|Class name: inputDevice;<br>API declaration: function isFunctionKeyEnabled(functionKey: FunctionKey): Promise\<boolean>;<br>DIfferences: function isFunctionKeyEnabled(functionKey: FunctionKey): Promise\<boolean>;|api/@ohos.multimodalInput.inputDevice.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_A = 2301<br>DIfferences: KEYCODE_BUTTON_A = 2301|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_B = 2302<br>DIfferences: KEYCODE_BUTTON_B = 2302|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_X = 2304<br>DIfferences: KEYCODE_BUTTON_X = 2304|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_Y = 2305<br>DIfferences: KEYCODE_BUTTON_Y = 2305|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_L1 = 2307<br>DIfferences: KEYCODE_BUTTON_L1 = 2307|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_R1 = 2308<br>DIfferences: KEYCODE_BUTTON_R1 = 2308|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_L2 = 2309<br>DIfferences: KEYCODE_BUTTON_L2 = 2309|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_R2 = 2310<br>DIfferences: KEYCODE_BUTTON_R2 = 2310|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_SELECT = 2311<br>DIfferences: KEYCODE_BUTTON_SELECT = 2311|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_START = 2312<br>DIfferences: KEYCODE_BUTTON_START = 2312|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_MODE = 2313<br>DIfferences: KEYCODE_BUTTON_MODE = 2313|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_THUMBL = 2314<br>DIfferences: KEYCODE_BUTTON_THUMBL = 2314|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_BUTTON_THUMBR = 2315<br>DIfferences: KEYCODE_BUTTON_THUMBR = 2315|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_DAGGER_CLICK = 3211<br>DIfferences: KEYCODE_DAGGER_CLICK = 3211|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_DAGGER_DOUBLE_CLICK = 3212<br>DIfferences: KEYCODE_DAGGER_DOUBLE_CLICK = 3212|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_DAGGER_LONG_PRESS = 3213<br>DIfferences: KEYCODE_DAGGER_LONG_PRESS = 3213|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: KeyCode;<br>API declaration: KEYCODE_DIV = 3220<br>DIfferences: KEYCODE_DIV = 3220|api/@ohos.multimodalInput.keyCode.d.ts|
|New API |NA|Class name: MouseEvent;<br>API declaration: globalX?: number;<br>DIfferences: globalX?: number;|api/@ohos.multimodalInput.mouseEvent.d.ts|
|New API |NA|Class name: MouseEvent;<br>API declaration: globalY?: number;<br>DIfferences: globalY?: number;|api/@ohos.multimodalInput.mouseEvent.d.ts|
|New API |NA|Class name: Touch;<br>API declaration: globalX?: number;<br>DIfferences: globalX?: number;|api/@ohos.multimodalInput.touchEvent.d.ts|
|New API |NA|Class name: Touch;<br>API declaration: globalY?: number;<br>DIfferences: globalY?: number;|api/@ohos.multimodalInput.touchEvent.d.ts|
