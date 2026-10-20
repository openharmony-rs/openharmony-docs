# scroll.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @shengu_lancer; @rongShao-Z-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

提供滚动到指定索引时使用的快速滚动模式枚举。

**引用文件：** <arkui/node_attributes/scroll.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_FastScrollMode](#oh_arkui_fastscrollmode) | OH_ArkUI_FastScrollMode | 定义滚动到指定索引时使用的快速滚动模式，用于设置[NODE_LIST_SCROLL_TO_INDEX](capi-native-node-h-nodeattributetype-scrollablecontainer.md#node_list_scroll_to_index)的.value[4]?.i32参数。仅当.value[1]?.i32为1（开启动效）时生效。 |

## 枚举类型说明

### OH_ArkUI_FastScrollMode

```c
enum OH_ArkUI_FastScrollMode
```

**描述：**

定义滚动到指定索引时使用的快速滚动模式，用于设置[NODE_LIST_SCROLL_TO_INDEX](capi-native-node-h-nodeattributetype-scrollablecontainer.md#node_list_scroll_to_index)的.value[4]?.i32参数。仅当.value[1]?.i32为1（开启动效）时生效。

> **说明：**
>
> - 当滚动距离较大且触发跳跃时，通常先从起始位置连续滚动约2屏，再跳到距离最终停靠位置约2屏的位置，继续滚动至最终位置。一屏指List可视区域在滚动方向上的长度。
> - 跳过创建或测量只针对上述被跳过的滚动路径；前后两段连续滚动中需要显示的子组件仍会按需创建和测量。实际创建和测量的范围还受对齐方式、额外偏移量和子组件大小等因素影响，并非固定为4屏。
> - 快速滚动不保证遍历并显示滚动路径上的每一个子组件。
> - 向NODE_LIST_SCROLL_TO_INDEX传入本枚举未定义的值时，按OH_ARKUI_FAST_SCROLL_MODE_NONE处理，不启用快速滚动优化，其余滚动参数仍按原有规则生效。

**起始版本：** 26.2.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_FAST_SCROLL_MODE_NONE = 0 | 不启用快速滚动优化，与不设置快速滚动模式参数时的行为相同。开启动画时，会在动画开始前创建并测量滚动路径上的所有子组件。 |
| OH_ARKUI_FAST_SCROLL_MODE_SKIP_MEASURE = 1 | 跳过中间子组件的测量，仍可创建中间子组件以确认类型和目标所在行。适用于多列List中同时存在ListItem和ListItemGroup的场景：ListItem占一行中的一列，ListItemGroup占满一整行，需要根据子组件类型确定目标所在行。 |
| OH_ARKUI_FAST_SCROLL_MODE_SKIP_CREATE_AND_MEASURE = 2 | 跳过中间子组件的创建和测量，进一步减少开销。<br/>**说明：**<br/>不适用于多列List中同时存在ListItem和ListItemGroup的场景。在该场景下使用此模式会导致List布局和滚动异常，应改用OH_ARKUI_FAST_SCROLL_MODE_SKIP_MEASURE。 |
