# NavigationMode

导航页显示模式。Navigation处于分栏显示状态时，导航页和内容区之间会显示分割线。 > **说明：** > > 为了简化表示，可以将`组件宽度 - minContentWidth - 分割线宽度 (1px)`称为calcNavBarWidth。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum NavigationMode--><!--Device-unnamed-export declare enum NavigationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Stack

```TypeScript
Stack
```

The navigation bar and the content area are displayed in stack.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationMode-Stack--><!--Device-NavigationMode-Stack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Split

```TypeScript
Split
```

The navigation bar and the content area are displayed side by side.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationMode-Split--><!--Device-NavigationMode-Split-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto
```

If the window width is greater than the sum of minNavBarWidth and minContentWidth, the navigation component is displayed in split mode. Otherwise it's displayed in stack mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationMode-Auto--><!--Device-NavigationMode-Auto-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO_WITH_ASPECT_RATIO

```TypeScript
AUTO_WITH_ASPECT_RATIO
```

如果导航宽度大于minNavBarWidth和minContentWidth之和。 导航组件的长宽比（高宽比）小于等于1.2， 则导航组件以分割方式显示。否则它将以堆栈模式显示。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationMode-AUTO_WITH_ASPECT_RATIO--><!--Device-NavigationMode-AUTO_WITH_ASPECT_RATIO-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

