# AIP Error Codes
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @my-2024-->
<!--Designer: @cuile44; @fysun17; @AnruiWang-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=f357ad4bf8e21ca38a4fe32686c2e588bbe381f6 translatedAt=2026-09-04T03:17:35.933Z pushedAt=2026-09-09T09:11:03.698Z -->

> NOTE
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