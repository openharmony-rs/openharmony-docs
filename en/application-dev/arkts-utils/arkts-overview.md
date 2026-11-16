# About This Kit

<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @Malzahar-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-11-04T09:05:04.333Z pushedAt=2026-11-04T09:34:24.234Z nl=1 -->

ArkTS is the official high-level language for OpenHarmony application development.

Built on the [TypeScript](https://www.typescriptlang.org/) (TS) ecosystem, ArkTS extends its functionality while maintaining the basic style of TS. It enhances static check and analysis during development through standardized definitions, improving code robustness and achieving better program execution stability and performance. For details about the differences compared with standard TS, see [TypeScript to ArkTS Cookbook](../quick-start/typescript-to-arkts-migration-guide.md). ArkTS also supports efficient interoperability with TS/JavaScript (JS).

The ArkTS basic class library and container class library enhance the basic capabilities of the language, providing features such as the [high-precision math library Decimal](../reference/apis-arkts/js-apis-arkts-decimal.md), [Buffer and FastBuffer](buffer.md), [XML Overview](xml-overview.md), and various container libraries, helping developers simplify development and improve efficiency.

To address the limited concurrency support in TS/JS, ArkTS enhances concurrency programming APIs and capabilities. It provides two concurrency APIs, [TaskPool](taskpool-introduction.md) and [Worker](worker-introduction.md). In addition, ArkTS introduces the concept of Sendable to support object reference passing between concurrent instances, improving communication performance of ArkTS objects in concurrent environments.

ArkCompiler supports the compilation and execution of ArkTS, TS, and JS. Currently, it is divided into two main parts: the ArkTS compilation toolchain and the ArkTS runtime. The ArkTS compilation toolchain is responsible for compiling high-level languages into Ark bytecode files (\*.abc), whereas the ArkTS runtime runs the bytecode files on the device side to execute the program logic.

In the future, ArkTS will continue to evolve based on application development and runtime requirements, gradually introducing more features such as enhanced concurrency capabilities, enhanced system types, and distributed development paradigms.

<!--RP1-->
<!--RP1End-->