# ZoneRules

提供查询时区跳变规则的能力。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class ZoneRules--><!--Device-i18n-export class ZoneRules-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
```

## nextTransition

```TypeScript
public nextTransition(date?: double): ZoneOffsetTransition
```

获取指定时间的下一个时区跳变对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ZoneRules-public nextTransition(date?: double): ZoneOffsetTransition--><!--Device-ZoneRules-public nextTransition(date?: double): ZoneOffsetTransition-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | double | 否 | 从1970年1月1日0时0分0秒到指定时间之间的毫秒数。 <br>默认值：系统时间。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ZoneOffsetTransition](arkts-na-i18n-zoneoffsettransition-c.md) | 时区跳变对象。 |

