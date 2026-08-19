# HolidayManager

提供解析节假日数据的能力，包括节假日判断和指定年份节假日列表获取等。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class HolidayManager--><!--Device-i18n-export class HolidayManager-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(icsPath: String)
```

创建HolidayManager对象，用于解析节假日数据。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-HolidayManager-constructor(icsPath: String)--><!--Device-HolidayManager-constructor(icsPath: String)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icsPath | String | 是 | 在设备上有应用读取权限的iCalendar格式的ics文件路径。iCalendar格式是一种标准的互联网日历格式，用于存储日历数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## getHolidayInfoItemArray

```TypeScript
getHolidayInfoItemArray(year?: int): Array<HolidayInfoItem>
```

获取指定年的节假日信息列表。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-HolidayManager-getHolidayInfoItemArray(year?: int): Array<HolidayInfoItem>--><!--Device-HolidayManager-getHolidayInfoItemArray(year?: int): Array<HolidayInfoItem>-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| year | int | 否 | 年，例如2023。 <br>默认值：当前年份。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[HolidayInfoItem](arkts-na-i18n-holidayinfoitem-i.md)&gt; | 返回节假日信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## isHoliday

```TypeScript
isHoliday(date?: Date): boolean
```

判断指定的日期是否是节假日。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-HolidayManager-isHoliday(date?: Date): boolean--><!--Device-HolidayManager-isHoliday(date?: Date): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 否 | 时间日期。 <br>**说明：** <br>月份从0开始计数，0表示一月。 <br>默认值：当前日期。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示指定的日期是节假日，false表示指定的日期不是节假日。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

