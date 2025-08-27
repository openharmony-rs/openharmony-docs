# @ohos.multimodalInput.keyCode (键值)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

按键设备的键码值，按键设备包括键盘、电源键、拍照键等。

> **说明：**
> 
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { KeyCode } from '@kit.InputKit';
```

## KeyCode

键码值。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

| 名称                               | 值   |  说明        |
| -------------------------------- | ------ | --------------------------- |
| KEYCODE_FN                       |  0 | 功能（Fn）键。                     |
| KEYCODE_UNKNOWN                  |  -1 | 未知按键。                        |
| KEYCODE_HOME                     |  1 | 功能（Home）键。                  |
| KEYCODE_BACK                     |  2 | 返回键。                         |
| KEYCODE_SEARCH<sup>13+</sup> | 9 | 搜索键。 |
| KEYCODE_MEDIA_PLAY_PAUSE        |  10 | 多媒体键：播放/暂停。<br/>与KEYCODE_PLAYPAUSE的区别为：<br/>KEYCODE_PLAYPAUSE是较早的定义，KEYCODE_MEDIA_PLAY_PAUSE为现代媒体键设备设计，常见于较新的媒体键设备。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                  |
| KEYCODE_MEDIA_STOP               |  11 | 光盘停止键。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                     |
| KEYCODE_MEDIA_NEXT               |  12 | 多媒体键：下一首。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                    |
| KEYCODE_MEDIA_PREVIOUS           |  13 | 多媒体键：上一首。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                    |
| KEYCODE_MEDIA_REWIND            |  14 | 多媒体键：快退。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                     |
| KEYCODE_MEDIA_FAST_FORWARD       |  15 | 多媒体键：快进。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                     |
| KEYCODE_VOLUME_UP                |  16 | 音量增加键。                       |
| KEYCODE_VOLUME_DOWN              |  17 | 音量减小键。                       |
| KEYCODE_POWER                    |  18 | 电源键。                        |
| KEYCODE_CAMERA                   |  19 | 拍照键。                         |
| KEYCODE_VOLUME_MUTE              |  22 | 扬声器静音键。                      |
| KEYCODE_MUTE                     |  23 | 话筒静音键。                       |
| KEYCODE_BRIGHTNESS_UP            |  40 | 亮度调节按键：调亮。                   |
| KEYCODE_BRIGHTNESS_DOWN          |  41 | 亮度调节按键：调暗。                   |
| KEYCODE_0                        |  2000 | 按键'0'。                       |
| KEYCODE_1                        |  2001 | 按键'1'。                       |
| KEYCODE_2                        |  2002 | 按键'2'。                       |
| KEYCODE_3                        |  2003 | 按键'3'。                       |
| KEYCODE_4                        |  2004 | 按键'4'。                       |
| KEYCODE_5                        |  2005 | 按键'5'。                       |
| KEYCODE_6                        |  2006 | 按键'6'。                       |
| KEYCODE_7                        |  2007 | 按键'7'。                       |
| KEYCODE_8                        |  2008 | 按键'8'。                       |
| KEYCODE_9                        |  2009 | 按键'9'。                       |
| KEYCODE_STAR                     |  2010 | 按键'*'。                       |
| KEYCODE_POUND                    |  2011 | 按键'#'。                       |
| KEYCODE_DPAD_UP                  |  2012 | 导航键：向上。                      |
| KEYCODE_DPAD_DOWN                |  2013 | 导航键：向下。                      |
| KEYCODE_DPAD_LEFT                |  2014 | 导航键：向左。                      |
| KEYCODE_DPAD_RIGHT               |  2015 | 导航键：向右。                      |
| KEYCODE_DPAD_CENTER              |  2016 | 导航键：确定键。                     |
| KEYCODE_A                        |  2017 | 按键'A'。                       |
| KEYCODE_B                        |  2018 | 按键'B'。                       |
| KEYCODE_C                        |  2019 | 按键'C'。                       |
| KEYCODE_D                        |  2020 | 按键'D'。                       |
| KEYCODE_E                        |  2021 | 按键'E'。                       |
| KEYCODE_F                        |  2022 | 按键'F'。                       |
| KEYCODE_G                        |  2023 | 按键'G'。                       |
| KEYCODE_H                        |  2024 | 按键'H'。                       |
| KEYCODE_I                        |  2025 | 按键'I'。                       |
| KEYCODE_J                        |  2026 | 按键'J'。                       |
| KEYCODE_K                        |  2027 | 按键'K'。                       |
| KEYCODE_L                        |  2028 | 按键'L'。                       |
| KEYCODE_M                        |  2029 | 按键'M'。                       |
| KEYCODE_N                        |  2030 | 按键'N'。                       |
| KEYCODE_O                        |  2031 | 按键'O'。                       |
| KEYCODE_P                        |  2032 | 按键'P'。                       |
| KEYCODE_Q                        |  2033 | 按键'Q'。                       |
| KEYCODE_R                        |  2034 | 按键'R'。                       |
| KEYCODE_S                        |  2035 | 按键'S'。                       |
| KEYCODE_T                        |  2036 | 按键'T'。                       |
| KEYCODE_U                        |  2037 | 按键'U'。                       |
| KEYCODE_V                        |  2038 | 按键'V'。                       |
| KEYCODE_W                        |  2039 | 按键'W'。                       |
| KEYCODE_X                        |  2040 | 按键'X'。                       |
| KEYCODE_Y                        |  2041 | 按键'Y'。                       |
| KEYCODE_Z                        |  2042 | 按键'Z'。                       |
| KEYCODE_COMMA                    |  2043 | 按键','。                       |
| KEYCODE_PERIOD                   |  2044 | 按键'.'。                       |
| KEYCODE_ALT_LEFT                 |  2045 | 左Alt键。                    |
| KEYCODE_ALT_RIGHT                |  2046 | 右Alt键。                 |
| KEYCODE_SHIFT_LEFT               |  2047 | 左Shift键。                |
| KEYCODE_SHIFT_RIGHT              |  2048 | 右Shift键。                 |
| KEYCODE_TAB                      |  2049 | Tab键。                        |
| KEYCODE_SPACE                    |  2050 | 空格键。                         |
| KEYCODE_SYM                      |  2051 | 符号修改器按键。                     |
| KEYCODE_EXPLORER                 |  2052 | 浏览器功能键，此键用于启动浏览器应用程序。      |
| KEYCODE_ENVELOPE                 |  2053 | 电子邮件功能键，此键用于启动电子邮件应用程序。    |
| KEYCODE_ENTER                    |  2054 | 回车键。                         |
| KEYCODE_DEL                      |  2055 | 退格键。                         |
| KEYCODE_GRAVE                    |  2056 | 按键'`'。                       |
| KEYCODE_MINUS                    |  2057 | 按键'-'。                       |
| KEYCODE_EQUALS                   |  2058 | 按键'='。                       |
| KEYCODE_LEFT_BRACKET             |  2059 | 按键'['。                       |
| KEYCODE_RIGHT_BRACKET            |  2060 | 按键']'。                       |
| KEYCODE_BACKSLASH                |  2061 | 按键'\\'。                       |
| KEYCODE_SEMICOLON                |  2062 | 按键';'。                       |
| KEYCODE_APOSTROPHE               |  2063 | 按键''' (单引号)。                 |
| KEYCODE_SLASH                    |  2064 | 按键'/'。                       |
| KEYCODE_AT                       |  2065 | 按键'@'。                       |
| KEYCODE_PLUS                     |  2066 | 按键'+'。                       |
| KEYCODE_MENU                     |  2067 | 菜单键。                         |
| KEYCODE_PAGE_UP                  |  2068 | 向上翻页键。                       |
| KEYCODE_PAGE_DOWN                |  2069 | 向下翻页键。                       |
| KEYCODE_ESCAPE                   |  2070 | Esc键。                        |
| KEYCODE_FORWARD_DEL              |  2071 | 删除键。                         |
| KEYCODE_CTRL_LEFT                |  2072 | 左Ctrl键。                |
| KEYCODE_CTRL_RIGHT               |  2073 | 右Ctrl键。               |
| KEYCODE_CAPS_LOCK                |  2074 | 大写锁定键。                       |
| KEYCODE_SCROLL_LOCK              |  2075 | 滚动锁定键。                       |
| KEYCODE_META_LEFT                |  2076 | 左Meta键。                      |
| KEYCODE_META_RIGHT               |  2077 | 右Meta键。                      |
| KEYCODE_FUNCTION                 |  2078 | 功能键。                      |
| KEYCODE_SYSRQ                    |  2079 | 系统请求/打印屏幕键。                  |
| KEYCODE_BREAK                    |  2080 | Break/Pause键。                |
| KEYCODE_MOVE_HOME                |  2081 | 光标移动到开始键。                    |
| KEYCODE_MOVE_END                 |  2082 | 光标移动到末尾键。                    |
| KEYCODE_INSERT                   |  2083 | 插入键。                         |
| KEYCODE_FORWARD                  |  2084 | 前进键。                         |
| KEYCODE_MEDIA_PLAY               |  2085 | 多媒体键：播放。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                     |
| KEYCODE_MEDIA_PAUSE              |  2086 | 光盘暂停键。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。                     |
| KEYCODE_MEDIA_CLOSE              |  2087 | 光盘关闭键。                     |
| KEYCODE_MEDIA_EJECT              |  2088 | 光盘弹出键。                     |
| KEYCODE_MEDIA_RECORD             |  2089 | 多媒体键：录音。                     |
| KEYCODE_F1                       |  2090 | 按键'F1'。                      |
| KEYCODE_F2                       |  2091 | 按键'F2'。                      |
| KEYCODE_F3                       |  2092 | 按键'F3'。                      |
| KEYCODE_F4                       |  2093 | 按键'F4'。                      |
| KEYCODE_F5                       |  2094 | 按键'F5'。                      |
| KEYCODE_F6                       |  2095 | 按键'F6'。                      |
| KEYCODE_F7                       |  2096 | 按键'F7'。                      |
| KEYCODE_F8                       |  2097 | 按键'F8'。                      |
| KEYCODE_F9                       |  2098 | 按键'F9'。                      |
| KEYCODE_F10                      |  2099 | 按键'F10'。                     |
| KEYCODE_F11                      |  2100 | 按键'F11'。                     |
| KEYCODE_F12                      |  2101 | 按键'F12'。                     |
| KEYCODE_NUM_LOCK                 |  2102 | 小键盘锁。                        |
| KEYCODE_NUMPAD_0                 |  2103 | 小键盘按键'0'。                    |
| KEYCODE_NUMPAD_1                 |  2104 | 小键盘按键'1'。                    |
| KEYCODE_NUMPAD_2                 |  2105 | 小键盘按键'2'。                    |
| KEYCODE_NUMPAD_3                 |  2106 | 小键盘按键'3'。                    |
| KEYCODE_NUMPAD_4                 |  2107 | 小键盘按键'4'。                    |
| KEYCODE_NUMPAD_5                 |  2108 | 小键盘按键'5'。                    |
| KEYCODE_NUMPAD_6                 |  2109 | 小键盘按键'6'。                    |
| KEYCODE_NUMPAD_7                 |  2110 | 小键盘按键'7'。                    |
| KEYCODE_NUMPAD_8                 |  2111 | 小键盘按键'8'。                    |
| KEYCODE_NUMPAD_9                 |  2112 | 小键盘按键'9'。                    |
| KEYCODE_NUMPAD_DIVIDE            |  2113 | 小键盘按键'/'。                    |
| KEYCODE_NUMPAD_MULTIPLY          |  2114 | 小键盘按键'*'。                    |
| KEYCODE_NUMPAD_SUBTRACT          |  2115 | 小键盘按键'-'。                    |
| KEYCODE_NUMPAD_ADD               |  2116 | 小键盘按键'+'。                    |
| KEYCODE_NUMPAD_DOT               |  2117 | 小键盘按键'.'。                    |
| KEYCODE_NUMPAD_COMMA             |  2118 | 小键盘按键','。                    |
| KEYCODE_NUMPAD_ENTER             |  2119 | 小键盘按键回车。                     |
| KEYCODE_NUMPAD_EQUALS            |  2120 | 小键盘按键'='。                    |
| KEYCODE_NUMPAD_LEFT_PAREN        |  2121 | 小键盘按键'('。                    |
| KEYCODE_NUMPAD_RIGHT_PAREN       |  2122 | 小键盘按键')'。                    |
| KEYCODE_VIRTUAL_MULTITASK        |  2210 | 虚拟多任务键。                      |
| KEYCODE_BUTTON_A<sup>15+</sup>  |  2301 | 游戏手柄按键'A'。            |
| KEYCODE_BUTTON_B<sup>15+</sup>  |  2302 | 游戏手柄按键'B'。            |
| KEYCODE_BUTTON_X<sup>15+</sup>  |  2304 | 游戏手柄按键'X'。            |
| KEYCODE_BUTTON_Y<sup>15+</sup>  |  2305 | 游戏手柄按键'Y'。            |
| KEYCODE_BUTTON_L1<sup>15+</sup> |  2307 | 游戏手柄按键'L1'。           |
| KEYCODE_BUTTON_R1<sup>15+</sup> |  2308 | 游戏手柄按键'R1'。           |
| KEYCODE_BUTTON_L2<sup>15+</sup> |  2309 | 游戏手柄按键'L2'。           |
| KEYCODE_BUTTON_R2<sup>15+</sup> |  2310 | 游戏手柄按键'R2'。           |
| KEYCODE_BUTTON_SELECT<sup>15+</sup>  |  2311 | 游戏手柄按键'Select'。       |
| KEYCODE_BUTTON_START<sup>15+</sup>   |  2312 | 游戏手柄按键'Start'。        |
| KEYCODE_BUTTON_MODE<sup>15+</sup>    |  2313 | 游戏手柄按键'Mode'。         |
| KEYCODE_BUTTON_THUMBL<sup>15+</sup>  |  2314 | 游戏手柄按键'THUMBL'。       |
| KEYCODE_BUTTON_THUMBR<sup>15+</sup>  |  2315 | 游戏手柄按键'THUMBR'。       |
| KEYCODE_SLEEP                    |  2600 | 睡眠键。                         |
| KEYCODE_ZENKAKU_HANKAKU          |  2601 | 日文全宽/半宽键。                    |
| KEYCODE_102ND                    |  2602 | 102nd按键。                     |
| KEYCODE_RO                       |  2603 | 日文Ro键。                       |
| KEYCODE_KATAKANA                 |  2604 | 日文片假名键。                      |
| KEYCODE_HIRAGANA                 |  2605 | 日文平假名键。                      |
| KEYCODE_HENKAN                   |  2606 | 日文转换键。                       |
| KEYCODE_KATAKANA_HIRAGANA        |  2607 | 日语片假名/平假名键。                  |
| KEYCODE_MUHENKAN                 |  2608 | 日文非转换键。                      |
| KEYCODE_LINEFEED                 |  2609 | 换行键。                         |
| KEYCODE_MACRO                    |  2610 | 宏键。                          |
| KEYCODE_NUMPAD_PLUSMINUS         |  2611 | 数字键盘上的加号/减号键。                |
| KEYCODE_SCALE                    |  2612 | 扩展键。                         |
| KEYCODE_HANGUEL                  |  2613 | 日文韩语键。                       |
| KEYCODE_HANJA                    |  2614 | 日文汉语键。                       |
| KEYCODE_YEN                      |  2615 | 日元键。                         |
| KEYCODE_STOP                     |  2616 | 停止键。                         |
| KEYCODE_AGAIN                    |  2617 | 重复键。                         |
| KEYCODE_PROPS                    |  2618 | 道具键。                         |
| KEYCODE_UNDO                     |  2619 | 撤消键。                         |
| KEYCODE_COPY                     |  2620 | 复制键。                         |
| KEYCODE_OPEN                     |  2621 | 打开键。                         |
| KEYCODE_PASTE                    |  2622 | 粘贴键。                         |
| KEYCODE_FIND                     |  2623 | 查找键。                         |
| KEYCODE_CUT                      |  2624 | 剪切键。                         |
| KEYCODE_HELP                     |  2625 | 帮助键。                         |
| KEYCODE_CALC                     |  2626 | 计算器特殊功能键，用于启动计算器应用程序。        |
| KEYCODE_FILE                     |  2627 | 文件按键。                        |
| KEYCODE_BOOKMARKS                |  2628 | 书签键。                         |
| KEYCODE_NEXT                     |  2629 | Page Down键。                       |
| KEYCODE_PLAYPAUSE                |  2630 | 多媒体键：播放/暂停。<br/>与KEYCODE_MEDIA_PLAY_PAUSE的区别为：<br/>KEYCODE_PLAYPAUSE是较早的定义，KEYCODE_MEDIA_PLAY_PAUSE为现代媒体键设备设计，常见于较新的媒体键设备。                      |
| KEYCODE_PREVIOUS                 |  2631 | Page Up键。                       |
| KEYCODE_STOPCD                   |  2632 | CD停止键。                       |
| KEYCODE_CONFIG                   |  2634 | 配置键。                         |
| KEYCODE_REFRESH                  |  2635 | 刷新键。                         |
| KEYCODE_EXIT                     |  2636 | 退出键。                         |
| KEYCODE_EDIT                     |  2637 | 编辑键。                         |
| KEYCODE_SCROLLUP                 |  2638 | 向上滚动键。                       |
| KEYCODE_SCROLLDOWN               |  2639 | 向下滚动键。                       |
| KEYCODE_NEW                      |  2640 | 新建键。                         |
| KEYCODE_REDO                     |  2641 | 恢复键。                         |
| KEYCODE_CLOSE                    |  2642 | 关闭键。                         |
| KEYCODE_PLAY                     |  2643 | 播放键。                         |
| KEYCODE_BASSBOOST                |  2644 | 低音增强键。                       |
| KEYCODE_PRINT                    |  2645 | 打印键。                         |
| KEYCODE_CHAT                     |  2646 | 聊天键。                         |
| KEYCODE_FINANCE                  |  2647 | 金融键。                         |
| KEYCODE_CANCEL                   |  2648 | 取消键。                         |
| KEYCODE_KBDILLUM_TOGGLE          |  2649 | 键盘灯光切换键。                     |
| KEYCODE_KBDILLUM_DOWN            |  2650 | 键盘灯光调暗键。                     |
| KEYCODE_KBDILLUM_UP              |  2651 | 键盘灯光调亮键。                     |
| KEYCODE_SEND                     |  2652 | 发送键。                         |
| KEYCODE_REPLY                    |  2653 | 答复键。                        |
| KEYCODE_FORWARDMAIL              |  2654 | 邮件转发键。                       |
| KEYCODE_SAVE                     |  2655 | 保存键。                         |
| KEYCODE_DOCUMENTS                |  2656 | 文件键。                         |
| KEYCODE_VIDEO_NEXT               |  2657 | 下一个视频键。                      |
| KEYCODE_VIDEO_PREV               |  2658 | 上一个视频键。                      |
| KEYCODE_BRIGHTNESS_CYCLE         |  2659 | 背光渐变键。                       |
| KEYCODE_BRIGHTNESS_ZERO          |  2660 | 亮度调节为0键。                     |
| KEYCODE_DISPLAY_OFF              |  2661 | 显示关闭键。                       |
| KEYCODE_BTN_MISC                 |  2662 | 游戏手柄上的各种按键。                  |
| KEYCODE_GOTO                     |  2663 | 进入键。                         |
| KEYCODE_INFO                     |  2664 | 信息查看键。                       |
| KEYCODE_PROGRAM                  |  2665 | 程序键。                         |
| KEYCODE_PVR                      |  2666 | 个人录像机（PVR）键。                 |
| KEYCODE_SUBTITLE                 |  2667 | 字幕键。                         |
| KEYCODE_FULL_SCREEN              |  2668 | 全屏键。                         |
| KEYCODE_KEYBOARD                 |  2669 | 键盘。                          |
| KEYCODE_ASPECT_RATIO             |  2670 | 屏幕纵横比调节键。                    |
| KEYCODE_PC                       |  2671 | 端口控制键。                       |
| KEYCODE_TV                       |  2672 | TV键。                        |
| KEYCODE_TV2                      |  2673 | TV键2。                        |
| KEYCODE_VCR                      |  2674 | 录像机开启键。                      |
| KEYCODE_VCR2                     |  2675 | 录像机开启键2。                     |
| KEYCODE_SAT                      |  2676 | SIM卡应用工具包（SAT）键。             |
| KEYCODE_CD                       |  2677 | CD键。                         |
| KEYCODE_TAPE                     |  2678 | 磁带键。                         |
| KEYCODE_TUNER                    |  2679 | 调谐器键。                        |
| KEYCODE_PLAYER                   |  2680 | 播放器键。                        |
| KEYCODE_DVD                      |  2681 | DVD键。                        |
| KEYCODE_AUDIO                    |  2682 | 音频键。                         |
| KEYCODE_VIDEO                    |  2683 | 视频键。                         |
| KEYCODE_MEMO                     |  2684 | 备忘录键。                        |
| KEYCODE_CALENDAR                 |  2685 | 日历键。                         |
| KEYCODE_RED                      |  2686 | 红色指示器。                       |
| KEYCODE_GREEN                    |  2687 | 绿色指示器。                       |
| KEYCODE_YELLOW                   |  2688 | 黄色指示器。                       |
| KEYCODE_BLUE                     |  2689 | 蓝色指示器。                       |
| KEYCODE_CHANNELUP                |  2690 | 频道向上键。                       |
| KEYCODE_CHANNELDOWN              |  2691 | 频道向下键。                       |
| KEYCODE_LAST                     |  2692 | 末尾键。                         |
| KEYCODE_RESTART                  |  2693 | 重启键。                         |
| KEYCODE_SLOW                     |  2694 | 慢速键。                         |
| KEYCODE_SHUFFLE                  |  2695 | 随机播放键。                       |
| KEYCODE_VIDEOPHONE               |  2696 | 可视电话键。                       |
| KEYCODE_GAMES                    |  2697 | 游戏键。                         |
| KEYCODE_ZOOMIN                   |  2698 | 放大键。                         |
| KEYCODE_ZOOMOUT                  |  2699 | 缩小键。                         |
| KEYCODE_ZOOMRESET                |  2700 | 缩放重置键。                       |
| KEYCODE_WORDPROCESSOR            |  2701 | 文字处理键。                       |
| KEYCODE_EDITOR                   |  2702 | 编辑器键。                        |
| KEYCODE_SPREADSHEET              |  2703 | 电子表格键。                       |
| KEYCODE_GRAPHICSEDITOR           |  2704 | 图形编辑器键。                      |
| KEYCODE_PRESENTATION             |  2705 | 演示文稿键。                       |
| KEYCODE_DATABASE                 |  2706 | 数据库键标。                       |
| KEYCODE_NEWS                     |  2707 | 新闻键。                         |
| KEYCODE_VOICEMAIL                |  2708 | 语音信箱。                        |
| KEYCODE_ADDRESSBOOK              |  2709 | 通讯簿。                         |
| KEYCODE_MESSENGER                |  2710 | 通信键。                         |
| KEYCODE_BRIGHTNESS_TOGGLE        |  2711 | 亮度切换键。                       |
| KEYCODE_SPELLCHECK               |  2712 | AL拼写检查。                      |
| KEYCODE_COFFEE                   |  2713 | 终端锁/屏幕保护程序。                  |
| KEYCODE_MEDIA_REPEAT             |  2714 | 媒体循环键。                       |
| KEYCODE_IMAGES                   |  2715 | 图像键。                         |
| KEYCODE_BUTTONCONFIG             |  2716 | 按键配置键。                       |
| KEYCODE_TASKMANAGER              |  2717 | 任务管理器。                       |
| KEYCODE_JOURNAL                  |  2718 | 日志按键。                        |
| KEYCODE_CONTROLPANEL             |  2719 | 控制面板键。                       |
| KEYCODE_APPSELECT                |  2720 | 应用程序选择键。                     |
| KEYCODE_SCREENSAVER              |  2721 | 屏幕保护程序键。                     |
| KEYCODE_ASSISTANT                |  2722 | 智慧键。                      |
| KEYCODE_KBD_LAYOUT_NEXT          |  2723 | 下一个键盘布局键。                    |
| KEYCODE_BRIGHTNESS_MIN           |  2724 | 最小亮度键。                       |
| KEYCODE_BRIGHTNESS_MAX           |  2725 | 最大亮度键。                       |
| KEYCODE_KBDINPUTASSIST_PREV      |  2726 | 键盘输入Assist_Previous，查看输入法输入记录。         |
| KEYCODE_KBDINPUTASSIST_NEXT      |  2727 | 键盘输入Assist_Next，查看输入法输入拓展。           |
| KEYCODE_KBDINPUTASSIST_PREVGROUP |  2728 | 键盘输入Assist_Previous，切换输入组中上一个输入法。         |
| KEYCODE_KBDINPUTASSIST_NEXTGROUP |  2729 | 键盘输入Assist_Next，切换输入组中下一个输入法。               |
| KEYCODE_KBDINPUTASSIST_ACCEPT    |  2730 | 键盘输入Assist_Accept。           |
| KEYCODE_KBDINPUTASSIST_CANCEL    |  2731 | 键盘输入Assist_Cancel。          |
| KEYCODE_FRONT                    |  2800 | 挡风玻璃除雾器开关。                   |
| KEYCODE_SETUP                    |  2801 | 设置键。                         |
| KEYCODE_WAKEUP                   |  2802 | 唤醒键。                         |
| KEYCODE_SENDFILE                 |  2803 | 发送文件按键。                      |
| KEYCODE_DELETEFILE               |  2804 | 删除文件按键。                      |
| KEYCODE_XFER                     |  2805 | 文件传输（XFER）按键。                |
| KEYCODE_PROG1                    |  2806 | 程序键1。                        |
| KEYCODE_PROG2                    |  2807 | 程序键2。                       |
| KEYCODE_MSDOS                    |  2808 | MS-DOS键（微软磁盘操作系统）。            |
| KEYCODE_SCREENLOCK               |  2809 | 屏幕锁定键。                       |
| KEYCODE_DIRECTION_ROTATE_DISPLAY |  2810 | 方向旋转显示键。                     |
| KEYCODE_CYCLEWINDOWS             |  2811 | Windows循环键。                  |
| KEYCODE_COMPUTER                 |  2812 | 按键。                          |
| KEYCODE_EJECTCLOSECD             |  2813 | 弹出CD键。                      |
| KEYCODE_ISO                      |  2814 | ISO键。                        |
| KEYCODE_MOVE                     |  2815 | 移动键。                         |
| KEYCODE_F13                      |  2816 | 按键'F13'。                     |
| KEYCODE_F14                      |  2817 | 按键'F14'。                     |
| KEYCODE_F15                      |  2818 | 按键'F15'。                     |
| KEYCODE_F16                      |  2819 | 按键'F16'。                     |
| KEYCODE_F17                      |  2820 | 按键'F17'。                     |
| KEYCODE_F18                      |  2821 | 按键'F18'。                     |
| KEYCODE_F19                      |  2822 | 按键'F19'。                     |
| KEYCODE_F20                      |  2823 | 按键'F20'。                     |
| KEYCODE_F21                      |  2824 | 按键'F21'。                     |
| KEYCODE_F22                      |  2825 | 按键'F22'。                     |
| KEYCODE_F23                      |  2826 | 按键'F23'。                     |
| KEYCODE_F24                      |  2827 | 按键'F24'。                     |
| KEYCODE_PROG3                    |  2828 | 程序键3。                        |
| KEYCODE_PROG4                    |  2829 | 程序键4。                        |
| KEYCODE_DASHBOARD                |  2830 | 仪表板。                         |
| KEYCODE_SUSPEND                  |  2831 | 挂起键。                         |
| KEYCODE_HP                       |  2832 | 高阶路径键。                       |
| KEYCODE_SOUND                    |  2833 | 音量键。                         |
| KEYCODE_QUESTION                 |  2834 | 疑问按键。                        |
| KEYCODE_CONNECT                  |  2836 | 连接键。                         |
| KEYCODE_SPORT                    |  2837 | 运动按键。                        |
| KEYCODE_SHOP                     |  2838 | 商城键。                         |
| KEYCODE_ALTERASE                 |  2839 | 交替键。                         |
| KEYCODE_SWITCHVIDEOMODE          |  2841 | 在可用视频之间循环输出（监视器/LCD/TV输出/等）。 |
| KEYCODE_BATTERY                  |  2842 | 电池按键。                        |
| KEYCODE_BLUETOOTH                |  2843 | 蓝牙按键。                        |
| KEYCODE_WLAN                     |  2844 | 无线局域网。                       |
| KEYCODE_UWB                      |  2845 | 超宽带（UWB）。                    |
| KEYCODE_WWAN_WIMAX               |  2846 | WWAN WiMAX按键。                |
| KEYCODE_RFKILL                   |  2847 | 控制所有收音机的键。                   |
| KEYCODE_CHANNEL                  |  3001 | 向上频道键。                       |
| KEYCODE_BTN_0                    |  3100 | 按键0。                         |
| KEYCODE_BTN_1                    |  3101 | 按键1。                         |
| KEYCODE_BTN_2                    |  3102 | 按键2。                         |
| KEYCODE_BTN_3                    |  3103 | 按键3。                         |
| KEYCODE_BTN_4                    |  3104 | 按键4。                         |
| KEYCODE_BTN_5                    |  3105 | 按键5。                         |
| KEYCODE_BTN_6                    |  3106 | 按键6。                         |
| KEYCODE_BTN_7                    |  3107 | 按键7。                         |
| KEYCODE_BTN_8                    |  3108 | 按键8。                         |
| KEYCODE_BTN_9                    |  3109 | 按键9。                         |
| KEYCODE_DAGGER_CLICK<sup>18+</sup> | 3211 | 智能手表智感窗按键单击。 |
| KEYCODE_DAGGER_DOUBLE_CLICK<sup>18+</sup> | 3212 | 智能手表智感窗按键双击。 |
| KEYCODE_DAGGER_LONG_PRESS<sup>18+</sup> | 3213 | 智能手表智感窗按键长按。 |
| KEYCODE_DIV<sup>20+</sup> | 3220 | 智能手表左按键，仅支持智能穿戴设备使用。 |
