# BadgeParamWithNumber

BadgeParamWithNumber继承自[BadgeParam](arkts-na-badge-badgeparam-i.md#BadgeParam)，具有BadgeParam的全部属性。

**继承/实现关系：** BadgeParamWithNumber extends [BadgeParam](arkts-na-badge-badgeparam-i.md#BadgeParam)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface BadgeParamWithNumber--><!--Device-unnamed-export declare interface BadgeParamWithNumber-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: int
```

设置提醒消息数。 **说明：** 当该值小于等于0且小于maxCount时不显示信息标记。 取值应为[-2147483648,2147483647]内的整数。取值约束：超出范围时会加上或减去4294967296，使得值仍在范围内，非整数时会舍去小数部分取整数部分，如5.5取5。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BadgeParamWithNumber-count: int--><!--Device-BadgeParamWithNumber-count: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxCount

```TypeScript
maxCount?: int
```

最大消息数，超过最大消息时仅显示maxCount+，如maxCount是99时，显示`99+`。 取值范围：[-2147483648, 2147483647]。取值约束：超出范围时会加上或减去4294967296，使得值仍在范围内，非整数时会舍去小数部分取整数部分，如5.5取5。。默认值：99。

**类型：** int

**默认值：** 99

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BadgeParamWithNumber-maxCount?: int--><!--Device-BadgeParamWithNumber-maxCount?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

