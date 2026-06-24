# @ohos.systemDateTime

本模块主要由系统时间和系统时区功能组成。开发者可以获取系统时间及系统时区。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.Time

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getAutoTimeStatus](arkts-basicservices-systemdatetime-getautotimestatus-f.md#getAutoTimeStatus-1) | 获取自动设置时间开关状态，使用同步方式。<br/> |
| <!--DelRow-->[getCurrentTime](arkts-basicservices-systemdatetime-getcurrenttime-f.md#getCurrentTime-1) | 获取自Unix纪元以来经过的时间，使用callback异步回调。<br/> |
| <!--DelRow-->[getCurrentTime](arkts-basicservices-systemdatetime-getcurrenttime-f.md#getCurrentTime-2) | 获取自Unix纪元以来经过的时间，使用callback异步回调。<br/> |
| <!--DelRow-->[getCurrentTime](arkts-basicservices-systemdatetime-getcurrenttime-f.md#getCurrentTime-3) | 获取自Unix纪元以来经过的时间，使用Promise异步回调。<br/> |
| <!--DelRow-->[getDate](arkts-basicservices-systemdatetime-getdate-f.md#getDate-1) | 获取当前系统日期，使用callback异步回调。<br/> |
| <!--DelRow-->[getDate](arkts-basicservices-systemdatetime-getdate-f.md#getDate-2) | 获取当前系统日期，使用Promise异步回调。<br/> |
| <!--DelRow-->[getNtpTime](arkts-basicservices-systemdatetime-getntptime-f-sys.md#getNtpTime-1) | 使用同步方式获取基于上次更新的NTP时间所计算出的真实时间。<br/> |
| <!--DelRow-->[getRealActiveTime](arkts-basicservices-systemdatetime-getrealactivetime-f.md#getRealActiveTime-1) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。<br/> |
| <!--DelRow-->[getRealActiveTime](arkts-basicservices-systemdatetime-getrealactivetime-f.md#getRealActiveTime-2) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。<br/> |
| <!--DelRow-->[getRealActiveTime](arkts-basicservices-systemdatetime-getrealactivetime-f.md#getRealActiveTime-3) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用Promise异步回调。<br/> |
| <!--DelRow-->[getRealTime](arkts-basicservices-systemdatetime-getrealtime-f.md#getRealTime-1) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。<br/> |
| <!--DelRow-->[getRealTime](arkts-basicservices-systemdatetime-getrealtime-f.md#getRealTime-2) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。<br/> |
| <!--DelRow-->[getRealTime](arkts-basicservices-systemdatetime-getrealtime-f.md#getRealTime-3) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用Promise异步回调。<br/> |
| <!--DelRow-->[getTime](arkts-basicservices-systemdatetime-gettime-f.md#getTime-1) | 使用同步方式获取自Unix纪元以来到当前系统时间所经过的时间。<br/> |
| <!--DelRow-->[getTimezone](arkts-basicservices-systemdatetime-gettimezone-f.md#getTimezone-1) | 获取系统时区，使用callback异步回调。<br/> |
| <!--DelRow-->[getTimezone](arkts-basicservices-systemdatetime-gettimezone-f.md#getTimezone-2) | 获取系统时区，使用Promise异步回调。<br/> |
| <!--DelRow-->[getTimezoneSync](arkts-basicservices-systemdatetime-gettimezonesync-f.md#getTimezoneSync-1) | 获取系统时区，使用同步方式。<br/> |
| <!--DelRow-->[getUptime](arkts-basicservices-systemdatetime-getuptime-f.md#getUptime-1) | 使用同步方式获取自系统启动以来经过的时间。<br/> |
| <!--DelRow-->[setAutoTimeStatus](arkts-basicservices-systemdatetime-setautotimestatus-f-sys.md#setAutoTimeStatus-1) | 设置自动设置时间开关状态，使用Promise异步回调。<br/> |
| <!--DelRow-->[setDate](arkts-basicservices-systemdatetime-setdate-f-sys.md#setDate-1) | 设置系统日期，使用callback异步回调。<br/> |
| <!--DelRow-->[setDate](arkts-basicservices-systemdatetime-setdate-f-sys.md#setDate-2) | 设置系统日期，使用Promise异步回调。<br/> |
| <!--DelRow-->[setTime](arkts-basicservices-systemdatetime-settime-f-sys.md#setTime-1) | 设置系统时间，使用callback异步回调。<br/> |
| <!--DelRow-->[setTime](arkts-basicservices-systemdatetime-settime-f-sys.md#setTime-2) | 设置系统时间，使用Promise异步回调。<br/> |
| <!--DelRow-->[setTimezone](arkts-basicservices-systemdatetime-settimezone-f-sys.md#setTimezone-1) | 设置系统时区，使用callback异步回调。<br/> |
| <!--DelRow-->[setTimezone](arkts-basicservices-systemdatetime-settimezone-f-sys.md#setTimezone-2) | 设置系统时区，使用Promise异步回调。<br/> |
| <!--DelRow-->[updateNtpTime](arkts-basicservices-systemdatetime-updatentptime-f-sys.md#updateNtpTime-1) | 使用异步方式从NTP服务器更新NTP时间。该方法一小时内只会从NTP服务器更新一次NTP时间。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[TimeType](arkts-basicservices-systemdatetime-timetype-e.md) | 定义获取时间的枚举类型。<br/> |

