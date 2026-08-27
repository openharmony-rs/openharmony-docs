# @ohos.systemTime(系统时间、时区)

本模块主要由系统时间和系统时区功能组成。开发者可以设置、获取系统时间及系统时区。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [systemDateTime](arkts-systemdatetime.md)

**系统能力：** SystemCapability.MiscServices.Time

## 导入模块

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCurrentTime(系统时间、时区)](arkts-basicservices-systemtime-getcurrenttime-f.md) | 获取自Unix纪元以来经过的时间，使用callback异步回调。 |
| [getCurrentTime(系统时间、时区)](arkts-basicservices-systemtime-getcurrenttime-f.md) | 获取自Unix纪元以来经过的时间，使用callback异步回调。 |
| [getCurrentTime(系统时间、时区)](arkts-basicservices-systemtime-getcurrenttime-f.md) | 获取自Unix纪元以来经过的时间，使用Promise异步回调。 |
| [getDate(系统时间、时区)](arkts-basicservices-systemtime-getdate-f.md) | 获取当前系统日期，使用callback异步回调。 |
| [getDate(系统时间、时区)](arkts-basicservices-systemtime-getdate-f.md) | 获取当前系统日期，使用Promise异步回调。 |
| [getRealActiveTime(系统时间、时区)](arkts-basicservices-systemtime-getrealactivetime-f.md) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。 |
| [getRealActiveTime(系统时间、时区)](arkts-basicservices-systemtime-getrealactivetime-f.md) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用callback异步回调。 |
| [getRealActiveTime(系统时间、时区)](arkts-basicservices-systemtime-getrealactivetime-f.md) | 获取自系统启动以来经过的时间，不包括深度睡眠时间，使用Promise异步回调。 |
| [getRealTime(系统时间、时区)](arkts-basicservices-systemtime-getrealtime-f.md) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。 |
| [getRealTime(系统时间、时区)](arkts-basicservices-systemtime-getrealtime-f.md) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。 |
| [getRealTime(系统时间、时区)](arkts-basicservices-systemtime-getrealtime-f.md) | 获取自系统启动以来经过的时间，包括深度睡眠时间，使用Promise异步回调。 |
| [getTimezone(系统时间、时区)](arkts-basicservices-systemtime-gettimezone-f.md) | 获取系统时区，使用callback异步回调。 |
| [getTimezone(系统时间、时区)](arkts-basicservices-systemtime-gettimezone-f.md) | 获取系统时区，使用Promise异步回调。 |
| [setDate(系统时间、时区)](arkts-basicservices-systemtime-setdate-f.md) | 设置系统日期，使用callback异步回调。 |
| [setDate(系统时间、时区)](arkts-basicservices-systemtime-setdate-f.md) | 设置系统日期，使用Promise异步回调。 |
| [setTime(系统时间、时区)](arkts-basicservices-systemtime-settime-f.md) | 设置系统时间，使用callback异步回调。 |
| [setTime(系统时间、时区)](arkts-basicservices-systemtime-settime-f.md) | 设置系统时间，使用Promise异步回调。 |
| [setTimezone(系统时间、时区)](arkts-basicservices-systemtime-settimezone-f.md) | 设置系统时区，使用callback异步回调。 |
| [setTimezone(系统时间、时区)](arkts-basicservices-systemtime-settimezone-f.md) | 使用Promise异步回调设置系统时区。 |
