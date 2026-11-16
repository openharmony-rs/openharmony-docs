# 文件打印（C/C++）

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @Zouhaifeng1-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->

OpenHarmony提供以下两种文件打印方式：

- [系统预览打印](#通过接口拉起系统打印预览界面下发任务)：应用通过接口拉起系统打印预览界面，适合未实现打印预览能力的应用。
- [直接打印](#通过打印接口直接下发打印任务)：应用指定打印机、打印文件和打印选项后直接下发任务，适合已实现打印预览能力的应用。API 24及以上还可以在下发任务时注册[状态回调](#状态回调打印)。

> **说明：**
>
> 使用打印服务前，需[声明权限](../../security/AccessToken/declare-permissions.md)：`ohos.permission.PRINT`。
>
> C/C++接口需要在NDK工程中使用，NDK工程的创建和配置方法请参考[NDK开发导读](../../napi/ndk-development-overview.md)。
>
> 不再使用打印服务时，需先调用`OH_Print_UnregisterPrinterChangeListener()`和`OH_Print_StopPrinterDiscovery()`取消事件订阅，再调用`OH_Print_Release()`释放打印客户端资源。

## 开发准备

本文代码摘录自 [NativePrintFile 完整 Sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/print/NativePrintFile)，对应目录为 `code/DocsSample/print/NativePrintFile`。请下载完整工程后构建；各代码块共享同一工程中的模型、辅助函数和资源。

- **版本与设备：** 完整 Sample 使用 API 24 的状态回调接口，`build-profile.json5` 的 `compileSdkVersion`、`targetSdkVersion`、`compatibleSdkVersion` 均为 24，`runtimeOS` 为 `OpenHarmony`。需准备 OpenHarmony API 24 SDK（包括 Native 组件）及 API 24 或以上版本的目标设备；发现和连接还依赖系统中已安装且可用的 Print Extension。
- **权限：** 在 `entry/src/main/module.json5` 的 `module.requestPermissions` 中声明 `ohos.permission.PRINT`，完整配置见 [module.json5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/module.json5)。
- **Native 类型：** [Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/types/libentry/Index.d.ts) 声明 `libentry.so` 的函数和返回结构；[entry/oh-package.json5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/oh-package.json5) 通过 `"libentry.so": "file:./src/main/cpp/types/libentry"` 关联该类型包。类型声明须与 Native 导出及实际返回值保持一致。
- **文件准备：** Sample 自带 `entry/src/main/resources/rawfile/printDemo.pdf` 和 `printSample.jpg`。[PrintFileUtils.openSample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/print/utils/PrintFileUtils.ets) 先读取 rawfile 内容，写入 `context.filesDir` 中的同名文件，关闭写入描述符，再以只读方式打开文件供打印使用。打开失败返回 `undefined`，调用方在 `finally` 中调用 `PrintFileUtils.close` 回收只读描述符。

步骤1：在`entry/src/main/cpp/napi_init.cpp`中引入打印、NAPI和日志头文件。示例使用互斥锁保护跨线程回调对象，并使用标准容器保存需要跨越C API调用边界的数据。

<!-- @[print_native_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include "BasicServicesKit/ohprint.h"
#include "hilog/log.h"
#include "napi/native_api.h"

#include <cerrno>
#include <cstdint>
#include <fcntl.h>
#include <mutex>
#include <string>
#include <unistd.h>
#include <vector>

#undef LOG_TAG
#define LOG_TAG "NativePrintFile"
#define LOGE(...) OH_LOG_ERROR(LOG_APP, ##__VA_ARGS__)
#define LOGI(...) OH_LOG_INFO(LOG_APP, ##__VA_ARGS__)
```

步骤2：在`entry/src/main/ets/pages/Index.ets`中引入NAPI模块、文件模块、数据模型和ArkUI组件。

<!-- @[print_native_import_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { Context } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';
import nativePrint from 'libentry.so';
import { PrintSettings } from '../print/components/PrintSettings';
import { PrinterDialog } from '../print/dialogs/PrinterDialog';
import {
  DiscoveryEvent,
  INVALID_PRINTER_ERROR,
  MarginModel,
  NativePrintEventType,
  PageSizeModel,
  PrinterInfoModel,
  PrintJobModel,
  PrintOptionModel,
  PrintPropertyModel,
  PrintRequest
} from '../print/model/PrintModels';
import { PrintFileUtils } from '../print/utils/PrintFileUtils';
```

步骤3：在`entry/src/main/cpp/CMakeLists.txt`中链接NAPI、日志和打印动态库。

<!-- @[print_native_cmake](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/CMakeLists.txt) -->

``` Text
cmake_minimum_required(VERSION 3.5.0)
project(NativePrintFile)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(entry SHARED napi_init.cpp)
string(CONCAT PRINT_LOG_LIBRARY "libhilog_n" "dk.z.so")
target_link_libraries(entry PUBLIC libace_napi.z.so ${PRINT_LOG_LIBRARY} libohprint.so)
```

步骤4：将打印机信息复制到应用自有数据结构后，再通过线程安全函数传递到ArkTS线程，避免在C API回调结束后继续访问`Print_PrinterInfo`中的指针。

<!-- @[print_native_declarations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
struct PageSizeData {
    std::string id;
    std::string name;
    uint32_t width = 0;
    uint32_t height = 0;
};

struct PrinterInfoData {
    std::string printerId;
    std::string printerName;
    std::string printerUri;
    uint32_t printerState = 0;
    uint32_t colorMode = 0;
    uint32_t copySupported = 0;
    bool isOnline = false;
    std::vector<PageSizeData> pageSizes;
};

struct PrinterEventData {
    uint32_t event = 0;
    PrinterInfoData printerInfo;
};

struct NativePrintEventData {
    uint32_t eventType = 0;
    std::string jobId;
    uint32_t state = 0;
    uint32_t writeCode = 0;
};

struct PrintJobStateEventData {
    std::string jobId;
    uint32_t state = 0;
};
```

## 初始化与发现打印机

步骤1：封装打印服务初始化和释放接口。释放时先停止发现并注销监听，回收对应线程安全函数，再释放打印服务并清理本地打印回调和文件描述符。线程安全函数的创建、传值及释放辅助实现见完整 Sample 的 [napi_init.cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp)。

<!-- @[print_native_lifecycle_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
napi_value NativeInit(napi_env env, napi_callback_info)
{
    std::lock_guard<std::mutex> lock(g_serviceMutex);
    if (g_initialized) {
        return CreateInt32(env, PRINT_ERROR_NONE);
    }
    Print_ErrorCode code = OH_Print_Init();
    if (code == PRINT_ERROR_NONE) {
        g_initialized = true;
    }
    return CreateInt32(env, code);
}

napi_value NativeRelease(napi_env env, napi_callback_info)
{
    {
        std::lock_guard<std::mutex> lock(g_serviceMutex);
        if (!g_initialized) {
            return CreateInt32(env, PRINT_ERROR_NONE);
        }
    }
    if (g_discoveryRunning) {
        OH_Print_StopPrinterDiscovery();
        g_discoveryRunning = false;
    }
    ReleaseTsfn(g_discoveryMutex, g_discoveryTsfn, napi_tsfn_abort);
    if (g_listenerRegistered) {
        OH_Print_UnregisterPrinterChangeListener();
        g_listenerRegistered = false;
    }
    ReleaseTsfn(g_printerChangeMutex, g_printerChangeTsfn, napi_tsfn_abort);
    Print_ErrorCode code = OH_Print_Release();
    ReleaseNativePrintTask(napi_tsfn_abort);
    ReleasePrintJobStateTask(napi_tsfn_abort);
    {
        std::lock_guard<std::mutex> lock(g_serviceMutex);
        g_initialized = false;
    }
    return CreateInt32(env, code);
}
```

步骤2：将打印服务生命周期与页面生命周期绑定。页面只持有一条发现会话，添加打印机弹窗直接复用页面保存的发现结果。

<!-- @[print_native_lifecycle_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
aboutToAppear(): void {
  this.operationResult = this.getResourceText($r('app.string.waiting_operation'));
  const initCode: number = nativePrint.nativeInit();
  if (initCode !== 0) {
    this.setCodeResult('OH_Print_Init', initCode);
    return;
  }
  const listenerCode: number = nativePrint.nativeRegisterPrinterChangeListener(
    (event: number, printerInfo: nativePrint.PrinterInfo): void => {
      this.handlePrinterChange(event, PrinterInfoModel.fromNative(printerInfo));
    });
  if (listenerCode !== 0) {
    this.setCodeResult('OH_Print_RegisterPrinterChangeListener', listenerCode);
  }
  this.startDiscovery();
}

aboutToDisappear(): void {
  this.printerDialogController.close();
  nativePrint.nativeStopPrinterDiscovery();
  nativePrint.nativeUnregisterPrinterChangeListener();
  nativePrint.nativeRelease();
}
```

步骤3：在Native层注册发现回调并封装开始发现、停止发现和连接打印机接口。线程安全函数采用单会话管理，停止发现时同步释放。

<!-- @[print_native_discovery_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
void PrinterDiscoveryCallback(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)
{
    if (printerInfo == nullptr) {
        return;
    }
    PrinterEventData *data = new PrinterEventData;
    data->event = static_cast<uint32_t>(event);
    data->printerInfo = CopyPrinterInfo(printerInfo);
    std::lock_guard<std::mutex> lock(g_discoveryMutex);
    if (g_discoveryTsfn == nullptr ||
        napi_call_threadsafe_function(g_discoveryTsfn, data, napi_tsfn_nonblocking) != napi_ok) {
        delete data;
    }
}

napi_value NativeStartPrinterDiscovery(napi_env env, napi_callback_info info)
{
    size_t count = 1;
    napi_value args[1] = {nullptr};
    if (napi_get_cb_info(env, info, &count, args, nullptr, nullptr) != napi_ok || count != 1 ||
        GetValueType(env, args[ARG_FIRST]) != napi_function) {
        return CreateInt32(env, PRINT_ERROR_INVALID_PARAMETER);
    }
    {
        std::lock_guard<std::mutex> lock(g_discoveryMutex);
        if (g_discoveryTsfn != nullptr ||
            !CreateTsfn(env, args[ARG_FIRST], "PrinterDiscovery", CallPrinterEventJs, g_discoveryTsfn)) {
            return CreateInt32(env, ERROR_GENERIC);
        }
    }
    Print_ErrorCode code = OH_Print_StartPrinterDiscovery(PrinterDiscoveryCallback);
    if (code != PRINT_ERROR_NONE) {
        ReleaseTsfn(g_discoveryMutex, g_discoveryTsfn, napi_tsfn_abort);
    } else {
        g_discoveryRunning = true;
    }
    return CreateInt32(env, code);
}

napi_value NativeStopPrinterDiscovery(napi_env env, napi_callback_info)
{
    Print_ErrorCode code = PRINT_ERROR_NONE;
    if (g_discoveryRunning) {
        code = OH_Print_StopPrinterDiscovery();
        g_discoveryRunning = false;
    }
    ReleaseTsfn(g_discoveryMutex, g_discoveryTsfn, napi_tsfn_abort);
    return CreateInt32(env, code);
}

napi_value NativeConnectPrinter(napi_env env, napi_callback_info info)
{
    size_t count = 1;
    napi_value args[1] = {nullptr};
    std::string printerId;
    if (napi_get_cb_info(env, info, &count, args, nullptr, nullptr) != napi_ok || count != 1 ||
        !GetString(env, args[ARG_FIRST], printerId) || printerId.empty()) {
        return CreateInt32(env, PRINT_ERROR_INVALID_PARAMETER);
    }
    return CreateInt32(env, OH_Print_ConnectPrinter(printerId.c_str()));
}
```

步骤4：ArkTS侧分别处理`DISCOVERED`、`LOST`、`CONNECTING`和`CONNECTED`事件，只有收到`CONNECTED`事件后才将打印机设为当前打印机。

<!-- @[print_native_discovery_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
private startDiscovery(): void {
  const addedPrinters: nativePrint.PrinterIdListResult = nativePrint.nativeQueryPrinterList();
  if (addedPrinters.code === 0) {
    for (const printerId of addedPrinters.printerIds) {
      const result: nativePrint.PrinterInfoResult = nativePrint.nativeQueryPrinterInfo(printerId);
      if (result.code === 0 && result.printerInfo !== undefined) {
        this.upsertPrinter(PrinterInfoModel.fromNative(result.printerInfo));
      }
    }
  }
  const code: number = nativePrint.nativeStartPrinterDiscovery(
    (event: number, printerInfo: nativePrint.PrinterInfo): void => {
      this.handleDiscoveryEvent(event, PrinterInfoModel.fromNative(printerInfo));
    });
  this.setCodeResult('OH_Print_StartPrinterDiscovery', code);
}

private handleDiscoveryEvent(event: number, printer: PrinterInfoModel): void {
  if (event === DiscoveryEvent.LOST) {
    if (this.selectedPrinter.printerId === printer.printerId) {
      const result: nativePrint.PrinterInfoResult = nativePrint.nativeQueryPrinterInfo(printer.printerId);
      if (result.code === 0 && result.printerInfo !== undefined) {
        this.selectPrinter(PrinterInfoModel.fromNative(result.printerInfo));
        return;
      }
    }
    this.removePrinter(printer.printerId);
    return;
  }
  if (event === DiscoveryEvent.DISCOVERED) {
    this.upsertPrinter(printer);
    return;
  }
  if (event === DiscoveryEvent.CONNECTING) {
    if (this.selectedPrinter.printerId !== printer.printerId) {
      this.operationResult = this.getResourceText($r('app.string.connecting')) + ': ' + printer.printerName;
    }
    return;
  }
  if (event === DiscoveryEvent.CONNECTED) {
    this.upsertPrinter(printer);
    this.selectPrinter(printer);
    this.operationResult = this.getResourceText($r('app.string.connected')) + ': ' + printer.printerName;
  }
}

private connectPrinter(printer: PrinterInfoModel): void {
  const addedPrinters: nativePrint.PrinterIdListResult = nativePrint.nativeQueryPrinterList();
  if (addedPrinters.code === 0 && addedPrinters.printerIds.includes(printer.printerId)) {
    const existing: nativePrint.PrinterInfoResult = nativePrint.nativeQueryPrinterInfo(printer.printerId);
    if (existing.code === 0 && existing.printerInfo !== undefined) {
      const addedPrinter: PrinterInfoModel = PrinterInfoModel.fromNative(existing.printerInfo);
      this.upsertPrinter(addedPrinter);
      this.selectPrinter(addedPrinter);
      this.setCodeResult('OH_Print_QueryPrinterInfo (added)', existing.code);
      return;
    }
  }
  const code: number = nativePrint.nativeConnectPrinter(printer.printerId);
  this.setCodeResult('OH_Print_ConnectPrinter', code);
  if (code !== 0) {
    return;
  }
  const result: nativePrint.PrinterInfoResult = nativePrint.nativeQueryPrinterInfo(printer.printerId);
  if (result.code === 0 && result.printerInfo !== undefined) {
    const connectedPrinter: PrinterInfoModel = PrinterInfoModel.fromNative(result.printerInfo);
    this.upsertPrinter(connectedPrinter);
    this.selectPrinter(connectedPrinter);
    this.operationResult = this.getResourceText($r('app.string.connected')) + ': ' + connectedPrinter.printerName;
  }
}
```

## 通过接口拉起系统打印预览界面下发任务

系统预览打印通过`OH_Print_StartPrintByNative()`拉起系统打印界面。**本示例的系统预览仅支持 PDF**，请选择内置 `printDemo.pdf`；选择 JPEG 时，页面提示改选 PDF，不会替换用户所选文件。布局回调需要向系统提供的文件描述符写入 PDF，本示例直接复制已有 PDF，没有实现 JPEG 转 PDF。

系统预览的打印机和打印选项在系统打印界面中选择。页面上的纸张、份数、颜色、单双面、方向、质量、边距及无边距设置仅传给后文的直接打印和状态回调打印入口。示例布局回调没有使用 `oldAttrs` / `newAttrs` 重新排版，而是复制固定 PDF；需要随打印属性改变文档内容的应用，应自行实现布局与 PDF 生成。

Native层使用`dup()`持有ArkTS传入的源文件描述符；系统请求写入时，[CopyFileToPrintFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) 再复制一份描述符，从文件起始位置读取并在本次复制结束后关闭该副本。持久副本由 `ReleaseNativePrintTask` 在预览会话结束、接口启动失败或打印服务释放时回收。

`NativeStartLayoutWrite` 在复制完成后关闭本次布局回调收到的目标文件描述符，再通过 `writeCallback` 报告结果；复制失败也执行关闭，关闭失败报告文件创建失败。源文件副本和布局目标文件描述符分别释放，避免重复布局时积累文件句柄。

`Print_WriteResultCallback` 的 `code` 表示文件生成结果：0为创建成功，1为创建失败，2为创建成功但未渲染。它不是 `Print_ErrorCode`，也不是任务状态。示例将文件复制成功映射为0、失败映射为1；具体 I/O 错误保留在日志中，ArkTS 事件的 `writeCode` 使用相同的0/1含义。

预览状态回调使用 [Print_JobDocAdapterState](../../reference/apis-basic-services-kit/capi-ohprint-h.md#print_jobdocadapterstate)，与 API 24 的任务状态枚举不同：

| 状态值 | 枚举项 | 含义 |
| --- | --- | --- |
| 0 | `PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY` | 预览能力销毁 |
| 1 | `PRINT_DOC_ADAPTER_PRINT_TASK_SUCCEED` | 打印任务成功 |
| 2 | `PRINT_DOC_ADAPTER_PRINT_TASK_FAIL` | 打印任务失败 |
| 3 | `PRINT_DOC_ADAPTER_PRINT_TASK_CANCEL` | 打印任务取消 |
| 4 | `PRINT_DOC_ADAPTER_PRINT_TASK_BLOCK` | 打印任务阻塞 |
| 5 | `PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_CANCELED` | 因取消导致预览能力销毁 |
| 6 | `PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_STARTED` | 因启动导致预览能力销毁 |

本示例保留阻塞状态下的资源，收到其他上述状态后结束本地预览会话并释放回调。0、5、6只表示预览能力销毁，不能据此判断打印成功；该预览会话结束后，示例不再通过它持续追踪最终打印结果。

步骤1：在Native层实现文件写入回调、任务状态回调和NAPI接口。

<!-- @[print_native_preview_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
void NativeStartLayoutWrite(const char *jobId, uint32_t fd, const Print_PrintAttributes *,
    const Print_PrintAttributes *, Print_WriteResultCallback writeCallback)
{
    const uint32_t ioCode = CopyFileToPrintFd(fd);
    if (ioCode != PRINT_ERROR_NONE) {
        LOGE("Failed to copy PDF, error=%{public}u", ioCode);
    }
    const int closeResult = close(static_cast<int32_t>(fd));
    if (closeResult != 0) {
        LOGE("Failed to close layout file, errno=%{public}d", errno);
    }
    // Print_WriteResultCallback uses file creation results: 0 = success, 1 = failure.
    const uint32_t writeResult = ioCode == PRINT_ERROR_NONE && closeResult == 0 ? 0 : 1;
    NotifyNativePrintEvent(0, jobId, 0, writeResult);
    if (writeCallback != nullptr) {
        writeCallback(jobId, writeResult);
    }
}

void NativeJobStateChanged(const char *jobId, uint32_t state)
{
    NotifyNativePrintEvent(1, jobId, state, 0);
    if (state != PRINT_DOC_ADAPTER_PRINT_TASK_BLOCK) {
        ReleaseNativePrintTask(napi_tsfn_release);
    }
}

napi_value NativeStartPrintByNative(napi_env env, napi_callback_info info)
{
    size_t count = NATIVE_PRINT_ARGUMENT_COUNT;
    napi_value args[NATIVE_PRINT_ARGUMENT_COUNT] = {nullptr};
    std::string jobName;
    int32_t sourceFd = -1;
    void *context = nullptr;
    if (napi_get_cb_info(env, info, &count, args, nullptr, nullptr) != napi_ok ||
        count != NATIVE_PRINT_ARGUMENT_COUNT || !GetString(env, args[ARG_FIRST], jobName) || jobName.empty() ||
        GetValueType(env, args[ARG_SECOND]) != napi_number ||
        napi_get_value_int32(env, args[ARG_SECOND], &sourceFd) != napi_ok || sourceFd < 0 ||
        napi_unwrap(env, args[ARG_THIRD], &context) != napi_ok || context == nullptr ||
        GetValueType(env, args[ARG_FOURTH]) != napi_function) {
        return CreateInt32(env, PRINT_ERROR_INVALID_PARAMETER);
    }
    {
        std::lock_guard<std::mutex> lock(g_nativePrintMutex);
        if (g_nativePrintTsfn != nullptr ||
            !CreateTsfn(env, args[ARG_FOURTH], "NativePrint", CallNativePrintEventJs, g_nativePrintTsfn)) {
            return CreateInt32(env, ERROR_GENERIC);
        }
        g_nativePrintSourceFd = dup(sourceFd);
        if (g_nativePrintSourceFd < 0) {
            napi_threadsafe_function failed = g_nativePrintTsfn;
            g_nativePrintTsfn = nullptr;
            napi_release_threadsafe_function(failed, napi_tsfn_abort);
            return CreateInt32(env, PRINT_ERROR_FILE_IO);
        }
    }
    Print_PrintDocCallback callback = {NativeStartLayoutWrite, NativeJobStateChanged};
    Print_ErrorCode code = OH_Print_StartPrintByNative(jobName.c_str(), callback, context);
    if (code != PRINT_ERROR_NONE) {
        ReleaseNativePrintTask(napi_tsfn_abort);
    }
    return CreateInt32(env, code);
}
```

步骤2：ArkTS侧先检查所选文件为PDF，再临时打开文件。Native接口返回后立即关闭ArkTS持有的文件描述符，后续写入由Native层持有的副本完成。返回0表示本次接口调用成功；后续文件写入和预览状态通过回调分别观察。

<!-- @[print_native_preview_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
private async startSystemPreviewPrint(): Promise<void> {
  if (this.selectedDocumentFormat !== 'application/pdf') {
    this.operationResult = this.getResourceText($r('app.string.preview_pdf_only'));
    return;
  }
  const context: Context | undefined = this.getContext();
  if (context === undefined) {
    this.setCodeResult('OH_Print_StartPrintByNative', 401);
    return;
  }
  let file: fileIo.File | undefined = undefined;
  try {
    file = await PrintFileUtils.openSample(context, this.selectedFileName);
    if (file === undefined) {
      this.operationResult = this.getResourceText($r('app.string.open_file_failed'));
      return;
    }
    const code: number = nativePrint.nativeStartPrintByNative('NativePrintFile', file.fd, context,
      (event: nativePrint.NativePrintEvent): void => {
        if (event.eventType === NativePrintEventType.WRITE_RESULT) {
          this.operationResult = 'OH_Print_StartPrintByNative writeCode=' + event.writeCode.toString();
        } else {
          this.operationResult = 'OH_Print_StartPrintByNative state=' + event.state.toString();
        }
      });
    this.setCodeResult('OH_Print_StartPrintByNative', code);
  } catch {
    this.operationResult = this.getResourceText($r('app.string.open_file_failed'));
  } finally {
    PrintFileUtils.close(file);
  }
}
```

## 通过打印接口直接下发打印任务

直接打印需要使用已连接的打印机ID、文件描述符、纸张ID、分辨率、份数、颜色、单双面、方向、质量、边距和文档格式构造`Print_PrintJob`。此入口与状态回调打印均演示 JPEG / PDF 文件，格式由所选文件对应的 MIME 类型传入。

步骤1：使用 `PrintJobStorage` 持有作业中的字符串和文件描述符数组，再由 `BuildPrintJob` 校验并映射 ArkTS 的四组参数。

<!-- @[print_native_job_storage_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
struct PrintJobStorage {
    Print_PrintJob job = {};
    std::vector<uint32_t> fdList;
    std::string printerId;
    std::string jobName;
    std::string paperSource;
    std::string mediaType;
    std::string pageSizeId;
    std::string advancedOptions;
};
```

<!-- @[print_native_build_job_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
bool BuildPrintJob(napi_env env, napi_value printJobValue, napi_value pageSizeValue, napi_value marginValue,
    napi_value optionValue, PrintJobStorage &storage)
{
    napi_value fdListValue = GetProperty(env, printJobValue, "fdList");
    uint32_t dpi = 0;
    uint32_t colorMode = 0;
    uint32_t duplexMode = 0;
    uint32_t orientationMode = 0;
    uint32_t printQuality = 0;
    std::string documentFormat;
    bool borderless = false;
    bool valid = fdListValue != nullptr && GetUint32Array(env, fdListValue, storage.fdList) &&
        GetStringProperty(env, printJobValue, "printerId", storage.printerId) && !storage.printerId.empty() &&
        GetUint32Property(env, printJobValue, "copyNumber", storage.job.copyNumber) &&
        GetUint32Property(env, printJobValue, "dpi", dpi) &&
        GetUint32Property(env, printJobValue, "colorMode", colorMode) &&
        GetUint32Property(env, printJobValue, "duplexMode", duplexMode) &&
        GetUint32Property(env, printJobValue, "orientationMode", orientationMode) &&
        GetStringProperty(env, pageSizeValue, "id", storage.pageSizeId) && !storage.pageSizeId.empty() &&
        GetUint32Property(env, marginValue, "leftMargin", storage.job.printMargin.leftMargin) &&
        GetUint32Property(env, marginValue, "topMargin", storage.job.printMargin.topMargin) &&
        GetUint32Property(env, marginValue, "rightMargin", storage.job.printMargin.rightMargin) &&
        GetUint32Property(env, marginValue, "bottomMargin", storage.job.printMargin.bottomMargin) &&
        GetStringProperty(env, optionValue, "jobName", storage.jobName) && !storage.jobName.empty() &&
        GetStringProperty(env, optionValue, "paperSource", storage.paperSource) &&
        GetStringProperty(env, optionValue, "mediaType", storage.mediaType) &&
        GetUint32Property(env, optionValue, "printQuality", printQuality) &&
        GetStringProperty(env, optionValue, "documentFormat", documentFormat) &&
        GetBooleanProperty(env, optionValue, "borderless", borderless) &&
        GetStringProperty(env, optionValue, "advancedOptions", storage.advancedOptions);
    if (!valid || storage.job.copyNumber == 0 || printQuality < PRINT_QUALITY_DRAFT ||
        printQuality > PRINT_QUALITY_HIGH || colorMode > COLOR_MODE_AUTO ||
        duplexMode > DUPLEX_MODE_TWO_SIDED_SHORT_EDGE || orientationMode > ORIENTATION_MODE_NONE) {
        return false;
    }
    storage.job.fdList = storage.fdList.data();
    storage.job.fdListCount = static_cast<uint32_t>(storage.fdList.size());
    storage.job.printerId = storage.printerId.data();
    storage.job.jobName = storage.jobName.data();
    storage.job.paperSource = storage.paperSource.empty() ? nullptr : storage.paperSource.data();
    storage.job.mediaType = storage.mediaType.empty() ? nullptr : storage.mediaType.data();
    storage.job.pageSizeId = storage.pageSizeId.data();
    storage.job.colorMode = static_cast<Print_ColorMode>(colorMode);
    storage.job.duplexMode = static_cast<Print_DuplexMode>(duplexMode);
    storage.job.resolution = {dpi, dpi};
    storage.job.borderless = borderless;
    storage.job.orientationMode = static_cast<Print_OrientationMode>(orientationMode);
    storage.job.printQuality = static_cast<Print_Quality>(printQuality);
    storage.job.documentFormat = ParseDocumentFormat(documentFormat);
    storage.job.advancedOptions = storage.advancedOptions.empty() ? nullptr : storage.advancedOptions.data();
    return true;
}
```

`Print_PrintJob` 中的字符串指针指向 `PrintJobStorage` 的字符串成员，`fdList` 指向其数组内存。绑定这些指针后，在 C API 返回前保持 `storage` 存活且不修改相应字符串或数组，避免地址失效。`storage.fdList` 仅保存描述符数值，不负责关闭文件；文件由 ArkTS 调用方持有并在接口返回后的 `finally` 中关闭。参数转换辅助函数及 MIME 类型映射见完整 Sample 的 [napi_init.cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp)。

步骤2：在Native层构造打印任务并下发。

<!-- @[print_native_start_job_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
napi_value NativeStartPrintJob(napi_env env, napi_callback_info info)
{
    napi_value args[PRINT_JOB_ARGUMENT_COUNT] = {nullptr};
    if (!GetPrintArguments(env, info, PRINT_JOB_ARGUMENT_COUNT, args)) {
        return CreateInt32(env, PRINT_ERROR_INVALID_PARAMETER);
    }
    PrintJobStorage storage;
    if (!BuildPrintJob(env, args[ARG_FIRST], args[ARG_SECOND], args[ARG_THIRD], args[ARG_FOURTH], storage)) {
        return CreateInt32(env, PRINT_ERROR_INVALID_PARAMETER);
    }
    return CreateInt32(env, OH_Print_StartPrintJob(&storage.job));
}
```

步骤3：ArkTS侧使用 `createPrintRequest` 将页面设置组合成请求。所用 [PrintModels.ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/print/model/PrintModels.ets) 实现了 `.d.ts` 中的类型，Native层从下列四组字段中读取对应数据。

| 请求字段 | 来源及 Native 用途 |
| --- | --- |
| `printJob` | 当前文件fd、已连接打印机ID、份数、颜色、单双面及方向；模型提供分辨率 |
| `pageSize` | 当前所选纸张；Native层使用其 `id` 填写 `pageSizeId` |
| `margin` | 页面四边边距，经 `parseMargin` 转为非负整数后填写 `printMargin` |
| `option` | 所选文件格式、质量、无边距等；模型补齐作业名及其他字段 |

<!-- @[print_native_request_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
private createPrintRequest(fd: number): PrintRequest {
  const margin: MarginModel = new MarginModel(this.parseMargin(this.leftMargin),
    this.parseMargin(this.topMargin), this.parseMargin(this.rightMargin), this.parseMargin(this.bottomMargin));
  const printJob: PrintJobModel = new PrintJobModel(fd, this.selectedPrinter.printerId, this.copyNumber,
    this.colorMode, this.duplexMode, this.orientationMode);
  const option: PrintOptionModel = new PrintOptionModel(this.selectedDocumentFormat, this.printQuality,
    this.borderless, this.mediaType);
  return new PrintRequest(printJob, this.selectedPageSize, margin, option);
}
```

步骤4：检查是否已选择打印机，在调用期间临时打开文件，并在`finally`中关闭文件描述符。

<!-- @[print_native_start_job_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
private async startDirectPrint(): Promise<void> {
  if (this.selectedPrinter.printerId.length === 0) {
    this.setCodeResult('OH_Print_StartPrintJob', INVALID_PRINTER_ERROR);
    return;
  }
  const context: Context | undefined = this.getContext();
  if (context === undefined) {
    this.setCodeResult('OH_Print_StartPrintJob', 401);
    return;
  }
  let file: fileIo.File | undefined = undefined;
  try {
    file = await PrintFileUtils.openSample(context, this.selectedFileName);
    if (file === undefined) {
      this.operationResult = this.getResourceText($r('app.string.open_file_failed'));
      return;
    }
    const request: PrintRequest = this.createPrintRequest(file.fd);
    const code: number = nativePrint.nativeStartPrintJob(request.printJob, request.pageSize, request.margin,
      request.option);
    this.setCodeResult('OH_Print_StartPrintJob', code);
  } catch {
    this.operationResult = this.getResourceText($r('app.string.open_file_failed'));
  } finally {
    PrintFileUtils.close(file);
  }
}
```

完整Sample还提供`OH_Print_QueryPrinterList()`、`OH_Print_QueryPrinterInfo()`、`OH_Print_QueryPrinterProperties()`、`OH_Print_UpdatePrinterProperties()`、`OH_Print_RestorePrinterProperties()`和`OH_Print_LaunchPrinterManager()`的操作入口。属性的 Key 和 Value 应使用目标打印机及其 Print Extension 支持的值；界面展示接口返回码和查询结果，操作说明见 [Sample README](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/README.md)。

`nativeQueryPrinterProperties` 返回 `PrinterPropertiesResult`：`properties` 始终为数组，无效参数或查询失败时为空数组。调用方应先根据 `code` 判断是否成功；空数组本身不代表查询成功。详情查询的 `printerInfo` 则是可选字段，应遵循 `.d.ts` 中各自的返回结构。

## 状态回调打印

从API 24开始，可以使用`OH_Print_StartPrintWithJobStateCallback()`下发任务并接收 [OH_Print_JobState](../../reference/apis-basic-services-kit/capi-ohprint-h.md#oh_print_jobstate) 状态。它复用直接打印的文件和页面设置，但使用独立的状态枚举：

| 状态值 | 枚举项 | 含义及示例处理 |
| --- | --- | --- |
| 0 | `OH_PRINT_JOB_SUCCEED` | 成功，释放回调资源 |
| 1 | `OH_PRINT_JOB_FAIL` | 失败，释放回调资源 |
| 2 | `OH_PRINT_JOB_CANCEL` | 取消，释放回调资源 |
| 3 | `OH_PRINT_JOB_BLOCK` | 阻塞，保留回调并等待后续状态 |

示例每次只保留一个状态回调任务，使用 `jobId` 关联回调。接口返回0表示本次提交调用成功，任务是否完成需观察上述后续回调；实际出纸还需在目标打印机上确认。页面退出释放服务后，本地状态回调随之结束。

步骤1：在Native层创建线程安全函数，调用带状态回调的打印接口，并在终态释放回调资源。

<!-- @[print_native_job_state_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
void PrintJobStateChanged(const char *jobId, OH_Print_JobState state)
{
    PrintJobStateEventData *data = new PrintJobStateEventData;
    data->jobId = SafeString(jobId);
    data->state = static_cast<uint32_t>(state);
    {
        std::lock_guard<std::mutex> lock(g_printJobStateMutex);
        if (g_printJobStateTsfn == nullptr ||
            napi_call_threadsafe_function(g_printJobStateTsfn, data, napi_tsfn_nonblocking) != napi_ok) {
            delete data;
        }
    }
    if (state != OH_PRINT_JOB_BLOCK) {
        ReleasePrintJobStateTask(napi_tsfn_release);
    }
}

napi_value NativeStartPrintWithJobStateCallback(napi_env env, napi_callback_info info)
{
    napi_value args[PRINT_JOB_STATE_ARGUMENT_COUNT] = {nullptr};
    if (!GetPrintArguments(env, info, PRINT_JOB_STATE_ARGUMENT_COUNT, args) ||
        GetValueType(env, args[ARG_FIFTH]) != napi_function) {
        return CreateInt32(env, PRINT_ERROR_INVALID_PARAMETER);
    }
    PrintJobStorage storage;
    if (!BuildPrintJob(env, args[ARG_FIRST], args[ARG_SECOND], args[ARG_THIRD], args[ARG_FOURTH], storage)) {
        return CreateInt32(env, PRINT_ERROR_INVALID_PARAMETER);
    }
    {
        std::lock_guard<std::mutex> lock(g_printJobStateMutex);
        if (g_printJobStateTsfn != nullptr ||
            !CreateTsfn(env, args[ARG_FIFTH], "PrintJobState", CallPrintJobStateEventJs, g_printJobStateTsfn)) {
            return CreateInt32(env, ERROR_GENERIC);
        }
    }
    Print_ErrorCode code = OH_Print_StartPrintWithJobStateCallback(&storage.job, PrintJobStateChanged);
    if (code != PRINT_ERROR_NONE) {
        ReleasePrintJobStateTask(napi_tsfn_abort);
    }
    return CreateInt32(env, code);
}
```

步骤2：ArkTS侧复用直接打印的参数构造过程，并在回调中处理任务ID和状态。

<!-- @[print_native_job_state_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
private async startPrintWithStateCallback(): Promise<void> {
  if (this.selectedPrinter.printerId.length === 0) {
    this.setCodeResult('OH_Print_StartPrintWithJobStateCallback', INVALID_PRINTER_ERROR);
    return;
  }
  const context: Context | undefined = this.getContext();
  if (context === undefined) {
    this.setCodeResult('OH_Print_StartPrintWithJobStateCallback', 401);
    return;
  }
  let file: fileIo.File | undefined = undefined;
  try {
    file = await PrintFileUtils.openSample(context, this.selectedFileName);
    if (file === undefined) {
      this.operationResult = this.getResourceText($r('app.string.open_file_failed'));
      return;
    }
    const request: PrintRequest = this.createPrintRequest(file.fd);
    const code: number = nativePrint.nativeStartPrintWithJobStateCallback(request.printJob, request.pageSize,
      request.margin, request.option, (event: nativePrint.PrintJobStateEvent): void => {
        this.operationResult = 'OH_Print_StartPrintWithJobStateCallback jobId=' + event.jobId + ', state=' +
          event.state.toString();
      });
    this.setCodeResult('OH_Print_StartPrintWithJobStateCallback', code);
  } catch {
    this.operationResult = this.getResourceText($r('app.string.open_file_failed'));
  } finally {
    PrintFileUtils.close(file);
  }
}
```

## 导出NAPI接口

在模块初始化函数中导出打印服务生命周期、监听、发现、连接、查询、属性操作和三种打印接口。

<!-- @[print_native_napi_exports](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/NativePrintFile/entry/src/main/cpp/napi_init.cpp) -->

``` C++
napi_property_descriptor properties[] = {
    {"nativeInit", nullptr, NativeInit, nullptr, nullptr, nullptr, napi_default, nullptr},
    {"nativeRelease", nullptr, NativeRelease, nullptr, nullptr, nullptr, napi_default, nullptr},
    {"nativeRegisterPrinterChangeListener", nullptr, NativeRegisterPrinterChangeListener, nullptr, nullptr,
        nullptr, napi_default, nullptr},
    {"nativeUnregisterPrinterChangeListener", nullptr, NativeUnregisterPrinterChangeListener, nullptr, nullptr,
        nullptr, napi_default, nullptr},
    {"nativeStartPrinterDiscovery", nullptr, NativeStartPrinterDiscovery, nullptr, nullptr, nullptr, napi_default,
        nullptr},
    {"nativeStopPrinterDiscovery", nullptr, NativeStopPrinterDiscovery, nullptr, nullptr, nullptr, napi_default,
        nullptr},
    {"nativeConnectPrinter", nullptr, NativeConnectPrinter, nullptr, nullptr, nullptr, napi_default, nullptr},
    {"nativeLaunchPrinterManager", nullptr, NativeLaunchPrinterManager, nullptr, nullptr, nullptr, napi_default,
        nullptr},
    {"nativeQueryPrinterList", nullptr, NativeQueryPrinterList, nullptr, nullptr, nullptr, napi_default, nullptr},
    {"nativeQueryPrinterInfo", nullptr, NativeQueryPrinterInfo, nullptr, nullptr, nullptr, napi_default, nullptr},
    {"nativeQueryPrinterProperties", nullptr, NativeQueryPrinterProperties, nullptr, nullptr, nullptr,
        napi_default, nullptr},
    {"nativeUpdatePrinterProperties", nullptr, NativeUpdatePrinterProperties, nullptr, nullptr, nullptr,
        napi_default, nullptr},
    {"nativeRestorePrinterProperties", nullptr, NativeRestorePrinterProperties, nullptr, nullptr, nullptr,
        napi_default, nullptr},
    {"nativeStartPrintByNative", nullptr, NativeStartPrintByNative, nullptr, nullptr, nullptr, napi_default,
        nullptr},
    {"nativeStartPrintJob", nullptr, NativeStartPrintJob, nullptr, nullptr, nullptr, napi_default, nullptr},
    {"nativeStartPrintJobWithDefaultSettings", nullptr, NativeStartPrintJobWithDefaultSettings, nullptr, nullptr,
        nullptr, napi_default, nullptr},
    {"nativeStartPrintWithJobStateCallback", nullptr, NativeStartPrintWithJobStateCallback, nullptr, nullptr,
        nullptr, napi_default, nullptr},
};
napi_define_properties(env, exports, sizeof(properties) / sizeof(properties[0]), properties);
```

## 资源释放

- 打印机列表、打印机详情和属性查询结果在转换为应用自有数据后，分别调用`OH_Print_ReleasePrinterList()`、`OH_Print_ReleasePrinterInfo()`和`OH_Print_ReleasePrinterProperties()`释放。
- 直接打印和状态回调打印仅在调用打印接口期间打开JPEG或PDF文件，接口返回后立即关闭。
- 系统预览打印由Native层通过`dup()`持有PDF源文件描述符；每次布局写入时使用临时副本，写入完成后关闭临时副本。预览会话结束、接口启动失败或打印服务释放时回收持久副本和对应线程安全函数。
- API 24 状态回调在成功、失败、取消时释放，阻塞时保留；接口启动失败或页面退出时也需回收。两种回调应分别按照各自枚举判断，不能共用数值含义。
- 页面退出时按“停止发现、注销监听、释放服务”的顺序清理资源，避免重复进入页面时残留回调或文件描述符。
