# AnimationMode

点击[TabBar](TabContentAttribute#tabBar(options: string | Resource | CustomBuilder | TabBarOptions))页签时切换TabContent的动画形式枚举。

**起始版本：** 12

<!--Device-unnamed-declare enum AnimationMode--><!--Device-unnamed-declare enum AnimationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_FIRST

```TypeScript
CONTENT_FIRST = 0
```

先加载目标页内容，再开始切换动画。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AnimationMode-CONTENT_FIRST = 0--><!--Device-AnimationMode-CONTENT_FIRST = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ACTION_FIRST

```TypeScript
ACTION_FIRST = 1
```

先开始切换动画，再加载目标页内容；生效需要同时需要满足：Tabs的height、width没有设置成auto。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AnimationMode-ACTION_FIRST = 1--><!--Device-AnimationMode-ACTION_FIRST = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NO_ANIMATION

```TypeScript
NO_ANIMATION = 2
```

关闭默认动画。调用TabsController的[changeIndex](arkts-arkui-tabscontroller-c.md#changeindex-1)接口切换TabContent时该枚举值不生效。

可以通过设置[animationDuration](TabsAttribute#animationDuration)为0实现调用TabsController的changeIndex接口时不带动画。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AnimationMode-NO_ANIMATION = 2--><!--Device-AnimationMode-NO_ANIMATION = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_FIRST_WITH_JUMP

```TypeScript
CONTENT_FIRST_WITH_JUMP = 3
```

先加载目标页内容，再无动画跳转到目标页附近，最后有动画跳转到目标页。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-AnimationMode-CONTENT_FIRST_WITH_JUMP = 3--><!--Device-AnimationMode-CONTENT_FIRST_WITH_JUMP = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ACTION_FIRST_WITH_JUMP

```TypeScript
ACTION_FIRST_WITH_JUMP = 4
```

先无动画跳转到目标页附近，再有动画跳转到目标页，最后加载目标页内容。此项生效需要同时需要满足：Tabs的height、width没有设置成auto。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-AnimationMode-ACTION_FIRST_WITH_JUMP = 4--><!--Device-AnimationMode-ACTION_FIRST_WITH_JUMP = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

