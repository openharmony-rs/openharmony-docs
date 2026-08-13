# CacheCountInfo

缓存数量信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CacheCountInfo--><!--Device-unnamed-export declare interface CacheCountInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxCount

```TypeScript
maxCount: int
```

最大缓存数，当实际缓存数大于最大缓存数时，缓存内容会回收或释放，当UI空闲时（无动画或用户操作），会加载缓存到最大缓存数。 取值范围：[minCount, +∞)，小于minCount时按minCount处理。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CacheCountInfo-maxCount: int--><!--Device-CacheCountInfo-maxCount: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minCount

```TypeScript
minCount: int
```

最小缓存数，当实际缓存数小于最小缓存数时，在滚动动画帧间空闲时隙加载缓存。 取值范围：[0, +∞)，小于0时按1处理。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CacheCountInfo-minCount: int--><!--Device-CacheCountInfo-minCount: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

