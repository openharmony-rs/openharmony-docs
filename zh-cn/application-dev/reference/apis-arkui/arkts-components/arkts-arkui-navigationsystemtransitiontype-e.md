# NavigationSystemTransitionType

系统转场动画类型。
> **说明：**
> 设置系统转场动画，支持分别设置系统标题栏动画和内容动画。
> 系统默认转场动画中只有STANDARD页面的push和pop动画有单独的标题栏动画，存在如下限制：
> 设置NONE或者TITLE时没有系统转场动画，设置CONTENT和DEFAULT时默认系统转场动画。

**起始版本：** 14

<!--Device-unnamed-declare enum NavigationSystemTransitionType--><!--Device-unnamed-declare enum NavigationSystemTransitionType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认系统转场动画。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationSystemTransitionType-DEFAULT = 0--><!--Device-NavigationSystemTransitionType-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 1
```

无系统转场动画。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationSystemTransitionType-NONE = 1--><!--Device-NavigationSystemTransitionType-NONE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TITLE

```TypeScript
TITLE = 2
```

标题栏系统转场动画。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationSystemTransitionType-TITLE = 2--><!--Device-NavigationSystemTransitionType-TITLE = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTENT

```TypeScript
CONTENT = 3
```

内容区系统转场动画。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationSystemTransitionType-CONTENT = 3--><!--Device-NavigationSystemTransitionType-CONTENT = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FADE

```TypeScript
FADE = 4
```

渐变类型的系统转场动画。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationSystemTransitionType-FADE = 4--><!--Device-NavigationSystemTransitionType-FADE = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EXPLODE

```TypeScript
EXPLODE = 5
```

中心缩放类型的系统转场动画。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationSystemTransitionType-EXPLODE = 5--><!--Device-NavigationSystemTransitionType-EXPLODE = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_RIGHT

```TypeScript
SLIDE_RIGHT = 6
```

右侧平移类型的系统转场动画。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationSystemTransitionType-SLIDE_RIGHT = 6--><!--Device-NavigationSystemTransitionType-SLIDE_RIGHT = 6-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_BOTTOM

```TypeScript
SLIDE_BOTTOM = 7
```

底部平移类型的系统转场动画。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationSystemTransitionType-SLIDE_BOTTOM = 7--><!--Device-NavigationSystemTransitionType-SLIDE_BOTTOM = 7-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

