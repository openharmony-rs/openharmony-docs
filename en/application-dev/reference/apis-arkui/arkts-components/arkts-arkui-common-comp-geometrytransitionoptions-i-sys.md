# GeometryTransitionOptions

```TypeScript
declare interface GeometryTransitionOptions
```

Defines the options of geometry transition.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hierarchyStrategy

```TypeScript
hierarchyStrategy?: TransitionHierarchyStrategy
```

Strategy for the hierarchical position movement of **in** / **out** components in the component tree during the shared element transition process. Default value: **TransitionHierarchyStrategy.ADAPTIVE**.

The setting significantly affects the front-to-back overlap relationship of the **in** / **out** components in comparison to other components. Exercise caution with it under normal conditions.

You are advised to adjust this setting only when there is an error in the component overlap relationship observed during the shared element transition process.

**Type:** [TransitionHierarchyStrategy](arkts-arkui-common-comp-transitionhierarchystrategy-e-sys.md)

**Default:** TransitionHierarchyStrategy.ADAPTIVE

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12 - 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
