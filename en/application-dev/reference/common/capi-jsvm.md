# JSVM
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Provides standard JavaScript engine capabilities. Function description: The standard JavaScript engine is a JavaScript code execution engine that strictly complies with the ECMAScript specification. It supports the standard libraries defined by the ECMAScript specification and provides complete native APIs for interaction between C++ and JavaScript. The standard JavaScript engine accelerates code execution through Just-In-Time (JIT) compilation, providing secure and efficient JavaScript execution capabilities for applications. The capabilities of the standard JS engine are provided through a stable set of application binary interfaces (ABIs), that is, JSVM-API. JSVM-API can be dynamically linked to JS engine libraries of different versions to shield the differences between engine interfaces. JSVM-API provides capabilities such as engine lifecycle management, JavaScript context management, JavaScript code execution, JavaScript/C++ interoperability, execution environment snapshot, and codecache.<br> Platform: ARM64.<br> Usage: Link **libjsvm.so** in the SDK and include the **ark_runtime/jsvm.h** header file in the C++ code.<br>

**Since**: 11
## Files

| Name| Description|
| -- | -- |
| [jsvm.h](capi-jsvm-h.md) | Provides JSVM-API API definitions. Provides independent, standard, and complete JavaScript engine capabilities for developers through APIs, including managing the engine lifecycle, compiling and running JavaScript code, implementing cross-language calling between JavaScript and C++, and taking snapshots.|
| [jsvm_types.h](capi-jsvm-types-h.md) | JSVM-API type definitions. Provides independent, standard, and complete JavaScript engine capabilities for developers through APIs, including managing the engine lifecycle, compiling and running JavaScript code, implementing cross-language calling between JavaScript and C++, and taking snapshots.|
