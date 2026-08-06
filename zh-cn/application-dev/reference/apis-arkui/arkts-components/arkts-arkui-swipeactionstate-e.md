# SwipeActionState

列表项滑动状态枚举。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-unnamed-declare enum SwipeActionState--><!--Device-unnamed-declare enum SwipeActionState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COLLAPSED

```TypeScript
COLLAPSED
```

收起状态，操作项处于隐藏状态。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionState-COLLAPSED--><!--Device-SwipeActionState-COLLAPSED-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EXPANDED

```TypeScript
EXPANDED
```

展开状态，操作项处于显示状态。 **说明：** 需要ListItem设置划出操作项。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionState-EXPANDED--><!--Device-SwipeActionState-EXPANDED-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ACTIONING

```TypeScript
ACTIONING
```

长距离状态，当ListItem进入长距删除区后删除ListItem的状态。 **说明：** actionAreaDistance的最终取值大于0，且小于ListItem在划动方向上的尺寸减去划出组件在划动方向上的尺寸时，滑动后松手的位置超过或等于该取值才能进入该状态。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeActionState-ACTIONING--><!--Device-SwipeActionState-ACTIONING-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

