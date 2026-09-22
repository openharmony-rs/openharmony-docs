# HiLog

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @suxunquan-->
<!--Designer: @milkbread123-->
<!--Tester: @yufeifei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=3fb53ed46665e1d6717965d283cf425836c325fb translatedAt=2026-09-21T02:35:29.119Z pushedAt=2026-09-22T01:29:30.391Z -->

## Overview

The HiLog module is a C/C++ logging module provided by OpenHarmony. It is used to output structured log information while an application is running. You can use these APIs to implement logging-related functions. When outputting logs, you can specify the log type, business domain, log TAG, and log level.

Use scenario: This module is used when developers need to record runtime logs for problem diagnosis, process tracking, and behavior analysis during application development. DEBUG-level logs are used to record debugging information and track service processes and running status. INFO-level logs are used to record key service node information in abnormal cases, such as no network signal or login failure. When an exception or error occurs, WARN-, ERROR-, and FATAL-level logs are used to record fault information for quick identification of the root cause.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 8

## Files

| Name| Description|
| -- | -- |
| [log.h](capi-log-h.md) | Defines the logging APIs of the HiLog module, through which log printing functions are implemented. When outputting logs, users first define the business domain and log TAG to which the logs belong, then select the corresponding API based on the log type and log level, and specify the privacy parameter identifier to output the log content.<br> Business domain: specifies the business domain to which the logs belong. It is user-defined and used to identify the subsystem and module of a service. It is a hexadecimal integer ranging from 0x0 to 0xFFFF. If the value is out of range, the logging API does not output log content.<br> Log TAG: a string constant used to identify the class or service where the call is made. A TAG supports a maximum of 31 bytes and is truncated if it exceeds the limit. Chinese characters are not recommended to avoid garbled characters and alignment issues.<br> Log level: DEBUG, INFO, WARN, ERROR, and FATAL. For details about each level, see [log.h](capi-log-h.md).<br> Parameter format: printf-like % format, including a format string (including parameter type identifiers) and variable arguments.<br> Privacy parameter identifier: in the format string, `{public}` or `{private}` can be optionally added after the % symbol and before the type for each parameter. If no privacy identifier is specified for a parameter, it defaults to private. |
