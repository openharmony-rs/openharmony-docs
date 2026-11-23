# AIP Error Codes
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @my-2024-->
<!--Designer: @cuile44; @fysun17; @AnruiWang-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b3d483b49d1071ea35ea7373cd3db3058b2f8c7a translatedAt=2026-11-16T01:45:27.537Z pushedAt=2026-11-20T07:27:28.559Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 31300000 Internal Error

**Error Message**

Inner error.

**Description**

This error code is reported when an internal service exception occurs while calling APIs of the smart data platform module, for example, a model fails to be loaded occasionally due to high memory usage or high CPU load.

**Possible Causes**

1. The application does not load the corresponding embedding model.
2. Memory allocation fails.

**Solution**

1. Before using the APIs related to the vectorization capability, ensure that the corresponding model resources are loaded.
2. For issues such as high memory usage and CPU load, retry the operation. If the problem persists, prompt the user to restart the application, upgrade the application, or upgrade the device version.