# Overview

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @mzyan-->
<!--Designer: @liyueric-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

Performance Analysis Kit provides comprehensive capabilities such as fault detection and exception handling. As faults vary in causes and symptoms, application stability deteriorates, affecting application development efficiency, delivery costs, and user experience. Therefore, you need to improve quality by designing a fault management system, which includes the detection, analysis, locating and rectification of faults, and quality measurement.

To help you quickly locate and rectify application faults, this topic describes the detection principles, log specifications, log obtaining methods, and restrictions of faults such as process crash, address out-of-bounds, application freeze, resource leak, task execution timeout, and application termination.

> **NOTE**
>
> The following faults cause unexpected application or system process exit:
>
> 1. Native code does not process crash exception signals, and C++ crash logs are generated. For details, see [Cpp Crash (Process Crash) Detection](cppcrash-guidelines.md).
>
> 2. JS/ArkTS code does not process exceptions, and JS crash logs are generated. For details, see [JS Crash (Process Crash) Detection](jscrash-guidelines.md).
>
> 3. The application is freezing and AppFreeze logs are generated. For details, see [Application Freeze Detection](appfreeze-guidelines.md).
>
> 4. The application process is terminated by the system, and the application exits unexpectedly. For details, see [Application Killed Detection](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/appkilled-guidelines).
