# getTimeZone

## getTimeZone

```TypeScript
export function getTimeZone(zoneID?: string): TimeZone
```

获取时区ID对应的时区对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getTimeZone(zoneID?: string): TimeZone--><!--Device-i18n-export function getTimeZone(zoneID?: string): TimeZone-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| zoneID | string | 否 | 时区ID。默认值：系统时区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TimeZone](arkts-localization-i18n-timezone-c.md) | 时区ID对应的时区对象。 |

