# Application Grayscale Error Codes

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @buzhenwang-->
<!--Designer: @tangyyan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=93660783cda81c6a66669c7bc215e6da819f14ee translatedAt=2026-11-16T01:09:03.776Z pushedAt=2026-11-20T07:28:30.346Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 36000001

**Message**

Initialization error. Possibly caused by invoking this function before invoking init function.

**Symptom**

An exception occurs during application grayscale initialization.

**Possible causes**

The application grayscale initialization is not complete.

**Solution**

Before calling this API, call the [hiRetrieval.init()](js-apis-hiretrieval.md#hiretrievalinit) API to complete application grayscale initialization.