# HiDebug接口使用示例(ArkTS)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

HiDebug ArkTS接口功能独立，需要获取调试信息时直接调用。具体调用方式请参考[API参考文档](../reference/apis-performance-analysis-kit/js-apis-hidebug.md)中的示例。

## 开发示例

本文以获取系统CPU使用率为例，展示如何调用HiDebug ArkTS接口。

1. 使用DevEco Studio新建工程，选择“Empty Ability”。

2. 在Project窗口单击entry > src > main > ets > pages，打开并编辑Index.ets文件：
   导入所需依赖：
   <!-- @[TestHidebugArk_Import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/ets/pages/Index.ets) -->
   定义测试方法：
   <!-- @[TestHidebugArk_Function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/ets/pages/Index.ets) -->

   添加按钮以触发接口调用：
   <!-- @[TestHidebugArk_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/ets/pages/Index.ets) -->

3. 点击运行，然后在设备上点击“testHiDebugArk”按钮，触发接口调用。

4. 若接口调用存在日志输出，在DevEco Studio的底部，切换到“Log”窗口，即可查看相关日志。

   ```Text
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     getSystemCpuUsage: 0.2878989952876323
   ```
