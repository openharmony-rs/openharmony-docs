# LevelMode

弹窗显示层级模式。

**起始版本：** 15

<!--Device-unnamed-export enum LevelMode--><!--Device-unnamed-export enum LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OVERLAY

```TypeScript
OVERLAY = 0
```

弹窗层级为应用窗口根节点，应用内路由导航切换弹窗不隐藏。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-LevelMode-OVERLAY = 0--><!--Device-LevelMode-OVERLAY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EMBEDDED

```TypeScript
EMBEDDED = 1
```

弹窗节点为页面内路由/导航下的节点，随路由导航切换，弹窗随页面隐藏。

**说明：**

1. 目前只支持挂载在Page或者[NavDestination](../arkts-components/arkts-arkui-navdestination.md)节点上，优先挂载在Page节点下，只支持在这两种页面内顶层显示。2. 该模式下新起的页面可以覆盖在弹窗上，页面返回后该弹窗依旧存在，弹窗内容不会丢失。3. 该模式下需确保目标页面节点如Page节点已挂载上树，再拉起弹窗，否则弹窗将无法挂载到对应的页面节点内。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-LevelMode-EMBEDDED = 1--><!--Device-LevelMode-EMBEDDED = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

