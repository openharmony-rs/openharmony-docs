# ZoneOffsetTransition

提供解析时区跳变规则的能力。

**起始版本：** 20

<!--Device-i18n-export class ZoneOffsetTransition--><!--Device-i18n-export class ZoneOffsetTransition-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getMilliseconds

```TypeScript
public getMilliseconds(): number
```

获取时区跳变点的时间戳。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ZoneOffsetTransition-public getMilliseconds(): double--><!--Device-ZoneOffsetTransition-public getMilliseconds(): double-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 从1970年1月1日0时0分0秒到时区跳变点之间的毫秒数，例如：1762074000000，单位为毫秒（ms）。如果当前时区[原始偏移量](arkts-localization-i18n-timezone-c.md#getrawoffset)保持不变并且不使用夏令时，则返回0。 |

## getOffsetAfter

```TypeScript
public getOffsetAfter(): number
```

获取时区跳变后的偏移量。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ZoneOffsetTransition-public getOffsetAfter(): int--><!--Device-ZoneOffsetTransition-public getOffsetAfter(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 时区跳变后的偏移量，表示跳变后的时间相对于标准时间（协调世界时UTC）的时间差，单位为毫秒（ms）。例如：-28800000表示跳变后的时间比标准时间慢28800000毫秒（8小时）。 |

## getOffsetBefore

```TypeScript
public getOffsetBefore(): number
```

获取时区跳变前的偏移量。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ZoneOffsetTransition-public getOffsetBefore(): int--><!--Device-ZoneOffsetTransition-public getOffsetBefore(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 时区跳变前的偏移量，表示跳变前的时间相对于标准时间（协调世界时UTC）的时间差，单位为毫秒（ms）。例如：-25200000表示跳变前的时间比标准时间慢25200000毫秒（7小时）。 |

