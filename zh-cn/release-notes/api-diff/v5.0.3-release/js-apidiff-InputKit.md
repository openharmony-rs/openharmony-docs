| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：801|api/@ohos.multimodalInput.pointer.d.ts|
|新增错误码|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean): Promise\<void>;<br>差异内容：NA|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean): Promise\<void>;<br>差异内容：801|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：PointerStyle；<br>API声明：MIDDLE_BTN_EAST_WEST<br>差异内容：MIDDLE_BTN_EAST_WEST|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：PointerStyle；<br>API声明：SCREENRECORDER_CURSOR = 48<br>差异内容：SCREENRECORDER_CURSOR = 48|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：RightClickType；<br>API声明：TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON = 4<br>差异内容：TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON = 4|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：RightClickType；<br>API声明：TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON = 5<br>差异内容：TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON = 5|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：pointer；<br>API声明：interface CustomCursor<br>差异内容：interface CustomCursor|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：CustomCursor；<br>API声明：pixelMap: image.PixelMap;<br>差异内容：pixelMap: image.PixelMap;|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：CustomCursor；<br>API声明：focusX?: number;<br>差异内容：focusX?: number;|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：CustomCursor；<br>API声明：focusY?: number;<br>差异内容：focusY?: number;|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：pointer；<br>API声明：interface CursorConfig<br>差异内容：interface CursorConfig|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：CursorConfig；<br>API声明：followSystem: boolean;<br>差异内容：followSystem: boolean;|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：infraredEmitter；<br>API声明：interface InfraredFrequency<br>差异内容：interface InfraredFrequency|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|新增API|NA|类名：InfraredFrequency；<br>API声明：max: number;<br>差异内容：max: number;|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|新增API|NA|类名：InfraredFrequency；<br>API声明：min: number;<br>差异内容：min: number;|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|新增API|NA|类名：infraredEmitter；<br>API声明：function transmitInfrared(infraredFrequency: number, pattern: Array\<number>): void;<br>差异内容：function transmitInfrared(infraredFrequency: number, pattern: Array\<number>): void;|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|新增API|NA|类名：infraredEmitter；<br>API声明：function getInfraredFrequencies(): Array\<InfraredFrequency>;<br>差异内容：function getInfraredFrequencies(): Array\<InfraredFrequency>;|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：interface KeyPressedConfig<br>差异内容：interface KeyPressedConfig|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：KeyPressedConfig；<br>API声明：key: number;<br>差异内容：key: number;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：KeyPressedConfig；<br>API声明：action: number;<br>差异内容：action: number;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：KeyPressedConfig；<br>API声明：isRepeat: boolean;<br>差异内容：isRepeat: boolean;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback\<KeyEvent>): void;<br>差异内容：function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback\<KeyEvent>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：function off(type: 'keyPressed', callback?: Callback\<KeyEvent>): void;<br>差异内容：function off(type: 'keyPressed', callback?: Callback\<KeyEvent>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputDevice；<br>API声明：enum FunctionKey<br>差异内容：enum FunctionKey|api/@ohos.multimodalInput.inputDevice.d.ts|
|新增API|NA|类名：FunctionKey；<br>API声明：CAPS_LOCK = 1<br>差异内容：CAPS_LOCK = 1|api/@ohos.multimodalInput.inputDevice.d.ts|
|新增API|NA|类名：inputDevice；<br>API声明：function setFunctionKeyEnabled(functionKey: FunctionKey, enabled: boolean): Promise\<void>;<br>差异内容：function setFunctionKeyEnabled(functionKey: FunctionKey, enabled: boolean): Promise\<void>;|api/@ohos.multimodalInput.inputDevice.d.ts|
|新增API|NA|类名：inputDevice；<br>API声明：function isFunctionKeyEnabled(functionKey: FunctionKey): Promise\<boolean>;<br>差异内容：function isFunctionKeyEnabled(functionKey: FunctionKey): Promise\<boolean>;|api/@ohos.multimodalInput.inputDevice.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_A = 2301<br>差异内容：KEYCODE_BUTTON_A = 2301|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_B = 2302<br>差异内容：KEYCODE_BUTTON_B = 2302|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_X = 2304<br>差异内容：KEYCODE_BUTTON_X = 2304|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_Y = 2305<br>差异内容：KEYCODE_BUTTON_Y = 2305|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_L1 = 2307<br>差异内容：KEYCODE_BUTTON_L1 = 2307|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_R1 = 2308<br>差异内容：KEYCODE_BUTTON_R1 = 2308|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_L2 = 2309<br>差异内容：KEYCODE_BUTTON_L2 = 2309|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_R2 = 2310<br>差异内容：KEYCODE_BUTTON_R2 = 2310|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_SELECT = 2311<br>差异内容：KEYCODE_BUTTON_SELECT = 2311|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_START = 2312<br>差异内容：KEYCODE_BUTTON_START = 2312|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_MODE = 2313<br>差异内容：KEYCODE_BUTTON_MODE = 2313|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_THUMBL = 2314<br>差异内容：KEYCODE_BUTTON_THUMBL = 2314|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_BUTTON_THUMBR = 2315<br>差异内容：KEYCODE_BUTTON_THUMBR = 2315|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_DAGGER_CLICK = 3211<br>差异内容：KEYCODE_DAGGER_CLICK = 3211|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_DAGGER_DOUBLE_CLICK = 3212<br>差异内容：KEYCODE_DAGGER_DOUBLE_CLICK = 3212|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_DAGGER_LONG_PRESS = 3213<br>差异内容：KEYCODE_DAGGER_LONG_PRESS = 3213|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_DIV = 3220<br>差异内容：KEYCODE_DIV = 3220|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：MouseEvent；<br>API声明：globalX?: number;<br>差异内容：globalX?: number;|api/@ohos.multimodalInput.mouseEvent.d.ts|
|新增API|NA|类名：MouseEvent；<br>API声明：globalY?: number;<br>差异内容：globalY?: number;|api/@ohos.multimodalInput.mouseEvent.d.ts|
|新增API|NA|类名：Touch；<br>API声明：globalX?: number;<br>差异内容：globalX?: number;|api/@ohos.multimodalInput.touchEvent.d.ts|
|新增API|NA|类名：Touch；<br>API声明：globalY?: number;<br>差异内容：globalY?: number;|api/@ohos.multimodalInput.touchEvent.d.ts|
