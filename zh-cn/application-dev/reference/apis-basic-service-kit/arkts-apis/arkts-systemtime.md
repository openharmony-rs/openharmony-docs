# @ohos.systemTime

本模块主要由系统时间和系统时区功能组成。开发者可以设置、获取系统时间及系统时区。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [systemDateTime:systemDateTime](arkts-systemdatetime.md)

<!--Device-unnamed-declare namespace systemTime--><!--Device-unnamed-declare namespace systemTime-End-->

**系统能力：** SystemCapability.MiscServices.Time

## 导入模块

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getCurrentTime](arkts-basicservices-systemtime-getcurrenttime-f.md#getcurrenttime-1) | 获取自Unix纪元以来经过的时间，使用callback异步回调。 |
| [getCurrentTime](arkts-basicservices-systemtime-getcurrenttime-f.md#getcurrenttime-2) | 获取自Unix纪元以来经过的时间，使用callback异步回调。 |
| [getCurrentTime](arkts-basicservices-systemtime-getcurrenttime-f.md#getcurrenttime-3) | 获取自Unix纪元以来经过的时间，使用Promise异步回调。 |
| [getDate](arkts-basicservices-systemtime-getdate-f.md#getdate-1) | 获取当前系统日期，使用callback异步回调。 |
| [getDate](arkts-basicservices-systemtime-getdate-f.md#getdate-2) | 获取当前系统日期，使用Promise异步回调。 |
| [getRealActiveTime](arkts-basicservices-systemtime-getrealactivetime-f.md#getrealactivetime-1) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。 |
| [getRealActiveTime](arkts-basicservices-systemtime-getrealactivetime-f.md#getrealactivetime-2) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。 |
| [getRealActiveTime](arkts-basicservices-systemtime-getrealactivetime-f.md#getrealactivetime-3) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用Promise异步回调。 |
| [getRealTime](arkts-basicservices-systemtime-getrealtime-f.md#getrealtime-1) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。 |
| [getRealTime](arkts-basicservices-systemtime-getrealtime-f.md#getrealtime-2) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。 |
| [getRealTime](arkts-basicservices-systemtime-getrealtime-f.md#getrealtime-3) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用Promise异步回调。 |
| [getTimezone](arkts-basicservices-systemtime-gettimezone-f.md#gettimezone-1) | 获取系统时区，使用callback异步回调。 |
| [getTimezone](arkts-basicservices-systemtime-gettimezone-f.md#gettimezone-2) | 获取系统时区，使用Promise异步回调。 |
| [setDate](arkts-basicservices-systemtime-setdate-f.md#setdate-1) | 设置系统日期，使用callback异步回调。 |
| [setDate](arkts-basicservices-systemtime-setdate-f.md#setdate-2) | 设置系统日期，使用Promise异步回调。 |
| [setTime](arkts-basicservices-systemtime-settime-f.md#settime-1) | 设置系统时间，使用callback异步回调。 |
| [setTime](arkts-basicservices-systemtime-settime-f.md#settime-2) | 设置系统时间，使用Promise异步回调。 |
| [setTimezone](arkts-basicservices-systemtime-settimezone-f.md#settimezone-1) | 设置系统时区，使用callback异步回调。 |
| [setTimezone](arkts-basicservices-systemtime-settimezone-f.md#settimezone-2) | 使用Promise异步回调设置系统时区。 |
<!--DelEnd-->

