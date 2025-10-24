# oh_key_code.h

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines key codes of the key device.

**File to include**: <multimodalinput/oh_key_code.h>

**Library**: libohinput.so

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Related module**: [input](capi-input.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Input_KeyCode](#input_keycode) | Input_KeyCode | Key code.|

## Enum Description

### Input_KeyCode

```
enum Input_KeyCode
```

**Description**

Enumerates the key codes.

**Since**: 12

| Enum| Description|
| -- | -- |
| KEYCODE_UNKNOWN = -1 | Unknown key|
| KEYCODE_FN = 0 | Function (Fn) key|
| KEYCODE_HOME = 1 | Function (Home) key<br>**Since**: 22|
| KEYCODE_BACK = 2 | Back button<br>**Since**: 22|
| KEYCODE_SEARCH = 9 | Search key<br>**Since**: 22|
| KEYCODE_MEDIA_PLAY_PAUSE = 10 | Media: Play/Pause key<br>**Since**: 22<br>Difference between this key and **KEYCODE_PLAYPAUSE**:<br>**KEYCODE_PLAYPAUSE** is an earlier definition, while **KEYCODE_MEDIA_PLAY_PAUSE** is designed for modern media key devices.|
| KEYCODE_MEDIA_STOP = 11 | Media: Stop Key<br>**Since**: 22|
| KEYCODE_MEDIA_NEXT = 12 | Media: Next key<br>**Since**: 22|
| KEYCODE_MEDIA_PREVIOUS = 13 | Media: Previous key<br>**Since**: 22|
| KEYCODE_MEDIA_REWIND = 14 | Media: Rewind key<br>**Since**: 22|
| KEYCODE_MEDIA_FAST_FORWARD = 15 | Media: Fast Forward key<br>**Since**: 22|
| KEYCODE_VOLUME_UP = 16 | Volume Up key|
| KEYCODE_VOLUME_DOWN = 17 | Volume Down key|
| KEYCODE_POWER = 18 | Power key|
| KEYCODE_CAMERA = 19 | Camera key|
| KEYCODE_VOLUME_MUTE = 22 | Speaker Mute key|
| KEYCODE_MUTE = 23 | Mute key|
| KEYCODE_BRIGHTNESS_UP = 40 | Brightness Up key|
| KEYCODE_BRIGHTNESS_DOWN = 41 | Brightness Down key|
| KEYCODE_0 = 2000 | Key 0|
| KEYCODE_1 = 2001 | Key 1|
| KEYCODE_2 = 2002 | Key 2|
| KEYCODE_3 = 2003 | Key 3|
| KEYCODE_4 = 2004 | Key 4|
| KEYCODE_5 = 2005 | Key 5|
| KEYCODE_6 = 2006 | Key 6|
| KEYCODE_7 = 2007 | Key 7|
| KEYCODE_8 = 2008 | Key 8|
| KEYCODE_9 = 2009 | Key 9|
| KEYCODE_STAR = 2010 | Key *|
| KEYCODE_POUND = 2011 | Key #|
| KEYCODE_DPAD_UP = 2012 | Up key on D-pad|
| KEYCODE_DPAD_DOWN = 2013 | Down key on D-pad|
| KEYCODE_DPAD_LEFT = 2014 | Left key on D-pad|
| KEYCODE_DPAD_RIGHT = 2015 | Right key on D-pad|
| KEYCODE_DPAD_CENTER = 2016 | Center key on D-pad|
| KEYCODE_A = 2017 | Key A|
| KEYCODE_B = 2018 | Key B|
| KEYCODE_C = 2019 | Key C|
| KEYCODE_D = 2020 | Key D|
| KEYCODE_E = 2021 | Key E|
| KEYCODE_F = 2022 | Key F|
| KEYCODE_G = 2023 | Key G|
| KEYCODE_H = 2024 | Key H|
| KEYCODE_I = 2025 | Key I|
| KEYCODE_J = 2026 | Key J|
| KEYCODE_K = 2027 | Key K|
| KEYCODE_L = 2028 | Key L|
| KEYCODE_M = 2029 | Key M|
| KEYCODE_N = 2030 | Key N|
| KEYCODE_O = 2031 | Key O|
| KEYCODE_P = 2032 | Key P|
| KEYCODE_Q = 2033 | Key Q|
| KEYCODE_R = 2034 | Key R|
| KEYCODE_S = 2035 | Key S|
| KEYCODE_T = 2036 | Key T|
| KEYCODE_U = 2037 | Key U|
| KEYCODE_V = 2038 | Key V|
| KEYCODE_W = 2039 | Key W|
| KEYCODE_X = 2040 | Key X|
| KEYCODE_Y = 2041 | Key Y|
| KEYCODE_Z = 2042 | Key Z|
| KEYCODE_COMMA = 2043 | Key ,|
| KEYCODE_PERIOD = 2044 | Key .|
| KEYCODE_ALT_LEFT = 2045 | Left Alt key|
| KEYCODE_ALT_RIGHT = 2046 | Right Alt key|
| KEYCODE_SHIFT_LEFT = 2047 | Left Shift key|
| KEYCODE_SHIFT_RIGHT = 2048 | Right Shift key|
| KEYCODE_TAB = 2049 | Tab key|
| KEYCODE_SPACE = 2050 | Space key|
| KEYCODE_SYM = 2051 | Symbol key|
| KEYCODE_EXPLORER = 2052 | Explorer key, used to start the explorer application|
| KEYCODE_ENVELOPE = 2053 | Email key, used to start the email application|
| KEYCODE_ENTER = 2054 | Enter key|
| KEYCODE_DEL = 2055 | Delete key|
| KEYCODE_GRAVE = 2056 | Key `|
| KEYCODE_MINUS = 2057 | Key -|
| KEYCODE_EQUALS = 2058 | Key =|
| KEYCODE_LEFT_BRACKET = 2059 | Key [|
| KEYCODE_RIGHT_BRACKET = 2060 | Key ]|
| KEYCODE_BACKSLASH = 2061 | Key \|
| KEYCODE_SEMICOLON = 2062 | Key ;|
| KEYCODE_APOSTROPHE = 2063 | Key '|
| KEYCODE_SLASH = 2064 | Key /|
| KEYCODE_AT = 2065 | Key @|
| KEYCODE_PLUS = 2066 | Key +|
| KEYCODE_MENU = 2067 | Menu key|
| KEYCODE_PAGE_UP = 2068 | Page Up key|
| KEYCODE_PAGE_DOWN = 2069 | Page Down key|
| KEYCODE_ESCAPE = 2070 | ESC key|
| KEYCODE_FORWARD_DEL = 2071 | Forward Delete key|
| KEYCODE_CTRL_LEFT = 2072 | Left Ctrl key|
| KEYCODE_CTRL_RIGHT = 2073 | Right Ctrl key|
| KEYCODE_CAPS_LOCK = 2074 | Caps Lock key|
| KEYCODE_SCROLL_LOCK = 2075 | Scroll Lock key|
| KEYCODE_META_LEFT = 2076 | Left Meta key|
| KEYCODE_META_RIGHT = 2077 | Right Meta key|
| KEYCODE_FUNCTION = 2078 | Function key|
| KEYCODE_SYSRQ = 2079 | System Request/Print Screen key|
| KEYCODE_BREAK = 2080 | Break/Pause key|
| KEYCODE_MOVE_HOME = 2081 | Move to Home key|
| KEYCODE_MOVE_END = 2082 | Move to End key|
| KEYCODE_INSERT = 2083 | Insert key|
| KEYCODE_FORWARD = 2084 | Forward key|
| KEYCODE_MEDIA_PLAY = 2085 | Media: Play key|
| KEYCODE_MEDIA_PAUSE = 2086 | Media: Pause key|
| KEYCODE_MEDIA_CLOSE = 2087 | Media: Close key|
| KEYCODE_MEDIA_EJECT = 2088 | Media: Eject key|
| KEYCODE_MEDIA_RECORD = 2089 | Media: Record key|
| KEYCODE_F1 = 2090 | F1 key|
| KEYCODE_F2 = 2091 | F2 key|
| KEYCODE_F3 = 2092 | F3 key|
| KEYCODE_F4 = 2093 | F4 key|
| KEYCODE_F5 = 2094 | F5 key|
| KEYCODE_F6 = 2095 | F6 key|
| KEYCODE_F7 = 2096 | F7 key|
| KEYCODE_F8 = 2097 | F8 key|
| KEYCODE_F9 = 2098 | F9 key|
| KEYCODE_F10 = 2099 | F10 key|
| KEYCODE_F11 = 2100 | F11 key|
| KEYCODE_F12 = 2101 | F12 key|
| KEYCODE_NUM_LOCK = 2102 | Number Lock key|
| KEYCODE_NUMPAD_0 = 2103 | Key 0 on numeric keypad|
| KEYCODE_NUMPAD_1 = 2104 | Key 1 on numeric keypad|
| KEYCODE_NUMPAD_2 = 2105 | Key 2 on numeric keypad|
| KEYCODE_NUMPAD_3 = 2106 | Key 3 on numeric keypad|
| KEYCODE_NUMPAD_4 = 2107 | Key 4 on numeric keypad|
| KEYCODE_NUMPAD_5 = 2108 | Key 5 on numeric keypad|
| KEYCODE_NUMPAD_6 = 2109 | Key 6 on numeric keypad|
| KEYCODE_NUMPAD_7 = 2110 | Key 7 on numeric keypad|
| KEYCODE_NUMPAD_8 = 2111 | Key 8 on numeric keypad|
| KEYCODE_NUMPAD_9 = 2112 | Key 9 on numeric keypad|
| KEYCODE_NUMPAD_DIVIDE = 2113 | Key / on numeric keypad|
| KEYCODE_NUMPAD_MULTIPLY = 2114 | Key * on numeric keypad|
| KEYCODE_NUMPAD_SUBTRACT = 2115 | Key - on numeric keypad|
| KEYCODE_NUMPAD_ADD = 2116 | Key + on numeric keypad|
| KEYCODE_NUMPAD_DOT = 2117 | Key . on numeric keypad|
| KEYCODE_NUMPAD_COMMA = 2118 | Key , on numeric keypad|
| KEYCODE_NUMPAD_ENTER = 2119 | Enter key on numeric keypad|
| KEYCODE_NUMPAD_EQUALS = 2120 | Key = on numeric keypad|
| KEYCODE_NUMPAD_LEFT_PAREN = 2121 | Key ( on numeric keypad|
| KEYCODE_NUMPAD_RIGHT_PAREN = 2122 | Key ) on numeric keypad|
| KEYCODE_VIRTUAL_MULTITASK = 2210 | Multi-task key<br>**Since**: 22|
| KEYCODE_BUTTON_A = 2301 | Joystick key A<br>**Since**: 22|
| KEYCODE_BUTTON_B = 2302 | Joystick key B<br>**Since**: 22|
| KEYCODE_BUTTON_X = 2304 | Joystick key X<br>**Since**: 22|
| KEYCODE_BUTTON_Y = 2305 | Joystick key Y<br>**Since**: 22|
| KEYCODE_BUTTON_L1 = 2307 | Joystick key L1<br>**Since**: 22|
| KEYCODE_BUTTON_R1 = 2308 | Joystick key R1<br>**Since**: 22|
| KEYCODE_BUTTON_L2 = 2309 | Joystick key L2<br>**Since**: 22|
| KEYCODE_BUTTON_R2 = 2310 | Joystick key R2<br>**Since**: 22|
| KEYCODE_BUTTON_SELECT = 2311 | Joystick key Select<br>**Since**: 22|
| KEYCODE_BUTTON_START = 2312 | Joystick key Start<br>**Since**: 22|
| KEYCODE_BUTTON_MODE = 2313 | Joystick key Mode<br>**Since**: 22|
| KEYCODE_BUTTON_THUMBL = 2314 | Joystick key THUMBL<br>**Since**: 22|
| KEYCODE_BUTTON_THUMBR = 2315 | Joystick key THUMBR<br>**Since**: 22|
| KEYCODE_SLEEP = 2600 | Sleep key<br>**Since**: 22|
| KEYCODE_ZENKAKU_HANKAKU = 2601 | Zenkaku/Hankaku key<br>**Since**: 22|
| KEYCODE_102ND = 2602 | 102nd key<br>**Since**: 22|
| KEYCODE_RO = 2603 | Ro key<br>**Since**: 22|
| KEYCODE_KATAKANA = 2604 | Katakana key<br>**Since**: 22|
| KEYCODE_HIRAGANA = 2605 | Hiragana key<br>**Since**: 22|
| KEYCODE_HENKAN = 2606 | Henkan key<br>**Since**: 22|
| KEYCODE_KATAKANA_HIRAGANA = 2607 | Katakana/Hiragana key<br>**Since**: 22|
| KEYCODE_MUHENKAN = 2608 | Muhenkan key<br>**Since**: 22|
| KEYCODE_LINEFEED = 2609 | Linefeed key<br>**Since**: 22|
| KEYCODE_MACRO = 2610 | Macro key<br>**Since**: 22|
| KEYCODE_NUMPAD_PLUSMINUS = 2611 | Plus/Minus key on the numeric keypad<br>**Since**: 22|
| KEYCODE_SCALE = 2612 | Scale key<br>**Since**: 22|
| KEYCODE_HANGUEL = 2613 | Hanguel key<br>**Since**: 22|
| KEYCODE_HANJA = 2614 | Hanja key<br>**Since**: 22|
| KEYCODE_YEN = 2615 | Yen key<br>**Since**: 22|
| KEYCODE_STOP = 2616 | Stop key<br>**Since**: 22|
| KEYCODE_AGAIN = 2617 | Again key<br>**Since**: 22|
| KEYCODE_PROPS = 2618 | Props key<br>**Since**: 22|
| KEYCODE_UNDO = 2619 | Undo key<br>**Since**: 22|
| KEYCODE_COPY = 2620 | Copy key<br>**Since**: 22|
| KEYCODE_OPEN = 2621 | Open key<br>**Since**: 22|
| KEYCODE_PASTE = 2622 | Paste key<br>**Since**: 22|
| KEYCODE_FIND = 2623 | Find key<br>**Since**: 22|
| KEYCODE_CUT = 2624 | Cut key<br>**Since**: 22|
| KEYCODE_HELP = 2625 | Help key<br>**Since**: 22|
| KEYCODE_CALC = 2626 | Calc key, which is used to start the calculator application<br>**Since**: 22|
| KEYCODE_FILE = 2627 | File key<br>**Since**: 22|
| KEYCODE_BOOKMARKS = 2628 | Bookmarks key<br>**Since**: 22|
| KEYCODE_NEXT = 2629 | Page Down key<br>**Since**: 22|
| KEYCODE_PLAYPAUSE = 2630 | Media: Play/Pause key<br>**Since**: 22<br>Difference between this key and **KEYCODE_MEDIA_PLAY_PAUSE**:<br>**KEYCODE_PLAYPAUSE** is an earlier definition, while **KEYCODE_MEDIA_PLAY_PAUSE** is designed for modern media key devices.|
| KEYCODE_PREVIOUS = 2631 | Page Up key<br>**Since**: 22|
| KEYCODE_STOPCD = 2632 | Stop CD key<br>**Since**: 22|
| KEYCODE_CONFIG = 2634 | Configuration key<br>**Since**: 22|
| KEYCODE_REFRESH = 2635 | Refresh key<br>**Since**: 22|
| KEYCODE_EXIT = 2636 | Exit key<br>**Since**: 22|
| KEYCODE_EDIT = 2637 | Edit key<br>**Since**: 22|
| KEYCODE_SCROLLUP = 2638 | Scroll Up key<br>**Since**: 22|
| KEYCODE_SCROLLDOWN = 2639 | Scroll Down key<br>**Since**: 22|
| KEYCODE_NEW = 2640 | New key<br>**Since**: 22|
| KEYCODE_REDO = 2641 | Redo key<br>**Since**: 22|
| KEYCODE_CLOSE = 2642 | Close key<br>**Since**: 22|
| KEYCODE_PLAY = 2643 | Play key<br>**Since**: 22|
| KEYCODE_BASSBOOST = 2644 | Bass Boost key<br>**Since**: 22|
| KEYCODE_PRINT = 2645 | Print key<br>**Since**: 22|
| KEYCODE_CHAT = 2646 | Chat key<br>**Since**: 22|
| KEYCODE_FINANCE = 2647 | Finance key<br>**Since**: 22|
| KEYCODE_CANCEL = 2648 | Cancel key<br>**Since**: 22|
| KEYCODE_KBDILLUM_TOGGLE = 2649 | Keyboard Illumination Toggle key<br>**Since**: 22|
| KEYCODE_KBDILLUM_DOWN = 2650 | Keyboard Illumination Down key<br>**Since**: 22|
| KEYCODE_KBDILLUM_UP = 2651 | Keyboard Illumination Up key<br>**Since**: 22|
| KEYCODE_SEND = 2652 | Send key<br>**Since**: 22|
| KEYCODE_REPLY = 2653 | Reply key<br>**Since**: 22|
| KEYCODE_FORWARDMAIL = 2654 | Forward Mail key<br>**Since**: 22|
| KEYCODE_SAVE = 2655 | Save key<br>**Since**: 22|
| KEYCODE_DOCUMENTS = 2656 | Documents key<br>**Since**: 22|
| KEYCODE_VIDEO_NEXT = 2657 | Next Video key<br>**Since**: 22|
| KEYCODE_VIDEO_PREV = 2658 | Previous Video key<br>**Since**: 22|
| KEYCODE_BRIGHTNESS_CYCLE = 2659 | Brightness Cycle key<br>**Since**: 22|
| KEYCODE_BRIGHTNESS_ZERO = 2660 | Brightness Zero key<br>**Since**: 22|
| KEYCODE_DISPLAY_OFF = 2661 | Display Off Key<br>**Since**: 22|
| KEYCODE_BTN_MISC = 2662 | Misc Button key<br>**Since**: 22|
| KEYCODE_GOTO = 2663 | Goto key<br>**Since**: 22|
| KEYCODE_INFO = 2664 | Info key<br>**Since**: 22|
| KEYCODE_PROGRAM = 2665 | Program key<br>**Since**: 22|
| KEYCODE_PVR = 2666 | PVR key<br>**Since**: 22|
| KEYCODE_SUBTITLE = 2667 | Subtitle key<br>**Since**: 22|
| KEYCODE_FULL_SCREEN = 2668 | Full Screen key<br>**Since**: 22|
| KEYCODE_KEYBOARD = 2669 | Keyboard<br>**Since**: 22|
| KEYCODE_ASPECT_RATIO = 2670 | Aspect Ratio key<br>**Since**: 22|
| KEYCODE_PC = 2671 | Port Control key<br>**Since**: 22|
| KEYCODE_TV = 2672 | TV key<br>**Since**: 22|
| KEYCODE_TV2 = 2673 | TV key 2<br>**Since**: 22|
| KEYCODE_VCR = 2674 | VCR key<br>**Since**: 22|
| KEYCODE_VCR2 = 2675 | VCR key 2<br>**Since**: 22|
| KEYCODE_SAT = 2676 | SAT key<br>**Since**: 22|
| KEYCODE_CD = 2677 | CD key<br>**Since**: 22|
| KEYCODE_TAPE = 2678 | Tape key<br>**Since**: 22|
| KEYCODE_TUNER = 2679 | Tuner key<br>**Since**: 22|
| KEYCODE_PLAYER = 2680 | Player key<br>**Since**: 22|
| KEYCODE_DVD = 2681 | DVD key<br>**Since**: 22|
| KEYCODE_AUDIO = 2682 | Audio key<br>**Since**: 22|
| KEYCODE_VIDEO = 2683 | Video key<br>**Since**: 22|
| KEYCODE_MEMO = 2684 | Memo key<br>**Since**: 22|
| KEYCODE_CALENDAR = 2685 | Calendar key<br>**Since**: 22|
| KEYCODE_RED = 2686 | Red indicator<br>**Since**: 22|
| KEYCODE_GREEN = 2687 | Green indicator<br>**Since**: 22|
| KEYCODE_YELLOW = 2688 | Yellow indicator<br>**Since**: 22|
| KEYCODE_BLUE = 2689 | Blue indicator<br>**Since**: 22|
| KEYCODE_CHANNELUP = 2690 | Channel Up key<br>**Since**: 22|
| KEYCODE_CHANNELDOWN = 2691 | Channel Down key<br>**Since**: 22|
| KEYCODE_LAST = 2692 | Last key<br>**Since**: 22|
| KEYCODE_RESTART = 2693 | Restart key<br>**Since**: 22|
| KEYCODE_SLOW = 2694 | Slow key<br>**Since**: 22|
| KEYCODE_SHUFFLE = 2695 | Shuffle key<br>**Since**: 22|
| KEYCODE_VIDEOPHONE = 2696 | Videophone key<br>**Since**: 22|
| KEYCODE_GAMES = 2697 | Games key<br>**Since**: 22|
| KEYCODE_ZOOMIN = 2698 | Zoom In key<br>**Since**: 22|
| KEYCODE_ZOOMOUT = 2699 | Zoom Out key<br>**Since**: 22|
| KEYCODE_ZOOMRESET = 2700 | Zoom Reset key<br>**Since**: 22|
| KEYCODE_WORDPROCESSOR = 2701 | Word Processor key<br>**Since**: 22|
| KEYCODE_EDITOR = 2702 | Editor key<br>**Since**: 22|
| KEYCODE_SPREADSHEET = 2703 | Spreadsheet key<br>**Since**: 22|
| KEYCODE_GRAPHICSEDITOR = 2704 | Graphics Editor key<br>**Since**: 22|
| KEYCODE_PRESENTATION = 2705 | Presentation key<br>**Since**: 22|
| KEYCODE_DATABASE = 2706 | Database key<br>**Since**: 22|
| KEYCODE_NEWS = 2707 | News key<br>**Since**: 22|
| KEYCODE_VOICEMAIL = 2708 | Voice mailbox<br>**Since**: 22|
| KEYCODE_ADDRESSBOOK = 2709 | Address book key<br>**Since**: 22|
| KEYCODE_MESSENGER = 2710 | Messenger key<br>**Since**: 22|
| KEYCODE_BRIGHTNESS_TOGGLE = 2711 | Brightness Toggle key<br>**Since**: 22|
| KEYCODE_SPELLCHECK = 2712 | Spell Check key<br>**Since**: 22|
| KEYCODE_COFFEE = 2713 | Coffee key, which is used to launch screen lock or screen saver<br>**Since**: 22|
| KEYCODE_MEDIA_REPEAT = 2714 | Media Repeat key<br>**Since**: 22|
| KEYCODE_IMAGES = 2715 | Images key<br>**Since**: 22|
| KEYCODE_BUTTONCONFIG = 2716 | Button Configuration key<br>**Since**: 22|
| KEYCODE_TASKMANAGER = 2717 | Task Manager<br>**Since**: 22|
| KEYCODE_JOURNAL = 2718 | Log key<br>**Since**: 22|
| KEYCODE_CONTROLPANEL = 2719 | Control Panel key<br>**Since**: 22|
| KEYCODE_APPSELECT = 2720 | App Select key<br>**Since**: 22|
| KEYCODE_SCREENSAVER = 2721 | Screen Saver key<br>**Since**: 22|
| KEYCODE_ASSISTANT = 2722 | Assistant key<br>**Since**: 22|
| KEYCODE_KBD_LAYOUT_NEXT  = 2723 | Next Keyboard Layout key<br>**Since**: 22|
| KEYCODE_BRIGHTNESS_MIN = 2724 | Min Brightness key<br>**Since**: 22|
| KEYCODE_BRIGHTNESS_MAX = 2725 | Max Brightness key<br>**Since**: 22|
| KEYCODE_KBDINPUTASSIST_PREV = 2726 | Assist_Previous key, used to view historical inputs<br>**Since**: 22|
| KEYCODE_KBDINPUTASSIST_NEXT = 2727 | Assist_Next key, used to view predictive inputs<br>**Since**: 22|
| KEYCODE_KBDINPUTASSIST_PREVGROUP = 2728 | Assist_Previous_Group key, used to switch to the previous input method in the input group<br>**Since**: 22|
| KEYCODE_KBDINPUTASSIST_NEXTGROUP = 2729 | Assist_Next_Group key, used to switch to the next input method in the input group<br>**Since**: 22|
| KEYCODE_KBDINPUTASSIST_ACCEPT = 2730 | Keyboard Input-assisted Accept key<br>**Since**: 22|
| KEYCODE_KBDINPUTASSIST_CANCEL = 2731 | Keyboard Input-assisted Cancel key<br>**Since**: 22|
| KEYCODE_FRONT = 2800 | Front key, which is used to launch the windshield defogger<br>**Since**: 22|
| KEYCODE_SETUP = 2801 | Setup key<br>**Since**: 22|
| KEYCODE_WAKEUP = 2802 | Wakeup key<br>**Since**: 22|
| KEYCODE_SENDFILE = 2803 | Send File key<br>**Since**: 22|
| KEYCODE_DELETEFILE = 2804 | Delete File key<br>**Since**: 22|
| KEYCODE_XFER = 2805 | XFER key, which is used to start file transfer<br>**Since**: 22|
| KEYCODE_PROG1 = 2806 | Program key 1<br>**Since**: 22|
| KEYCODE_PROG2 = 2807 | Program key 2<br>**Since**: 22|
| KEYCODE_MSDOS = 2808 | MS-DOS key<br>**Since**: 22|
| KEYCODE_SCREENLOCK = 2809 | Screen Lock key<br>**Since**: 22|
| KEYCODE_DIRECTION_ROTATE_DISPLAY = 2810 | Directional Rotation Display key<br>**Since**: 22|
| KEYCODE_CYCLEWINDOWS = 2811 | Windows Cycle key<br>**Since**: 22|
| KEYCODE_COMPUTER = 2812 | Computer key<br>**Since**: 22|
| KEYCODE_EJECTCLOSECD = 2813 | Eject CD key<br>**Since**: 22|
| KEYCODE_ISO = 2814 | ISO key<br>**Since**: 22|
| KEYCODE_MOVE = 2815 | Move key<br>**Since**: 22|
| KEYCODE_F13 = 2816 | F13 key<br>**Since**: 22|
| KEYCODE_F14 = 2817 | F14 key<br>**Since**: 22|
| KEYCODE_F15 = 2818 | F15 key<br>**Since**: 22|
| KEYCODE_F16 = 2819 | F16 key<br>**Since**: 22|
| KEYCODE_F17 = 2820 | F17 key<br>**Since**: 22|
| KEYCODE_F18 = 2821 | F18 key<br>**Since**: 22|
| KEYCODE_F19 = 2822 | F19 key<br>**Since**: 22|
| KEYCODE_F20 = 2823 | F20 key<br>**Since**: 22|
| KEYCODE_F21 = 2824 | F21 key<br>**Since**: 22|
| KEYCODE_F22 = 2825 | F22 key<br>**Since**: 22|
| KEYCODE_F23 = 2826 | F23 key<br>**Since**: 22|
| KEYCODE_F24 = 2827 | F24 key<br>**Since**: 22|
| KEYCODE_PROG3 = 2828 | Program key 3<br>**Since**: 22|
| KEYCODE_PROG4 = 2829 | Program key 4<br>**Since**: 22|
| KEYCODE_DASHBOARD = 2830 | Dashboard<br>**Since**: 22|
| KEYCODE_SUSPEND = 2831 | Suspend key<br>**Since**: 22|
| KEYCODE_HP = 2832 | HP key<br>**Since**: 22|
| KEYCODE_SOUND = 2833 | Sound key<br>**Since**: 22|
| KEYCODE_QUESTION = 2834 | Question key<br>**Since**: 22|
| KEYCODE_CONNECT = 2836 | Connect key<br>**Since**: 22|
| KEYCODE_SPORT = 2837 | Sport key<br>**Since**: 22|
| KEYCODE_SHOP = 2838 | Shop key<br>**Since**: 22|
| KEYCODE_ALTERASE = 2839 | Alternate key<br>**Since**: 22|
| KEYCODE_SWITCHVIDEOMODE  = 2841 | Switch Video Mode key (monitor, LCD, and TV, etc.)<br>**Since**: 22|
| KEYCODE_BATTERY = 2842 | Battery key<br>**Since**: 22|
| KEYCODE_BLUETOOTH = 2843 | Bluetooth key<br>**Since**: 22|
| KEYCODE_WLAN = 2844 | WLAN key<br>**Since**: 22|
| KEYCODE_UWB = 2845 | Ultra-wideband key<br>**Since**: 22|
| KEYCODE_WWAN_WIMAX = 2846 | WWAN WiMAX key<br>**Since**: 22|
| KEYCODE_RFKILL = 2847 | RF Kill key<br>**Since**: 22|
| KEYCODE_CHANNEL = 3001 | Channel key<br>**Since**: 22|
| KEYCODE_BTN_0 = 3100 | Button 0<br>**Since**: 22|
| KEYCODE_BTN_1 = 3101 | Button 1<br>**Since**: 22|
| KEYCODE_BTN_2 = 3102 | Button 2<br>**Since**: 22|
| KEYCODE_BTN_3 = 3103 | Button 3<br>**Since**: 22|
| KEYCODE_BTN_4 = 3104 | Button 4<br>**Since**: 22|
| KEYCODE_BTN_5 = 3105 | Button 5<br>**Since**: 22|
| KEYCODE_BTN_6 = 3106 | Button 6<br>**Since**: 22|
| KEYCODE_BTN_7 = 3107 | Button 7<br>**Since**: 22|
| KEYCODE_BTN_8 = 3108 | Button 8<br>**Since**: 22|
| KEYCODE_BTN_9 = 3109 | Button 9<br>**Since**: 22|
| KEYCODE_DAGGER_CLICK = 3211 | Single tapping the smart watch's X-TAP sensor<br>**Since**: 18|	
| KEYCODE_DAGGER_DOUBLE_CLICK = 3212 | Double tapping the smart watch's X-TAP sensor<br>**Since**: 18|	
| KEYCODE_DAGGER_LONG_PRESS = 3213 | Long-pressing the smart watch's X-TAP sensor<br>**Since**: 18|
| KEYCODE_DIV = 3220 | Left button of the smart watch<br>**Since**: 22|
