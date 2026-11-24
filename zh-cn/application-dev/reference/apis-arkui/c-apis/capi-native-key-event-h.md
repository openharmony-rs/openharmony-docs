# native_key_event.h

## 概述

提供NativeKeyEvent相关接口定义。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**相关模块：** [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md) | OH_ArkUI_KeyboardShortcutKey | 定义键盘快捷键按键结构体，描述快捷键按键的设计逻辑，如按键类型和按键值。应用可注册和管理自定义快捷键。 |
| [OH_ArkUI_ApplicationShortcutCallbackInfo](capi-arkui-nativemodule-oh-arkui-applicationshortcutcallbackinfo.md) | OH_ArkUI_ApplicationShortcutCallbackInfo | 定义应用级键盘快捷键的回调信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_KeyCode](#arkui_keycode) | ArkUI_KeyCode | 按键事件的键码。 |
| [ArkUI_KeyEventType](#arkui_keyeventtype) | ArkUI_KeyEventType | 按键的类型。 |
| [ArkUI_KeySourceType](#arkui_keysourcetype) | ArkUI_KeySourceType | 触发当前按键的输入设备类型。 |
| [ArkUI_KeyIntension](#arkui_keyintension) | ArkUI_KeyIntension | 按键对应的意图。 |
| [OH_ArkUI_KeyboardShortcutModifierKey](#oh_arkui_keyboardshortcutmodifierkey) | OH_ArkUI_KeyboardShortcutModifierKey | 枚举键盘快捷键支持的修饰键。<br> 枚举值为位标志，可以使用按位或运算符进行组合。 |
| [OH_ArkUI_KeyboardShortcutFunctionKey](#oh_arkui_keyboardshortcutfunctionkey) | OH_ArkUI_KeyboardShortcutFunctionKey | 枚举键盘快捷键支持的功能键。 |
| [OH_ArkUI_KeyboardShortcutKeyType](#oh_arkui_keyboardshortcutkeytype) | OH_ArkUI_KeyboardShortcutKeyType | 枚举键盘快捷键支持的按键类型。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_Create(ArkUI_UIInputEvent** event)](#oh_arkui_keyevent_create) | - | 创建可通过 [OH_ArkUI_KeyEvent_Dispatch](capi-native-key-event-h.md#oh_arkui_keyevent_dispatch) 分发的按键事件。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_Destroy(ArkUI_UIInputEvent** event)](#oh_arkui_keyevent_destroy) | - | 销毁通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件，并将事件指针置空。<br> 当 **event** 不为空且 **event** 指向的事件指针为空时，函数执行成功。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetType(ArkUI_UIInputEvent* event, ArkUI_KeyEventType type)](#oh_arkui_keyevent_settype) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件类型。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyCode(ArkUI_UIInputEvent* event, int32_t keyCode)](#oh_arkui_keyevent_setkeycode) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件键码。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyText(ArkUI_UIInputEvent* event, const char* keyText)](#oh_arkui_keyevent_setkeytext) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件键值。<br> 本函数会复制 **keyText**。函数返回后，调用方可以释放或复用原字符串。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeySource(ArkUI_UIInputEvent* event, ArkUI_KeySourceType keySource)](#oh_arkui_keyevent_setkeysource) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件输入设备类型。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetDeviceId(ArkUI_UIInputEvent* event, int32_t deviceId)](#oh_arkui_keyevent_setdeviceid) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件设备ID。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetUnicode(ArkUI_UIInputEvent* event, uint32_t unicode)](#oh_arkui_keyevent_setunicode) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件Unicode码值。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetEventTime(ArkUI_UIInputEvent* event, int64_t timestamp)](#oh_arkui_keyevent_seteventtime) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件发生时间。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetPressedKeys(ArkUI_UIInputEvent* event, const int32_t* pressedKeyCodes, int32_t length)](#oh_arkui_keyevent_setpressedkeys) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件中所有已按下的按键。<br> 本函数会复制 **pressedKeyCodes**。函数返回后，调用方可以释放或复用原数组。 将 **pressedKeyCodes** 传入空指针、**length** 传入 **0** 可以清空已按下的按键。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyIntentionCode(ArkUI_UIInputEvent* event, OH_ArkUI_KeyIntention intentionCode)](#oh_arkui_keyevent_setkeyintentioncode) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件意图码。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetNumLockOn(ArkUI_UIInputEvent* event, bool isNumLockOn)](#oh_arkui_keyevent_setnumlockon) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件NumLock状态。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetCapsLockOn(ArkUI_UIInputEvent* event, bool isCapsLockOn)](#oh_arkui_keyevent_setcapslockon) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件CapsLock状态。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetScrollLockOn(ArkUI_UIInputEvent* event, bool isScrollLockOn)](#oh_arkui_keyevent_setscrolllockon) | - | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件ScrollLock状态。 |
| [ArkUI_KeyEventType OH_ArkUI_KeyEvent_GetType(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_gettype) | - | 获取按键的类型。 |
| [int32_t OH_ArkUI_KeyEvent_GetKeyCode(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeycode) | - | 获取按键的键码。 |
| [const char *OH_ArkUI_KeyEvent_GetKeyText(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeytext) | - | 获取按键的键值。 |
| [ArkUI_KeySourceType OH_ArkUI_KeyEvent_GetKeySource(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeysource) | - | 获取当前按键的输入设备类型。 |
| [void OH_ArkUI_KeyEvent_StopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)](#oh_arkui_keyevent_stoppropagation) | - | 阻塞事件冒泡传递。 |
| [ArkUI_KeyIntension OH_ArkUI_KeyEvent_GetKeyIntensionCode(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeyintensioncode) | - | 获取按键对应的意图。 |
| [uint32_t OH_ArkUI_KeyEvent_GetUnicode(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getunicode) | - | 获取按键的Unicode码值。支持范围为非空格的基本拉丁字符：0x0021-0x007E，不支持字符为0。组合键场景下，返回当前keyEvent对应按键的Unicode码值。 |
| [void OH_ArkUI_KeyEvent_SetConsumed(const ArkUI_UIInputEvent* event, bool isConsumed)](#oh_arkui_keyevent_setconsumed) | - | 在按键事件回调中，设置事件是否被该回调消费。 |
| [void OH_ArkUI_KeyEvent_Dispatch(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_dispatch) | - | 将按键事件分发到特定组件节点。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsNumLockOn(const ArkUI_UIInputEvent* event, bool* state)](#oh_arkui_keyevent_isnumlockon) | - | 获取按键事件发生时NumLock的状态。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsCapsLockOn(const ArkUI_UIInputEvent* event, bool* state)](#oh_arkui_keyevent_iscapslockon) | - | 获取按键事件发生时CapsLock的状态。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsScrollLockOn(const ArkUI_UIInputEvent* event, bool* state)](#oh_arkui_keyevent_isscrolllockon) | - | 获取按键事件发生时ScrollLock的状态。 |
| [OH_ArkUI_KeyboardShortcutKey* OH_ArkUI_KeyboardShortcutKey_Create(void)](#oh_arkui_keyboardshortcutkey_create) | - | 创建键盘快捷键按键对象。可调用[OH_ArkUI_KeyboardShortcutKey_Destroy](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkey_destroy)销毁键盘快捷键按键对象。 |
| [void OH_ArkUI_KeyboardShortcutKey_Destroy(OH_ArkUI_KeyboardShortcutKey** key)](#oh_arkui_keyboardshortcutkey_destroy) | - | 销毁键盘快捷键按键对象。 |
| [void OH_ArkUI_KeyboardShortcutKey_SetType(OH_ArkUI_KeyboardShortcutKey* key, OH_ArkUI_KeyboardShortcutKeyType type)](#oh_arkui_keyboardshortcutkey_settype) | - | 设置键盘快捷键按键的类型。 |
| [OH_ArkUI_KeyboardShortcutKeyType OH_ArkUI_KeyboardShortcutKey_GetType(const OH_ArkUI_KeyboardShortcutKey* key)](#oh_arkui_keyboardshortcutkey_gettype) | - | 获取键盘快捷键按键的类型。 |
| [void OH_ArkUI_KeyboardShortcutKey_SetCharacter(OH_ArkUI_KeyboardShortcutKey* key, char character)](#oh_arkui_keyboardshortcutkey_setcharacter) | - | 设置字符键盘快捷键按键的字符。调用此函数前，按键类型必须已设置为 [OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_CHARACTER](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkeytype)。 |
| [char OH_ArkUI_KeyboardShortcutKey_GetCharacter(const OH_ArkUI_KeyboardShortcutKey* key)](#oh_arkui_keyboardshortcutkey_getcharacter) | - | 获取字符键盘快捷键按键的字符。 |
| [void OH_ArkUI_KeyboardShortcutKey_SetFunctionKey(OH_ArkUI_KeyboardShortcutKey* key, OH_ArkUI_KeyboardShortcutFunctionKey functionKey)](#oh_arkui_keyboardshortcutkey_setfunctionkey) | - | 设置功能键盘快捷键按键的功能键。调用此函数前，按键类型必须已设置为 [OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_FUNCTION_KEY](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkeytype)。 |
| [OH_ArkUI_KeyboardShortcutFunctionKey OH_ArkUI_KeyboardShortcutKey_GetFunctionKey(const OH_ArkUI_KeyboardShortcutKey* key)](#oh_arkui_keyboardshortcutkey_getfunctionkey) | - | 获取功能键盘快捷键按键的功能键。 |
| [typedef void (\*OH_ArkUI_ApplicationShortcutCallback)(const OH_ArkUI_ApplicationShortcutCallbackInfo* info, void* userData)](#oh_arkui_applicationshortcutcallback) | OH_ArkUI_ApplicationShortcutCallback | 定义应用级键盘快捷键触发时调用的回调函数。该回调在触发快捷键的UI实例对应的UI线程上执行。 |
| [ArkUI_ContextHandle OH_ArkUI_ApplicationShortcutCallbackInfo_GetUIContext(const OH_ArkUI_ApplicationShortcutCallbackInfo* info)](#oh_arkui_applicationshortcutcallbackinfo_getuicontext) | - | 获取触发应用级键盘快捷键的UI实例对应的UI上下文。 |
| [ArkUI_ErrorCode OH_ArkUI_ApplicationShortcut_Register(const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys, void* userData, OH_ArkUI_ApplicationShortcutCallback callback, int32_t* registrationId)](#oh_arkui_applicationshortcut_register) | - | 注册应用级键盘快捷键。该快捷键在应用内全局生效。 如果存在匹配的组件级快捷键，则优先触发组件级快捷键。<br> 每次注册生成一个应用内唯一的正整数注册标识符，即使快捷键和回调相同，标识符也不同。 同一个快捷键的多次注册均被保留，仅最近一次未注销的注册生效。 注册标识符在应用运行期间不复用。 |
| [ArkUI_ErrorCode OH_ArkUI_ApplicationShortcut_Unregister(int32_t registrationId)](#oh_arkui_applicationshortcut_unregister) | - | 注销指定注册标识符对应的应用级键盘快捷键绑定。<br> 仅移除该标识符对应的绑定，其他绑定不受影响。如果移除的是当前生效的绑定， 则最近一次仍未注销的同快捷键绑定恢复生效。标识符不存在或已注销时，不执行任何操作，仍返回成功。 |
| [typedef void (\*OH_ArkUI_KeyboardShortcutCallback)(void* userData)](#oh_arkui_keyboardshortcutcallback) | OH_ArkUI_KeyboardShortcutCallback | 定义组件级键盘快捷键触发时调用的回调函数。 |
| [ArkUI_ErrorCode OH_ArkUI_NodeKeyboardShortcut_Register(ArkUI_NodeHandle node, const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys, void* userData, OH_ArkUI_KeyboardShortcutCallback callback)](#oh_arkui_nodekeyboardshortcut_register) | - | 为组件注册键盘快捷键。同一组件重复注册相同快捷键时，以最后一次注册为准。组件级快捷键的触发优先级 高于相同的应用级快捷键。 |
| [ArkUI_ErrorCode OH_ArkUI_NodeKeyboardShortcut_Unregister(ArkUI_NodeHandle node, const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys)](#oh_arkui_nodekeyboardshortcut_unregister) | - | 注销组件的键盘快捷键。如果没有注册匹配的快捷键，该操作仍然成功。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| ArkUI_KeyIntension OH_ArkUI_KeyIntention | 按键事件意图类型的正确拼写别名。<br> 原类型名 [ArkUI_KeyIntension](capi-native-key-event-h.md#arkui_keyintension) 将保留以兼容已有接口。<br>**起始版本：** 26.1.0<br>**系统能力：** SystemCapability.ArkUI.ArkUI.Full<br><!--Device-ArkUI_KeyIntension OH_ArkUI_KeyIntention--><!--Device-ArkUI_KeyIntension OH_ArkUI_KeyIntention-End--> |

## 枚举类型说明

### ArkUI_KeyCode

```c
enum ArkUI_KeyCode
```

**描述：**

按键事件的键码。

<!--Device-enum ArkUI_KeyCode--><!--Device-enum ArkUI_KeyCode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEYCODE_UNKNOWN = -1 | 未知按键。<br><!--Device-ARKUI_KEYCODE_UNKNOWN = -1--><!--Device-ARKUI_KEYCODE_UNKNOWN = -1-End--> |
| ARKUI_KEYCODE_FN = 0 | 功能（Fn）键。<br><!--Device-ARKUI_KEYCODE_FN = 0--><!--Device-ARKUI_KEYCODE_FN = 0-End--> |
| ARKUI_KEYCODE_VOLUME_UP = 16 | 音量增加键。<br><!--Device-ARKUI_KEYCODE_VOLUME_UP = 16--><!--Device-ARKUI_KEYCODE_VOLUME_UP = 16-End--> |
| ARKUI_KEYCODE_VOLUME_DOWN = 17 | 音量减小键。<br><!--Device-ARKUI_KEYCODE_VOLUME_DOWN = 17--><!--Device-ARKUI_KEYCODE_VOLUME_DOWN = 17-End--> |
| ARKUI_KEYCODE_POWER = 18 | 电源键。<br><!--Device-ARKUI_KEYCODE_POWER = 18--><!--Device-ARKUI_KEYCODE_POWER = 18-End--> |
| ARKUI_KEYCODE_CAMERA = 19 | 拍照键。<br><!--Device-ARKUI_KEYCODE_CAMERA = 19--><!--Device-ARKUI_KEYCODE_CAMERA = 19-End--> |
| ARKUI_KEYCODE_VOLUME_MUTE = 22 | 扬声器静音键。<br><!--Device-ARKUI_KEYCODE_VOLUME_MUTE = 22--><!--Device-ARKUI_KEYCODE_VOLUME_MUTE = 22-End--> |
| ARKUI_KEYCODE_MUTE = 23 | 话筒静音键。<br><!--Device-ARKUI_KEYCODE_MUTE = 23--><!--Device-ARKUI_KEYCODE_MUTE = 23-End--> |
| ARKUI_KEYCODE_BRIGHTNESS_UP = 40 | 亮度调节按键，调亮。<br><!--Device-ARKUI_KEYCODE_BRIGHTNESS_UP = 40--><!--Device-ARKUI_KEYCODE_BRIGHTNESS_UP = 40-End--> |
| ARKUI_KEYCODE_BRIGHTNESS_DOWN = 41 | 亮度调节按键，调暗。<br><!--Device-ARKUI_KEYCODE_BRIGHTNESS_DOWN = 41--><!--Device-ARKUI_KEYCODE_BRIGHTNESS_DOWN = 41-End--> |
| ARKUI_KEYCODE_0 = 2000 | 按键'0'。<br><!--Device-ARKUI_KEYCODE_0 = 2000--><!--Device-ARKUI_KEYCODE_0 = 2000-End--> |
| ARKUI_KEYCODE_1 = 2001 | 按键'1'。<br><!--Device-ARKUI_KEYCODE_1 = 2001--><!--Device-ARKUI_KEYCODE_1 = 2001-End--> |
| ARKUI_KEYCODE_2 = 2002 | 按键'2'。<br><!--Device-ARKUI_KEYCODE_2 = 2002--><!--Device-ARKUI_KEYCODE_2 = 2002-End--> |
| ARKUI_KEYCODE_3 = 2003 | 按键'3'。<br><!--Device-ARKUI_KEYCODE_3 = 2003--><!--Device-ARKUI_KEYCODE_3 = 2003-End--> |
| ARKUI_KEYCODE_4 = 2004 | 按键'4'。<br><!--Device-ARKUI_KEYCODE_4 = 2004--><!--Device-ARKUI_KEYCODE_4 = 2004-End--> |
| ARKUI_KEYCODE_5 = 2005 | 按键'5'。<br><!--Device-ARKUI_KEYCODE_5 = 2005--><!--Device-ARKUI_KEYCODE_5 = 2005-End--> |
| ARKUI_KEYCODE_6 = 2006 | 按键'6'。<br><!--Device-ARKUI_KEYCODE_6 = 2006--><!--Device-ARKUI_KEYCODE_6 = 2006-End--> |
| ARKUI_KEYCODE_7 = 2007 | 按键'7'。<br><!--Device-ARKUI_KEYCODE_7 = 2007--><!--Device-ARKUI_KEYCODE_7 = 2007-End--> |
| ARKUI_KEYCODE_8 = 2008 | 按键'8'。<br><!--Device-ARKUI_KEYCODE_8 = 2008--><!--Device-ARKUI_KEYCODE_8 = 2008-End--> |
| ARKUI_KEYCODE_9 = 2009 | 按键'9'。<br><!--Device-ARKUI_KEYCODE_9 = 2009--><!--Device-ARKUI_KEYCODE_9 = 2009-End--> |
| ARKUI_KEYCODE_STAR = 2010 | 按键'+'。<br><!--Device-ARKUI_KEYCODE_STAR = 2010--><!--Device-ARKUI_KEYCODE_STAR = 2010-End--> |
| ARKUI_KEYCODE_POUND = 2011 | 按键'#'。<br><!--Device-ARKUI_KEYCODE_POUND = 2011--><!--Device-ARKUI_KEYCODE_POUND = 2011-End--> |
| ARKUI_KEYCODE_DPAD_UP = 2012 | 导航键，向上。<br><!--Device-ARKUI_KEYCODE_DPAD_UP = 2012--><!--Device-ARKUI_KEYCODE_DPAD_UP = 2012-End--> |
| ARKUI_KEYCODE_DPAD_DOWN = 2013 | 导航键，向下。<br><!--Device-ARKUI_KEYCODE_DPAD_DOWN = 2013--><!--Device-ARKUI_KEYCODE_DPAD_DOWN = 2013-End--> |
| ARKUI_KEYCODE_DPAD_LEFT = 2014 | 导航键，向左。<br><!--Device-ARKUI_KEYCODE_DPAD_LEFT = 2014--><!--Device-ARKUI_KEYCODE_DPAD_LEFT = 2014-End--> |
| ARKUI_KEYCODE_DPAD_RIGHT = 2015 | 导航键，向右。<br><!--Device-ARKUI_KEYCODE_DPAD_RIGHT = 2015--><!--Device-ARKUI_KEYCODE_DPAD_RIGHT = 2015-End--> |
| ARKUI_KEYCODE_DPAD_CENTER = 2016 | 导航键，确定键。<br><!--Device-ARKUI_KEYCODE_DPAD_CENTER = 2016--><!--Device-ARKUI_KEYCODE_DPAD_CENTER = 2016-End--> |
| ARKUI_KEYCODE_A = 2017 | 按键'A'。<br><!--Device-ARKUI_KEYCODE_A = 2017--><!--Device-ARKUI_KEYCODE_A = 2017-End--> |
| ARKUI_KEYCODE_B = 2018 | 按键'B'。<br><!--Device-ARKUI_KEYCODE_B = 2018--><!--Device-ARKUI_KEYCODE_B = 2018-End--> |
| ARKUI_KEYCODE_C = 2019 | 按键'C'。<br><!--Device-ARKUI_KEYCODE_C = 2019--><!--Device-ARKUI_KEYCODE_C = 2019-End--> |
| ARKUI_KEYCODE_D = 2020 | 按键'D'。<br><!--Device-ARKUI_KEYCODE_D = 2020--><!--Device-ARKUI_KEYCODE_D = 2020-End--> |
| ARKUI_KEYCODE_E = 2021 | 按键'E'。<br><!--Device-ARKUI_KEYCODE_E = 2021--><!--Device-ARKUI_KEYCODE_E = 2021-End--> |
| ARKUI_KEYCODE_F = 2022 | 按键'F'。<br><!--Device-ARKUI_KEYCODE_F = 2022--><!--Device-ARKUI_KEYCODE_F = 2022-End--> |
| ARKUI_KEYCODE_G = 2023 | 按键'G'。<br><!--Device-ARKUI_KEYCODE_G = 2023--><!--Device-ARKUI_KEYCODE_G = 2023-End--> |
| ARKUI_KEYCODE_H = 2024 | 按键'H'。<br><!--Device-ARKUI_KEYCODE_H = 2024--><!--Device-ARKUI_KEYCODE_H = 2024-End--> |
| ARKUI_KEYCODE_I = 2025 | 按键'I'。<br><!--Device-ARKUI_KEYCODE_I = 2025--><!--Device-ARKUI_KEYCODE_I = 2025-End--> |
| ARKUI_KEYCODE_J = 2026 | 按键'J'。<br><!--Device-ARKUI_KEYCODE_J = 2026--><!--Device-ARKUI_KEYCODE_J = 2026-End--> |
| ARKUI_KEYCODE_K = 2027 | 按键'K'。<br><!--Device-ARKUI_KEYCODE_K = 2027--><!--Device-ARKUI_KEYCODE_K = 2027-End--> |
| ARKUI_KEYCODE_L = 2028 | 按键'L'。<br><!--Device-ARKUI_KEYCODE_L = 2028--><!--Device-ARKUI_KEYCODE_L = 2028-End--> |
| ARKUI_KEYCODE_M = 2029 | 按键'M'。<br><!--Device-ARKUI_KEYCODE_M = 2029--><!--Device-ARKUI_KEYCODE_M = 2029-End--> |
| ARKUI_KEYCODE_N = 2030 | 按键'N'。<br><!--Device-ARKUI_KEYCODE_N = 2030--><!--Device-ARKUI_KEYCODE_N = 2030-End--> |
| ARKUI_KEYCODE_O = 2031 | 按键'O'。<br><!--Device-ARKUI_KEYCODE_O = 2031--><!--Device-ARKUI_KEYCODE_O = 2031-End--> |
| ARKUI_KEYCODE_P = 2032 | 按键'P'。<br><!--Device-ARKUI_KEYCODE_P = 2032--><!--Device-ARKUI_KEYCODE_P = 2032-End--> |
| ARKUI_KEYCODE_Q = 2033 | 按键'Q'。<br><!--Device-ARKUI_KEYCODE_Q = 2033--><!--Device-ARKUI_KEYCODE_Q = 2033-End--> |
| ARKUI_KEYCODE_R = 2034 | 按键'R'。<br><!--Device-ARKUI_KEYCODE_R = 2034--><!--Device-ARKUI_KEYCODE_R = 2034-End--> |
| ARKUI_KEYCODE_S = 2035 | 按键'S'。<br><!--Device-ARKUI_KEYCODE_S = 2035--><!--Device-ARKUI_KEYCODE_S = 2035-End--> |
| ARKUI_KEYCODE_T = 2036 | 按键'T'。<br><!--Device-ARKUI_KEYCODE_T = 2036--><!--Device-ARKUI_KEYCODE_T = 2036-End--> |
| ARKUI_KEYCODE_U = 2037 | 按键'U'。<br><!--Device-ARKUI_KEYCODE_U = 2037--><!--Device-ARKUI_KEYCODE_U = 2037-End--> |
| ARKUI_KEYCODE_V = 2038 | 按键'V'。<br><!--Device-ARKUI_KEYCODE_V = 2038--><!--Device-ARKUI_KEYCODE_V = 2038-End--> |
| ARKUI_KEYCODE_W = 2039 | 按键'W'。<br><!--Device-ARKUI_KEYCODE_W = 2039--><!--Device-ARKUI_KEYCODE_W = 2039-End--> |
| ARKUI_KEYCODE_X = 2040 | 按键'X'。<br><!--Device-ARKUI_KEYCODE_X = 2040--><!--Device-ARKUI_KEYCODE_X = 2040-End--> |
| ARKUI_KEYCODE_Y = 2041 | 按键'Y'。<br><!--Device-ARKUI_KEYCODE_Y = 2041--><!--Device-ARKUI_KEYCODE_Y = 2041-End--> |
| ARKUI_KEYCODE_Z = 2042 | 按键'Z'。<br><!--Device-ARKUI_KEYCODE_Z = 2042--><!--Device-ARKUI_KEYCODE_Z = 2042-End--> |
| ARKUI_KEYCODE_COMMA = 2043 | 按键','。<br><!--Device-ARKUI_KEYCODE_COMMA = 2043--><!--Device-ARKUI_KEYCODE_COMMA = 2043-End--> |
| ARKUI_KEYCODE_PERIOD = 2044 | 按键'.'。<br><!--Device-ARKUI_KEYCODE_PERIOD = 2044--><!--Device-ARKUI_KEYCODE_PERIOD = 2044-End--> |
| ARKUI_KEYCODE_ALT_LEFT = 2045 | 左Alt键。<br><!--Device-ARKUI_KEYCODE_ALT_LEFT = 2045--><!--Device-ARKUI_KEYCODE_ALT_LEFT = 2045-End--> |
| ARKUI_KEYCODE_ALT_RIGHT = 2046 | 右Alt键。<br><!--Device-ARKUI_KEYCODE_ALT_RIGHT = 2046--><!--Device-ARKUI_KEYCODE_ALT_RIGHT = 2046-End--> |
| ARKUI_KEYCODE_SHIFT_LEFT = 2047 | 左Shift键。<br><!--Device-ARKUI_KEYCODE_SHIFT_LEFT = 2047--><!--Device-ARKUI_KEYCODE_SHIFT_LEFT = 2047-End--> |
| ARKUI_KEYCODE_SHIFT_RIGHT = 2048 | 右Shift键。<br><!--Device-ARKUI_KEYCODE_SHIFT_RIGHT = 2048--><!--Device-ARKUI_KEYCODE_SHIFT_RIGHT = 2048-End--> |
| ARKUI_KEYCODE_TAB = 2049 | Tab键。<br><!--Device-ARKUI_KEYCODE_TAB = 2049--><!--Device-ARKUI_KEYCODE_TAB = 2049-End--> |
| ARKUI_KEYCODE_SPACE = 2050 | 空格键。<br><!--Device-ARKUI_KEYCODE_SPACE = 2050--><!--Device-ARKUI_KEYCODE_SPACE = 2050-End--> |
| ARKUI_KEYCODE_SYM = 2051 | 符号修改器按键。<br><!--Device-ARKUI_KEYCODE_SYM = 2051--><!--Device-ARKUI_KEYCODE_SYM = 2051-End--> |
| ARKUI_KEYCODE_EXPLORER = 2052 | 浏览器功能键，此键用于启动浏览器应用程序。<br><!--Device-ARKUI_KEYCODE_EXPLORER = 2052--><!--Device-ARKUI_KEYCODE_EXPLORER = 2052-End--> |
| ARKUI_KEYCODE_ENVELOPE = 2053 | 电子邮件功能键，此键用于启动电子邮件应用程序。<br><!--Device-ARKUI_KEYCODE_ENVELOPE = 2053--><!--Device-ARKUI_KEYCODE_ENVELOPE = 2053-End--> |
| ARKUI_KEYCODE_ENTER = 2054 | 回车键。<br><!--Device-ARKUI_KEYCODE_ENTER = 2054--><!--Device-ARKUI_KEYCODE_ENTER = 2054-End--> |
| ARKUI_KEYCODE_DEL = 2055 | 退格键。<br><!--Device-ARKUI_KEYCODE_DEL = 2055--><!--Device-ARKUI_KEYCODE_DEL = 2055-End--> |
| ARKUI_KEYCODE_GRAVE = 2056 | 按键'`'。<br><!--Device-ARKUI_KEYCODE_GRAVE = 2056--><!--Device-ARKUI_KEYCODE_GRAVE = 2056-End--> |
| ARKUI_KEYCODE_MINUS = 2057 | 按键'-'。<br><!--Device-ARKUI_KEYCODE_MINUS = 2057--><!--Device-ARKUI_KEYCODE_MINUS = 2057-End--> |
| ARKUI_KEYCODE_EQUALS = 2058 | 按键'='。<br><!--Device-ARKUI_KEYCODE_EQUALS = 2058--><!--Device-ARKUI_KEYCODE_EQUALS = 2058-End--> |
| ARKUI_KEYCODE_LEFT_BRACKET = 2059 | 按键'['。<br><!--Device-ARKUI_KEYCODE_LEFT_BRACKET = 2059--><!--Device-ARKUI_KEYCODE_LEFT_BRACKET = 2059-End--> |
| ARKUI_KEYCODE_RIGHT_BRACKET = 2060 | 按键']'。<br><!--Device-ARKUI_KEYCODE_RIGHT_BRACKET = 2060--><!--Device-ARKUI_KEYCODE_RIGHT_BRACKET = 2060-End--> |
| ARKUI_KEYCODE_BACKSLASH = 2061 | 按键'\'。<br><!--Device-ARKUI_KEYCODE_BACKSLASH = 2061--><!--Device-ARKUI_KEYCODE_BACKSLASH = 2061-End--> |
| ARKUI_KEYCODE_SEMICOLON = 2062 | 按键';'。<br><!--Device-ARKUI_KEYCODE_SEMICOLON = 2062--><!--Device-ARKUI_KEYCODE_SEMICOLON = 2062-End--> |
| ARKUI_KEYCODE_APOSTROPHE = 2063 | 按键''' (单引号)。<br><!--Device-ARKUI_KEYCODE_APOSTROPHE = 2063--><!--Device-ARKUI_KEYCODE_APOSTROPHE = 2063-End--> |
| ARKUI_KEYCODE_SLASH = 2064 | 按键'/'。<br><!--Device-ARKUI_KEYCODE_SLASH = 2064--><!--Device-ARKUI_KEYCODE_SLASH = 2064-End--> |
| ARKUI_KEYCODE_AT = 2065 | 按键 '@'。<br><!--Device-ARKUI_KEYCODE_AT = 2065--><!--Device-ARKUI_KEYCODE_AT = 2065-End--> |
| ARKUI_KEYCODE_PLUS = 2066 | 按键'+'。<br><!--Device-ARKUI_KEYCODE_PLUS = 2066--><!--Device-ARKUI_KEYCODE_PLUS = 2066-End--> |
| ARKUI_KEYCODE_MENU = 2067 | 菜单键。<br><!--Device-ARKUI_KEYCODE_MENU = 2067--><!--Device-ARKUI_KEYCODE_MENU = 2067-End--> |
| ARKUI_KEYCODE_PAGE_UP = 2068 | 向上翻页键。<br><!--Device-ARKUI_KEYCODE_PAGE_UP = 2068--><!--Device-ARKUI_KEYCODE_PAGE_UP = 2068-End--> |
| ARKUI_KEYCODE_PAGE_DOWN = 2069 | 向下翻页键。<br><!--Device-ARKUI_KEYCODE_PAGE_DOWN = 2069--><!--Device-ARKUI_KEYCODE_PAGE_DOWN = 2069-End--> |
| ARKUI_KEYCODE_ESCAPE = 2070 | ESC键。<br><!--Device-ARKUI_KEYCODE_ESCAPE = 2070--><!--Device-ARKUI_KEYCODE_ESCAPE = 2070-End--> |
| ARKUI_KEYCODE_FORWARD_DEL = 2071 | 删除键。<br><!--Device-ARKUI_KEYCODE_FORWARD_DEL = 2071--><!--Device-ARKUI_KEYCODE_FORWARD_DEL = 2071-End--> |
| ARKUI_KEYCODE_CTRL_LEFT = 2072 | 左Ctrl键。<br><!--Device-ARKUI_KEYCODE_CTRL_LEFT = 2072--><!--Device-ARKUI_KEYCODE_CTRL_LEFT = 2072-End--> |
| ARKUI_KEYCODE_CTRL_RIGHT = 2073 | 右Ctrl键。<br><!--Device-ARKUI_KEYCODE_CTRL_RIGHT = 2073--><!--Device-ARKUI_KEYCODE_CTRL_RIGHT = 2073-End--> |
| ARKUI_KEYCODE_CAPS_LOCK = 2074 | 大写锁定键。<br><!--Device-ARKUI_KEYCODE_CAPS_LOCK = 2074--><!--Device-ARKUI_KEYCODE_CAPS_LOCK = 2074-End--> |
| ARKUI_KEYCODE_SCROLL_LOCK = 2075 | 滚动锁定键。<br><!--Device-ARKUI_KEYCODE_SCROLL_LOCK = 2075--><!--Device-ARKUI_KEYCODE_SCROLL_LOCK = 2075-End--> |
| ARKUI_KEYCODE_META_LEFT = 2076 | 左元修改器键。<br><!--Device-ARKUI_KEYCODE_META_LEFT = 2076--><!--Device-ARKUI_KEYCODE_META_LEFT = 2076-End--> |
| ARKUI_KEYCODE_META_RIGHT = 2077 | 右元修改器键。<br><!--Device-ARKUI_KEYCODE_META_RIGHT = 2077--><!--Device-ARKUI_KEYCODE_META_RIGHT = 2077-End--> |
| ARKUI_KEYCODE_FUNCTION = 2078 | 功能键。<br><!--Device-ARKUI_KEYCODE_FUNCTION = 2078--><!--Device-ARKUI_KEYCODE_FUNCTION = 2078-End--> |
| ARKUI_KEYCODE_SYSRQ = 2079 | 系统请求/打印屏幕键。<br><!--Device-ARKUI_KEYCODE_SYSRQ = 2079--><!--Device-ARKUI_KEYCODE_SYSRQ = 2079-End--> |
| ARKUI_KEYCODE_BREAK = 2080 | Break/Pause键。<br><!--Device-ARKUI_KEYCODE_BREAK = 2080--><!--Device-ARKUI_KEYCODE_BREAK = 2080-End--> |
| ARKUI_KEYCODE_MOVE_HOME = 2081 | 光标移动到开始键。<br><!--Device-ARKUI_KEYCODE_MOVE_HOME = 2081--><!--Device-ARKUI_KEYCODE_MOVE_HOME = 2081-End--> |
| ARKUI_KEYCODE_MOVE_END = 2082 | 光标移动到末尾键。<br><!--Device-ARKUI_KEYCODE_MOVE_END = 2082--><!--Device-ARKUI_KEYCODE_MOVE_END = 2082-End--> |
| ARKUI_KEYCODE_INSERT = 2083 | 插入键。<br><!--Device-ARKUI_KEYCODE_INSERT = 2083--><!--Device-ARKUI_KEYCODE_INSERT = 2083-End--> |
| ARKUI_KEYCODE_FORWARD = 2084 | 前进键。<br><!--Device-ARKUI_KEYCODE_FORWARD = 2084--><!--Device-ARKUI_KEYCODE_FORWARD = 2084-End--> |
| ARKUI_KEYCODE_MEDIA_PLAY = 2085 | 多媒体键，播放。<br><!--Device-ARKUI_KEYCODE_MEDIA_PLAY = 2085--><!--Device-ARKUI_KEYCODE_MEDIA_PLAY = 2085-End--> |
| ARKUI_KEYCODE_MEDIA_PAUSE = 2086 | 多媒体键，暂停。<br><!--Device-ARKUI_KEYCODE_MEDIA_PAUSE = 2086--><!--Device-ARKUI_KEYCODE_MEDIA_PAUSE = 2086-End--> |
| ARKUI_KEYCODE_MEDIA_CLOSE = 2087 | 多媒体键，关闭。<br><!--Device-ARKUI_KEYCODE_MEDIA_CLOSE = 2087--><!--Device-ARKUI_KEYCODE_MEDIA_CLOSE = 2087-End--> |
| ARKUI_KEYCODE_MEDIA_EJECT = 2088 | 多媒体键，弹出。<br><!--Device-ARKUI_KEYCODE_MEDIA_EJECT = 2088--><!--Device-ARKUI_KEYCODE_MEDIA_EJECT = 2088-End--> |
| ARKUI_KEYCODE_MEDIA_RECORD = 2089 | 多媒体键，录音。<br><!--Device-ARKUI_KEYCODE_MEDIA_RECORD = 2089--><!--Device-ARKUI_KEYCODE_MEDIA_RECORD = 2089-End--> |
| ARKUI_KEYCODE_F1 = 2090 | 按键'F1'。<br><!--Device-ARKUI_KEYCODE_F1 = 2090--><!--Device-ARKUI_KEYCODE_F1 = 2090-End--> |
| ARKUI_KEYCODE_F2 = 2091 | 按键'F2'。<br><!--Device-ARKUI_KEYCODE_F2 = 2091--><!--Device-ARKUI_KEYCODE_F2 = 2091-End--> |
| ARKUI_KEYCODE_F3 = 2092 | 按键'F3'。<br><!--Device-ARKUI_KEYCODE_F3 = 2092--><!--Device-ARKUI_KEYCODE_F3 = 2092-End--> |
| ARKUI_KEYCODE_F4 = 2093 | 按键'F4'。<br><!--Device-ARKUI_KEYCODE_F4 = 2093--><!--Device-ARKUI_KEYCODE_F4 = 2093-End--> |
| ARKUI_KEYCODE_F5 = 2094 | 按键'F5'。<br><!--Device-ARKUI_KEYCODE_F5 = 2094--><!--Device-ARKUI_KEYCODE_F5 = 2094-End--> |
| ARKUI_KEYCODE_F6 = 2095 | 按键'F6'。<br><!--Device-ARKUI_KEYCODE_F6 = 2095--><!--Device-ARKUI_KEYCODE_F6 = 2095-End--> |
| ARKUI_KEYCODE_F7 = 2096 | 按键'F7'。<br><!--Device-ARKUI_KEYCODE_F7 = 2096--><!--Device-ARKUI_KEYCODE_F7 = 2096-End--> |
| ARKUI_KEYCODE_F8 = 2097 | 按键'F8'。<br><!--Device-ARKUI_KEYCODE_F8 = 2097--><!--Device-ARKUI_KEYCODE_F8 = 2097-End--> |
| ARKUI_KEYCODE_F9 = 2098 | 按键'F9'。<br><!--Device-ARKUI_KEYCODE_F9 = 2098--><!--Device-ARKUI_KEYCODE_F9 = 2098-End--> |
| ARKUI_KEYCODE_F10 = 2099 | 按键'F10'。<br><!--Device-ARKUI_KEYCODE_F10 = 2099--><!--Device-ARKUI_KEYCODE_F10 = 2099-End--> |
| ARKUI_KEYCODE_F11 = 2100 | 按键'F11'。<br><!--Device-ARKUI_KEYCODE_F11 = 2100--><!--Device-ARKUI_KEYCODE_F11 = 2100-End--> |
| ARKUI_KEYCODE_F12 = 2101 | 按键'F12'。<br><!--Device-ARKUI_KEYCODE_F12 = 2101--><!--Device-ARKUI_KEYCODE_F12 = 2101-End--> |
| ARKUI_KEYCODE_NUM_LOCK = 2102 | 小键盘锁。<br><!--Device-ARKUI_KEYCODE_NUM_LOCK = 2102--><!--Device-ARKUI_KEYCODE_NUM_LOCK = 2102-End--> |
| ARKUI_KEYCODE_NUMPAD_0 = 2103 | 小键盘按键'0'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_0 = 2103--><!--Device-ARKUI_KEYCODE_NUMPAD_0 = 2103-End--> |
| ARKUI_KEYCODE_NUMPAD_1 = 2104 | 小键盘按键'1'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_1 = 2104--><!--Device-ARKUI_KEYCODE_NUMPAD_1 = 2104-End--> |
| ARKUI_KEYCODE_NUMPAD_2 = 2105 | 小键盘按键'2'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_2 = 2105--><!--Device-ARKUI_KEYCODE_NUMPAD_2 = 2105-End--> |
| ARKUI_KEYCODE_NUMPAD_3 = 2106 | 小键盘按键'3'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_3 = 2106--><!--Device-ARKUI_KEYCODE_NUMPAD_3 = 2106-End--> |
| ARKUI_KEYCODE_NUMPAD_4 = 2107 | 小键盘按键'4'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_4 = 2107--><!--Device-ARKUI_KEYCODE_NUMPAD_4 = 2107-End--> |
| ARKUI_KEYCODE_NUMPAD_5 = 2108 | 小键盘按键'5'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_5 = 2108--><!--Device-ARKUI_KEYCODE_NUMPAD_5 = 2108-End--> |
| ARKUI_KEYCODE_NUMPAD_6 = 2109 | 小键盘按键'6'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_6 = 2109--><!--Device-ARKUI_KEYCODE_NUMPAD_6 = 2109-End--> |
| ARKUI_KEYCODE_NUMPAD_7 = 2110 | 小键盘按键'7'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_7 = 2110--><!--Device-ARKUI_KEYCODE_NUMPAD_7 = 2110-End--> |
| ARKUI_KEYCODE_NUMPAD_8 = 2111 | 小键盘按键'8'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_8 = 2111--><!--Device-ARKUI_KEYCODE_NUMPAD_8 = 2111-End--> |
| ARKUI_KEYCODE_NUMPAD_9 = 2112 | 小键盘按键'9'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_9 = 2112--><!--Device-ARKUI_KEYCODE_NUMPAD_9 = 2112-End--> |
| ARKUI_KEYCODE_NUMPAD_DIVIDE = 2113 | 小键盘按键'/'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_DIVIDE = 2113--><!--Device-ARKUI_KEYCODE_NUMPAD_DIVIDE = 2113-End--> |
| ARKUI_KEYCODE_NUMPAD_MULTIPLY = 2114 | 小键盘按键'*'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_MULTIPLY = 2114--><!--Device-ARKUI_KEYCODE_NUMPAD_MULTIPLY = 2114-End--> |
| ARKUI_KEYCODE_NUMPAD_SUBTRACT = 2115 | 小键盘按键'-'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_SUBTRACT = 2115--><!--Device-ARKUI_KEYCODE_NUMPAD_SUBTRACT = 2115-End--> |
| ARKUI_KEYCODE_NUMPAD_ADD = 2116 | 小键盘按键'+'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_ADD = 2116--><!--Device-ARKUI_KEYCODE_NUMPAD_ADD = 2116-End--> |
| ARKUI_KEYCODE_NUMPAD_DOT = 2117 | 小键盘按键'.'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_DOT = 2117--><!--Device-ARKUI_KEYCODE_NUMPAD_DOT = 2117-End--> |
| ARKUI_KEYCODE_NUMPAD_COMMA = 2118 | 小键盘按键','。<br><!--Device-ARKUI_KEYCODE_NUMPAD_COMMA = 2118--><!--Device-ARKUI_KEYCODE_NUMPAD_COMMA = 2118-End--> |
| ARKUI_KEYCODE_NUMPAD_ENTER = 2119 | 小键盘按键回车。<br><!--Device-ARKUI_KEYCODE_NUMPAD_ENTER = 2119--><!--Device-ARKUI_KEYCODE_NUMPAD_ENTER = 2119-End--> |
| ARKUI_KEYCODE_NUMPAD_EQUALS = 2120 | 小键盘按键'='。<br><!--Device-ARKUI_KEYCODE_NUMPAD_EQUALS = 2120--><!--Device-ARKUI_KEYCODE_NUMPAD_EQUALS = 2120-End--> |
| ARKUI_KEYCODE_NUMPAD_LEFT_PAREN = 2121 | 小键盘按键'('。<br><!--Device-ARKUI_KEYCODE_NUMPAD_LEFT_PAREN = 2121--><!--Device-ARKUI_KEYCODE_NUMPAD_LEFT_PAREN = 2121-End--> |
| ARKUI_KEYCODE_NUMPAD_RIGHT_PAREN = 2122 | 小键盘按键')'。<br><!--Device-ARKUI_KEYCODE_NUMPAD_RIGHT_PAREN = 2122--><!--Device-ARKUI_KEYCODE_NUMPAD_RIGHT_PAREN = 2122-End--> |
| ARKUI_KEYCODE_BUTTON_A = 2301 | 游戏手柄按键'A'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_A = 2301--><!--Device-ARKUI_KEYCODE_BUTTON_A = 2301-End--> |
| ARKUI_KEYCODE_BUTTON_B = 2302 | 游戏手柄按键'B'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_B = 2302--><!--Device-ARKUI_KEYCODE_BUTTON_B = 2302-End--> |
| ARKUI_KEYCODE_BUTTON_X = 2304 | 游戏手柄按键'X'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_X = 2304--><!--Device-ARKUI_KEYCODE_BUTTON_X = 2304-End--> |
| ARKUI_KEYCODE_BUTTON_Y = 2305 | 游戏手柄按键'Y'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_Y = 2305--><!--Device-ARKUI_KEYCODE_BUTTON_Y = 2305-End--> |
| ARKUI_KEYCODE_BUTTON_L1 = 2307 | 游戏手柄按键'L1'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_L1 = 2307--><!--Device-ARKUI_KEYCODE_BUTTON_L1 = 2307-End--> |
| ARKUI_KEYCODE_BUTTON_R1 = 2308 | 游戏手柄按键'R1'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_R1 = 2308--><!--Device-ARKUI_KEYCODE_BUTTON_R1 = 2308-End--> |
| ARKUI_KEYCODE_BUTTON_L2 = 2309 | 游戏手柄按键'L2'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_L2 = 2309--><!--Device-ARKUI_KEYCODE_BUTTON_L2 = 2309-End--> |
| ARKUI_KEYCODE_BUTTON_R2 = 2310 | 游戏手柄按键'R2'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_R2 = 2310--><!--Device-ARKUI_KEYCODE_BUTTON_R2 = 2310-End--> |
| ARKUI_KEYCODE_BUTTON_SELECT = 2311 | 游戏手柄按键'Select'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_SELECT = 2311--><!--Device-ARKUI_KEYCODE_BUTTON_SELECT = 2311-End--> |
| ARKUI_KEYCODE_BUTTON_START = 2312 | 游戏手柄按键'Start'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_START = 2312--><!--Device-ARKUI_KEYCODE_BUTTON_START = 2312-End--> |
| ARKUI_KEYCODE_BUTTON_MODE = 2313 | 游戏手柄按键'Mode'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_MODE = 2313--><!--Device-ARKUI_KEYCODE_BUTTON_MODE = 2313-End--> |
| ARKUI_KEYCODE_BUTTON_THUMBL = 2314 | 游戏手柄按键'THUMBL'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_THUMBL = 2314--><!--Device-ARKUI_KEYCODE_BUTTON_THUMBL = 2314-End--> |
| ARKUI_KEYCODE_BUTTON_THUMBR = 2315 | 游戏手柄按键'THUMBR'。<br>**起始版本：** 15<br><!--Device-ARKUI_KEYCODE_BUTTON_THUMBR = 2315--><!--Device-ARKUI_KEYCODE_BUTTON_THUMBR = 2315-End--> |

### ArkUI_KeyEventType

```c
enum ArkUI_KeyEventType
```

**描述：**

按键的类型。

<!--Device-enum ArkUI_KeyEventType--><!--Device-enum ArkUI_KeyEventType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEY_EVENT_UNKNOWN = -1 | 未知类型。<br><!--Device-ARKUI_KEY_EVENT_UNKNOWN = -1--><!--Device-ARKUI_KEY_EVENT_UNKNOWN = -1-End--> |
| ARKUI_KEY_EVENT_DOWN = 0 | 按键按下。<br><!--Device-ARKUI_KEY_EVENT_DOWN = 0--><!--Device-ARKUI_KEY_EVENT_DOWN = 0-End--> |
| ARKUI_KEY_EVENT_UP = 1 | 按键松开。<br><!--Device-ARKUI_KEY_EVENT_UP = 1--><!--Device-ARKUI_KEY_EVENT_UP = 1-End--> |
| ARKUI_KEY_EVENT_LONG_PRESS = 2 | 按键长按。<br><!--Device-ARKUI_KEY_EVENT_LONG_PRESS = 2--><!--Device-ARKUI_KEY_EVENT_LONG_PRESS = 2-End--> |
| ARKUI_KEY_EVENT_CLICK = 3 | 按键点击。<br><!--Device-ARKUI_KEY_EVENT_CLICK = 3--><!--Device-ARKUI_KEY_EVENT_CLICK = 3-End--> |

### ArkUI_KeySourceType

```c
enum ArkUI_KeySourceType
```

**描述：**

触发当前按键的输入设备类型。

<!--Device-enum ArkUI_KeySourceType--><!--Device-enum ArkUI_KeySourceType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEY_SOURCE_UNKNOWN = 0 | 未知类型。<br><!--Device-ARKUI_KEY_SOURCE_UNKNOWN = 0--><!--Device-ARKUI_KEY_SOURCE_UNKNOWN = 0-End--> |
| ARKUI_KEY_SOURCE_TYPE_MOUSE = 1 | 鼠标。<br><!--Device-ARKUI_KEY_SOURCE_TYPE_MOUSE = 1--><!--Device-ARKUI_KEY_SOURCE_TYPE_MOUSE = 1-End--> |
| ARKUI_KEY_SOURCE_TYPE_KEYBOARD = 4 | 键盘。<br><!--Device-ARKUI_KEY_SOURCE_TYPE_KEYBOARD = 4--><!--Device-ARKUI_KEY_SOURCE_TYPE_KEYBOARD = 4-End--> |
| ARKUI_KEY_SOURCE_TYPE_JOYSTICK = 5 | 游戏手柄。<br>**起始版本：** 15<br><!--Device-ARKUI_KEY_SOURCE_TYPE_JOYSTICK = 5--><!--Device-ARKUI_KEY_SOURCE_TYPE_JOYSTICK = 5-End--> |

### ArkUI_KeyIntension

```c
enum ArkUI_KeyIntension
```

**描述：**

按键对应的意图。

<!--Device-enum ArkUI_KeyIntension--><!--Device-enum ArkUI_KeyIntension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEY_INTENSION_UNKNOWN = -1 | 未知意图。<br><!--Device-ARKUI_KEY_INTENSION_UNKNOWN = -1--><!--Device-ARKUI_KEY_INTENSION_UNKNOWN = -1-End--> |
| ARKUI_KEY_INTENSION_UP = 1 | 向上。<br><!--Device-ARKUI_KEY_INTENSION_UP = 1--><!--Device-ARKUI_KEY_INTENSION_UP = 1-End--> |
| ARKUI_KEY_INTENSION_DOWN = 2 | 向下。<br><!--Device-ARKUI_KEY_INTENSION_DOWN = 2--><!--Device-ARKUI_KEY_INTENSION_DOWN = 2-End--> |
| ARKUI_KEY_INTENSION_LEFT = 3 | 向左。<br><!--Device-ARKUI_KEY_INTENSION_LEFT = 3--><!--Device-ARKUI_KEY_INTENSION_LEFT = 3-End--> |
| ARKUI_KEY_INTENSION_RIGHT = 4 | 向右。<br><!--Device-ARKUI_KEY_INTENSION_RIGHT = 4--><!--Device-ARKUI_KEY_INTENSION_RIGHT = 4-End--> |
| ARKUI_KEY_INTENSION_SELECT = 5 | 选中。<br><!--Device-ARKUI_KEY_INTENSION_SELECT = 5--><!--Device-ARKUI_KEY_INTENSION_SELECT = 5-End--> |
| ARKUI_KEY_INTENSION_ESCAPE = 6 | 返回。<br><!--Device-ARKUI_KEY_INTENSION_ESCAPE = 6--><!--Device-ARKUI_KEY_INTENSION_ESCAPE = 6-End--> |
| ARKUI_KEY_INTENSION_BACK = 7 | 后退。<br><!--Device-ARKUI_KEY_INTENSION_BACK = 7--><!--Device-ARKUI_KEY_INTENSION_BACK = 7-End--> |
| ARKUI_KEY_INTENSION_FORWARD = 8 | 前进。<br><!--Device-ARKUI_KEY_INTENSION_FORWARD = 8--><!--Device-ARKUI_KEY_INTENSION_FORWARD = 8-End--> |
| ARKUI_KEY_INTENSION_MENU = 9 | 菜单。<br><!--Device-ARKUI_KEY_INTENSION_MENU = 9--><!--Device-ARKUI_KEY_INTENSION_MENU = 9-End--> |
| ARKUI_KEY_INTENSION_HOME = 10 | 主页。<br><!--Device-ARKUI_KEY_INTENSION_HOME = 10--><!--Device-ARKUI_KEY_INTENSION_HOME = 10-End--> |
| ARKUI_KEY_INTENSION_PAGE_UP = 11 | 上一页。<br><!--Device-ARKUI_KEY_INTENSION_PAGE_UP = 11--><!--Device-ARKUI_KEY_INTENSION_PAGE_UP = 11-End--> |
| ARKUI_KEY_INTENSION_PAGE_DOWN = 12 | 下一页。<br><!--Device-ARKUI_KEY_INTENSION_PAGE_DOWN = 12--><!--Device-ARKUI_KEY_INTENSION_PAGE_DOWN = 12-End--> |
| ARKUI_KEY_INTENSION_ZOOM_OUT = 13 | 缩小。<br><!--Device-ARKUI_KEY_INTENSION_ZOOM_OUT = 13--><!--Device-ARKUI_KEY_INTENSION_ZOOM_OUT = 13-End--> |
| ARKUI_KEY_INTENSION_ZOOM_IN = 14 | 放大。<br><!--Device-ARKUI_KEY_INTENSION_ZOOM_IN = 14--><!--Device-ARKUI_KEY_INTENSION_ZOOM_IN = 14-End--> |
| ARKUI_KEY_INTENTION_MEDIA_PLAY_PAUSE = 100 | 播放/暂停。<br><!--Device-ARKUI_KEY_INTENTION_MEDIA_PLAY_PAUSE = 100--><!--Device-ARKUI_KEY_INTENTION_MEDIA_PLAY_PAUSE = 100-End--> |
| ARKUI_KEY_INTENTION_MEDIA_FAST_FORWARD = 101 | 快进。<br><!--Device-ARKUI_KEY_INTENTION_MEDIA_FAST_FORWARD = 101--><!--Device-ARKUI_KEY_INTENTION_MEDIA_FAST_FORWARD = 101-End--> |
| ARKUI_KEY_INTENTION_MEDIA_FAST_PLAYBACK = 103 | 快速播放。<br><!--Device-ARKUI_KEY_INTENTION_MEDIA_FAST_PLAYBACK = 103--><!--Device-ARKUI_KEY_INTENTION_MEDIA_FAST_PLAYBACK = 103-End--> |
| ARKUI_KEY_INTENTION_MEDIA_NEXT = 104 | 下一首。<br><!--Device-ARKUI_KEY_INTENTION_MEDIA_NEXT = 104--><!--Device-ARKUI_KEY_INTENTION_MEDIA_NEXT = 104-End--> |
| ARKUI_KEY_INTENTION_MEDIA_PREVIOUS = 105 | 上一首。<br><!--Device-ARKUI_KEY_INTENTION_MEDIA_PREVIOUS = 105--><!--Device-ARKUI_KEY_INTENTION_MEDIA_PREVIOUS = 105-End--> |
| ARKUI_KEY_INTENTION_MEDIA_MUTE = 106 | 静音。<br><!--Device-ARKUI_KEY_INTENTION_MEDIA_MUTE = 106--><!--Device-ARKUI_KEY_INTENTION_MEDIA_MUTE = 106-End--> |
| ARKUI_KEY_INTENTION_VOLUME_UP = 107 | 音量增加。<br><!--Device-ARKUI_KEY_INTENTION_VOLUME_UP = 107--><!--Device-ARKUI_KEY_INTENTION_VOLUME_UP = 107-End--> |
| ARKUI_KEY_INTENTION_VOLUME_DOWN = 108 | 音量降低。<br><!--Device-ARKUI_KEY_INTENTION_VOLUME_DOWN = 108--><!--Device-ARKUI_KEY_INTENTION_VOLUME_DOWN = 108-End--> |
| ARKUI_KEY_INTENTION_CALL = 200 | 接听电话。<br><!--Device-ARKUI_KEY_INTENTION_CALL = 200--><!--Device-ARKUI_KEY_INTENTION_CALL = 200-End--> |
| ARKUI_KEY_INTENTION_CAMERA = 300 | 拍照。<br><!--Device-ARKUI_KEY_INTENTION_CAMERA = 300--><!--Device-ARKUI_KEY_INTENTION_CAMERA = 300-End--> |

### OH_ArkUI_KeyboardShortcutModifierKey

```c
enum OH_ArkUI_KeyboardShortcutModifierKey
```

**描述：**

枚举键盘快捷键支持的修饰键。<br> 枚举值为位标志，可以使用按位或运算符进行组合。

<!--Device-enum OH_ArkUI_KeyboardShortcutModifierKey--><!--Device-enum OH_ArkUI_KeyboardShortcutModifierKey-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_NONE = 0 | 不使用修饰键。该值仅可与功能键一起使用。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_NONE = 0--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_NONE = 0-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_CTRL = 1 | Ctrl键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_CTRL = 1--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_CTRL = 1-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_SHIFT = 2 | Shift键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_SHIFT = 2--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_SHIFT = 2-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_ALT = 4 | Alt键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_ALT = 4--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_ALT = 4-End--> |

### OH_ArkUI_KeyboardShortcutFunctionKey

```c
enum OH_ArkUI_KeyboardShortcutFunctionKey
```

**描述：**

枚举键盘快捷键支持的功能键。

<!--Device-enum OH_ArkUI_KeyboardShortcutFunctionKey--><!--Device-enum OH_ArkUI_KeyboardShortcutFunctionKey-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_ESC = 0 | Esc键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_ESC = 0--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_ESC = 0-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F1 = 1 | F1键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F1 = 1--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F1 = 1-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F2 = 2 | F2键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F2 = 2--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F2 = 2-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F3 = 3 | F3键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F3 = 3--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F3 = 3-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F4 = 4 | F4键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F4 = 4--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F4 = 4-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F5 = 5 | F5键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F5 = 5--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F5 = 5-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F6 = 6 | F6键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F6 = 6--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F6 = 6-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F7 = 7 | F7键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F7 = 7--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F7 = 7-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F8 = 8 | F8键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F8 = 8--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F8 = 8-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F9 = 9 | F9键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F9 = 9--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F9 = 9-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F10 = 10 | F10键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F10 = 10--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F10 = 10-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F11 = 11 | F11键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F11 = 11--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F11 = 11-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F12 = 12 | F12键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F12 = 12--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_F12 = 12-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_TAB = 13 | Tab键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_TAB = 13--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_TAB = 13-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_UP = 14 | 向上方向键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_UP = 14--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_UP = 14-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_DOWN = 15 | 向下方向键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_DOWN = 15--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_DOWN = 15-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_LEFT = 16 | 向左方向键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_LEFT = 16--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_LEFT = 16-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_RIGHT = 17 | 向右方向键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_RIGHT = 17--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DPAD_RIGHT = 17-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_CAPS_LOCK = 18 | CapsLock键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_CAPS_LOCK = 18--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_CAPS_LOCK = 18-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_SCROLL_LOCK = 19 | ScrollLock键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_SCROLL_LOCK = 19--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_SCROLL_LOCK = 19-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_PAUSE_BREAK = 20 | Pause/Break键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_PAUSE_BREAK = 20--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_PAUSE_BREAK = 20-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_NUM_LOCK = 21 | NumLock键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_NUM_LOCK = 21--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_NUM_LOCK = 21-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_INSERT = 22 | Insert键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_INSERT = 22--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_INSERT = 22-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DELETE = 23 | Delete键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DELETE = 23--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_DELETE = 23-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_HOME = 24 | Home键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_HOME = 24--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_HOME = 24-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_END = 25 | End键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_END = 25--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_END = 25-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_PAGE_UP = 26 | Page Up键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_PAGE_UP = 26--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_PAGE_UP = 26-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_PAGE_DOWN = 27 | Page Down键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_PAGE_DOWN = 27--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_PAGE_DOWN = 27-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_ENTER = 28 | Enter键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_ENTER = 28--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_ENTER = 28-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_BACKSPACE = 29 | Backspace键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_BACKSPACE = 29--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_BACKSPACE = 29-End--> |

### OH_ArkUI_KeyboardShortcutKeyType

```c
enum OH_ArkUI_KeyboardShortcutKeyType
```

**描述：**

枚举键盘快捷键支持的按键类型。

<!--Device-enum OH_ArkUI_KeyboardShortcutKeyType--><!--Device-enum OH_ArkUI_KeyboardShortcutKeyType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_CHARACTER = 0 | 字符键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_CHARACTER = 0--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_CHARACTER = 0-End--> |
| OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_FUNCTION_KEY = 1 | 功能键。<br>**起始版本：** 26.1.0<br><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_FUNCTION_KEY = 1--><!--Device-OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_FUNCTION_KEY = 1-End--> |


## 函数说明

### OH_ArkUI_KeyEvent_Create()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_Create(ArkUI_UIInputEvent** event)
```

**描述：**

创建可通过 [OH_ArkUI_KeyEvent_Dispatch](capi-native-key-event-h.md#oh_arkui_keyevent_dispatch) 分发的按键事件。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_Create(ArkUI_UIInputEvent** event)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_Create(ArkUI_UIInputEvent** event)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**资源释放：** [OH_ArkUI_KeyEvent_Destroy](#oh_arkui_keyevent_destroy)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)** event | [out] 二级指针，指向创建的 **ArkUI_UIInputEvent** 对象，不能为空。成功时创建的事件写入 **event**，事件归调用方所有，必须调用[OH_ArkUI_KeyEvent_Destroy](capi-native-key-event-h.md#oh_arkui_keyevent_destroy)释放。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空。</li> </ul> |

### OH_ArkUI_KeyEvent_Destroy()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_Destroy(ArkUI_UIInputEvent** event)
```

**描述：**

销毁通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件，并将事件指针置空。<br> 当 **event** 不为空且 **event** 指向的事件指针为空时，函数执行成功。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_Destroy(ArkUI_UIInputEvent** event)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_Destroy(ArkUI_UIInputEvent** event)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)** event | [in] 二级指针，指向待销毁的 **ArkUI_UIInputEvent** 对象，不能为空。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或者输入事件不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetType()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetType(ArkUI_UIInputEvent* event, ArkUI_KeyEventType type)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件类型。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetType(ArkUI_UIInputEvent* event, ArkUI_KeyEventType type)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetType(ArkUI_UIInputEvent* event, ArkUI_KeyEventType type)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| [ArkUI_KeyEventType](capi-native-key-event-h.md#arkui_keyeventtype) type | [in] 按键事件类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeyCode()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyCode(ArkUI_UIInputEvent* event, int32_t keyCode)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件键码。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyCode(ArkUI_UIInputEvent* event, int32_t keyCode)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyCode(ArkUI_UIInputEvent* event, int32_t keyCode)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| int32_t keyCode | [in] 按键键码，取值由 [ArkUI_KeyCode](capi-native-key-event-h.md#arkui_keycode) 定义。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeyText()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyText(ArkUI_UIInputEvent* event, const char* keyText)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件键值。<br> 本函数会复制 **keyText**。函数返回后，调用方可以释放或复用原字符串。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyText(ArkUI_UIInputEvent* event, const char* keyText)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyText(ArkUI_UIInputEvent* event, const char* keyText)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| const char* keyText | [in] 以空字符结尾的按键键值，UTF-8编码，不能为空。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeySource()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeySource(ArkUI_UIInputEvent* event, ArkUI_KeySourceType keySource)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件输入设备类型。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeySource(ArkUI_UIInputEvent* event, ArkUI_KeySourceType keySource)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeySource(ArkUI_UIInputEvent* event, ArkUI_KeySourceType keySource)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| [ArkUI_KeySourceType](capi-native-key-event-h.md#arkui_keysourcetype) keySource | [in] 输入设备类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetDeviceId()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetDeviceId(ArkUI_UIInputEvent* event, int32_t deviceId)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件设备ID。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetDeviceId(ArkUI_UIInputEvent* event, int32_t deviceId)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetDeviceId(ArkUI_UIInputEvent* event, int32_t deviceId)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| int32_t deviceId | [in] 设备ID，由系统分配的输入设备标识。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetUnicode()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetUnicode(ArkUI_UIInputEvent* event, uint32_t unicode)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件Unicode码值。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetUnicode(ArkUI_UIInputEvent* event, uint32_t unicode)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetUnicode(ArkUI_UIInputEvent* event, uint32_t unicode)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| uint32_t unicode | [in] Unicode码值，必须为有效的Unicode码位。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetEventTime()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetEventTime(ArkUI_UIInputEvent* event, int64_t timestamp)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件发生时间。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetEventTime(ArkUI_UIInputEvent* event, int64_t timestamp)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetEventTime(ArkUI_UIInputEvent* event, int64_t timestamp)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| int64_t timestamp | [in] 事件发生时间，单位为ns，时间基准与[OH_ArkUI_UIInputEvent_GetEventTime](capi-ui-input-event-h.md#oh_arkui_uiinputevent_geteventtime)一致。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetPressedKeys()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetPressedKeys(ArkUI_UIInputEvent* event, const int32_t* pressedKeyCodes, int32_t length)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件中所有已按下的按键。<br> 本函数会复制 **pressedKeyCodes**。函数返回后，调用方可以释放或复用原数组。 将 **pressedKeyCodes** 传入空指针、**length** 传入 **0** 可以清空已按下的按键。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetPressedKeys(ArkUI_UIInputEvent* event, const int32_t* pressedKeyCodes, int32_t length)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetPressedKeys(ArkUI_UIInputEvent* event, const int32_t* pressedKeyCodes, int32_t length)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| const int32_t* pressedKeyCodes | [in] 所有已按下按键的键码数组，仅当 **length** 为 **0** 时可以为 <b>nullptr</b>。 每个元素的取值由 [ArkUI_KeyCode](capi-native-key-event-h.md#arkui_keycode) 定义。 |
| int32_t length | [in] **pressedKeyCodes** 中的元素个数，必须大于等于 **0**。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeyIntentionCode()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyIntentionCode(ArkUI_UIInputEvent* event, OH_ArkUI_KeyIntention intentionCode)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件意图码。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyIntentionCode(ArkUI_UIInputEvent* event, OH_ArkUI_KeyIntention intentionCode)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyIntentionCode(ArkUI_UIInputEvent* event, OH_ArkUI_KeyIntention intentionCode)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| OH_ArkUI_KeyIntention intentionCode | [in] 按键事件关联的意图码。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetNumLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetNumLockOn(ArkUI_UIInputEvent* event, bool isNumLockOn)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件NumLock状态。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetNumLockOn(ArkUI_UIInputEvent* event, bool isNumLockOn)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetNumLockOn(ArkUI_UIInputEvent* event, bool isNumLockOn)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| bool isNumLockOn | [in] NumLock是否激活。true表示处于激活状态，false表示处于未激活状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetCapsLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetCapsLockOn(ArkUI_UIInputEvent* event, bool isCapsLockOn)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件CapsLock状态。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetCapsLockOn(ArkUI_UIInputEvent* event, bool isCapsLockOn)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetCapsLockOn(ArkUI_UIInputEvent* event, bool isCapsLockOn)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| bool isCapsLockOn | [in] CapsLock是否激活。true表示处于激活状态，false表示处于未激活状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetScrollLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetScrollLockOn(ArkUI_UIInputEvent* event, bool isScrollLockOn)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件ScrollLock状态。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetScrollLockOn(ArkUI_UIInputEvent* event, bool isScrollLockOn)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetScrollLockOn(ArkUI_UIInputEvent* event, bool isScrollLockOn)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] 目标 **ArkUI_UIInputEvent** 对象的指针，不能为空，且必须是 通过[OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。 |
| bool isScrollLockOn | [in] ScrollLock是否激活。true表示处于激活状态，false表示处于未激活状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。</li> <li>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_GetType()

```c
ArkUI_KeyEventType OH_ArkUI_KeyEvent_GetType(const ArkUI_UIInputEvent* event)
```

**描述：**

获取按键的类型。

<!--Device-ArkUI_KeyEventType OH_ArkUI_KeyEvent_GetType(const ArkUI_UIInputEvent* event)--><!--Device-ArkUI_KeyEventType OH_ArkUI_KeyEvent_GetType(const ArkUI_UIInputEvent* event)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_KeyEventType](capi-native-key-event-h.md#arkui_keyeventtype) | ArkUI_KeyEventType 按键的类型。 |

### OH_ArkUI_KeyEvent_GetKeyCode()

```c
int32_t OH_ArkUI_KeyEvent_GetKeyCode(const ArkUI_UIInputEvent* event)
```

**描述：**

获取按键的键码。

<!--Device-int32_t OH_ArkUI_KeyEvent_GetKeyCode(const ArkUI_UIInputEvent* event)--><!--Device-int32_t OH_ArkUI_KeyEvent_GetKeyCode(const ArkUI_UIInputEvent* event)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 按键的键码。 |

### OH_ArkUI_KeyEvent_GetKeyText()

```c
const char *OH_ArkUI_KeyEvent_GetKeyText(const ArkUI_UIInputEvent* event)
```

**描述：**

获取按键的键值。

<!--Device-const char *OH_ArkUI_KeyEvent_GetKeyText(const ArkUI_UIInputEvent* event)--><!--Device-const char *OH_ArkUI_KeyEvent_GetKeyText(const ArkUI_UIInputEvent* event)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| const char * | 按键的键值。 |

### OH_ArkUI_KeyEvent_GetKeySource()

```c
ArkUI_KeySourceType OH_ArkUI_KeyEvent_GetKeySource(const ArkUI_UIInputEvent* event)
```

**描述：**

获取当前按键的输入设备类型。

<!--Device-ArkUI_KeySourceType OH_ArkUI_KeyEvent_GetKeySource(const ArkUI_UIInputEvent* event)--><!--Device-ArkUI_KeySourceType OH_ArkUI_KeyEvent_GetKeySource(const ArkUI_UIInputEvent* event)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_KeySourceType](capi-native-key-event-h.md#arkui_keysourcetype) | ArkUI_KeySourceType 当前按键的输入设备类型。 |

### OH_ArkUI_KeyEvent_StopPropagation()

```c
void OH_ArkUI_KeyEvent_StopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)
```

**描述：**

阻塞事件冒泡传递。

<!--Device-void OH_ArkUI_KeyEvent_StopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)--><!--Device-void OH_ArkUI_KeyEvent_StopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |
| bool stopPropagation | 表示是否阻止事件冒泡。true表示阻止事件冒泡，false表示不阻止事件冒泡。 |

### OH_ArkUI_KeyEvent_GetKeyIntensionCode()

```c
ArkUI_KeyIntension OH_ArkUI_KeyEvent_GetKeyIntensionCode(const ArkUI_UIInputEvent* event)
```

**描述：**

获取按键对应的意图。

<!--Device-ArkUI_KeyIntension OH_ArkUI_KeyEvent_GetKeyIntensionCode(const ArkUI_UIInputEvent* event)--><!--Device-ArkUI_KeyIntension OH_ArkUI_KeyEvent_GetKeyIntensionCode(const ArkUI_UIInputEvent* event)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_KeyIntension](capi-native-key-event-h.md#arkui_keyintension) | ArkUI_KeyIntension 按键对应的意图。 |

### OH_ArkUI_KeyEvent_GetUnicode()

```c
uint32_t OH_ArkUI_KeyEvent_GetUnicode(const ArkUI_UIInputEvent* event)
```

**描述：**

获取按键的Unicode码值。支持范围为非空格的基本拉丁字符：0x0021-0x007E，不支持字符为0。组合键场景下，返回当前keyEvent对应按键的Unicode码值。

<!--Device-uint32_t OH_ArkUI_KeyEvent_GetUnicode(const ArkUI_UIInputEvent* event)--><!--Device-uint32_t OH_ArkUI_KeyEvent_GetUnicode(const ArkUI_UIInputEvent* event)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Unicode码值。 |

### OH_ArkUI_KeyEvent_SetConsumed()

```c
void OH_ArkUI_KeyEvent_SetConsumed(const ArkUI_UIInputEvent* event, bool isConsumed)
```

**描述：**

在按键事件回调中，设置事件是否被该回调消费。

<!--Device-void OH_ArkUI_KeyEvent_SetConsumed(const ArkUI_UIInputEvent* event, bool isConsumed)--><!--Device-void OH_ArkUI_KeyEvent_SetConsumed(const ArkUI_UIInputEvent* event, bool isConsumed)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |
| bool isConsumed | 事件是否被该回调消费。true表示事件被消费，false表示事件未被消费。 |

### OH_ArkUI_KeyEvent_Dispatch()

```c
void OH_ArkUI_KeyEvent_Dispatch(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)
```

**描述：**

将按键事件分发到特定组件节点。

<!--Device-void OH_ArkUI_KeyEvent_Dispatch(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)--><!--Device-void OH_ArkUI_KeyEvent_Dispatch(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | 指定的节点。 |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |

### OH_ArkUI_KeyEvent_IsNumLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsNumLockOn(const ArkUI_UIInputEvent* event, bool* state)
```

**描述：**

获取按键事件发生时NumLock的状态。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsNumLockOn(const ArkUI_UIInputEvent* event, bool* state)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsNumLockOn(const ArkUI_UIInputEvent* event, bool* state)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |
| bool* state | 输出参数，返回NumLock的状态。true表示处于激活状态，false表示处于未激活状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<br>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。<br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_KeyEvent_IsCapsLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsCapsLockOn(const ArkUI_UIInputEvent* event, bool* state)
```

**描述：**

获取按键事件发生时CapsLock的状态。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsCapsLockOn(const ArkUI_UIInputEvent* event, bool* state)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsCapsLockOn(const ArkUI_UIInputEvent* event, bool* state)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |
| bool* state | 输出参数，返回CapsLock的状态。true表示处于激活状态，false表示处于未激活状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<br>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。<br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_KeyEvent_IsScrollLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsScrollLockOn(const ArkUI_UIInputEvent* event, bool* state)
```

**描述：**

获取按键事件发生时ScrollLock的状态。

<!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsScrollLockOn(const ArkUI_UIInputEvent* event, bool* state)--><!--Device-ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsScrollLockOn(const ArkUI_UIInputEvent* event, bool* state)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | ArkUI_UIInputEvent事件指针。 |
| bool* state | 输出参数，返回ScrollLock的状态。true表示处于激活状态，false表示处于未激活状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<br>[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode) 成功。<br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_KeyboardShortcutKey_Create()

```c
OH_ArkUI_KeyboardShortcutKey* OH_ArkUI_KeyboardShortcutKey_Create(void)
```

**描述：**

创建键盘快捷键按键对象。可调用[OH_ArkUI_KeyboardShortcutKey_Destroy](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkey_destroy)销毁键盘快捷键按键对象。

<!--Device-OH_ArkUI_KeyboardShortcutKey* OH_ArkUI_KeyboardShortcutKey_Create(void)--><!--Device-OH_ArkUI_KeyboardShortcutKey* OH_ArkUI_KeyboardShortcutKey_Create(void)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**资源释放：** [OH_ArkUI_KeyboardShortcutKey_Destroy](#oh_arkui_keyboardshortcutkey_destroy)

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_KeyboardShortcutKey*](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md) | 键盘快捷键按键对象。<ul> <li>成功时返回归调用方所有的[OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)对象，调用方必须通过[OH_ArkUI_KeyboardShortcutKey_Destroy](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkey_destroy)释放。</li> <li>操作失败时（例如内存分配失败）返回<b>nullptr</b>。</li> </ul> |

### OH_ArkUI_KeyboardShortcutKey_Destroy()

```c
void OH_ArkUI_KeyboardShortcutKey_Destroy(OH_ArkUI_KeyboardShortcutKey** key)
```

**描述：**

销毁键盘快捷键按键对象。

<!--Device-void OH_ArkUI_KeyboardShortcutKey_Destroy(OH_ArkUI_KeyboardShortcutKey** key)--><!--Device-void OH_ArkUI_KeyboardShortcutKey_Destroy(OH_ArkUI_KeyboardShortcutKey** key)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)** key | [in] 键盘快捷键按键对象。 |

### OH_ArkUI_KeyboardShortcutKey_SetType()

```c
void OH_ArkUI_KeyboardShortcutKey_SetType(OH_ArkUI_KeyboardShortcutKey* key, OH_ArkUI_KeyboardShortcutKeyType type)
```

**描述：**

设置键盘快捷键按键的类型。

<!--Device-void OH_ArkUI_KeyboardShortcutKey_SetType(OH_ArkUI_KeyboardShortcutKey* key, OH_ArkUI_KeyboardShortcutKeyType type)--><!--Device-void OH_ArkUI_KeyboardShortcutKey_SetType(OH_ArkUI_KeyboardShortcutKey* key, OH_ArkUI_KeyboardShortcutKeyType type)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)* key | [in] 键盘快捷键按键对象指针。 |
| [OH_ArkUI_KeyboardShortcutKeyType](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkeytype) type | [in] 按键类型。 |

### OH_ArkUI_KeyboardShortcutKey_GetType()

```c
OH_ArkUI_KeyboardShortcutKeyType OH_ArkUI_KeyboardShortcutKey_GetType(const OH_ArkUI_KeyboardShortcutKey* key)
```

**描述：**

获取键盘快捷键按键的类型。

<!--Device-OH_ArkUI_KeyboardShortcutKeyType OH_ArkUI_KeyboardShortcutKey_GetType(const OH_ArkUI_KeyboardShortcutKey* key)--><!--Device-OH_ArkUI_KeyboardShortcutKeyType OH_ArkUI_KeyboardShortcutKey_GetType(const OH_ArkUI_KeyboardShortcutKey* key)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)* key | [in] 键盘快捷键按键对象指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_KeyboardShortcutKeyType](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkeytype) | 按键类型。<ul> <li>按键类型。</li> <li>如果<b>key</b>为<b>nullptr</b>，则返回[OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_CHARACTER](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkeytype)。</li> </ul> |

### OH_ArkUI_KeyboardShortcutKey_SetCharacter()

```c
void OH_ArkUI_KeyboardShortcutKey_SetCharacter(OH_ArkUI_KeyboardShortcutKey* key, char character)
```

**描述：**

设置字符键盘快捷键按键的字符。调用此函数前，按键类型必须已设置为 [OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_CHARACTER](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkeytype)。

<!--Device-void OH_ArkUI_KeyboardShortcutKey_SetCharacter(OH_ArkUI_KeyboardShortcutKey* key, char character)--><!--Device-void OH_ArkUI_KeyboardShortcutKey_SetCharacter(OH_ArkUI_KeyboardShortcutKey* key, char character)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)* key | [in] 键盘快捷键按键对象指针。 |
| char character | [in] 可通过键盘输入的单个字符。 |

### OH_ArkUI_KeyboardShortcutKey_GetCharacter()

```c
char OH_ArkUI_KeyboardShortcutKey_GetCharacter(const OH_ArkUI_KeyboardShortcutKey* key)
```

**描述：**

获取字符键盘快捷键按键的字符。

<!--Device-char OH_ArkUI_KeyboardShortcutKey_GetCharacter(const OH_ArkUI_KeyboardShortcutKey* key)--><!--Device-char OH_ArkUI_KeyboardShortcutKey_GetCharacter(const OH_ArkUI_KeyboardShortcutKey* key)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)* key | [in] 键盘快捷键按键对象指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| char | 字符。<ul> <li>字符。</li> <li>如果<b>key</b>为<b>nullptr</b>，则返回<b>'\\0'</b>。</li> </ul> |

### OH_ArkUI_KeyboardShortcutKey_SetFunctionKey()

```c
void OH_ArkUI_KeyboardShortcutKey_SetFunctionKey(OH_ArkUI_KeyboardShortcutKey* key, OH_ArkUI_KeyboardShortcutFunctionKey functionKey)
```

**描述：**

设置功能键盘快捷键按键的功能键。调用此函数前，按键类型必须已设置为 [OH_ARKUI_KEYBOARD_SHORTCUT_KEY_TYPE_FUNCTION_KEY](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkeytype)。

<!--Device-void OH_ArkUI_KeyboardShortcutKey_SetFunctionKey(OH_ArkUI_KeyboardShortcutKey* key, OH_ArkUI_KeyboardShortcutFunctionKey functionKey)--><!--Device-void OH_ArkUI_KeyboardShortcutKey_SetFunctionKey(OH_ArkUI_KeyboardShortcutKey* key, OH_ArkUI_KeyboardShortcutFunctionKey functionKey)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)* key | [in] 键盘快捷键按键对象指针。 |
| [OH_ArkUI_KeyboardShortcutFunctionKey](capi-native-key-event-h.md#oh_arkui_keyboardshortcutfunctionkey) functionKey | [in] 功能键。 |

### OH_ArkUI_KeyboardShortcutKey_GetFunctionKey()

```c
OH_ArkUI_KeyboardShortcutFunctionKey OH_ArkUI_KeyboardShortcutKey_GetFunctionKey(const OH_ArkUI_KeyboardShortcutKey* key)
```

**描述：**

获取功能键盘快捷键按键的功能键。

<!--Device-OH_ArkUI_KeyboardShortcutFunctionKey OH_ArkUI_KeyboardShortcutKey_GetFunctionKey(const OH_ArkUI_KeyboardShortcutKey* key)--><!--Device-OH_ArkUI_KeyboardShortcutFunctionKey OH_ArkUI_KeyboardShortcutKey_GetFunctionKey(const OH_ArkUI_KeyboardShortcutKey* key)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)* key | [in] 键盘快捷键按键对象指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_KeyboardShortcutFunctionKey](capi-native-key-event-h.md#oh_arkui_keyboardshortcutfunctionkey) | 功能键。<ul> <li>功能键。</li> <li>如果<b>key</b>为<b>nullptr</b>，则返回[OH_ARKUI_KEYBOARD_SHORTCUT_FUNCTION_KEY_ESC](capi-native-key-event-h.md#oh_arkui_keyboardshortcutfunctionkey)。</li> </ul> |

### OH_ArkUI_ApplicationShortcutCallback()

```c
typedef void (*OH_ArkUI_ApplicationShortcutCallback)(const OH_ArkUI_ApplicationShortcutCallbackInfo* info, void* userData)
```

**描述：**

定义应用级键盘快捷键触发时调用的回调函数。该回调在触发快捷键的UI实例对应的UI线程上执行。

<!--Device-typedef void (*OH_ArkUI_ApplicationShortcutCallback)(const OH_ArkUI_ApplicationShortcutCallbackInfo* info, void* userData)--><!--Device-typedef void (*OH_ArkUI_ApplicationShortcutCallback)(const OH_ArkUI_ApplicationShortcutCallbackInfo* info, void* userData)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_ApplicationShortcutCallbackInfo](capi-arkui-nativemodule-oh-arkui-applicationshortcutcallbackinfo.md)* info | [out] 指向触发快捷键的UI实例回调信息对象的指针，不能为空。使用 [OH_ArkUI_ApplicationShortcutCallbackInfo_GetUIContext](capi-native-key-event-h.md#oh_arkui_applicationshortcutcallbackinfo_getuicontext)获取对应的UI上下文。该对象仅在回调执行期间 有效，不得持有。 |
| void* userData | [out] 注册快捷键时传入的用户自定义数据。该值不会被复制，在快捷键注销前必须保持有效。 |

### OH_ArkUI_ApplicationShortcutCallbackInfo_GetUIContext()

```c
ArkUI_ContextHandle OH_ArkUI_ApplicationShortcutCallbackInfo_GetUIContext(const OH_ArkUI_ApplicationShortcutCallbackInfo* info)
```

**描述：**

获取触发应用级键盘快捷键的UI实例对应的UI上下文。

<!--Device-ArkUI_ContextHandle OH_ArkUI_ApplicationShortcutCallbackInfo_GetUIContext(const OH_ArkUI_ApplicationShortcutCallbackInfo* info)--><!--Device-ArkUI_ContextHandle OH_ArkUI_ApplicationShortcutCallbackInfo_GetUIContext(const OH_ArkUI_ApplicationShortcutCallbackInfo* info)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_ApplicationShortcutCallbackInfo](capi-arkui-nativemodule-oh-arkui-applicationshortcutcallbackinfo.md)* info | [in] 指向[OH_ArkUI_ApplicationShortcutCallback](capi-native-key-event-h.md#oh_arkui_applicationshortcutcallback)接收到的单个回调信息对象的指针， 不能为空。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ContextHandle | UI上下文。<ul> <li>触发快捷键的UI实例对应的UI上下文。</li> <li>如果<b>info</b>无效，则返回<b>nullptr</b>。</li> </ul> |

### OH_ArkUI_ApplicationShortcut_Register()

```c
ArkUI_ErrorCode OH_ArkUI_ApplicationShortcut_Register(const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys, void* userData, OH_ArkUI_ApplicationShortcutCallback callback, int32_t* registrationId)
```

**描述：**

注册应用级键盘快捷键。该快捷键在应用内全局生效。 如果存在匹配的组件级快捷键，则优先触发组件级快捷键。<br> 每次注册生成一个应用内唯一的正整数注册标识符，即使快捷键和回调相同，标识符也不同。 同一个快捷键的多次注册均被保留，仅最近一次未注销的注册生效。 注册标识符在应用运行期间不复用。

<!--Device-ArkUI_ErrorCode OH_ArkUI_ApplicationShortcut_Register(const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys, void* userData, OH_ArkUI_ApplicationShortcutCallback callback, int32_t* registrationId)--><!--Device-ArkUI_ErrorCode OH_ArkUI_ApplicationShortcut_Register(const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys, void* userData, OH_ArkUI_ApplicationShortcutCallback callback, int32_t* registrationId)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)* key | [in] 指向键盘快捷键按键对象的指针，不能为<b>nullptr</b>。该对象通过 [OH_ArkUI_KeyboardShortcutKey_Create](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkey_create)创建。字符键通过 [OH_ArkUI_KeyboardShortcutKey_SetCharacter](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkey_setcharacter)设置的字符必须为单个可通过键盘输入的字符。 |
| uint32_t modifierKeys | [in] 修饰键位掩码。使用[OH_ArkUI_KeyboardShortcutModifierKey](capi-native-key-event-h.md#oh_arkui_keyboardshortcutmodifierkey)中的值进行按位或组合。功能键可使用 [OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_NONE](capi-native-key-event-h.md#oh_arkui_keyboardshortcutmodifierkey)注册不带修饰键的快捷键，字符键至少需要指定一个修饰键。 仅接受[OH_ArkUI_KeyboardShortcutModifierKey](capi-native-key-event-h.md#oh_arkui_keyboardshortcutmodifierkey)中定义的位，设置其他位时返回 [ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode)。 |
| void* userData | [in] 传递给回调函数的用户自定义数据，可以为<b>nullptr</b>。该值不会被复制， 在快捷键注销前必须保持有效。 |
| [OH_ArkUI_ApplicationShortcutCallback](capi-native-key-event-h.md#oh_arkui_applicationshortcutcallback) callback | [in] 快捷键触发时调用的回调函数，不能为<b>nullptr</b>。 |
| int32_t* registrationId | [out] 用于接收本次快捷键绑定注册标识符的输出指针，不能为<b>nullptr</b>。 仅在注册成功时写入，注册失败时保持原值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 返回执行结果。<ul> <li>如果操作成功，则返回[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode)。</li> <li>如果参数无效，则返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode)。</li> </ul> |

### OH_ArkUI_ApplicationShortcut_Unregister()

```c
ArkUI_ErrorCode OH_ArkUI_ApplicationShortcut_Unregister(int32_t registrationId)
```

**描述：**

注销指定注册标识符对应的应用级键盘快捷键绑定。<br> 仅移除该标识符对应的绑定，其他绑定不受影响。如果移除的是当前生效的绑定， 则最近一次仍未注销的同快捷键绑定恢复生效。标识符不存在或已注销时，不执行任何操作，仍返回成功。

<!--Device-ArkUI_ErrorCode OH_ArkUI_ApplicationShortcut_Unregister(int32_t registrationId)--><!--Device-ArkUI_ErrorCode OH_ArkUI_ApplicationShortcut_Unregister(int32_t registrationId)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t registrationId | [in] 注册快捷键时获得的注册标识符。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 返回执行结果。<br>如果操作成功或注册标识符不存在，则返回[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode)。 |

### OH_ArkUI_KeyboardShortcutCallback()

```c
typedef void (*OH_ArkUI_KeyboardShortcutCallback)(void* userData)
```

**描述：**

定义组件级键盘快捷键触发时调用的回调函数。

<!--Device-typedef void (*OH_ArkUI_KeyboardShortcutCallback)(void* userData)--><!--Device-typedef void (*OH_ArkUI_KeyboardShortcutCallback)(void* userData)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void* userData | 注册快捷键时传入的用户自定义数据。 |

### OH_ArkUI_NodeKeyboardShortcut_Register()

```c
ArkUI_ErrorCode OH_ArkUI_NodeKeyboardShortcut_Register(ArkUI_NodeHandle node, const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys, void* userData, OH_ArkUI_KeyboardShortcutCallback callback)
```

**描述：**

为组件注册键盘快捷键。同一组件重复注册相同快捷键时，以最后一次注册为准。组件级快捷键的触发优先级 高于相同的应用级快捷键。

<!--Device-ArkUI_ErrorCode OH_ArkUI_NodeKeyboardShortcut_Register(ArkUI_NodeHandle node, const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys, void* userData, OH_ArkUI_KeyboardShortcutCallback callback)--><!--Device-ArkUI_ErrorCode OH_ArkUI_NodeKeyboardShortcut_Register(ArkUI_NodeHandle node, const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys, void* userData, OH_ArkUI_KeyboardShortcutCallback callback)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | [in] 目标组件节点。 |
| [const OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)* key | [in] 指向键盘快捷键按键对象的指针，不能为<b>nullptr</b>。该对象通过 [OH_ArkUI_KeyboardShortcutKey_Create](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkey_create)创建。字符键通过 [OH_ArkUI_KeyboardShortcutKey_SetCharacter](capi-native-key-event-h.md#oh_arkui_keyboardshortcutkey_setcharacter)设置的字符必须为单个可通过键盘输入的字符。 |
| uint32_t modifierKeys | [in] 修饰键位掩码。使用[OH_ArkUI_KeyboardShortcutModifierKey](capi-native-key-event-h.md#oh_arkui_keyboardshortcutmodifierkey)中的值进行按位或组合。功能键可使用 [OH_ARKUI_KEYBOARD_SHORTCUT_MODIFIER_NONE](capi-native-key-event-h.md#oh_arkui_keyboardshortcutmodifierkey)注册不带修饰键的快捷键，字符键至少需要指定一个修饰键。 仅接受[OH_ArkUI_KeyboardShortcutModifierKey](capi-native-key-event-h.md#oh_arkui_keyboardshortcutmodifierkey)中定义的位，设置其他位时返回 [ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode)。 |
| void* userData | [in] 传递给回调函数的用户自定义数据，可以为<b>nullptr</b>。该值不会被复制， 在快捷键注销前必须保持有效。 |
| [OH_ArkUI_KeyboardShortcutCallback](capi-native-key-event-h.md#oh_arkui_keyboardshortcutcallback) callback | [in] 快捷键触发时调用的回调函数。如果为<b>nullptr</b>，则触发组件的点击事件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 返回执行结果。<ul> <li>如果操作成功，则返回[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode)。</li> <li>如果参数无效，则返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode)。</li> </ul> |

### OH_ArkUI_NodeKeyboardShortcut_Unregister()

```c
ArkUI_ErrorCode OH_ArkUI_NodeKeyboardShortcut_Unregister(ArkUI_NodeHandle node, const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys)
```

**描述：**

注销组件的键盘快捷键。如果没有注册匹配的快捷键，该操作仍然成功。

<!--Device-ArkUI_ErrorCode OH_ArkUI_NodeKeyboardShortcut_Unregister(ArkUI_NodeHandle node, const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys)--><!--Device-ArkUI_ErrorCode OH_ArkUI_NodeKeyboardShortcut_Unregister(ArkUI_NodeHandle node, const OH_ArkUI_KeyboardShortcutKey* key, uint32_t modifierKeys)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_NodeHandle node | [in] 目标组件节点。 |
| [const OH_ArkUI_KeyboardShortcutKey](capi-arkui-nativemodule-oh-arkui-keyboardshortcutkey.md)* key | [in] 指向注册时所用键盘快捷键按键对象的指针，不能为<b>nullptr</b>。 |
| uint32_t modifierKeys | [in] 注册时使用的修饰键位掩码。仅接受[OH_ArkUI_KeyboardShortcutModifierKey](capi-native-key-event-h.md#oh_arkui_keyboardshortcutmodifierkey) 中定义的位，设置其他位时返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 返回执行结果。<ul> <li>如果操作成功，则返回[ARKUI_ERROR_CODE_NO_ERROR](capi-error-code-h.md#arkui_errorcode)。</li> <li>如果参数无效，则返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-error-code-h.md#arkui_errorcode)。</li> </ul> |


