# HiLog

## Overview

Provides logging functions.<br> For example, you can use these functions to output logs of the specified log type, service domain, log tag, and log level.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 8

## Files

| Name | Description |
| -- | -- |
| [log.h](capi-log-h.md) | Defines the logging functions of the HiLog module.<br> Before outputting logs, you must define the service domain, and log tag, use the function with the specified log type and level, and specify the privacy identifier. <ul><li>Service domain: used to identify the subsystem and module of a service. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF.  <li>Log tag: a string used to identify the class, file, or service.</li>  <li>Log level: <b>DEBUG</b>, <b>INFO</b>, <b>WARN</b>, <b>ERROR</b>, and <b>FATAL</b></li>  <li>Parameter format: a printf format string that starts with a % character, including format specifiers and variable parameters.</li>  <li>Privacy identifier: {public} or {private} added between the % character and the format specifier in<br>each parameter. Note that each parameter has a privacy identifier. If no privacy identifier is added,<br>the parameter is considered to be <b>private</b>.</li></ul> <br>Sample code:<br>Defining the service domain and log tag:<br>    #include <hilog/log.h><br>    #define LOG_DOMAIN 0x0201<br>    #define LOG_TAG "MY_TAG"<br>Outputting logs:<br>    HILOG_WARN({@link LOG_APP}, "Failed to visit %{private}s, reason:%{public}d.", url, errno); Output result: 05-06 15:01:06.870 1051 1051 W 0201/MY_TAG: Failed to visit <private>, reason:503. |
