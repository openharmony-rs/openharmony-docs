# CachedCountOptions

定义用于控制缓存计数行为的属性

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CachedCountOptions--><!--Device-unnamed-export declare interface CachedCountOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## independent

```TypeScript
independent?: boolean
```

cachedCount 是否按组计算。 true表示cachedCount按实际子组件个数计算，不按组计算；false表示如果displayCount.swipeByGroup=true，则cachedCount按组计算，否则按实际子组件个数计算。 默认值： false。 undefined 当设置为true时，cachedCount将根据实际的子组件计数来计算。 独立于displayCount分组计算。 &lt;br&gt;如果启用了SwiftByGroup并且该值为false，则cachedCount将按组计算。 &lt;/p&gt;。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CachedCountOptions-independent?: boolean--><!--Device-CachedCountOptions-independent?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
isShown?: boolean
```

预加载范围内的节点是否进行绘制。 true表示预加载范围内的节点进行绘制；false表示预加载范围内的节点不进行绘制。 默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CachedCountOptions-isShown?: boolean--><!--Device-CachedCountOptions-isShown?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

