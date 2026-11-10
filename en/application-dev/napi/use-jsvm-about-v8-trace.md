---
kits: ["ArkTS Kit"]
description: "How to collect and parse JSVM traces with HiSmartPerf, including enabling web.debug.rcs, capturing traces with hitrace, and filtering RCS_-prefixed events by categories such as compile, runtime, and builtin."
keywords: [HiSmartPerf, JSVM trace, hitrace, web.debug.rcs, RCS prefix, trace points, performance optimization]
doctype: guide
status: active
---

# Using HiSmartPerf to Collect JSVM Trace
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=1bcf41641a10f17d0f56bfc82362dc9488eaf7eb translatedAt=2026-11-09T08:52:17.340Z nl=1 -->

## Overview

JSVM trace is a tool provided by the JSVM engine for analyzing and debugging the execution process of JavaScript code. It records and outputs detailed information about code execution, including function calls, execution time, and memory usage, helping you understand code performance, diagnose potential problems, and optimize code.

Currently, HiSmartPerf supports trace points of the **compile**, **runtime**, **builtin**, and **JS_Execution** types in JSVM. You can view information about events of these types in HiSmartPerf.

## How to Use

### Default State
JSVM trace collection is controlled by the **web.debug.rcs** switch, which is disabled by default. When a web page is started, "RCS is off" is displayed in HiLog.

### Collecting JSVM Trace
1. To collect JSVM trace, you need to enable **web.debug.rcs** before starting the web page. Run the following command before starting the web page:

   ``` shell
   hdc shell setenforce 0
   hdc shell param set web.debug.rcs true
   ```
2. When a web page is started, "RCS is on" is displayed in HiLog.
3. Use hitrace to capture traces of the corresponding scenario. For details about how to use hitrace, see [hitrace](../dfx/hitrace.md).
4. Use HiSmartPerf to parse the captured traces. The trace points prefixed with **RCS_** are supported by HiSmartPerf.
5. To view the trace data of **compile**, **runtime**, **builtin**, and **JS_Execution**, use the following keywords to filter the data:
   - **compile**: **RCS_v8.compile**
   - **runtime**: **RCS_V8.Runtime**
   - **builtin**: **RCS_v8.runtime_V8.Builtin**
   - **JS_Execution**: **RCS_JS_Execution**
