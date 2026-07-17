# TabsNestedScrollMode

Tabs组件和父组件的嵌套滚动模式枚举。

**起始版本：** 24

<!--Device-unnamed-declare enum TabsNestedScrollMode--><!--Device-unnamed-declare enum TabsNestedScrollMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELF_ONLY

```TypeScript
SELF_ONLY = 0
```

Tabs自身滚动，不与父组件联动。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TabsNestedScrollMode-SELF_ONLY = 0--><!--Device-TabsNestedScrollMode-SELF_ONLY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELF_FIRST

```TypeScript
SELF_FIRST = 1
```

Tabs自身先滚动，自身滚动到边缘以后父组件滚动。父组件滚动到边缘以后，如果父组件有边缘效果，则父组件触发边缘效果，否则Tabs触发边缘效果。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TabsNestedScrollMode-SELF_FIRST = 1--><!--Device-TabsNestedScrollMode-SELF_FIRST = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

