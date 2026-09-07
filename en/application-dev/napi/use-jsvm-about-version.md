# Obtaining the JSVM-API Version Using JSVM-API
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e7d54c65a024645f8f688ed024b0b4059342e5b3 translatedAt=2026-09-01T02:42:33.628Z pushedAt=2026-09-02T06:39:06.794Z -->

## Introduction

This topic walks you through how to use JSVM-API to obtain the JSVM-API version.

## Available APIs

| API                      | Description                      |
|----------------------------|--------------------------------|
| OH_JSVM_GetVersion         | Obtains the latest JSVM API version supported by the JSVM runtime.|
| OH_JSVM_GetVMInfo          | Obtains the VM information.             |

## Example

If you are just starting out with JSVM-API, see [JSVM-API Development Process](use-jsvm-process.md). The following demonstrates only the C++ code involved in using version-related APIs.

### OH_JSVM_GetVersion && OH_JSVM_GetVMInfo

Use **OH_JSVM_GetVersion && OH_JSVM_GetVMInfo** to obtain the latest JSVM API version supported by the current environment and the VM information.

CPP code:

<!-- @[oh_jsvm_get_version_and_vm_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/JSVMAPI/JsvmUsageGuide/UsageInstructionsTwo/getversion/src/main/cpp/hello.cpp) -->

``` C++
// Define OH_JSVM_GetVersion.
static JSVM_Value GetVersion(JSVM_Env env, JSVM_CallbackInfo info)
{
    uint32_t jsVersion = 0;
    // Obtain the latest JSVM API version supported by the current JSVM runtime.
    JSVM_CALL(OH_JSVM_GetVersion(env, &jsVersion));
    int value = static_cast<int>(jsVersion);
    OH_LOG_INFO(LOG_APP, "JSVM GetVersion success:%{public}d", value);
    return nullptr;
}

// Define OH_JSVM_GetVMInfo.
// Print the JSVM information.
void PrintVmInfo(JSVM_VMInfo vmInfo)
{
    OH_LOG_INFO(LOG_APP, "JSVM API apiVersion: %{public}d", vmInfo.apiVersion);
    OH_LOG_INFO(LOG_APP, "JSVM API engine: %{public}s", vmInfo.engine);
    OH_LOG_INFO(LOG_APP, "JSVM API version: %{public}s", vmInfo.version);
    OH_LOG_INFO(LOG_APP, "JSVM API cachedDataVersionTag: 0x%{public}x", vmInfo.cachedDataVersionTag);
}

static JSVM_Value GetVMInfo(JSVM_Env env, JSVM_CallbackInfo info)
{
    // Obtain the VM information.
    JSVM_VMInfo result;
    JSVM_CALL(OH_JSVM_GetVMInfo(&result));
    // Output the VM information.
    PrintVmInfo(result);
    return nullptr;
}

// Register callbacks for GetVersion and GetVMInfo.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = GetVersion},
    {.data = nullptr, .callback = GetVMInfo},
};
static JSVM_CallbackStruct *method = param;
// Aliases for GetVersion and GetVMInfo methods, for JS to call.
static JSVM_PropertyDescriptor descriptor[] = {
    {"getVersion", nullptr, method, nullptr, nullptr, nullptr, JSVM_DEFAULT},
    {"getVMInfo", nullptr, method + 1, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};

// Sample test JS.
static const char *STR_TASK = R"JS(getVersion();getVMInfo();)JS";
```

Expected result:
```txt
JSVM GetVersion success:9
JSVM API apiVersion: 1
JSVM API engine: v8
JSVM API version: 13.2.152.41
JSVM API cachedDataVersionTag: 0x81ff9402
```
