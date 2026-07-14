# CachedCountOptions

预加载子组件的配置选项。

**起始版本：** 24

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## independent

```TypeScript
independent?: boolean
```

[cachedCount](SwiperAttribute#cachedCount(count: number, options: CachedCountOptions))是否按组计算。

设置为true时，cachedCount按实际子组件个数计算，不按组计算。

设置为false时，如果displayCount.swipeByGroup=true，则cachedCount按组计算，否则按实际子组件个数计算。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
isShown?: boolean
```

预加载范围内的节点是否进行绘制。

设置为true时，预加载范围内的节点进行绘制。

设置为false时，预加载范围内的节点不进行绘制。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

