# native_key_event.h

## 概述

提供NativeKeyEvent相关接口定义。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_KeyCode](#arkui_keycode) | ArkUI_KeyCode | 按键事件的键码。 |
| [ArkUI_KeyEventType](#arkui_keyeventtype) | ArkUI_KeyEventType | 按键的类型。 |
| [ArkUI_KeySourceType](#arkui_keysourcetype) | ArkUI_KeySourceType | 触发当前按键的输入设备类型。 |
| [ArkUI_KeyIntension](#arkui_keyintension) | ArkUI_KeyIntension | 按键对应的意图。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_Create(ArkUI_UIInputEvent** event)](#oh_arkui_keyevent_create) | 创建可通过 [OH_ArkUI_KeyEvent_Dispatch](capi-native-key-event-h.md#oh_arkui_keyevent_dispatch) 分发的按键事件。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_Destroy(ArkUI_UIInputEvent** event)](#oh_arkui_keyevent_destroy) | 销毁通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件，并将事件指针置空。<br> 当 **event** 不为空且 **event** 指向的事件指针为空时，函数执行成功。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetType(ArkUI_UIInputEvent* event, ArkUI_KeyEventType type)](#oh_arkui_keyevent_settype) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件类型。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyCode(ArkUI_UIInputEvent* event, int32_t keyCode)](#oh_arkui_keyevent_setkeycode) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件键码。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyText(ArkUI_UIInputEvent* event, const char* keyText)](#oh_arkui_keyevent_setkeytext) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件键值。<br> 本函数会复制 **keyText**。函数返回后，调用方可以释放或复用原字符串。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeySource(ArkUI_UIInputEvent* event, ArkUI_KeySourceType keySource)](#oh_arkui_keyevent_setkeysource) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件输入设备类型。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetDeviceId(ArkUI_UIInputEvent* event, int32_t deviceId)](#oh_arkui_keyevent_setdeviceid) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件设备ID。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetUnicode(ArkUI_UIInputEvent* event, uint32_t unicode)](#oh_arkui_keyevent_setunicode) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件Unicode码值。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetEventTime(ArkUI_UIInputEvent* event, int64_t timestamp)](#oh_arkui_keyevent_seteventtime) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件发生时间。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetPressedKeys(ArkUI_UIInputEvent* event, const int32_t* pressedKeyCodes, int32_t length)](#oh_arkui_keyevent_setpressedkeys) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件中所有已按下的按键。<br> 本函数会复制 **pressedKeyCodes**。函数返回后，调用方可以释放或复用原数组。 将 **pressedKeyCodes** 传入空指针、**length** 传入 **0** 可以清空已按下的按键。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyIntentionCode(ArkUI_UIInputEvent* event, OH_ArkUI_KeyIntention intentionCode)](#oh_arkui_keyevent_setkeyintentioncode) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件意图码。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetNumLockOn(ArkUI_UIInputEvent* event, bool isNumLockOn)](#oh_arkui_keyevent_setnumlockon) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件NumLock状态。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetCapsLockOn(ArkUI_UIInputEvent* event, bool isCapsLockOn)](#oh_arkui_keyevent_setcapslockon) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件CapsLock状态。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetScrollLockOn(ArkUI_UIInputEvent* event, bool isScrollLockOn)](#oh_arkui_keyevent_setscrolllockon) | 设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件ScrollLock状态。 |
| [ArkUI_KeyEventType OH_ArkUI_KeyEvent_GetType(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_gettype) | 获取按键的类型。 |
| [int32_t OH_ArkUI_KeyEvent_GetKeyCode(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeycode) | 获取按键的键码。 |
| [const char *OH_ArkUI_KeyEvent_GetKeyText(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeytext) | 获取按键的键值。 |
| [ArkUI_KeySourceType OH_ArkUI_KeyEvent_GetKeySource(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeysource) | 获取当前按键的输入设备类型。 |
| [void OH_ArkUI_KeyEvent_StopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)](#oh_arkui_keyevent_stoppropagation) | 阻塞事件冒泡传递。 |
| [ArkUI_KeyIntension OH_ArkUI_KeyEvent_GetKeyIntensionCode(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeyintensioncode) | 获取按键对应的意图。 |
| [uint32_t OH_ArkUI_KeyEvent_GetUnicode(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getunicode) | 获取按键的Unicode码值。支持范围为非空格的基本拉丁字符：0x0021-0x007E，不支持字符为0。组合键场景下，返回当前keyEvent对应按键的Unicode码值。 |
| [void OH_ArkUI_KeyEvent_SetConsumed(const ArkUI_UIInputEvent* event, bool isConsumed)](#oh_arkui_keyevent_setconsumed) | 在按键事件回调中，设置事件是否被该回调消费。 |
| [void OH_ArkUI_KeyEvent_Dispatch(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_dispatch) | 将按键事件分发到特定组件节点。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsNumLockOn(const ArkUI_UIInputEvent* event, bool* state)](#oh_arkui_keyevent_isnumlockon) | 获取按键事件发生时NumLock的状态。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsCapsLockOn(const ArkUI_UIInputEvent* event, bool* state)](#oh_arkui_keyevent_iscapslockon) | 获取按键事件发生时CapsLock的状态。 |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsScrollLockOn(const ArkUI_UIInputEvent* event, bool* state)](#oh_arkui_keyevent_isscrolllockon) | 获取按键事件发生时ScrollLock的状态。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| ArkUI_KeyIntension OH_ArkUI_KeyIntention | 按键事件意图类型的正确拼写别名。<br> 原类型名 [ArkUI_KeyIntension](capi-native-key-event-h.md#arkui_keyintension) 将保留以兼容已有接口。<br>**起始版本：** 26.1.0<br>**系统能力：** SystemCapability.ArkUI.ArkUI.Full |

## 枚举类型说明

### ArkUI_KeyCode

```c
enum ArkUI_KeyCode
```

**描述：**

按键事件的键码。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEYCODE_UNKNOWN = -1 | 未知按键。 |
| ARKUI_KEYCODE_FN = 0 | 功能（Fn）键。 |
| ARKUI_KEYCODE_VOLUME_UP = 16 | 音量增加键。 |
| ARKUI_KEYCODE_VOLUME_DOWN = 17 | 音量减小键。 |
| ARKUI_KEYCODE_POWER = 18 | 电源键。 |
| ARKUI_KEYCODE_CAMERA = 19 | 拍照键。 |
| ARKUI_KEYCODE_VOLUME_MUTE = 22 | 扬声器静音键。 |
| ARKUI_KEYCODE_MUTE = 23 | 话筒静音键。 |
| ARKUI_KEYCODE_BRIGHTNESS_UP = 40 | 亮度调节按键，调亮。 |
| ARKUI_KEYCODE_BRIGHTNESS_DOWN = 41 | 亮度调节按键，调暗。 |
| ARKUI_KEYCODE_0 = 2000 | 按键'0'。 |
| ARKUI_KEYCODE_1 = 2001 | 按键'1'。 |
| ARKUI_KEYCODE_2 = 2002 | 按键'2'。 |
| ARKUI_KEYCODE_3 = 2003 | 按键'3'。 |
| ARKUI_KEYCODE_4 = 2004 | 按键'4'。 |
| ARKUI_KEYCODE_5 = 2005 | 按键'5'。 |
| ARKUI_KEYCODE_6 = 2006 | 按键'6'。 |
| ARKUI_KEYCODE_7 = 2007 | 按键'7'。 |
| ARKUI_KEYCODE_8 = 2008 | 按键'8'。 |
| ARKUI_KEYCODE_9 = 2009 | 按键'9'。 |
| ARKUI_KEYCODE_STAR = 2010 | 按键'+'。 |
| ARKUI_KEYCODE_POUND = 2011 | 按键'#'。 |
| ARKUI_KEYCODE_DPAD_UP = 2012 | 导航键，向上。 |
| ARKUI_KEYCODE_DPAD_DOWN = 2013 | 导航键，向下。 |
| ARKUI_KEYCODE_DPAD_LEFT = 2014 | 导航键，向左。 |
| ARKUI_KEYCODE_DPAD_RIGHT = 2015 | 导航键，向右。 |
| ARKUI_KEYCODE_DPAD_CENTER = 2016 | 导航键，确定键。 |
| ARKUI_KEYCODE_A = 2017 | 按键'A'。 |
| ARKUI_KEYCODE_B = 2018 | 按键'B'。 |
| ARKUI_KEYCODE_C = 2019 | 按键'C'。 |
| ARKUI_KEYCODE_D = 2020 | 按键'D'。 |
| ARKUI_KEYCODE_E = 2021 | 按键'E'。 |
| ARKUI_KEYCODE_F = 2022 | 按键'F'。 |
| ARKUI_KEYCODE_G = 2023 | 按键'G'。 |
| ARKUI_KEYCODE_H = 2024 | 按键'H'。 |
| ARKUI_KEYCODE_I = 2025 | 按键'I'。 |
| ARKUI_KEYCODE_J = 2026 | 按键'J'。 |
| ARKUI_KEYCODE_K = 2027 | 按键'K'。 |
| ARKUI_KEYCODE_L = 2028 | 按键'L'。 |
| ARKUI_KEYCODE_M = 2029 | 按键'M'。 |
| ARKUI_KEYCODE_N = 2030 | 按键'N'。 |
| ARKUI_KEYCODE_O = 2031 | 按键'O'。 |
| ARKUI_KEYCODE_P = 2032 | 按键'P'。 |
| ARKUI_KEYCODE_Q = 2033 | 按键'Q'。 |
| ARKUI_KEYCODE_R = 2034 | 按键'R'。 |
| ARKUI_KEYCODE_S = 2035 | 按键'S'。 |
| ARKUI_KEYCODE_T = 2036 | 按键'T'。 |
| ARKUI_KEYCODE_U = 2037 | 按键'U'。 |
| ARKUI_KEYCODE_V = 2038 | 按键'V'。 |
| ARKUI_KEYCODE_W = 2039 | 按键'W'。 |
| ARKUI_KEYCODE_X = 2040 | 按键'X'。 |
| ARKUI_KEYCODE_Y = 2041 | 按键'Y'。 |
| ARKUI_KEYCODE_Z = 2042 | 按键'Z'。 |
| ARKUI_KEYCODE_COMMA = 2043 | 按键','。 |
| ARKUI_KEYCODE_PERIOD = 2044 | 按键'.'。 |
| ARKUI_KEYCODE_ALT_LEFT = 2045 | 左Alt键。 |
| ARKUI_KEYCODE_ALT_RIGHT = 2046 | 右Alt键。 |
| ARKUI_KEYCODE_SHIFT_LEFT = 2047 | 左Shift键。 |
| ARKUI_KEYCODE_SHIFT_RIGHT = 2048 | 右Shift键。 |
| ARKUI_KEYCODE_TAB = 2049 | Tab键。 |
| ARKUI_KEYCODE_SPACE = 2050 | 空格键。 |
| ARKUI_KEYCODE_SYM = 2051 | 符号修改器按键。 |
| ARKUI_KEYCODE_EXPLORER = 2052 | 浏览器功能键，此键用于启动浏览器应用程序。 |
| ARKUI_KEYCODE_ENVELOPE = 2053 | 电子邮件功能键，此键用于启动电子邮件应用程序。 |
| ARKUI_KEYCODE_ENTER = 2054 | 回车键。 |
| ARKUI_KEYCODE_DEL = 2055 | 退格键。 |
| ARKUI_KEYCODE_GRAVE = 2056 | 按键'`'。 |
| ARKUI_KEYCODE_MINUS = 2057 | 按键'-'。 |
| ARKUI_KEYCODE_EQUALS = 2058 | 按键'='。 |
| ARKUI_KEYCODE_LEFT_BRACKET = 2059 | 按键'['。 |
| ARKUI_KEYCODE_RIGHT_BRACKET = 2060 | 按键']'。 |
| ARKUI_KEYCODE_BACKSLASH = 2061 | 按键'\'。 |
| ARKUI_KEYCODE_SEMICOLON = 2062 | 按键';'。 |
| ARKUI_KEYCODE_APOSTROPHE = 2063 | 按键''' (单引号)。 |
| ARKUI_KEYCODE_SLASH = 2064 | 按键'/'。 |
| ARKUI_KEYCODE_AT = 2065 | 按键 '@'。 |
| ARKUI_KEYCODE_PLUS = 2066 | 按键'+'。 |
| ARKUI_KEYCODE_MENU = 2067 | 菜单键。 |
| ARKUI_KEYCODE_PAGE_UP = 2068 | 向上翻页键。 |
| ARKUI_KEYCODE_PAGE_DOWN = 2069 | 向下翻页键。 |
| ARKUI_KEYCODE_ESCAPE = 2070 | ESC键。 |
| ARKUI_KEYCODE_FORWARD_DEL = 2071 | 删除键。 |
| ARKUI_KEYCODE_CTRL_LEFT = 2072 | 左Ctrl键。 |
| ARKUI_KEYCODE_CTRL_RIGHT = 2073 | 右Ctrl键。 |
| ARKUI_KEYCODE_CAPS_LOCK = 2074 | 大写锁定键。 |
| ARKUI_KEYCODE_SCROLL_LOCK = 2075 | 滚动锁定键。 |
| ARKUI_KEYCODE_META_LEFT = 2076 | 左元修改器键。 |
| ARKUI_KEYCODE_META_RIGHT = 2077 | 右元修改器键。 |
| ARKUI_KEYCODE_FUNCTION = 2078 | 功能键。 |
| ARKUI_KEYCODE_SYSRQ = 2079 | 系统请求/打印屏幕键。 |
| ARKUI_KEYCODE_BREAK = 2080 | Break/Pause键。 |
| ARKUI_KEYCODE_MOVE_HOME = 2081 | 光标移动到开始键。 |
| ARKUI_KEYCODE_MOVE_END = 2082 | 光标移动到末尾键。 |
| ARKUI_KEYCODE_INSERT = 2083 | 插入键。 |
| ARKUI_KEYCODE_FORWARD = 2084 | 前进键。 |
| ARKUI_KEYCODE_MEDIA_PLAY = 2085 | 多媒体键，播放。 |
| ARKUI_KEYCODE_MEDIA_PAUSE = 2086 | 多媒体键，暂停。 |
| ARKUI_KEYCODE_MEDIA_CLOSE = 2087 | 多媒体键，关闭。 |
| ARKUI_KEYCODE_MEDIA_EJECT = 2088 | 多媒体键，弹出。 |
| ARKUI_KEYCODE_MEDIA_RECORD = 2089 | 多媒体键，录音。 |
| ARKUI_KEYCODE_F1 = 2090 | 按键'F1'。 |
| ARKUI_KEYCODE_F2 = 2091 | 按键'F2'。 |
| ARKUI_KEYCODE_F3 = 2092 | 按键'F3'。 |
| ARKUI_KEYCODE_F4 = 2093 | 按键'F4'。 |
| ARKUI_KEYCODE_F5 = 2094 | 按键'F5'。 |
| ARKUI_KEYCODE_F6 = 2095 | 按键'F6'。 |
| ARKUI_KEYCODE_F7 = 2096 | 按键'F7'。 |
| ARKUI_KEYCODE_F8 = 2097 | 按键'F8'。 |
| ARKUI_KEYCODE_F9 = 2098 | 按键'F9'。 |
| ARKUI_KEYCODE_F10 = 2099 | 按键'F10'。 |
| ARKUI_KEYCODE_F11 = 2100 | 按键'F11'。 |
| ARKUI_KEYCODE_F12 = 2101 | 按键'F12'。 |
| ARKUI_KEYCODE_NUM_LOCK = 2102 | 小键盘锁。 |
| ARKUI_KEYCODE_NUMPAD_0 = 2103 | 小键盘按键'0'。 |
| ARKUI_KEYCODE_NUMPAD_1 = 2104 | 小键盘按键'1'。 |
| ARKUI_KEYCODE_NUMPAD_2 = 2105 | 小键盘按键'2'。 |
| ARKUI_KEYCODE_NUMPAD_3 = 2106 | 小键盘按键'3'。 |
| ARKUI_KEYCODE_NUMPAD_4 = 2107 | 小键盘按键'4'。 |
| ARKUI_KEYCODE_NUMPAD_5 = 2108 | 小键盘按键'5'。 |
| ARKUI_KEYCODE_NUMPAD_6 = 2109 | 小键盘按键'6'。 |
| ARKUI_KEYCODE_NUMPAD_7 = 2110 | 小键盘按键'7'。 |
| ARKUI_KEYCODE_NUMPAD_8 = 2111 | 小键盘按键'8'。 |
| ARKUI_KEYCODE_NUMPAD_9 = 2112 | 小键盘按键'9'。 |
| ARKUI_KEYCODE_NUMPAD_DIVIDE = 2113 | 小键盘按键'/'。 |
| ARKUI_KEYCODE_NUMPAD_MULTIPLY = 2114 | 小键盘按键'*'。 |
| ARKUI_KEYCODE_NUMPAD_SUBTRACT = 2115 | 小键盘按键'-'。 |
| ARKUI_KEYCODE_NUMPAD_ADD = 2116 | 小键盘按键'+'。 |
| ARKUI_KEYCODE_NUMPAD_DOT = 2117 | 小键盘按键'.'。 |
| ARKUI_KEYCODE_NUMPAD_COMMA = 2118 | 小键盘按键','。 |
| ARKUI_KEYCODE_NUMPAD_ENTER = 2119 | 小键盘按键回车。 |
| ARKUI_KEYCODE_NUMPAD_EQUALS = 2120 | 小键盘按键'='。 |
| ARKUI_KEYCODE_NUMPAD_LEFT_PAREN = 2121 | 小键盘按键'('。 |
| ARKUI_KEYCODE_NUMPAD_RIGHT_PAREN = 2122 | 小键盘按键')'。 |
| ARKUI_KEYCODE_BUTTON_A = 2301 |  |
| ARKUI_KEYCODE_BUTTON_B = 2302 |  |
| ARKUI_KEYCODE_BUTTON_X = 2304 |  |
| ARKUI_KEYCODE_BUTTON_Y = 2305 |  |
| ARKUI_KEYCODE_BUTTON_L1 = 2307 |  |
| ARKUI_KEYCODE_BUTTON_R1 = 2308 |  |
| ARKUI_KEYCODE_BUTTON_L2 = 2309 |  |
| ARKUI_KEYCODE_BUTTON_R2 = 2310 |  |
| ARKUI_KEYCODE_BUTTON_SELECT = 2311 |  |
| ARKUI_KEYCODE_BUTTON_START = 2312 |  |
| ARKUI_KEYCODE_BUTTON_MODE = 2313 |  |
| ARKUI_KEYCODE_BUTTON_THUMBL = 2314 |  |
| ARKUI_KEYCODE_BUTTON_THUMBR = 2315 |  |

### ArkUI_KeyEventType

```c
enum ArkUI_KeyEventType
```

**描述：**

按键的类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEY_EVENT_UNKNOWN = -1 | 未知类型。 |
| ARKUI_KEY_EVENT_DOWN = 0 | 按键按下。 |
| ARKUI_KEY_EVENT_UP = 1 | 按键松开。 |
| ARKUI_KEY_EVENT_LONG_PRESS = 2 | 按键长按。 |
| ARKUI_KEY_EVENT_CLICK = 3 | 按键点击。 |

### ArkUI_KeySourceType

```c
enum ArkUI_KeySourceType
```

**描述：**

触发当前按键的输入设备类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEY_SOURCE_UNKNOWN = 0 | 未知类型。 |
| ARKUI_KEY_SOURCE_TYPE_MOUSE = 1 | 鼠标。 |
| ARKUI_KEY_SOURCE_TYPE_KEYBOARD = 4 | 键盘。 |
| ARKUI_KEY_SOURCE_TYPE_JOYSTICK = 5 | 游戏手柄。<br>**起始版本：** 15 |

### ArkUI_KeyIntension

```c
enum ArkUI_KeyIntension
```

**描述：**

按键对应的意图。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEY_INTENSION_UNKNOWN = -1 | 未知意图。 |
| ARKUI_KEY_INTENSION_UP = 1 | 向上。 |
| ARKUI_KEY_INTENSION_DOWN = 2 | 向下。 |
| ARKUI_KEY_INTENSION_LEFT = 3 | 向左。 |
| ARKUI_KEY_INTENSION_RIGHT = 4 | 向右。 |
| ARKUI_KEY_INTENSION_SELECT = 5 | 选中。 |
| ARKUI_KEY_INTENSION_ESCAPE = 6 | 返回。 |
| ARKUI_KEY_INTENSION_BACK = 7 | 后退。 |
| ARKUI_KEY_INTENSION_FORWARD = 8 | 前进。 |
| ARKUI_KEY_INTENSION_MENU = 9 | 菜单。 |
| ARKUI_KEY_INTENSION_HOME = 10 | 主页。 |
| ARKUI_KEY_INTENSION_PAGE_UP = 11 | 上一页。 |
| ARKUI_KEY_INTENSION_PAGE_DOWN = 12 | 下一页。 |
| ARKUI_KEY_INTENSION_ZOOM_OUT = 13 | 缩小。 |
| ARKUI_KEY_INTENSION_ZOOM_IN = 14 | 放大。 |
| ARKUI_KEY_INTENTION_MEDIA_PLAY_PAUSE = 100 | 播放/暂停。 |
| ARKUI_KEY_INTENTION_MEDIA_FAST_FORWARD = 101 | 快进。 |
| ARKUI_KEY_INTENTION_MEDIA_FAST_PLAYBACK = 103 | 快速播放。 |
| ARKUI_KEY_INTENTION_MEDIA_NEXT = 104 | 下一首。 |
| ARKUI_KEY_INTENTION_MEDIA_PREVIOUS = 105 | 上一首。 |
| ARKUI_KEY_INTENTION_MEDIA_MUTE = 106 | 静音。 |
| ARKUI_KEY_INTENTION_VOLUME_UP = 107 | 音量增加。 |
| ARKUI_KEY_INTENTION_VOLUME_DOWN = 108 | 音量降低。 |
| ARKUI_KEY_INTENTION_CALL = 200 | 接听电话。 |
| ARKUI_KEY_INTENTION_CAMERA = 300 | 拍照。 |


## 函数说明

### OH_ArkUI_KeyEvent_Create()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_Create(ArkUI_UIInputEvent** event)
```

**描述：**

创建可通过 [OH_ArkUI_KeyEvent_Dispatch](capi-native-key-event-h.md#oh_arkui_keyevent_dispatch) 分发的按键事件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**资源释放：** arkui/OH_ArkUI_KeyEvent_Destroy {event}

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)** event | [out] 二级指针，指向创建的 **ArkUI_UIInputEvent** 对象，不能为空。成功时创建的事件写入 **event**，事件归调用方所有，必须调用[OH_ArkUI_KeyEvent_Destroy](capi-native-key-event-h.md#oh_arkui_keyevent_destroy)释放。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空。</li> </ul> |

### OH_ArkUI_KeyEvent_Destroy()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_Destroy(ArkUI_UIInputEvent** event)
```

**描述：**

销毁通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件，并将事件指针置空。<br> 当 **event** 不为空且 **event** 指向的事件指针为空时，函数执行成功。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)** event | [in] 二级指针，指向待销毁的 **ArkUI_UIInputEvent** 对象，不能为空。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或者输入事件不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetType()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetType(ArkUI_UIInputEvent* event, ArkUI_KeyEventType type)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件类型。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeyCode()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyCode(ArkUI_UIInputEvent* event, int32_t keyCode)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件键码。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeyText()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyText(ArkUI_UIInputEvent* event, const char* keyText)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件键值。<br> 本函数会复制 **keyText**。函数返回后，调用方可以释放或复用原字符串。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeySource()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeySource(ArkUI_UIInputEvent* event, ArkUI_KeySourceType keySource)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件输入设备类型。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetDeviceId()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetDeviceId(ArkUI_UIInputEvent* event, int32_t deviceId)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件设备ID。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetUnicode()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetUnicode(ArkUI_UIInputEvent* event, uint32_t unicode)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件Unicode码值。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetEventTime()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetEventTime(ArkUI_UIInputEvent* event, int64_t timestamp)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件发生时间。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetPressedKeys()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetPressedKeys(ArkUI_UIInputEvent* event, const int32_t* pressedKeyCodes, int32_t length)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件中所有已按下的按键。<br> 本函数会复制 **pressedKeyCodes**。函数返回后，调用方可以释放或复用原数组。 将 **pressedKeyCodes** 传入空指针、**length** 传入 **0** 可以清空已按下的按键。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeyIntentionCode()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyIntentionCode(ArkUI_UIInputEvent* event, OH_ArkUI_KeyIntention intentionCode)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件意图码。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetNumLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetNumLockOn(ArkUI_UIInputEvent* event, bool isNumLockOn)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件NumLock状态。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetCapsLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetCapsLockOn(ArkUI_UIInputEvent* event, bool isCapsLockOn)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件CapsLock状态。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_SetScrollLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetScrollLockOn(ArkUI_UIInputEvent* event, bool isScrollLockOn)
```

**描述：**

设置通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) 创建的按键事件ScrollLock状态。

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
| ArkUI_ErrorCode | 错误码。<ul> <li>ARKUI_ERROR_CODE_NO_ERROR 成功。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID **event** 为空，或不是通过 [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create)创建的按键事件。</li> </ul> |

### OH_ArkUI_KeyEvent_GetType()

```c
ArkUI_KeyEventType OH_ArkUI_KeyEvent_GetType(const ArkUI_UIInputEvent* event)
```

**描述：**

获取按键的类型。

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
| ArkUI_ErrorCode | 错误码。<br>ARKUI_ERROR_CODE_NO_ERROR 成功。<br>ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 |

### OH_ArkUI_KeyEvent_IsCapsLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsCapsLockOn(const ArkUI_UIInputEvent* event, bool* state)
```

**描述：**

获取按键事件发生时CapsLock的状态。

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
| ArkUI_ErrorCode | 错误码。<br>ARKUI_ERROR_CODE_NO_ERROR 成功。<br>ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 |

### OH_ArkUI_KeyEvent_IsScrollLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsScrollLockOn(const ArkUI_UIInputEvent* event, bool* state)
```

**描述：**

获取按键事件发生时ScrollLock的状态。

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
| ArkUI_ErrorCode | 错误码。<br>ARKUI_ERROR_CODE_NO_ERROR 成功。<br>ARKUI_ERROR_CODE_PARAM_INVALID 函数参数异常。 |


