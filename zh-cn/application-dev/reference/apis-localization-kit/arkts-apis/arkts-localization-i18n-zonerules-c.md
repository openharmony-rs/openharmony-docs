# ZoneRules

提供查询时区跳变规则的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-i18n-export class ZoneRules--><!--Device-i18n-export class ZoneRules-End-->

**系统能力：** SystemCapability.Global.I18n

## nextTransition

```TypeScript
public nextTransition(date?: double): ZoneOffsetTransition
```

获取指定时间的下一个时区跳变对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ZoneRules-public nextTransition(date?: double): ZoneOffsetTransition--><!--Device-ZoneRules-public nextTransition(date?: double): ZoneOffsetTransition-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | double | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ZoneOffsetTransition](arkts-localization-i18n-zoneoffsettransition-c.md) | 时区跳变对象。 |

