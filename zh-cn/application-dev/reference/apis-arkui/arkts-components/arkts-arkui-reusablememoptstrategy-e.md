# ReusableMemOptStrategy

可复用自定义组件内存优化策略枚举。@enum { number }

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

无内存优化策略。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_AUTO_CACHE_OPTIMIZATION

```TypeScript
ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0
```

自动内存优化策略。建议在需要降低可复用自定义组件内存使用量的场景下使用此策略。满足以下任一条件时，释放复用池内的所有该类型自定义组件：  
- 应用退后台时。  
- 复用池所在组件不可见时（[visibility](arkts-arkui-commonmethod-c.md#visibility)属性设置为Visible以外的值，或组件面积为0，不考虑遮挡）。  
- 整机低内存时（[MemoryLevel](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-memorylevel-e.md)达到MEMORY_LEVEL_LOW或  
MEMORY_LEVEL_CRITICAL）。当复用池中相同ReuseId的该类型自定义组件数量超过8，且5分钟内不再增加时，保留8个组件，释放其余组件。在释放节点时，会触发[自定义组件生命周期](../../../ui/state-management/arkts-page-custom-components-lifecycle.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
