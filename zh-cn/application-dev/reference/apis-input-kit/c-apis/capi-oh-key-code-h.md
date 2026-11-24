# oh_key_code.h

## 概述

按键设备的键值。

**引用文件：** <multimodalinput/oh_key_code.h>

**库：** libohinput.so

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**起始版本：** 12

**相关模块：** [input](capi-input-kit-input.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Input_KeyCode](#input_keycode) | Input_KeyCode | 键值。 |

## 枚举类型说明

### Input_KeyCode

```c
enum Input_KeyCode
```

**描述：**

键值。

<!--Device-enum Input_KeyCode--><!--Device-enum Input_KeyCode-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| KEYCODE_UNKNOWN = -1 | 未知按键<br><!--Device-KEYCODE_UNKNOWN = -1--><!--Device-KEYCODE_UNKNOWN = -1-End--> |
| KEYCODE_FN = 0 | 功能（Fn）键<br><!--Device-KEYCODE_FN = 0--><!--Device-KEYCODE_FN = 0-End--> |
| KEYCODE_HOME = 1 | 功能（Home）键<br>**起始版本：** 22<br><!--Device-KEYCODE_HOME = 1--><!--Device-KEYCODE_HOME = 1-End--> |
| KEYCODE_BACK = 2 | 返回键<br>**起始版本：** 22<br><!--Device-KEYCODE_BACK = 2--><!--Device-KEYCODE_BACK = 2-End--> |
| KEYCODE_SEARCH = 9 | 搜索键<br>**起始版本：** 22<br><!--Device-KEYCODE_SEARCH = 9--><!--Device-KEYCODE_SEARCH = 9-End--> |
| KEYCODE_MEDIA_PLAY_PAUSE = 10 | 多媒体键：播放/暂停。<br/>与KEYCODE_PLAYPAUSE的区别为：<br/>KEYCODE_PLAYPAUSE是较早的定义， KEYCODE_MEDIA_PLAY_PAUSE为现代媒体键设备设计，常见于较新的媒体键设备。<br>**起始版本：** 22<br><!--Device-KEYCODE_MEDIA_PLAY_PAUSE = 10--><!--Device-KEYCODE_MEDIA_PLAY_PAUSE = 10-End--> |
| KEYCODE_MEDIA_STOP = 11 | 光盘停止键<br>**起始版本：** 22<br><!--Device-KEYCODE_MEDIA_STOP = 11--><!--Device-KEYCODE_MEDIA_STOP = 11-End--> |
| KEYCODE_MEDIA_NEXT = 12 | 多媒体键：下一首<br>**起始版本：** 22<br><!--Device-KEYCODE_MEDIA_NEXT = 12--><!--Device-KEYCODE_MEDIA_NEXT = 12-End--> |
| KEYCODE_MEDIA_PREVIOUS = 13 | 多媒体键：上一首<br>**起始版本：** 22<br><!--Device-KEYCODE_MEDIA_PREVIOUS = 13--><!--Device-KEYCODE_MEDIA_PREVIOUS = 13-End--> |
| KEYCODE_MEDIA_REWIND = 14 | 多媒体键：快退<br>**起始版本：** 22<br><!--Device-KEYCODE_MEDIA_REWIND = 14--><!--Device-KEYCODE_MEDIA_REWIND = 14-End--> |
| KEYCODE_MEDIA_FAST_FORWARD = 15 | 多媒体键：快进<br>**起始版本：** 22<br><!--Device-KEYCODE_MEDIA_FAST_FORWARD = 15--><!--Device-KEYCODE_MEDIA_FAST_FORWARD = 15-End--> |
| KEYCODE_VOLUME_UP = 16 | 音量增加键<br><!--Device-KEYCODE_VOLUME_UP = 16--><!--Device-KEYCODE_VOLUME_UP = 16-End--> |
| KEYCODE_VOLUME_DOWN = 17 | 音量减小键<br><!--Device-KEYCODE_VOLUME_DOWN = 17--><!--Device-KEYCODE_VOLUME_DOWN = 17-End--> |
| KEYCODE_POWER = 18 | 电源键<br><!--Device-KEYCODE_POWER = 18--><!--Device-KEYCODE_POWER = 18-End--> |
| KEYCODE_CAMERA = 19 | 拍照键<br><!--Device-KEYCODE_CAMERA = 19--><!--Device-KEYCODE_CAMERA = 19-End--> |
| KEYCODE_VOLUME_MUTE = 22 | 扬声器静音键<br><!--Device-KEYCODE_VOLUME_MUTE = 22--><!--Device-KEYCODE_VOLUME_MUTE = 22-End--> |
| KEYCODE_MUTE = 23 | 话筒静音键<br><!--Device-KEYCODE_MUTE = 23--><!--Device-KEYCODE_MUTE = 23-End--> |
| KEYCODE_BRIGHTNESS_UP = 40 | 亮度调节按键：调亮<br><!--Device-KEYCODE_BRIGHTNESS_UP = 40--><!--Device-KEYCODE_BRIGHTNESS_UP = 40-End--> |
| KEYCODE_BRIGHTNESS_DOWN = 41 | 亮度调节按键：调暗<br><!--Device-KEYCODE_BRIGHTNESS_DOWN = 41--><!--Device-KEYCODE_BRIGHTNESS_DOWN = 41-End--> |
| KEYCODE_0 = 2000 | 按键'0'<br><!--Device-KEYCODE_0 = 2000--><!--Device-KEYCODE_0 = 2000-End--> |
| KEYCODE_1 = 2001 | 按键'1'<br><!--Device-KEYCODE_1 = 2001--><!--Device-KEYCODE_1 = 2001-End--> |
| KEYCODE_2 = 2002 | 按键'2'<br><!--Device-KEYCODE_2 = 2002--><!--Device-KEYCODE_2 = 2002-End--> |
| KEYCODE_3 = 2003 | 按键'3'<br><!--Device-KEYCODE_3 = 2003--><!--Device-KEYCODE_3 = 2003-End--> |
| KEYCODE_4 = 2004 | 按键'4'<br><!--Device-KEYCODE_4 = 2004--><!--Device-KEYCODE_4 = 2004-End--> |
| KEYCODE_5 = 2005 | 按键'5'<br><!--Device-KEYCODE_5 = 2005--><!--Device-KEYCODE_5 = 2005-End--> |
| KEYCODE_6 = 2006 | 按键'6'<br><!--Device-KEYCODE_6 = 2006--><!--Device-KEYCODE_6 = 2006-End--> |
| KEYCODE_7 = 2007 | 按键'7'<br><!--Device-KEYCODE_7 = 2007--><!--Device-KEYCODE_7 = 2007-End--> |
| KEYCODE_8 = 2008 | 按键'8'<br><!--Device-KEYCODE_8 = 2008--><!--Device-KEYCODE_8 = 2008-End--> |
| KEYCODE_9 = 2009 | 按键'9'<br><!--Device-KEYCODE_9 = 2009--><!--Device-KEYCODE_9 = 2009-End--> |
| KEYCODE_STAR = 2010 | 按键'*'<br>**起始版本：** 12<br><!--Device-KEYCODE_STAR = 2010--><!--Device-KEYCODE_STAR = 2010-End--> |
| KEYCODE_POUND = 2011 | 按键'#'<br><!--Device-KEYCODE_POUND = 2011--><!--Device-KEYCODE_POUND = 2011-End--> |
| KEYCODE_DPAD_UP = 2012 | 导航键：向上<br><!--Device-KEYCODE_DPAD_UP = 2012--><!--Device-KEYCODE_DPAD_UP = 2012-End--> |
| KEYCODE_DPAD_DOWN = 2013 | 导航键：向下<br><!--Device-KEYCODE_DPAD_DOWN = 2013--><!--Device-KEYCODE_DPAD_DOWN = 2013-End--> |
| KEYCODE_DPAD_LEFT = 2014 | 导航键：向左<br><!--Device-KEYCODE_DPAD_LEFT = 2014--><!--Device-KEYCODE_DPAD_LEFT = 2014-End--> |
| KEYCODE_DPAD_RIGHT = 2015 | 导航键：向右<br><!--Device-KEYCODE_DPAD_RIGHT = 2015--><!--Device-KEYCODE_DPAD_RIGHT = 2015-End--> |
| KEYCODE_DPAD_CENTER = 2016 | 导航键：确定键<br><!--Device-KEYCODE_DPAD_CENTER = 2016--><!--Device-KEYCODE_DPAD_CENTER = 2016-End--> |
| KEYCODE_A = 2017 | 按键'A'<br><!--Device-KEYCODE_A = 2017--><!--Device-KEYCODE_A = 2017-End--> |
| KEYCODE_B = 2018 | 按键'B'<br><!--Device-KEYCODE_B = 2018--><!--Device-KEYCODE_B = 2018-End--> |
| KEYCODE_C = 2019 | 按键'C'<br><!--Device-KEYCODE_C = 2019--><!--Device-KEYCODE_C = 2019-End--> |
| KEYCODE_D = 2020 | 按键'D'<br><!--Device-KEYCODE_D = 2020--><!--Device-KEYCODE_D = 2020-End--> |
| KEYCODE_E = 2021 | 按键'E'<br><!--Device-KEYCODE_E = 2021--><!--Device-KEYCODE_E = 2021-End--> |
| KEYCODE_F = 2022 | 按键'F'<br><!--Device-KEYCODE_F = 2022--><!--Device-KEYCODE_F = 2022-End--> |
| KEYCODE_G = 2023 | 按键'G'<br><!--Device-KEYCODE_G = 2023--><!--Device-KEYCODE_G = 2023-End--> |
| KEYCODE_H = 2024 | 按键'H'<br><!--Device-KEYCODE_H = 2024--><!--Device-KEYCODE_H = 2024-End--> |
| KEYCODE_I = 2025 | 按键'I'<br><!--Device-KEYCODE_I = 2025--><!--Device-KEYCODE_I = 2025-End--> |
| KEYCODE_J = 2026 | 按键'J'<br><!--Device-KEYCODE_J = 2026--><!--Device-KEYCODE_J = 2026-End--> |
| KEYCODE_K = 2027 | 按键'K'<br><!--Device-KEYCODE_K = 2027--><!--Device-KEYCODE_K = 2027-End--> |
| KEYCODE_L = 2028 | 按键'L'<br><!--Device-KEYCODE_L = 2028--><!--Device-KEYCODE_L = 2028-End--> |
| KEYCODE_M = 2029 | 按键'M'<br><!--Device-KEYCODE_M = 2029--><!--Device-KEYCODE_M = 2029-End--> |
| KEYCODE_N = 2030 | 按键'N'<br><!--Device-KEYCODE_N = 2030--><!--Device-KEYCODE_N = 2030-End--> |
| KEYCODE_O = 2031 | 按键'O'<br><!--Device-KEYCODE_O = 2031--><!--Device-KEYCODE_O = 2031-End--> |
| KEYCODE_P = 2032 | 按键'P'<br><!--Device-KEYCODE_P = 2032--><!--Device-KEYCODE_P = 2032-End--> |
| KEYCODE_Q = 2033 | 按键'Q'<br><!--Device-KEYCODE_Q = 2033--><!--Device-KEYCODE_Q = 2033-End--> |
| KEYCODE_R = 2034 | 按键'R'<br><!--Device-KEYCODE_R = 2034--><!--Device-KEYCODE_R = 2034-End--> |
| KEYCODE_S = 2035 | 按键'S'<br><!--Device-KEYCODE_S = 2035--><!--Device-KEYCODE_S = 2035-End--> |
| KEYCODE_T = 2036 | 按键'T'<br><!--Device-KEYCODE_T = 2036--><!--Device-KEYCODE_T = 2036-End--> |
| KEYCODE_U = 2037 | 按键'U'<br><!--Device-KEYCODE_U = 2037--><!--Device-KEYCODE_U = 2037-End--> |
| KEYCODE_V = 2038 | 按键'V'<br><!--Device-KEYCODE_V = 2038--><!--Device-KEYCODE_V = 2038-End--> |
| KEYCODE_W = 2039 | 按键'W'<br><!--Device-KEYCODE_W = 2039--><!--Device-KEYCODE_W = 2039-End--> |
| KEYCODE_X = 2040 | 按键'X'<br><!--Device-KEYCODE_X = 2040--><!--Device-KEYCODE_X = 2040-End--> |
| KEYCODE_Y = 2041 | 按键'Y'<br><!--Device-KEYCODE_Y = 2041--><!--Device-KEYCODE_Y = 2041-End--> |
| KEYCODE_Z = 2042 | 按键'Z'<br><!--Device-KEYCODE_Z = 2042--><!--Device-KEYCODE_Z = 2042-End--> |
| KEYCODE_COMMA = 2043 | 按键','<br><!--Device-KEYCODE_COMMA = 2043--><!--Device-KEYCODE_COMMA = 2043-End--> |
| KEYCODE_PERIOD = 2044 | 按键'.'<br><!--Device-KEYCODE_PERIOD = 2044--><!--Device-KEYCODE_PERIOD = 2044-End--> |
| KEYCODE_ALT_LEFT = 2045 | 左Alt键<br><!--Device-KEYCODE_ALT_LEFT = 2045--><!--Device-KEYCODE_ALT_LEFT = 2045-End--> |
| KEYCODE_ALT_RIGHT = 2046 | 右Alt键<br><!--Device-KEYCODE_ALT_RIGHT = 2046--><!--Device-KEYCODE_ALT_RIGHT = 2046-End--> |
| KEYCODE_SHIFT_LEFT = 2047 | 左Shift键<br><!--Device-KEYCODE_SHIFT_LEFT = 2047--><!--Device-KEYCODE_SHIFT_LEFT = 2047-End--> |
| KEYCODE_SHIFT_RIGHT = 2048 | 右Shift键<br><!--Device-KEYCODE_SHIFT_RIGHT = 2048--><!--Device-KEYCODE_SHIFT_RIGHT = 2048-End--> |
| KEYCODE_TAB = 2049 | Tab键<br><!--Device-KEYCODE_TAB = 2049--><!--Device-KEYCODE_TAB = 2049-End--> |
| KEYCODE_SPACE = 2050 | 空格键<br><!--Device-KEYCODE_SPACE = 2050--><!--Device-KEYCODE_SPACE = 2050-End--> |
| KEYCODE_SYM = 2051 | 符号修改器按键<br><!--Device-KEYCODE_SYM = 2051--><!--Device-KEYCODE_SYM = 2051-End--> |
| KEYCODE_EXPLORER = 2052 | 浏览器功能键，此键用于启动浏览器应用程序。<br><!--Device-KEYCODE_EXPLORER = 2052--><!--Device-KEYCODE_EXPLORER = 2052-End--> |
| KEYCODE_ENVELOPE = 2053 | 电子邮件功能键，此键用于启动电子邮件应用程序。<br><!--Device-KEYCODE_ENVELOPE = 2053--><!--Device-KEYCODE_ENVELOPE = 2053-End--> |
| KEYCODE_ENTER = 2054 | 回车键<br><!--Device-KEYCODE_ENTER = 2054--><!--Device-KEYCODE_ENTER = 2054-End--> |
| KEYCODE_DEL = 2055 | 退格键<br><!--Device-KEYCODE_DEL = 2055--><!--Device-KEYCODE_DEL = 2055-End--> |
| KEYCODE_GRAVE = 2056 | 按键'`'<br><!--Device-KEYCODE_GRAVE = 2056--><!--Device-KEYCODE_GRAVE = 2056-End--> |
| KEYCODE_MINUS = 2057 | 按键'-'<br><!--Device-KEYCODE_MINUS = 2057--><!--Device-KEYCODE_MINUS = 2057-End--> |
| KEYCODE_EQUALS = 2058 | 按键'='<br><!--Device-KEYCODE_EQUALS = 2058--><!--Device-KEYCODE_EQUALS = 2058-End--> |
| KEYCODE_LEFT_BRACKET = 2059 | 按键'['<br><!--Device-KEYCODE_LEFT_BRACKET = 2059--><!--Device-KEYCODE_LEFT_BRACKET = 2059-End--> |
| KEYCODE_RIGHT_BRACKET = 2060 | 按键']'<br><!--Device-KEYCODE_RIGHT_BRACKET = 2060--><!--Device-KEYCODE_RIGHT_BRACKET = 2060-End--> |
| KEYCODE_BACKSLASH = 2061 | 按键'\'<br>**起始版本：** 12<br><!--Device-KEYCODE_BACKSLASH = 2061--><!--Device-KEYCODE_BACKSLASH = 2061-End--> |
| KEYCODE_SEMICOLON = 2062 | 按键';'<br><!--Device-KEYCODE_SEMICOLON = 2062--><!--Device-KEYCODE_SEMICOLON = 2062-End--> |
| KEYCODE_APOSTROPHE = 2063 | 按键'''（单引号）<br>**起始版本：** 12<br><!--Device-KEYCODE_APOSTROPHE = 2063--><!--Device-KEYCODE_APOSTROPHE = 2063-End--> |
| KEYCODE_SLASH = 2064 | 按键'/'<br>**起始版本：** 12<br><!--Device-KEYCODE_SLASH = 2064--><!--Device-KEYCODE_SLASH = 2064-End--> |
| KEYCODE_AT = 2065 | 按键'@'<br><!--Device-KEYCODE_AT = 2065--><!--Device-KEYCODE_AT = 2065-End--> |
| KEYCODE_PLUS = 2066 | 按键'+'<br><!--Device-KEYCODE_PLUS = 2066--><!--Device-KEYCODE_PLUS = 2066-End--> |
| KEYCODE_MENU = 2067 | 菜单键<br><!--Device-KEYCODE_MENU = 2067--><!--Device-KEYCODE_MENU = 2067-End--> |
| KEYCODE_PAGE_UP = 2068 | 向上翻页键<br><!--Device-KEYCODE_PAGE_UP = 2068--><!--Device-KEYCODE_PAGE_UP = 2068-End--> |
| KEYCODE_PAGE_DOWN = 2069 | 向下翻页键<br><!--Device-KEYCODE_PAGE_DOWN = 2069--><!--Device-KEYCODE_PAGE_DOWN = 2069-End--> |
| KEYCODE_ESCAPE = 2070 | Esc键<br><!--Device-KEYCODE_ESCAPE = 2070--><!--Device-KEYCODE_ESCAPE = 2070-End--> |
| KEYCODE_FORWARD_DEL = 2071 | 删除键<br><!--Device-KEYCODE_FORWARD_DEL = 2071--><!--Device-KEYCODE_FORWARD_DEL = 2071-End--> |
| KEYCODE_CTRL_LEFT = 2072 | 左Ctrl键<br><!--Device-KEYCODE_CTRL_LEFT = 2072--><!--Device-KEYCODE_CTRL_LEFT = 2072-End--> |
| KEYCODE_CTRL_RIGHT = 2073 | 右Ctrl键<br><!--Device-KEYCODE_CTRL_RIGHT = 2073--><!--Device-KEYCODE_CTRL_RIGHT = 2073-End--> |
| KEYCODE_CAPS_LOCK = 2074 | 大写锁定键<br><!--Device-KEYCODE_CAPS_LOCK = 2074--><!--Device-KEYCODE_CAPS_LOCK = 2074-End--> |
| KEYCODE_SCROLL_LOCK = 2075 | 滚动锁定键<br><!--Device-KEYCODE_SCROLL_LOCK = 2075--><!--Device-KEYCODE_SCROLL_LOCK = 2075-End--> |
| KEYCODE_META_LEFT = 2076 | 左Meta键<br><!--Device-KEYCODE_META_LEFT = 2076--><!--Device-KEYCODE_META_LEFT = 2076-End--> |
| KEYCODE_META_RIGHT = 2077 | 右Meta键<br><!--Device-KEYCODE_META_RIGHT = 2077--><!--Device-KEYCODE_META_RIGHT = 2077-End--> |
| KEYCODE_FUNCTION = 2078 | 功能键<br><!--Device-KEYCODE_FUNCTION = 2078--><!--Device-KEYCODE_FUNCTION = 2078-End--> |
| KEYCODE_SYSRQ = 2079 | 系统请求/打印屏幕键<br><!--Device-KEYCODE_SYSRQ = 2079--><!--Device-KEYCODE_SYSRQ = 2079-End--> |
| KEYCODE_BREAK = 2080 | Break/Pause键<br><!--Device-KEYCODE_BREAK = 2080--><!--Device-KEYCODE_BREAK = 2080-End--> |
| KEYCODE_MOVE_HOME = 2081 | 光标移动到开始键<br><!--Device-KEYCODE_MOVE_HOME = 2081--><!--Device-KEYCODE_MOVE_HOME = 2081-End--> |
| KEYCODE_MOVE_END = 2082 | 光标移动到末尾键<br><!--Device-KEYCODE_MOVE_END = 2082--><!--Device-KEYCODE_MOVE_END = 2082-End--> |
| KEYCODE_INSERT = 2083 | 插入键<br><!--Device-KEYCODE_INSERT = 2083--><!--Device-KEYCODE_INSERT = 2083-End--> |
| KEYCODE_FORWARD = 2084 | 前进键<br><!--Device-KEYCODE_FORWARD = 2084--><!--Device-KEYCODE_FORWARD = 2084-End--> |
| KEYCODE_MEDIA_PLAY = 2085 | 多媒体键：播放<br><!--Device-KEYCODE_MEDIA_PLAY = 2085--><!--Device-KEYCODE_MEDIA_PLAY = 2085-End--> |
| KEYCODE_MEDIA_PAUSE = 2086 | 光盘暂停键<br><!--Device-KEYCODE_MEDIA_PAUSE = 2086--><!--Device-KEYCODE_MEDIA_PAUSE = 2086-End--> |
| KEYCODE_MEDIA_CLOSE = 2087 | 光盘关闭键<br><!--Device-KEYCODE_MEDIA_CLOSE = 2087--><!--Device-KEYCODE_MEDIA_CLOSE = 2087-End--> |
| KEYCODE_MEDIA_EJECT = 2088 | 光盘弹出键<br>**起始版本：** 12<br><!--Device-KEYCODE_MEDIA_EJECT = 2088--><!--Device-KEYCODE_MEDIA_EJECT = 2088-End--> |
| KEYCODE_MEDIA_RECORD = 2089 | 多媒体键：录音<br><!--Device-KEYCODE_MEDIA_RECORD = 2089--><!--Device-KEYCODE_MEDIA_RECORD = 2089-End--> |
| KEYCODE_F1 = 2090 | 按键'F1'<br><!--Device-KEYCODE_F1 = 2090--><!--Device-KEYCODE_F1 = 2090-End--> |
| KEYCODE_F2 = 2091 | 按键'F2'<br><!--Device-KEYCODE_F2 = 2091--><!--Device-KEYCODE_F2 = 2091-End--> |
| KEYCODE_F3 = 2092 | 按键'F3'<br><!--Device-KEYCODE_F3 = 2092--><!--Device-KEYCODE_F3 = 2092-End--> |
| KEYCODE_F4 = 2093 | 按键'F4'<br><!--Device-KEYCODE_F4 = 2093--><!--Device-KEYCODE_F4 = 2093-End--> |
| KEYCODE_F5 = 2094 | 按键'F5'<br><!--Device-KEYCODE_F5 = 2094--><!--Device-KEYCODE_F5 = 2094-End--> |
| KEYCODE_F6 = 2095 | 按键'F6'<br><!--Device-KEYCODE_F6 = 2095--><!--Device-KEYCODE_F6 = 2095-End--> |
| KEYCODE_F7 = 2096 | 按键'F7'<br><!--Device-KEYCODE_F7 = 2096--><!--Device-KEYCODE_F7 = 2096-End--> |
| KEYCODE_F8 = 2097 | 按键'F8'<br><!--Device-KEYCODE_F8 = 2097--><!--Device-KEYCODE_F8 = 2097-End--> |
| KEYCODE_F9 = 2098 | 按键'F9'<br><!--Device-KEYCODE_F9 = 2098--><!--Device-KEYCODE_F9 = 2098-End--> |
| KEYCODE_F10 = 2099 | 按键'F10'<br><!--Device-KEYCODE_F10 = 2099--><!--Device-KEYCODE_F10 = 2099-End--> |
| KEYCODE_F11 = 2100 | 按键'F11'<br><!--Device-KEYCODE_F11 = 2100--><!--Device-KEYCODE_F11 = 2100-End--> |
| KEYCODE_F12 = 2101 | 按键'F12'<br><!--Device-KEYCODE_F12 = 2101--><!--Device-KEYCODE_F12 = 2101-End--> |
| KEYCODE_NUM_LOCK = 2102 | 小键盘锁<br><!--Device-KEYCODE_NUM_LOCK = 2102--><!--Device-KEYCODE_NUM_LOCK = 2102-End--> |
| KEYCODE_NUMPAD_0 = 2103 | 小键盘按键'0'<br><!--Device-KEYCODE_NUMPAD_0 = 2103--><!--Device-KEYCODE_NUMPAD_0 = 2103-End--> |
| KEYCODE_NUMPAD_1 = 2104 | 小键盘按键'1'<br><!--Device-KEYCODE_NUMPAD_1 = 2104--><!--Device-KEYCODE_NUMPAD_1 = 2104-End--> |
| KEYCODE_NUMPAD_2 = 2105 | 小键盘按键'2'<br><!--Device-KEYCODE_NUMPAD_2 = 2105--><!--Device-KEYCODE_NUMPAD_2 = 2105-End--> |
| KEYCODE_NUMPAD_3 = 2106 | 小键盘按键'3'<br><!--Device-KEYCODE_NUMPAD_3 = 2106--><!--Device-KEYCODE_NUMPAD_3 = 2106-End--> |
| KEYCODE_NUMPAD_4 = 2107 | 小键盘按键'4'<br><!--Device-KEYCODE_NUMPAD_4 = 2107--><!--Device-KEYCODE_NUMPAD_4 = 2107-End--> |
| KEYCODE_NUMPAD_5 = 2108 | 小键盘按键'5'<br><!--Device-KEYCODE_NUMPAD_5 = 2108--><!--Device-KEYCODE_NUMPAD_5 = 2108-End--> |
| KEYCODE_NUMPAD_6 = 2109 | 小键盘按键'6'<br><!--Device-KEYCODE_NUMPAD_6 = 2109--><!--Device-KEYCODE_NUMPAD_6 = 2109-End--> |
| KEYCODE_NUMPAD_7 = 2110 | 小键盘按键'7'<br><!--Device-KEYCODE_NUMPAD_7 = 2110--><!--Device-KEYCODE_NUMPAD_7 = 2110-End--> |
| KEYCODE_NUMPAD_8 = 2111 | 小键盘按键'8'<br><!--Device-KEYCODE_NUMPAD_8 = 2111--><!--Device-KEYCODE_NUMPAD_8 = 2111-End--> |
| KEYCODE_NUMPAD_9 = 2112 | 小键盘按键'9'<br><!--Device-KEYCODE_NUMPAD_9 = 2112--><!--Device-KEYCODE_NUMPAD_9 = 2112-End--> |
| KEYCODE_NUMPAD_DIVIDE = 2113 | 小键盘按键'/'<br><!--Device-KEYCODE_NUMPAD_DIVIDE = 2113--><!--Device-KEYCODE_NUMPAD_DIVIDE = 2113-End--> |
| KEYCODE_NUMPAD_MULTIPLY = 2114 | 小键盘按键'*'<br><!--Device-KEYCODE_NUMPAD_MULTIPLY = 2114--><!--Device-KEYCODE_NUMPAD_MULTIPLY = 2114-End--> |
| KEYCODE_NUMPAD_SUBTRACT = 2115 | 小键盘按键'-'<br><!--Device-KEYCODE_NUMPAD_SUBTRACT = 2115--><!--Device-KEYCODE_NUMPAD_SUBTRACT = 2115-End--> |
| KEYCODE_NUMPAD_ADD = 2116 | 小键盘按键'+'<br><!--Device-KEYCODE_NUMPAD_ADD = 2116--><!--Device-KEYCODE_NUMPAD_ADD = 2116-End--> |
| KEYCODE_NUMPAD_DOT = 2117 | 小键盘按键'.'<br><!--Device-KEYCODE_NUMPAD_DOT = 2117--><!--Device-KEYCODE_NUMPAD_DOT = 2117-End--> |
| KEYCODE_NUMPAD_COMMA = 2118 | 小键盘按键','<br><!--Device-KEYCODE_NUMPAD_COMMA = 2118--><!--Device-KEYCODE_NUMPAD_COMMA = 2118-End--> |
| KEYCODE_NUMPAD_ENTER = 2119 | 小键盘按键回车<br><!--Device-KEYCODE_NUMPAD_ENTER = 2119--><!--Device-KEYCODE_NUMPAD_ENTER = 2119-End--> |
| KEYCODE_NUMPAD_EQUALS = 2120 | 小键盘按键'='<br><!--Device-KEYCODE_NUMPAD_EQUALS = 2120--><!--Device-KEYCODE_NUMPAD_EQUALS = 2120-End--> |
| KEYCODE_NUMPAD_LEFT_PAREN = 2121 | 小键盘按键'('<br><!--Device-KEYCODE_NUMPAD_LEFT_PAREN = 2121--><!--Device-KEYCODE_NUMPAD_LEFT_PAREN = 2121-End--> |
| KEYCODE_NUMPAD_RIGHT_PAREN = 2122 | 小键盘按键')'<br><!--Device-KEYCODE_NUMPAD_RIGHT_PAREN = 2122--><!--Device-KEYCODE_NUMPAD_RIGHT_PAREN = 2122-End--> |
| KEYCODE_VIRTUAL_MULTITASK = 2210 | 虚拟多任务键<br>**起始版本：** 22<br><!--Device-KEYCODE_VIRTUAL_MULTITASK = 2210--><!--Device-KEYCODE_VIRTUAL_MULTITASK = 2210-End--> |
| KEYCODE_BUTTON_A = 2301 | 游戏手柄按键'A'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_A = 2301--><!--Device-KEYCODE_BUTTON_A = 2301-End--> |
| KEYCODE_BUTTON_B = 2302 | 游戏手柄按键'B'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_B = 2302--><!--Device-KEYCODE_BUTTON_B = 2302-End--> |
| KEYCODE_BUTTON_X = 2304 | 游戏手柄按键'X'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_X = 2304--><!--Device-KEYCODE_BUTTON_X = 2304-End--> |
| KEYCODE_BUTTON_Y = 2305 | 游戏手柄按键'Y'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_Y = 2305--><!--Device-KEYCODE_BUTTON_Y = 2305-End--> |
| KEYCODE_BUTTON_L1 = 2307 | 游戏手柄按键'L1'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_L1 = 2307--><!--Device-KEYCODE_BUTTON_L1 = 2307-End--> |
| KEYCODE_BUTTON_R1 = 2308 | 游戏手柄按键'R1'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_R1 = 2308--><!--Device-KEYCODE_BUTTON_R1 = 2308-End--> |
| KEYCODE_BUTTON_L2 = 2309 | 游戏手柄按键'L2'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_L2 = 2309--><!--Device-KEYCODE_BUTTON_L2 = 2309-End--> |
| KEYCODE_BUTTON_R2 = 2310 | 游戏手柄按键'R2'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_R2 = 2310--><!--Device-KEYCODE_BUTTON_R2 = 2310-End--> |
| KEYCODE_BUTTON_SELECT = 2311 | 游戏手柄按键'Select'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_SELECT = 2311--><!--Device-KEYCODE_BUTTON_SELECT = 2311-End--> |
| KEYCODE_BUTTON_START = 2312 | 游戏手柄按键'Start'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_START = 2312--><!--Device-KEYCODE_BUTTON_START = 2312-End--> |
| KEYCODE_BUTTON_MODE = 2313 | 游戏手柄按键'Mode'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_MODE = 2313--><!--Device-KEYCODE_BUTTON_MODE = 2313-End--> |
| KEYCODE_BUTTON_THUMBL = 2314 | 游戏手柄按键'THUMBL'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_THUMBL = 2314--><!--Device-KEYCODE_BUTTON_THUMBL = 2314-End--> |
| KEYCODE_BUTTON_THUMBR = 2315 | 游戏手柄按键'THUMBR'<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTON_THUMBR = 2315--><!--Device-KEYCODE_BUTTON_THUMBR = 2315-End--> |
| KEYCODE_SLEEP = 2600 | 睡眠键<br>**起始版本：** 22<br><!--Device-KEYCODE_SLEEP = 2600--><!--Device-KEYCODE_SLEEP = 2600-End--> |
| KEYCODE_ZENKAKU_HANKAKU = 2601 | 日文全宽/半宽键<br>**起始版本：** 22<br><!--Device-KEYCODE_ZENKAKU_HANKAKU = 2601--><!--Device-KEYCODE_ZENKAKU_HANKAKU = 2601-End--> |
| KEYCODE_102ND = 2602 | 国际键盘扩展键<br>**起始版本：** 22<br><!--Device-KEYCODE_102ND = 2602--><!--Device-KEYCODE_102ND = 2602-End--> |
| KEYCODE_RO = 2603 | 日文Ro键<br>**起始版本：** 22<br><!--Device-KEYCODE_RO = 2603--><!--Device-KEYCODE_RO = 2603-End--> |
| KEYCODE_KATAKANA = 2604 | 日文片假名键<br>**起始版本：** 22<br><!--Device-KEYCODE_KATAKANA = 2604--><!--Device-KEYCODE_KATAKANA = 2604-End--> |
| KEYCODE_HIRAGANA = 2605 | 日文平假名键<br>**起始版本：** 22<br><!--Device-KEYCODE_HIRAGANA = 2605--><!--Device-KEYCODE_HIRAGANA = 2605-End--> |
| KEYCODE_HENKAN = 2606 | 日文转换键<br>**起始版本：** 22<br><!--Device-KEYCODE_HENKAN = 2606--><!--Device-KEYCODE_HENKAN = 2606-End--> |
| KEYCODE_KATAKANA_HIRAGANA = 2607 | 日语片假名/平假名键<br>**起始版本：** 22<br><!--Device-KEYCODE_KATAKANA_HIRAGANA = 2607--><!--Device-KEYCODE_KATAKANA_HIRAGANA = 2607-End--> |
| KEYCODE_MUHENKAN = 2608 | 日文非转换键<br>**起始版本：** 22<br><!--Device-KEYCODE_MUHENKAN = 2608--><!--Device-KEYCODE_MUHENKAN = 2608-End--> |
| KEYCODE_LINEFEED = 2609 | 换行键<br>**起始版本：** 22<br><!--Device-KEYCODE_LINEFEED = 2609--><!--Device-KEYCODE_LINEFEED = 2609-End--> |
| KEYCODE_MACRO = 2610 | 宏键<br>**起始版本：** 22<br><!--Device-KEYCODE_MACRO = 2610--><!--Device-KEYCODE_MACRO = 2610-End--> |
| KEYCODE_NUMPAD_PLUSMINUS = 2611 | 数字键盘上的加号/减号键<br>**起始版本：** 22<br><!--Device-KEYCODE_NUMPAD_PLUSMINUS = 2611--><!--Device-KEYCODE_NUMPAD_PLUSMINUS = 2611-End--> |
| KEYCODE_SCALE = 2612 | 扩展键<br>**起始版本：** 22<br><!--Device-KEYCODE_SCALE = 2612--><!--Device-KEYCODE_SCALE = 2612-End--> |
| KEYCODE_HANGUEL = 2613 | 韩文键<br>**起始版本：** 22<br><!--Device-KEYCODE_HANGUEL = 2613--><!--Device-KEYCODE_HANGUEL = 2613-End--> |
| KEYCODE_HANJA = 2614 | 韩文汉字键<br>**起始版本：** 22<br><!--Device-KEYCODE_HANJA = 2614--><!--Device-KEYCODE_HANJA = 2614-End--> |
| KEYCODE_YEN = 2615 | 日元键<br>**起始版本：** 22<br><!--Device-KEYCODE_YEN = 2615--><!--Device-KEYCODE_YEN = 2615-End--> |
| KEYCODE_STOP = 2616 | 停止键<br>**起始版本：** 22<br><!--Device-KEYCODE_STOP = 2616--><!--Device-KEYCODE_STOP = 2616-End--> |
| KEYCODE_AGAIN = 2617 | 重复键<br>**起始版本：** 22<br><!--Device-KEYCODE_AGAIN = 2617--><!--Device-KEYCODE_AGAIN = 2617-End--> |
| KEYCODE_PROPS = 2618 | 道具键<br>**起始版本：** 22<br><!--Device-KEYCODE_PROPS = 2618--><!--Device-KEYCODE_PROPS = 2618-End--> |
| KEYCODE_UNDO = 2619 | 撤销键<br>**起始版本：** 22<br><!--Device-KEYCODE_UNDO = 2619--><!--Device-KEYCODE_UNDO = 2619-End--> |
| KEYCODE_COPY = 2620 | 复制键<br>**起始版本：** 22<br><!--Device-KEYCODE_COPY = 2620--><!--Device-KEYCODE_COPY = 2620-End--> |
| KEYCODE_OPEN = 2621 | 打开键<br>**起始版本：** 22<br><!--Device-KEYCODE_OPEN = 2621--><!--Device-KEYCODE_OPEN = 2621-End--> |
| KEYCODE_PASTE = 2622 | 粘贴键<br>**起始版本：** 22<br><!--Device-KEYCODE_PASTE = 2622--><!--Device-KEYCODE_PASTE = 2622-End--> |
| KEYCODE_FIND = 2623 | 查找键<br>**起始版本：** 22<br><!--Device-KEYCODE_FIND = 2623--><!--Device-KEYCODE_FIND = 2623-End--> |
| KEYCODE_CUT = 2624 | 剪切键<br>**起始版本：** 22<br><!--Device-KEYCODE_CUT = 2624--><!--Device-KEYCODE_CUT = 2624-End--> |
| KEYCODE_HELP = 2625 | 帮助键<br>**起始版本：** 22<br><!--Device-KEYCODE_HELP = 2625--><!--Device-KEYCODE_HELP = 2625-End--> |
| KEYCODE_CALC = 2626 | 计算器特殊功能键，用于启动计算器应用程序。<br>**起始版本：** 22<br><!--Device-KEYCODE_CALC = 2626--><!--Device-KEYCODE_CALC = 2626-End--> |
| KEYCODE_FILE = 2627 | 文件按键<br>**起始版本：** 22<br><!--Device-KEYCODE_FILE = 2627--><!--Device-KEYCODE_FILE = 2627-End--> |
| KEYCODE_BOOKMARKS = 2628 | 书签键<br>**起始版本：** 22<br><!--Device-KEYCODE_BOOKMARKS = 2628--><!--Device-KEYCODE_BOOKMARKS = 2628-End--> |
| KEYCODE_NEXT = 2629 | Page Down键<br>**起始版本：** 22<br><!--Device-KEYCODE_NEXT = 2629--><!--Device-KEYCODE_NEXT = 2629-End--> |
| KEYCODE_PLAYPAUSE = 2630 | 多媒体键：播放/暂停。<br/>与KEYCODE_MEDIA_PLAY_PAUSE的区别为：<br/>KEYCODE_PLAYPAUSE是较早的定义， KEYCODE_MEDIA_PLAY_PAUSE为现代媒体键设备设计，常见于较新的媒体键设备。<br>**起始版本：** 22<br><!--Device-KEYCODE_PLAYPAUSE = 2630--><!--Device-KEYCODE_PLAYPAUSE = 2630-End--> |
| KEYCODE_PREVIOUS = 2631 | Page Up键<br>**起始版本：** 22<br><!--Device-KEYCODE_PREVIOUS = 2631--><!--Device-KEYCODE_PREVIOUS = 2631-End--> |
| KEYCODE_STOPCD = 2632 | CD停止键<br>**起始版本：** 22<br><!--Device-KEYCODE_STOPCD = 2632--><!--Device-KEYCODE_STOPCD = 2632-End--> |
| KEYCODE_CONFIG = 2634 | 配置键<br>**起始版本：** 22<br><!--Device-KEYCODE_CONFIG = 2634--><!--Device-KEYCODE_CONFIG = 2634-End--> |
| KEYCODE_REFRESH = 2635 | 刷新键<br>**起始版本：** 22<br><!--Device-KEYCODE_REFRESH = 2635--><!--Device-KEYCODE_REFRESH = 2635-End--> |
| KEYCODE_EXIT = 2636 | 退出键<br>**起始版本：** 22<br><!--Device-KEYCODE_EXIT = 2636--><!--Device-KEYCODE_EXIT = 2636-End--> |
| KEYCODE_EDIT = 2637 | 编辑键<br>**起始版本：** 22<br><!--Device-KEYCODE_EDIT = 2637--><!--Device-KEYCODE_EDIT = 2637-End--> |
| KEYCODE_SCROLLUP = 2638 | 向上滚动键<br>**起始版本：** 22<br><!--Device-KEYCODE_SCROLLUP = 2638--><!--Device-KEYCODE_SCROLLUP = 2638-End--> |
| KEYCODE_SCROLLDOWN = 2639 | 向下滚动键<br>**起始版本：** 22<br><!--Device-KEYCODE_SCROLLDOWN = 2639--><!--Device-KEYCODE_SCROLLDOWN = 2639-End--> |
| KEYCODE_NEW = 2640 | 新建键<br>**起始版本：** 22<br><!--Device-KEYCODE_NEW = 2640--><!--Device-KEYCODE_NEW = 2640-End--> |
| KEYCODE_REDO = 2641 | 恢复键<br>**起始版本：** 22<br><!--Device-KEYCODE_REDO = 2641--><!--Device-KEYCODE_REDO = 2641-End--> |
| KEYCODE_CLOSE = 2642 | 关闭键<br>**起始版本：** 22<br><!--Device-KEYCODE_CLOSE = 2642--><!--Device-KEYCODE_CLOSE = 2642-End--> |
| KEYCODE_PLAY = 2643 | 播放键<br>**起始版本：** 22<br><!--Device-KEYCODE_PLAY = 2643--><!--Device-KEYCODE_PLAY = 2643-End--> |
| KEYCODE_BASSBOOST = 2644 | 低音增强键<br>**起始版本：** 22<br><!--Device-KEYCODE_BASSBOOST = 2644--><!--Device-KEYCODE_BASSBOOST = 2644-End--> |
| KEYCODE_PRINT = 2645 | 打印键<br>**起始版本：** 22<br><!--Device-KEYCODE_PRINT = 2645--><!--Device-KEYCODE_PRINT = 2645-End--> |
| KEYCODE_CHAT = 2646 | 聊天键<br>**起始版本：** 22<br><!--Device-KEYCODE_CHAT = 2646--><!--Device-KEYCODE_CHAT = 2646-End--> |
| KEYCODE_FINANCE = 2647 | 金融键<br>**起始版本：** 22<br><!--Device-KEYCODE_FINANCE = 2647--><!--Device-KEYCODE_FINANCE = 2647-End--> |
| KEYCODE_CANCEL = 2648 | 取消键<br>**起始版本：** 22<br><!--Device-KEYCODE_CANCEL = 2648--><!--Device-KEYCODE_CANCEL = 2648-End--> |
| KEYCODE_KBDILLUM_TOGGLE = 2649 | 键盘灯光切换键<br>**起始版本：** 22<br><!--Device-KEYCODE_KBDILLUM_TOGGLE = 2649--><!--Device-KEYCODE_KBDILLUM_TOGGLE = 2649-End--> |
| KEYCODE_KBDILLUM_DOWN = 2650 | 键盘灯光调暗键<br>**起始版本：** 22<br><!--Device-KEYCODE_KBDILLUM_DOWN = 2650--><!--Device-KEYCODE_KBDILLUM_DOWN = 2650-End--> |
| KEYCODE_KBDILLUM_UP = 2651 | 键盘灯光调亮键<br>**起始版本：** 22<br><!--Device-KEYCODE_KBDILLUM_UP = 2651--><!--Device-KEYCODE_KBDILLUM_UP = 2651-End--> |
| KEYCODE_SEND = 2652 | 发送键<br>**起始版本：** 22<br><!--Device-KEYCODE_SEND = 2652--><!--Device-KEYCODE_SEND = 2652-End--> |
| KEYCODE_REPLY = 2653 | 答复键<br>**起始版本：** 22<br><!--Device-KEYCODE_REPLY = 2653--><!--Device-KEYCODE_REPLY = 2653-End--> |
| KEYCODE_FORWARDMAIL = 2654 | 邮件转发键<br>**起始版本：** 22<br><!--Device-KEYCODE_FORWARDMAIL = 2654--><!--Device-KEYCODE_FORWARDMAIL = 2654-End--> |
| KEYCODE_SAVE = 2655 | 保存键<br>**起始版本：** 22<br><!--Device-KEYCODE_SAVE = 2655--><!--Device-KEYCODE_SAVE = 2655-End--> |
| KEYCODE_DOCUMENTS = 2656 | 文件键<br>**起始版本：** 22<br><!--Device-KEYCODE_DOCUMENTS = 2656--><!--Device-KEYCODE_DOCUMENTS = 2656-End--> |
| KEYCODE_VIDEO_NEXT = 2657 | 下一个视频键<br>**起始版本：** 22<br><!--Device-KEYCODE_VIDEO_NEXT = 2657--><!--Device-KEYCODE_VIDEO_NEXT = 2657-End--> |
| KEYCODE_VIDEO_PREV = 2658 | 上一个视频键<br>**起始版本：** 22<br><!--Device-KEYCODE_VIDEO_PREV = 2658--><!--Device-KEYCODE_VIDEO_PREV = 2658-End--> |
| KEYCODE_BRIGHTNESS_CYCLE = 2659 | 背光渐变键<br>**起始版本：** 22<br><!--Device-KEYCODE_BRIGHTNESS_CYCLE = 2659--><!--Device-KEYCODE_BRIGHTNESS_CYCLE = 2659-End--> |
| KEYCODE_BRIGHTNESS_ZERO = 2660 | 亮度调节为0键<br>**起始版本：** 22<br><!--Device-KEYCODE_BRIGHTNESS_ZERO = 2660--><!--Device-KEYCODE_BRIGHTNESS_ZERO = 2660-End--> |
| KEYCODE_DISPLAY_OFF = 2661 | 显示关闭键<br>**起始版本：** 22<br><!--Device-KEYCODE_DISPLAY_OFF = 2661--><!--Device-KEYCODE_DISPLAY_OFF = 2661-End--> |
| KEYCODE_BTN_MISC = 2662 | 游戏手柄上的各种按键<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_MISC = 2662--><!--Device-KEYCODE_BTN_MISC = 2662-End--> |
| KEYCODE_GOTO = 2663 | 进入键<br>**起始版本：** 22<br><!--Device-KEYCODE_GOTO = 2663--><!--Device-KEYCODE_GOTO = 2663-End--> |
| KEYCODE_INFO = 2664 | 信息查看键<br>**起始版本：** 22<br><!--Device-KEYCODE_INFO = 2664--><!--Device-KEYCODE_INFO = 2664-End--> |
| KEYCODE_PROGRAM = 2665 | 程序键<br>**起始版本：** 22<br><!--Device-KEYCODE_PROGRAM = 2665--><!--Device-KEYCODE_PROGRAM = 2665-End--> |
| KEYCODE_PVR = 2666 | 个人录像机（PVR）键<br>**起始版本：** 22<br><!--Device-KEYCODE_PVR = 2666--><!--Device-KEYCODE_PVR = 2666-End--> |
| KEYCODE_SUBTITLE = 2667 | 字幕键<br>**起始版本：** 22<br><!--Device-KEYCODE_SUBTITLE = 2667--><!--Device-KEYCODE_SUBTITLE = 2667-End--> |
| KEYCODE_FULL_SCREEN = 2668 | 全屏键<br>**起始版本：** 22<br><!--Device-KEYCODE_FULL_SCREEN = 2668--><!--Device-KEYCODE_FULL_SCREEN = 2668-End--> |
| KEYCODE_KEYBOARD = 2669 | 键盘<br>**起始版本：** 22<br><!--Device-KEYCODE_KEYBOARD = 2669--><!--Device-KEYCODE_KEYBOARD = 2669-End--> |
| KEYCODE_ASPECT_RATIO = 2670 | 屏幕纵横比调节键<br>**起始版本：** 22<br><!--Device-KEYCODE_ASPECT_RATIO = 2670--><!--Device-KEYCODE_ASPECT_RATIO = 2670-End--> |
| KEYCODE_PC = 2671 | 端口控制键<br>**起始版本：** 22<br><!--Device-KEYCODE_PC = 2671--><!--Device-KEYCODE_PC = 2671-End--> |
| KEYCODE_TV = 2672 | TV键<br>**起始版本：** 22<br><!--Device-KEYCODE_TV = 2672--><!--Device-KEYCODE_TV = 2672-End--> |
| KEYCODE_TV2 = 2673 | TV键2<br>**起始版本：** 22<br><!--Device-KEYCODE_TV2 = 2673--><!--Device-KEYCODE_TV2 = 2673-End--> |
| KEYCODE_VCR = 2674 | 录像机开启键<br>**起始版本：** 22<br><!--Device-KEYCODE_VCR = 2674--><!--Device-KEYCODE_VCR = 2674-End--> |
| KEYCODE_VCR2 = 2675 | 录像机开启键2<br>**起始版本：** 22<br><!--Device-KEYCODE_VCR2 = 2675--><!--Device-KEYCODE_VCR2 = 2675-End--> |
| KEYCODE_SAT = 2676 | SIM卡应用工具包（SAT）键<br>**起始版本：** 22<br><!--Device-KEYCODE_SAT = 2676--><!--Device-KEYCODE_SAT = 2676-End--> |
| KEYCODE_CD = 2677 | CD键<br>**起始版本：** 22<br><!--Device-KEYCODE_CD = 2677--><!--Device-KEYCODE_CD = 2677-End--> |
| KEYCODE_TAPE = 2678 | 磁带键<br>**起始版本：** 22<br><!--Device-KEYCODE_TAPE = 2678--><!--Device-KEYCODE_TAPE = 2678-End--> |
| KEYCODE_TUNER = 2679 | 调谐器键<br>**起始版本：** 22<br><!--Device-KEYCODE_TUNER = 2679--><!--Device-KEYCODE_TUNER = 2679-End--> |
| KEYCODE_PLAYER = 2680 | 播放器键<br>**起始版本：** 22<br><!--Device-KEYCODE_PLAYER = 2680--><!--Device-KEYCODE_PLAYER = 2680-End--> |
| KEYCODE_DVD = 2681 | DVD键<br>**起始版本：** 22<br><!--Device-KEYCODE_DVD = 2681--><!--Device-KEYCODE_DVD = 2681-End--> |
| KEYCODE_AUDIO = 2682 | 音频键<br>**起始版本：** 22<br><!--Device-KEYCODE_AUDIO = 2682--><!--Device-KEYCODE_AUDIO = 2682-End--> |
| KEYCODE_VIDEO = 2683 | 视频键<br>**起始版本：** 22<br><!--Device-KEYCODE_VIDEO = 2683--><!--Device-KEYCODE_VIDEO = 2683-End--> |
| KEYCODE_MEMO = 2684 | 备忘录键<br>**起始版本：** 22<br><!--Device-KEYCODE_MEMO = 2684--><!--Device-KEYCODE_MEMO = 2684-End--> |
| KEYCODE_CALENDAR = 2685 | 日历键<br>**起始版本：** 22<br><!--Device-KEYCODE_CALENDAR = 2685--><!--Device-KEYCODE_CALENDAR = 2685-End--> |
| KEYCODE_RED = 2686 | 红色指示器键<br>**起始版本：** 22<br><!--Device-KEYCODE_RED = 2686--><!--Device-KEYCODE_RED = 2686-End--> |
| KEYCODE_GREEN = 2687 | 绿色指示器键<br>**起始版本：** 22<br><!--Device-KEYCODE_GREEN = 2687--><!--Device-KEYCODE_GREEN = 2687-End--> |
| KEYCODE_YELLOW = 2688 | 黄色指示器键<br>**起始版本：** 22<br><!--Device-KEYCODE_YELLOW = 2688--><!--Device-KEYCODE_YELLOW = 2688-End--> |
| KEYCODE_BLUE = 2689 | 蓝色指示器键<br>**起始版本：** 22<br><!--Device-KEYCODE_BLUE = 2689--><!--Device-KEYCODE_BLUE = 2689-End--> |
| KEYCODE_CHANNELUP = 2690 | 频道向上键<br>**起始版本：** 22<br><!--Device-KEYCODE_CHANNELUP = 2690--><!--Device-KEYCODE_CHANNELUP = 2690-End--> |
| KEYCODE_CHANNELDOWN = 2691 | 频道向下键<br>**起始版本：** 22<br><!--Device-KEYCODE_CHANNELDOWN = 2691--><!--Device-KEYCODE_CHANNELDOWN = 2691-End--> |
| KEYCODE_LAST = 2692 | 末尾键<br>**起始版本：** 22<br><!--Device-KEYCODE_LAST = 2692--><!--Device-KEYCODE_LAST = 2692-End--> |
| KEYCODE_RESTART = 2693 | 重启键<br>**起始版本：** 22<br><!--Device-KEYCODE_RESTART = 2693--><!--Device-KEYCODE_RESTART = 2693-End--> |
| KEYCODE_SLOW = 2694 | 慢速键<br>**起始版本：** 22<br><!--Device-KEYCODE_SLOW = 2694--><!--Device-KEYCODE_SLOW = 2694-End--> |
| KEYCODE_SHUFFLE = 2695 | 随机播放键<br>**起始版本：** 22<br><!--Device-KEYCODE_SHUFFLE = 2695--><!--Device-KEYCODE_SHUFFLE = 2695-End--> |
| KEYCODE_VIDEOPHONE = 2696 | 可视电话键<br>**起始版本：** 22<br><!--Device-KEYCODE_VIDEOPHONE = 2696--><!--Device-KEYCODE_VIDEOPHONE = 2696-End--> |
| KEYCODE_GAMES = 2697 | 游戏键<br>**起始版本：** 22<br><!--Device-KEYCODE_GAMES = 2697--><!--Device-KEYCODE_GAMES = 2697-End--> |
| KEYCODE_ZOOMIN = 2698 | 放大键<br>**起始版本：** 22<br><!--Device-KEYCODE_ZOOMIN = 2698--><!--Device-KEYCODE_ZOOMIN = 2698-End--> |
| KEYCODE_ZOOMOUT = 2699 | 缩小键<br>**起始版本：** 22<br><!--Device-KEYCODE_ZOOMOUT = 2699--><!--Device-KEYCODE_ZOOMOUT = 2699-End--> |
| KEYCODE_ZOOMRESET = 2700 | 缩放重置键<br>**起始版本：** 22<br><!--Device-KEYCODE_ZOOMRESET = 2700--><!--Device-KEYCODE_ZOOMRESET = 2700-End--> |
| KEYCODE_WORDPROCESSOR = 2701 | 文字处理键<br>**起始版本：** 22<br><!--Device-KEYCODE_WORDPROCESSOR = 2701--><!--Device-KEYCODE_WORDPROCESSOR = 2701-End--> |
| KEYCODE_EDITOR = 2702 | 编辑器键<br>**起始版本：** 22<br><!--Device-KEYCODE_EDITOR = 2702--><!--Device-KEYCODE_EDITOR = 2702-End--> |
| KEYCODE_SPREADSHEET = 2703 | 电子表格键<br>**起始版本：** 22<br><!--Device-KEYCODE_SPREADSHEET = 2703--><!--Device-KEYCODE_SPREADSHEET = 2703-End--> |
| KEYCODE_GRAPHICSEDITOR = 2704 | 图形编辑器键<br>**起始版本：** 22<br><!--Device-KEYCODE_GRAPHICSEDITOR = 2704--><!--Device-KEYCODE_GRAPHICSEDITOR = 2704-End--> |
| KEYCODE_PRESENTATION = 2705 | 演示文稿键<br>**起始版本：** 22<br><!--Device-KEYCODE_PRESENTATION = 2705--><!--Device-KEYCODE_PRESENTATION = 2705-End--> |
| KEYCODE_DATABASE = 2706 | 数据库键<br>**起始版本：** 22<br><!--Device-KEYCODE_DATABASE = 2706--><!--Device-KEYCODE_DATABASE = 2706-End--> |
| KEYCODE_NEWS = 2707 | 新闻键<br>**起始版本：** 22<br><!--Device-KEYCODE_NEWS = 2707--><!--Device-KEYCODE_NEWS = 2707-End--> |
| KEYCODE_VOICEMAIL = 2708 | 语音信箱键<br>**起始版本：** 22<br><!--Device-KEYCODE_VOICEMAIL = 2708--><!--Device-KEYCODE_VOICEMAIL = 2708-End--> |
| KEYCODE_ADDRESSBOOK = 2709 | 通讯簿键<br>**起始版本：** 22<br><!--Device-KEYCODE_ADDRESSBOOK = 2709--><!--Device-KEYCODE_ADDRESSBOOK = 2709-End--> |
| KEYCODE_MESSENGER = 2710 | 通信键<br>**起始版本：** 22<br><!--Device-KEYCODE_MESSENGER = 2710--><!--Device-KEYCODE_MESSENGER = 2710-End--> |
| KEYCODE_BRIGHTNESS_TOGGLE = 2711 | 亮度切换键<br>**起始版本：** 22<br><!--Device-KEYCODE_BRIGHTNESS_TOGGLE = 2711--><!--Device-KEYCODE_BRIGHTNESS_TOGGLE = 2711-End--> |
| KEYCODE_SPELLCHECK = 2712 | 拼写检查键<br>**起始版本：** 22<br><!--Device-KEYCODE_SPELLCHECK = 2712--><!--Device-KEYCODE_SPELLCHECK = 2712-End--> |
| KEYCODE_COFFEE = 2713 | 终端锁/屏幕保护程序键<br>**起始版本：** 22<br><!--Device-KEYCODE_COFFEE = 2713--><!--Device-KEYCODE_COFFEE = 2713-End--> |
| KEYCODE_MEDIA_REPEAT = 2714 | 媒体循环键<br>**起始版本：** 22<br><!--Device-KEYCODE_MEDIA_REPEAT = 2714--><!--Device-KEYCODE_MEDIA_REPEAT = 2714-End--> |
| KEYCODE_IMAGES = 2715 | 图像键<br>**起始版本：** 22<br><!--Device-KEYCODE_IMAGES = 2715--><!--Device-KEYCODE_IMAGES = 2715-End--> |
| KEYCODE_BUTTONCONFIG = 2716 | 按键配置键<br>**起始版本：** 22<br><!--Device-KEYCODE_BUTTONCONFIG = 2716--><!--Device-KEYCODE_BUTTONCONFIG = 2716-End--> |
| KEYCODE_TASKMANAGER = 2717 | 任务管理器键<br>**起始版本：** 22<br><!--Device-KEYCODE_TASKMANAGER = 2717--><!--Device-KEYCODE_TASKMANAGER = 2717-End--> |
| KEYCODE_JOURNAL = 2718 | 日志按键<br>**起始版本：** 22<br><!--Device-KEYCODE_JOURNAL = 2718--><!--Device-KEYCODE_JOURNAL = 2718-End--> |
| KEYCODE_CONTROLPANEL = 2719 | 控制面板键<br>**起始版本：** 22<br><!--Device-KEYCODE_CONTROLPANEL = 2719--><!--Device-KEYCODE_CONTROLPANEL = 2719-End--> |
| KEYCODE_APPSELECT = 2720 | 应用程序选择键<br>**起始版本：** 22<br><!--Device-KEYCODE_APPSELECT = 2720--><!--Device-KEYCODE_APPSELECT = 2720-End--> |
| KEYCODE_SCREENSAVER = 2721 | 屏幕保护程序键<br>**起始版本：** 22<br><!--Device-KEYCODE_SCREENSAVER = 2721--><!--Device-KEYCODE_SCREENSAVER = 2721-End--> |
| KEYCODE_ASSISTANT = 2722 | 智慧键<br>**起始版本：** 22<br><!--Device-KEYCODE_ASSISTANT = 2722--><!--Device-KEYCODE_ASSISTANT = 2722-End--> |
| KEYCODE_KBD_LAYOUT_NEXT = 2723 | 下一个键盘布局键<br>**起始版本：** 22<br><!--Device-KEYCODE_KBD_LAYOUT_NEXT = 2723--><!--Device-KEYCODE_KBD_LAYOUT_NEXT = 2723-End--> |
| KEYCODE_BRIGHTNESS_MIN = 2724 | 最小亮度键<br>**起始版本：** 22<br><!--Device-KEYCODE_BRIGHTNESS_MIN = 2724--><!--Device-KEYCODE_BRIGHTNESS_MIN = 2724-End--> |
| KEYCODE_BRIGHTNESS_MAX = 2725 | 最大亮度键<br>**起始版本：** 22<br><!--Device-KEYCODE_BRIGHTNESS_MAX = 2725--><!--Device-KEYCODE_BRIGHTNESS_MAX = 2725-End--> |
| KEYCODE_KBDINPUTASSIST_PREV = 2726 | 键盘输入Assist_Previous，查看输入法输入记录。<br>**起始版本：** 22<br><!--Device-KEYCODE_KBDINPUTASSIST_PREV = 2726--><!--Device-KEYCODE_KBDINPUTASSIST_PREV = 2726-End--> |
| KEYCODE_KBDINPUTASSIST_NEXT = 2727 | 键盘输入Assist_Next，查看输入法输入拓展。<br>**起始版本：** 22<br><!--Device-KEYCODE_KBDINPUTASSIST_NEXT = 2727--><!--Device-KEYCODE_KBDINPUTASSIST_NEXT = 2727-End--> |
| KEYCODE_KBDINPUTASSIST_PREVGROUP = 2728 | 键盘输入Assist_Previous，切换输入组中上一个输入法。<br>**起始版本：** 22<br><!--Device-KEYCODE_KBDINPUTASSIST_PREVGROUP = 2728--><!--Device-KEYCODE_KBDINPUTASSIST_PREVGROUP = 2728-End--> |
| KEYCODE_KBDINPUTASSIST_NEXTGROUP = 2729 | 键盘输入Assist_Next，切换输入组中下一个输入法。<br>**起始版本：** 22<br><!--Device-KEYCODE_KBDINPUTASSIST_NEXTGROUP = 2729--><!--Device-KEYCODE_KBDINPUTASSIST_NEXTGROUP = 2729-End--> |
| KEYCODE_KBDINPUTASSIST_ACCEPT = 2730 | 键盘输入Assist_Accept<br>**起始版本：** 22<br><!--Device-KEYCODE_KBDINPUTASSIST_ACCEPT = 2730--><!--Device-KEYCODE_KBDINPUTASSIST_ACCEPT = 2730-End--> |
| KEYCODE_KBDINPUTASSIST_CANCEL = 2731 | 键盘输入Assist_Cancel<br>**起始版本：** 22<br><!--Device-KEYCODE_KBDINPUTASSIST_CANCEL = 2731--><!--Device-KEYCODE_KBDINPUTASSIST_CANCEL = 2731-End--> |
| KEYCODE_MOUSE_ASSISTANT = 2732 | 鼠标AI助手键<br>**起始版本：** 26.0.0<br><!--Device-KEYCODE_MOUSE_ASSISTANT = 2732--><!--Device-KEYCODE_MOUSE_ASSISTANT = 2732-End--> |
| KEYCODE_MOUSE_INTELLIGENCE_SELECTION = 2733 | 鼠标智慧框选键<br>**起始版本：** 26.0.0<br><!--Device-KEYCODE_MOUSE_INTELLIGENCE_SELECTION = 2733--><!--Device-KEYCODE_MOUSE_INTELLIGENCE_SELECTION = 2733-End--> |
| KEYCODE_AOD_SINGLE_CLICK = 2740 | 手机触摸屏单击事件，在熄屏显示状态下使用。<br>**起始版本：** 26.0.0<br><!--Device-KEYCODE_AOD_SINGLE_CLICK = 2740--><!--Device-KEYCODE_AOD_SINGLE_CLICK = 2740-End--> |
| KEYCODE_FRONT = 2800 | 挡风玻璃除雾器开关键<br>**起始版本：** 22<br><!--Device-KEYCODE_FRONT = 2800--><!--Device-KEYCODE_FRONT = 2800-End--> |
| KEYCODE_SETUP = 2801 | 设置键<br>**起始版本：** 22<br><!--Device-KEYCODE_SETUP = 2801--><!--Device-KEYCODE_SETUP = 2801-End--> |
| KEYCODE_WAKEUP = 2802 | 唤醒键<br>**起始版本：** 22<br><!--Device-KEYCODE_WAKEUP = 2802--><!--Device-KEYCODE_WAKEUP = 2802-End--> |
| KEYCODE_SENDFILE = 2803 | 发送文件按键<br>**起始版本：** 22<br><!--Device-KEYCODE_SENDFILE = 2803--><!--Device-KEYCODE_SENDFILE = 2803-End--> |
| KEYCODE_DELETEFILE = 2804 | 删除文件按键<br>**起始版本：** 22<br><!--Device-KEYCODE_DELETEFILE = 2804--><!--Device-KEYCODE_DELETEFILE = 2804-End--> |
| KEYCODE_XFER = 2805 | 文件传输（XFER）按键<br>**起始版本：** 22<br><!--Device-KEYCODE_XFER = 2805--><!--Device-KEYCODE_XFER = 2805-End--> |
| KEYCODE_PROG1 = 2806 | 程序键1<br>**起始版本：** 22<br><!--Device-KEYCODE_PROG1 = 2806--><!--Device-KEYCODE_PROG1 = 2806-End--> |
| KEYCODE_PROG2 = 2807 | 程序键2<br>**起始版本：** 22<br><!--Device-KEYCODE_PROG2 = 2807--><!--Device-KEYCODE_PROG2 = 2807-End--> |
| KEYCODE_MSDOS = 2808 | DOS面板键<br>**起始版本：** 22<br><!--Device-KEYCODE_MSDOS = 2808--><!--Device-KEYCODE_MSDOS = 2808-End--> |
| KEYCODE_SCREENLOCK = 2809 | 屏幕锁定键<br>**起始版本：** 22<br><!--Device-KEYCODE_SCREENLOCK = 2809--><!--Device-KEYCODE_SCREENLOCK = 2809-End--> |
| KEYCODE_DIRECTION_ROTATE_DISPLAY = 2810 | 方向旋转显示键<br>**起始版本：** 22<br><!--Device-KEYCODE_DIRECTION_ROTATE_DISPLAY = 2810--><!--Device-KEYCODE_DIRECTION_ROTATE_DISPLAY = 2810-End--> |
| KEYCODE_CYCLEWINDOWS = 2811 | 窗口切换键<br>**起始版本：** 22<br><!--Device-KEYCODE_CYCLEWINDOWS = 2811--><!--Device-KEYCODE_CYCLEWINDOWS = 2811-End--> |
| KEYCODE_COMPUTER = 2812 | 按键<br>**起始版本：** 22<br><!--Device-KEYCODE_COMPUTER = 2812--><!--Device-KEYCODE_COMPUTER = 2812-End--> |
| KEYCODE_EJECTCLOSECD = 2813 | 弹出CD键<br>**起始版本：** 22<br><!--Device-KEYCODE_EJECTCLOSECD = 2813--><!--Device-KEYCODE_EJECTCLOSECD = 2813-End--> |
| KEYCODE_ISO = 2814 | ISO键<br>**起始版本：** 22<br><!--Device-KEYCODE_ISO = 2814--><!--Device-KEYCODE_ISO = 2814-End--> |
| KEYCODE_MOVE = 2815 | 移动键<br>**起始版本：** 22<br><!--Device-KEYCODE_MOVE = 2815--><!--Device-KEYCODE_MOVE = 2815-End--> |
| KEYCODE_F13 = 2816 | 按键'F13'<br>**起始版本：** 22<br><!--Device-KEYCODE_F13 = 2816--><!--Device-KEYCODE_F13 = 2816-End--> |
| KEYCODE_F14 = 2817 | 按键'F14'<br>**起始版本：** 22<br><!--Device-KEYCODE_F14 = 2817--><!--Device-KEYCODE_F14 = 2817-End--> |
| KEYCODE_F15 = 2818 | 按键'F15'<br>**起始版本：** 22<br><!--Device-KEYCODE_F15 = 2818--><!--Device-KEYCODE_F15 = 2818-End--> |
| KEYCODE_F16 = 2819 | 按键'F16'<br>**起始版本：** 22<br><!--Device-KEYCODE_F16 = 2819--><!--Device-KEYCODE_F16 = 2819-End--> |
| KEYCODE_F17 = 2820 | 按键'F17'<br>**起始版本：** 22<br><!--Device-KEYCODE_F17 = 2820--><!--Device-KEYCODE_F17 = 2820-End--> |
| KEYCODE_F18 = 2821 | 按键'F18'<br>**起始版本：** 22<br><!--Device-KEYCODE_F18 = 2821--><!--Device-KEYCODE_F18 = 2821-End--> |
| KEYCODE_F19 = 2822 | 按键'F19'<br>**起始版本：** 22<br><!--Device-KEYCODE_F19 = 2822--><!--Device-KEYCODE_F19 = 2822-End--> |
| KEYCODE_F20 = 2823 | 按键'F20'<br>**起始版本：** 22<br><!--Device-KEYCODE_F20 = 2823--><!--Device-KEYCODE_F20 = 2823-End--> |
| KEYCODE_F21 = 2824 | 按键'F21'<br>**起始版本：** 22<br><!--Device-KEYCODE_F21 = 2824--><!--Device-KEYCODE_F21 = 2824-End--> |
| KEYCODE_F22 = 2825 | 按键'F22'<br>**起始版本：** 22<br><!--Device-KEYCODE_F22 = 2825--><!--Device-KEYCODE_F22 = 2825-End--> |
| KEYCODE_F23 = 2826 | 按键'F23'<br>**起始版本：** 22<br><!--Device-KEYCODE_F23 = 2826--><!--Device-KEYCODE_F23 = 2826-End--> |
| KEYCODE_F24 = 2827 | 按键'F24'<br>**起始版本：** 22<br><!--Device-KEYCODE_F24 = 2827--><!--Device-KEYCODE_F24 = 2827-End--> |
| KEYCODE_PROG3 = 2828 | 程序键3<br>**起始版本：** 22<br><!--Device-KEYCODE_PROG3 = 2828--><!--Device-KEYCODE_PROG3 = 2828-End--> |
| KEYCODE_PROG4 = 2829 | 程序键4<br>**起始版本：** 22<br><!--Device-KEYCODE_PROG4 = 2829--><!--Device-KEYCODE_PROG4 = 2829-End--> |
| KEYCODE_DASHBOARD = 2830 | 仪表板键<br>**起始版本：** 22<br><!--Device-KEYCODE_DASHBOARD = 2830--><!--Device-KEYCODE_DASHBOARD = 2830-End--> |
| KEYCODE_SUSPEND = 2831 | 挂起键<br>**起始版本：** 22<br><!--Device-KEYCODE_SUSPEND = 2831--><!--Device-KEYCODE_SUSPEND = 2831-End--> |
| KEYCODE_HP = 2832 | 高阶路径键<br>**起始版本：** 22<br><!--Device-KEYCODE_HP = 2832--><!--Device-KEYCODE_HP = 2832-End--> |
| KEYCODE_SOUND = 2833 | 音量键<br>**起始版本：** 22<br><!--Device-KEYCODE_SOUND = 2833--><!--Device-KEYCODE_SOUND = 2833-End--> |
| KEYCODE_QUESTION = 2834 | 疑问按键<br>**起始版本：** 22<br><!--Device-KEYCODE_QUESTION = 2834--><!--Device-KEYCODE_QUESTION = 2834-End--> |
| KEYCODE_CONNECT = 2836 | 连接键<br>**起始版本：** 22<br><!--Device-KEYCODE_CONNECT = 2836--><!--Device-KEYCODE_CONNECT = 2836-End--> |
| KEYCODE_SPORT = 2837 | 运动按键<br>**起始版本：** 22<br><!--Device-KEYCODE_SPORT = 2837--><!--Device-KEYCODE_SPORT = 2837-End--> |
| KEYCODE_SHOP = 2838 | 商城键<br>**起始版本：** 22<br><!--Device-KEYCODE_SHOP = 2838--><!--Device-KEYCODE_SHOP = 2838-End--> |
| KEYCODE_ALTERASE = 2839 | 交替键<br>**起始版本：** 22<br><!--Device-KEYCODE_ALTERASE = 2839--><!--Device-KEYCODE_ALTERASE = 2839-End--> |
| KEYCODE_SWITCHVIDEOMODE = 2841 | 在可用视频之间循环输出（监视器/LCD/TV输出/等）。<br>**起始版本：** 22<br><!--Device-KEYCODE_SWITCHVIDEOMODE = 2841--><!--Device-KEYCODE_SWITCHVIDEOMODE = 2841-End--> |
| KEYCODE_BATTERY = 2842 | 电池按键<br>**起始版本：** 22<br><!--Device-KEYCODE_BATTERY = 2842--><!--Device-KEYCODE_BATTERY = 2842-End--> |
| KEYCODE_BLUETOOTH = 2843 | 蓝牙按键<br>**起始版本：** 22<br><!--Device-KEYCODE_BLUETOOTH = 2843--><!--Device-KEYCODE_BLUETOOTH = 2843-End--> |
| KEYCODE_WLAN = 2844 | 无线局域网键<br>**起始版本：** 22<br><!--Device-KEYCODE_WLAN = 2844--><!--Device-KEYCODE_WLAN = 2844-End--> |
| KEYCODE_UWB = 2845 | 超宽带控制键<br>**起始版本：** 22<br><!--Device-KEYCODE_UWB = 2845--><!--Device-KEYCODE_UWB = 2845-End--> |
| KEYCODE_WWAN_WIMAX = 2846 | 移动网络控制键<br>**起始版本：** 22<br><!--Device-KEYCODE_WWAN_WIMAX = 2846--><!--Device-KEYCODE_WWAN_WIMAX = 2846-End--> |
| KEYCODE_RFKILL = 2847 | 控制所有无线设备的键<br>**起始版本：** 22<br><!--Device-KEYCODE_RFKILL = 2847--><!--Device-KEYCODE_RFKILL = 2847-End--> |
| KEYCODE_CHANNEL = 3001 | 向上频道键<br>**起始版本：** 22<br><!--Device-KEYCODE_CHANNEL = 3001--><!--Device-KEYCODE_CHANNEL = 3001-End--> |
| KEYCODE_BTN_0 = 3100 | 按钮'0'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_0 = 3100--><!--Device-KEYCODE_BTN_0 = 3100-End--> |
| KEYCODE_BTN_1 = 3101 | 按钮'1'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_1 = 3101--><!--Device-KEYCODE_BTN_1 = 3101-End--> |
| KEYCODE_BTN_2 = 3102 | 按钮'2'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_2 = 3102--><!--Device-KEYCODE_BTN_2 = 3102-End--> |
| KEYCODE_BTN_3 = 3103 | 按钮'3'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_3 = 3103--><!--Device-KEYCODE_BTN_3 = 3103-End--> |
| KEYCODE_BTN_4 = 3104 | 按钮'4'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_4 = 3104--><!--Device-KEYCODE_BTN_4 = 3104-End--> |
| KEYCODE_BTN_5 = 3105 | 按钮'5'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_5 = 3105--><!--Device-KEYCODE_BTN_5 = 3105-End--> |
| KEYCODE_BTN_6 = 3106 | 按钮'6'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_6 = 3106--><!--Device-KEYCODE_BTN_6 = 3106-End--> |
| KEYCODE_BTN_7 = 3107 | 按钮'7'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_7 = 3107--><!--Device-KEYCODE_BTN_7 = 3107-End--> |
| KEYCODE_BTN_8 = 3108 | 按钮'8'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_8 = 3108--><!--Device-KEYCODE_BTN_8 = 3108-End--> |
| KEYCODE_BTN_9 = 3109 | 按钮'9'<br>**起始版本：** 22<br><!--Device-KEYCODE_BTN_9 = 3109--><!--Device-KEYCODE_BTN_9 = 3109-End--> |
| KEYCODE_DAGGER_CLICK = 3211 | 智能手表智感窗按键单击<br>**起始版本：** 22<br><!--Device-KEYCODE_DAGGER_CLICK = 3211--><!--Device-KEYCODE_DAGGER_CLICK = 3211-End--> |
| KEYCODE_DAGGER_DOUBLE_CLICK = 3212 | 智能手表智感窗按键双击<br>**起始版本：** 22<br><!--Device-KEYCODE_DAGGER_DOUBLE_CLICK = 3212--><!--Device-KEYCODE_DAGGER_DOUBLE_CLICK = 3212-End--> |
| KEYCODE_DAGGER_LONG_PRESS = 3213 | 智能手表智感窗按键长按<br>**起始版本：** 22<br><!--Device-KEYCODE_DAGGER_LONG_PRESS = 3213--><!--Device-KEYCODE_DAGGER_LONG_PRESS = 3213-End--> |
| KEYCODE_DIV = 3220 | 智能手表左按键<br>**起始版本：** 22<br><!--Device-KEYCODE_DIV = 3220--><!--Device-KEYCODE_DIV = 3220-End--> |
| KEYCODE_XKEY = 3232 | 自定义快捷键<br>**起始版本：** 26.0.0<br><!--Device-KEYCODE_XKEY = 3232--><!--Device-KEYCODE_XKEY = 3232-End--> |
| KEYCODE_FINGERPRINT_SLIDE_UP = 3233 | 智控键上滑<br>**起始版本：** 26.0.0<br><!--Device-KEYCODE_FINGERPRINT_SLIDE_UP = 3233--><!--Device-KEYCODE_FINGERPRINT_SLIDE_UP = 3233-End--> |
| KEYCODE_FINGERPRINT_SLIDE_DOWN = 3234 | 智控键下滑<br>**起始版本：** 26.0.0<br><!--Device-KEYCODE_FINGERPRINT_SLIDE_DOWN = 3234--><!--Device-KEYCODE_FINGERPRINT_SLIDE_DOWN = 3234-End--> |
| OH_INPUT_KEYCODE_PTZ_CLICK = 3235 | 云台模式调节键<br>**起始版本：** 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_CLICK = 3235--><!--Device-OH_INPUT_KEYCODE_PTZ_CLICK = 3235-End--> |
| OH_INPUT_KEYCODE_PTZ_FOCUS_LEFT = 3236 | 云台调焦左调节<br>**起始版本：** 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_FOCUS_LEFT = 3236--><!--Device-OH_INPUT_KEYCODE_PTZ_FOCUS_LEFT = 3236-End--> |
| OH_INPUT_KEYCODE_PTZ_FOCUS_RIGHT = 3237 | 云台调焦右调节<br>**起始版本：** 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_FOCUS_RIGHT = 3237--><!--Device-OH_INPUT_KEYCODE_PTZ_FOCUS_RIGHT = 3237-End--> |
| OH_INPUT_KEYCODE_PTZ_EXPOSURE_LEFT = 3238 | 云台曝光左调节<br>**起始版本：** 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_EXPOSURE_LEFT = 3238--><!--Device-OH_INPUT_KEYCODE_PTZ_EXPOSURE_LEFT = 3238-End--> |
| OH_INPUT_KEYCODE_PTZ_EXPOSURE_RIGHT = 3239 | 云台曝光右调节<br>**起始版本：** 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_EXPOSURE_RIGHT = 3239--><!--Device-OH_INPUT_KEYCODE_PTZ_EXPOSURE_RIGHT = 3239-End--> |
| OH_INPUT_KEYCODE_PTZ_SHUTTER_LEFT = 3240 | 云台快门速度左调节<br>**起始版本：** 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_SHUTTER_LEFT = 3240--><!--Device-OH_INPUT_KEYCODE_PTZ_SHUTTER_LEFT = 3240-End--> |
| OH_INPUT_KEYCODE_PTZ_SHUTTER_RIGHT = 3241 | 云台快门速度右调节<br>**起始版本：** 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_SHUTTER_RIGHT = 3241--><!--Device-OH_INPUT_KEYCODE_PTZ_SHUTTER_RIGHT = 3241-End--> |
| OH_INPUT_KEYCODE_PTZ_APERTURE_LEFT = 3242 | 云台光圈左调节<br>**起始版本：** 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_APERTURE_LEFT = 3242--><!--Device-OH_INPUT_KEYCODE_PTZ_APERTURE_LEFT = 3242-End--> |
| OH_INPUT_KEYCODE_PTZ_APERTURE_RIGHT = 3243 | 云台光圈右调节<br>**起始版本：** 26.0.1<br><!--Device-OH_INPUT_KEYCODE_PTZ_APERTURE_RIGHT = 3243--><!--Device-OH_INPUT_KEYCODE_PTZ_APERTURE_RIGHT = 3243-End--> |
| OH_INPUT_KEYCODE_DESKTOP = 3245 | 返回桌面<br>**起始版本：** 26.1.0<br><!--Device-OH_INPUT_KEYCODE_DESKTOP = 3245--><!--Device-OH_INPUT_KEYCODE_DESKTOP = 3245-End--> |


