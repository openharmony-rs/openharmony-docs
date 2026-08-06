# BottomOffset

设置不同情景模式下弹框距离底部的距离，判断依据为是否存在菜单栏，默认显示为不存在菜单栏情况下的距离。 | 名称 | 值 | 说明 | | - | - | - | | OFFSET\_FOR\_BAR | 0 | 存在菜单栏情况下与窗口底部的距离。设置后弹框距离底部88vp。 | | OFFSET\_FOR\_NONE | 1 | 不存在菜单栏情况下与窗口底部的距离。默认值，设置后弹框距离底部44vp。 |

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-export declare enum BottomOffset--><!--Device-unnamed-export declare enum BottomOffset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSET_FOR_BAR

```TypeScript
OFFSET_FOR_BAR = 0
```

dialog distance relative to the bottom in the presence of tabs.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BottomOffset-OFFSET_FOR_BAR = 0--><!--Device-BottomOffset-OFFSET_FOR_BAR = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSET_FOR_NONE

```TypeScript
OFFSET_FOR_NONE = 1
```

dialog is the distance relative to the bottom without tabs.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BottomOffset-OFFSET_FOR_NONE = 1--><!--Device-BottomOffset-OFFSET_FOR_NONE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

