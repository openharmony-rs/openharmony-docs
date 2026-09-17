# PerfMetric

APP_START_COMPLETE_TIME**):  
> - Application startup latency data is subject to the system logging and reporting and may be different from what end users perceive. The start time is when the tap event is reported, the end time of the response latency is when the first frame is displayed on the screen after the tap, and the end time of the completion latency is when the first frame is displayed on the screen after the application is started.
> - Application startup latency data can be collected in the following scenarios: tapping an application icon on the home screen, tapping an application icon on the dock bar, and tapping an application icon in the application center.
> - During a test, only the first startup latency of the specified application is collected.
> 4. Description of collecting the page switching latency data (**PAGE_SWITCH_COMPLETE_TIME**):
> - Page switching latency calculation is subject to the system logging and reporting and may be different from what end users perceive. The start time is when the tap event is reported, and the end time is when the first frame is displayed on the screen after the page switching.
> - Page switching latency data can be collected in the **Router** and **Navigation** components.
> - During a test, only the first page switching latency in the specified application is collected.
> 5. Description of collecting the list scrolling frame rate (**LIST_SWIPE_FPS**):
> - **LIST_SWIPE_FPS**: The number of frames rendered and updated on the screen per second when the list is scrolled.
> - Supported scenarios: list scrolling of the **List**, **Grid**, **Scroll**, and **WaterFlow** components in the ArkUI subsystem.
> - During a test, only the first list scrolling frame rate in the specified application is collected.

@enum { int }

**Since:** 20

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## DURATION

```TypeScript
DURATION = 0
```

Execution duration of a code segment, in milliseconds.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## CPU_LOAD

```TypeScript
CPU_LOAD = 1
```

CPU load of the application process, in percentage.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## CPU_USAGE

```TypeScript
CPU_USAGE = 2
```

CPU usage of the application process, in percentage.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## MEMORY_RSS

```TypeScript
MEMORY_RSS = 3
```

Physical memory (including the shared library) occupied by the application process when a code segment is executed, in KB.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## MEMORY_PSS

```TypeScript
MEMORY_PSS = 4
```

Physical memory (the proportionally allocated memory occupied by shared libraries) occupied by the application process when a code segment is executed, in KB.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## APP_START_RESPONSE_TIME

```TypeScript
APP_START_RESPONSE_TIME = 5
```

Response latency of application startup, in milliseconds.

Marks: 1) Delay calculation is restricted by system dotting reporting. The start time is the time when the click event is reported, and the end time of the response delay is the time when the system responds to the first frame after the click. It is different from the end-to-end user-perceived delay. 2) Application start delay can be collected in the following scenarios: clicking the application icon on the desktop; clicking the application on the Multi-Task Center; clicking the application icon on the Dock; clicking the application icon on the application center. 3) This metric does not support the test of current application. 4) During the test, only the data of the first startup of the specified application can be collected.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## APP_START_COMPLETE_TIME

```TypeScript
APP_START_COMPLETE_TIME = 6
```

Completion latency of application startup, in milliseconds.

Marks: 1) Delay calculation is restricted by system dotting reporting. The start time is the time when the click event is reported, and the end time of the completion delay is the time when the first frame is displayed after the application is started. It is different from the end-to-end user-perceived delay. 2) Application start delay can be collected in the following scenarios: clicking the application icon on the desktop; clicking the application on the Multi-Task Center; clicking the application icon on the Dock; clicking the application icon on the application center. 3) This metric does not support the test of current application. 4) During the test, only the data of the first start of specified application can be collected.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## PAGE_SWITCH_COMPLETE_TIME

```TypeScript
PAGE_SWITCH_COMPLETE_TIME = 7
```

Completion latency of page switching in an application, in milliseconds.

Marks: 1) Delay calculation is restricted by system dotting and reporting. The start time is the time when the click event is reported, and the end time of the completion delay is the time when the first frame is displayed after page is switched. It is different from the end-to-end user-perceived delay. 2) Page switching delay can be collected in the page switchover scenario of the Router or Navigation component. 3) During the test, only the data of the first page switching in specified application can be collected.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## LIST_SWIPE_FPS

```TypeScript
LIST_SWIPE_FPS = 8
```

List scrolling frame rate in an application, in frames per second (fps).

Mark: 1) List sliding frame rate: refers to the frequency at which the screen can be refreshed when the list is sliding. Only the sliding frame rate of the List, grid, scroll, and waterflow scroll components of ArkUI subsystems can be collected. 2) During the test, only the data of the first sliding of the component in specified application can be collected.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.
