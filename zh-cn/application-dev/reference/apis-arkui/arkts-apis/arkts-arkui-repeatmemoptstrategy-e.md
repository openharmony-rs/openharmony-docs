# RepeatMemOptStrategy

Repeat内存优化策略枚举。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-declare enum RepeatMemOptStrategy--><!--Device-unnamed-declare enum RepeatMemOptStrategy-End-->

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

<!--Device-RepeatMemOptStrategy-DEFAULT = 0--><!--Device-RepeatMemOptStrategy-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_AUTO_CACHE_OPTIMIZATION

```TypeScript
ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0
```

自动内存优化策略，当需要降低Repeat子节点的内存占用时，建议使用此策略以降低内存使用量。 当应用退后台时、Repeat所在组件不可见时（[visibility]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_属性设置为[Visible]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_以外的值，或组件面积为0，不考虑遮 挡）、整机低内存时（[MemoryLevel]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_达到MEMORY\_LEVEL\_LOW或 MEMORY\_LEVEL\_CRITICAL），释放\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_内的所有 节点。 当应用恢复前台时、Repeat所在组件恢复显示时，恢复缓存池内的节点。 在释放和恢复节点时，会触发\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RepeatMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0--><!--Device-RepeatMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

