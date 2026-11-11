---
kits: ["ArkTS"]
description: "Introduces the modularization debugging tools provided by the ArkTS runtime, including module loading chain debugging, circular dependency detection, and modularization trace instrumentation, to help developers locate module loading exceptions and performance issues."
keywords: [ArkTS, modularization debugging, loading chain, circular dependency, trace instrumentation, module loading exception, performance analysis, debugging tool]
doctype: guide
status: active
---

# Modularization Debugging Tools
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @li-jiangfeng-->
<!--Designer: @li-jiangfeng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-02T14:09:34.717Z pushedAt=2026-11-03T03:55:41.781Z nl=1 -->

The ArkTS runtime provides a variety of modularization debugging tools to help developers quickly locate and resolve modularization-related issues.

| Tool Name | Main Function | Applicable Scenarios | API Version |
|---------|---------|---------|---------|
| [Module Loading Trace Debugging Tool](#module-loading-trace-debugging-tool)| Records the module loading path | Module loading exceptions, module loading path analysis |26.0.0|
| [Circular Dependency Detection Tool](#circular-dependency-detection-tool) | Detects module circular dependencies and records the circular dependency chain | Circular dependency locating, module initialization exception analysis |26.1.0|
| [Modular Trace Instrumentation Tool](#modular-trace-instrumentation-tool) | Analyzes module performance and collects usage statistics | Performance analysis, performance optimization |26.0.0|

## Module Loading Trace Debugging Tool
When an app crashes due to an exception during the module loading phase, or when developers want to obtain the module call trace, they can use this feature to quickly locate the problematic module and its call path. It is especially suitable for fault diagnosis in multi-level nested import scenarios.

### Enabling and Disabling

Enabling the tool: When a JsCrash or CppCrash occurs during the module loading phase of an app, you can enable this feature. Once enabled, the crash log records the complete module loading trace, helping you locate the source of the problem.
```bash
# Enable the module loading chain debugging feature.
hdc shell param set persist.ark.properties 0x40000105c
```

Disabling the tool: This feature continuously records module loading information, which incurs a certain runtime performance overhead. Therefore, after the issue is located and fixed, disable it immediately to avoid affecting the normal running performance of the app.
```bash
# Disable the module loading chain debugging feature.
hdc shell param set persist.ark.properties 0x0000105c
```

### Stack Data Format

After the module loading trace debugging feature is enabled, the module loading trace information is displayed in JsCrash and CppCrash crash logs.

**JsCrash log example:**

After the module loading trace debugging feature is enabled, the `ModuleImportStack` field is added to the JsCrash crash log.
```text
...
Stacktrace:
    at anonymous entry (entry/src/main/ets/pages/Index.ets:7:13)
HybridStack:
...
AsyncStack:
...
ModuleImportStack:
#0 entry/src/main/ets/pages/Index.ets
#1 entry/src/main/ets/utils/Helper.ets
#2 entry/src/main/ets/core/Core.ets

HiLog:
...
```

**CppCrash log example:**

After the Module Loading Trace Debugging feature is enabled, the module call chain is displayed in the LastFatalMessage field of the CppCrash crash log.
```text
...
LastFatalMessage:Failed to load &entry/src/main/ets/pages/A&, the dependency import call stack is as follows
#0 &entry/src/main/ets/pages/A&
#1 &entry/src/main/ets/pages/Index&
Fault thread info:
...
```

> **NOTE**
> 
> The Module Loading Trace Debugging feature prints a maximum of 64 KB of content. For scenarios with deep nesting, CppCrash and JsCrash omit the intermediate stack frames.

```text
ModuleImportStack:
#000 entry/src/main/ets/pages/Index.ets
#001 entry/src/main/ets/utils/Helper.ets
...
#999 entry/src/main/ets/deep/Module99.ets
```
### Using JsCrash to Trace the Module Loading Path
To quickly locate the module import chain that causes a problem, developers can throw a JsError at the top level of the problematic module. For example, after throwing an exception at the top level of module B, developers can view the module loading chain when they enable the tool and reproduce the scenario.
```js
// entry/src/main/ets/pages/Index.ets
import { A } from './A'

A()
```
```js
// entry/src/main/ets/pages/A.ets
import { b } from "./B"

export function A(){
  return b + 2;
}
```
```js
// entry/src/main/ets/pages/B.ets
// Throw the exception at the top level, not inside a function.
throw new Error("ModuleImportStack test")
export const b = 1;
```
Example output:
```text
ModuleImportStack:
#0 &entry/src/main/ets/pages/B&
#1 &entry/src/main/ets/pages/A&
#2 &entry/src/main/ets/pages/Index&
```
### Tracing the ETS Import Source of a Shared Object (.so) Module
To quickly locate the loading trace of the shared object (.so) module that causes the problem, developers can throw a CppCrash in the napi_init of the problematic .so module. For example, dereference a null pointer in napi_init.cpp to trigger a CppCrash. After enabling the tool and reproducing the scenario, developers can see from which ETS file the libentry.so module is imported.
```js
// entry/src/main/ets/pages/Index.ets
import { a } from './A'
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
hilog.info(DOMAIN, 'testTag', 'ModuleImportStack test a = %{public}d', a);
```
```js
// entry/src/main/ets/pages/A.ets
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';

const DOMAIN = 0x0000;
hilog.info(DOMAIN, 'testTag', 'Test NAPI 2 + 3 = %{public}d', testNapi.add(2, 3));
export const a = 1;
```
```cpp
// entry/src/main/cpp/napi_init.cpp
EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        { "add", nullptr, Add, nullptr, nullptr, nullptr, napi_default, nullptr }
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    // Throw a null pointer in the file where the call chain needs to be known to trigger CppCrash.
    int *p = nullptr;
    *p = 42;
    return exports;
}
EXTERN_C_END
```
Example output:
```text
LastFatalMessage:Failed to load &entry/src/main/ets/pages/A&, the dependency import call stack is as follows
#0 &entry/src/main/ets/pages/A&
#1 &entry/src/main/ets/pages/Index&
```  

## Circular Dependency Detection Tool

When an application has complex module dependency relationships, or when exceptions such as uninitialized module variables occur, you can use the circular dependency detection tool to help locate the modules involved in circular imports and their dependency chains. After the tool detects a circular dependency, it records the names of the modules involved in the cycle and the module loading chain to a file, without interrupting the application's running.

### Enabling and Disabling

Enable the tool:

```bash
# Enable the circular dependency detection feature
hdc shell param set persist.ark.properties 0x40000105c
```

Disable the tool: During circular dependency detection, module loading information is continuously recorded, which causes a certain performance overhead at runtime. After the issue is located, disable this feature in a timely manner.

```bash
# Disable the circular dependency detection feature
hdc shell param set persist.ark.properties 0x0000105c
```

> **Note:**
>
> The circular dependency detection tool and the module loading chain debugging tool share the same switch. After the circular dependency detection feature is enabled, the module loading chain debugging feature is also enabled at the same time.

### Viewing Detection Results
After enabling the tool and reproducing the issue, you can view the detection result files in the `data/app/el2/100/base/<bundleName>/files/` directory of the app sandbox. The file name format is as follows:

```text
<bundleName>_<pid>_circularImport.txt
```

When a circular dependency occurs in a Worker thread, the file name also contains the thread ID:

```text
<bundleName>_<tid>_<pid>_circularImport.txt
```

Example of detection results:

```text
circular Module Name: &entry/src/main/ets/pages/B&
ModuleImportStack:
#0 &entry/src/main/ets/pages/B&
#1 &entry/src/main/ets/pages/C&
#2 &entry/src/main/ets/pages/B&
#3 &entry/src/main/ets/pages/Index&
```

`circular Module Name` indicates the module detected with circular import. `ModuleImportStack` records the module loading call chain, and `#0` indicates the module currently being loaded. The same module appearing repeatedly in the chain indicates that the module is involved in a circular dependency. Developers can adjust the code structure based on the dependency relationships between the repeated modules to eliminate circular imports.

> **NOTE**
>
> - Detection results are appended to the file. When reproducing the issue multiple times, it is recommended to clear historical results first to avoid confusion between records from different runs.
> - A circular dependency does not necessarily cause an app exception immediately, but it may complicate the module initialization order. It is recommended to determine the impact scope based on the exception information and business code.

## Modular Trace Instrumentation Tool

Developers can use this switch when they need to analyze the performance of file loading scenarios.  

### How to Use

Enabling and disabling the tool: When an app needs to analyze file loading performance, you can enable this feature. After it is enabled, the captured trace data displays modular instrumentation, which helps analyze performance issues. This feature continuously instruments modules and causes a certain performance overhead at runtime. Therefore, you can disable it after capturing the trace to avoid affecting the normal running performance of the app.
```bash
# Enable the modularization instrumentation feature
hdc shell param set persist.ark.properties 0x100105c
# Disable the modularization instrumentation feature
hdc shell param set persist.ark.properties 0x000105c
```

Use HiSmartPerf to capture traces:  

> **NOTE**  
>  
> HiSmartPerf is a standalone performance tuning tool used to collect system, CPU, and GPU performance data during a test period. It presents the data through a visual interface, making it easier for developers to analyze the runtime performance of the app under development and identify the causes, so that they can perform in-depth performance optimization and make the app run more smoothly.
>
> For a complete introduction to HiSmartPerf, see the guide: [HiSmartPerf](https://developer.huawei.com/consumer/en/doc/AppGallery-connect-Guides/smartperf-tool-0000001873208929).

1. Enter CPU Trace.

   Open the HiSmartPerf tool and go to the CPU Trace page for game performance analysis. Although the page is titled game performance analysis, the analysis scenarios are not limited to game scenarios.
  

2. Configure the collection duration and start collection.

   After collection is complete, you will be prompted to transfer the file back. Please wait patiently if the file is large.
   

3. Open the trace file and select the app to view.
  

### Trace File Analysis

The instantiated files and shared object (.so) modules are under SourceTextModule::Instantiate.   
 

The executed files and shared object (.so) modules are under SourceTextModule::Evaluate.  
   

After you select the area to analyze, a table is generated below. You can use the table data to optimize the performance of files that take a long time.  

