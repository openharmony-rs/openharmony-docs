# RepeatMemOptStrategy

Repeat内存优化策略枚举。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

无内存优化策略。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_AUTO_CACHE_OPTIMIZATION

```TypeScript
ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0
```

自动内存优化策略，当Repeat子节点内存占用较高时，建议使用此策略以降低内存使用量。

当应用退后台时、Repeat所在组件不可见时（[visibility](arkts-arkui-commonmethod-c.md#visibility-1)属性设置为[Visible](arkts-arkui-visibility-e.md)以外的值，或组件面积为0，不考虑遮
挡）、整机低内存时（[MemoryLevel](../../apis-ability-kit/arkts-apis/arkts-ability-memorylevel-e.md)达到MEMORY_LEVEL_LOW或
MEMORY_LEVEL_CRITICAL），释放[缓存池](../../../../ui/rendering-control/arkts-new-rendering-control-repeat.md#节点更新复用能力说明)内的所有
节点。

当应用恢复前台时、Repeat所在组件恢复显示时，恢复缓存池内的节点。

在释放和恢复节点时，会触发[自定义组件生命周期](../../../../ui/state-management/arkts-page-custom-components-lifecycle.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

