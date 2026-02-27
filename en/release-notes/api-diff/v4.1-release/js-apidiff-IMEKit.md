| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace inputMethod<br>Differences: declare namespace inputMethod|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: const MAX_TYPE_NUM: number;<br>Differences: const MAX_TYPE_NUM: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function getInputMethodSetting(): InputMethodSetting;<br>Differences: function getInputMethodSetting(): InputMethodSetting;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function getInputMethodController(): InputMethodController;<br>Differences: function getInputMethodController(): InputMethodController;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function getSetting(): InputMethodSetting;<br>Differences: function getSetting(): InputMethodSetting;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function getController(): InputMethodController;<br>Differences: function getController(): InputMethodController;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function getDefaultInputMethod(): InputMethodProperty;<br>Differences: function getDefaultInputMethod(): InputMethodProperty;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function getSystemInputMethodConfigAbility(): ElementName;<br>Differences: function getSystemInputMethodConfigAbility(): ElementName;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback\<boolean>): void;<br>Differences: function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function switchInputMethod(target: InputMethodProperty): Promise\<boolean>;<br>Differences: function switchInputMethod(target: InputMethodProperty): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function getCurrentInputMethod(): InputMethodProperty;<br>Differences: function getCurrentInputMethod(): InputMethodProperty;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function switchCurrentInputMethodSubtype(target: InputMethodSubtype, callback: AsyncCallback\<boolean>): void;<br>Differences: function switchCurrentInputMethodSubtype(target: InputMethodSubtype, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function switchCurrentInputMethodSubtype(target: InputMethodSubtype): Promise\<boolean>;<br>Differences: function switchCurrentInputMethodSubtype(target: InputMethodSubtype): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function getCurrentInputMethodSubtype(): InputMethodSubtype;<br>Differences: function getCurrentInputMethodSubtype(): InputMethodSubtype;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype, callback: AsyncCallback\<boolean>): void;<br>Differences: function switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: function switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype): Promise\<boolean>;<br>Differences: function switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: interface InputMethodSetting<br>Differences: interface InputMethodSetting|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: on(type: 'imeChange', callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void;<br>Differences: on(type: 'imeChange', callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: off(type: 'imeChange', callback?: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void;<br>Differences: off(type: 'imeChange', callback?: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: listInputMethodSubtype(inputMethodProperty: InputMethodProperty, callback: AsyncCallback\<Array\<InputMethodSubtype>>): void;<br>Differences: listInputMethodSubtype(inputMethodProperty: InputMethodProperty, callback: AsyncCallback\<Array\<InputMethodSubtype>>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: listInputMethodSubtype(inputMethodProperty: InputMethodProperty): Promise\<Array\<InputMethodSubtype>>;<br>Differences: listInputMethodSubtype(inputMethodProperty: InputMethodProperty): Promise\<Array\<InputMethodSubtype>>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: listCurrentInputMethodSubtype(callback: AsyncCallback\<Array\<InputMethodSubtype>>): void;<br>Differences: listCurrentInputMethodSubtype(callback: AsyncCallback\<Array\<InputMethodSubtype>>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: listCurrentInputMethodSubtype(): Promise\<Array\<InputMethodSubtype>>;<br>Differences: listCurrentInputMethodSubtype(): Promise\<Array\<InputMethodSubtype>>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: getInputMethods(enable: boolean, callback: AsyncCallback\<Array\<InputMethodProperty>>): void;<br>Differences: getInputMethods(enable: boolean, callback: AsyncCallback\<Array\<InputMethodProperty>>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: getInputMethods(enable: boolean): Promise\<Array\<InputMethodProperty>>;<br>Differences: getInputMethods(enable: boolean): Promise\<Array\<InputMethodProperty>>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: getInputMethodsSync(enable: boolean): Array\<InputMethodProperty>;<br>Differences: getInputMethodsSync(enable: boolean): Array\<InputMethodProperty>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: getAllInputMethods(callback: AsyncCallback\<Array\<InputMethodProperty>>): void;<br>Differences: getAllInputMethods(callback: AsyncCallback\<Array\<InputMethodProperty>>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: getAllInputMethods(): Promise\<Array\<InputMethodProperty>>;<br>Differences: getAllInputMethods(): Promise\<Array\<InputMethodProperty>>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: getAllInputMethodsSync(): Array\<InputMethodProperty>;<br>Differences: getAllInputMethodsSync(): Array\<InputMethodProperty>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: listInputMethod(callback: AsyncCallback\<Array\<InputMethodProperty>>): void;<br>Differences: listInputMethod(callback: AsyncCallback\<Array\<InputMethodProperty>>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: listInputMethod(): Promise\<Array\<InputMethodProperty>>;<br>Differences: listInputMethod(): Promise\<Array\<InputMethodProperty>>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;<br>Differences: showOptionalInputMethods(callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: showOptionalInputMethods(): Promise\<boolean>;<br>Differences: showOptionalInputMethods(): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: displayOptionalInputMethod(callback: AsyncCallback\<void>): void;<br>Differences: displayOptionalInputMethod(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodSetting;<br>API declaration: displayOptionalInputMethod(): Promise\<void>;<br>Differences: displayOptionalInputMethod(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: interface InputMethodController<br>Differences: interface InputMethodController|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: attach(showKeyboard: boolean, textConfig: TextConfig, callback: AsyncCallback\<void>): void;<br>Differences: attach(showKeyboard: boolean, textConfig: TextConfig, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: attach(showKeyboard: boolean, textConfig: TextConfig): Promise\<void>;<br>Differences: attach(showKeyboard: boolean, textConfig: TextConfig): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: showTextInput(callback: AsyncCallback\<void>): void;<br>Differences: showTextInput(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: showTextInput(): Promise\<void>;<br>Differences: showTextInput(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: hideTextInput(callback: AsyncCallback\<void>): void;<br>Differences: hideTextInput(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: hideTextInput(): Promise\<void>;<br>Differences: hideTextInput(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: detach(callback: AsyncCallback\<void>): void;<br>Differences: detach(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: detach(): Promise\<void>;<br>Differences: detach(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: setCallingWindow(windowId: number, callback: AsyncCallback\<void>): void;<br>Differences: setCallingWindow(windowId: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: setCallingWindow(windowId: number): Promise\<void>;<br>Differences: setCallingWindow(windowId: number): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: updateCursor(cursorInfo: CursorInfo, callback: AsyncCallback\<void>): void;<br>Differences: updateCursor(cursorInfo: CursorInfo, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: updateCursor(cursorInfo: CursorInfo): Promise\<void>;<br>Differences: updateCursor(cursorInfo: CursorInfo): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: changeSelection(text: string, start: number, end: number, callback: AsyncCallback\<void>): void;<br>Differences: changeSelection(text: string, start: number, end: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: changeSelection(text: string, start: number, end: number): Promise\<void>;<br>Differences: changeSelection(text: string, start: number, end: number): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: updateAttribute(attribute: InputAttribute, callback: AsyncCallback\<void>): void;<br>Differences: updateAttribute(attribute: InputAttribute, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: updateAttribute(attribute: InputAttribute): Promise\<void>;<br>Differences: updateAttribute(attribute: InputAttribute): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: stopInputSession(callback: AsyncCallback\<boolean>): void;<br>Differences: stopInputSession(callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: stopInputSession(): Promise\<boolean>;<br>Differences: stopInputSession(): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: stopInput(callback: AsyncCallback\<boolean>): void;<br>Differences: stopInput(callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: stopInput(): Promise\<boolean>;<br>Differences: stopInput(): Promise\<boolean>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: showSoftKeyboard(callback: AsyncCallback\<void>): void;<br>Differences: showSoftKeyboard(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: showSoftKeyboard(): Promise\<void>;<br>Differences: showSoftKeyboard(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: hideSoftKeyboard(callback: AsyncCallback\<void>): void;<br>Differences: hideSoftKeyboard(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: hideSoftKeyboard(): Promise\<void>;<br>Differences: hideSoftKeyboard(): Promise\<void>;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'selectByRange', callback: Callback\<Range>): void;<br>Differences: on(type: 'selectByRange', callback: Callback\<Range>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'selectByRange', callback?: Callback\<Range>): void;<br>Differences: off(type: 'selectByRange', callback?: Callback\<Range>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'selectByMovement', callback: Callback\<Movement>): void;<br>Differences: on(type: 'selectByMovement', callback: Callback\<Movement>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'selectByMovement', callback?: Callback\<Movement>): void;<br>Differences: off(type: 'selectByMovement', callback?: Callback\<Movement>): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'insertText', callback: (text: string) => void): void;<br>Differences: on(type: 'insertText', callback: (text: string) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'insertText', callback?: (text: string) => void): void;<br>Differences: off(type: 'insertText', callback?: (text: string) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'deleteLeft', callback: (length: number) => void): void;<br>Differences: on(type: 'deleteLeft', callback: (length: number) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'deleteLeft', callback?: (length: number) => void): void;<br>Differences: off(type: 'deleteLeft', callback?: (length: number) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'deleteRight', callback: (length: number) => void): void;<br>Differences: on(type: 'deleteRight', callback: (length: number) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'deleteRight', callback?: (length: number) => void): void;<br>Differences: off(type: 'deleteRight', callback?: (length: number) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'sendKeyboardStatus', callback: (keyboardStatus: KeyboardStatus) => void): void;<br>Differences: on(type: 'sendKeyboardStatus', callback: (keyboardStatus: KeyboardStatus) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'sendKeyboardStatus', callback?: (keyboardStatus: KeyboardStatus) => void): void;<br>Differences: off(type: 'sendKeyboardStatus', callback?: (keyboardStatus: KeyboardStatus) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'sendFunctionKey', callback: (functionKey: FunctionKey) => void): void;<br>Differences: on(type: 'sendFunctionKey', callback: (functionKey: FunctionKey) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'sendFunctionKey', callback?: (functionKey: FunctionKey) => void): void;<br>Differences: off(type: 'sendFunctionKey', callback?: (functionKey: FunctionKey) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'moveCursor', callback: (direction: Direction) => void): void;<br>Differences: on(type: 'moveCursor', callback: (direction: Direction) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'moveCursor', callback?: (direction: Direction) => void): void;<br>Differences: off(type: 'moveCursor', callback?: (direction: Direction) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'handleExtendAction', callback: (action: ExtendAction) => void): void;<br>Differences: on(type: 'handleExtendAction', callback: (action: ExtendAction) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'handleExtendAction', callback?: (action: ExtendAction) => void): void;<br>Differences: off(type: 'handleExtendAction', callback?: (action: ExtendAction) => void): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'getLeftTextOfCursor', callback: (length: number) => string): void;<br>Differences: on(type: 'getLeftTextOfCursor', callback: (length: number) => string): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'getLeftTextOfCursor', callback?: (length: number) => string): void;<br>Differences: off(type: 'getLeftTextOfCursor', callback?: (length: number) => string): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'getRightTextOfCursor', callback: (length: number) => string): void;<br>Differences: on(type: 'getRightTextOfCursor', callback: (length: number) => string): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'getRightTextOfCursor', callback?: (length: number) => string): void;<br>Differences: off(type: 'getRightTextOfCursor', callback?: (length: number) => string): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: on(type: 'getTextIndexAtCursor', callback: () => number): void;<br>Differences: on(type: 'getTextIndexAtCursor', callback: () => number): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodController;<br>API declaration: off(type: 'getTextIndexAtCursor', callback?: () => number): void;<br>Differences: off(type: 'getTextIndexAtCursor', callback?: () => number): void;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: interface InputMethodProperty<br>Differences: interface InputMethodProperty|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodProperty;<br>API declaration: readonly packageName: string;<br>Differences: readonly packageName: string;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodProperty;<br>API declaration: readonly methodId: string;<br>Differences: readonly methodId: string;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodProperty;<br>API declaration: readonly name: string;<br>Differences: readonly name: string;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodProperty;<br>API declaration: readonly id: string;<br>Differences: readonly id: string;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodProperty;<br>API declaration: readonly label?: string;<br>Differences: readonly label?: string;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodProperty;<br>API declaration: readonly labelId?: number;<br>Differences: readonly labelId?: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodProperty;<br>API declaration: readonly icon?: string;<br>Differences: readonly icon?: string;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodProperty;<br>API declaration: readonly iconId?: number;<br>Differences: readonly iconId?: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputMethodProperty;<br>API declaration: extra?: object;<br>Differences: extra?: object;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export enum Direction<br>Differences: export enum Direction|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: CURSOR_UP = 1<br>Differences: CURSOR_UP = 1|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: CURSOR_DOWN<br>Differences: CURSOR_DOWN|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: CURSOR_LEFT<br>Differences: CURSOR_LEFT|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: CURSOR_RIGHT<br>Differences: CURSOR_RIGHT|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export interface Range<br>Differences: export interface Range|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: Range;<br>API declaration: start: number;<br>Differences: start: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: Range;<br>API declaration: end: number;<br>Differences: end: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export interface Movement<br>Differences: export interface Movement|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: Movement;<br>API declaration: direction: Direction;<br>Differences: direction: Direction;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export enum TextInputType<br>Differences: export enum TextInputType|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: NONE = -1<br>Differences: NONE = -1|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: TEXT = 0<br>Differences: TEXT = 0|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: MULTILINE<br>Differences: MULTILINE|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: NUMBER<br>Differences: NUMBER|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: PHONE<br>Differences: PHONE|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: DATETIME<br>Differences: DATETIME|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: EMAIL_ADDRESS<br>Differences: EMAIL_ADDRESS|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: URL<br>Differences: URL|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: VISIBLE_PASSWORD<br>Differences: VISIBLE_PASSWORD|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextInputType;<br>API declaration: NUMBER_PASSWORD<br>Differences: NUMBER_PASSWORD|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export enum EnterKeyType<br>Differences: export enum EnterKeyType|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: EnterKeyType;<br>API declaration: UNSPECIFIED = 0<br>Differences: UNSPECIFIED = 0|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: EnterKeyType;<br>API declaration: NONE<br>Differences: NONE|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: EnterKeyType;<br>API declaration: GO<br>Differences: GO|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: EnterKeyType;<br>API declaration: SEARCH<br>Differences: SEARCH|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: EnterKeyType;<br>API declaration: SEND<br>Differences: SEND|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: EnterKeyType;<br>API declaration: NEXT<br>Differences: NEXT|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: EnterKeyType;<br>API declaration: DONE<br>Differences: DONE|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: EnterKeyType;<br>API declaration: PREVIOUS<br>Differences: PREVIOUS|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export enum KeyboardStatus<br>Differences: export enum KeyboardStatus|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: KeyboardStatus;<br>API declaration: NONE = 0<br>Differences: NONE = 0|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: KeyboardStatus;<br>API declaration: HIDE = 1<br>Differences: HIDE = 1|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: KeyboardStatus;<br>API declaration: SHOW = 2<br>Differences: SHOW = 2|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export interface InputAttribute<br>Differences: export interface InputAttribute|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputAttribute;<br>API declaration: textInputType: TextInputType;<br>Differences: textInputType: TextInputType;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputAttribute;<br>API declaration: enterKeyType: EnterKeyType;<br>Differences: enterKeyType: EnterKeyType;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export interface FunctionKey<br>Differences: export interface FunctionKey|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: FunctionKey;<br>API declaration: enterKeyType: EnterKeyType;<br>Differences: enterKeyType: EnterKeyType;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export interface CursorInfo<br>Differences: export interface CursorInfo|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: CursorInfo;<br>API declaration: left: number;<br>Differences: left: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: CursorInfo;<br>API declaration: top: number;<br>Differences: top: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: CursorInfo;<br>API declaration: width: number;<br>Differences: width: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: CursorInfo;<br>API declaration: height: number;<br>Differences: height: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export interface TextConfig<br>Differences: export interface TextConfig|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextConfig;<br>API declaration: inputAttribute: InputAttribute;<br>Differences: inputAttribute: InputAttribute;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextConfig;<br>API declaration: cursorInfo?: CursorInfo;<br>Differences: cursorInfo?: CursorInfo;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextConfig;<br>API declaration: selection?: Range;<br>Differences: selection?: Range;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: TextConfig;<br>API declaration: windowId?: number;<br>Differences: windowId?: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export enum ExtendAction<br>Differences: export enum ExtendAction|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: ExtendAction;<br>API declaration: SELECT_ALL = 0<br>Differences: SELECT_ALL = 0|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: ExtendAction;<br>API declaration: CUT = 3<br>Differences: CUT = 3|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: ExtendAction;<br>API declaration: COPY = 4<br>Differences: COPY = 4|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: ExtendAction;<br>API declaration: PASTE = 5<br>Differences: PASTE = 5|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: inputMethod;<br>API declaration: export interface InputWindowInfo<br>Differences: export interface InputWindowInfo|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputWindowInfo;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputWindowInfo;<br>API declaration: left: number;<br>Differences: left: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputWindowInfo;<br>API declaration: top: number;<br>Differences: top: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputWindowInfo;<br>API declaration: width: number;<br>Differences: width: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: InputWindowInfo;<br>API declaration: height: number;<br>Differences: height: number;|api/@ohos.inputMethod.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface PanelInfo<br>Differences: export interface PanelInfo|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: PanelInfo;<br>API declaration: type: PanelType;<br>Differences: type: PanelType;|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: PanelInfo;<br>API declaration: flag?: PanelFlag;<br>Differences: flag?: PanelFlag;|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: global;<br>API declaration: export enum PanelFlag<br>Differences: export enum PanelFlag|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: PanelFlag;<br>API declaration: FLAG_FIXED = 0<br>Differences: FLAG_FIXED = 0|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: PanelFlag;<br>API declaration: FLAG_FLOATING<br>Differences: FLAG_FLOATING|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: PanelFlag;<br>API declaration: FLAG_CANDIDATE<br>Differences: FLAG_CANDIDATE|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: global;<br>API declaration: export enum PanelType<br>Differences: export enum PanelType|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: PanelType;<br>API declaration: SOFT_KEYBOARD = 0<br>Differences: SOFT_KEYBOARD = 0|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: PanelType;<br>API declaration: STATUS_BAR<br>Differences: STATUS_BAR|api/@ohos.inputMethod.Panel.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace inputMethodEngine<br>Differences: declare namespace inputMethodEngine|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const ENTER_KEY_TYPE_UNSPECIFIED: number;<br>Differences: const ENTER_KEY_TYPE_UNSPECIFIED: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const ENTER_KEY_TYPE_GO: number;<br>Differences: const ENTER_KEY_TYPE_GO: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const ENTER_KEY_TYPE_SEARCH: number;<br>Differences: const ENTER_KEY_TYPE_SEARCH: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const ENTER_KEY_TYPE_SEND: number;<br>Differences: const ENTER_KEY_TYPE_SEND: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const ENTER_KEY_TYPE_NEXT: number;<br>Differences: const ENTER_KEY_TYPE_NEXT: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const ENTER_KEY_TYPE_DONE: number;<br>Differences: const ENTER_KEY_TYPE_DONE: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const ENTER_KEY_TYPE_PREVIOUS: number;<br>Differences: const ENTER_KEY_TYPE_PREVIOUS: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_NULL: number;<br>Differences: const PATTERN_NULL: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_TEXT: number;<br>Differences: const PATTERN_TEXT: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_NUMBER: number;<br>Differences: const PATTERN_NUMBER: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_PHONE: number;<br>Differences: const PATTERN_PHONE: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_DATETIME: number;<br>Differences: const PATTERN_DATETIME: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_EMAIL: number;<br>Differences: const PATTERN_EMAIL: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_URI: number;<br>Differences: const PATTERN_URI: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_PASSWORD: number;<br>Differences: const PATTERN_PASSWORD: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_PASSWORD_SCREEN_LOCK: number;<br>Differences: const PATTERN_PASSWORD_SCREEN_LOCK: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const PATTERN_PASSWORD_NUMBER: number;<br>Differences: const PATTERN_PASSWORD_NUMBER: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const FLAG_SELECTING: number;<br>Differences: const FLAG_SELECTING: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const FLAG_SINGLE_LINE: number;<br>Differences: const FLAG_SINGLE_LINE: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const DISPLAY_MODE_PART: number;<br>Differences: const DISPLAY_MODE_PART: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const DISPLAY_MODE_FULL: number;<br>Differences: const DISPLAY_MODE_FULL: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const OPTION_ASCII: number;<br>Differences: const OPTION_ASCII: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const OPTION_NONE: number;<br>Differences: const OPTION_NONE: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const OPTION_AUTO_CAP_CHARACTERS: number;<br>Differences: const OPTION_AUTO_CAP_CHARACTERS: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const OPTION_AUTO_CAP_SENTENCES: number;<br>Differences: const OPTION_AUTO_CAP_SENTENCES: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const OPTION_AUTO_WORDS: number;<br>Differences: const OPTION_AUTO_WORDS: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const OPTION_MULTI_LINE: number;<br>Differences: const OPTION_MULTI_LINE: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const OPTION_NO_FULLSCREEN: number;<br>Differences: const OPTION_NO_FULLSCREEN: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const CURSOR_UP: number;<br>Differences: const CURSOR_UP: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const CURSOR_DOWN: number;<br>Differences: const CURSOR_DOWN: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const CURSOR_LEFT: number;<br>Differences: const CURSOR_LEFT: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const CURSOR_RIGHT: number;<br>Differences: const CURSOR_RIGHT: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: const WINDOW_TYPE_INPUT_METHOD_FLOAT: number;<br>Differences: const WINDOW_TYPE_INPUT_METHOD_FLOAT: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: function getInputMethodAbility(): InputMethodAbility;<br>Differences: function getInputMethodAbility(): InputMethodAbility;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: function getInputMethodEngine(): InputMethodEngine;<br>Differences: function getInputMethodEngine(): InputMethodEngine;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: function getKeyboardDelegate(): KeyboardDelegate;<br>Differences: function getKeyboardDelegate(): KeyboardDelegate;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: function createKeyboardDelegate(): KeyboardDelegate;<br>Differences: function createKeyboardDelegate(): KeyboardDelegate;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: interface KeyboardController<br>Differences: interface KeyboardController|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardController;<br>API declaration: hide(callback: AsyncCallback\<void>): void;<br>Differences: hide(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardController;<br>API declaration: hide(): Promise\<void>;<br>Differences: hide(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardController;<br>API declaration: hideKeyboard(callback: AsyncCallback\<void>): void;<br>Differences: hideKeyboard(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardController;<br>API declaration: hideKeyboard(): Promise\<void>;<br>Differences: hideKeyboard(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardController;<br>API declaration: exitCurrentInputType(callback: AsyncCallback\<void>): void;<br>Differences: exitCurrentInputType(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardController;<br>API declaration: exitCurrentInputType(): Promise\<void>;<br>Differences: exitCurrentInputType(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: interface InputMethodEngine<br>Differences: interface InputMethodEngine|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodEngine;<br>API declaration: on(type: 'inputStart', callback: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void;<br>Differences: on(type: 'inputStart', callback: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodEngine;<br>API declaration: off(type: 'inputStart', callback?: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void;<br>Differences: off(type: 'inputStart', callback?: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodEngine;<br>API declaration: on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;<br>Differences: on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodEngine;<br>API declaration: on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;<br>Differences: on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodEngine;<br>API declaration: off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;<br>Differences: off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodEngine;<br>API declaration: off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;<br>Differences: off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: interface InputMethodAbility<br>Differences: interface InputMethodAbility|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void;<br>Differences: on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void;<br>Differences: off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'inputStop', callback: () => void): void;<br>Differences: on(type: 'inputStop', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'inputStop', callback: () => void): void;<br>Differences: off(type: 'inputStop', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'setCallingWindow', callback: (wid: number) => void): void;<br>Differences: on(type: 'setCallingWindow', callback: (wid: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'setCallingWindow', callback: (wid: number) => void): void;<br>Differences: off(type: 'setCallingWindow', callback: (wid: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;<br>Differences: on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;<br>Differences: on(type: 'keyboardShow' \| 'keyboardHide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;<br>Differences: off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;<br>Differences: off(type: 'keyboardShow' \| 'keyboardHide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void;<br>Differences: on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void;<br>Differences: off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: on(type: 'securityModeChange', callback: Callback\<SecurityMode>): void;<br>Differences: on(type: 'securityModeChange', callback: Callback\<SecurityMode>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: off(type: 'securityModeChange', callback?: Callback\<SecurityMode>): void;<br>Differences: off(type: 'securityModeChange', callback?: Callback\<SecurityMode>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: getSecurityMode(): SecurityMode;<br>Differences: getSecurityMode(): SecurityMode;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback\<Panel>): void;<br>Differences: createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback\<Panel>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: createPanel(ctx: BaseContext, info: PanelInfo): Promise\<Panel>;<br>Differences: createPanel(ctx: BaseContext, info: PanelInfo): Promise\<Panel>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: destroyPanel(panel: Panel, callback: AsyncCallback\<void>): void;<br>Differences: destroyPanel(panel: Panel, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputMethodAbility;<br>API declaration: destroyPanel(panel: Panel): Promise\<void>;<br>Differences: destroyPanel(panel: Panel): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: interface TextInputClient<br>Differences: interface TextInputClient|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: sendKeyFunction(action: number, callback: AsyncCallback\<boolean>): void;<br>Differences: sendKeyFunction(action: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: sendKeyFunction(action: number): Promise\<boolean>;<br>Differences: sendKeyFunction(action: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: deleteForward(length: number, callback: AsyncCallback\<boolean>): void;<br>Differences: deleteForward(length: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: deleteForward(length: number): Promise\<boolean>;<br>Differences: deleteForward(length: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: deleteBackward(length: number, callback: AsyncCallback\<boolean>): void;<br>Differences: deleteBackward(length: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: deleteBackward(length: number): Promise\<boolean>;<br>Differences: deleteBackward(length: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: insertText(text: string, callback: AsyncCallback\<boolean>): void;<br>Differences: insertText(text: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: insertText(text: string): Promise\<boolean>;<br>Differences: insertText(text: string): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: getForward(length: number, callback: AsyncCallback\<string>): void;<br>Differences: getForward(length: number, callback: AsyncCallback\<string>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: getForward(length: number): Promise\<string>;<br>Differences: getForward(length: number): Promise\<string>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: getBackward(length: number, callback: AsyncCallback\<string>): void;<br>Differences: getBackward(length: number, callback: AsyncCallback\<string>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: getBackward(length: number): Promise\<string>;<br>Differences: getBackward(length: number): Promise\<string>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: getEditorAttribute(callback: AsyncCallback\<EditorAttribute>): void;<br>Differences: getEditorAttribute(callback: AsyncCallback\<EditorAttribute>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: TextInputClient;<br>API declaration: getEditorAttribute(): Promise\<EditorAttribute>;<br>Differences: getEditorAttribute(): Promise\<EditorAttribute>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: interface InputClient<br>Differences: interface InputClient|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: sendKeyFunction(action: number, callback: AsyncCallback\<boolean>): void;<br>Differences: sendKeyFunction(action: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: sendKeyFunction(action: number): Promise\<boolean>;<br>Differences: sendKeyFunction(action: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: deleteForward(length: number, callback: AsyncCallback\<boolean>): void;<br>Differences: deleteForward(length: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: deleteForward(length: number): Promise\<boolean>;<br>Differences: deleteForward(length: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: deleteForwardSync(length: number): void;<br>Differences: deleteForwardSync(length: number): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: deleteBackward(length: number, callback: AsyncCallback\<boolean>): void;<br>Differences: deleteBackward(length: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: deleteBackward(length: number): Promise\<boolean>;<br>Differences: deleteBackward(length: number): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: deleteBackwardSync(length: number): void;<br>Differences: deleteBackwardSync(length: number): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: insertText(text: string, callback: AsyncCallback\<boolean>): void;<br>Differences: insertText(text: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: insertText(text: string): Promise\<boolean>;<br>Differences: insertText(text: string): Promise\<boolean>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: insertTextSync(text: string): void;<br>Differences: insertTextSync(text: string): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getForward(length: number, callback: AsyncCallback\<string>): void;<br>Differences: getForward(length: number, callback: AsyncCallback\<string>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getForward(length: number): Promise\<string>;<br>Differences: getForward(length: number): Promise\<string>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getForwardSync(length: number): string;<br>Differences: getForwardSync(length: number): string;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getBackward(length: number, callback: AsyncCallback\<string>): void;<br>Differences: getBackward(length: number, callback: AsyncCallback\<string>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getBackward(length: number): Promise\<string>;<br>Differences: getBackward(length: number): Promise\<string>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getBackwardSync(length: number): string;<br>Differences: getBackwardSync(length: number): string;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getEditorAttribute(callback: AsyncCallback\<EditorAttribute>): void;<br>Differences: getEditorAttribute(callback: AsyncCallback\<EditorAttribute>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getEditorAttribute(): Promise\<EditorAttribute>;<br>Differences: getEditorAttribute(): Promise\<EditorAttribute>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getEditorAttributeSync(): EditorAttribute;<br>Differences: getEditorAttributeSync(): EditorAttribute;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: moveCursor(direction: number, callback: AsyncCallback\<void>): void;<br>Differences: moveCursor(direction: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: moveCursor(direction: number): Promise\<void>;<br>Differences: moveCursor(direction: number): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: moveCursorSync(direction: number): void;<br>Differences: moveCursorSync(direction: number): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: selectByRange(range: Range, callback: AsyncCallback\<void>): void;<br>Differences: selectByRange(range: Range, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: selectByRange(range: Range): Promise\<void>;<br>Differences: selectByRange(range: Range): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: selectByRangeSync(range: Range): void;<br>Differences: selectByRangeSync(range: Range): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: selectByMovement(movement: Movement, callback: AsyncCallback\<void>): void;<br>Differences: selectByMovement(movement: Movement, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: selectByMovement(movement: Movement): Promise\<void>;<br>Differences: selectByMovement(movement: Movement): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: selectByMovementSync(movement: Movement): void;<br>Differences: selectByMovementSync(movement: Movement): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getTextIndexAtCursor(callback: AsyncCallback\<number>): void;<br>Differences: getTextIndexAtCursor(callback: AsyncCallback\<number>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getTextIndexAtCursor(): Promise\<number>;<br>Differences: getTextIndexAtCursor(): Promise\<number>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: getTextIndexAtCursorSync(): number;<br>Differences: getTextIndexAtCursorSync(): number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: sendExtendAction(action: ExtendAction, callback: AsyncCallback\<void>): void;<br>Differences: sendExtendAction(action: ExtendAction, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: InputClient;<br>API declaration: sendExtendAction(action: ExtendAction): Promise\<void>;<br>Differences: sendExtendAction(action: ExtendAction): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: interface KeyboardDelegate<br>Differences: interface KeyboardDelegate|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: on(type: 'keyDown' \| 'keyUp', callback: (event: KeyEvent) => boolean): void;<br>Differences: on(type: 'keyDown' \| 'keyUp', callback: (event: KeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: on(type: 'keyDown' \| 'keyUp', callback: (event: KeyEvent) => boolean): void;<br>Differences: on(type: 'keyDown' \| 'keyUp', callback: (event: KeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: off(type: 'keyDown' \| 'keyUp', callback?: (event: KeyEvent) => boolean): void;<br>Differences: off(type: 'keyDown' \| 'keyUp', callback?: (event: KeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: off(type: 'keyDown' \| 'keyUp', callback?: (event: KeyEvent) => boolean): void;<br>Differences: off(type: 'keyDown' \| 'keyUp', callback?: (event: KeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: on(type: 'keyEvent', callback: (event: InputKeyEvent) => boolean): void;<br>Differences: on(type: 'keyEvent', callback: (event: InputKeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: off(type: 'keyEvent', callback?: (event: InputKeyEvent) => boolean): void;<br>Differences: off(type: 'keyEvent', callback?: (event: InputKeyEvent) => boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: on(type: 'cursorContextChange', callback: (x: number, y: number, height: number) => void): void;<br>Differences: on(type: 'cursorContextChange', callback: (x: number, y: number, height: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: off(type: 'cursorContextChange', callback?: (x: number, y: number, height: number) => void): void;<br>Differences: off(type: 'cursorContextChange', callback?: (x: number, y: number, height: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: on(type: 'selectionChange', callback: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void;<br>Differences: on(type: 'selectionChange', callback: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: off(type: 'selectionChange', callback?: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void;<br>Differences: off(type: 'selectionChange', callback?: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: on(type: 'textChange', callback: (text: string) => void): void;<br>Differences: on(type: 'textChange', callback: (text: string) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: off(type: 'textChange', callback?: (text: string) => void): void;<br>Differences: off(type: 'textChange', callback?: (text: string) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: on(type: 'editorAttributeChanged', callback: (attr: EditorAttribute) => void): void;<br>Differences: on(type: 'editorAttributeChanged', callback: (attr: EditorAttribute) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyboardDelegate;<br>API declaration: off(type: 'editorAttributeChanged', callback?: (attr: EditorAttribute) => void): void;<br>Differences: off(type: 'editorAttributeChanged', callback?: (attr: EditorAttribute) => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: interface Panel<br>Differences: interface Panel|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: setUiContent(path: string, callback: AsyncCallback\<void>): void;<br>Differences: setUiContent(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: setUiContent(path: string): Promise\<void>;<br>Differences: setUiContent(path: string): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: setUiContent(path: string, storage: LocalStorage, callback: AsyncCallback\<void>): void;<br>Differences: setUiContent(path: string, storage: LocalStorage, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: setUiContent(path: string, storage: LocalStorage): Promise\<void>;<br>Differences: setUiContent(path: string, storage: LocalStorage): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: resize(width: number, height: number, callback: AsyncCallback\<void>): void;<br>Differences: resize(width: number, height: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: resize(width: number, height: number): Promise\<void>;<br>Differences: resize(width: number, height: number): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: moveTo(x: number, y: number, callback: AsyncCallback\<void>): void;<br>Differences: moveTo(x: number, y: number, callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: moveTo(x: number, y: number): Promise\<void>;<br>Differences: moveTo(x: number, y: number): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: show(callback: AsyncCallback\<void>): void;<br>Differences: show(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: show(): Promise\<void>;<br>Differences: show(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: hide(callback: AsyncCallback\<void>): void;<br>Differences: hide(callback: AsyncCallback\<void>): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: hide(): Promise\<void>;<br>Differences: hide(): Promise\<void>;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: on(type: 'show', callback: () => void): void;<br>Differences: on(type: 'show', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: off(type: 'show', callback?: () => void): void;<br>Differences: off(type: 'show', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: on(type: 'hide', callback: () => void): void;<br>Differences: on(type: 'hide', callback: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: off(type: 'hide', callback?: () => void): void;<br>Differences: off(type: 'hide', callback?: () => void): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: changeFlag(flag: PanelFlag): void;<br>Differences: changeFlag(flag: PanelFlag): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Panel;<br>API declaration: setPrivacyMode(isPrivacyMode: boolean): void;<br>Differences: setPrivacyMode(isPrivacyMode: boolean): void;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: interface EditorAttribute<br>Differences: interface EditorAttribute|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: EditorAttribute;<br>API declaration: readonly inputPattern: number;<br>Differences: readonly inputPattern: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: EditorAttribute;<br>API declaration: readonly enterKeyType: number;<br>Differences: readonly enterKeyType: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: interface KeyEvent<br>Differences: interface KeyEvent|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyEvent;<br>API declaration: readonly keyCode: number;<br>Differences: readonly keyCode: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: KeyEvent;<br>API declaration: readonly keyAction: number;<br>Differences: readonly keyAction: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export enum PanelFlag<br>Differences: export enum PanelFlag|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: PanelFlag;<br>API declaration: FLG_FIXED = 0<br>Differences: FLG_FIXED = 0|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: PanelFlag;<br>API declaration: FLG_FLOATING<br>Differences: FLG_FLOATING|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export enum PanelType<br>Differences: export enum PanelType|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: PanelType;<br>API declaration: SOFT_KEYBOARD = 0<br>Differences: SOFT_KEYBOARD = 0|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: PanelType;<br>API declaration: STATUS_BAR<br>Differences: STATUS_BAR|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export interface PanelInfo<br>Differences: export interface PanelInfo|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: PanelInfo;<br>API declaration: type: PanelType;<br>Differences: type: PanelType;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: PanelInfo;<br>API declaration: flag?: PanelFlag;<br>Differences: flag?: PanelFlag;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export enum Direction<br>Differences: export enum Direction|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: CURSOR_UP = 1<br>Differences: CURSOR_UP = 1|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: CURSOR_DOWN<br>Differences: CURSOR_DOWN|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: CURSOR_LEFT<br>Differences: CURSOR_LEFT|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: CURSOR_RIGHT<br>Differences: CURSOR_RIGHT|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export enum SecurityMode<br>Differences: export enum SecurityMode|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: SecurityMode;<br>API declaration: BASIC = 0<br>Differences: BASIC = 0|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: SecurityMode;<br>API declaration: FULL<br>Differences: FULL|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export interface Range<br>Differences: export interface Range|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Range;<br>API declaration: start: number;<br>Differences: start: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Range;<br>API declaration: end: number;<br>Differences: end: number;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export interface Movement<br>Differences: export interface Movement|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: Movement;<br>API declaration: direction: Direction;<br>Differences: direction: Direction;|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: inputMethodEngine;<br>API declaration: export enum ExtendAction<br>Differences: export enum ExtendAction|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: ExtendAction;<br>API declaration: SELECT_ALL = 0<br>Differences: SELECT_ALL = 0|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: ExtendAction;<br>API declaration: CUT = 3<br>Differences: CUT = 3|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: ExtendAction;<br>API declaration: COPY = 4<br>Differences: COPY = 4|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: ExtendAction;<br>API declaration: PASTE = 5<br>Differences: PASTE = 5|api/@ohos.inputMethodEngine.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class InputMethodExtensionAbility<br>Differences: export default class InputMethodExtensionAbility|api/@ohos.InputMethodExtensionAbility.d.ts|
|New API|NA|Class name: InputMethodExtensionAbility;<br>API declaration: context: InputMethodExtensionContext;<br>Differences: context: InputMethodExtensionContext;|api/@ohos.InputMethodExtensionAbility.d.ts|
|New API|NA|Class name: InputMethodExtensionAbility;<br>API declaration: onCreate(want: Want): void;<br>Differences: onCreate(want: Want): void;|api/@ohos.InputMethodExtensionAbility.d.ts|
|New API|NA|Class name: InputMethodExtensionAbility;<br>API declaration: onDestroy(): void;<br>Differences: onDestroy(): void;|api/@ohos.InputMethodExtensionAbility.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class InputMethodExtensionContext<br>Differences: export default class InputMethodExtensionContext|api/@ohos.InputMethodExtensionContext.d.ts|
|New API|NA|Class name: InputMethodExtensionContext;<br>API declaration: destroy(callback: AsyncCallback\<void>): void;<br>Differences: destroy(callback: AsyncCallback\<void>): void;|api/@ohos.InputMethodExtensionContext.d.ts|
|New API|NA|Class name: InputMethodExtensionContext;<br>API declaration: destroy(): Promise\<void>;<br>Differences: destroy(): Promise\<void>;|api/@ohos.InputMethodExtensionContext.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface PatternOptions<br>Differences: export interface PatternOptions|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: PatternOptions;<br>API declaration: defaultSelected?: number;<br>Differences: defaultSelected?: number;|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: PatternOptions;<br>API declaration: patterns: Array\<Pattern>;<br>Differences: patterns: Array\<Pattern>;|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: PatternOptions;<br>API declaration: action: (index: number) => void;<br>Differences: action: (index: number) => void;|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: global;<br>API declaration: export interface Pattern<br>Differences: export interface Pattern|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: Pattern;<br>API declaration: icon: Resource;<br>Differences: icon: Resource;|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: Pattern;<br>API declaration: selectedIcon: Resource;<br>Differences: selectedIcon: Resource;|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: global;<br>API declaration: export declare struct InputMethodListDialog<br>Differences: export declare struct InputMethodListDialog|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: InputMethodListDialog;<br>API declaration: controller: CustomDialogController;<br>Differences: controller: CustomDialogController;|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: InputMethodListDialog;<br>API declaration: patternOptions?: PatternOptions;<br>Differences: patternOptions?: PatternOptions;|api/@ohos.inputMethodList.d.ets|
|New API|NA|Class name: global;<br>API declaration: export default interface InputMethodSubtype<br>Differences: export default interface InputMethodSubtype|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: readonly label?: string;<br>Differences: readonly label?: string;|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: readonly labelId?: number;<br>Differences: readonly labelId?: number;|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: readonly name: string;<br>Differences: readonly name: string;|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: readonly id: string;<br>Differences: readonly id: string;|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: readonly mode?: 'upper' \| 'lower';<br>Differences: readonly mode?: 'upper' \| 'lower';|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: readonly locale: string;<br>Differences: readonly locale: string;|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: readonly language: string;<br>Differences: readonly language: string;|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: readonly icon?: string;<br>Differences: readonly icon?: string;|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: readonly iconId?: number;<br>Differences: readonly iconId?: number;|api/@ohos.InputMethodSubtype.d.ts|
|New API|NA|Class name: InputMethodSubtype;<br>API declaration: extra?: object;<br>Differences: extra?: object;|api/@ohos.InputMethodSubtype.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.inputMethod.d.ts<br>Differences: IMEKit|api/@ohos.inputMethod.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.inputMethod.Panel.d.ts<br>Differences: IMEKit|api/@ohos.inputMethod.Panel.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.inputMethodEngine.d.ts<br>Differences: IMEKit|api/@ohos.inputMethodEngine.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.InputMethodExtensionAbility.d.ts<br>Differences: IMEKit|api/@ohos.InputMethodExtensionAbility.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.InputMethodExtensionContext.d.ts<br>Differences: IMEKit|api/@ohos.InputMethodExtensionContext.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.inputMethodList.d.ets<br>Differences: IMEKit|api/@ohos.inputMethodList.d.ets|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.InputMethodSubtype.d.ts<br>Differences: IMEKit|api/@ohos.InputMethodSubtype.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.IMEKit.d.ts<br>Differences: IMEKit|kits/@kit.IMEKit.d.ts|
