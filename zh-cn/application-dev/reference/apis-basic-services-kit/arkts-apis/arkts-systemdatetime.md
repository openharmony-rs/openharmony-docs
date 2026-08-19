# @ohos.systemDateTime

本模块主要由系统时间和系统时区功能组成。开发者可以获取系统时间及系统时区。

**起始版本：** 23

<!--Device-unnamed-declare namespace systemDateTime--><!--Device-unnamed-declare namespace systemDateTime-End-->

**系统能力：** SystemCapability.MiscServices.Time

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAutoTimeStatus](arkts-basicservices-systemdatetime-getautotimestatus-f.md) | 获取自动设置时间开关状态，使用同步方式。 |
| [getCurrentTime](arkts-basicservices-systemdatetime-getcurrenttime-f.md) | 获取自Unix纪元以来经过的时间，使用callback异步回调。 |
| [getCurrentTime](arkts-basicservices-systemdatetime-getcurrenttime-f.md) | 获取自Unix纪元以来经过的时间，使用callback异步回调。 |
| [getCurrentTime](arkts-basicservices-systemdatetime-getcurrenttime-f.md) | 获取自Unix纪元以来经过的时间，使用Promise异步回调。 |
| [getDate](arkts-basicservices-systemdatetime-getdate-f.md) | 获取当前系统日期，使用callback异步回调。 |
| [getDate](arkts-basicservices-systemdatetime-getdate-f.md) | 获取当前系统日期，使用Promise异步回调。 |
| [getRealActiveTime](arkts-basicservices-systemdatetime-getrealactivetime-f.md) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。 |
| [getRealActiveTime](arkts-basicservices-systemdatetime-getrealactivetime-f.md) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。 |
| [getRealActiveTime](arkts-basicservices-systemdatetime-getrealactivetime-f.md) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用Promise异步回调。 |
| [getRealTime](arkts-basicservices-systemdatetime-getrealtime-f.md) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。 |
| [getRealTime](arkts-basicservices-systemdatetime-getrealtime-f.md) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。 |
| [getRealTime](arkts-basicservices-systemdatetime-getrealtime-f.md) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用Promise异步回调。 |
| [getTime](arkts-basicservices-systemdatetime-gettime-f.md) | 使用同步方式获取自Unix纪元以来到当前系统时间所经过的时间。 |
| [getTimezone](arkts-basicservices-systemdatetime-gettimezone-f.md) | 获取系统时区，使用callback异步回调。 |
| [getTimezone](arkts-basicservices-systemdatetime-gettimezone-f.md) | 获取系统时区，使用Promise异步回调。 |
| [getTimezoneSync](arkts-basicservices-systemdatetime-gettimezonesync-f.md) | 获取系统时区，使用同步方式。 |
| [getUptime](arkts-basicservices-systemdatetime-getuptime-f.md) | 使用同步方式获取自系统启动以来经过的时间。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getNtpTime](arkts-basicservices-systemdatetime-getntptime-f-sys.md) | 使用同步方式获取基于上次更新的NTP时间所计算出的真实时间。 |
| [setAutoTimeStatus](arkts-basicservices-systemdatetime-setautotimestatus-f-sys.md) | 设置自动设置时间开关状态，使用Promise异步回调。 |
| [setDate](arkts-basicservices-systemdatetime-setdate-f-sys.md) | 设置系统日期，使用callback异步回调。 |
| [setDate](arkts-basicservices-systemdatetime-setdate-f-sys.md) | 设置系统日期，使用Promise异步回调。 |
| [setTime](arkts-basicservices-systemdatetime-settime-f-sys.md) | 设置系统时间，使用callback异步回调。 |
| [setTime](arkts-basicservices-systemdatetime-settime-f-sys.md) | 设置系统时间，使用Promise异步回调。 |
| [setTimezone](arkts-basicservices-systemdatetime-settimezone-f-sys.md) | 设置系统时区，使用callback异步回调。 |
| [setTimezone](arkts-basicservices-systemdatetime-settimezone-f-sys.md) | 设置系统时区，使用Promise异步回调。 |
| [updateNtpTime](arkts-basicservices-systemdatetime-updatentptime-f-sys.md) | 使用异步方式从NTP服务器更新NTP时间。该方法一小时内只会从NTP服务器更新一次NTP时间。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TimeType](arkts-basicservices-systemdatetime-timetype-e.md) | 定义获取时间的枚举类型。 |

