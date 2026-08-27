# ExpandMode

子节点展开模式枚举。

**起始版本：** 15

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NOT_EXPAND

```TypeScript
NOT_EXPAND = 0
```

表示不展开当前FrameNode的子节点。如果FrameNode包含LazyForEach子节点，获取在主节点树上的子节点时，不展 开当前FrameNode的子节点。子节点序列号按在主节点树上的子节点计算。使用场景：仅需获取主节点树上已展开子节点且不触发展开操作的场景。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EXPAND

```TypeScript
EXPAND = 1
```

表示展开当前FrameNode的子节点。如果FrameNode包含LazyForEach子节点，获取所有子节点时，展开当前 FrameNode的子节点。子节点序列号按所有子节点计算。使用场景：需要获取包含懒加载在内的所有子节点的场景。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LAZY_EXPAND

```TypeScript
LAZY_EXPAND = 2
```

表示按需展开当前FrameNode的子节点。如果FrameNode包含LazyForEach子节点，获取在主节点树上的子节点时，不 展开当前FrameNode的子节点；获取不在主节点树上的子节点时，展开当前FrameNode的子节点。子节点序列号按所有子节点计算。使用场景：需要兼顾主节点树与非主节点树子节点按需获取的场景。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LAZY_NOT_EXPAND

```TypeScript
LAZY_NOT_EXPAND = 3
```

表示不展开当前FrameNode的子节点，如果FrameNode包含LazyForEach子节点，对于已经展开的子节点，可以直接返 回，获取未展开的子节点时，仅创建对应位置的节点，而不展开所有子节点。子节点序列号按所有子节点计算。使用场景：需要按位置精确获取子节点但不批量展开懒加载子节点的场景。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
