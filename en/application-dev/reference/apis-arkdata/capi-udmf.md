# UDMF
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=0fca7c152f15931be356eaaefd37fcbd0f832eea translatedAt=2026-09-04T03:09:20.275Z pushedAt=2026-09-09T09:11:03.689Z -->

## Overview

The Unified Data Management Framework (UDMF) defines standards for data management across applications, devices, and platforms, and provides a unified OpenHarmony data language and standard data access channels.

**Since**: 12

## Files

| Name                                      | Description                                                        |
| ------------------------------------------ | ------------------------------------------------------------ |
| [udmf.h](capi-udmf-h.md)                   | Provides the APIs, data structures, and enums for accessing the data of the UDMF. When the parameter type is char*, the string must end with a null character ('\0'); otherwise, undefined behavior or a function error may occur. |
| [udmf_err_code.h](capi-udmf-err-code-h.md) | Declares the error code definitions and error descriptions of the UDMF. |
| [udmf_meta.h](capi-udmf-meta-h.md)         | Declares the unified data type information.  |
| [uds.h](capi-uds-h.md)                     | Provides the APIs and struct definitions related to standardized data structures. When the parameter type is char*, the string must end with a null character ('\0'); otherwise, undefined behavior or a function error may occur. |
| [utd.h](capi-utd-h.md)                     | Provides the APIs and data structures related to standardized data type descriptions. When the parameter type is char*, the string must end with a null character ('\0'); otherwise, undefined behavior or a function error may occur. |

