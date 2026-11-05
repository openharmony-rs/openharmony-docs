# Cleaning Up external_log Files (C/C++)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @jiangwenhao-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=cd8d7c80e214eec0c28814e8db1d37ffcbef77fe translatedAt=2026-11-05T00:59:07.219Z nl=1 -->

Since API version 26.0.1, you can register an external_log manager to notify the app to clean up and delete files when a fault log sandbox directory reaches its capacity threshold.

## Available APIs

For API usage, including parameter constraints and value ranges, see [hiappevent.h](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md).

| Name | Description |
| -------- | -------- |
| int OH_HiAppEvent_RegExternalLogCapacityReachedCallback(OH_HiAppEvent_ExternalLogCapacityReachedCallback callback) | Registers an external_log manager. |

## Registering an external_log Manager

### Creating a Project and Configuring the Build

1. Copy the jsoncpp library files required by the sample project to the new project.

   Open [HiAppEvent EventSub Sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub) and click **Download Current Directory** to download the EventSub project files.
   
   Create a Native C++ project. Copy the jsoncpp library files (the entire entry/libs and entry/src/main/cpp/thirdparty directories) from the extracted EventSub folder to the new project. The directory structure is as follows:
   ```text
   entry
   ├── libs        // Create this folder and place the third-party libraries here.
   └── src
       ├── main
       │   ├── cpp
       │   │   ├── CMakeLists.txt       // Import shared libraries.
       │   │   ├── napi_init.cpp        // Functions and watcher definitions.
       │   │   ├── thirdparty    // Create this folder and place the third-party libraries here.
       │   │   │   └── jsoncpp
       │   │   └── types
       │   │       └── libentry
       │   │           ├── Index.d.ts        // Define ArkTS APIs.
       │   │           └── oh-package.json5
       │   ├── ets
       │   │   ├── entryability
       │   │   │   └── EntryAbility.ets    // Add API calls.
       │   │   ├── entrybackupability
       │   │   │   └── EntryBackupAbility.ets
       │   │   └── pages
       │   │       └── Index.ets        // Home page.
   ```
   The source code for the jsoncpp library in this sample comes from the [third-party open-source jsoncpp library](https://codeload.github.com/open-source-parsers/jsoncpp/tar.gz/refs/tags/1.9.6).

2. Edit CMakeLists.txt to add the required source files and dynamic libraries.

   ```cmake
   set(GZ_FILE "${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/jsoncpp/src/jsoncpp-1.9.6.tar.gz")
   set(DEST_DIR "${CMAKE_CURRENT_SOURCE_DIR}/../../../build")
   # Check whether the entry/build directory exists.
   execute_process(COMMAND ${CMAKE_COMMAND} -E make_directory ${DEST_DIR})
   # Extract jsoncpp-1.9.6.tar.gz to entry/build to obtain the jsoncpp header directory.
   execute_process(COMMAND tar -xzf ${GZ_FILE} -C ${DEST_DIR}
       WORKING_DIRECTORY ${DEST_DIR})

   add_library(entry SHARED napi_init.cpp)
   # Add dependencies on libhiappevent_ndk.z.so and libhilog_ndk.z.so (log output).
   target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so libhiappevent_ndk.z.so)
   # Add the third-party libjsoncpp.so dependency to parse JSON strings in subscribed events.
   target_link_libraries(entry PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/jsoncpp/${OHOS_ARCH}/lib/libjsoncpp.so)
   target_include_directories(entry PRIVATE ${DEST_DIR}/jsoncpp-1.9.6/include/json)
   ```

3. Edit napi_init.cpp to include the dependencies and define LOG_TAG:

   <!-- @[EventSub_napi_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   #include "napi/native_api.h"
   // Adjust the json.h include path to match the location of jsoncpp in the project.
   #include "../../../build/jsoncpp-1.9.6/include/json/json.h"
   #include "hiappevent/hiappevent.h"
   #include "hiappevent/hiappevent_param.h"
   #include "hilog/log.h"
   
   #undef LOG_TAG
   #define LOG_TAG "testTag"
   ```
### Registering an external_log Manager

1. Edit napi_init.cpp to define the methods for registering an external_log manager:

    <!-- @[RegisterExternalLogMgr](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    // Define the callback function.
    void OnExternalLogCapacityReached(OH_HiAppEvent_ExternalLog* externalLogArr, uint32_t arrLen)
    {
        OH_LOG_INFO(LogType::LOG_APP, "[ExternalLogMgr_c] onCapacityReached triggered, log count: %{public}u", arrLen);
        for (uint32_t i = 0; i < arrLen; i++) {
            OH_HiAppEvent_ExternalLog* log = &externalLogArr[i];
            OH_LOG_INFO(LogType::LOG_APP, "[ExternalLogMgr_c] filePath: %{public}s, %{public}lld, %{public}ld,
                kb event: %{public}d", log->filePath, log->generationTs, log->fileSize, log->event);
            // Decide which fault files to delete. This example deletes the first 5 returned files.
            if (i < 5) {
                remove(log->filePath);
                OH_LOG_INFO(LogType::LOG_APP, "[ExternalLogMgr_c] remove file %{public}s", log->filePath);
            }
        }
    }

    // Register an external_log manager.
    static napi_value RegisterExternalLogMgr(napi_env env, napi_callback_info info)
    {
        int ret = OH_HiAppEvent_RegExternalLogCapacityReachedCallback(OnExternalLogCapacityReached);
        if (ret == HIAPPEVENT_SUCCESS) {
            OH_LOG_INFO(LogType::LOG_APP, "[ExternalLogMgr_c] RegExternalLogMgr succeeded");
        } else {
            OH_LOG_INFO(LogType::LOG_APP, "[ExternalLogMgr_c] RegExternalLogMgr failed, ret %{public}d", ret);
        }

        return {};
    }
    ```

2. Edit napi_init.cpp to expose RegisterExternalLogMgr() as an ArkTS API for registering an external_log manager:

    ``` C++
    static napi_value Init(napi_env env, napi_value exports)
    {
        napi_property_descriptor desc[] = {
            // ...
            { "registerExternalLogMgr", nullptr, RegisterExternalLogMgr, nullptr, nullptr, nullptr, napi_default, nullptr },
            // ...
        };
        napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
        return exports;
    }
    ```

3. Edit index.d.ts to define the ArkTS API:   

    ``` ts
    export const registerExternalLogMgr: () => void;
    ```

4. Edit EntryAbility.ets to add the API call in onCreate():   
   
   ``` ts
   import testNapi from 'libentry.so';
   ``` 

   ``` ts
   // Add a C API call in onCreate().
   // Register an external_log manager at startup.
   testNapi.registerExternalLogMgr();
   ```

### Adding a Subscription

Subscribe to a fault event. This example uses [Subscribing to Crash Events (C/C++)](hiappevent-watcher-crash-events-ndk.md).

## Debugging and Verification

1. Click the run button in DevEco Studio to run the project and start the app.

2. Search for ExternalLogMgr_c in the HiLog window to view the external_log manager registration log:

   ```text
   [ExternalLogMgr_c] RegExternalLogMgr succeeded
   ```

3. Trigger app crashes repeatedly until the external_log directory reaches its capacity threshold. Search for ExternalLogMgr_c in the HiLog window to view the capacity-threshold callback logs:

   ```text
   [ExternalLogMgr_c] onCapacityReached triggered, log count: 13
   [ExternalLogMgr_c] filePath: /data/storage/el2/log/hiappevent/APP_CRASH_1788402790404_27596_0.log, 1788402790404, 183 kb event: 2
   [ExternalLogMgr_c] remove file /data/storage/el2/log/hiappevent/APP_CRASH_1788402790404_27596_0.log
   ...
   [ExternalLogMgr_c] filePath: /data/storage/el2/log/hiappevent/APP_CRASH_1788399327280_26303_0.log, 1788399327280, 515 kb event: 1
   [ExternalLogMgr_c] remove file /data/storage/el2/log/hiappevent/APP_CRASH_1788399327280_26303_0.log
   ...
   [ExternalLogMgr_c] filePath: /data/storage/el2/log/hiappevent/APP_CRASH_1788402913687_48668_0.log, 1788402913687, 518 kb event: 1
   ```
