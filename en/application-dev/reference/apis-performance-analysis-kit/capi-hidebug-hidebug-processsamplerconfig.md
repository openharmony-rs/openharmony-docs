# HiDebug_ProcessSamplerConfig

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Defines a struct for sampling configuration.

**Since**: 22

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t* tids | Array of thread IDs to sample. A maximum of 10 threads can be sampled at the same time. If the array length exceeds 10, the first 10 threads are sampled.|
| uint32_t size | Length of the array to which **tids** points.|
| uint32_t frequency | Sampling frequency, in Hz. The value ranges from 1 to 200. If the value is out of the range, the default value **100** is used.|
| uint32_t duration | Sampling duration, in ms. The value ranges from 1000 to 10000. If the value is less than 1000, the API call is abnormal. If the value is greater than 10000, 10000 is used.|
| uint32_t reserved | Reserved.|
