# Application Grayscale Error Codes

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @lyj_love_code-->
<!--Designer: @tangyyan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

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

## 36000002 

**Message**

Multi-instance applications not supported error. Possibly caused by invoking this function in a multi-instance application.

**Symptom**

An exception occurs when a multi-instance application calls the [hiRetrieval.init()](js-apis-hiretrieval.md#hiretrievalinit) API. (Currently, this error code is returned only by the **init()** API.)

**Possible causes**

The current version does not support multi-instance applications to call the application grayscale release capability.

**Solution**

Check whether the current application is a [multi-instance application](../../quick-start/multiInstance.md). If the application is a multi-instance application, do not call HiRetrieval APIs.
