# ScrollState

滑动状态枚举。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum ScrollState--><!--Device-unnamed-export declare enum ScrollState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Idle

```TypeScript
Idle
```

Idle state. Triggered when the scroll state returns to idle, and when the controller's non-animated methods are used to control the scroll.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollState-Idle--><!--Device-ScrollState-Idle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Scroll

```TypeScript
Scroll
```

Scrolling state. Triggered when the list is dragged with the finger, when the scrollbar is dragged, or when the mouse scroll wheel is used.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollState-Scroll--><!--Device-ScrollState-Scroll-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Fling

```TypeScript
Fling
```

Inertial scrolling state.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollState-Fling--><!--Device-ScrollState-Fling-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

