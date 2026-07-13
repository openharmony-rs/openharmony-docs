# ChildrenCountMode

子节点计数模式枚举。用于指定获取子节点数量时的计数方式。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ALL_EXPAND

```TypeScript
ALL_EXPAND = 0
```

展开模式。当遇到懒加载节点（如[LazyForEach](../arkts-components/arkts-arkui-lazyforeach.md)）时，展开节点并返回所有子节点数量。

是否展开懒加载节点：是

使用场景：需要展开并返回所有子节点数量的场景。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ONLY_EXPANDED

```TypeScript
ONLY_EXPANDED = 1
```

计数已展开模式。不展开懒加载节点，只返回当前已展开的子节点数量。未展开的懒加载节点不包含在计数中。

是否展开懒加载节点：否

使用场景：仅查询已展开子节点数量的场景。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ALL_NOT_EXPAND

```TypeScript
ALL_NOT_EXPAND = 2
```

计数所有模式。不展开懒加载节点，但返回包含所有潜在子节点的数量（包括已展开和未展开的懒加载节点）。此模式提供潜在子节点总数而不触发展开操作。

是否展开懒加载节点：否

使用场景：需要获取所有子节点数量的场景，与ALL_EXPAND相比，该模式不会展开子节点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

