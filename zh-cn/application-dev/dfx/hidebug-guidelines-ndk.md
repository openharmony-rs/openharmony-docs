# HiDebug接口使用示例(C/C++)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

HiDebug C/C++接口功能独立，需要获取调试信息时直接调用。具体调用示例请参考下文。

## 通用开发示例


下文展示如何在应用内使用HiDebug Ndk接口以进行线程栈回溯，且获取进程内线程的CPU使用率：

步骤一：创建项目

1. 使用DevEco Studio新建一个Native C++工程，并新增文件“test_backtrace.cpp”与“test_backtrace.h”，目录结构如下：

   ```yml
   entry:
     src:
       main:
         cpp:
           - types:
             - libentry:
               - index.d.ts
           - CMakeLists.txt
           - napi_init.cpp
           - test_backtrace.cpp
           - test_backtrace.h
         ets:
           pages:
             - Index.ets
   ```

2. 编辑“test_backtrace.h”文件，内容如下：

   <!-- @[TestHidebugNdk_Backtrace](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/cpp/test_backtrace.h) -->

3. 编辑“test_backtrace.cpp”文件, 内容如下：

   <!-- @[TestHidebugNdk_Backtrace](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/cpp/test_backtrace.cpp) -->

4. 编辑“CMakeLists.txt”文件，添加库依赖：

   ```cmake
   # 新增动态库依赖libohhidebug.so和libhilog_ndk.z.so（日志输出）
   add_library(entry SHARED napi_init.cpp test_backtrace.cpp)
   target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so libohhidebug.so)
   ```

5. 编辑“napi_init.cpp”文件，导入依赖文件并定义测试方法。

   <!-- @[TestHidebugNdk_Function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/cpp/napi_init.cpp) -->

   注册“TestHiDebugNdk”为ArkTS接口并初始化主线程的信号处理函数:

   <!-- @[TestHidebugNdk_Define](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/cpp/napi_init.cpp) -->

6. 编辑“index.d.ts”文件，声明ArkTS接口：
   <!-- @[TestHidebugNdk](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/cpp/types/libentry/Index.d.ts) -->

7. 编辑“Index.ets”文件，添加触发接口调用的按钮，示例代码如下：
   导入依赖：
   <!-- @[TestHidebugNdk_Import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/ets/pages/Index.ets) -->
   定义测试方法：
   <!-- @[TestHidebugNdk_Function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/ets/pages/Index.ets) -->
   钮以触发接口调用：
   <!-- @[TestHidebugNdk_Buttons](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiDebugTool/entry/src/main/ets/pages/Index.ets) -->

步骤二：运行工程

1. 点击DevEco Studio界面中的运行按钮，然后分别单击应用界面上的“testGetThreadCpuUsage” 和 ‘’testHiDebugBackTrace‘ 按钮。

2. 在DevEco Studio底部切换到“Log”窗口，设置日志过滤条件为“testTag”，即可查看相关日志：

   ```Text
   ...
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000104
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000000
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000040
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000010
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000001
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000038
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000000
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000007
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000004
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000007
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000006
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000001
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000004
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000002
   **-** **:**:**.***   *****-*****   A00000/com.sam...gtool/testTag  com.sampl...ebugtool  I     GetAppThreadCpuUsage: threadId *****, cpuUsage: 0.000001
   ...
   **-** **:**:**.***   *****-*****   A0FF00/com.sam...gtool/testTag  com.sampl...ebugtool  I     native stack frame info for pc: ************ is relativePc: ****** funcOffset: 0x38 mapName: /data/storage/el1/bundle/libs/arm64/libentry.so functionName: TestNativeFrames(int) buildId: b6d3429f6e2e594b1c696e13049dae7e51694099 reserved: (null).
   **-** **:**:**.***   *****-*****   A0FF00/com.sam...gtool/testTag  com.sampl...ebugtool  I     native stack frame info for pc: ************ is relativePc: ****** funcOffset: 0x30 mapName: /data/storage/el1/bundle/libs/arm64/libentry.so functionName: TestNativeFrames(int) buildId: b6d3429f6e2e594b1c696e13049dae7e51694099 reserved: (null).
   **-** **:**:**.***   *****-*****   A0FF00/com.sam...gtool/testTag  com.sampl...ebugtool  I     native stack frame info for pc: ************ is relativePc: ****** funcOffset: 0x1c mapName: /data/storage/el1/bundle/libs/arm64/libentry.so functionName: TestBackTrace(napi_env__*, napi_callback_info__*) buildId: b6d3429f6e2e594b1c696e13049dae7e51694099 reserved: (null).
   ...
   **-** **:**:**.***   *****-*****   A0FF00/com.sam...gtool/testTag  com.sampl...ebugtool  I     js stack frame info for pc: ************ is relativePc: ****** line: 27 column: 21 mapName: /data/storage/el1/bundle/entry.hap functionName: testBackTraceJsFrame url: entry|entry|1.0.0|src/main/ets/pages/Index.ts packageName: .
   **-** **:**:**.***   *****-*****   A0FF00/com.sam...gtool/testTag  com.sampl...ebugtool  I     js stack frame info for pc: ************ is relativePc: ****** line: 25 column: 16 mapName: /data/storage/el1/bundle/entry.hap functionName: testBackTraceJsFrame url: entry|entry|1.0.0|src/main/ets/pages/Index.ts packageName: .
   **-** **:**:**.***   *****-*****   A0FF00/com.sam...gtool/testTag  com.sampl...ebugtool  I     js stack frame info for pc: ************ is relativePc: ****** line: 25 column: 16 mapName: /data/storage/el1/bundle/entry.hap functionName: testBackTraceJsFrame url: entry|entry|1.0.0|src/main/ets/pages/Index.ts packageName: .
   **-** **:**:**.***   *****-*****   A0FF00/com.sam...gtool/testTag  com.sampl...ebugtool  I     js stack frame info for pc: ************ is relativePc: ****** line: 25 column: 16 mapName: /data/storage/el1/bundle/entry.hap functionName: testBackTraceJsFrame url: entry|entry|1.0.0|src/main/ets/pages/Index.ts packageName: .
   ...
   ```