| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：801|api/@ohos.multimodalInput.pointer.d.ts|
|新增错误码|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean): Promise\<void>;<br>差异内容：NA|类名：pointer；<br>API声明：function setPointerVisible(visible: boolean): Promise\<void>;<br>差异内容：801|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：PointerStyle；<br>API声明：MIDDLE_BTN_EAST_WEST<br>差异内容：MIDDLE_BTN_EAST_WEST|api/@ohos.multimodalInput.pointer.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：interface KeyPressedConfig<br>差异内容：interface KeyPressedConfig|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：KeyPressedConfig；<br>API声明：key: number;<br>差异内容：key: number;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：KeyPressedConfig；<br>API声明：action: number;<br>差异内容：action: number;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：KeyPressedConfig；<br>API声明：isRepeat: boolean;<br>差异内容：isRepeat: boolean;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback\<KeyEvent>): void;<br>差异内容：function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback\<KeyEvent>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：inputConsumer；<br>API声明：function off(type: 'keyPressed', callback?: Callback\<KeyEvent>): void;<br>差异内容：function off(type: 'keyPressed', callback?: Callback\<KeyEvent>): void;|api/@ohos.multimodalInput.inputConsumer.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_DAGGER_CLICK = 3211<br>差异内容：KEYCODE_DAGGER_CLICK = 3211|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_DAGGER_DOUBLE_CLICK = 3212<br>差异内容：KEYCODE_DAGGER_DOUBLE_CLICK = 3212|api/@ohos.multimodalInput.keyCode.d.ts|
|新增API|NA|类名：KeyCode；<br>API声明：KEYCODE_DAGGER_LONG_PRESS = 3213<br>差异内容：KEYCODE_DAGGER_LONG_PRESS = 3213|api/@ohos.multimodalInput.keyCode.d.ts|
|起始版本有变化|类名：infraredEmitter；<br>API声明：interface InfraredFrequency<br>差异内容：12|类名：infraredEmitter；<br>API声明：interface InfraredFrequency<br>差异内容：15|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|起始版本有变化|类名：InfraredFrequency；<br>API声明：max: number;<br>差异内容：12|类名：InfraredFrequency；<br>API声明：max: number;<br>差异内容：15|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|起始版本有变化|类名：InfraredFrequency；<br>API声明：min: number;<br>差异内容：12|类名：InfraredFrequency；<br>API声明：min: number;<br>差异内容：15|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|起始版本有变化|类名：infraredEmitter；<br>API声明：function transmitInfrared(infraredFrequency: number, pattern: Array\<number>): void;<br>差异内容：12|类名：infraredEmitter；<br>API声明：function transmitInfrared(infraredFrequency: number, pattern: Array\<number>): void;<br>差异内容：15|api/@ohos.multimodalInput.infraredEmitter.d.ts|
|起始版本有变化|类名：infraredEmitter；<br>API声明：function getInfraredFrequencies(): Array\<InfraredFrequency>;<br>差异内容：12|类名：infraredEmitter；<br>API声明：function getInfraredFrequencies(): Array\<InfraredFrequency>;<br>差异内容：15|api/@ohos.multimodalInput.infraredEmitter.d.ts|
