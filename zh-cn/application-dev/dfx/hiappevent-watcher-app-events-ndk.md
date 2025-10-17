# 事件订阅（C/C++）

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @junjie_shi-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

HiAppEvent提供了事件订阅接口，用于获取应用的事件。

## 接口说明

API接口的使用说明，包括参数使用限制和取值范围，请参考[HiAppEvent C API文档](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md)。

**订阅接口功能介绍**：

| 接口名 | 描述 |
| -------- | -------- |
| int OH_HiAppEvent_AddWatcher(HiAppEvent_Watcher* watcher) | 添加应用的事件观察者。 |
| int OH_HiAppEvent_RemoveWatcher(HiAppEvent_Watcher* watcher) | 移除应用的事件观察者。 |

**打点接口功能介绍**：

| 接口名 | 描述 |
| -------- | -------- |
| int OH_HiAppEvent_Write(const char* domain, const char* name, enum EventType type, const ParamList list) | 实现对参数为列表类型的应用事件打点。 |

## 事件订阅开发指导

以订阅崩溃事件（系统事件）和按钮点击事件（应用事件）为例，说明开发步骤。

### 步骤一：新建工程及编译配置

1. 获取该示例工程依赖的jsoncpp文件，
   从[三方开源库jsoncpp代码仓](https://github.com/open-source-parsers/jsoncpp)下载源码的压缩包，并按照README的**Amalgamated source**中介绍的操作步骤得到jsoncpp.cpp、json.h和json-forwards.h三个文件。
   新建Native C++工程，并将jsoncpp导入工程，目录结构如下：

   ```text
   entry
   └── src
       └── main
           ├── cpp
           │   ├── CMakeLists.txt
           │   ├── json
           │   │   ├── json-forwards.h
           │   │   └── json.h
           │   ├── jsoncpp.cpp
           │   ├── napi_init.cpp
           │   └── types
           │       └── libentry
           │           ├── Index.d.ts
           │           └── oh-package.json5
           └── ets
               ├── entryability
               │   └── EntryAbility.ets
               └── pages
                   └── Index.ets
   ```

2. 编辑“CMakeLists.txt”文件，添加源文件和动态库。

   ```cmake
   # 新增jsoncpp.cpp(解析订阅事件中的json字符串)源文件
   add_library(entry SHARED napi_init.cpp jsoncpp.cpp)
   # 新增动态库依赖libhiappevent_ndk.z.so和libhilog_ndk.z.so(日志输出)
   target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so libhiappevent_ndk.z.so)
   ```

3. 编辑“napi_init.cpp”文件，导入依赖的文件并定义LOG_TAG：

   <!-- @[EventSub_napi_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include "napi/native_api.h"
#include "json/json.h"
#include "hilog/log.h"
#include "hiappevent/hiappevent.h"
#include "hiappevent/hiappevent_event.h"

#undef LOG_TAG
#define LOG_TAG "testTag"
```

### 步骤二：订阅事件

1. 订阅事件。分别使用OnReceive类型观察者、OnTrigger类型观察者的订阅方式。
   - 订阅崩溃事件（系统事件），采用OnReceive类型观察者的订阅方式，观察者接收到事件后会立即触发OnReceive()回调。编辑“napi_init.cpp”文件，定义OnReceive类型观察者相关方法：

    <!-- @[AppEvent_Crash_C++_Add_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

   - 订阅按钮点击事件（应用事件），采用OnTrigger类型观察者的订阅方式。需满足OH_HiAppEvent_SetTriggerCondition()设置的条件，才能触发OnTrigger()回调。编辑 “napi_init.cpp”文件，定义OnTrigger类型观察者相关方法：

    <!-- @[AppEvent_Click_C++_Add_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

2. 编辑“napi_init.cpp”文件，添加按钮点击事件的打点接口：

   <!-- @[AppEvent_Click_C++_WriteAppEvent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

3. 编辑“napi_init.cpp”文件，注册RegisterWatcherCrash()(订阅崩溃事件)、RegisterWatcherClick()（订阅按钮点击事件）、WriteAppEvent()(按钮点击事件打点接口)为ArkTS接口：

   <!-- @[AppEvent_C++_Init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

4. 编辑“index.d.ts”文件，定义ArkTS接口：

   <!-- @[AppEvent_C++_Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/types/libentry/Index.d.ts) -->

5. 编辑“EntryAbility.ets”文件，在onCreate()函数中添加接口调用：

   <!-- @[EventSub_Capi_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   <!-- @[AppEvent_Call_Capi_Function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

### 步骤三：触发事件

编辑“Index.ets”文件，新增“WatchAppCrash ArkTS&C++”按钮以触发崩溃事件；新增“writeEvent C++”按钮，在按钮点击函数中进行事件打点。示例代码如下：

<!-- @[EventSub_Index_Capi_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->

<!-- @[AppEvent_Crash_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->

<!-- @[AppEvent_CPP_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->

## 调测验证

1. 点击DevEco Studio界面中的运行按钮，运行应用工程。在应用界面中点击“WatchAppCrash ArkTS&C++”按钮，触发崩溃事件。应用退出后重新打开应用。

2. 搜索关键字“AppEvents”，在HiLog窗口查看应用处理崩溃事件数据的日志：

   ```text
   AppEvents HiAppEvent success to read events with onReceive callback form C API
   AppEvents HiAppEvent eventInfo.domain=OS
   AppEvents HiAppEvent eventInfo.name=APP_CRASH
   AppEvents HiAppEvent eventInfo.eventType=1
   AppEvents HiAppEvent eventInfo.params.time=1750946685473
   AppEvents HiAppEvent eventInfo.params.bundle_name=com.example.cxxxx
   AppEvents HiAppEvent eventInfo.params.external_log=["/data/storage/el2/log/hiappevent/APP_CRASH_1750946685805_64003.log"]
   ```

3. 点击“writeEvent C++”按钮，触发按钮点击事件。搜索关键字“AppEvents”，在HiLog窗口查看应用处理按钮点击事件数据的日志：

   ```text
   AppEvents HiAppEvent success to read events with onTrigger callback form C API
   AppEvents HiAppEvent eventInfo={"domain_":"button","name_":"click","type_":4,"time_":1750947007108,"tz_":"","pid_":64750,"tid_":64750,"clickTime":1750947007}
   AppEvents HiAppEvent eventInfo.domain=button
   AppEvents HiAppEvent eventInfo.name=click
   AppEvents HiAppEvent eventInfo.eventType=4
   AppEvents HiAppEvent eventInfo.params.clickTime=1750947007
   ```

4. 移除应用的事件观察者：

   <!-- @[AppEvent_C++_RemoveWatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

5. 销毁应用的事件观察者：

   <!-- @[AppEvent_C++_DestroyWatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
