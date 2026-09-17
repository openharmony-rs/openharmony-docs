# @ohos.test.PerfTest

PerfTest provides white-box performance test capabilities in test scenarios. It can automatically execute tests on
 specified code segments or scenarios and collect performance data such as time required, CPU usage, memory usage,
 latency, and frame rate.

> **NOTE**
 > - The initial APIs of this module are supported since API version 20.
 Newly added APIs will be marked with a superscript to indicate their earliest API version.
 > - The APIs of this module can be used only in <!--RP1-->[JsUnit](../../../application-test/unittest-guidelines.md)<!--RP1End-->.
 > - The APIs of this module do not support concurrent calls.
 > - The APIs of this module are applicable to phones, tablets, PCs/2-in-1 devices, smart TVs, and head units.



## Modules to Import

```TypeScript
import {PerfMetric, PerfTestStrategy, PerfMeasureResult, PerfTest} from '@kit.TestKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [PerfTest](arkts-test-test-perftest-perftest-c.md) | Represents the general entry of the white-box performance test framework. It provides capabilities such as test task creation, test code segment execution, data collection, and measurement result obtaining. |

### Interfaces

| Name | Description |
| --- | --- |
| [PerfMeasureResult](arkts-test-test-perftest-perfmeasureresult-i.md) | Represents the measurement result data corresponding to the performance metric. |
| [PerfTestStrategy](arkts-test-test-perftest-perfteststrategy-i.md) | Represents the performance test strategy. |

### Enums

| Name | Description |
| --- | --- |
| [PerfMetric](arkts-test-test-perftest-perfmetric-e.md) | APP_START_COMPLETE_TIME**):  > - Application startup latency data is subject to the system logging and reporting and may be different from what end users perceive. The start time is when the tap event is reported, the end time of the response latency is when the first frame is displayed on the screen after the tap, and the end time of the completion latency is when the first frame is displayed on the screen after the application is started. > - Application startup latency data can be collected in the following scenarios: tapping an application icon on the home screen, tapping an application icon on the dock bar, and tapping an application icon in the application center. > - During a test, only the first startup latency of the specified application is collected. > 4. Description of collecting the page switching latency data (**PAGE_SWITCH_COMPLETE_TIME**): > - Page switching latency calculation is subject to the system logging and reporting and may be different from what end users perceive. The start time is when the tap event is reported, and the end time is when the first frame is displayed on the screen after the page switching. > - Page switching latency data can be collected in the **Router** and **Navigation** components. > - During a test, only the first page switching latency in the specified application is collected. > 5. Description of collecting the list scrolling frame rate (**LIST_SWIPE_FPS**): > - **LIST_SWIPE_FPS**: The number of frames rendered and updated on the screen per second when the list is scrolled. > - Supported scenarios: list scrolling of the **List**, **Grid**, **Scroll**, and **WaterFlow** components in the ArkUI subsystem. > - During a test, only the first list scrolling frame rate in the specified application is collected. |
