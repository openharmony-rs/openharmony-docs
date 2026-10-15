# @ohos.systemTime(系统时间、时区)

本模块主要由系统时间和系统时区功能组成。开发者可以设置、获取系统时间及系统时区。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [systemDateTime](arkts-basicservices-systemdatetime.md)

<!--Device-unnamed-declare namespace systemTime--><!--Device-unnamed-declare namespace systemTime-End-->

**系统能力：** SystemCapability.MiscServices.Time

## 导入模块

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCurrentTime](arkts-basicservices-systemtime-getcurrenttime-f.md#getcurrenttime1) | 获取自Unix纪元以来经过的时间，使用callback异步回调。 |
| [getCurrentTime](arkts-basicservices-systemtime-getcurrenttime-f.md#getcurrenttime2) | 获取自Unix纪元以来经过的时间，使用callback异步回调。 |
| [getCurrentTime](arkts-basicservices-systemtime-getcurrenttime-f.md#getcurrenttime3) | 获取自Unix纪元以来经过的时间，使用Promise异步回调。 |
| [getDate](arkts-basicservices-systemtime-getdate-f.md#getdate1) | 获取当前系统日期，使用callback异步回调。 |
| [getDate](arkts-basicservices-systemtime-getdate-f.md#getdate2) | 获取当前系统日期，使用Promise异步回调。 |
| [getRealActiveTime](arkts-basicservices-systemtime-getrealactivetime-f.md#getrealactivetime1) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。 |
| [getRealActiveTime](arkts-basicservices-systemtime-getrealactivetime-f.md#getrealactivetime2) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。 |
| [getRealActiveTime](arkts-basicservices-systemtime-getrealactivetime-f.md#getrealactivetime3) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用Promise异步回调。 |
| [getRealTime](arkts-basicservices-systemtime-getrealtime-f.md#getrealtime1) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。 |
| [getRealTime](arkts-basicservices-systemtime-getrealtime-f.md#getrealtime2) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。 |
| [getRealTime](arkts-basicservices-systemtime-getrealtime-f.md#getrealtime3) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用Promise异步回调。 |
| [getTimezone](arkts-basicservices-systemtime-gettimezone-f.md#gettimezone1) | 获取系统时区，使用callback异步回调。 |
| [getTimezone](arkts-basicservices-systemtime-gettimezone-f.md#gettimezone2) | 获取系统时区，使用Promise异步回调。 |
| [setDate](arkts-basicservices-systemtime-setdate-f.md#setdate1) | 设置系统日期，使用callback异步回调。 |
| [setDate](arkts-basicservices-systemtime-setdate-f.md#setdate2) | 设置系统日期，使用Promise异步回调。 |
| [setTime](arkts-basicservices-systemtime-settime-f.md#settime1) | 设置系统时间，使用callback异步回调。 |
| [setTime](arkts-basicservices-systemtime-settime-f.md#settime2) | 设置系统时间，使用Promise异步回调。 |
| [setTimezone](arkts-basicservices-systemtime-settimezone-f.md#settimezone1) | 设置系统时区，使用callback异步回调。 |
| [setTimezone](arkts-basicservices-systemtime-settimezone-f.md#settimezone2) | 使用Promise异步回调设置系统时区。 |
