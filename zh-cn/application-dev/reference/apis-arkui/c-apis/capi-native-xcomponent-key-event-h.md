# native_xcomponent_key_event.h

## 概述

声明用于访问Native XComponent按键事件所使用到的枚举类型。

**引用文件：** <ace/xcomponent/native_xcomponent_key_event.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 10

**相关模块：** [OH_NativeXComponent Native XComponent](capi-arkui-oh-nativexcomponent-native-xcomponent.md)

**相关示例：** [NativeXComponentSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeXComponentSample)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_NativeXComponent_KeyCode](#oh_nativexcomponent_keycode) | OH_NativeXComponent_KeyCode | 按键事件的键码。 |
| [OH_NativeXComponent_KeyAction](#oh_nativexcomponent_keyaction) | OH_NativeXComponent_KeyAction | 按键事件动作。 |

## 枚举类型说明

### OH_NativeXComponent_KeyCode

```c
enum OH_NativeXComponent_KeyCode
```

**描述：**

按键事件的键码。

<!--Device-enum OH_NativeXComponent_KeyCode--><!--Device-enum OH_NativeXComponent_KeyCode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| KEY_UNKNOWN = -1 | 未知按键。<br><!--Device-KEY_UNKNOWN = -1--><!--Device-KEY_UNKNOWN = -1-End--> |
| KEY_FN = 0 | 功能（Fn）键。<br><!--Device-KEY_FN = 0--><!--Device-KEY_FN = 0-End--> |
| KEY_HOME = 1 | 功能（Home）键。<br><!--Device-KEY_HOME = 1--><!--Device-KEY_HOME = 1-End--> |
| KEY_BACK = 2 | 返回键。<br><!--Device-KEY_BACK = 2--><!--Device-KEY_BACK = 2-End--> |
| KEY_MEDIA_PLAY_PAUSE = 10 | 多媒体键，播放/暂停。<br><!--Device-KEY_MEDIA_PLAY_PAUSE = 10--><!--Device-KEY_MEDIA_PLAY_PAUSE = 10-End--> |
| KEY_MEDIA_STOP = 11 | 多媒体键，停止。<br><!--Device-KEY_MEDIA_STOP = 11--><!--Device-KEY_MEDIA_STOP = 11-End--> |
| KEY_MEDIA_NEXT = 12 | 多媒体键，下一首。<br><!--Device-KEY_MEDIA_NEXT = 12--><!--Device-KEY_MEDIA_NEXT = 12-End--> |
| KEY_MEDIA_PREVIOUS = 13 | 多媒体键，上一首。<br><!--Device-KEY_MEDIA_PREVIOUS = 13--><!--Device-KEY_MEDIA_PREVIOUS = 13-End--> |
| KEY_MEDIA_REWIND = 14 | 多媒体键，快退。<br><!--Device-KEY_MEDIA_REWIND = 14--><!--Device-KEY_MEDIA_REWIND = 14-End--> |
| KEY_MEDIA_FAST_FORWARD = 15 | 多媒体键，快进。<br><!--Device-KEY_MEDIA_FAST_FORWARD = 15--><!--Device-KEY_MEDIA_FAST_FORWARD = 15-End--> |
| KEY_VOLUME_UP = 16 | 音量增加键。<br><!--Device-KEY_VOLUME_UP = 16--><!--Device-KEY_VOLUME_UP = 16-End--> |
| KEY_VOLUME_DOWN = 17 | 音量减小键。<br><!--Device-KEY_VOLUME_DOWN = 17--><!--Device-KEY_VOLUME_DOWN = 17-End--> |
| KEY_POWER = 18 | 电源键。<br><!--Device-KEY_POWER = 18--><!--Device-KEY_POWER = 18-End--> |
| KEY_CAMERA = 19 | 拍照键。<br><!--Device-KEY_CAMERA = 19--><!--Device-KEY_CAMERA = 19-End--> |
| KEY_VOLUME_MUTE = 22 | 扬声器静音键。<br><!--Device-KEY_VOLUME_MUTE = 22--><!--Device-KEY_VOLUME_MUTE = 22-End--> |
| KEY_MUTE = 23 | 话筒静音键。<br><!--Device-KEY_MUTE = 23--><!--Device-KEY_MUTE = 23-End--> |
| KEY_BRIGHTNESS_UP = 40 | 亮度调节按键，调亮。<br><!--Device-KEY_BRIGHTNESS_UP = 40--><!--Device-KEY_BRIGHTNESS_UP = 40-End--> |
| KEY_BRIGHTNESS_DOWN = 41 | 亮度调节按键，调暗。<br><!--Device-KEY_BRIGHTNESS_DOWN = 41--><!--Device-KEY_BRIGHTNESS_DOWN = 41-End--> |
| KEY_0 = 2000 | 按键'0'。<br><!--Device-KEY_0 = 2000--><!--Device-KEY_0 = 2000-End--> |
| KEY_1 = 2001 | 按键'1'。<br><!--Device-KEY_1 = 2001--><!--Device-KEY_1 = 2001-End--> |
| KEY_2 = 2002 | 按键'2'。<br><!--Device-KEY_2 = 2002--><!--Device-KEY_2 = 2002-End--> |
| KEY_3 = 2003 | 按键'3'。<br><!--Device-KEY_3 = 2003--><!--Device-KEY_3 = 2003-End--> |
| KEY_4 = 2004 | 按键'4'。<br><!--Device-KEY_4 = 2004--><!--Device-KEY_4 = 2004-End--> |
| KEY_5 = 2005 | 按键'5'。<br><!--Device-KEY_5 = 2005--><!--Device-KEY_5 = 2005-End--> |
| KEY_6 = 2006 | 按键'6'。<br><!--Device-KEY_6 = 2006--><!--Device-KEY_6 = 2006-End--> |
| KEY_7 = 2007 | 按键'7'。<br><!--Device-KEY_7 = 2007--><!--Device-KEY_7 = 2007-End--> |
| KEY_8 = 2008 | 按键'8'。<br><!--Device-KEY_8 = 2008--><!--Device-KEY_8 = 2008-End--> |
| KEY_9 = 2009 | 按键'9'。<br><!--Device-KEY_9 = 2009--><!--Device-KEY_9 = 2009-End--> |
| KEY_STAR = 2010 | 按键'*'。<br><!--Device-KEY_STAR = 2010--><!--Device-KEY_STAR = 2010-End--> |
| KEY_POUND = 2011 | 按键'#'。<br><!--Device-KEY_POUND = 2011--><!--Device-KEY_POUND = 2011-End--> |
| KEY_DPAD_UP = 2012 | 导航键，向上。<br><!--Device-KEY_DPAD_UP = 2012--><!--Device-KEY_DPAD_UP = 2012-End--> |
| KEY_DPAD_DOWN = 2013 | 导航键，向下。<br><!--Device-KEY_DPAD_DOWN = 2013--><!--Device-KEY_DPAD_DOWN = 2013-End--> |
| KEY_DPAD_LEFT = 2014 | 导航键，向左。<br><!--Device-KEY_DPAD_LEFT = 2014--><!--Device-KEY_DPAD_LEFT = 2014-End--> |
| KEY_DPAD_RIGHT = 2015 | 导航键，向右。<br><!--Device-KEY_DPAD_RIGHT = 2015--><!--Device-KEY_DPAD_RIGHT = 2015-End--> |
| KEY_DPAD_CENTER = 2016 | 导航键，确定键。<br><!--Device-KEY_DPAD_CENTER = 2016--><!--Device-KEY_DPAD_CENTER = 2016-End--> |
| KEY_A = 2017 | 按键'A'。<br><!--Device-KEY_A = 2017--><!--Device-KEY_A = 2017-End--> |
| KEY_B = 2018 | 按键'B'。<br><!--Device-KEY_B = 2018--><!--Device-KEY_B = 2018-End--> |
| KEY_C = 2019 | 按键'C'。<br><!--Device-KEY_C = 2019--><!--Device-KEY_C = 2019-End--> |
| KEY_D = 2020 | 按键'D'。<br><!--Device-KEY_D = 2020--><!--Device-KEY_D = 2020-End--> |
| KEY_E = 2021 | 按键'E'。<br><!--Device-KEY_E = 2021--><!--Device-KEY_E = 2021-End--> |
| KEY_F = 2022 | 按键'F'。<br><!--Device-KEY_F = 2022--><!--Device-KEY_F = 2022-End--> |
| KEY_G = 2023 | 按键'G'。<br><!--Device-KEY_G = 2023--><!--Device-KEY_G = 2023-End--> |
| KEY_H = 2024 | 按键'H'。<br><!--Device-KEY_H = 2024--><!--Device-KEY_H = 2024-End--> |
| KEY_I = 2025 | 按键'I'。<br><!--Device-KEY_I = 2025--><!--Device-KEY_I = 2025-End--> |
| KEY_J = 2026 | 按键'J'。<br><!--Device-KEY_J = 2026--><!--Device-KEY_J = 2026-End--> |
| KEY_K = 2027 | 按键'K'。<br><!--Device-KEY_K = 2027--><!--Device-KEY_K = 2027-End--> |
| KEY_L = 2028 | 按键'L'。<br><!--Device-KEY_L = 2028--><!--Device-KEY_L = 2028-End--> |
| KEY_M = 2029 | 按键'M'。<br><!--Device-KEY_M = 2029--><!--Device-KEY_M = 2029-End--> |
| KEY_N = 2030 | 按键'N'。<br><!--Device-KEY_N = 2030--><!--Device-KEY_N = 2030-End--> |
| KEY_O = 2031 | 按键'O'。<br><!--Device-KEY_O = 2031--><!--Device-KEY_O = 2031-End--> |
| KEY_P = 2032 | 按键'P'。<br><!--Device-KEY_P = 2032--><!--Device-KEY_P = 2032-End--> |
| KEY_Q = 2033 | 按键'Q'。<br><!--Device-KEY_Q = 2033--><!--Device-KEY_Q = 2033-End--> |
| KEY_R = 2034 | 按键'R'。<br><!--Device-KEY_R = 2034--><!--Device-KEY_R = 2034-End--> |
| KEY_S = 2035 | 按键'S'。<br><!--Device-KEY_S = 2035--><!--Device-KEY_S = 2035-End--> |
| KEY_T = 2036 | 按键'T'。<br><!--Device-KEY_T = 2036--><!--Device-KEY_T = 2036-End--> |
| KEY_U = 2037 | 按键'U'。<br><!--Device-KEY_U = 2037--><!--Device-KEY_U = 2037-End--> |
| KEY_V = 2038 | 按键'V'。<br><!--Device-KEY_V = 2038--><!--Device-KEY_V = 2038-End--> |
| KEY_W = 2039 | 按键'W'。<br><!--Device-KEY_W = 2039--><!--Device-KEY_W = 2039-End--> |
| KEY_X = 2040 | 按键'X'。<br><!--Device-KEY_X = 2040--><!--Device-KEY_X = 2040-End--> |
| KEY_Y = 2041 | 按键'Y'。<br><!--Device-KEY_Y = 2041--><!--Device-KEY_Y = 2041-End--> |
| KEY_Z = 2042 | 按键'Z'。<br><!--Device-KEY_Z = 2042--><!--Device-KEY_Z = 2042-End--> |
| KEY_COMMA = 2043 | 按键','。<br><!--Device-KEY_COMMA = 2043--><!--Device-KEY_COMMA = 2043-End--> |
| KEY_PERIOD = 2044 | 按键'.'。<br><!--Device-KEY_PERIOD = 2044--><!--Device-KEY_PERIOD = 2044-End--> |
| KEY_ALT_LEFT = 2045 | 左Alt键。<br><!--Device-KEY_ALT_LEFT = 2045--><!--Device-KEY_ALT_LEFT = 2045-End--> |
| KEY_ALT_RIGHT = 2046 | 右Alt键。<br><!--Device-KEY_ALT_RIGHT = 2046--><!--Device-KEY_ALT_RIGHT = 2046-End--> |
| KEY_SHIFT_LEFT = 2047 | 左Shift键。<br><!--Device-KEY_SHIFT_LEFT = 2047--><!--Device-KEY_SHIFT_LEFT = 2047-End--> |
| KEY_SHIFT_RIGHT = 2048 | 右Shift键。<br><!--Device-KEY_SHIFT_RIGHT = 2048--><!--Device-KEY_SHIFT_RIGHT = 2048-End--> |
| KEY_TAB = 2049 | Tab键。<br><!--Device-KEY_TAB = 2049--><!--Device-KEY_TAB = 2049-End--> |
| KEY_SPACE = 2050 | 空格键。<br><!--Device-KEY_SPACE = 2050--><!--Device-KEY_SPACE = 2050-End--> |
| KEY_SYM = 2051 | 符号修改器按键。<br><!--Device-KEY_SYM = 2051--><!--Device-KEY_SYM = 2051-End--> |
| KEY_EXPLORER = 2052 | 浏览器功能键，用于启动浏览器应用程序。<br><!--Device-KEY_EXPLORER = 2052--><!--Device-KEY_EXPLORER = 2052-End--> |
| KEY_ENVELOPE = 2053 | 电子邮件功能键，用于启动电子邮件应用程序。<br><!--Device-KEY_ENVELOPE = 2053--><!--Device-KEY_ENVELOPE = 2053-End--> |
| KEY_ENTER = 2054 | 回车键。<br><!--Device-KEY_ENTER = 2054--><!--Device-KEY_ENTER = 2054-End--> |
| KEY_DEL = 2055 | 退格键。<br><!--Device-KEY_DEL = 2055--><!--Device-KEY_DEL = 2055-End--> |
| KEY_GRAVE = 2056 | 按键'`'。<br><!--Device-KEY_GRAVE = 2056--><!--Device-KEY_GRAVE = 2056-End--> |
| KEY_MINUS = 2057 | 按键'-'。<br><!--Device-KEY_MINUS = 2057--><!--Device-KEY_MINUS = 2057-End--> |
| KEY_EQUALS = 2058 | 按键'='。<br><!--Device-KEY_EQUALS = 2058--><!--Device-KEY_EQUALS = 2058-End--> |
| KEY_LEFT_BRACKET = 2059 | 按键'['。<br><!--Device-KEY_LEFT_BRACKET = 2059--><!--Device-KEY_LEFT_BRACKET = 2059-End--> |
| KEY_RIGHT_BRACKET = 2060 | 按键']'。<br><!--Device-KEY_RIGHT_BRACKET = 2060--><!--Device-KEY_RIGHT_BRACKET = 2060-End--> |
| KEY_BACKSLASH = 2061 | 按键'\\'。<br><!--Device-KEY_BACKSLASH = 2061--><!--Device-KEY_BACKSLASH = 2061-End--> |
| KEY_SEMICOLON = 2062 | 按键';'。<br><!--Device-KEY_SEMICOLON = 2062--><!--Device-KEY_SEMICOLON = 2062-End--> |
| KEY_APOSTROPHE = 2063 | 按键'''（单引号）。<br><!--Device-KEY_APOSTROPHE = 2063--><!--Device-KEY_APOSTROPHE = 2063-End--> |
| KEY_SLASH = 2064 | 按键'/'。<br><!--Device-KEY_SLASH = 2064--><!--Device-KEY_SLASH = 2064-End--> |
| KEY_AT = 2065 | 按键'@'。<br><!--Device-KEY_AT = 2065--><!--Device-KEY_AT = 2065-End--> |
| KEY_PLUS = 2066 | 按键'+'。<br><!--Device-KEY_PLUS = 2066--><!--Device-KEY_PLUS = 2066-End--> |
| KEY_MENU = 2067 | 菜单键。<br><!--Device-KEY_MENU = 2067--><!--Device-KEY_MENU = 2067-End--> |
| KEY_PAGE_UP = 2068 | 向上翻页键。<br><!--Device-KEY_PAGE_UP = 2068--><!--Device-KEY_PAGE_UP = 2068-End--> |
| KEY_PAGE_DOWN = 2069 | 向下翻页键。<br><!--Device-KEY_PAGE_DOWN = 2069--><!--Device-KEY_PAGE_DOWN = 2069-End--> |
| KEY_ESCAPE = 2070 | ESC键。<br><!--Device-KEY_ESCAPE = 2070--><!--Device-KEY_ESCAPE = 2070-End--> |
| KEY_FORWARD_DEL = 2071 | 删除键。<br><!--Device-KEY_FORWARD_DEL = 2071--><!--Device-KEY_FORWARD_DEL = 2071-End--> |
| KEY_CTRL_LEFT = 2072 | 左Ctrl键。<br><!--Device-KEY_CTRL_LEFT = 2072--><!--Device-KEY_CTRL_LEFT = 2072-End--> |
| KEY_CTRL_RIGHT = 2073 | 右Ctrl键。<br><!--Device-KEY_CTRL_RIGHT = 2073--><!--Device-KEY_CTRL_RIGHT = 2073-End--> |
| KEY_CAPS_LOCK = 2074 | 大写锁定键。<br><!--Device-KEY_CAPS_LOCK = 2074--><!--Device-KEY_CAPS_LOCK = 2074-End--> |
| KEY_SCROLL_LOCK = 2075 | 滚动锁定键。<br><!--Device-KEY_SCROLL_LOCK = 2075--><!--Device-KEY_SCROLL_LOCK = 2075-End--> |
| KEY_META_LEFT = 2076 | 左元修改器键。<br><!--Device-KEY_META_LEFT = 2076--><!--Device-KEY_META_LEFT = 2076-End--> |
| KEY_META_RIGHT = 2077 | 右元修改器键。<br><!--Device-KEY_META_RIGHT = 2077--><!--Device-KEY_META_RIGHT = 2077-End--> |
| KEY_FUNCTION = 2078 | 功能键。<br><!--Device-KEY_FUNCTION = 2078--><!--Device-KEY_FUNCTION = 2078-End--> |
| KEY_SYSRQ = 2079 | 系统请求/打印屏幕键。<br><!--Device-KEY_SYSRQ = 2079--><!--Device-KEY_SYSRQ = 2079-End--> |
| KEY_BREAK = 2080 | Break/Pause键。<br><!--Device-KEY_BREAK = 2080--><!--Device-KEY_BREAK = 2080-End--> |
| KEY_MOVE_HOME = 2081 | 光标移动到开始键。<br><!--Device-KEY_MOVE_HOME = 2081--><!--Device-KEY_MOVE_HOME = 2081-End--> |
| KEY_MOVE_END = 2082 | 光标移动到末尾键。<br><!--Device-KEY_MOVE_END = 2082--><!--Device-KEY_MOVE_END = 2082-End--> |
| KEY_INSERT = 2083 | 插入键。<br><!--Device-KEY_INSERT = 2083--><!--Device-KEY_INSERT = 2083-End--> |
| KEY_FORWARD = 2084 | 前进键。<br><!--Device-KEY_FORWARD = 2084--><!--Device-KEY_FORWARD = 2084-End--> |
| KEY_MEDIA_PLAY = 2085 | 多媒体键，播放。<br><!--Device-KEY_MEDIA_PLAY = 2085--><!--Device-KEY_MEDIA_PLAY = 2085-End--> |
| KEY_MEDIA_PAUSE = 2086 | 多媒体键，暂停。<br><!--Device-KEY_MEDIA_PAUSE = 2086--><!--Device-KEY_MEDIA_PAUSE = 2086-End--> |
| KEY_MEDIA_CLOSE = 2087 | 多媒体键，关闭。<br><!--Device-KEY_MEDIA_CLOSE = 2087--><!--Device-KEY_MEDIA_CLOSE = 2087-End--> |
| KEY_MEDIA_EJECT = 2088 | 多媒体键，弹出。<br><!--Device-KEY_MEDIA_EJECT = 2088--><!--Device-KEY_MEDIA_EJECT = 2088-End--> |
| KEY_MEDIA_RECORD = 2089 | 多媒体键，录音。<br><!--Device-KEY_MEDIA_RECORD = 2089--><!--Device-KEY_MEDIA_RECORD = 2089-End--> |
| KEY_F1 = 2090 | 按键'F1'。<br><!--Device-KEY_F1 = 2090--><!--Device-KEY_F1 = 2090-End--> |
| KEY_F2 = 2091 | 按键'F2'。<br><!--Device-KEY_F2 = 2091--><!--Device-KEY_F2 = 2091-End--> |
| KEY_F3 = 2092 | 按键'F3'。<br><!--Device-KEY_F3 = 2092--><!--Device-KEY_F3 = 2092-End--> |
| KEY_F4 = 2093 | 按键'F4'。<br><!--Device-KEY_F4 = 2093--><!--Device-KEY_F4 = 2093-End--> |
| KEY_F5 = 2094 | 按键'F5'。<br><!--Device-KEY_F5 = 2094--><!--Device-KEY_F5 = 2094-End--> |
| KEY_F6 = 2095 | 按键'F6'。<br><!--Device-KEY_F6 = 2095--><!--Device-KEY_F6 = 2095-End--> |
| KEY_F7 = 2096 | 按键'F7'。<br><!--Device-KEY_F7 = 2096--><!--Device-KEY_F7 = 2096-End--> |
| KEY_F8 = 2097 | 按键'F8'。<br><!--Device-KEY_F8 = 2097--><!--Device-KEY_F8 = 2097-End--> |
| KEY_F9 = 2098 | 按键'F9'。<br><!--Device-KEY_F9 = 2098--><!--Device-KEY_F9 = 2098-End--> |
| KEY_F10 = 2099 | 按键'F10'。<br><!--Device-KEY_F10 = 2099--><!--Device-KEY_F10 = 2099-End--> |
| KEY_F11 = 2100 | 按键'F11'。<br><!--Device-KEY_F11 = 2100--><!--Device-KEY_F11 = 2100-End--> |
| KEY_F12 = 2101 | 按键'F12'。<br><!--Device-KEY_F12 = 2101--><!--Device-KEY_F12 = 2101-End--> |
| KEY_NUM_LOCK = 2102 | 小键盘锁。<br><!--Device-KEY_NUM_LOCK = 2102--><!--Device-KEY_NUM_LOCK = 2102-End--> |
| KEY_NUMPAD_0 = 2103 | 小键盘按键'0'。<br><!--Device-KEY_NUMPAD_0 = 2103--><!--Device-KEY_NUMPAD_0 = 2103-End--> |
| KEY_NUMPAD_1 = 2104 | 小键盘按键'1'。<br><!--Device-KEY_NUMPAD_1 = 2104--><!--Device-KEY_NUMPAD_1 = 2104-End--> |
| KEY_NUMPAD_2 = 2105 | 小键盘按键'2'。<br><!--Device-KEY_NUMPAD_2 = 2105--><!--Device-KEY_NUMPAD_2 = 2105-End--> |
| KEY_NUMPAD_3 = 2106 | 小键盘按键'3'。<br><!--Device-KEY_NUMPAD_3 = 2106--><!--Device-KEY_NUMPAD_3 = 2106-End--> |
| KEY_NUMPAD_4 = 2107 | 小键盘按键'4'。<br><!--Device-KEY_NUMPAD_4 = 2107--><!--Device-KEY_NUMPAD_4 = 2107-End--> |
| KEY_NUMPAD_5 = 2108 | 小键盘按键'5'。<br><!--Device-KEY_NUMPAD_5 = 2108--><!--Device-KEY_NUMPAD_5 = 2108-End--> |
| KEY_NUMPAD_6 = 2109 | 小键盘按键'6'。<br><!--Device-KEY_NUMPAD_6 = 2109--><!--Device-KEY_NUMPAD_6 = 2109-End--> |
| KEY_NUMPAD_7 = 2110 | 小键盘按键'7'。<br><!--Device-KEY_NUMPAD_7 = 2110--><!--Device-KEY_NUMPAD_7 = 2110-End--> |
| KEY_NUMPAD_8 = 2111 | 小键盘按键'8'。<br><!--Device-KEY_NUMPAD_8 = 2111--><!--Device-KEY_NUMPAD_8 = 2111-End--> |
| KEY_NUMPAD_9 = 2112 | 小键盘按键'9'。<br><!--Device-KEY_NUMPAD_9 = 2112--><!--Device-KEY_NUMPAD_9 = 2112-End--> |
| KEY_NUMPAD_DIVIDE = 2113 | 小键盘按键'/'。<br><!--Device-KEY_NUMPAD_DIVIDE = 2113--><!--Device-KEY_NUMPAD_DIVIDE = 2113-End--> |
| KEY_NUMPAD_MULTIPLY = 2114 | 小键盘按键'*'。<br><!--Device-KEY_NUMPAD_MULTIPLY = 2114--><!--Device-KEY_NUMPAD_MULTIPLY = 2114-End--> |
| KEY_NUMPAD_SUBTRACT = 2115 | 小键盘按键'-'。<br><!--Device-KEY_NUMPAD_SUBTRACT = 2115--><!--Device-KEY_NUMPAD_SUBTRACT = 2115-End--> |
| KEY_NUMPAD_ADD = 2116 | 小键盘按键'+'。<br><!--Device-KEY_NUMPAD_ADD = 2116--><!--Device-KEY_NUMPAD_ADD = 2116-End--> |
| KEY_NUMPAD_DOT = 2117 | 小键盘按键'.'。<br><!--Device-KEY_NUMPAD_DOT = 2117--><!--Device-KEY_NUMPAD_DOT = 2117-End--> |
| KEY_NUMPAD_COMMA = 2118 | 小键盘按键','。<br><!--Device-KEY_NUMPAD_COMMA = 2118--><!--Device-KEY_NUMPAD_COMMA = 2118-End--> |
| KEY_NUMPAD_ENTER = 2119 | 小键盘按键回车。<br><!--Device-KEY_NUMPAD_ENTER = 2119--><!--Device-KEY_NUMPAD_ENTER = 2119-End--> |
| KEY_NUMPAD_EQUALS = 2120 | 小键盘按键'='。<br><!--Device-KEY_NUMPAD_EQUALS = 2120--><!--Device-KEY_NUMPAD_EQUALS = 2120-End--> |
| KEY_NUMPAD_LEFT_PAREN = 2121 | 小键盘按键'('。<br><!--Device-KEY_NUMPAD_LEFT_PAREN = 2121--><!--Device-KEY_NUMPAD_LEFT_PAREN = 2121-End--> |
| KEY_NUMPAD_RIGHT_PAREN = 2122 | 小键盘按键')'。<br><!--Device-KEY_NUMPAD_RIGHT_PAREN = 2122--><!--Device-KEY_NUMPAD_RIGHT_PAREN = 2122-End--> |
| KEY_VIRTUAL_MULTITASK = 2210 | 虚拟多任务键。<br><!--Device-KEY_VIRTUAL_MULTITASK = 2210--><!--Device-KEY_VIRTUAL_MULTITASK = 2210-End--> |
| KEY_SLEEP = 2600 | 睡眠键。<br><!--Device-KEY_SLEEP = 2600--><!--Device-KEY_SLEEP = 2600-End--> |
| KEY_ZENKAKU_HANKAKU = 2601 | 日文全角/半角键。<br><!--Device-KEY_ZENKAKU_HANKAKU = 2601--><!--Device-KEY_ZENKAKU_HANKAKU = 2601-End--> |
| KEY_102ND = 2602 | 非美式键盘布局（102键）上的额外按键，通常位于左Shift键右侧（对应'<'、'>'或'\<br><!--Device-KEY_102ND = 2602--><!--Device-KEY_102ND = 2602-End--> |
| KEY_RO = 2603 | 日文Ro键。<br><!--Device-KEY_RO = 2603--><!--Device-KEY_RO = 2603-End--> |
| KEY_KATAKANA = 2604 | 日文片假名键。<br><!--Device-KEY_KATAKANA = 2604--><!--Device-KEY_KATAKANA = 2604-End--> |
| KEY_HIRAGANA = 2605 | 日文平假名键。<br><!--Device-KEY_HIRAGANA = 2605--><!--Device-KEY_HIRAGANA = 2605-End--> |
| KEY_HENKAN = 2606 | 日文转换键。<br><!--Device-KEY_HENKAN = 2606--><!--Device-KEY_HENKAN = 2606-End--> |
| KEY_KATAKANA_HIRAGANA = 2607 | 日文片假名/平假名键。<br><!--Device-KEY_KATAKANA_HIRAGANA = 2607--><!--Device-KEY_KATAKANA_HIRAGANA = 2607-End--> |
| KEY_MUHENKAN = 2608 | 日文非转换键。<br><!--Device-KEY_MUHENKAN = 2608--><!--Device-KEY_MUHENKAN = 2608-End--> |
| KEY_LINEFEED = 2609 | 换行键。<br><!--Device-KEY_LINEFEED = 2609--><!--Device-KEY_LINEFEED = 2609-End--> |
| KEY_MACRO = 2610 | 宏键。<br><!--Device-KEY_MACRO = 2610--><!--Device-KEY_MACRO = 2610-End--> |
| KEY_NUMPAD_PLUSMINUS = 2611 | 小键盘加号/减号键。<br><!--Device-KEY_NUMPAD_PLUSMINUS = 2611--><!--Device-KEY_NUMPAD_PLUSMINUS = 2611-End--> |
| KEY_SCALE = 2612 | 缩放键。<br><!--Device-KEY_SCALE = 2612--><!--Device-KEY_SCALE = 2612-End--> |
| KEY_HANGUEL = 2613 | 韩语键。<br><!--Device-KEY_HANGUEL = 2613--><!--Device-KEY_HANGUEL = 2613-End--> |
| KEY_HANJA = 2614 | 韩语汉字键。<br><!--Device-KEY_HANJA = 2614--><!--Device-KEY_HANJA = 2614-End--> |
| KEY_YEN = 2615 | 日元键。<br><!--Device-KEY_YEN = 2615--><!--Device-KEY_YEN = 2615-End--> |
| KEY_STOP = 2616 | 停止键。<br><!--Device-KEY_STOP = 2616--><!--Device-KEY_STOP = 2616-End--> |
| KEY_AGAIN = 2617 | 重复键。<br><!--Device-KEY_AGAIN = 2617--><!--Device-KEY_AGAIN = 2617-End--> |
| KEY_PROPS = 2618 | 属性键。<br><!--Device-KEY_PROPS = 2618--><!--Device-KEY_PROPS = 2618-End--> |
| KEY_UNDO = 2619 | 撤销键。<br><!--Device-KEY_UNDO = 2619--><!--Device-KEY_UNDO = 2619-End--> |
| KEY_COPY = 2620 | 复制键。<br><!--Device-KEY_COPY = 2620--><!--Device-KEY_COPY = 2620-End--> |
| KEY_OPEN = 2621 | 打开键。<br><!--Device-KEY_OPEN = 2621--><!--Device-KEY_OPEN = 2621-End--> |
| KEY_PASTE = 2622 | 粘贴键。<br><!--Device-KEY_PASTE = 2622--><!--Device-KEY_PASTE = 2622-End--> |
| KEY_FIND = 2623 | 查找键。<br><!--Device-KEY_FIND = 2623--><!--Device-KEY_FIND = 2623-End--> |
| KEY_CUT = 2624 | 剪切键。<br><!--Device-KEY_CUT = 2624--><!--Device-KEY_CUT = 2624-End--> |
| KEY_HELP = 2625 | 帮助键。<br><!--Device-KEY_HELP = 2625--><!--Device-KEY_HELP = 2625-End--> |
| KEY_CALC = 2626 | 计算器特殊功能键，用于启动计算器应用程序。<br><!--Device-KEY_CALC = 2626--><!--Device-KEY_CALC = 2626-End--> |
| KEY_FILE = 2627 | 文件按键。<br><!--Device-KEY_FILE = 2627--><!--Device-KEY_FILE = 2627-End--> |
| KEY_BOOKMARKS = 2628 | 书签键。<br><!--Device-KEY_BOOKMARKS = 2628--><!--Device-KEY_BOOKMARKS = 2628-End--> |
| KEY_NEXT = 2629 | 下一个按键。<br><!--Device-KEY_NEXT = 2629--><!--Device-KEY_NEXT = 2629-End--> |
| KEY_PLAYPAUSE = 2630 | 播放/暂停键。<br><!--Device-KEY_PLAYPAUSE = 2630--><!--Device-KEY_PLAYPAUSE = 2630-End--> |
| KEY_PREVIOUS = 2631 | 上一个按键。<br><!--Device-KEY_PREVIOUS = 2631--><!--Device-KEY_PREVIOUS = 2631-End--> |
| KEY_STOPCD = 2632 | CD停止键。<br><!--Device-KEY_STOPCD = 2632--><!--Device-KEY_STOPCD = 2632-End--> |
| KEY_CONFIG = 2634 | 配置键。<br><!--Device-KEY_CONFIG = 2634--><!--Device-KEY_CONFIG = 2634-End--> |
| KEY_REFRESH = 2635 | 刷新键。<br><!--Device-KEY_REFRESH = 2635--><!--Device-KEY_REFRESH = 2635-End--> |
| KEY_EXIT = 2636 | 退出键。<br><!--Device-KEY_EXIT = 2636--><!--Device-KEY_EXIT = 2636-End--> |
| KEY_EDIT = 2637 | 编辑键。<br><!--Device-KEY_EDIT = 2637--><!--Device-KEY_EDIT = 2637-End--> |
| KEY_SCROLLUP = 2638 | 向上滚动键。<br><!--Device-KEY_SCROLLUP = 2638--><!--Device-KEY_SCROLLUP = 2638-End--> |
| KEY_SCROLLDOWN = 2639 | 向下滚动键。<br><!--Device-KEY_SCROLLDOWN = 2639--><!--Device-KEY_SCROLLDOWN = 2639-End--> |
| KEY_NEW = 2640 | 新建键。<br><!--Device-KEY_NEW = 2640--><!--Device-KEY_NEW = 2640-End--> |
| KEY_REDO = 2641 | 重做键。<br><!--Device-KEY_REDO = 2641--><!--Device-KEY_REDO = 2641-End--> |
| KEY_CLOSE = 2642 | 关闭键。<br><!--Device-KEY_CLOSE = 2642--><!--Device-KEY_CLOSE = 2642-End--> |
| KEY_PLAY = 2643 | 播放键。<br><!--Device-KEY_PLAY = 2643--><!--Device-KEY_PLAY = 2643-End--> |
| KEY_BASSBOOST = 2644 | 低音增强键。<br><!--Device-KEY_BASSBOOST = 2644--><!--Device-KEY_BASSBOOST = 2644-End--> |
| KEY_PRINT = 2645 | 打印键。<br><!--Device-KEY_PRINT = 2645--><!--Device-KEY_PRINT = 2645-End--> |
| KEY_CHAT = 2646 | 聊天键。<br><!--Device-KEY_CHAT = 2646--><!--Device-KEY_CHAT = 2646-End--> |
| KEY_FINANCE = 2647 | 金融键。<br><!--Device-KEY_FINANCE = 2647--><!--Device-KEY_FINANCE = 2647-End--> |
| KEY_CANCEL = 2648 | 取消键。<br><!--Device-KEY_CANCEL = 2648--><!--Device-KEY_CANCEL = 2648-End--> |
| KEY_KBDILLUM_TOGGLE = 2649 | 键盘灯光切换键。<br><!--Device-KEY_KBDILLUM_TOGGLE = 2649--><!--Device-KEY_KBDILLUM_TOGGLE = 2649-End--> |
| KEY_KBDILLUM_DOWN = 2650 | 键盘灯光调暗键。<br><!--Device-KEY_KBDILLUM_DOWN = 2650--><!--Device-KEY_KBDILLUM_DOWN = 2650-End--> |
| KEY_KBDILLUM_UP = 2651 | 键盘灯光调亮键。<br><!--Device-KEY_KBDILLUM_UP = 2651--><!--Device-KEY_KBDILLUM_UP = 2651-End--> |
| KEY_SEND = 2652 | 发送键。<br><!--Device-KEY_SEND = 2652--><!--Device-KEY_SEND = 2652-End--> |
| KEY_REPLY = 2653 | 答复键。<br><!--Device-KEY_REPLY = 2653--><!--Device-KEY_REPLY = 2653-End--> |
| KEY_FORWARDMAIL = 2654 | 邮件转发键。<br><!--Device-KEY_FORWARDMAIL = 2654--><!--Device-KEY_FORWARDMAIL = 2654-End--> |
| KEY_SAVE = 2655 | 保存键。<br><!--Device-KEY_SAVE = 2655--><!--Device-KEY_SAVE = 2655-End--> |
| KEY_DOCUMENTS = 2656 | 文档键。<br><!--Device-KEY_DOCUMENTS = 2656--><!--Device-KEY_DOCUMENTS = 2656-End--> |
| KEY_VIDEO_NEXT = 2657 | 下一个视频键。<br><!--Device-KEY_VIDEO_NEXT = 2657--><!--Device-KEY_VIDEO_NEXT = 2657-End--> |
| KEY_VIDEO_PREV = 2658 | 上一个视频键。<br><!--Device-KEY_VIDEO_PREV = 2658--><!--Device-KEY_VIDEO_PREV = 2658-End--> |
| KEY_BRIGHTNESS_CYCLE = 2659 | 亮度循环切换键。<br><!--Device-KEY_BRIGHTNESS_CYCLE = 2659--><!--Device-KEY_BRIGHTNESS_CYCLE = 2659-End--> |
| KEY_BRIGHTNESS_ZERO = 2660 | 亮度调节为0键。<br><!--Device-KEY_BRIGHTNESS_ZERO = 2660--><!--Device-KEY_BRIGHTNESS_ZERO = 2660-End--> |
| KEY_DISPLAY_OFF = 2661 | 显示关闭键。<br><!--Device-KEY_DISPLAY_OFF = 2661--><!--Device-KEY_DISPLAY_OFF = 2661-End--> |
| KEY_BTN_MISC = 2662 | 游戏手柄上的各种按键。<br><!--Device-KEY_BTN_MISC = 2662--><!--Device-KEY_BTN_MISC = 2662-End--> |
| KEY_GOTO = 2663 | 进入键。<br><!--Device-KEY_GOTO = 2663--><!--Device-KEY_GOTO = 2663-End--> |
| KEY_INFO = 2664 | 信息查看键。<br><!--Device-KEY_INFO = 2664--><!--Device-KEY_INFO = 2664-End--> |
| KEY_PROGRAM = 2665 | 程序键。<br><!--Device-KEY_PROGRAM = 2665--><!--Device-KEY_PROGRAM = 2665-End--> |
| KEY_PVR = 2666 | 个人录像机（PVR）键。<br><!--Device-KEY_PVR = 2666--><!--Device-KEY_PVR = 2666-End--> |
| KEY_SUBTITLE = 2667 | 字幕键。<br><!--Device-KEY_SUBTITLE = 2667--><!--Device-KEY_SUBTITLE = 2667-End--> |
| KEY_FULL_SCREEN = 2668 | 全屏键。<br><!--Device-KEY_FULL_SCREEN = 2668--><!--Device-KEY_FULL_SCREEN = 2668-End--> |
| KEY_KEYBOARD = 2669 | 键盘键，用于唤起或切换键盘功能键。<br><!--Device-KEY_KEYBOARD = 2669--><!--Device-KEY_KEYBOARD = 2669-End--> |
| KEY_ASPECT_RATIO = 2670 | 屏幕纵横比调节键。<br><!--Device-KEY_ASPECT_RATIO = 2670--><!--Device-KEY_ASPECT_RATIO = 2670-End--> |
| KEY_PC = 2671 | PC键。<br><!--Device-KEY_PC = 2671--><!--Device-KEY_PC = 2671-End--> |
| KEY_TV = 2672 | TV键。<br><!--Device-KEY_TV = 2672--><!--Device-KEY_TV = 2672-End--> |
| KEY_TV2 = 2673 | TV键2。<br><!--Device-KEY_TV2 = 2673--><!--Device-KEY_TV2 = 2673-End--> |
| KEY_VCR = 2674 | 录像机开启键。<br><!--Device-KEY_VCR = 2674--><!--Device-KEY_VCR = 2674-End--> |
| KEY_VCR2 = 2675 | 录像机开启键2。<br><!--Device-KEY_VCR2 = 2675--><!--Device-KEY_VCR2 = 2675-End--> |
| KEY_SAT = 2676 | 卫星键。<br><!--Device-KEY_SAT = 2676--><!--Device-KEY_SAT = 2676-End--> |
| KEY_CD = 2677 | CD键。<br><!--Device-KEY_CD = 2677--><!--Device-KEY_CD = 2677-End--> |
| KEY_TAPE = 2678 | 磁带键。<br><!--Device-KEY_TAPE = 2678--><!--Device-KEY_TAPE = 2678-End--> |
| KEY_TUNER = 2679 | 调谐器键。<br><!--Device-KEY_TUNER = 2679--><!--Device-KEY_TUNER = 2679-End--> |
| KEY_PLAYER = 2680 | 播放器键。<br><!--Device-KEY_PLAYER = 2680--><!--Device-KEY_PLAYER = 2680-End--> |
| KEY_DVD = 2681 | DVD键。<br><!--Device-KEY_DVD = 2681--><!--Device-KEY_DVD = 2681-End--> |
| KEY_AUDIO = 2682 | 音频键。<br><!--Device-KEY_AUDIO = 2682--><!--Device-KEY_AUDIO = 2682-End--> |
| KEY_VIDEO = 2683 | 视频键。<br><!--Device-KEY_VIDEO = 2683--><!--Device-KEY_VIDEO = 2683-End--> |
| KEY_MEMO = 2684 | 备忘录键。<br><!--Device-KEY_MEMO = 2684--><!--Device-KEY_MEMO = 2684-End--> |
| KEY_CALENDAR = 2685 | 日历键。<br><!--Device-KEY_CALENDAR = 2685--><!--Device-KEY_CALENDAR = 2685-End--> |
| KEY_RED = 2686 | 红色按键。<br><!--Device-KEY_RED = 2686--><!--Device-KEY_RED = 2686-End--> |
| KEY_GREEN = 2687 | 绿色按键。<br><!--Device-KEY_GREEN = 2687--><!--Device-KEY_GREEN = 2687-End--> |
| KEY_YELLOW = 2688 | 黄色按键。<br><!--Device-KEY_YELLOW = 2688--><!--Device-KEY_YELLOW = 2688-End--> |
| KEY_BLUE = 2689 | 蓝色按键。<br><!--Device-KEY_BLUE = 2689--><!--Device-KEY_BLUE = 2689-End--> |
| KEY_CHANNELUP = 2690 | 频道向上键。<br><!--Device-KEY_CHANNELUP = 2690--><!--Device-KEY_CHANNELUP = 2690-End--> |
| KEY_CHANNELDOWN = 2691 | 频道向下键。<br><!--Device-KEY_CHANNELDOWN = 2691--><!--Device-KEY_CHANNELDOWN = 2691-End--> |
| KEY_LAST = 2692 | 末尾键。<br><!--Device-KEY_LAST = 2692--><!--Device-KEY_LAST = 2692-End--> |
| KEY_RESTART = 2693 | 重启键。<br><!--Device-KEY_RESTART = 2693--><!--Device-KEY_RESTART = 2693-End--> |
| KEY_SLOW = 2694 | 慢速键。<br><!--Device-KEY_SLOW = 2694--><!--Device-KEY_SLOW = 2694-End--> |
| KEY_SHUFFLE = 2695 | 随机播放键。<br><!--Device-KEY_SHUFFLE = 2695--><!--Device-KEY_SHUFFLE = 2695-End--> |
| KEY_VIDEOPHONE = 2696 | 可视电话键。<br><!--Device-KEY_VIDEOPHONE = 2696--><!--Device-KEY_VIDEOPHONE = 2696-End--> |
| KEY_GAMES = 2697 | 游戏键。<br><!--Device-KEY_GAMES = 2697--><!--Device-KEY_GAMES = 2697-End--> |
| KEY_ZOOMIN = 2698 | 放大键。<br><!--Device-KEY_ZOOMIN = 2698--><!--Device-KEY_ZOOMIN = 2698-End--> |
| KEY_ZOOMOUT = 2699 | 缩小键。<br><!--Device-KEY_ZOOMOUT = 2699--><!--Device-KEY_ZOOMOUT = 2699-End--> |
| KEY_ZOOMRESET = 2700 | 缩放重置键。<br><!--Device-KEY_ZOOMRESET = 2700--><!--Device-KEY_ZOOMRESET = 2700-End--> |
| KEY_WORDPROCESSOR = 2701 | 文字处理键。<br><!--Device-KEY_WORDPROCESSOR = 2701--><!--Device-KEY_WORDPROCESSOR = 2701-End--> |
| KEY_EDITOR = 2702 | 编辑器键。<br><!--Device-KEY_EDITOR = 2702--><!--Device-KEY_EDITOR = 2702-End--> |
| KEY_SPREADSHEET = 2703 | 电子表格键。<br><!--Device-KEY_SPREADSHEET = 2703--><!--Device-KEY_SPREADSHEET = 2703-End--> |
| KEY_GRAPHICSEDITOR = 2704 | 图形编辑器键。<br><!--Device-KEY_GRAPHICSEDITOR = 2704--><!--Device-KEY_GRAPHICSEDITOR = 2704-End--> |
| KEY_PRESENTATION = 2705 | 演示文稿键。<br><!--Device-KEY_PRESENTATION = 2705--><!--Device-KEY_PRESENTATION = 2705-End--> |
| KEY_DATABASE = 2706 | 数据库键。<br><!--Device-KEY_DATABASE = 2706--><!--Device-KEY_DATABASE = 2706-End--> |
| KEY_NEWS = 2707 | 新闻键。<br><!--Device-KEY_NEWS = 2707--><!--Device-KEY_NEWS = 2707-End--> |
| KEY_VOICEMAIL = 2708 | 语音信箱键。<br><!--Device-KEY_VOICEMAIL = 2708--><!--Device-KEY_VOICEMAIL = 2708-End--> |
| KEY_ADDRESSBOOK = 2709 | 通讯簿键。<br><!--Device-KEY_ADDRESSBOOK = 2709--><!--Device-KEY_ADDRESSBOOK = 2709-End--> |
| KEY_MESSENGER = 2710 | 通信键。<br><!--Device-KEY_MESSENGER = 2710--><!--Device-KEY_MESSENGER = 2710-End--> |
| KEY_BRIGHTNESS_TOGGLE = 2711 | 亮度切换键。<br><!--Device-KEY_BRIGHTNESS_TOGGLE = 2711--><!--Device-KEY_BRIGHTNESS_TOGGLE = 2711-End--> |
| KEY_SPELLCHECK = 2712 | 拼写检查键。<br><!--Device-KEY_SPELLCHECK = 2712--><!--Device-KEY_SPELLCHECK = 2712-End--> |
| KEY_COFFEE = 2713 | 终端锁/屏幕保护程序。<br><!--Device-KEY_COFFEE = 2713--><!--Device-KEY_COFFEE = 2713-End--> |
| KEY_MEDIA_REPEAT = 2714 | 媒体循环键。<br><!--Device-KEY_MEDIA_REPEAT = 2714--><!--Device-KEY_MEDIA_REPEAT = 2714-End--> |
| KEY_IMAGES = 2715 | 图像键。<br><!--Device-KEY_IMAGES = 2715--><!--Device-KEY_IMAGES = 2715-End--> |
| KEY_BUTTONCONFIG = 2716 | 按键配置键。<br><!--Device-KEY_BUTTONCONFIG = 2716--><!--Device-KEY_BUTTONCONFIG = 2716-End--> |
| KEY_TASKMANAGER = 2717 | 任务管理器键。<br><!--Device-KEY_TASKMANAGER = 2717--><!--Device-KEY_TASKMANAGER = 2717-End--> |
| KEY_JOURNAL = 2718 | 日志按键。<br><!--Device-KEY_JOURNAL = 2718--><!--Device-KEY_JOURNAL = 2718-End--> |
| KEY_CONTROLPANEL = 2719 | 控制面板键。<br><!--Device-KEY_CONTROLPANEL = 2719--><!--Device-KEY_CONTROLPANEL = 2719-End--> |
| KEY_APPSELECT = 2720 | 应用程序选择键。<br><!--Device-KEY_APPSELECT = 2720--><!--Device-KEY_APPSELECT = 2720-End--> |
| KEY_SCREENSAVER = 2721 | 屏幕保护程序键。<br><!--Device-KEY_SCREENSAVER = 2721--><!--Device-KEY_SCREENSAVER = 2721-End--> |
| KEY_ASSISTANT = 2722 | 辅助键。<br><!--Device-KEY_ASSISTANT = 2722--><!--Device-KEY_ASSISTANT = 2722-End--> |
| KEY_KBD_LAYOUT_NEXT = 2723 | 下一个键盘布局键。<br><!--Device-KEY_KBD_LAYOUT_NEXT = 2723--><!--Device-KEY_KBD_LAYOUT_NEXT = 2723-End--> |
| KEY_BRIGHTNESS_MIN = 2724 | 最小亮度键。<br><!--Device-KEY_BRIGHTNESS_MIN = 2724--><!--Device-KEY_BRIGHTNESS_MIN = 2724-End--> |
| KEY_BRIGHTNESS_MAX = 2725 | 最大亮度键。<br><!--Device-KEY_BRIGHTNESS_MAX = 2725--><!--Device-KEY_BRIGHTNESS_MAX = 2725-End--> |
| KEY_KBDINPUTASSIST_PREV = 2726 | 键盘输入辅助上一个候选。<br><!--Device-KEY_KBDINPUTASSIST_PREV = 2726--><!--Device-KEY_KBDINPUTASSIST_PREV = 2726-End--> |
| KEY_KBDINPUTASSIST_NEXT = 2727 | 键盘输入辅助下一个候选。<br><!--Device-KEY_KBDINPUTASSIST_NEXT = 2727--><!--Device-KEY_KBDINPUTASSIST_NEXT = 2727-End--> |
| KEY_KBDINPUTASSIST_PREVGROUP = 2728 | 键盘输入辅助上一个候选组。<br><!--Device-KEY_KBDINPUTASSIST_PREVGROUP = 2728--><!--Device-KEY_KBDINPUTASSIST_PREVGROUP = 2728-End--> |
| KEY_KBDINPUTASSIST_NEXTGROUP = 2729 | 键盘输入辅助下一个候选组。<br><!--Device-KEY_KBDINPUTASSIST_NEXTGROUP = 2729--><!--Device-KEY_KBDINPUTASSIST_NEXTGROUP = 2729-End--> |
| KEY_KBDINPUTASSIST_ACCEPT = 2730 | 键盘输入辅助接受。<br><!--Device-KEY_KBDINPUTASSIST_ACCEPT = 2730--><!--Device-KEY_KBDINPUTASSIST_ACCEPT = 2730-End--> |
| KEY_KBDINPUTASSIST_CANCEL = 2731 | 键盘输入辅助取消。<br><!--Device-KEY_KBDINPUTASSIST_CANCEL = 2731--><!--Device-KEY_KBDINPUTASSIST_CANCEL = 2731-End--> |
| KEY_FRONT = 2800 | 挡风玻璃除雾器开关。<br><!--Device-KEY_FRONT = 2800--><!--Device-KEY_FRONT = 2800-End--> |
| KEY_SETUP = 2801 | 设置键。<br><!--Device-KEY_SETUP = 2801--><!--Device-KEY_SETUP = 2801-End--> |
| KEY_WAKEUP = 2802 | 唤醒键。<br><!--Device-KEY_WAKEUP = 2802--><!--Device-KEY_WAKEUP = 2802-End--> |
| KEY_SENDFILE = 2803 | 发送文件按键。<br><!--Device-KEY_SENDFILE = 2803--><!--Device-KEY_SENDFILE = 2803-End--> |
| KEY_DELETEFILE = 2804 | 删除文件按键。<br><!--Device-KEY_DELETEFILE = 2804--><!--Device-KEY_DELETEFILE = 2804-End--> |
| KEY_XFER = 2805 | 文件传输（XFER）按键。<br><!--Device-KEY_XFER = 2805--><!--Device-KEY_XFER = 2805-End--> |
| KEY_PROG1 = 2806 | 程序键1。<br><!--Device-KEY_PROG1 = 2806--><!--Device-KEY_PROG1 = 2806-End--> |
| KEY_PROG2 = 2807 | 程序键2。<br><!--Device-KEY_PROG2 = 2807--><!--Device-KEY_PROG2 = 2807-End--> |
| KEY_MSDOS = 2808 | MS-DOS键（微软磁盘操作系统）。<br><!--Device-KEY_MSDOS = 2808--><!--Device-KEY_MSDOS = 2808-End--> |
| KEY_SCREENLOCK = 2809 | 屏幕锁定键。<br><!--Device-KEY_SCREENLOCK = 2809--><!--Device-KEY_SCREENLOCK = 2809-End--> |
| KEY_DIRECTION_ROTATE_DISPLAY = 2810 | 方向旋转显示键。<br><!--Device-KEY_DIRECTION_ROTATE_DISPLAY = 2810--><!--Device-KEY_DIRECTION_ROTATE_DISPLAY = 2810-End--> |
| KEY_CYCLEWINDOWS = 2811 | Windows循环键。<br><!--Device-KEY_CYCLEWINDOWS = 2811--><!--Device-KEY_CYCLEWINDOWS = 2811-End--> |
| KEY_COMPUTER = 2812 | 计算机键。<br><!--Device-KEY_COMPUTER = 2812--><!--Device-KEY_COMPUTER = 2812-End--> |
| KEY_EJECTCLOSECD = 2813 | 弹出CD键。<br><!--Device-KEY_EJECTCLOSECD = 2813--><!--Device-KEY_EJECTCLOSECD = 2813-End--> |
| KEY_ISO = 2814 | ISO键盘布局标准定义的特殊功能键。<br><!--Device-KEY_ISO = 2814--><!--Device-KEY_ISO = 2814-End--> |
| KEY_MOVE = 2815 | 移动键。<br><!--Device-KEY_MOVE = 2815--><!--Device-KEY_MOVE = 2815-End--> |
| KEY_F13 = 2816 | 按键'F13'。<br><!--Device-KEY_F13 = 2816--><!--Device-KEY_F13 = 2816-End--> |
| KEY_F14 = 2817 | 按键'F14'。<br><!--Device-KEY_F14 = 2817--><!--Device-KEY_F14 = 2817-End--> |
| KEY_F15 = 2818 | 按键'F15'。<br><!--Device-KEY_F15 = 2818--><!--Device-KEY_F15 = 2818-End--> |
| KEY_F16 = 2819 | 按键'F16'。<br><!--Device-KEY_F16 = 2819--><!--Device-KEY_F16 = 2819-End--> |
| KEY_F17 = 2820 | 按键'F17'。<br><!--Device-KEY_F17 = 2820--><!--Device-KEY_F17 = 2820-End--> |
| KEY_F18 = 2821 | 按键'F18'。<br><!--Device-KEY_F18 = 2821--><!--Device-KEY_F18 = 2821-End--> |
| KEY_F19 = 2822 | 按键'F19'。<br><!--Device-KEY_F19 = 2822--><!--Device-KEY_F19 = 2822-End--> |
| KEY_F20 = 2823 | 按键'F20'。<br><!--Device-KEY_F20 = 2823--><!--Device-KEY_F20 = 2823-End--> |
| KEY_F21 = 2824 | 按键'F21'。<br><!--Device-KEY_F21 = 2824--><!--Device-KEY_F21 = 2824-End--> |
| KEY_F22 = 2825 | 按键'F22'。<br><!--Device-KEY_F22 = 2825--><!--Device-KEY_F22 = 2825-End--> |
| KEY_F23 = 2826 | 按键'F23'。<br><!--Device-KEY_F23 = 2826--><!--Device-KEY_F23 = 2826-End--> |
| KEY_F24 = 2827 | 按键'F24'。<br><!--Device-KEY_F24 = 2827--><!--Device-KEY_F24 = 2827-End--> |
| KEY_PROG3 = 2828 | 程序键3。<br><!--Device-KEY_PROG3 = 2828--><!--Device-KEY_PROG3 = 2828-End--> |
| KEY_PROG4 = 2829 | 程序键4。<br><!--Device-KEY_PROG4 = 2829--><!--Device-KEY_PROG4 = 2829-End--> |
| KEY_DASHBOARD = 2830 | 仪表板键，用于打开或切换到仪表板界面。<br><!--Device-KEY_DASHBOARD = 2830--><!--Device-KEY_DASHBOARD = 2830-End--> |
| KEY_SUSPEND = 2831 | 挂起键。<br><!--Device-KEY_SUSPEND = 2831--><!--Device-KEY_SUSPEND = 2831-End--> |
| KEY_HP = 2832 | HP功能键。<br><!--Device-KEY_HP = 2832--><!--Device-KEY_HP = 2832-End--> |
| KEY_SOUND = 2833 | 音量键。<br><!--Device-KEY_SOUND = 2833--><!--Device-KEY_SOUND = 2833-End--> |
| KEY_QUESTION = 2834 | 疑问按键。<br><!--Device-KEY_QUESTION = 2834--><!--Device-KEY_QUESTION = 2834-End--> |
| KEY_CONNECT = 2836 | 连接键。<br><!--Device-KEY_CONNECT = 2836--><!--Device-KEY_CONNECT = 2836-End--> |
| KEY_SPORT = 2837 | 运动按键。<br><!--Device-KEY_SPORT = 2837--><!--Device-KEY_SPORT = 2837-End--> |
| KEY_SHOP = 2838 | 商城键。<br><!--Device-KEY_SHOP = 2838--><!--Device-KEY_SHOP = 2838-End--> |
| KEY_ALTERASE = 2839 | 交替擦除键。<br><!--Device-KEY_ALTERASE = 2839--><!--Device-KEY_ALTERASE = 2839-End--> |
| KEY_SWITCHVIDEOMODE = 2841 | 在可用视频之间循环输出（监视器/LCD/TV输出等）。<br><!--Device-KEY_SWITCHVIDEOMODE = 2841--><!--Device-KEY_SWITCHVIDEOMODE = 2841-End--> |
| KEY_BATTERY = 2842 | 电池按键。<br><!--Device-KEY_BATTERY = 2842--><!--Device-KEY_BATTERY = 2842-End--> |
| KEY_BLUETOOTH = 2843 | 蓝牙按键。<br><!--Device-KEY_BLUETOOTH = 2843--><!--Device-KEY_BLUETOOTH = 2843-End--> |
| KEY_WLAN = 2844 | 无线局域网按键。<br><!--Device-KEY_WLAN = 2844--><!--Device-KEY_WLAN = 2844-End--> |
| KEY_UWB = 2845 | 超宽带（UWB）按键。<br><!--Device-KEY_UWB = 2845--><!--Device-KEY_UWB = 2845-End--> |
| KEY_WWAN_WIMAX = 2846 | WWAN WiMAX按键。<br><!--Device-KEY_WWAN_WIMAX = 2846--><!--Device-KEY_WWAN_WIMAX = 2846-End--> |
| KEY_RFKILL = 2847 | 射频关闭键。<br><!--Device-KEY_RFKILL = 2847--><!--Device-KEY_RFKILL = 2847-End--> |
| KEY_CHANNEL = 3001 | 频道键。<br><!--Device-KEY_CHANNEL = 3001--><!--Device-KEY_CHANNEL = 3001-End--> |
| KEY_BTN_0 = 3100 | 按键0。<br><!--Device-KEY_BTN_0 = 3100--><!--Device-KEY_BTN_0 = 3100-End--> |
| KEY_BTN_1 = 3101 | 按键1。<br><!--Device-KEY_BTN_1 = 3101--><!--Device-KEY_BTN_1 = 3101-End--> |
| KEY_BTN_2 = 3102 | 按键2。<br><!--Device-KEY_BTN_2 = 3102--><!--Device-KEY_BTN_2 = 3102-End--> |
| KEY_BTN_3 = 3103 | 按键3。<br><!--Device-KEY_BTN_3 = 3103--><!--Device-KEY_BTN_3 = 3103-End--> |
| KEY_BTN_4 = 3104 | 按键4。<br><!--Device-KEY_BTN_4 = 3104--><!--Device-KEY_BTN_4 = 3104-End--> |
| KEY_BTN_5 = 3105 | 按键5。<br><!--Device-KEY_BTN_5 = 3105--><!--Device-KEY_BTN_5 = 3105-End--> |
| KEY_BTN_6 = 3106 | 按键6。<br><!--Device-KEY_BTN_6 = 3106--><!--Device-KEY_BTN_6 = 3106-End--> |
| KEY_BTN_7 = 3107 | 按键7。<br><!--Device-KEY_BTN_7 = 3107--><!--Device-KEY_BTN_7 = 3107-End--> |
| KEY_BTN_8 = 3108 | 按键8。<br><!--Device-KEY_BTN_8 = 3108--><!--Device-KEY_BTN_8 = 3108-End--> |
| KEY_BTN_9 = 3109 | 按键9。<br><!--Device-KEY_BTN_9 = 3109--><!--Device-KEY_BTN_9 = 3109-End--> |

### OH_NativeXComponent_KeyAction

```c
enum OH_NativeXComponent_KeyAction
```

**描述：**

按键事件动作。

<!--Device-enum OH_NativeXComponent_KeyAction--><!--Device-enum OH_NativeXComponent_KeyAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| OH_NATIVEXCOMPONENT_KEY_ACTION_UNKNOWN = -1 | 未知的按键动作。<br><!--Device-OH_NATIVEXCOMPONENT_KEY_ACTION_UNKNOWN = -1--><!--Device-OH_NATIVEXCOMPONENT_KEY_ACTION_UNKNOWN = -1-End--> |
| OH_NATIVEXCOMPONENT_KEY_ACTION_DOWN = 0 | 按键按下动作。<br><!--Device-OH_NATIVEXCOMPONENT_KEY_ACTION_DOWN = 0--><!--Device-OH_NATIVEXCOMPONENT_KEY_ACTION_DOWN = 0-End--> |
| OH_NATIVEXCOMPONENT_KEY_ACTION_UP | 按键抬起动作。<br><!--Device-OH_NATIVEXCOMPONENT_KEY_ACTION_UP--><!--Device-OH_NATIVEXCOMPONENT_KEY_ACTION_UP-End--> |


