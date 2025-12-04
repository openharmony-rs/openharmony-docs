| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace inputMethod<br>差异内容：declare namespace inputMethod|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：const MAX_TYPE_NUM: number;<br>差异内容：const MAX_TYPE_NUM: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function getInputMethodSetting(): InputMethodSetting;<br>差异内容：function getInputMethodSetting(): InputMethodSetting;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function getInputMethodController(): InputMethodController;<br>差异内容：function getInputMethodController(): InputMethodController;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function getSetting(): InputMethodSetting;<br>差异内容：function getSetting(): InputMethodSetting;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function getController(): InputMethodController;<br>差异内容：function getController(): InputMethodController;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function getDefaultInputMethod(): InputMethodProperty;<br>差异内容：function getDefaultInputMethod(): InputMethodProperty;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function getSystemInputMethodConfigAbility(): ElementName;<br>差异内容：function getSystemInputMethodConfigAbility(): ElementName;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback\<boolean>): void;<br>差异内容：function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function switchInputMethod(target: InputMethodProperty): Promise\<boolean>;<br>差异内容：function switchInputMethod(target: InputMethodProperty): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function getCurrentInputMethod(): InputMethodProperty;<br>差异内容：function getCurrentInputMethod(): InputMethodProperty;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function switchCurrentInputMethodSubtype(target: InputMethodSubtype, callback: AsyncCallback\<boolean>): void;<br>差异内容：function switchCurrentInputMethodSubtype(target: InputMethodSubtype, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function switchCurrentInputMethodSubtype(target: InputMethodSubtype): Promise\<boolean>;<br>差异内容：function switchCurrentInputMethodSubtype(target: InputMethodSubtype): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function getCurrentInputMethodSubtype(): InputMethodSubtype;<br>差异内容：function getCurrentInputMethodSubtype(): InputMethodSubtype;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype, callback: AsyncCallback\<boolean>): void;<br>差异内容：function switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：function switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype): Promise\<boolean>;<br>差异内容：function switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：interface InputMethodSetting<br>差异内容：interface InputMethodSetting|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：on(type: 'imeChange', callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void;<br>差异内容：on(type: 'imeChange', callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：off(type: 'imeChange', callback?: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void;<br>差异内容：off(type: 'imeChange', callback?: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：listInputMethodSubtype(inputMethodProperty: InputMethodProperty, callback: AsyncCallback\<Array\<InputMethodSubtype>>): void;<br>差异内容：listInputMethodSubtype(inputMethodProperty: InputMethodProperty, callback: AsyncCallback\<Array\<InputMethodSubtype>>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：listInputMethodSubtype(inputMethodProperty: InputMethodProperty): Promise\<Array\<InputMethodSubtype>>;<br>差异内容：listInputMethodSubtype(inputMethodProperty: InputMethodProperty): Promise\<Array\<InputMethodSubtype>>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：listCurrentInputMethodSubtype(callback: AsyncCallback\<Array\<InputMethodSubtype>>): void;<br>差异内容：listCurrentInputMethodSubtype(callback: AsyncCallback\<Array\<InputMethodSubtype>>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：listCurrentInputMethodSubtype(): Promise\<Array\<InputMethodSubtype>>;<br>差异内容：listCurrentInputMethodSubtype(): Promise\<Array\<InputMethodSubtype>>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：getInputMethods(enable: boolean, callback: AsyncCallback\<Array\<InputMethodProperty>>): void;<br>差异内容：getInputMethods(enable: boolean, callback: AsyncCallback\<Array\<InputMethodProperty>>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：getInputMethods(enable: boolean): Promise\<Array\<InputMethodProperty>>;<br>差异内容：getInputMethods(enable: boolean): Promise\<Array\<InputMethodProperty>>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：getInputMethodsSync(enable: boolean): Array\<InputMethodProperty>;<br>差异内容：getInputMethodsSync(enable: boolean): Array\<InputMethodProperty>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：getAllInputMethods(callback: AsyncCallback\<Array\<InputMethodProperty>>): void;<br>差异内容：getAllInputMethods(callback: AsyncCallback\<Array\<InputMethodProperty>>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：getAllInputMethods(): Promise\<Array\<InputMethodProperty>>;<br>差异内容：getAllInputMethods(): Promise\<Array\<InputMethodProperty>>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：getAllInputMethodsSync(): Array\<InputMethodProperty>;<br>差异内容：getAllInputMethodsSync(): Array\<InputMethodProperty>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：listInputMethod(callback: AsyncCallback\<Array\<InputMethodProperty>>): void;<br>差异内容：listInputMethod(callback: AsyncCallback\<Array\<InputMethodProperty>>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：listInputMethod(): Promise\<Array\<InputMethodProperty>>;<br>差异内容：listInputMethod(): Promise\<Array\<InputMethodProperty>>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>差异内容：showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：showOptionalInputMethods(): Promise\<boolean>;<br>差异内容：showOptionalInputMethods(): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：displayOptionalInputMethod(callback: AsyncCallback\<void>): void;<br>差异内容：displayOptionalInputMethod(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodSetting；<br>API声明：displayOptionalInputMethod(): Promise\<void>;<br>差异内容：displayOptionalInputMethod(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：interface InputMethodController<br>差异内容：interface InputMethodController|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：attach(showKeyboard: boolean, textConfig: TextConfig, callback: AsyncCallback\<void>): void;<br>差异内容：attach(showKeyboard: boolean, textConfig: TextConfig, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：attach(showKeyboard: boolean, textConfig: TextConfig): Promise\<void>;<br>差异内容：attach(showKeyboard: boolean, textConfig: TextConfig): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：showTextInput(callback: AsyncCallback\<void>): void;<br>差异内容：showTextInput(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：showTextInput(): Promise\<void>;<br>差异内容：showTextInput(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：hideTextInput(callback: AsyncCallback\<void>): void;<br>差异内容：hideTextInput(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：hideTextInput(): Promise\<void>;<br>差异内容：hideTextInput(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：detach(callback: AsyncCallback\<void>): void;<br>差异内容：detach(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：detach(): Promise\<void>;<br>差异内容：detach(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：setCallingWindow(windowId: number, callback: AsyncCallback\<void>): void;<br>差异内容：setCallingWindow(windowId: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：setCallingWindow(windowId: number): Promise\<void>;<br>差异内容：setCallingWindow(windowId: number): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：updateCursor(cursorInfo: CursorInfo, callback: AsyncCallback\<void>): void;<br>差异内容：updateCursor(cursorInfo: CursorInfo, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：updateCursor(cursorInfo: CursorInfo): Promise\<void>;<br>差异内容：updateCursor(cursorInfo: CursorInfo): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：changeSelection(text: string, start: number, end: number, callback: AsyncCallback\<void>): void;<br>差异内容：changeSelection(text: string, start: number, end: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：changeSelection(text: string, start: number, end: number): Promise\<void>;<br>差异内容：changeSelection(text: string, start: number, end: number): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：updateAttribute(attribute: InputAttribute, callback: AsyncCallback\<void>): void;<br>差异内容：updateAttribute(attribute: InputAttribute, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：updateAttribute(attribute: InputAttribute): Promise\<void>;<br>差异内容：updateAttribute(attribute: InputAttribute): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：stopInputSession(callback: AsyncCallback\<boolean>): void;<br>差异内容：stopInputSession(callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：stopInputSession(): Promise\<boolean>;<br>差异内容：stopInputSession(): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：stopInput(callback: AsyncCallback\<boolean>): void;<br>差异内容：stopInput(callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：stopInput(): Promise\<boolean>;<br>差异内容：stopInput(): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：showSoftKeyboard(callback: AsyncCallback\<void>): void;<br>差异内容：showSoftKeyboard(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：showSoftKeyboard(): Promise\<void>;<br>差异内容：showSoftKeyboard(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：hideSoftKeyboard(callback: AsyncCallback\<void>): void;<br>差异内容：hideSoftKeyboard(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：hideSoftKeyboard(): Promise\<void>;<br>差异内容：hideSoftKeyboard(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'selectByRange', callback: Callback\<Range>): void;<br>差异内容：on(type: 'selectByRange', callback: Callback\<Range>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'selectByRange', callback?: Callback\<Range>): void;<br>差异内容：off(type: 'selectByRange', callback?: Callback\<Range>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'selectByMovement', callback: Callback\<Movement>): void;<br>差异内容：on(type: 'selectByMovement', callback: Callback\<Movement>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'selectByMovement', callback?: Callback\<Movement>): void;<br>差异内容：off(type: 'selectByMovement', callback?: Callback\<Movement>): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'insertText', callback: (text: string) => void): void;<br>差异内容：on(type: 'insertText', callback: (text: string) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'insertText', callback?: (text: string) => void): void;<br>差异内容：off(type: 'insertText', callback?: (text: string) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'deleteLeft', callback: (length: number) => void): void;<br>差异内容：on(type: 'deleteLeft', callback: (length: number) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'deleteLeft', callback?: (length: number) => void): void;<br>差异内容：off(type: 'deleteLeft', callback?: (length: number) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'deleteRight', callback: (length: number) => void): void;<br>差异内容：on(type: 'deleteRight', callback: (length: number) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'deleteRight', callback?: (length: number) => void): void;<br>差异内容：off(type: 'deleteRight', callback?: (length: number) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'sendKeyboardStatus', callback: (keyboardStatus: KeyboardStatus) => void): void;<br>差异内容：on(type: 'sendKeyboardStatus', callback: (keyboardStatus: KeyboardStatus) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'sendKeyboardStatus', callback?: (keyboardStatus: KeyboardStatus) => void): void;<br>差异内容：off(type: 'sendKeyboardStatus', callback?: (keyboardStatus: KeyboardStatus) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'sendFunctionKey', callback: (functionKey: FunctionKey) => void): void;<br>差异内容：on(type: 'sendFunctionKey', callback: (functionKey: FunctionKey) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'sendFunctionKey', callback?: (functionKey: FunctionKey) => void): void;<br>差异内容：off(type: 'sendFunctionKey', callback?: (functionKey: FunctionKey) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'moveCursor', callback: (direction: Direction) => void): void;<br>差异内容：on(type: 'moveCursor', callback: (direction: Direction) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'moveCursor', callback?: (direction: Direction) => void): void;<br>差异内容：off(type: 'moveCursor', callback?: (direction: Direction) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'handleExtendAction', callback: (action: ExtendAction) => void): void;<br>差异内容：on(type: 'handleExtendAction', callback: (action: ExtendAction) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'handleExtendAction', callback?: (action: ExtendAction) => void): void;<br>差异内容：off(type: 'handleExtendAction', callback?: (action: ExtendAction) => void): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'getLeftTextOfCursor', callback: (length: number) => string): void;<br>差异内容：on(type: 'getLeftTextOfCursor', callback: (length: number) => string): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'getLeftTextOfCursor', callback?: (length: number) => string): void;<br>差异内容：off(type: 'getLeftTextOfCursor', callback?: (length: number) => string): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'getRightTextOfCursor', callback: (length: number) => string): void;<br>差异内容：on(type: 'getRightTextOfCursor', callback: (length: number) => string): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'getRightTextOfCursor', callback?: (length: number) => string): void;<br>差异内容：off(type: 'getRightTextOfCursor', callback?: (length: number) => string): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：on(type: 'getTextIndexAtCursor', callback: () => number): void;<br>差异内容：on(type: 'getTextIndexAtCursor', callback: () => number): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodController；<br>API声明：off(type: 'getTextIndexAtCursor', callback?: () => number): void;<br>差异内容：off(type: 'getTextIndexAtCursor', callback?: () => number): void;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：interface InputMethodProperty<br>差异内容：interface InputMethodProperty|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：readonly packageName: string;<br>差异内容：readonly packageName: string;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：readonly methodId: string;<br>差异内容：readonly methodId: string;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：readonly id: string;<br>差异内容：readonly id: string;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：readonly label?: string;<br>差异内容：readonly label?: string;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：readonly labelId?: number;<br>差异内容：readonly labelId?: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：readonly icon?: string;<br>差异内容：readonly icon?: string;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：readonly iconId?: number;<br>差异内容：readonly iconId?: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputMethodProperty；<br>API声明：extra?: object;<br>差异内容：extra?: object;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export enum Direction<br>差异内容：export enum Direction|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：Direction；<br>API声明：CURSOR_UP = 1<br>差异内容：CURSOR_UP = 1|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：Direction；<br>API声明：CURSOR_DOWN<br>差异内容：CURSOR_DOWN|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：Direction；<br>API声明：CURSOR_LEFT<br>差异内容：CURSOR_LEFT|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：Direction；<br>API声明：CURSOR_RIGHT<br>差异内容：CURSOR_RIGHT|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export interface Range<br>差异内容：export interface Range|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：Range；<br>API声明：start: number;<br>差异内容：start: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：Range；<br>API声明：end: number;<br>差异内容：end: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export interface Movement<br>差异内容：export interface Movement|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：Movement；<br>API声明：direction: Direction;<br>差异内容：direction: Direction;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export enum TextInputType<br>差异内容：export enum TextInputType|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：NONE = -1<br>差异内容：NONE = -1|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：TEXT = 0<br>差异内容：TEXT = 0|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：MULTILINE<br>差异内容：MULTILINE|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：NUMBER<br>差异内容：NUMBER|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：PHONE<br>差异内容：PHONE|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：DATETIME<br>差异内容：DATETIME|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：EMAIL_ADDRESS<br>差异内容：EMAIL_ADDRESS|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：URL<br>差异内容：URL|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：VISIBLE_PASSWORD<br>差异内容：VISIBLE_PASSWORD|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextInputType；<br>API声明：NUMBER_PASSWORD<br>差异内容：NUMBER_PASSWORD|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export enum EnterKeyType<br>差异内容：export enum EnterKeyType|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnterKeyType；<br>API声明：UNSPECIFIED = 0<br>差异内容：UNSPECIFIED = 0|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnterKeyType；<br>API声明：NONE<br>差异内容：NONE|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnterKeyType；<br>API声明：GO<br>差异内容：GO|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnterKeyType；<br>API声明：SEARCH<br>差异内容：SEARCH|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnterKeyType；<br>API声明：SEND<br>差异内容：SEND|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnterKeyType；<br>API声明：NEXT<br>差异内容：NEXT|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnterKeyType；<br>API声明：DONE<br>差异内容：DONE|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：EnterKeyType；<br>API声明：PREVIOUS<br>差异内容：PREVIOUS|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export enum KeyboardStatus<br>差异内容：export enum KeyboardStatus|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：KeyboardStatus；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：KeyboardStatus；<br>API声明：HIDE = 1<br>差异内容：HIDE = 1|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：KeyboardStatus；<br>API声明：SHOW = 2<br>差异内容：SHOW = 2|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export interface InputAttribute<br>差异内容：export interface InputAttribute|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputAttribute；<br>API声明：textInputType: TextInputType;<br>差异内容：textInputType: TextInputType;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputAttribute；<br>API声明：enterKeyType: EnterKeyType;<br>差异内容：enterKeyType: EnterKeyType;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export interface FunctionKey<br>差异内容：export interface FunctionKey|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：FunctionKey；<br>API声明：enterKeyType: EnterKeyType;<br>差异内容：enterKeyType: EnterKeyType;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export interface CursorInfo<br>差异内容：export interface CursorInfo|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：CursorInfo；<br>API声明：left: number;<br>差异内容：left: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：CursorInfo；<br>API声明：top: number;<br>差异内容：top: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：CursorInfo；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：CursorInfo；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export interface TextConfig<br>差异内容：export interface TextConfig|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextConfig；<br>API声明：inputAttribute: InputAttribute;<br>差异内容：inputAttribute: InputAttribute;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextConfig；<br>API声明：cursorInfo?: CursorInfo;<br>差异内容：cursorInfo?: CursorInfo;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextConfig；<br>API声明：selection?: Range;<br>差异内容：selection?: Range;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：TextConfig；<br>API声明：windowId?: number;<br>差异内容：windowId?: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export enum ExtendAction<br>差异内容：export enum ExtendAction|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：ExtendAction；<br>API声明：SELECT_ALL = 0<br>差异内容：SELECT_ALL = 0|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：ExtendAction；<br>API声明：CUT = 3<br>差异内容：CUT = 3|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：ExtendAction；<br>API声明：COPY = 4<br>差异内容：COPY = 4|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：ExtendAction；<br>API声明：PASTE = 5<br>差异内容：PASTE = 5|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：inputMethod；<br>API声明：export interface InputWindowInfo<br>差异内容：export interface InputWindowInfo|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputWindowInfo；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputWindowInfo；<br>API声明：left: number;<br>差异内容：left: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputWindowInfo；<br>API声明：top: number;<br>差异内容：top: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputWindowInfo；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：InputWindowInfo；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.inputMethod.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface PanelInfo<br>差异内容：export interface PanelInfo|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：PanelInfo；<br>API声明：type: PanelType;<br>差异内容：type: PanelType;|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：PanelInfo；<br>API声明：flag?: PanelFlag;<br>差异内容：flag?: PanelFlag;|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum PanelFlag<br>差异内容：export enum PanelFlag|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：PanelFlag；<br>API声明：FLAG_FIXED = 0<br>差异内容：FLAG_FIXED = 0|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：PanelFlag；<br>API声明：FLAG_FLOATING<br>差异内容：FLAG_FLOATING|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：PanelFlag；<br>API声明：FLAG_CANDIDATE<br>差异内容：FLAG_CANDIDATE|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum PanelType<br>差异内容：export enum PanelType|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：PanelType；<br>API声明：SOFT_KEYBOARD = 0<br>差异内容：SOFT_KEYBOARD = 0|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：PanelType；<br>API声明：STATUS_BAR<br>差异内容：STATUS_BAR|api/@ohos.inputMethod.Panel.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace inputMethodEngine<br>差异内容：declare namespace inputMethodEngine|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const ENTER_KEY_TYPE_UNSPECIFIED: number;<br>差异内容：const ENTER_KEY_TYPE_UNSPECIFIED: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const ENTER_KEY_TYPE_GO: number;<br>差异内容：const ENTER_KEY_TYPE_GO: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const ENTER_KEY_TYPE_SEARCH: number;<br>差异内容：const ENTER_KEY_TYPE_SEARCH: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const ENTER_KEY_TYPE_SEND: number;<br>差异内容：const ENTER_KEY_TYPE_SEND: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const ENTER_KEY_TYPE_NEXT: number;<br>差异内容：const ENTER_KEY_TYPE_NEXT: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const ENTER_KEY_TYPE_DONE: number;<br>差异内容：const ENTER_KEY_TYPE_DONE: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const ENTER_KEY_TYPE_PREVIOUS: number;<br>差异内容：const ENTER_KEY_TYPE_PREVIOUS: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_NULL: number;<br>差异内容：const PATTERN_NULL: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_TEXT: number;<br>差异内容：const PATTERN_TEXT: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_NUMBER: number;<br>差异内容：const PATTERN_NUMBER: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_PHONE: number;<br>差异内容：const PATTERN_PHONE: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_DATETIME: number;<br>差异内容：const PATTERN_DATETIME: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_EMAIL: number;<br>差异内容：const PATTERN_EMAIL: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_URI: number;<br>差异内容：const PATTERN_URI: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_PASSWORD: number;<br>差异内容：const PATTERN_PASSWORD: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_PASSWORD_SCREEN_LOCK: number;<br>差异内容：const PATTERN_PASSWORD_SCREEN_LOCK: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const PATTERN_PASSWORD_NUMBER: number;<br>差异内容：const PATTERN_PASSWORD_NUMBER: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const FLAG_SELECTING: number;<br>差异内容：const FLAG_SELECTING: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const FLAG_SINGLE_LINE: number;<br>差异内容：const FLAG_SINGLE_LINE: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const DISPLAY_MODE_PART: number;<br>差异内容：const DISPLAY_MODE_PART: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const DISPLAY_MODE_FULL: number;<br>差异内容：const DISPLAY_MODE_FULL: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const OPTION_ASCII: number;<br>差异内容：const OPTION_ASCII: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const OPTION_NONE: number;<br>差异内容：const OPTION_NONE: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const OPTION_AUTO_CAP_CHARACTERS: number;<br>差异内容：const OPTION_AUTO_CAP_CHARACTERS: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const OPTION_AUTO_CAP_SENTENCES: number;<br>差异内容：const OPTION_AUTO_CAP_SENTENCES: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const OPTION_AUTO_WORDS: number;<br>差异内容：const OPTION_AUTO_WORDS: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const OPTION_MULTI_LINE: number;<br>差异内容：const OPTION_MULTI_LINE: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const OPTION_NO_FULLSCREEN: number;<br>差异内容：const OPTION_NO_FULLSCREEN: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const CURSOR_UP: number;<br>差异内容：const CURSOR_UP: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const CURSOR_DOWN: number;<br>差异内容：const CURSOR_DOWN: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const CURSOR_LEFT: number;<br>差异内容：const CURSOR_LEFT: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const CURSOR_RIGHT: number;<br>差异内容：const CURSOR_RIGHT: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：const WINDOW_TYPE_INPUT_METHOD_FLOAT: number;<br>差异内容：const WINDOW_TYPE_INPUT_METHOD_FLOAT: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：function getInputMethodAbility(): InputMethodAbility;<br>差异内容：function getInputMethodAbility(): InputMethodAbility;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：function getInputMethodEngine(): InputMethodEngine;<br>差异内容：function getInputMethodEngine(): InputMethodEngine;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：function getKeyboardDelegate(): KeyboardDelegate;<br>差异内容：function getKeyboardDelegate(): KeyboardDelegate;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：function createKeyboardDelegate(): KeyboardDelegate;<br>差异内容：function createKeyboardDelegate(): KeyboardDelegate;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface KeyboardController<br>差异内容：interface KeyboardController|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardController；<br>API声明：hide(callback: AsyncCallback\<void>): void;<br>差异内容：hide(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardController；<br>API声明：hide(): Promise\<void>;<br>差异内容：hide(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardController；<br>API声明：hideKeyboard(callback: AsyncCallback\<void>): void;<br>差异内容：hideKeyboard(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardController；<br>API声明：hideKeyboard(): Promise\<void>;<br>差异内容：hideKeyboard(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardController；<br>API声明：exitCurrentInputType(callback: AsyncCallback\<void>): void;<br>差异内容：exitCurrentInputType(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardController；<br>API声明：exitCurrentInputType(): Promise\<void>;<br>差异内容：exitCurrentInputType(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface InputMethodEngine<br>差异内容：interface InputMethodEngine|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodEngine；<br>API声明：on(type: 'inputStart', callback: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void;<br>差异内容：on(type: 'inputStart', callback: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodEngine；<br>API声明：off(type: 'inputStart', callback?: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void;<br>差异内容：off(type: 'inputStart', callback?: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodEngine；<br>API声明：on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;<br>差异内容：on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodEngine；<br>API声明：on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;<br>差异内容：on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodEngine；<br>API声明：off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;<br>差异内容：off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodEngine；<br>API声明：off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;<br>差异内容：off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface InputMethodAbility<br>差异内容：interface InputMethodAbility|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void;<br>差异内容：on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void;<br>差异内容：off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'inputStop', callback: () => void): void;<br>差异内容：on(type: 'inputStop', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'inputStop', callback: () => void): void;<br>差异内容：off(type: 'inputStop', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'setCallingWindow', callback: (wid: number) => void): void;<br>差异内容：on(type: 'setCallingWindow', callback: (wid: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'setCallingWindow', callback: (wid: number) => void): void;<br>差异内容：off(type: 'setCallingWindow', callback: (wid: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;<br>差异内容：on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;<br>差异内容：on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;<br>差异内容：off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;<br>差异内容：off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void;<br>差异内容：on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void;<br>差异内容：off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：on(type: 'securityModeChange', callback: Callback\<SecurityMode>): void;<br>差异内容：on(type: 'securityModeChange', callback: Callback\<SecurityMode>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：off(type: 'securityModeChange', callback?: Callback\<SecurityMode>): void;<br>差异内容：off(type: 'securityModeChange', callback?: Callback\<SecurityMode>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：getSecurityMode(): SecurityMode;<br>差异内容：getSecurityMode(): SecurityMode;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback\<Panel>): void;<br>差异内容：createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback\<Panel>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：createPanel(ctx: BaseContext, info: PanelInfo): Promise\<Panel>;<br>差异内容：createPanel(ctx: BaseContext, info: PanelInfo): Promise\<Panel>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：destroyPanel(panel: Panel, callback: AsyncCallback\<void>): void;<br>差异内容：destroyPanel(panel: Panel, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputMethodAbility；<br>API声明：destroyPanel(panel: Panel): Promise\<void>;<br>差异内容：destroyPanel(panel: Panel): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface TextInputClient<br>差异内容：interface TextInputClient|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：sendKeyFunction(action: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：sendKeyFunction(action: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：sendKeyFunction(action: number): Promise\<boolean>;<br>差异内容：sendKeyFunction(action: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：deleteForward(length: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：deleteForward(length: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：deleteForward(length: number): Promise\<boolean>;<br>差异内容：deleteForward(length: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：deleteBackward(length: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：deleteBackward(length: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：deleteBackward(length: number): Promise\<boolean>;<br>差异内容：deleteBackward(length: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：insertText(text: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：insertText(text: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：insertText(text: string): Promise\<boolean>;<br>差异内容：insertText(text: string): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：getForward(length: number, callback: AsyncCallback\<string>): void;<br>差异内容：getForward(length: number, callback: AsyncCallback\<string>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：getForward(length: number): Promise\<string>;<br>差异内容：getForward(length: number): Promise\<string>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：getBackward(length: number, callback: AsyncCallback\<string>): void;<br>差异内容：getBackward(length: number, callback: AsyncCallback\<string>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：getBackward(length: number): Promise\<string>;<br>差异内容：getBackward(length: number): Promise\<string>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：getEditorAttribute(callback: AsyncCallback\<EditorAttribute>): void;<br>差异内容：getEditorAttribute(callback: AsyncCallback\<EditorAttribute>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：TextInputClient；<br>API声明：getEditorAttribute(): Promise\<EditorAttribute>;<br>差异内容：getEditorAttribute(): Promise\<EditorAttribute>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface InputClient<br>差异内容：interface InputClient|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：sendKeyFunction(action: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：sendKeyFunction(action: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：sendKeyFunction(action: number): Promise\<boolean>;<br>差异内容：sendKeyFunction(action: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：deleteForward(length: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：deleteForward(length: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：deleteForward(length: number): Promise\<boolean>;<br>差异内容：deleteForward(length: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：deleteForwardSync(length: number): void;<br>差异内容：deleteForwardSync(length: number): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：deleteBackward(length: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：deleteBackward(length: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：deleteBackward(length: number): Promise\<boolean>;<br>差异内容：deleteBackward(length: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：deleteBackwardSync(length: number): void;<br>差异内容：deleteBackwardSync(length: number): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：insertText(text: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：insertText(text: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：insertText(text: string): Promise\<boolean>;<br>差异内容：insertText(text: string): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：insertTextSync(text: string): void;<br>差异内容：insertTextSync(text: string): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getForward(length: number, callback: AsyncCallback\<string>): void;<br>差异内容：getForward(length: number, callback: AsyncCallback\<string>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getForward(length: number): Promise\<string>;<br>差异内容：getForward(length: number): Promise\<string>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getForwardSync(length: number): string;<br>差异内容：getForwardSync(length: number): string;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getBackward(length: number, callback: AsyncCallback\<string>): void;<br>差异内容：getBackward(length: number, callback: AsyncCallback\<string>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getBackward(length: number): Promise\<string>;<br>差异内容：getBackward(length: number): Promise\<string>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getBackwardSync(length: number): string;<br>差异内容：getBackwardSync(length: number): string;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getEditorAttribute(callback: AsyncCallback\<EditorAttribute>): void;<br>差异内容：getEditorAttribute(callback: AsyncCallback\<EditorAttribute>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getEditorAttribute(): Promise\<EditorAttribute>;<br>差异内容：getEditorAttribute(): Promise\<EditorAttribute>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getEditorAttributeSync(): EditorAttribute;<br>差异内容：getEditorAttributeSync(): EditorAttribute;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：moveCursor(direction: number, callback: AsyncCallback\<void>): void;<br>差异内容：moveCursor(direction: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：moveCursor(direction: number): Promise\<void>;<br>差异内容：moveCursor(direction: number): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：moveCursorSync(direction: number): void;<br>差异内容：moveCursorSync(direction: number): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：selectByRange(range: Range, callback: AsyncCallback\<void>): void;<br>差异内容：selectByRange(range: Range, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：selectByRange(range: Range): Promise\<void>;<br>差异内容：selectByRange(range: Range): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：selectByRangeSync(range: Range): void;<br>差异内容：selectByRangeSync(range: Range): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：selectByMovement(movement: Movement, callback: AsyncCallback\<void>): void;<br>差异内容：selectByMovement(movement: Movement, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：selectByMovement(movement: Movement): Promise\<void>;<br>差异内容：selectByMovement(movement: Movement): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：selectByMovementSync(movement: Movement): void;<br>差异内容：selectByMovementSync(movement: Movement): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getTextIndexAtCursor(callback: AsyncCallback\<number>): void;<br>差异内容：getTextIndexAtCursor(callback: AsyncCallback\<number>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getTextIndexAtCursor(): Promise\<number>;<br>差异内容：getTextIndexAtCursor(): Promise\<number>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：getTextIndexAtCursorSync(): number;<br>差异内容：getTextIndexAtCursorSync(): number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：sendExtendAction(action: ExtendAction, callback: AsyncCallback\<void>): void;<br>差异内容：sendExtendAction(action: ExtendAction, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：InputClient；<br>API声明：sendExtendAction(action: ExtendAction): Promise\<void>;<br>差异内容：sendExtendAction(action: ExtendAction): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface KeyboardDelegate<br>差异内容：interface KeyboardDelegate|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：on(type: 'keyDown' \| 'keyUp', callback: (event: KeyEvent) => boolean): void;<br>差异内容：on(type: 'keyDown' \| 'keyUp', callback: (event: KeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：on(type: 'keyDown' \| 'keyUp', callback: (event: KeyEvent) => boolean): void;<br>差异内容：on(type: 'keyDown' \| 'keyUp', callback: (event: KeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：off(type: 'keyDown' \| 'keyUp', callback?: (event: KeyEvent) => boolean): void;<br>差异内容：off(type: 'keyDown' \| 'keyUp', callback?: (event: KeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：off(type: 'keyDown' \| 'keyUp', callback?: (event: KeyEvent) => boolean): void;<br>差异内容：off(type: 'keyDown' \| 'keyUp', callback?: (event: KeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：on(type: 'keyEvent', callback: (event: InputKeyEvent) => boolean): void;<br>差异内容：on(type: 'keyEvent', callback: (event: InputKeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：off(type: 'keyEvent', callback?: (event: InputKeyEvent) => boolean): void;<br>差异内容：off(type: 'keyEvent', callback?: (event: InputKeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：on(type: 'cursorContextChange', callback: (x: number, y: number, height: number) => void): void;<br>差异内容：on(type: 'cursorContextChange', callback: (x: number, y: number, height: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：off(type: 'cursorContextChange', callback?: (x: number, y: number, height: number) => void): void;<br>差异内容：off(type: 'cursorContextChange', callback?: (x: number, y: number, height: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：on(type: 'selectionChange', callback: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void;<br>差异内容：on(type: 'selectionChange', callback: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：off(type: 'selectionChange', callback?: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void;<br>差异内容：off(type: 'selectionChange', callback?: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：on(type: 'textChange', callback: (text: string) => void): void;<br>差异内容：on(type: 'textChange', callback: (text: string) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：off(type: 'textChange', callback?: (text: string) => void): void;<br>差异内容：off(type: 'textChange', callback?: (text: string) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：on(type: 'editorAttributeChanged', callback: (attr: EditorAttribute) => void): void;<br>差异内容：on(type: 'editorAttributeChanged', callback: (attr: EditorAttribute) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyboardDelegate；<br>API声明：off(type: 'editorAttributeChanged', callback?: (attr: EditorAttribute) => void): void;<br>差异内容：off(type: 'editorAttributeChanged', callback?: (attr: EditorAttribute) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface Panel<br>差异内容：interface Panel|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：setUiContent(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：setUiContent(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：setUiContent(path: string): Promise\<void>;<br>差异内容：setUiContent(path: string): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：setUiContent(path: string, storage: LocalStorage, callback: AsyncCallback\<void>): void;<br>差异内容：setUiContent(path: string, storage: LocalStorage, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：setUiContent(path: string, storage: LocalStorage): Promise\<void>;<br>差异内容：setUiContent(path: string, storage: LocalStorage): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：resize(width: number, height: number, callback: AsyncCallback\<void>): void;<br>差异内容：resize(width: number, height: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：resize(width: number, height: number): Promise\<void>;<br>差异内容：resize(width: number, height: number): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：moveTo(x: number, y: number, callback: AsyncCallback\<void>): void;<br>差异内容：moveTo(x: number, y: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：moveTo(x: number, y: number): Promise\<void>;<br>差异内容：moveTo(x: number, y: number): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：show(callback: AsyncCallback\<void>): void;<br>差异内容：show(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：show(): Promise\<void>;<br>差异内容：show(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：hide(callback: AsyncCallback\<void>): void;<br>差异内容：hide(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：hide(): Promise\<void>;<br>差异内容：hide(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：on(type: 'show', callback: () => void): void;<br>差异内容：on(type: 'show', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：off(type: 'show', callback?: () => void): void;<br>差异内容：off(type: 'show', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：on(type: 'hide', callback: () => void): void;<br>差异内容：on(type: 'hide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：off(type: 'hide', callback?: () => void): void;<br>差异内容：off(type: 'hide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：changeFlag(flag: PanelFlag): void;<br>差异内容：changeFlag(flag: PanelFlag): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Panel；<br>API声明：setPrivacyMode(isPrivacyMode: boolean): void;<br>差异内容：setPrivacyMode(isPrivacyMode: boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface EditorAttribute<br>差异内容：interface EditorAttribute|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly inputPattern: number;<br>差异内容：readonly inputPattern: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：EditorAttribute；<br>API声明：readonly enterKeyType: number;<br>差异内容：readonly enterKeyType: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：interface KeyEvent<br>差异内容：interface KeyEvent|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyEvent；<br>API声明：readonly keyCode: number;<br>差异内容：readonly keyCode: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：KeyEvent；<br>API声明：readonly keyAction: number;<br>差异内容：readonly keyAction: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export enum PanelFlag<br>差异内容：export enum PanelFlag|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：PanelFlag；<br>API声明：FLG_FIXED = 0<br>差异内容：FLG_FIXED = 0|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：PanelFlag；<br>API声明：FLG_FLOATING<br>差异内容：FLG_FLOATING|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export enum PanelType<br>差异内容：export enum PanelType|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：PanelType；<br>API声明：SOFT_KEYBOARD = 0<br>差异内容：SOFT_KEYBOARD = 0|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：PanelType；<br>API声明：STATUS_BAR<br>差异内容：STATUS_BAR|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export interface PanelInfo<br>差异内容：export interface PanelInfo|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：PanelInfo；<br>API声明：type: PanelType;<br>差异内容：type: PanelType;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：PanelInfo；<br>API声明：flag?: PanelFlag;<br>差异内容：flag?: PanelFlag;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export enum Direction<br>差异内容：export enum Direction|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Direction；<br>API声明：CURSOR_UP = 1<br>差异内容：CURSOR_UP = 1|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Direction；<br>API声明：CURSOR_DOWN<br>差异内容：CURSOR_DOWN|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Direction；<br>API声明：CURSOR_LEFT<br>差异内容：CURSOR_LEFT|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Direction；<br>API声明：CURSOR_RIGHT<br>差异内容：CURSOR_RIGHT|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export enum SecurityMode<br>差异内容：export enum SecurityMode|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：SecurityMode；<br>API声明：BASIC = 0<br>差异内容：BASIC = 0|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：SecurityMode；<br>API声明：FULL<br>差异内容：FULL|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export interface Range<br>差异内容：export interface Range|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Range；<br>API声明：start: number;<br>差异内容：start: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Range；<br>API声明：end: number;<br>差异内容：end: number;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export interface Movement<br>差异内容：export interface Movement|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：Movement；<br>API声明：direction: Direction;<br>差异内容：direction: Direction;|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：inputMethodEngine；<br>API声明：export enum ExtendAction<br>差异内容：export enum ExtendAction|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ExtendAction；<br>API声明：SELECT_ALL = 0<br>差异内容：SELECT_ALL = 0|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ExtendAction；<br>API声明：CUT = 3<br>差异内容：CUT = 3|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ExtendAction；<br>API声明：COPY = 4<br>差异内容：COPY = 4|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：ExtendAction；<br>API声明：PASTE = 5<br>差异内容：PASTE = 5|api/@ohos.inputMethodEngine.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class InputMethodExtensionAbility<br>差异内容：export default class InputMethodExtensionAbility|api/@ohos.InputMethodExtensionAbility.d.ts|
|新增API|NA|类名：InputMethodExtensionAbility；<br>API声明：context: InputMethodExtensionContext;<br>差异内容：context: InputMethodExtensionContext;|api/@ohos.InputMethodExtensionAbility.d.ts|
|新增API|NA|类名：InputMethodExtensionAbility；<br>API声明：onCreate(want: Want): void;<br>差异内容：onCreate(want: Want): void;|api/@ohos.InputMethodExtensionAbility.d.ts|
|新增API|NA|类名：InputMethodExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：onDestroy(): void;|api/@ohos.InputMethodExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class InputMethodExtensionContext<br>差异内容：export default class InputMethodExtensionContext|api/@ohos.InputMethodExtensionContext.d.ts|
|新增API|NA|类名：InputMethodExtensionContext；<br>API声明：destroy(callback: AsyncCallback\<void>): void;<br>差异内容：destroy(callback: AsyncCallback\<void>): void;|api/@ohos.InputMethodExtensionContext.d.ts|
|新增API|NA|类名：InputMethodExtensionContext；<br>API声明：destroy(): Promise\<void>;<br>差异内容：destroy(): Promise\<void>;|api/@ohos.InputMethodExtensionContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface PatternOptions<br>差异内容：export interface PatternOptions|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：PatternOptions；<br>API声明：defaultSelected?: number;<br>差异内容：defaultSelected?: number;|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：PatternOptions；<br>API声明：patterns: Array\<Pattern>;<br>差异内容：patterns: Array\<Pattern>;|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：PatternOptions；<br>API声明：action: (index: number) => void;<br>差异内容：action: (index: number) => void;|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface Pattern<br>差异内容：export interface Pattern|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：Pattern；<br>API声明：icon: Resource;<br>差异内容：icon: Resource;|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：Pattern；<br>API声明：selectedIcon: Resource;<br>差异内容：selectedIcon: Resource;|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct InputMethodListDialog<br>差异内容：export declare struct InputMethodListDialog|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：InputMethodListDialog；<br>API声明：controller: CustomDialogController;<br>差异内容：controller: CustomDialogController;|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：InputMethodListDialog；<br>API声明：patternOptions?: PatternOptions;<br>差异内容：patternOptions?: PatternOptions;|api/@ohos.inputMethodList.d.ets|
|新增API|NA|类名：global；<br>API声明：export default interface InputMethodSubtype<br>差异内容：export default interface InputMethodSubtype|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：readonly label?: string;<br>差异内容：readonly label?: string;|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：readonly labelId?: number;<br>差异内容：readonly labelId?: number;|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：readonly id: string;<br>差异内容：readonly id: string;|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：readonly mode?: 'upper' \| 'lower';<br>差异内容：readonly mode?: 'upper' \| 'lower';|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：readonly locale: string;<br>差异内容：readonly locale: string;|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：readonly language: string;<br>差异内容：readonly language: string;|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：readonly icon?: string;<br>差异内容：readonly icon?: string;|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：readonly iconId?: number;<br>差异内容：readonly iconId?: number;|api/@ohos.InputMethodSubtype.d.ts|
|新增API|NA|类名：InputMethodSubtype；<br>API声明：extra?: object;<br>差异内容：extra?: object;|api/@ohos.InputMethodSubtype.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.inputMethod.d.ts<br>差异内容：IMEKit|api/@ohos.inputMethod.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.inputMethod.Panel.d.ts<br>差异内容：IMEKit|api/@ohos.inputMethod.Panel.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.inputMethodEngine.d.ts<br>差异内容：IMEKit|api/@ohos.inputMethodEngine.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.InputMethodExtensionAbility.d.ts<br>差异内容：IMEKit|api/@ohos.InputMethodExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.InputMethodExtensionContext.d.ts<br>差异内容：IMEKit|api/@ohos.InputMethodExtensionContext.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.inputMethodList.d.ets<br>差异内容：IMEKit|api/@ohos.inputMethodList.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.InputMethodSubtype.d.ts<br>差异内容：IMEKit|api/@ohos.InputMethodSubtype.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.IMEKit.d.ts<br>差异内容：IMEKit|kits/@kit.IMEKit.d.ts|
