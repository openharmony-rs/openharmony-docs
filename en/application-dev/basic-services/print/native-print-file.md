# Printing Files (C/C++)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @guoshengbang-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=02b3587e911190b13ac6bc78e61c77d58159e033 translatedAt=2026-09-02T02:16:36.558Z pushedAt=2026-09-02T07:05:54.530Z -->

## Two Printing Methods Provided by OpenHarmony

[Method 1](#pull-up-the-system-print-preview-interface-through-the-api-to-deliver-a-job): An application calls an API to start the system print preview page. This method is suitable for applications that do not implement the print preview capability.

[Method 2](#directly-sending-a-print-job-through-the-print-interface): An application specifies the print file and options through APIs to directly send print jobs. This method is suitable for applications that have already implemented the print preview capability.

> **NOTE**
>
> To use the print service, you need to [declare the permission](../../security/AccessToken/declare-permissions.md): ohos.permission.PRINT.
>
> When the print service is no longer used, call OH_Print_UnregisterPrinterChangeListener() and OH_Print_StopPrinterDiscovery() to cancel event subscriptions first, and then call OH_Print_Release() to release the print client resources.
>
> The C/C++ APIs need to be used in an NDK project. For details, see [NDK Development Guide](../../napi/ndk-development-overview.md).

### Including NDK Header Files
The initial path is entry/src/main/cpp/types/napi_init.cpp # NAPI initialization entry in the C++ source directory (bridging ArkTS and C++).

<!-- @[print_native_init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include "napi/native_api.h"
#include "BasicServicesKit/ohprint.h"
#include "hilog/log.h"
#include <string>
#include <fcntl.h>
#include <unistd.h>
#include <vector>

#undef LOG_TAG
#define LOG_TAG "print c/c++"
#define LOGE(...) OH_LOG_ERROR(LOG_APP, ##__VA_ARGS__)
#define LOGI(...) OH_LOG_INFO(LOG_APP, ##__VA_ARGS__)
```

The initial path is entry/src/main/ets/pages/Index.ets # Main page in the ArkTS source directory.

<!-- @[print_native_ts_init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
import { Context } from '@kit.AbilityKit';

class HiLog {
  static info(...args: string[]): void {
    hilog.info(0x0, 'print c/c++ ', '%{public}s', `${args.join(' ')}`);
  }
}
```

### Adding a Dynamic Link Library to the CMake Script
The initial path is entry/src/main/cpp/types/CMakeLists.txt # CMake build configuration for the C++ source directory.
```cmake
target_link_libraries(entry PUBLIC
    libace_napi.z.so
    libhilog_ndk.z.so
    libohprint.so
)
```

### Bind the Page and Print Service Lifecycle
It is recommended that you bind the initialization and release of the print service to the lifecycle of the page that uses the system printing capability.

Encapsulate the C/C++ APIs.

<!-- @[print_native_callback1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static void PrinterDiscoveryCallback(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)
{
    // Printer discovery event, using the device ID as the unique identifier.
    if (printerInfo == nullptr) {
        LOGE("printerInfo is nullptr");
        return;
    }
    // Developers need to implement the relevant logic based on the specific event.
    switch (event) {
        // A printer is discovered, which may be reported repeatedly.
        case PRINTER_DISCOVERED:
            LOGI("do something, printer[%{public}s] discovered", printerInfo->printerId);
            break;
        // The printer is removed from the discovery list, reported only once.
        case PRINTER_LOST:
            LOGI("do something, printer[%{public}s] lost", printerInfo->printerId);
            break;
        // The printer starts connecting, triggered by OH_Print_ConnectPrinter.
        case PRINTER_CONNECTING:
            LOGI("do something, printer[%{public}s] on connecting", printerInfo->printerId);
            break;
        // The printer is connected successfully, triggered by OH_Print_ConnectPrinter.
        case PRINTER_CONNECTED:
            LOGI("do something, printer[%{public}s] connected", printerInfo->printerId);
            break;
        default:
            break;
    }
}
```

<!-- @[print_native_callback2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static void PrinterChangeCallback(Print_PrinterEvent event, const Print_PrinterInfo *printerInfo)
{
    // Using the device ID as the unique identifier.
    if (printerInfo == nullptr) {
        LOGE("printerInfo is nullptr");
        return;
    }
    // Developers need to implement the relevant logic based on the specific event.
    switch (event) {
        // The printer is added to the added device list.
        case PRINTER_ADDED:
            LOGI("do something, printer[%{public}s] added", printerInfo->printerId);
            break;
        // The printer is removed from the added device list.
        case PRINTER_DELETED:
            LOGI("do something, printer[%{public}s] deleted", printerInfo->printerId);
            break;
        // The printer status changes.
        case PRINTER_STATE_CHANGED:
            LOGI("do something, printer[%{public}s] state change to %{public}d",
                 printerInfo->printerId, printerInfo->printerState);
            break;
        // The printer basic attributes change.
        case PRINTER_INFO_CHANGED:
            LOGI("do something, printer[%{public}s] info changed", printerInfo->printerId);
            break;
        default:
            break;
    }
}
```

<!-- @[print_native_lifecycle1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value NativeInit(napi_env env, napi_callback_info info)
{
    // Initialize the print service.
    Print_ErrorCode ret = OH_Print_Init();
    LOGI("nativeInit, ret = %{public}d", ret);
    napi_value n_ret = nullptr;
    napi_get_boolean(env, !ret, &n_ret);
    if (ret == 0) {
        // Subscribe to the added device status change event.
        Print_ErrorCode error = OH_Print_RegisterPrinterChangeListener(PrinterChangeCallback);
        LOGI("OH_Print_RegisterPrinterChangeListener, error = %{public}d", error);
        // Subscribe to device discovery related events.
        error = OH_Print_StartPrinterDiscovery(PrinterDiscoveryCallback);
        LOGI("OH_Print_StartPrinterDiscovery, error = %{public}d", error);
    }
    return n_ret;
}
```

<!-- @[print_native_lifecycle2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value NativeRelease(napi_env env, napi_callback_info info)
{
    // Unsubscribe from the added device status change event.
    OH_Print_UnregisterPrinterChangeListener();
    // Unsubscribe from device discovery related events.
    OH_Print_StopPrinterDiscovery();
    // Release the print service.
    Print_ErrorCode ret = OH_Print_Release();
    LOGI("nativeRelease, ret = %{public}d", ret);
    napi_value n_ret = nullptr;
    napi_get_boolean(env, !ret, &n_ret);
    return n_ret;
}
```

``` C++
// Add the napi interface declaration.
EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        { "nativeInit", nullptr, NativeInit, nullptr, nullptr, nullptr, napi_default, nullptr },
        { "nativeRelease", nullptr, NativeRelease, nullptr, nullptr, nullptr, napi_default, nullptr },
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END
```

On the application side, initialize the print service in the lifecycle when the page is launched, and release it when the page is closed.

<!-- @[print_native_ts_lifecycle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Initialize the print service when the page is displayed on the screen.
aboutToAppear(): void {
  testNapi.nativeInit();
}
// When the page leaves the screen.
aboutToDisappear(): void {
  testNapi.nativeRelease();
}
```

### Pull up the system print preview interface through the API to deliver a job
Encapsulate the C/C++ APIs.

<!-- @[print_native_startprint1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// WriteFile is implemented by the developer, and the example is only a simple file copy. Based on the print parameters modified by the current user, if the print file needs to be updated, it can be rewritten into the fd provided by the system.
static uint32_t WriteFile(uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs)
{
    // A valid path within the sandbox.
    const char* filePath = "/data/storage/el2/base/files/test.pdf";
    int32_t fileFd = open(filePath, O_RDONLY);
    if (fileFd == -1) {
        LOGE("open failed, errno=%{public}d", errno);
        return 1;
    }

    char buffer[4096];
    ssize_t bytesRead = -1;
    while ((bytesRead = read(fileFd, buffer, sizeof(buffer))) > 0) {
        if (write(fd, buffer, bytesRead) < bytesRead) {
            close(fileFd);
            return 1;
        }
    }
    close(fileFd);
    return 0;
}
```

<!-- @[print_native_startprint2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// Callback for the system print preview interface. Delayed file write callback triggered when the preview is first launched or when the user modifies print parameters. The print file can be modified appropriately based on the new parameters.
static void OnStartLayoutWriteCb(const char *jobId,
                                 uint32_t fd,
                                 const Print_PrintAttributes *oldAttrs,
                                 const Print_PrintAttributes *newAttrs,
                                 Print_WriteResultCallback writeCallback)
{
    // Write data to the fd provided by the system. The fd may differ for each callback, so do not save this fd.
    uint32_t retCode = WriteFile(fd, oldAttrs, newAttrs);
    // Notify the print system that file writing is complete. If asynchronous data writing is required, save the jobId.
    // retCode values: 0 - write succeeded, 1 - write exception, 2 - no need to rewrite.
    writeCallback(jobId, retCode);
}

// After the print file is written, the system print preview interface displays a preview, and the user can click "Start Printing" to submit the job.
// Callback function for print status changes corresponding to the job ID.
static void OnJobStateChangedCb(const char *jobId, uint32_t state)
{
    // state values: 0 - job preparing, 1 - job queued, 2 - job printing, 3 - job paused due to exception, 4 - job finished, 100 - unknown job exception.
    LOGI("do something with OnJobStateChangedCb, jobId: %{public}s, jobState: %{public}u", jobId, state);
}
```

<!-- @[print_native_startprint3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// Launch the system print preview interface
static napi_value NativeStartPrintByNative(napi_env env, napi_callback_info info)
{
    napi_value n_ret = nullptr;
    void *context = nullptr;
    size_t argc = 1;
    napi_value argv[1] = {nullptr};
    // Assume that both napi_get_cb_info and napi_unwrap return normally.
    napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);
    napi_unwrap(env, argv[0], &context);

    // Call the print API to launch the system print preview interface.
    std::string printJobName = "test";
    Print_PrintDocCallback printDocCallback = { OnStartLayoutWriteCb, OnJobStateChangedCb };
    Print_ErrorCode ret = OH_Print_StartPrintByNative(printJobName.c_str(), printDocCallback, context);
    napi_get_boolean(env, !ret, &n_ret);
    return n_ret;
}
```

``` C++
// Add the napi interface declaration.
EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        { "nativeStartPrintByNative",
            nullptr, NativeStartPrintByNative, nullptr, nullptr, nullptr, napi_default, nullptr },
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END
```

Add a button on the home page. When the button is clicked, the nativeStartPrintByNative C/C++ API is called to pull up the print preview interface.

<!-- @[print_native_ts_startprint](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('OH_Print_StartPrintByNative')
  .onClick(() => {
    HiLog.info("OH_Print_StartPrintByNative onClick");
    let ctx: Context | undefined = this.getUIContext().getHostContext();
    let ret: boolean = testNapi.nativeStartPrintByNative(ctx);
    HiLog.info(`nativeStartPrintByNative ret: ${JSON.stringify(ret)}`);
  })
```

### Directly Sending a Print Job Through the Print Interface
Encapsulate the C/C++ interface. This example only demonstrates obtaining information from the list of added print devices and sending a job.

<!-- @[print_native_startjob](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// Submit the print job.
static napi_value NativeStartPrintJob(napi_env env, napi_callback_info info)
{
    napi_value n_ret = nullptr;
    napi_get_boolean(env, false, &n_ret);
    Print_ErrorCode ret = PRINT_ERROR_INVALID_PARAMETER;

    // Obtain the list of added printers.
    Print_StringList pList = { 0 };
    ret = OH_Print_QueryPrinterList(&pList);
    if (ret != PRINT_ERROR_NONE) {
        OH_Print_ReleasePrinterList(&pList);
        return n_ret;
    }
    if (pList.count <= 0 || (!pList.list)) {
        OH_Print_ReleasePrinterList(&pList);
        return n_ret;
    }
    // Print all printer IDs in the list.
    for (uint32_t index = 0; index < pList.count; index++) {
        LOGI("pList->list[%{public}d]: %{public}s", index, pList.list[index]);
    }

    // Obtain the properties of the first printer in the list.
    const char *printerId = pList.list[0];
    Print_PrinterInfo *printerInfo = nullptr;
    ret = OH_Print_QueryPrinterInfo(printerId, &printerInfo);
    if (ret != PRINT_ERROR_NONE) {
        OH_Print_ReleasePrinterInfo(printerInfo);
        OH_Print_ReleasePrinterList(&pList);
        return n_ret;
    }
    // Open the files to print. There can be multiple files, with valid paths in the sandbox.
    const char* filePath = "/data/storage/el2/base/files/test.pdf";
    int32_t fd = open(filePath, O_RDONLY);
    if (fd == -1) {
        LOGE("open failed, errno=%{public}d", errno);
        ret = PRINT_ERROR_INVALID_PARAMETER;
        OH_Print_ReleasePrinterInfo(printerInfo);
        OH_Print_ReleasePrinterList(&pList);
        return n_ret;
    }
    std::vector<uint32_t> fdList = { static_cast<uint32_t>(fd) };
    // This example uses the preference printerInfo->defaultValue as the print job parameter to submit the job.
    Print_PrintJob printJob{ "jobName", fdList.data(), static_cast<uint32_t>(fdList.size()), printerInfo->printerId,
                             1, printerInfo->defaultValue.defaultPaperSource,
                             printerInfo->defaultValue.defaultMediaType, printerInfo->defaultValue.defaultPageSizeId,
                             printerInfo->defaultValue.defaultColorMode, printerInfo->defaultValue.defaultDuplexMode,
                             printerInfo->defaultValue.defaultResolution, printerInfo->defaultValue.defaultMargin,
                             true, printerInfo->defaultValue.defaultOrientation,
                             printerInfo->defaultValue.defaultPrintQuality, DOCUMENT_FORMAT_PDF,
                             printerInfo->defaultValue.otherDefaultValues, };
    ret = OH_Print_StartPrintJob(&printJob);
    close(fd);
    // Release the printer properties and the added list promptly after use.
    OH_Print_ReleasePrinterInfo(printerInfo);
    OH_Print_ReleasePrinterList(&pList);

    napi_get_boolean(env, !ret, &n_ret);
    return n_ret;
}
```

``` C++
// Add the napi interface declaration.
EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        { "nativeStartPrintJob", nullptr, NativeStartPrintJob, nullptr, nullptr, nullptr, napi_default, nullptr },
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END
```

Add a button on the home page. When clicked, it calls the C/C++ nativeStartPrintJob to directly send a job.

<!-- @[print_native_ts_startjob](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('OH_Print_StartPrintJob')
  .onClick(() => {
    HiLog.info('OH_Print_StartPrintJob onClick');
    let ret: boolean = testNapi.nativeStartPrintJob();
    HiLog.info(`OH_Print_StartPrintJob ret: ${JSON.stringify(ret)}`);
  })
```
