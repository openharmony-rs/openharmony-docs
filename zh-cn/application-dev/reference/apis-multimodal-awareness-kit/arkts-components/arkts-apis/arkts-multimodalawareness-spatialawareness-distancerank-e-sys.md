# DistanceRank（系统接口）

测距结果的距离挡位，不同的挡位对应不同的距离范围。

@enum { string } 表示测距距离类型

**起始版本：** 23

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## RANK_ULTRA_SHORT_RANGE

```TypeScript
RANK_ULTRA_SHORT_RANGE = 'rankUltraShort'
```

表示超短距。单位：cm，范围：[0:5]。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## RANK_SHORT_RANGE

```TypeScript
RANK_SHORT_RANGE = 'rankShort'
```

表示短距。单位：cm，范围：(5:100]。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## RANK_SHORT_MEDIUM_RANGE

```TypeScript
RANK_SHORT_MEDIUM_RANGE = 'rankMediumShort'
```

表示中短距。单位：cm，范围：(100:500]。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## RANK_MEDIUM_RANGE

```TypeScript
RANK_MEDIUM_RANGE = 'rankMedium'
```

表示中距。单位：cm，范围：(500:1000]。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。
