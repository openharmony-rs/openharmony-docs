# oh_key_code.h

## Overview

Defines key codes of the key device.

**File to Include**: <multimodalinput/oh_key_code.h>

**Library**: libohinput.so

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Related module**: [input](capi-input-kit-input.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Input_KeyCode](#input_keycode) | Input_KeyCode | Enumerates the key codes. |

## Enum type description

### Input_KeyCode

```c
enum Input_KeyCode
```

**Description**

Enumerates the key codes.

<!--Device-enum Input_KeyCode--><!--Device-enum Input_KeyCode-End-->

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| KEYCODE_UNKNOWN = -1 | Unknown key<br><!--Device-KEYCODE_UNKNOWN = -1--><!--Device-KEYCODE_UNKNOWN = -1-End--> |
| KEYCODE_FN = 0 | Function (Fn) key<br><!--Device-KEYCODE_FN = 0--><!--Device-KEYCODE_FN = 0-End--> |
| KEYCODE_HOME = 1 | Function (Home) key<br>**Since**: 22<br><!--Device-KEYCODE_HOME = 1--><!--Device-KEYCODE_HOME = 1-End--> |
| KEYCODE_BACK = 2 | Back button<br>**Since**: 22<br><!--Device-KEYCODE_BACK = 2--><!--Device-KEYCODE_BACK = 2-End--> |
| KEYCODE_SEARCH = 9 | Search key<br>**Since**: 22<br><!--Device-KEYCODE_SEARCH = 9--><!--Device-KEYCODE_SEARCH = 9-End--> |
| KEYCODE_MEDIA_PLAY_PAUSE = 10 | Media: Play/Pause key<br>Difference between this key and **KEYCODE_PLAYPAUSE**:<br> **KEYCODE_PLAYPAUSE**<br>is an earlier definition, while **KEYCODE_MEDIA_PLAY_PAUSE** is designed for modern media key devices.<br>**Since**: 22<br><!--Device-KEYCODE_MEDIA_PLAY_PAUSE = 10--><!--Device-KEYCODE_MEDIA_PLAY_PAUSE = 10-End--> |
| KEYCODE_MEDIA_STOP = 11 | Media: Stop Key<br>**Since**: 22<br><!--Device-KEYCODE_MEDIA_STOP = 11--><!--Device-KEYCODE_MEDIA_STOP = 11-End--> |
| KEYCODE_MEDIA_NEXT = 12 | Media: Next key<br>**Since**: 22<br><!--Device-KEYCODE_MEDIA_NEXT = 12--><!--Device-KEYCODE_MEDIA_NEXT = 12-End--> |
| KEYCODE_MEDIA_PREVIOUS = 13 | Media: Previous key<br>**Since**: 22<br><!--Device-KEYCODE_MEDIA_PREVIOUS = 13--><!--Device-KEYCODE_MEDIA_PREVIOUS = 13-End--> |
| KEYCODE_MEDIA_REWIND = 14 | Media: Rewind key<br>**Since**: 22<br><!--Device-KEYCODE_MEDIA_REWIND = 14--><!--Device-KEYCODE_MEDIA_REWIND = 14-End--> |
| KEYCODE_MEDIA_FAST_FORWARD = 15 | Media: Fast Forward key<br>**Since**: 22<br><!--Device-KEYCODE_MEDIA_FAST_FORWARD = 15--><!--Device-KEYCODE_MEDIA_FAST_FORWARD = 15-End--> |
| KEYCODE_VOLUME_UP = 16 | Volume Up key<br><!--Device-KEYCODE_VOLUME_UP = 16--><!--Device-KEYCODE_VOLUME_UP = 16-End--> |
| KEYCODE_VOLUME_DOWN = 17 | Volume Down key<br><!--Device-KEYCODE_VOLUME_DOWN = 17--><!--Device-KEYCODE_VOLUME_DOWN = 17-End--> |
| KEYCODE_POWER = 18 | Power key<br><!--Device-KEYCODE_POWER = 18--><!--Device-KEYCODE_POWER = 18-End--> |
| KEYCODE_CAMERA = 19 | Camera key<br><!--Device-KEYCODE_CAMERA = 19--><!--Device-KEYCODE_CAMERA = 19-End--> |
| KEYCODE_VOLUME_MUTE = 22 | Speaker Mute key<br><!--Device-KEYCODE_VOLUME_MUTE = 22--><!--Device-KEYCODE_VOLUME_MUTE = 22-End--> |
| KEYCODE_MUTE = 23 | Mute key<br><!--Device-KEYCODE_MUTE = 23--><!--Device-KEYCODE_MUTE = 23-End--> |
| KEYCODE_BRIGHTNESS_UP = 40 | Brightness Up key<br><!--Device-KEYCODE_BRIGHTNESS_UP = 40--><!--Device-KEYCODE_BRIGHTNESS_UP = 40-End--> |
| KEYCODE_BRIGHTNESS_DOWN = 41 | Brightness Down key<br><!--Device-KEYCODE_BRIGHTNESS_DOWN = 41--><!--Device-KEYCODE_BRIGHTNESS_DOWN = 41-End--> |
| KEYCODE_0 = 2000 | Key 0<br><!--Device-KEYCODE_0 = 2000--><!--Device-KEYCODE_0 = 2000-End--> |
| KEYCODE_1 = 2001 | Key 1<br><!--Device-KEYCODE_1 = 2001--><!--Device-KEYCODE_1 = 2001-End--> |
| KEYCODE_2 = 2002 | Key 2<br><!--Device-KEYCODE_2 = 2002--><!--Device-KEYCODE_2 = 2002-End--> |
| KEYCODE_3 = 2003 | Key 3<br><!--Device-KEYCODE_3 = 2003--><!--Device-KEYCODE_3 = 2003-End--> |
| KEYCODE_4 = 2004 | Key 4<br><!--Device-KEYCODE_4 = 2004--><!--Device-KEYCODE_4 = 2004-End--> |
| KEYCODE_5 = 2005 | Key 5<br><!--Device-KEYCODE_5 = 2005--><!--Device-KEYCODE_5 = 2005-End--> |
| KEYCODE_6 = 2006 | Key 6<br><!--Device-KEYCODE_6 = 2006--><!--Device-KEYCODE_6 = 2006-End--> |
| KEYCODE_7 = 2007 | Key 7<br><!--Device-KEYCODE_7 = 2007--><!--Device-KEYCODE_7 = 2007-End--> |
| KEYCODE_8 = 2008 | Key 8<br><!--Device-KEYCODE_8 = 2008--><!--Device-KEYCODE_8 = 2008-End--> |
| KEYCODE_9 = 2009 | Key 9<br><!--Device-KEYCODE_9 = 2009--><!--Device-KEYCODE_9 = 2009-End--> |
| KEYCODE_STAR = 2010 | Key *<br>**Since**: 12<br><!--Device-KEYCODE_STAR = 2010--><!--Device-KEYCODE_STAR = 2010-End--> |
| KEYCODE_POUND = 2011 | Key #<br><!--Device-KEYCODE_POUND = 2011--><!--Device-KEYCODE_POUND = 2011-End--> |
| KEYCODE_DPAD_UP = 2012 | Up key on D-pad<br><!--Device-KEYCODE_DPAD_UP = 2012--><!--Device-KEYCODE_DPAD_UP = 2012-End--> |
| KEYCODE_DPAD_DOWN = 2013 | Down key on D-pad<br><!--Device-KEYCODE_DPAD_DOWN = 2013--><!--Device-KEYCODE_DPAD_DOWN = 2013-End--> |
| KEYCODE_DPAD_LEFT = 2014 | Left key on D-pad<br><!--Device-KEYCODE_DPAD_LEFT = 2014--><!--Device-KEYCODE_DPAD_LEFT = 2014-End--> |
| KEYCODE_DPAD_RIGHT = 2015 | Right key on D-pad<br><!--Device-KEYCODE_DPAD_RIGHT = 2015--><!--Device-KEYCODE_DPAD_RIGHT = 2015-End--> |
| KEYCODE_DPAD_CENTER = 2016 | Center key on D-pad<br><!--Device-KEYCODE_DPAD_CENTER = 2016--><!--Device-KEYCODE_DPAD_CENTER = 2016-End--> |
| KEYCODE_A = 2017 | Key A<br><!--Device-KEYCODE_A = 2017--><!--Device-KEYCODE_A = 2017-End--> |
| KEYCODE_B = 2018 | Key B<br><!--Device-KEYCODE_B = 2018--><!--Device-KEYCODE_B = 2018-End--> |
| KEYCODE_C = 2019 | Key C<br><!--Device-KEYCODE_C = 2019--><!--Device-KEYCODE_C = 2019-End--> |
| KEYCODE_D = 2020 | Key D<br><!--Device-KEYCODE_D = 2020--><!--Device-KEYCODE_D = 2020-End--> |
| KEYCODE_E = 2021 | Key E<br><!--Device-KEYCODE_E = 2021--><!--Device-KEYCODE_E = 2021-End--> |
| KEYCODE_F = 2022 | Key F<br><!--Device-KEYCODE_F = 2022--><!--Device-KEYCODE_F = 2022-End--> |
| KEYCODE_G = 2023 | Key G<br><!--Device-KEYCODE_G = 2023--><!--Device-KEYCODE_G = 2023-End--> |
| KEYCODE_H = 2024 | Key H<br><!--Device-KEYCODE_H = 2024--><!--Device-KEYCODE_H = 2024-End--> |
| KEYCODE_I = 2025 | Key I<br><!--Device-KEYCODE_I = 2025--><!--Device-KEYCODE_I = 2025-End--> |
| KEYCODE_J = 2026 | Key J<br><!--Device-KEYCODE_J = 2026--><!--Device-KEYCODE_J = 2026-End--> |
| KEYCODE_K = 2027 | Key K<br><!--Device-KEYCODE_K = 2027--><!--Device-KEYCODE_K = 2027-End--> |
| KEYCODE_L = 2028 | Key L<br><!--Device-KEYCODE_L = 2028--><!--Device-KEYCODE_L = 2028-End--> |
| KEYCODE_M = 2029 | Key M<br><!--Device-KEYCODE_M = 2029--><!--Device-KEYCODE_M = 2029-End--> |
| KEYCODE_N = 2030 | Key N<br><!--Device-KEYCODE_N = 2030--><!--Device-KEYCODE_N = 2030-End--> |
| KEYCODE_O = 2031 | Key O<br><!--Device-KEYCODE_O = 2031--><!--Device-KEYCODE_O = 2031-End--> |
| KEYCODE_P = 2032 | Key P<br><!--Device-KEYCODE_P = 2032--><!--Device-KEYCODE_P = 2032-End--> |
| KEYCODE_Q = 2033 | Key Q<br><!--Device-KEYCODE_Q = 2033--><!--Device-KEYCODE_Q = 2033-End--> |
| KEYCODE_R = 2034 | Key R<br><!--Device-KEYCODE_R = 2034--><!--Device-KEYCODE_R = 2034-End--> |
| KEYCODE_S = 2035 | Key S<br><!--Device-KEYCODE_S = 2035--><!--Device-KEYCODE_S = 2035-End--> |
| KEYCODE_T = 2036 | Key T<br><!--Device-KEYCODE_T = 2036--><!--Device-KEYCODE_T = 2036-End--> |
| KEYCODE_U = 2037 | Key U<br><!--Device-KEYCODE_U = 2037--><!--Device-KEYCODE_U = 2037-End--> |
| KEYCODE_V = 2038 | Key V<br><!--Device-KEYCODE_V = 2038--><!--Device-KEYCODE_V = 2038-End--> |
| KEYCODE_W = 2039 | Key W<br><!--Device-KEYCODE_W = 2039--><!--Device-KEYCODE_W = 2039-End--> |
| KEYCODE_X = 2040 | Key X<br><!--Device-KEYCODE_X = 2040--><!--Device-KEYCODE_X = 2040-End--> |
| KEYCODE_Y = 2041 | Key Y<br><!--Device-KEYCODE_Y = 2041--><!--Device-KEYCODE_Y = 2041-End--> |
| KEYCODE_Z = 2042 | Key Z<br><!--Device-KEYCODE_Z = 2042--><!--Device-KEYCODE_Z = 2042-End--> |
| KEYCODE_COMMA = 2043 | Key ,<br><!--Device-KEYCODE_COMMA = 2043--><!--Device-KEYCODE_COMMA = 2043-End--> |
| KEYCODE_PERIOD = 2044 | Key .<br><!--Device-KEYCODE_PERIOD = 2044--><!--Device-KEYCODE_PERIOD = 2044-End--> |
| KEYCODE_ALT_LEFT = 2045 | Left Alt key<br><!--Device-KEYCODE_ALT_LEFT = 2045--><!--Device-KEYCODE_ALT_LEFT = 2045-End--> |
| KEYCODE_ALT_RIGHT = 2046 | Right Alt key<br><!--Device-KEYCODE_ALT_RIGHT = 2046--><!--Device-KEYCODE_ALT_RIGHT = 2046-End--> |
| KEYCODE_SHIFT_LEFT = 2047 | Left Shift key<br><!--Device-KEYCODE_SHIFT_LEFT = 2047--><!--Device-KEYCODE_SHIFT_LEFT = 2047-End--> |
| KEYCODE_SHIFT_RIGHT = 2048 | Right Shift key<br><!--Device-KEYCODE_SHIFT_RIGHT = 2048--><!--Device-KEYCODE_SHIFT_RIGHT = 2048-End--> |
| KEYCODE_TAB = 2049 | Tab key<br><!--Device-KEYCODE_TAB = 2049--><!--Device-KEYCODE_TAB = 2049-End--> |
| KEYCODE_SPACE = 2050 | Space key<br><!--Device-KEYCODE_SPACE = 2050--><!--Device-KEYCODE_SPACE = 2050-End--> |
| KEYCODE_SYM = 2051 | Symbol key<br><!--Device-KEYCODE_SYM = 2051--><!--Device-KEYCODE_SYM = 2051-End--> |
| KEYCODE_EXPLORER = 2052 | Browser function key, used to launch the browser application.<br><!--Device-KEYCODE_EXPLORER = 2052--><!--Device-KEYCODE_EXPLORER = 2052-End--> |
| KEYCODE_ENVELOPE = 2053 | Email function key, used to launch the email application.<br><!--Device-KEYCODE_ENVELOPE = 2053--><!--Device-KEYCODE_ENVELOPE = 2053-End--> |
| KEYCODE_ENTER = 2054 | Enter key<br><!--Device-KEYCODE_ENTER = 2054--><!--Device-KEYCODE_ENTER = 2054-End--> |
| KEYCODE_DEL = 2055 | Delete key<br><!--Device-KEYCODE_DEL = 2055--><!--Device-KEYCODE_DEL = 2055-End--> |
| KEYCODE_GRAVE = 2056 | Key `<br><!--Device-KEYCODE_GRAVE = 2056--><!--Device-KEYCODE_GRAVE = 2056-End--> |
| KEYCODE_MINUS = 2057 | Key -<br><!--Device-KEYCODE_MINUS = 2057--><!--Device-KEYCODE_MINUS = 2057-End--> |
| KEYCODE_EQUALS = 2058 | Key =<br><!--Device-KEYCODE_EQUALS = 2058--><!--Device-KEYCODE_EQUALS = 2058-End--> |
| KEYCODE_LEFT_BRACKET = 2059 | Key [<br><!--Device-KEYCODE_LEFT_BRACKET = 2059--><!--Device-KEYCODE_LEFT_BRACKET = 2059-End--> |
| KEYCODE_RIGHT_BRACKET = 2060 | Key ]<br><!--Device-KEYCODE_RIGHT_BRACKET = 2060--><!--Device-KEYCODE_RIGHT_BRACKET = 2060-End--> |
| KEYCODE_BACKSLASH = 2061 | Key \<br>**Since**: 12<br><!--Device-KEYCODE_BACKSLASH = 2061--><!--Device-KEYCODE_BACKSLASH = 2061-End--> |
| KEYCODE_SEMICOLON = 2062 | Key ;<br><!--Device-KEYCODE_SEMICOLON = 2062--><!--Device-KEYCODE_SEMICOLON = 2062-End--> |
| KEYCODE_APOSTROPHE = 2063 | Key ' (single quote)<br>**Since**: 12<br><!--Device-KEYCODE_APOSTROPHE = 2063--><!--Device-KEYCODE_APOSTROPHE = 2063-End--> |
| KEYCODE_SLASH = 2064 | Key<br>**Since**: 12<br><!--Device-KEYCODE_SLASH = 2064--><!--Device-KEYCODE_SLASH = 2064-End--> |
| KEYCODE_AT = 2065 | Key @<br><!--Device-KEYCODE_AT = 2065--><!--Device-KEYCODE_AT = 2065-End--> |
| KEYCODE_PLUS = 2066 | Key +<br><!--Device-KEYCODE_PLUS = 2066--><!--Device-KEYCODE_PLUS = 2066-End--> |
| KEYCODE_MENU = 2067 | Menu key<br><!--Device-KEYCODE_MENU = 2067--><!--Device-KEYCODE_MENU = 2067-End--> |
| KEYCODE_PAGE_UP = 2068 | Page Up key<br><!--Device-KEYCODE_PAGE_UP = 2068--><!--Device-KEYCODE_PAGE_UP = 2068-End--> |
| KEYCODE_PAGE_DOWN = 2069 | Page Down key<br><!--Device-KEYCODE_PAGE_DOWN = 2069--><!--Device-KEYCODE_PAGE_DOWN = 2069-End--> |
| KEYCODE_ESCAPE = 2070 | Esc key<br><!--Device-KEYCODE_ESCAPE = 2070--><!--Device-KEYCODE_ESCAPE = 2070-End--> |
| KEYCODE_FORWARD_DEL = 2071 | Forward Delete key<br><!--Device-KEYCODE_FORWARD_DEL = 2071--><!--Device-KEYCODE_FORWARD_DEL = 2071-End--> |
| KEYCODE_CTRL_LEFT = 2072 | Left Ctrl key<br><!--Device-KEYCODE_CTRL_LEFT = 2072--><!--Device-KEYCODE_CTRL_LEFT = 2072-End--> |
| KEYCODE_CTRL_RIGHT = 2073 | Right Ctrl key<br><!--Device-KEYCODE_CTRL_RIGHT = 2073--><!--Device-KEYCODE_CTRL_RIGHT = 2073-End--> |
| KEYCODE_CAPS_LOCK = 2074 | Caps Lock key<br><!--Device-KEYCODE_CAPS_LOCK = 2074--><!--Device-KEYCODE_CAPS_LOCK = 2074-End--> |
| KEYCODE_SCROLL_LOCK = 2075 | Scroll Lock key<br><!--Device-KEYCODE_SCROLL_LOCK = 2075--><!--Device-KEYCODE_SCROLL_LOCK = 2075-End--> |
| KEYCODE_META_LEFT = 2076 | Left Meta key<br><!--Device-KEYCODE_META_LEFT = 2076--><!--Device-KEYCODE_META_LEFT = 2076-End--> |
| KEYCODE_META_RIGHT = 2077 | Right Meta key<br><!--Device-KEYCODE_META_RIGHT = 2077--><!--Device-KEYCODE_META_RIGHT = 2077-End--> |
| KEYCODE_FUNCTION = 2078 | Function key<br><!--Device-KEYCODE_FUNCTION = 2078--><!--Device-KEYCODE_FUNCTION = 2078-End--> |
| KEYCODE_SYSRQ = 2079 | System Request/Print Screen key<br><!--Device-KEYCODE_SYSRQ = 2079--><!--Device-KEYCODE_SYSRQ = 2079-End--> |
| KEYCODE_BREAK = 2080 | Break/Pause key<br><!--Device-KEYCODE_BREAK = 2080--><!--Device-KEYCODE_BREAK = 2080-End--> |
| KEYCODE_MOVE_HOME = 2081 | Move to Home key<br><!--Device-KEYCODE_MOVE_HOME = 2081--><!--Device-KEYCODE_MOVE_HOME = 2081-End--> |
| KEYCODE_MOVE_END = 2082 | Move to End key<br><!--Device-KEYCODE_MOVE_END = 2082--><!--Device-KEYCODE_MOVE_END = 2082-End--> |
| KEYCODE_INSERT = 2083 | Insert key<br><!--Device-KEYCODE_INSERT = 2083--><!--Device-KEYCODE_INSERT = 2083-End--> |
| KEYCODE_FORWARD = 2084 | Forward key<br><!--Device-KEYCODE_FORWARD = 2084--><!--Device-KEYCODE_FORWARD = 2084-End--> |
| KEYCODE_MEDIA_PLAY = 2085 | Media: Play key<br><!--Device-KEYCODE_MEDIA_PLAY = 2085--><!--Device-KEYCODE_MEDIA_PLAY = 2085-End--> |
| KEYCODE_MEDIA_PAUSE = 2086 | Media: Pause key<br><!--Device-KEYCODE_MEDIA_PAUSE = 2086--><!--Device-KEYCODE_MEDIA_PAUSE = 2086-End--> |
| KEYCODE_MEDIA_CLOSE = 2087 | Media: Close key<br><!--Device-KEYCODE_MEDIA_CLOSE = 2087--><!--Device-KEYCODE_MEDIA_CLOSE = 2087-End--> |
| KEYCODE_MEDIA_EJECT = 2088 | Media: Eject key<br>**Since**: 12<br><!--Device-KEYCODE_MEDIA_EJECT = 2088--><!--Device-KEYCODE_MEDIA_EJECT = 2088-End--> |
| KEYCODE_MEDIA_RECORD = 2089 | Media: Record key<br><!--Device-KEYCODE_MEDIA_RECORD = 2089--><!--Device-KEYCODE_MEDIA_RECORD = 2089-End--> |
| KEYCODE_F1 = 2090 | F1 key<br><!--Device-KEYCODE_F1 = 2090--><!--Device-KEYCODE_F1 = 2090-End--> |
| KEYCODE_F2 = 2091 | F2 key<br><!--Device-KEYCODE_F2 = 2091--><!--Device-KEYCODE_F2 = 2091-End--> |
| KEYCODE_F3 = 2092 | F3 key<br><!--Device-KEYCODE_F3 = 2092--><!--Device-KEYCODE_F3 = 2092-End--> |
| KEYCODE_F4 = 2093 | F4 key<br><!--Device-KEYCODE_F4 = 2093--><!--Device-KEYCODE_F4 = 2093-End--> |
| KEYCODE_F5 = 2094 | F5 key<br><!--Device-KEYCODE_F5 = 2094--><!--Device-KEYCODE_F5 = 2094-End--> |
| KEYCODE_F6 = 2095 | F6 key<br><!--Device-KEYCODE_F6 = 2095--><!--Device-KEYCODE_F6 = 2095-End--> |
| KEYCODE_F7 = 2096 | F7 key<br><!--Device-KEYCODE_F7 = 2096--><!--Device-KEYCODE_F7 = 2096-End--> |
| KEYCODE_F8 = 2097 | F8 key<br><!--Device-KEYCODE_F8 = 2097--><!--Device-KEYCODE_F8 = 2097-End--> |
| KEYCODE_F9 = 2098 | F9 key<br><!--Device-KEYCODE_F9 = 2098--><!--Device-KEYCODE_F9 = 2098-End--> |
| KEYCODE_F10 = 2099 | F10 key<br><!--Device-KEYCODE_F10 = 2099--><!--Device-KEYCODE_F10 = 2099-End--> |
| KEYCODE_F11 = 2100 | F11 key<br><!--Device-KEYCODE_F11 = 2100--><!--Device-KEYCODE_F11 = 2100-End--> |
| KEYCODE_F12 = 2101 | F12 key<br><!--Device-KEYCODE_F12 = 2101--><!--Device-KEYCODE_F12 = 2101-End--> |
| KEYCODE_NUM_LOCK = 2102 | Number Lock key<br><!--Device-KEYCODE_NUM_LOCK = 2102--><!--Device-KEYCODE_NUM_LOCK = 2102-End--> |
| KEYCODE_NUMPAD_0 = 2103 | Key 0 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_0 = 2103--><!--Device-KEYCODE_NUMPAD_0 = 2103-End--> |
| KEYCODE_NUMPAD_1 = 2104 | Key 1 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_1 = 2104--><!--Device-KEYCODE_NUMPAD_1 = 2104-End--> |
| KEYCODE_NUMPAD_2 = 2105 | Key 2 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_2 = 2105--><!--Device-KEYCODE_NUMPAD_2 = 2105-End--> |
| KEYCODE_NUMPAD_3 = 2106 | Key 3 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_3 = 2106--><!--Device-KEYCODE_NUMPAD_3 = 2106-End--> |
| KEYCODE_NUMPAD_4 = 2107 | Key 4 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_4 = 2107--><!--Device-KEYCODE_NUMPAD_4 = 2107-End--> |
| KEYCODE_NUMPAD_5 = 2108 | Key 5 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_5 = 2108--><!--Device-KEYCODE_NUMPAD_5 = 2108-End--> |
| KEYCODE_NUMPAD_6 = 2109 | Key 6 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_6 = 2109--><!--Device-KEYCODE_NUMPAD_6 = 2109-End--> |
| KEYCODE_NUMPAD_7 = 2110 | Key 7 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_7 = 2110--><!--Device-KEYCODE_NUMPAD_7 = 2110-End--> |
| KEYCODE_NUMPAD_8 = 2111 | Key 8 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_8 = 2111--><!--Device-KEYCODE_NUMPAD_8 = 2111-End--> |
| KEYCODE_NUMPAD_9 = 2112 | Key 9 on numeric keypad<br><!--Device-KEYCODE_NUMPAD_9 = 2112--><!--Device-KEYCODE_NUMPAD_9 = 2112-End--> |
| KEYCODE_NUMPAD_DIVIDE = 2113 | Key / on numeric keypad<br><!--Device-KEYCODE_NUMPAD_DIVIDE = 2113--><!--Device-KEYCODE_NUMPAD_DIVIDE = 2113-End--> |
| KEYCODE_NUMPAD_MULTIPLY = 2114 | Key * on numeric keypad<br><!--Device-KEYCODE_NUMPAD_MULTIPLY = 2114--><!--Device-KEYCODE_NUMPAD_MULTIPLY = 2114-End--> |
| KEYCODE_NUMPAD_SUBTRACT = 2115 | Key - on numeric keypad<br><!--Device-KEYCODE_NUMPAD_SUBTRACT = 2115--><!--Device-KEYCODE_NUMPAD_SUBTRACT = 2115-End--> |
| KEYCODE_NUMPAD_ADD = 2116 | Key + on numeric keypad<br><!--Device-KEYCODE_NUMPAD_ADD = 2116--><!--Device-KEYCODE_NUMPAD_ADD = 2116-End--> |
| KEYCODE_NUMPAD_DOT = 2117 | Key . on numeric keypad<br><!--Device-KEYCODE_NUMPAD_DOT = 2117--><!--Device-KEYCODE_NUMPAD_DOT = 2117-End--> |
| KEYCODE_NUMPAD_COMMA = 2118 | Key , on numeric keypad<br><!--Device-KEYCODE_NUMPAD_COMMA = 2118--><!--Device-KEYCODE_NUMPAD_COMMA = 2118-End--> |
| KEYCODE_NUMPAD_ENTER = 2119 | Enter key on numeric keypad<br><!--Device-KEYCODE_NUMPAD_ENTER = 2119--><!--Device-KEYCODE_NUMPAD_ENTER = 2119-End--> |
| KEYCODE_NUMPAD_EQUALS = 2120 | Key = on numeric keypad<br><!--Device-KEYCODE_NUMPAD_EQUALS = 2120--><!--Device-KEYCODE_NUMPAD_EQUALS = 2120-End--> |
| KEYCODE_NUMPAD_LEFT_PAREN = 2121 | Key ( on numeric keypad<br><!--Device-KEYCODE_NUMPAD_LEFT_PAREN = 2121--><!--Device-KEYCODE_NUMPAD_LEFT_PAREN = 2121-End--> |
| KEYCODE_NUMPAD_RIGHT_PAREN = 2122 | Key ) on numeric keypad<br><!--Device-KEYCODE_NUMPAD_RIGHT_PAREN = 2122--><!--Device-KEYCODE_NUMPAD_RIGHT_PAREN = 2122-End--> |
| KEYCODE_VIRTUAL_MULTITASK = 2210 | Multi-task key<br>**Since**: 22<br><!--Device-KEYCODE_VIRTUAL_MULTITASK = 2210--><!--Device-KEYCODE_VIRTUAL_MULTITASK = 2210-End--> |
| KEYCODE_BUTTON_A = 2301 | Joystick key A<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_A = 2301--><!--Device-KEYCODE_BUTTON_A = 2301-End--> |
| KEYCODE_BUTTON_B = 2302 | Joystick key B<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_B = 2302--><!--Device-KEYCODE_BUTTON_B = 2302-End--> |
| KEYCODE_BUTTON_X = 2304 | Joystick key X<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_X = 2304--><!--Device-KEYCODE_BUTTON_X = 2304-End--> |
| KEYCODE_BUTTON_Y = 2305 | Joystick key Y<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_Y = 2305--><!--Device-KEYCODE_BUTTON_Y = 2305-End--> |
| KEYCODE_BUTTON_L1 = 2307 | Joystick key L1<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_L1 = 2307--><!--Device-KEYCODE_BUTTON_L1 = 2307-End--> |
| KEYCODE_BUTTON_R1 = 2308 | Joystick key R1<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_R1 = 2308--><!--Device-KEYCODE_BUTTON_R1 = 2308-End--> |
| KEYCODE_BUTTON_L2 = 2309 | Joystick key L2<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_L2 = 2309--><!--Device-KEYCODE_BUTTON_L2 = 2309-End--> |
| KEYCODE_BUTTON_R2 = 2310 | Joystick key R2<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_R2 = 2310--><!--Device-KEYCODE_BUTTON_R2 = 2310-End--> |
| KEYCODE_BUTTON_SELECT = 2311 | Joystick key Select<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_SELECT = 2311--><!--Device-KEYCODE_BUTTON_SELECT = 2311-End--> |
| KEYCODE_BUTTON_START = 2312 | Joystick key Start<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_START = 2312--><!--Device-KEYCODE_BUTTON_START = 2312-End--> |
| KEYCODE_BUTTON_MODE = 2313 | Joystick key Mode<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_MODE = 2313--><!--Device-KEYCODE_BUTTON_MODE = 2313-End--> |
| KEYCODE_BUTTON_THUMBL = 2314 | Joystick key THUMBL<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_THUMBL = 2314--><!--Device-KEYCODE_BUTTON_THUMBL = 2314-End--> |
| KEYCODE_BUTTON_THUMBR = 2315 | Joystick key THUMBR<br>**Since**: 22<br><!--Device-KEYCODE_BUTTON_THUMBR = 2315--><!--Device-KEYCODE_BUTTON_THUMBR = 2315-End--> |
| KEYCODE_SLEEP = 2600 | Sleep key<br>**Since**: 22<br><!--Device-KEYCODE_SLEEP = 2600--><!--Device-KEYCODE_SLEEP = 2600-End--> |
| KEYCODE_ZENKAKU_HANKAKU = 2601 | Zenkaku/Hankaku key<br>**Since**: 22<br><!--Device-KEYCODE_ZENKAKU_HANKAKU = 2601--><!--Device-KEYCODE_ZENKAKU_HANKAKU = 2601-End--> |
| KEYCODE_102ND = 2602 | International Keyboard Extension key<br>**Since**: 22<br><!--Device-KEYCODE_102ND = 2602--><!--Device-KEYCODE_102ND = 2602-End--> |
| KEYCODE_RO = 2603 | Ro key<br>**Since**: 22<br><!--Device-KEYCODE_RO = 2603--><!--Device-KEYCODE_RO = 2603-End--> |
| KEYCODE_KATAKANA = 2604 | Katakana key<br>**Since**: 22<br><!--Device-KEYCODE_KATAKANA = 2604--><!--Device-KEYCODE_KATAKANA = 2604-End--> |
| KEYCODE_HIRAGANA = 2605 | Hiragana key<br>**Since**: 22<br><!--Device-KEYCODE_HIRAGANA = 2605--><!--Device-KEYCODE_HIRAGANA = 2605-End--> |
| KEYCODE_HENKAN = 2606 | Henkan key<br>**Since**: 22<br><!--Device-KEYCODE_HENKAN = 2606--><!--Device-KEYCODE_HENKAN = 2606-End--> |
| KEYCODE_KATAKANA_HIRAGANA = 2607 | Katakana/Hiragana key<br>**Since**: 22<br><!--Device-KEYCODE_KATAKANA_HIRAGANA = 2607--><!--Device-KEYCODE_KATAKANA_HIRAGANA = 2607-End--> |
| KEYCODE_MUHENKAN = 2608 | Muhenkan key<br>**Since**: 22<br><!--Device-KEYCODE_MUHENKAN = 2608--><!--Device-KEYCODE_MUHENKAN = 2608-End--> |
| KEYCODE_LINEFEED = 2609 | Linefeed key<br>**Since**: 22<br><!--Device-KEYCODE_LINEFEED = 2609--><!--Device-KEYCODE_LINEFEED = 2609-End--> |
| KEYCODE_MACRO = 2610 | Macro key<br>**Since**: 22<br><!--Device-KEYCODE_MACRO = 2610--><!--Device-KEYCODE_MACRO = 2610-End--> |
| KEYCODE_NUMPAD_PLUSMINUS = 2611 | Plus/Minus key on the numeric keypad<br>**Since**: 22<br><!--Device-KEYCODE_NUMPAD_PLUSMINUS = 2611--><!--Device-KEYCODE_NUMPAD_PLUSMINUS = 2611-End--> |
| KEYCODE_SCALE = 2612 | Scale key<br>**Since**: 22<br><!--Device-KEYCODE_SCALE = 2612--><!--Device-KEYCODE_SCALE = 2612-End--> |
| KEYCODE_HANGUEL = 2613 | Hangul key<br>**Since**: 22<br><!--Device-KEYCODE_HANGUEL = 2613--><!--Device-KEYCODE_HANGUEL = 2613-End--> |
| KEYCODE_HANJA = 2614 | Hanja key<br>**Since**: 22<br><!--Device-KEYCODE_HANJA = 2614--><!--Device-KEYCODE_HANJA = 2614-End--> |
| KEYCODE_YEN = 2615 | Yen key<br>**Since**: 22<br><!--Device-KEYCODE_YEN = 2615--><!--Device-KEYCODE_YEN = 2615-End--> |
| KEYCODE_STOP = 2616 | Stop key<br>**Since**: 22<br><!--Device-KEYCODE_STOP = 2616--><!--Device-KEYCODE_STOP = 2616-End--> |
| KEYCODE_AGAIN = 2617 | Again key<br>**Since**: 22<br><!--Device-KEYCODE_AGAIN = 2617--><!--Device-KEYCODE_AGAIN = 2617-End--> |
| KEYCODE_PROPS = 2618 | Props key<br>**Since**: 22<br><!--Device-KEYCODE_PROPS = 2618--><!--Device-KEYCODE_PROPS = 2618-End--> |
| KEYCODE_UNDO = 2619 | Undo key<br>**Since**: 22<br><!--Device-KEYCODE_UNDO = 2619--><!--Device-KEYCODE_UNDO = 2619-End--> |
| KEYCODE_COPY = 2620 | Copy key<br>**Since**: 22<br><!--Device-KEYCODE_COPY = 2620--><!--Device-KEYCODE_COPY = 2620-End--> |
| KEYCODE_OPEN = 2621 | Open key<br>**Since**: 22<br><!--Device-KEYCODE_OPEN = 2621--><!--Device-KEYCODE_OPEN = 2621-End--> |
| KEYCODE_PASTE = 2622 | Paste key<br>**Since**: 22<br><!--Device-KEYCODE_PASTE = 2622--><!--Device-KEYCODE_PASTE = 2622-End--> |
| KEYCODE_FIND = 2623 | Find key<br>**Since**: 22<br><!--Device-KEYCODE_FIND = 2623--><!--Device-KEYCODE_FIND = 2623-End--> |
| KEYCODE_CUT = 2624 | Cut key<br>**Since**: 22<br><!--Device-KEYCODE_CUT = 2624--><!--Device-KEYCODE_CUT = 2624-End--> |
| KEYCODE_HELP = 2625 | Help key<br>**Since**: 22<br><!--Device-KEYCODE_HELP = 2625--><!--Device-KEYCODE_HELP = 2625-End--> |
| KEYCODE_CALC = 2626 | Calculator special function key, used to launch the calculator application.<br>**Since**: 22<br><!--Device-KEYCODE_CALC = 2626--><!--Device-KEYCODE_CALC = 2626-End--> |
| KEYCODE_FILE = 2627 | File key<br>**Since**: 22<br><!--Device-KEYCODE_FILE = 2627--><!--Device-KEYCODE_FILE = 2627-End--> |
| KEYCODE_BOOKMARKS = 2628 | Bookmarks key<br>**Since**: 22<br><!--Device-KEYCODE_BOOKMARKS = 2628--><!--Device-KEYCODE_BOOKMARKS = 2628-End--> |
| KEYCODE_NEXT = 2629 | Page Down key<br>**Since**: 22<br><!--Device-KEYCODE_NEXT = 2629--><!--Device-KEYCODE_NEXT = 2629-End--> |
| KEYCODE_PLAYPAUSE = 2630 | Media: Play/Pause key<br>Difference between this key and **KEYCODE_MEDIA_PLAY_PAUSE**:<br> **KEYCODE_PLAYPAUSE** is an earlier definition, while **KEYCODE_MEDIA_PLAY_PAUSE** is designed for modern media key devices.<br>**Since**: 22<br><!--Device-KEYCODE_PLAYPAUSE = 2630--><!--Device-KEYCODE_PLAYPAUSE = 2630-End--> |
| KEYCODE_PREVIOUS = 2631 | Page Up key<br>**Since**: 22<br><!--Device-KEYCODE_PREVIOUS = 2631--><!--Device-KEYCODE_PREVIOUS = 2631-End--> |
| KEYCODE_STOPCD = 2632 | Stop CD key<br>**Since**: 22<br><!--Device-KEYCODE_STOPCD = 2632--><!--Device-KEYCODE_STOPCD = 2632-End--> |
| KEYCODE_CONFIG = 2634 | Configuration key<br>**Since**: 22<br><!--Device-KEYCODE_CONFIG = 2634--><!--Device-KEYCODE_CONFIG = 2634-End--> |
| KEYCODE_REFRESH = 2635 | Refresh key<br>**Since**: 22<br><!--Device-KEYCODE_REFRESH = 2635--><!--Device-KEYCODE_REFRESH = 2635-End--> |
| KEYCODE_EXIT = 2636 | Exit key<br>**Since**: 22<br><!--Device-KEYCODE_EXIT = 2636--><!--Device-KEYCODE_EXIT = 2636-End--> |
| KEYCODE_EDIT = 2637 | Edit key<br>**Since**: 22<br><!--Device-KEYCODE_EDIT = 2637--><!--Device-KEYCODE_EDIT = 2637-End--> |
| KEYCODE_SCROLLUP = 2638 | Scroll Up key<br>**Since**: 22<br><!--Device-KEYCODE_SCROLLUP = 2638--><!--Device-KEYCODE_SCROLLUP = 2638-End--> |
| KEYCODE_SCROLLDOWN = 2639 | Scroll Down key<br>**Since**: 22<br><!--Device-KEYCODE_SCROLLDOWN = 2639--><!--Device-KEYCODE_SCROLLDOWN = 2639-End--> |
| KEYCODE_NEW = 2640 | New key<br>**Since**: 22<br><!--Device-KEYCODE_NEW = 2640--><!--Device-KEYCODE_NEW = 2640-End--> |
| KEYCODE_REDO = 2641 | Redo key<br>**Since**: 22<br><!--Device-KEYCODE_REDO = 2641--><!--Device-KEYCODE_REDO = 2641-End--> |
| KEYCODE_CLOSE = 2642 | Close key<br>**Since**: 22<br><!--Device-KEYCODE_CLOSE = 2642--><!--Device-KEYCODE_CLOSE = 2642-End--> |
| KEYCODE_PLAY = 2643 | Play key<br>**Since**: 22<br><!--Device-KEYCODE_PLAY = 2643--><!--Device-KEYCODE_PLAY = 2643-End--> |
| KEYCODE_BASSBOOST = 2644 | Bass Boost key<br>**Since**: 22<br><!--Device-KEYCODE_BASSBOOST = 2644--><!--Device-KEYCODE_BASSBOOST = 2644-End--> |
| KEYCODE_PRINT = 2645 | Print key<br>**Since**: 22<br><!--Device-KEYCODE_PRINT = 2645--><!--Device-KEYCODE_PRINT = 2645-End--> |
| KEYCODE_CHAT = 2646 | Chat key<br>**Since**: 22<br><!--Device-KEYCODE_CHAT = 2646--><!--Device-KEYCODE_CHAT = 2646-End--> |
| KEYCODE_FINANCE = 2647 | Finance key<br>**Since**: 22<br><!--Device-KEYCODE_FINANCE = 2647--><!--Device-KEYCODE_FINANCE = 2647-End--> |
| KEYCODE_CANCEL = 2648 | Cancel key<br>**Since**: 22<br><!--Device-KEYCODE_CANCEL = 2648--><!--Device-KEYCODE_CANCEL = 2648-End--> |
| KEYCODE_KBDILLUM_TOGGLE = 2649 | Keyboard Illumination Toggle key<br>**Since**: 22<br><!--Device-KEYCODE_KBDILLUM_TOGGLE = 2649--><!--Device-KEYCODE_KBDILLUM_TOGGLE = 2649-End--> |
| KEYCODE_KBDILLUM_DOWN = 2650 | Keyboard Illumination Down key<br>**Since**: 22<br><!--Device-KEYCODE_KBDILLUM_DOWN = 2650--><!--Device-KEYCODE_KBDILLUM_DOWN = 2650-End--> |
| KEYCODE_KBDILLUM_UP = 2651 | Keyboard Illumination Up key<br>**Since**: 22<br><!--Device-KEYCODE_KBDILLUM_UP = 2651--><!--Device-KEYCODE_KBDILLUM_UP = 2651-End--> |
| KEYCODE_SEND = 2652 | Send key<br>**Since**: 22<br><!--Device-KEYCODE_SEND = 2652--><!--Device-KEYCODE_SEND = 2652-End--> |
| KEYCODE_REPLY = 2653 | Reply key<br>**Since**: 22<br><!--Device-KEYCODE_REPLY = 2653--><!--Device-KEYCODE_REPLY = 2653-End--> |
| KEYCODE_FORWARDMAIL = 2654 | Forward Mail key<br>**Since**: 22<br><!--Device-KEYCODE_FORWARDMAIL = 2654--><!--Device-KEYCODE_FORWARDMAIL = 2654-End--> |
| KEYCODE_SAVE = 2655 | Save key<br>**Since**: 22<br><!--Device-KEYCODE_SAVE = 2655--><!--Device-KEYCODE_SAVE = 2655-End--> |
| KEYCODE_DOCUMENTS = 2656 | Documents key<br>**Since**: 22<br><!--Device-KEYCODE_DOCUMENTS = 2656--><!--Device-KEYCODE_DOCUMENTS = 2656-End--> |
| KEYCODE_VIDEO_NEXT = 2657 | Next Video key<br>**Since**: 22<br><!--Device-KEYCODE_VIDEO_NEXT = 2657--><!--Device-KEYCODE_VIDEO_NEXT = 2657-End--> |
| KEYCODE_VIDEO_PREV = 2658 | Previous Video key<br>**Since**: 22<br><!--Device-KEYCODE_VIDEO_PREV = 2658--><!--Device-KEYCODE_VIDEO_PREV = 2658-End--> |
| KEYCODE_BRIGHTNESS_CYCLE = 2659 | Brightness Cycle key<br>**Since**: 22<br><!--Device-KEYCODE_BRIGHTNESS_CYCLE = 2659--><!--Device-KEYCODE_BRIGHTNESS_CYCLE = 2659-End--> |
| KEYCODE_BRIGHTNESS_ZERO = 2660 | Brightness Zero key<br>**Since**: 22<br><!--Device-KEYCODE_BRIGHTNESS_ZERO = 2660--><!--Device-KEYCODE_BRIGHTNESS_ZERO = 2660-End--> |
| KEYCODE_DISPLAY_OFF = 2661 | Display Off Key<br>**Since**: 22<br><!--Device-KEYCODE_DISPLAY_OFF = 2661--><!--Device-KEYCODE_DISPLAY_OFF = 2661-End--> |
| KEYCODE_BTN_MISC = 2662 | Misc Button key<br>**Since**: 22<br><!--Device-KEYCODE_BTN_MISC = 2662--><!--Device-KEYCODE_BTN_MISC = 2662-End--> |
| KEYCODE_GOTO = 2663 | Goto key<br>**Since**: 22<br><!--Device-KEYCODE_GOTO = 2663--><!--Device-KEYCODE_GOTO = 2663-End--> |
| KEYCODE_INFO = 2664 | Info key<br>**Since**: 22<br><!--Device-KEYCODE_INFO = 2664--><!--Device-KEYCODE_INFO = 2664-End--> |
| KEYCODE_PROGRAM = 2665 | Program key<br>**Since**: 22<br><!--Device-KEYCODE_PROGRAM = 2665--><!--Device-KEYCODE_PROGRAM = 2665-End--> |
| KEYCODE_PVR = 2666 | PVR key<br>**Since**: 22<br><!--Device-KEYCODE_PVR = 2666--><!--Device-KEYCODE_PVR = 2666-End--> |
| KEYCODE_SUBTITLE = 2667 | Subtitle key<br>**Since**: 22<br><!--Device-KEYCODE_SUBTITLE = 2667--><!--Device-KEYCODE_SUBTITLE = 2667-End--> |
| KEYCODE_FULL_SCREEN = 2668 | Full Screen key<br>**Since**: 22<br><!--Device-KEYCODE_FULL_SCREEN = 2668--><!--Device-KEYCODE_FULL_SCREEN = 2668-End--> |
| KEYCODE_KEYBOARD = 2669 | Keyboard<br>**Since**: 22<br><!--Device-KEYCODE_KEYBOARD = 2669--><!--Device-KEYCODE_KEYBOARD = 2669-End--> |
| KEYCODE_ASPECT_RATIO = 2670 | Aspect Ratio key<br>**Since**: 22<br><!--Device-KEYCODE_ASPECT_RATIO = 2670--><!--Device-KEYCODE_ASPECT_RATIO = 2670-End--> |
| KEYCODE_PC = 2671 | Port Control key<br>**Since**: 22<br><!--Device-KEYCODE_PC = 2671--><!--Device-KEYCODE_PC = 2671-End--> |
| KEYCODE_TV = 2672 | TV key<br>**Since**: 22<br><!--Device-KEYCODE_TV = 2672--><!--Device-KEYCODE_TV = 2672-End--> |
| KEYCODE_TV2 = 2673 | TV key 2<br>**Since**: 22<br><!--Device-KEYCODE_TV2 = 2673--><!--Device-KEYCODE_TV2 = 2673-End--> |
| KEYCODE_VCR = 2674 | VCR key<br>**Since**: 22<br><!--Device-KEYCODE_VCR = 2674--><!--Device-KEYCODE_VCR = 2674-End--> |
| KEYCODE_VCR2 = 2675 | VCR key 2<br>**Since**: 22<br><!--Device-KEYCODE_VCR2 = 2675--><!--Device-KEYCODE_VCR2 = 2675-End--> |
| KEYCODE_SAT = 2676 | SAT key<br>**Since**: 22<br><!--Device-KEYCODE_SAT = 2676--><!--Device-KEYCODE_SAT = 2676-End--> |
| KEYCODE_CD = 2677 | CD key<br>**Since**: 22<br><!--Device-KEYCODE_CD = 2677--><!--Device-KEYCODE_CD = 2677-End--> |
| KEYCODE_TAPE = 2678 | Tape key<br>**Since**: 22<br><!--Device-KEYCODE_TAPE = 2678--><!--Device-KEYCODE_TAPE = 2678-End--> |
| KEYCODE_TUNER = 2679 | Tuner key<br>**Since**: 22<br><!--Device-KEYCODE_TUNER = 2679--><!--Device-KEYCODE_TUNER = 2679-End--> |
| KEYCODE_PLAYER = 2680 | Player key<br>**Since**: 22<br><!--Device-KEYCODE_PLAYER = 2680--><!--Device-KEYCODE_PLAYER = 2680-End--> |
| KEYCODE_DVD = 2681 | DVD key<br>**Since**: 22<br><!--Device-KEYCODE_DVD = 2681--><!--Device-KEYCODE_DVD = 2681-End--> |
| KEYCODE_AUDIO = 2682 | Audio key<br>**Since**: 22<br><!--Device-KEYCODE_AUDIO = 2682--><!--Device-KEYCODE_AUDIO = 2682-End--> |
| KEYCODE_VIDEO = 2683 | Video key<br>**Since**: 22<br><!--Device-KEYCODE_VIDEO = 2683--><!--Device-KEYCODE_VIDEO = 2683-End--> |
| KEYCODE_MEMO = 2684 | Memo key<br>**Since**: 22<br><!--Device-KEYCODE_MEMO = 2684--><!--Device-KEYCODE_MEMO = 2684-End--> |
| KEYCODE_CALENDAR = 2685 | Calendar key<br>**Since**: 22<br><!--Device-KEYCODE_CALENDAR = 2685--><!--Device-KEYCODE_CALENDAR = 2685-End--> |
| KEYCODE_RED = 2686 | Red indicator key<br>**Since**: 22<br><!--Device-KEYCODE_RED = 2686--><!--Device-KEYCODE_RED = 2686-End--> |
| KEYCODE_GREEN = 2687 | Green indicator key<br>**Since**: 22<br><!--Device-KEYCODE_GREEN = 2687--><!--Device-KEYCODE_GREEN = 2687-End--> |
| KEYCODE_YELLOW = 2688 | Yellow indicator key<br>**Since**: 22<br><!--Device-KEYCODE_YELLOW = 2688--><!--Device-KEYCODE_YELLOW = 2688-End--> |
| KEYCODE_BLUE = 2689 | Blue indicator key<br>**Since**: 22<br><!--Device-KEYCODE_BLUE = 2689--><!--Device-KEYCODE_BLUE = 2689-End--> |
| KEYCODE_CHANNELUP = 2690 | Channel Up key<br>**Since**: 22<br><!--Device-KEYCODE_CHANNELUP = 2690--><!--Device-KEYCODE_CHANNELUP = 2690-End--> |
| KEYCODE_CHANNELDOWN = 2691 | Channel Down key<br>**Since**: 22<br><!--Device-KEYCODE_CHANNELDOWN = 2691--><!--Device-KEYCODE_CHANNELDOWN = 2691-End--> |
| KEYCODE_LAST = 2692 | Last key<br>**Since**: 22<br><!--Device-KEYCODE_LAST = 2692--><!--Device-KEYCODE_LAST = 2692-End--> |
| KEYCODE_RESTART = 2693 | Restart key<br>**Since**: 22<br><!--Device-KEYCODE_RESTART = 2693--><!--Device-KEYCODE_RESTART = 2693-End--> |
| KEYCODE_SLOW = 2694 | Slow key<br>**Since**: 22<br><!--Device-KEYCODE_SLOW = 2694--><!--Device-KEYCODE_SLOW = 2694-End--> |
| KEYCODE_SHUFFLE = 2695 | Shuffle key<br>**Since**: 22<br><!--Device-KEYCODE_SHUFFLE = 2695--><!--Device-KEYCODE_SHUFFLE = 2695-End--> |
| KEYCODE_VIDEOPHONE = 2696 | Videophone key<br>**Since**: 22<br><!--Device-KEYCODE_VIDEOPHONE = 2696--><!--Device-KEYCODE_VIDEOPHONE = 2696-End--> |
| KEYCODE_GAMES = 2697 | Games key<br>**Since**: 22<br><!--Device-KEYCODE_GAMES = 2697--><!--Device-KEYCODE_GAMES = 2697-End--> |
| KEYCODE_ZOOMIN = 2698 | Zoom In key<br>**Since**: 22<br><!--Device-KEYCODE_ZOOMIN = 2698--><!--Device-KEYCODE_ZOOMIN = 2698-End--> |
| KEYCODE_ZOOMOUT = 2699 | Zoom Out key<br>**Since**: 22<br><!--Device-KEYCODE_ZOOMOUT = 2699--><!--Device-KEYCODE_ZOOMOUT = 2699-End--> |
| KEYCODE_ZOOMRESET = 2700 | Zoom Reset key<br>**Since**: 22<br><!--Device-KEYCODE_ZOOMRESET = 2700--><!--Device-KEYCODE_ZOOMRESET = 2700-End--> |
| KEYCODE_WORDPROCESSOR = 2701 | Word Processor key<br>**Since**: 22<br><!--Device-KEYCODE_WORDPROCESSOR = 2701--><!--Device-KEYCODE_WORDPROCESSOR = 2701-End--> |
| KEYCODE_EDITOR = 2702 | Editor key<br>**Since**: 22<br><!--Device-KEYCODE_EDITOR = 2702--><!--Device-KEYCODE_EDITOR = 2702-End--> |
| KEYCODE_SPREADSHEET = 2703 | Spreadsheet key<br>**Since**: 22<br><!--Device-KEYCODE_SPREADSHEET = 2703--><!--Device-KEYCODE_SPREADSHEET = 2703-End--> |
| KEYCODE_GRAPHICSEDITOR = 2704 | Graphics Editor key<br>**Since**: 22<br><!--Device-KEYCODE_GRAPHICSEDITOR = 2704--><!--Device-KEYCODE_GRAPHICSEDITOR = 2704-End--> |
| KEYCODE_PRESENTATION = 2705 | Presentation key<br>**Since**: 22<br><!--Device-KEYCODE_PRESENTATION = 2705--><!--Device-KEYCODE_PRESENTATION = 2705-End--> |
| KEYCODE_DATABASE = 2706 | Database key<br>**Since**: 22<br><!--Device-KEYCODE_DATABASE = 2706--><!--Device-KEYCODE_DATABASE = 2706-End--> |
| KEYCODE_NEWS = 2707 | News key<br>**Since**: 22<br><!--Device-KEYCODE_NEWS = 2707--><!--Device-KEYCODE_NEWS = 2707-End--> |
| KEYCODE_VOICEMAIL = 2708 | Voicemail key<br>**Since**: 22<br><!--Device-KEYCODE_VOICEMAIL = 2708--><!--Device-KEYCODE_VOICEMAIL = 2708-End--> |
| KEYCODE_ADDRESSBOOK = 2709 | Address book key<br>**Since**: 22<br><!--Device-KEYCODE_ADDRESSBOOK = 2709--><!--Device-KEYCODE_ADDRESSBOOK = 2709-End--> |
| KEYCODE_MESSENGER = 2710 | Messenger key<br>**Since**: 22<br><!--Device-KEYCODE_MESSENGER = 2710--><!--Device-KEYCODE_MESSENGER = 2710-End--> |
| KEYCODE_BRIGHTNESS_TOGGLE = 2711 | Brightness Toggle key<br>**Since**: 22<br><!--Device-KEYCODE_BRIGHTNESS_TOGGLE = 2711--><!--Device-KEYCODE_BRIGHTNESS_TOGGLE = 2711-End--> |
| KEYCODE_SPELLCHECK = 2712 | Spell Check key<br>**Since**: 22<br><!--Device-KEYCODE_SPELLCHECK = 2712--><!--Device-KEYCODE_SPELLCHECK = 2712-End--> |
| KEYCODE_COFFEE = 2713 | Terminal lock/screen saver key<br>**Since**: 22<br><!--Device-KEYCODE_COFFEE = 2713--><!--Device-KEYCODE_COFFEE = 2713-End--> |
| KEYCODE_MEDIA_REPEAT = 2714 | Media Repeat key<br>**Since**: 22<br><!--Device-KEYCODE_MEDIA_REPEAT = 2714--><!--Device-KEYCODE_MEDIA_REPEAT = 2714-End--> |
| KEYCODE_IMAGES = 2715 | Images key<br>**Since**: 22<br><!--Device-KEYCODE_IMAGES = 2715--><!--Device-KEYCODE_IMAGES = 2715-End--> |
| KEYCODE_BUTTONCONFIG = 2716 | Button Configuration key<br>**Since**: 22<br><!--Device-KEYCODE_BUTTONCONFIG = 2716--><!--Device-KEYCODE_BUTTONCONFIG = 2716-End--> |
| KEYCODE_TASKMANAGER = 2717 | Task manager key<br>**Since**: 22<br><!--Device-KEYCODE_TASKMANAGER = 2717--><!--Device-KEYCODE_TASKMANAGER = 2717-End--> |
| KEYCODE_JOURNAL = 2718 | Log key<br>**Since**: 22<br><!--Device-KEYCODE_JOURNAL = 2718--><!--Device-KEYCODE_JOURNAL = 2718-End--> |
| KEYCODE_CONTROLPANEL = 2719 | Control Panel key<br>**Since**: 22<br><!--Device-KEYCODE_CONTROLPANEL = 2719--><!--Device-KEYCODE_CONTROLPANEL = 2719-End--> |
| KEYCODE_APPSELECT = 2720 | App Select key<br>**Since**: 22<br><!--Device-KEYCODE_APPSELECT = 2720--><!--Device-KEYCODE_APPSELECT = 2720-End--> |
| KEYCODE_SCREENSAVER = 2721 | Screen Saver key<br>**Since**: 22<br><!--Device-KEYCODE_SCREENSAVER = 2721--><!--Device-KEYCODE_SCREENSAVER = 2721-End--> |
| KEYCODE_ASSISTANT = 2722 | Assistant key<br>**Since**: 22<br><!--Device-KEYCODE_ASSISTANT = 2722--><!--Device-KEYCODE_ASSISTANT = 2722-End--> |
| KEYCODE_KBD_LAYOUT_NEXT = 2723 | Next Keyboard Layout key<br>**Since**: 22<br><!--Device-KEYCODE_KBD_LAYOUT_NEXT = 2723--><!--Device-KEYCODE_KBD_LAYOUT_NEXT = 2723-End--> |
| KEYCODE_BRIGHTNESS_MIN = 2724 | Min Brightness key<br>**Since**: 22<br><!--Device-KEYCODE_BRIGHTNESS_MIN = 2724--><!--Device-KEYCODE_BRIGHTNESS_MIN = 2724-End--> |
| KEYCODE_BRIGHTNESS_MAX = 2725 | Max Brightness key<br>**Since**: 22<br><!--Device-KEYCODE_BRIGHTNESS_MAX = 2725--><!--Device-KEYCODE_BRIGHTNESS_MAX = 2725-End--> |
| KEYCODE_KBDINPUTASSIST_PREV = 2726 | Keyboard Input Assist_Previous, used to view input method input history.<br>**Since**: 22<br><!--Device-KEYCODE_KBDINPUTASSIST_PREV = 2726--><!--Device-KEYCODE_KBDINPUTASSIST_PREV = 2726-End--> |
| KEYCODE_KBDINPUTASSIST_NEXT = 2727 | Keyboard Input Assist_Next, used to view input method input extensions.<br>**Since**: 22<br><!--Device-KEYCODE_KBDINPUTASSIST_NEXT = 2727--><!--Device-KEYCODE_KBDINPUTASSIST_NEXT = 2727-End--> |
| KEYCODE_KBDINPUTASSIST_PREVGROUP = 2728 | Keyboard Input Assist_Previous, used to switch to the previous input method in the input group.<br>**Since**: 22<br><!--Device-KEYCODE_KBDINPUTASSIST_PREVGROUP = 2728--><!--Device-KEYCODE_KBDINPUTASSIST_PREVGROUP = 2728-End--> |
| KEYCODE_KBDINPUTASSIST_NEXTGROUP = 2729 | Keyboard Input Assist_Next, used to switch to the next input method in the input group.<br>**Since**: 22<br><!--Device-KEYCODE_KBDINPUTASSIST_NEXTGROUP = 2729--><!--Device-KEYCODE_KBDINPUTASSIST_NEXTGROUP = 2729-End--> |
| KEYCODE_KBDINPUTASSIST_ACCEPT = 2730 | Keyboard Input-assisted Accept key<br>**Since**: 22<br><!--Device-KEYCODE_KBDINPUTASSIST_ACCEPT = 2730--><!--Device-KEYCODE_KBDINPUTASSIST_ACCEPT = 2730-End--> |
| KEYCODE_KBDINPUTASSIST_CANCEL = 2731 | Keyboard Input-assisted Cancel key<br>**Since**: 22<br><!--Device-KEYCODE_KBDINPUTASSIST_CANCEL = 2731--><!--Device-KEYCODE_KBDINPUTASSIST_CANCEL = 2731-End--> |
| KEYCODE_MOUSE_ASSISTANT = 2732 | Mouse AI Assistant key<br>**Since**: 26.0.0<br><!--Device-KEYCODE_MOUSE_ASSISTANT = 2732--><!--Device-KEYCODE_MOUSE_ASSISTANT = 2732-End--> |
| KEYCODE_MOUSE_INTELLIGENCE_SELECTION = 2733 | Mouse Smart Selection key<br>**Since**: 26.0.0<br><!--Device-KEYCODE_MOUSE_INTELLIGENCE_SELECTION = 2733--><!--Device-KEYCODE_MOUSE_INTELLIGENCE_SELECTION = 2733-End--> |
| KEYCODE_AOD_SINGLE_CLICK = 2740 | Phone touchscreen single-click event, used in Always-On Display state.<br>**Since**: 26.0.0<br><!--Device-KEYCODE_AOD_SINGLE_CLICK = 2740--><!--Device-KEYCODE_AOD_SINGLE_CLICK = 2740-End--> |
| KEYCODE_FRONT = 2800 | Windshield defogger switch key<br>**Since**: 22<br><!--Device-KEYCODE_FRONT = 2800--><!--Device-KEYCODE_FRONT = 2800-End--> |
| KEYCODE_SETUP = 2801 | Setup key<br>**Since**: 22<br><!--Device-KEYCODE_SETUP = 2801--><!--Device-KEYCODE_SETUP = 2801-End--> |
| KEYCODE_WAKEUP = 2802 | Wakeup key<br>**Since**: 22<br><!--Device-KEYCODE_WAKEUP = 2802--><!--Device-KEYCODE_WAKEUP = 2802-End--> |
| KEYCODE_SENDFILE = 2803 | Send File key<br>**Since**: 22<br><!--Device-KEYCODE_SENDFILE = 2803--><!--Device-KEYCODE_SENDFILE = 2803-End--> |
| KEYCODE_DELETEFILE = 2804 | Delete File key<br>**Since**: 22<br><!--Device-KEYCODE_DELETEFILE = 2804--><!--Device-KEYCODE_DELETEFILE = 2804-End--> |
| KEYCODE_XFER = 2805 | XFER key, which is used to start file transfer<br>**Since**: 22<br><!--Device-KEYCODE_XFER = 2805--><!--Device-KEYCODE_XFER = 2805-End--> |
| KEYCODE_PROG1 = 2806 | Program key 1<br>**Since**: 22<br><!--Device-KEYCODE_PROG1 = 2806--><!--Device-KEYCODE_PROG1 = 2806-End--> |
| KEYCODE_PROG2 = 2807 | Program key 2<br>**Since**: 22<br><!--Device-KEYCODE_PROG2 = 2807--><!--Device-KEYCODE_PROG2 = 2807-End--> |
| KEYCODE_MSDOS = 2808 | DOS key<br>**Since**: 22<br><!--Device-KEYCODE_MSDOS = 2808--><!--Device-KEYCODE_MSDOS = 2808-End--> |
| KEYCODE_SCREENLOCK = 2809 | Screen Lock key<br>**Since**: 22<br><!--Device-KEYCODE_SCREENLOCK = 2809--><!--Device-KEYCODE_SCREENLOCK = 2809-End--> |
| KEYCODE_DIRECTION_ROTATE_DISPLAY = 2810 | Directional Rotation Display key<br>**Since**: 22<br><!--Device-KEYCODE_DIRECTION_ROTATE_DISPLAY = 2810--><!--Device-KEYCODE_DIRECTION_ROTATE_DISPLAY = 2810-End--> |
| KEYCODE_CYCLEWINDOWS = 2811 | Window Cycle key<br>**Since**: 22<br><!--Device-KEYCODE_CYCLEWINDOWS = 2811--><!--Device-KEYCODE_CYCLEWINDOWS = 2811-End--> |
| KEYCODE_COMPUTER = 2812 | Computer key<br>**Since**: 22<br><!--Device-KEYCODE_COMPUTER = 2812--><!--Device-KEYCODE_COMPUTER = 2812-End--> |
| KEYCODE_EJECTCLOSECD = 2813 | Eject CD key<br>**Since**: 22<br><!--Device-KEYCODE_EJECTCLOSECD = 2813--><!--Device-KEYCODE_EJECTCLOSECD = 2813-End--> |
| KEYCODE_ISO = 2814 | ISO key<br>**Since**: 22<br><!--Device-KEYCODE_ISO = 2814--><!--Device-KEYCODE_ISO = 2814-End--> |
| KEYCODE_MOVE = 2815 | Move key<br>**Since**: 22<br><!--Device-KEYCODE_MOVE = 2815--><!--Device-KEYCODE_MOVE = 2815-End--> |
| KEYCODE_F13 = 2816 | F13 key<br>**Since**: 22<br><!--Device-KEYCODE_F13 = 2816--><!--Device-KEYCODE_F13 = 2816-End--> |
| KEYCODE_F14 = 2817 | F14 key<br>**Since**: 22<br><!--Device-KEYCODE_F14 = 2817--><!--Device-KEYCODE_F14 = 2817-End--> |
| KEYCODE_F15 = 2818 | F15 key<br>**Since**: 22<br><!--Device-KEYCODE_F15 = 2818--><!--Device-KEYCODE_F15 = 2818-End--> |
| KEYCODE_F16 = 2819 | F16 key<br>**Since**: 22<br><!--Device-KEYCODE_F16 = 2819--><!--Device-KEYCODE_F16 = 2819-End--> |
| KEYCODE_F17 = 2820 | F17 key<br>**Since**: 22<br><!--Device-KEYCODE_F17 = 2820--><!--Device-KEYCODE_F17 = 2820-End--> |
| KEYCODE_F18 = 2821 | F18 key<br>**Since**: 22<br><!--Device-KEYCODE_F18 = 2821--><!--Device-KEYCODE_F18 = 2821-End--> |
| KEYCODE_F19 = 2822 | F19 key<br>**Since**: 22<br><!--Device-KEYCODE_F19 = 2822--><!--Device-KEYCODE_F19 = 2822-End--> |
| KEYCODE_F20 = 2823 | F20 key<br>**Since**: 22<br><!--Device-KEYCODE_F20 = 2823--><!--Device-KEYCODE_F20 = 2823-End--> |
| KEYCODE_F21 = 2824 | F21 key<br>**Since**: 22<br><!--Device-KEYCODE_F21 = 2824--><!--Device-KEYCODE_F21 = 2824-End--> |
| KEYCODE_F22 = 2825 | F22 key<br>**Since**: 22<br><!--Device-KEYCODE_F22 = 2825--><!--Device-KEYCODE_F22 = 2825-End--> |
| KEYCODE_F23 = 2826 | F23 key<br>**Since**: 22<br><!--Device-KEYCODE_F23 = 2826--><!--Device-KEYCODE_F23 = 2826-End--> |
| KEYCODE_F24 = 2827 | F24 key<br>**Since**: 22<br><!--Device-KEYCODE_F24 = 2827--><!--Device-KEYCODE_F24 = 2827-End--> |
| KEYCODE_PROG3 = 2828 | Program key 3<br>**Since**: 22<br><!--Device-KEYCODE_PROG3 = 2828--><!--Device-KEYCODE_PROG3 = 2828-End--> |
| KEYCODE_PROG4 = 2829 | Program key 4<br>**Since**: 22<br><!--Device-KEYCODE_PROG4 = 2829--><!--Device-KEYCODE_PROG4 = 2829-End--> |
| KEYCODE_DASHBOARD = 2830 | Dashboard key<br>**Since**: 22<br><!--Device-KEYCODE_DASHBOARD = 2830--><!--Device-KEYCODE_DASHBOARD = 2830-End--> |
| KEYCODE_SUSPEND = 2831 | Suspend key<br>**Since**: 22<br><!--Device-KEYCODE_SUSPEND = 2831--><!--Device-KEYCODE_SUSPEND = 2831-End--> |
| KEYCODE_HP = 2832 | HP key<br>**Since**: 22<br><!--Device-KEYCODE_HP = 2832--><!--Device-KEYCODE_HP = 2832-End--> |
| KEYCODE_SOUND = 2833 | Sound key<br>**Since**: 22<br><!--Device-KEYCODE_SOUND = 2833--><!--Device-KEYCODE_SOUND = 2833-End--> |
| KEYCODE_QUESTION = 2834 | Question key<br>**Since**: 22<br><!--Device-KEYCODE_QUESTION = 2834--><!--Device-KEYCODE_QUESTION = 2834-End--> |
| KEYCODE_CONNECT = 2836 | Connect key<br>**Since**: 22<br><!--Device-KEYCODE_CONNECT = 2836--><!--Device-KEYCODE_CONNECT = 2836-End--> |
| KEYCODE_SPORT = 2837 | Sport key<br>**Since**: 22<br><!--Device-KEYCODE_SPORT = 2837--><!--Device-KEYCODE_SPORT = 2837-End--> |
| KEYCODE_SHOP = 2838 | Shop key<br>**Since**: 22<br><!--Device-KEYCODE_SHOP = 2838--><!--Device-KEYCODE_SHOP = 2838-End--> |
| KEYCODE_ALTERASE = 2839 | Alternate key<br>**Since**: 22<br><!--Device-KEYCODE_ALTERASE = 2839--><!--Device-KEYCODE_ALTERASE = 2839-End--> |
| KEYCODE_SWITCHVIDEOMODE = 2841 | Cycle output between available videos (monitor/LCD/TV output/more)<br>**Since**: 22<br><!--Device-KEYCODE_SWITCHVIDEOMODE = 2841--><!--Device-KEYCODE_SWITCHVIDEOMODE = 2841-End--> |
| KEYCODE_BATTERY = 2842 | Battery key<br>**Since**: 22<br><!--Device-KEYCODE_BATTERY = 2842--><!--Device-KEYCODE_BATTERY = 2842-End--> |
| KEYCODE_BLUETOOTH = 2843 | Bluetooth key<br>**Since**: 22<br><!--Device-KEYCODE_BLUETOOTH = 2843--><!--Device-KEYCODE_BLUETOOTH = 2843-End--> |
| KEYCODE_WLAN = 2844 | WLAN key<br>**Since**: 22<br><!--Device-KEYCODE_WLAN = 2844--><!--Device-KEYCODE_WLAN = 2844-End--> |
| KEYCODE_UWB = 2845 | Ultra-wideband key<br>**Since**: 22<br><!--Device-KEYCODE_UWB = 2845--><!--Device-KEYCODE_UWB = 2845-End--> |
| KEYCODE_WWAN_WIMAX = 2846 | Mobile Network Control key<br>**Since**: 22<br><!--Device-KEYCODE_WWAN_WIMAX = 2846--><!--Device-KEYCODE_WWAN_WIMAX = 2846-End--> |
| KEYCODE_RFKILL = 2847 | Key for controlling all wireless devices<br>**Since**: 22<br><!--Device-KEYCODE_RFKILL = 2847--><!--Device-KEYCODE_RFKILL = 2847-End--> |
| KEYCODE_CHANNEL = 3001 | Channel key<br>**Since**: 22<br><!--Device-KEYCODE_CHANNEL = 3001--><!--Device-KEYCODE_CHANNEL = 3001-End--> |
| KEYCODE_BTN_0 = 3100 | Button '0'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_0 = 3100--><!--Device-KEYCODE_BTN_0 = 3100-End--> |
| KEYCODE_BTN_1 = 3101 | Button '1'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_1 = 3101--><!--Device-KEYCODE_BTN_1 = 3101-End--> |
| KEYCODE_BTN_2 = 3102 | Button '2'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_2 = 3102--><!--Device-KEYCODE_BTN_2 = 3102-End--> |
| KEYCODE_BTN_3 = 3103 | Button '3'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_3 = 3103--><!--Device-KEYCODE_BTN_3 = 3103-End--> |
| KEYCODE_BTN_4 = 3104 | Button '4'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_4 = 3104--><!--Device-KEYCODE_BTN_4 = 3104-End--> |
| KEYCODE_BTN_5 = 3105 | Button '5'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_5 = 3105--><!--Device-KEYCODE_BTN_5 = 3105-End--> |
| KEYCODE_BTN_6 = 3106 | Button '6'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_6 = 3106--><!--Device-KEYCODE_BTN_6 = 3106-End--> |
| KEYCODE_BTN_7 = 3107 | Button '7'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_7 = 3107--><!--Device-KEYCODE_BTN_7 = 3107-End--> |
| KEYCODE_BTN_8 = 3108 | Button '8'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_8 = 3108--><!--Device-KEYCODE_BTN_8 = 3108-End--> |
| KEYCODE_BTN_9 = 3109 | Button '9'<br>**Since**: 22<br><!--Device-KEYCODE_BTN_9 = 3109--><!--Device-KEYCODE_BTN_9 = 3109-End--> |
| KEYCODE_DAGGER_CLICK = 3211 | Single tapping the smart watch's X-TAP sensor<br>**Since**: 22<br><!--Device-KEYCODE_DAGGER_CLICK = 3211--><!--Device-KEYCODE_DAGGER_CLICK = 3211-End--> |
| KEYCODE_DAGGER_DOUBLE_CLICK = 3212 | Double tapping the smart watch's X-TAP sensor<br>**Since**: 22<br><!--Device-KEYCODE_DAGGER_DOUBLE_CLICK = 3212--><!--Device-KEYCODE_DAGGER_DOUBLE_CLICK = 3212-End--> |
| KEYCODE_DAGGER_LONG_PRESS = 3213 | Long-pressing the smart watch's X-TAP sensor<br>**Since**: 22<br><!--Device-KEYCODE_DAGGER_LONG_PRESS = 3213--><!--Device-KEYCODE_DAGGER_LONG_PRESS = 3213-End--> |
| KEYCODE_DIV = 3220 | Left button of the smart watch<br>**Since**: 22<br><!--Device-KEYCODE_DIV = 3220--><!--Device-KEYCODE_DIV = 3220-End--> |
| KEYCODE_XKEY = 3232 | Custom Shortcut Keys<br>**Since**: 26.0.0<br><!--Device-KEYCODE_XKEY = 3232--><!--Device-KEYCODE_XKEY = 3232-End--> |
| KEYCODE_FINGERPRINT_SLIDE_UP = 3233 | Smart control Key slide-up<br>**Since**: 26.0.0<br><!--Device-KEYCODE_FINGERPRINT_SLIDE_UP = 3233--><!--Device-KEYCODE_FINGERPRINT_SLIDE_UP = 3233-End--> |
| KEYCODE_FINGERPRINT_SLIDE_DOWN = 3234 | Smart control Key slide-down<br>**Since**: 26.0.0<br><!--Device-KEYCODE_FINGERPRINT_SLIDE_DOWN = 3234--><!--Device-KEYCODE_FINGERPRINT_SLIDE_DOWN = 3234-End--> |
| OH_INPUT_KEYCODE_PTZ_CLICK = 3235 | PTZ click<br>**Since**: 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_CLICK = 3235--><!--Device-OH_INPUT_KEYCODE_PTZ_CLICK = 3235-End--> |
| OH_INPUT_KEYCODE_PTZ_FOCUS_LEFT = 3236 | PTZ focus left<br>**Since**: 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_FOCUS_LEFT = 3236--><!--Device-OH_INPUT_KEYCODE_PTZ_FOCUS_LEFT = 3236-End--> |
| OH_INPUT_KEYCODE_PTZ_FOCUS_RIGHT = 3237 | PTZ focus right<br>**Since**: 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_FOCUS_RIGHT = 3237--><!--Device-OH_INPUT_KEYCODE_PTZ_FOCUS_RIGHT = 3237-End--> |
| OH_INPUT_KEYCODE_PTZ_EXPOSURE_LEFT = 3238 | PTZ exposure left<br>**Since**: 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_EXPOSURE_LEFT = 3238--><!--Device-OH_INPUT_KEYCODE_PTZ_EXPOSURE_LEFT = 3238-End--> |
| OH_INPUT_KEYCODE_PTZ_EXPOSURE_RIGHT = 3239 | PTZ exposure right<br>**Since**: 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_EXPOSURE_RIGHT = 3239--><!--Device-OH_INPUT_KEYCODE_PTZ_EXPOSURE_RIGHT = 3239-End--> |
| OH_INPUT_KEYCODE_PTZ_SHUTTER_LEFT = 3240 | PTZ shutter left<br>**Since**: 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_SHUTTER_LEFT = 3240--><!--Device-OH_INPUT_KEYCODE_PTZ_SHUTTER_LEFT = 3240-End--> |
| OH_INPUT_KEYCODE_PTZ_SHUTTER_RIGHT = 3241 | PTZ shutter right<br>**Since**: 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_SHUTTER_RIGHT = 3241--><!--Device-OH_INPUT_KEYCODE_PTZ_SHUTTER_RIGHT = 3241-End--> |
| OH_INPUT_KEYCODE_PTZ_APERTURE_LEFT = 3242 | PTZ aperture left<br>**Since**: 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_APERTURE_LEFT = 3242--><!--Device-OH_INPUT_KEYCODE_PTZ_APERTURE_LEFT = 3242-End--> |
| OH_INPUT_KEYCODE_PTZ_APERTURE_RIGHT = 3243 | PTZ aperture right<br>**Since**: 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_APERTURE_RIGHT = 3243--><!--Device-OH_INPUT_KEYCODE_PTZ_APERTURE_RIGHT = 3243-End--> |
| OH_INPUT_KEYCODE_DESKTOP = 3245 | Return to desktop<br>**Since**: 26.1.0<br><!--Device-OH_INPUT_KEYCODE_DESKTOP = 3245--><!--Device-OH_INPUT_KEYCODE_DESKTOP = 3245-End--> |


