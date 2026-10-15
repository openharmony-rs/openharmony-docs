# @ohos.systemTime(System Time and Time Zone)

The **systemTime** module provides system time and time zone features. You can use the APIs of this module to set and obtain the system time and time zone.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [systemDateTime](arkts-basicservices-systemdatetime.md)

<!--Device-unnamed-declare namespace systemTime--><!--Device-unnamed-declare namespace systemTime-End-->

**System capability:** SystemCapability.MiscServices.Time

## Modules to Import

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getCurrentTime](arkts-basicservices-systemtime-getcurrenttime-f.md#getcurrenttime1) | Obtains the time elapsed since the Unix epoch. This API uses an asynchronous callback to return the result. |
| [getCurrentTime](arkts-basicservices-systemtime-getcurrenttime-f.md#getcurrenttime2) | Obtains the time elapsed since the Unix epoch. This API uses an asynchronous callback to return the result. |
| [getCurrentTime](arkts-basicservices-systemtime-getcurrenttime-f.md#getcurrenttime3) | Obtains the time elapsed since the Unix epoch. This API uses a promise to return the result. |
| [getDate](arkts-basicservices-systemtime-getdate-f.md#getdate1) | Obtains the current system date. This API uses an asynchronous callback to return the result. |
| [getDate](arkts-basicservices-systemtime-getdate-f.md#getdate2) | Obtains the current system date. This API uses a promise to return the result. |
| [getRealActiveTime](arkts-basicservices-systemtime-getrealactivetime-f.md#getrealactivetime1) | Obtains the time elapsed since system startup, excluding the deep sleep time. This API uses an asynchronous callback to return the result. |
| [getRealActiveTime](arkts-basicservices-systemtime-getrealactivetime-f.md#getrealactivetime2) | Obtains the time elapsed since system startup, excluding the deep sleep time. This API uses an asynchronous callback to return the result. |
| [getRealActiveTime](arkts-basicservices-systemtime-getrealactivetime-f.md#getrealactivetime3) | Obtains the time elapsed since system startup, excluding the deep sleep time. This API uses a promise to return the result. |
| [getRealTime](arkts-basicservices-systemtime-getrealtime-f.md#getrealtime1) | Obtains the time elapsed since system startup, including the deep sleep time. This API uses an asynchronous callback to return the result. |
| [getRealTime](arkts-basicservices-systemtime-getrealtime-f.md#getrealtime2) | Obtains the time elapsed since system startup, including the deep sleep time. This API uses an asynchronous callback to return the result. |
| [getRealTime](arkts-basicservices-systemtime-getrealtime-f.md#getrealtime3) | Obtains the time elapsed since system startup, including the deep sleep time. This API uses a promise to return the result. |
| [getTimezone](arkts-basicservices-systemtime-gettimezone-f.md#gettimezone1) | Obtains the system time zone. This API uses an asynchronous callback to return the result. |
| [getTimezone](arkts-basicservices-systemtime-gettimezone-f.md#gettimezone2) | Obtains the system time zone. This API uses a promise to return the result. |
| [setDate](arkts-basicservices-systemtime-setdate-f.md#setdate1) | Sets the system date. This API uses an asynchronous callback to return the result. |
| [setDate](arkts-basicservices-systemtime-setdate-f.md#setdate2) | Sets the system date. This API uses a promise to return the result. |
| [setTime](arkts-basicservices-systemtime-settime-f.md#settime1) | Sets the system time. This API uses an asynchronous callback to return the result. |
| [setTime](arkts-basicservices-systemtime-settime-f.md#settime2) | Sets the system time. This API uses a promise to return the result. |
| [setTimezone](arkts-basicservices-systemtime-settimezone-f.md#settimezone1) | Sets the system time zone. This API uses an asynchronous callback to return the result. |
| [setTimezone](arkts-basicservices-systemtime-settimezone-f.md#settimezone2) | Sets the system time zone. This API uses a promise to return the result. |
