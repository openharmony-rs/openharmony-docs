| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除错误码|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：801|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.multimodalInput.pointer.d.ts|
|删除错误码|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean): Promise\<void>;<br>差异内容：801|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean): Promise\<void>;<br>差异内容：NA|api/@ohos.multimodalInput.pointer.d.ts|
|删除API|类名：inputConsumer；<br>API声明：interface KeyPressedConfig<br>差异内容：interface KeyPressedConfig|NA|api/@ohos.multimodalInput.inputConsumer.d.ts|
|删除API|类名：KeyPressedConfig；<br>API声明：key: number;<br>差异内容：key: number;|NA|api/@ohos.multimodalInput.inputConsumer.d.ts|
|删除API|类名：KeyPressedConfig；<br>API声明：action: number;<br>差异内容：action: number;|NA|api/@ohos.multimodalInput.inputConsumer.d.ts|
|删除API|类名：KeyPressedConfig；<br>API声明：isRepeat: boolean;<br>差异内容：isRepeat: boolean;|NA|api/@ohos.multimodalInput.inputConsumer.d.ts|
|删除API|类名：inputConsumer；<br>API声明：function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback\<KeyEvent>): void;<br>差异内容：function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback\<KeyEvent>): void;|NA|api/@ohos.multimodalInput.inputConsumer.d.ts|
|删除API|类名：inputConsumer；<br>API声明：function off(type: 'keyPressed', callback?: Callback\<KeyEvent>): void;<br>差异内容：function off(type: 'keyPressed', callback?: Callback\<KeyEvent>): void;|NA|api/@ohos.multimodalInput.inputConsumer.d.ts|
|删除API|类名：KeyCode；<br>API声明：KEYCODE_DAGGER_CLICK = 3211<br>差异内容：KEYCODE_DAGGER_CLICK = 3211|NA|api/@ohos.multimodalInput.keyCode.d.ts|
|删除API|类名：KeyCode；<br>API声明：KEYCODE_DAGGER_DOUBLE_CLICK = 3212<br>差异内容：KEYCODE_DAGGER_DOUBLE_CLICK = 3212|NA|api/@ohos.multimodalInput.keyCode.d.ts|
|删除API|类名：KeyCode；<br>API声明：KEYCODE_DAGGER_LONG_PRESS = 3213<br>差异内容：KEYCODE_DAGGER_LONG_PRESS = 3213|NA|api/@ohos.multimodalInput.keyCode.d.ts|
|删除API|类名：KeyCode；<br>API声明：KEYCODE_DIV = 3220<br>差异内容：KEYCODE_DIV = 3220|NA|api/@ohos.multimodalInput.keyCode.d.ts|
|删除API|类名：MouseEvent；<br>API声明：globalX?: number;<br>差异内容：globalX?: number;|NA|api/@ohos.multimodalInput.mouseEvent.d.ts|
|删除API|类名：MouseEvent；<br>API声明：globalY?: number;<br>差异内容：globalY?: number;|NA|api/@ohos.multimodalInput.mouseEvent.d.ts|
|删除API|类名：PointerStyle；<br>API声明：MIDDLE_BTN_EAST_WEST<br>差异内容：MIDDLE_BTN_EAST_WEST|NA|api/@ohos.multimodalInput.pointer.d.ts|
|删除API|类名：PointerStyle；<br>API声明：SCREENRECORDER_CURSOR = 48<br>差异内容：SCREENRECORDER_CURSOR = 48|NA|api/@ohos.multimodalInput.pointer.d.ts|
|删除API|类名：RightClickType；<br>API声明：TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON = 4<br>差异内容：TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON = 4|NA|api/@ohos.multimodalInput.pointer.d.ts|
|删除API|类名：RightClickType；<br>API声明：TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON = 5<br>差异内容：TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON = 5|NA|api/@ohos.multimodalInput.pointer.d.ts|
|删除API|类名：Touch；<br>API声明：globalX?: number;<br>差异内容：globalX?: number;|NA|api/@ohos.multimodalInput.touchEvent.d.ts|
|删除API|类名：Touch；<br>API声明：globalY?: number;<br>差异内容：globalY?: number;|NA|api/@ohos.multimodalInput.touchEvent.d.ts|
|起始版本有变化|类名：infraredEmitter；<br>API声明：interface InfraredFrequency<br>差异内容：15|类名：infraredEmitter；<br>API声明：interface InfraredFrequency<br>差异内容：12|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|起始版本有变化|类名：InfraredFrequency；<br>API声明：max: number;<br>差异内容：15|类名：InfraredFrequency；<br>API声明：max: number;<br>差异内容：12|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|起始版本有变化|类名：InfraredFrequency；<br>API声明：min: number;<br>差异内容：15|类名：InfraredFrequency；<br>API声明：min: number;<br>差异内容：12|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|起始版本有变化|类名：infraredEmitter；<br>API声明：function transmitInfrared(infraredFrequency: number, pattern: Array\<number>): void;<br>差异内容：15|类名：infraredEmitter；<br>API声明：function transmitInfrared(infraredFrequency: number, pattern: Array\<number>): void;<br>差异内容：12|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|起始版本有变化|类名：infraredEmitter；<br>API声明：function getInfraredFrequencies(): Array\<InfraredFrequency>;<br>差异内容：15|类名：infraredEmitter；<br>API声明：function getInfraredFrequencies(): Array\<InfraredFrequency>;<br>差异内容：12|api/@ohos.multimodalInput.infraredEmitter.d.ts|
