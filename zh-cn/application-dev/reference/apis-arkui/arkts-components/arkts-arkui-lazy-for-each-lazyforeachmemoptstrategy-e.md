# LazyForEachMemOptStrategy

LazyForEach内存优化策略枚举。

**起始版本：** 26.0.0

<!--Device-unnamed-declare enum LazyForEachMemOptStrategy--><!--Device-unnamed-declare enum LazyForEachMemOptStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

无内存优化策略。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachMemOptStrategy-DEFAULT = 0--><!--Device-LazyForEachMemOptStrategy-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_AUTO_CACHE_OPTIMIZATION

```TypeScript
ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0
```

自动内存优化策略，当LazyForEach子节点内存占用较高时，建议使用此策略以降低内存使用量。

当应用退后台时、LazyForEach所在组件不可见时（[visibility](arkts-arkui-common-commonmethod-c.md#visibility-1)属性设置为[Visible](../arkts-apis/arkts-arkui-enums-visibility-e.md)以外的值，或组件面积为0，不考虑遮挡）、整机低内存时（[MemoryLevel](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-memorylevel-e.md)达到MEMORY_LEVEL_LOW或MEMORY_LEVEL_CRITICAL），释放[预加载区域](../../../../ui/rendering-control/arkts-rendering-control-overview.md#基本概念)内的部分节点，直至上下预加载区域内的节点数量均不超过2。

当应用恢复前台时、LazyForEach所在组件恢复显示时，LazyForEach发生滑动时，恢复预加载区域内的节点。

在释放和恢复节点时，会触发[自定义组件生命周期](../../../../ui/state-management/arkts-page-custom-components-lifecycle.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0--><!--Device-LazyForEachMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

