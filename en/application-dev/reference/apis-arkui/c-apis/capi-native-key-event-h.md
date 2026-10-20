# native_key_event.h

## Overview

Declares the APIs of **NativeKeyEvent** for obtaining the type, key code, key value, input device type, key intent, and Unicode value of a key event. It supports controlling key event bubbling or consumption, dispatching key events, and querying the **NumLock**, **CapsLock**, and **ScrollLock** states. It is applicable to scenarios where the native side needs fine-grained processing of key input events, enabling you to obtain detailed key event information and flexibly control event propagation and consumption behavior.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_KeyCode](#arkui_keycode) | ArkUI_KeyCode | Enumerates the key codes for key events. |
| [ArkUI_KeyEventType](#arkui_keyeventtype) | ArkUI_KeyEventType | Enumerates the types of key events. |
| [ArkUI_KeySourceType](#arkui_keysourcetype) | ArkUI_KeySourceType | Enumerates the types of input devices that trigger key events. |
| [ArkUI_KeyIntension](#arkui_keyintension) | ArkUI_KeyIntension | Enumerates the intentions corresponding to key events. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_Create(ArkUI_UIInputEvent** event)](#oh_arkui_keyevent_create) | Creates a key event that can be dispatched by [OH_ArkUI_KeyEvent_Dispatch](capi-native-key-event-h.md#oh_arkui_keyevent_dispatch). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_Destroy(ArkUI_UIInputEvent** event)](#oh_arkui_keyevent_destroy) | Destroys a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) and sets the event pointer to null.<br> If **event** is not null and the pointer referenced by **event** is null, this function returns successfully. |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetType(ArkUI_UIInputEvent* event, ArkUI_KeyEventType type)](#oh_arkui_keyevent_settype) | Sets the type of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyCode(ArkUI_UIInputEvent* event, int32_t keyCode)](#oh_arkui_keyevent_setkeycode) | Sets the key code of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyText(ArkUI_UIInputEvent* event, const char* keyText)](#oh_arkui_keyevent_setkeytext) | Sets the key text of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).<br> This function copies **keyText**. The caller can release or reuse the original string after this function returns. |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeySource(ArkUI_UIInputEvent* event, ArkUI_KeySourceType keySource)](#oh_arkui_keyevent_setkeysource) | Sets the input device type of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetDeviceId(ArkUI_UIInputEvent* event, int32_t deviceId)](#oh_arkui_keyevent_setdeviceid) | Sets the device ID of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetUnicode(ArkUI_UIInputEvent* event, uint32_t unicode)](#oh_arkui_keyevent_setunicode) | Sets the Unicode value of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetEventTime(ArkUI_UIInputEvent* event, int64_t timestamp)](#oh_arkui_keyevent_seteventtime) | Sets the occurrence time of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetPressedKeys(ArkUI_UIInputEvent* event, const int32_t* pressedKeyCodes, int32_t length)](#oh_arkui_keyevent_setpressedkeys) | Sets all pressed keys of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).<br> This function copies **pressedKeyCodes**. The caller can release or reuse the original array after this function returns. Pass null for **pressedKeyCodes** and **0** for **length** to clear the pressed keys. |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyIntentionCode(ArkUI_UIInputEvent* event, OH_ArkUI_KeyIntention intentionCode)](#oh_arkui_keyevent_setkeyintentioncode) | Sets the intention code of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetNumLockOn(ArkUI_UIInputEvent* event, bool isNumLockOn)](#oh_arkui_keyevent_setnumlockon) | Sets the NumLock state of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetCapsLockOn(ArkUI_UIInputEvent* event, bool isCapsLockOn)](#oh_arkui_keyevent_setcapslockon) | Sets the CapsLock state of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetScrollLockOn(ArkUI_UIInputEvent* event, bool isScrollLockOn)](#oh_arkui_keyevent_setscrolllockon) | Sets the ScrollLock state of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_KeyEventType OH_ArkUI_KeyEvent_GetType(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_gettype) | Obtains the type of the specified key event. |
| [int32_t OH_ArkUI_KeyEvent_GetKeyCode(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeycode) | Obtains the key code from the specified key event. |
| [const char *OH_ArkUI_KeyEvent_GetKeyText(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeytext) | Obtains the key value from the specified key event. |
| [ArkUI_KeySourceType OH_ArkUI_KeyEvent_GetKeySource(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeysource) | Obtains the type of input device that triggers the specified key event. |
| [void OH_ArkUI_KeyEvent_StopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)](#oh_arkui_keyevent_stoppropagation) | Stops event bubbling in the key event callback. This API applies to scenarios where a child component has already handled a key event in a nested component structure and does not want the parent component to respond to the same key again, for example, stopping the event from bubbling upward when handling custom shortcuts. Unlike **OH_ArkUI_KeyEvent_SetConsumed**, this API controls the bubbling of the event, whereas **OH_ArkUI_KeyEvent_SetConsumed** sets whether the event is consumed by the callback. The two APIs can be used together without affecting each other. You are advised to select the appropriate API based on whether you need to stop bubbling or mark consumption. |
| [ArkUI_KeyIntension OH_ArkUI_KeyEvent_GetKeyIntensionCode(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getkeyintensioncode) | Obtains the intention code associated with the specified key event. |
| [uint32_t OH_ArkUI_KeyEvent_GetUnicode(const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_getunicode) | Obtains the Unicode value of the key. Non-space basic Latin characters in the 0x0021-0x007E range are supported. Characters with a value of 0 are not supported. In the case of key combination, this API returns the Unicode value of the key corresponding to the key event. |
| [void OH_ArkUI_KeyEvent_SetConsumed(const ArkUI_UIInputEvent* event, bool isConsumed)](#oh_arkui_keyevent_setconsumed) | Sets whether the event is consumed by the callback in the key event callback. This API applies to scenarios such as shortcut key handling and custom key response of a component, where the event needs to be marked as handled to avoid repeated processing. Unlike **OH_ArkUI_KeyEvent_StopPropagation**, this API marks whether the event is consumed by the current callback rather than controlling event bubbling. To stop the event from bubbling upward, use **OH_ArkUI_KeyEvent_StopPropagation**.<br> For the process and specific timing of key event triggering, see [Key Event Data Flow](../../ui/arkts-interaction-development-guide-keyboard.md#key-event-data-flow). |
| [void OH_ArkUI_KeyEvent_Dispatch(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)](#oh_arkui_keyevent_dispatch) | Dispatches the key event to the specified component node. After this API is called, the key event triggers the key event callback registered on the target node. This API can be used in the key event callback to forward the current key event to the specified component node for secondary processing. Unlike **StopPropagation** and **SetConsumed**, **Dispatch** does not affect the processing state of the current event. |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsNumLockOn(const ArkUI_UIInputEvent* event, bool* state)](#oh_arkui_keyevent_isnumlockon) | Obtains the state of the NumLock key when the specified key event occurs. |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsCapsLockOn(const ArkUI_UIInputEvent* event, bool* state)](#oh_arkui_keyevent_iscapslockon) | Obtains the state of the CapsLock key when the specified key event occurs. |
| [ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsScrollLockOn(const ArkUI_UIInputEvent* event, bool* state)](#oh_arkui_keyevent_isscrolllockon) | Obtains the state of the ScrollLock key when the specified key event occurs. |

### Variable

| Name | Description |
| -- | -- |
| ArkUI_KeyIntension OH_ArkUI_KeyIntention | Defines the correctly spelled alias for the key event intention type.<br> The original type name [ArkUI_KeyIntension](capi-native-key-event-h.md#arkui_keyintension) is retained for compatibility.<br>**Since**: 26.2.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

## Enum type description

### ArkUI_KeyCode

```c
enum ArkUI_KeyCode
```

**Description**

Enumerates the key codes for key events.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

| Enum item | Description |
| -- | -- |
| ARKUI_KEYCODE_UNKNOWN = -1 | Unknown key |
| ARKUI_KEYCODE_FN = 0 | Function (Fn) key |
| ARKUI_KEYCODE_VOLUME_UP = 16 | Volume Up key |
| ARKUI_KEYCODE_VOLUME_DOWN = 17 | Volume Down key |
| ARKUI_KEYCODE_POWER = 18 | Power key |
| ARKUI_KEYCODE_CAMERA = 19 | Camera key |
| ARKUI_KEYCODE_VOLUME_MUTE = 22 | Speaker Mute key |
| ARKUI_KEYCODE_MUTE = 23 | Mute key |
| ARKUI_KEYCODE_BRIGHTNESS_UP = 40 | Brightness Up key. |
| ARKUI_KEYCODE_BRIGHTNESS_DOWN = 41 | Brightness Down key. |
| ARKUI_KEYCODE_0 = 2000 | Key 0 |
| ARKUI_KEYCODE_1 = 2001 | Key 1 |
| ARKUI_KEYCODE_2 = 2002 | Key 2 |
| ARKUI_KEYCODE_3 = 2003 | Key 3 |
| ARKUI_KEYCODE_4 = 2004 | Key 4 |
| ARKUI_KEYCODE_5 = 2005 | Key 5 |
| ARKUI_KEYCODE_6 = 2006 | Key 6 |
| ARKUI_KEYCODE_7 = 2007 | Key 7 |
| ARKUI_KEYCODE_8 = 2008 | Key 8 |
| ARKUI_KEYCODE_9 = 2009 | Key 9 |
| ARKUI_KEYCODE_STAR = 2010 | Key |
| ARKUI_KEYCODE_POUND = 2011 | Key # |
| ARKUI_KEYCODE_DPAD_UP = 2012 | Up key on D-pad. |
| ARKUI_KEYCODE_DPAD_DOWN = 2013 | Down key on D-pad. |
| ARKUI_KEYCODE_DPAD_LEFT = 2014 | Left key on D-pad. |
| ARKUI_KEYCODE_DPAD_RIGHT = 2015 | Right key on D-pad. |
| ARKUI_KEYCODE_DPAD_CENTER = 2016 | Center key on D-pad. |
| ARKUI_KEYCODE_A = 2017 | Key A |
| ARKUI_KEYCODE_B = 2018 | Key B |
| ARKUI_KEYCODE_C = 2019 | Key C |
| ARKUI_KEYCODE_D = 2020 | Key D |
| ARKUI_KEYCODE_E = 2021 | Key E |
| ARKUI_KEYCODE_F = 2022 | Key F |
| ARKUI_KEYCODE_G = 2023 | Key G |
| ARKUI_KEYCODE_H = 2024 | Key H |
| ARKUI_KEYCODE_I = 2025 | Key I |
| ARKUI_KEYCODE_J = 2026 | Key J |
| ARKUI_KEYCODE_K = 2027 | Key K |
| ARKUI_KEYCODE_L = 2028 | Key L |
| ARKUI_KEYCODE_M = 2029 | Key M |
| ARKUI_KEYCODE_N = 2030 | Key N |
| ARKUI_KEYCODE_O = 2031 | Key O |
| ARKUI_KEYCODE_P = 2032 | Key P |
| ARKUI_KEYCODE_Q = 2033 | Key Q |
| ARKUI_KEYCODE_R = 2034 | Key R |
| ARKUI_KEYCODE_S = 2035 | Key S |
| ARKUI_KEYCODE_T = 2036 | Key T |
| ARKUI_KEYCODE_U = 2037 | Key U |
| ARKUI_KEYCODE_V = 2038 | Key V |
| ARKUI_KEYCODE_W = 2039 | Key W |
| ARKUI_KEYCODE_X = 2040 | Key X |
| ARKUI_KEYCODE_Y = 2041 | Key Y |
| ARKUI_KEYCODE_Z = 2042 | Key Z |
| ARKUI_KEYCODE_COMMA = 2043 | Key , |
| ARKUI_KEYCODE_PERIOD = 2044 | Key . |
| ARKUI_KEYCODE_ALT_LEFT = 2045 | Left Alt key |
| ARKUI_KEYCODE_ALT_RIGHT = 2046 | Right Alt key |
| ARKUI_KEYCODE_SHIFT_LEFT = 2047 | Left Shift key |
| ARKUI_KEYCODE_SHIFT_RIGHT = 2048 | Right Shift key |
| ARKUI_KEYCODE_TAB = 2049 | Tab key |
| ARKUI_KEYCODE_SPACE = 2050 | Space key |
| ARKUI_KEYCODE_SYM = 2051 | Symbol key |
| ARKUI_KEYCODE_EXPLORER = 2052 | Explorer key, which is used to start the explorer application |
| ARKUI_KEYCODE_ENVELOPE = 2053 | Email key, which is used to start the email application |
| ARKUI_KEYCODE_ENTER = 2054 | Enter key |
| ARKUI_KEYCODE_DEL = 2055 | Delete key |
| ARKUI_KEYCODE_GRAVE = 2056 | Key ` |
| ARKUI_KEYCODE_MINUS = 2057 | Key - |
| ARKUI_KEYCODE_EQUALS = 2058 | Key = |
| ARKUI_KEYCODE_LEFT_BRACKET = 2059 | Key [ |
| ARKUI_KEYCODE_RIGHT_BRACKET = 2060 | Key ] |
| ARKUI_KEYCODE_BACKSLASH = 2061 | Key \ |
| ARKUI_KEYCODE_SEMICOLON = 2062 | Key ; |
| ARKUI_KEYCODE_APOSTROPHE = 2063 | Key ' |
| ARKUI_KEYCODE_SLASH = 2064 | Key |
| ARKUI_KEYCODE_AT = 2065 | Key @ |
| ARKUI_KEYCODE_PLUS = 2066 | Key + |
| ARKUI_KEYCODE_MENU = 2067 | Menu key |
| ARKUI_KEYCODE_PAGE_UP = 2068 | Page Up key |
| ARKUI_KEYCODE_PAGE_DOWN = 2069 | Page Down key |
| ARKUI_KEYCODE_ESCAPE = 2070 | ESC key. |
| ARKUI_KEYCODE_FORWARD_DEL = 2071 | Forward Delete key |
| ARKUI_KEYCODE_CTRL_LEFT = 2072 | Left Ctrl key |
| ARKUI_KEYCODE_CTRL_RIGHT = 2073 | Right Ctrl key |
| ARKUI_KEYCODE_CAPS_LOCK = 2074 | Caps Lock key |
| ARKUI_KEYCODE_SCROLL_LOCK = 2075 | Scroll Lock key |
| ARKUI_KEYCODE_META_LEFT = 2076 | Left Meta key |
| ARKUI_KEYCODE_META_RIGHT = 2077 | Right Meta key |
| ARKUI_KEYCODE_FUNCTION = 2078 | Function key |
| ARKUI_KEYCODE_SYSRQ = 2079 | System Request/Print Screen key |
| ARKUI_KEYCODE_BREAK = 2080 | Break/Pause key |
| ARKUI_KEYCODE_MOVE_HOME = 2081 | Move to Home key |
| ARKUI_KEYCODE_MOVE_END = 2082 | Move to End key |
| ARKUI_KEYCODE_INSERT = 2083 | Insert key |
| ARKUI_KEYCODE_FORWARD = 2084 | Forward key |
| ARKUI_KEYCODE_MEDIA_PLAY = 2085 | Play key |
| ARKUI_KEYCODE_MEDIA_PAUSE = 2086 | Pause key |
| ARKUI_KEYCODE_MEDIA_CLOSE = 2087 | Close key |
| ARKUI_KEYCODE_MEDIA_EJECT = 2088 | Eject key |
| ARKUI_KEYCODE_MEDIA_RECORD = 2089 | Record key |
| ARKUI_KEYCODE_F1 = 2090 | F1 key |
| ARKUI_KEYCODE_F2 = 2091 | F2 key |
| ARKUI_KEYCODE_F3 = 2092 | F3 key |
| ARKUI_KEYCODE_F4 = 2093 | F4 key |
| ARKUI_KEYCODE_F5 = 2094 | F5 key |
| ARKUI_KEYCODE_F6 = 2095 | F6 key |
| ARKUI_KEYCODE_F7 = 2096 | F7 key |
| ARKUI_KEYCODE_F8 = 2097 | F8 key |
| ARKUI_KEYCODE_F9 = 2098 | F9 key |
| ARKUI_KEYCODE_F10 = 2099 | F10 key |
| ARKUI_KEYCODE_F11 = 2100 | F11 key |
| ARKUI_KEYCODE_F12 = 2101 | F12 key |
| ARKUI_KEYCODE_NUM_LOCK = 2102 | Number Lock key on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_0 = 2103 | Key 0 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_1 = 2104 | Key 1 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_2 = 2105 | Key 2 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_3 = 2106 | Key 3 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_4 = 2107 | Key 4 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_5 = 2108 | Key 5 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_6 = 2109 | Key 6 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_7 = 2110 | Key 7 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_8 = 2111 | Key 8 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_9 = 2112 | Key 9 on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_DIVIDE = 2113 | Key / on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_MULTIPLY = 2114 | Key * on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_SUBTRACT = 2115 | Key - on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_ADD = 2116 | Key + on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_DOT = 2117 | Key . on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_COMMA = 2118 | Key , on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_ENTER = 2119 | Enter key on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_EQUALS = 2120 | Key = on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_LEFT_PAREN = 2121 | Key ( on numeric keypad |
| ARKUI_KEYCODE_NUMPAD_RIGHT_PAREN = 2122 | Key ) on numeric keypad |
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

**Description**

Enumerates the types of key events.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

| Enum item | Description |
| -- | -- |
| ARKUI_KEY_EVENT_UNKNOWN = -1 | Unknown type. |
| ARKUI_KEY_EVENT_DOWN = 0 | Key press. |
| ARKUI_KEY_EVENT_UP = 1 | Release of a key. |
| ARKUI_KEY_EVENT_LONG_PRESS = 2 | Long press of a key. |
| ARKUI_KEY_EVENT_CLICK = 3 | Click of a key. |

### ArkUI_KeySourceType

```c
enum ArkUI_KeySourceType
```

**Description**

Enumerates the types of input devices that trigger key events.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

| Enum item | Description |
| -- | -- |
| ARKUI_KEY_SOURCE_UNKNOWN = 0 | Unknown type. |
| ARKUI_KEY_SOURCE_TYPE_MOUSE = 1 | Mouse. |
| ARKUI_KEY_SOURCE_TYPE_KEYBOARD = 4 | Keyboard. |
| ARKUI_KEY_SOURCE_TYPE_JOYSTICK = 5 | Game controller.<br>**Since**: 15 |

### ArkUI_KeyIntension

```c
enum ArkUI_KeyIntension
```

**Description**

Enumerates the intentions corresponding to key events.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

| Enum item | Description |
| -- | -- |
| ARKUI_KEY_INTENSION_UNKNOWN = -1 | Unknown intention. |
| ARKUI_KEY_INTENSION_UP = 1 | Upward. |
| ARKUI_KEY_INTENSION_DOWN = 2 | Downward. |
| ARKUI_KEY_INTENSION_LEFT = 3 | Leftward. |
| ARKUI_KEY_INTENSION_RIGHT = 4 | Rightward. |
| ARKUI_KEY_INTENSION_SELECT = 5 | Select. |
| ARKUI_KEY_INTENSION_ESCAPE = 6 | Return. |
| ARKUI_KEY_INTENSION_BACK = 7 | Back. |
| ARKUI_KEY_INTENSION_FORWARD = 8 | Forward. |
| ARKUI_KEY_INTENSION_MENU = 9 | Menu. |
| ARKUI_KEY_INTENSION_HOME = 10 | Home page. |
| ARKUI_KEY_INTENSION_PAGE_UP = 11 | Previous. |
| ARKUI_KEY_INTENSION_PAGE_DOWN = 12 | Next. |
| ARKUI_KEY_INTENSION_ZOOM_OUT = 13 | Zoom out. |
| ARKUI_KEY_INTENSION_ZOOM_IN = 14 | Zoom in. |
| ARKUI_KEY_INTENTION_MEDIA_PLAY_PAUSE = 100 | Play/Pause. |
| ARKUI_KEY_INTENTION_MEDIA_FAST_FORWARD = 101 | Fast-forward. |
| ARKUI_KEY_INTENTION_MEDIA_FAST_PLAYBACK = 103 | Fast playback. |
| ARKUI_KEY_INTENTION_MEDIA_NEXT = 104 | Play the next media asset. |
| ARKUI_KEY_INTENTION_MEDIA_PREVIOUS = 105 | Play the previous media asset. |
| ARKUI_KEY_INTENTION_MEDIA_MUTE = 106 | Mute. |
| ARKUI_KEY_INTENTION_VOLUME_UP = 107 | Volume up. |
| ARKUI_KEY_INTENTION_VOLUME_DOWN = 108 | Volume down. |
| ARKUI_KEY_INTENTION_CALL = 200 | Answer a call. |
| ARKUI_KEY_INTENTION_CAMERA = 300 | Take a photo. |


## Function description

### OH_ArkUI_KeyEvent_Create()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_Create(ArkUI_UIInputEvent** event)
```

**Description**

Creates a key event that can be dispatched by [OH_ArkUI_KeyEvent_Dispatch](capi-native-key-event-h.md#oh_arkui_keyevent_dispatch).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Resource release**: arkui/OH_ArkUI_KeyEvent_Destroy {event}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)** event | [out] Double pointer to the created **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b>. On success, the created event is written to **event**. The caller owns the created event and must release it by calling [OH_ArkUI_KeyEvent_Destroy](capi-native-key-event-h.md#oh_arkui_keyevent_destroy). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null.</li> </ul> |

### OH_ArkUI_KeyEvent_Destroy()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_Destroy(ArkUI_UIInputEvent** event)
```

**Description**

Destroys a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create) and sets the event pointer to null.<br> If **event** is not null and the pointer referenced by **event** is null, this function returns successfully.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)** event | [in] Double pointer to the **ArkUI_UIInputEvent** object to destroy. The value must not be <b>nullptr</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or the input event was not created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetType()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetType(ArkUI_UIInputEvent* event, ArkUI_KeyEventType type)
```

**Description**

Sets the type of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_KeyEventType](capi-native-key-event-h.md#arkui_keyeventtype) type | [in] Key event type. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeyCode()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyCode(ArkUI_UIInputEvent* event, int32_t keyCode)
```

**Description**

Sets the key code of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| int32_t keyCode | [in] Key code. The value is defined by [ArkUI_KeyCode](capi-native-key-event-h.md#arkui_keycode). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeyText()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyText(ArkUI_UIInputEvent* event, const char* keyText)
```

**Description**

Sets the key text of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).<br> This function copies **keyText**. The caller can release or reuse the original string after this function returns.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| const char* keyText | [in] Null-terminated key text, in UTF-8 encoding. The value must not be <b>nullptr</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeySource()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeySource(ArkUI_UIInputEvent* event, ArkUI_KeySourceType keySource)
```

**Description**

Sets the input device type of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| [ArkUI_KeySourceType](capi-native-key-event-h.md#arkui_keysourcetype) keySource | [in] Input device type. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetDeviceId()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetDeviceId(ArkUI_UIInputEvent* event, int32_t deviceId)
```

**Description**

Sets the device ID of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| int32_t deviceId | [in] Device ID, which is a system-assigned input device identifier. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetUnicode()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetUnicode(ArkUI_UIInputEvent* event, uint32_t unicode)
```

**Description**

Sets the Unicode value of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| uint32_t unicode | [in] Unicode value. The value must be a valid Unicode code point. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetEventTime()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetEventTime(ArkUI_UIInputEvent* event, int64_t timestamp)
```

**Description**

Sets the occurrence time of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| int64_t timestamp | [in] Event occurrence time, in ns, using the same time base as [OH_ArkUI_UIInputEvent_GetEventTime](capi-ui-input-event-h.md#oh_arkui_uiinputevent_geteventtime). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetPressedKeys()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetPressedKeys(ArkUI_UIInputEvent* event, const int32_t* pressedKeyCodes, int32_t length)
```

**Description**

Sets all pressed keys of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).<br> This function copies **pressedKeyCodes**. The caller can release or reuse the original array after this function returns. Pass null for **pressedKeyCodes** and **0** for **length** to clear the pressed keys.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| const int32_t* pressedKeyCodes | [in] Array of all pressed key codes. Each element is defined by [ArkUI_KeyCode](capi-native-key-event-h.md#arkui_keycode). The value can be <b>nullptr</b> only when **length** is **0**. |
| int32_t length | [in] Number of elements in **pressedKeyCodes**. The value must be greater than or equal to **0**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetKeyIntentionCode()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetKeyIntentionCode(ArkUI_UIInputEvent* event, OH_ArkUI_KeyIntention intentionCode)
```

**Description**

Sets the intention code of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| OH_ArkUI_KeyIntention intentionCode | [in] Intention code associated with the key event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetNumLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetNumLockOn(ArkUI_UIInputEvent* event, bool isNumLockOn)
```

**Description**

Sets the NumLock state of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| bool isNumLockOn | [in] Whether NumLock is activated. The value **true** indicates an activated state, and **false**<br>indicates an inactivated state. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetCapsLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetCapsLockOn(ArkUI_UIInputEvent* event, bool isCapsLockOn)
```

**Description**

Sets the CapsLock state of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| bool isCapsLockOn | [in] Whether CapsLock is activated. The value **true** indicates an activated state, and **false** indicates an inactivated state. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_SetScrollLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_SetScrollLockOn(ArkUI_UIInputEvent* event, bool isScrollLockOn)
```

**Description**

Sets the ScrollLock state of a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | [in] Pointer to the target **ArkUI_UIInputEvent** object. The value must not be <b>nullptr</b> and must reference a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create). |
| bool isScrollLockOn | [in] Whether ScrollLock is activated. The value **true** indicates an activated state, and **false** indicates an inactivated state. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <ul> <li>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>Returns ARKUI_ERROR_CODE_PARAM_INVALID if **event** is null or is not a key event created by [OH_ArkUI_KeyEvent_Create](capi-native-key-event-h.md#oh_arkui_keyevent_create).</li> </ul> |

### OH_ArkUI_KeyEvent_GetType()

```c
ArkUI_KeyEventType OH_ArkUI_KeyEvent_GetType(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the type of the specified key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, used to obtain the key event type corresponding to the event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_KeyEventType](capi-native-key-event-h.md#arkui_keyeventtype) | Key type. |

### OH_ArkUI_KeyEvent_GetKeyCode()

```c
int32_t OH_ArkUI_KeyEvent_GetKeyCode(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the key code from the specified key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, used to obtain the code value of the key corresponding to the event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Key code, corresponding to the code value defined in the **ArkUI_KeyCode** enumeration. |

### OH_ArkUI_KeyEvent_GetKeyText()

```c
const char *OH_ArkUI_KeyEvent_GetKeyText(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the key value from the specified key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, used to obtain the key value text of the key corresponding to the event. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Pointer to the text character content corresponding to the key, that is, the key value string generated by the key. |

### OH_ArkUI_KeyEvent_GetKeySource()

```c
ArkUI_KeySourceType OH_ArkUI_KeyEvent_GetKeySource(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the type of input device that triggers the specified key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, used to obtain the input device type that triggers the key event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_KeySourceType](capi-native-key-event-h.md#arkui_keysourcetype) | Input device type of the current key. |

### OH_ArkUI_KeyEvent_StopPropagation()

```c
void OH_ArkUI_KeyEvent_StopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)
```

**Description**

Stops event bubbling in the key event callback. This API applies to scenarios where a child component has already handled a key event in a nested component structure and does not want the parent component to respond to the same key again, for example, stopping the event from bubbling upward when handling custom shortcuts. Unlike **OH_ArkUI_KeyEvent_SetConsumed**, this API controls the bubbling of the event, whereas **OH_ArkUI_KeyEvent_SetConsumed** sets whether the event is consumed by the callback. The two APIs can be used together without affecting each other. You are advised to select the appropriate API based on whether you need to stop bubbling or mark consumption.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event for which the bubbling behavior is to be set. |
| bool stopPropagation | Whether to stop event bubbling. The value **true** indicates to stop event bubbling, and **false** indicates the opposite. |

### OH_ArkUI_KeyEvent_GetKeyIntensionCode()

```c
ArkUI_KeyIntension OH_ArkUI_KeyEvent_GetKeyIntensionCode(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the intention code associated with the specified key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, used to obtain the key intent corresponding to the event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_KeyIntension](capi-native-key-event-h.md#arkui_keyintension) | Key intent. |

### OH_ArkUI_KeyEvent_GetUnicode()

```c
uint32_t OH_ArkUI_KeyEvent_GetUnicode(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the Unicode value of the key. Non-space basic Latin characters in the 0x0021-0x007E range are supported. Characters with a value of 0 are not supported. In the case of key combination, this API returns the Unicode value of the key corresponding to the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, used to obtain the Unicode value of the key corresponding to the event. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Unicode value. |

### OH_ArkUI_KeyEvent_SetConsumed()

```c
void OH_ArkUI_KeyEvent_SetConsumed(const ArkUI_UIInputEvent* event, bool isConsumed)
```

**Description**

Sets whether the event is consumed by the callback in the key event callback. This API applies to scenarios such as shortcut key handling and custom key response of a component, where the event needs to be marked as handled to avoid repeated processing. Unlike **OH_ArkUI_KeyEvent_StopPropagation**, this API marks whether the event is consumed by the current callback rather than controlling event bubbling. To stop the event from bubbling upward, use **OH_ArkUI_KeyEvent_StopPropagation**.<br> For the process and specific timing of key event triggering, see [Key Event Data Flow](../../ui/arkts-interaction-development-guide-keyboard.md#key-event-data-flow).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, indicating the key event for which whether it is consumed by the current callback is to be set. |
| bool isConsumed | Whether the event is consumed by the callback. The value **true** indicates that the event is consumed, and **false** indicates the opposite. |

### OH_ArkUI_KeyEvent_Dispatch()

```c
void OH_ArkUI_KeyEvent_Dispatch(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)
```

**Description**

Dispatches the key event to the specified component node. After this API is called, the key event triggers the key event callback registered on the target node. This API can be used in the key event callback to forward the current key event to the specified component node for secondary processing. Unlike **StopPropagation** and **SetConsumed**, **Dispatch** does not affect the processing state of the current event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Target component node that receives the dispatched key event. The value must be a valid non-null **ArkUI_NodeHandle** node handle. |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, which indicates the key event to be dispatched to the target component node. |

### OH_ArkUI_KeyEvent_IsNumLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsNumLockOn(const ArkUI_UIInputEvent* event, bool* state)
```

**Description**

Obtains the state of the NumLock key when the specified key event occurs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, used to obtain the NumLock key state when the key event occurs. It must be a **UIInputEvent** of the key type. |
| bool* state | Pointer to the NumLock key state, which is an output parameter. The value **true** indicates an activated state, and **false** indicates an inactivated state. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_KeyEvent_IsCapsLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsCapsLockOn(const ArkUI_UIInputEvent* event, bool* state)
```

**Description**

Obtains the state of the CapsLock key when the specified key event occurs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, used to obtain the CapsLock key state when the key event occurs. |
| bool* state | Pointer to the CapsLock key state, which is an output parameter. The value **true** indicates an activated state, and **false** indicates an inactivated state. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_KeyEvent_IsScrollLockOn()

```c
ArkUI_ErrorCode OH_ArkUI_KeyEvent_IsScrollLockOn(const ArkUI_UIInputEvent* event, bool* state)
```

**Description**

Obtains the state of the ScrollLock key when the specified key event occurs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the key input event, used to obtain the ScrollLock key state when the key event occurs. |
| bool* state | Pointer to the ScrollLock key state, which is an output parameter. The value **true**<br>indicates an activated state, and **false** indicates an inactivated state. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |


