# DataPanelShadowOptions

DataPanelShadowOptions继承自[MultiShadowOptions](arkts-arkui-common-multishadowoptions-i.md)，具有MultiShadowOptions的全部属性。

**继承/实现关系：** DataPanelShadowOptions extends [MultiShadowOptions](arkts-arkui-common-multishadowoptions-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface DataPanelShadowOptions extends MultiShadowOptions--><!--Device-unnamed-declare interface DataPanelShadowOptions extends MultiShadowOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors?: Array<ResourceColor | LinearGradient>
```

各数据段投影的颜色。

默认值：与valueColors值相同

**说明：**

若设置的投影颜色的个数少于数据段个数时，则显示的投影颜色的个数和设置的投影颜色个数一致。

若设置的投影颜色的个数多于数据段个数时，则显示的投影颜色的个数和数据段个数一致。

**类型：** Array<ResourceColor | LinearGradient>

**默认值：** Consistent with valueColors

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataPanelShadowOptions-colors?: Array<ResourceColor | LinearGradient>--><!--Device-DataPanelShadowOptions-colors?: Array<ResourceColor | LinearGradient>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

