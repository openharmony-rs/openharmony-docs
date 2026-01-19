# About This Kit
<!--Kit: Test Kit-->
<!--Subsystem: Test-->
<!--Owner: @inter515-->
<!--Designer: @inter515-->
<!--Tester: @laonie666-->
<!--Adviser: @Brilliantry_Rui-->

Test Kit provides automated test frameworks that support unit, UI, and performance tests. It enables you to write and execute automated test scripts in ArkTS and assess the effectiveness of your features based on test results. Since API version 20, the performance test capability is supported.

- Unit test capability: provides basic APIs and running mechanisms for automated tests. For details, see <!--RP1-->[JsUnit User Guide](unittest-guidelines.md)<!--RP1-->. The main features are as follows:
  - APIs for defining automated test suites and cases.
  - Assertion APIs that can be flexibly integrated into your test scripts and support multiple assertion modes to verify that test cases meet expected behavior.
  - APIs for executing preset and clear actions at both test suite and test case levels.
  - Multiple test case execution modes, including specified test case execution, random execution, and stress execution.
- UI test capability: provides automated UI test features. UI test scripts are developed based on JSUnit. For details, see <!--RP2-->[UITest User Guide](uitest-guidelines.md)<!--RP2End-->. The main features are as follows:
  - APIs for searching for components in multiple modes, for example, by component attribute or relative position.
  - APIs for simulating UI operations, such as tapping, double-tapping, swiping, and the two-finger pinch gesture, as well as operations on external devices such as the mouse and keyboard.
  - APIs for simulating window operations, such as resizing and moving the window.
  - Shell commands for simulating UI operations, such as tapping, double-tapping, and swiping.
  - Capabilities of listening for system dialog boxes and toasts, and obtaining prompt messages.
- Performance test capability: provides automated white-box performance test features. Performance test scripts are developed based on JSUnit. For details, see <!--RP3-->[PerfTest User Guide](perftest-guideline.md)<!--RP3End-->. The main features are as follows:
  - Basic performance data collection during the execution of a specified code segment, including the execution duration, CPU usage, and memory usage.
  - Application scenario-based performance data collection, including the application launch latency, page switching latency, and list scrolling frame rate.
<!--Del-->
In addition, Test Kit provides the following command line tools:

- SmartPerf: monitors performance and power consumption metrics, including FPS, CPU, GPU, RAM, and Temp. It provides Device-hap and Device-daemon. For details, see [SmartPerf User Guide](smartperf-guidelines.md).
- wukong: supports random event injection, component injection, exception capture, report generation, and data traversal screenshot of abilities. For details, see [wukong User Guide](wukong-guidelines.md).
<!--DelEnd-->
