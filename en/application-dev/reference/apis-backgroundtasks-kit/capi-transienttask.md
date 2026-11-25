# TransientTask

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=531e9eb172de84358a19bcfc47d3cdd7f3217a90 translatedAt=2026-09-15T12:47:14.505Z pushedAt=2026-09-17T02:23:52.595Z -->

## Overview

This module provides C APIs for transient tasks, such as requesting, querying, and canceling transient tasks. This method is used to perform time-consuming operations in a short period of time after an app enters the background, such as status saving and message sending.

**Since**: 13
## Files

| Name| Description|
| -- | -- |
| [transient_task_api.h](capi-transient-task-api-h.md) | Declares the APIs for requesting, querying, and canceling transient tasks.|
| [transient_task_type.h](capi-transient-task-type-h.md) | Declares the error codes and structs of a transient task.|
