# ReusableMemOptStrategy

可复用自定义组件内存优化策略枚举。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-declare enum ReusableMemOptStrategy--><!--Device-unnamed-declare enum ReusableMemOptStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

无内存优化策略。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ReusableMemOptStrategy-DEFAULT = 0--><!--Device-ReusableMemOptStrategy-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_AUTO_CACHE_OPTIMIZATION

```TypeScript
ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0
```

自动内存优化策略。建议在需要降低可复用自定义组件内存使用量的场景下使用此策略。 满足以下任一条件时，释放复用池内的所有该类型自定义组件： - 应用退后台时。 - 复用池所在组件不可见时（[visibility]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_属性设置为[Visible]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_以外的值，或组件面积为0，不考虑遮挡）。 - 整机低内存时（[MemoryLevel]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_达到MEMORY\_LEVEL\_LOW或 MEMORY\_LEVEL\_CRITICAL）。 当复用池中相同ReuseId的该类型自定义组件数量超过8，且5分钟内不再增加时，保留8个组件，释放其余组件。 在释放节点时，会触发\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ReusableMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0--><!--Device-ReusableMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

