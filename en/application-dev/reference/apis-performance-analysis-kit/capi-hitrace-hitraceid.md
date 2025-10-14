# HiTraceId

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @qq_437963121-->
<!--Designer: @kutcherzhou1; @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Defines a **HiTraceId** instance.

**Since**: 12

**Related module**: [HiTrace](capi-hitrace.md)

**Header file**: [trace.h](capi-trace-h.md)

## Summary

### Member Variables

If the little endian mode is used, the structure sequence is as follows:

| Field| Number of Bits| Description|
| -------- | -------- | -------- |
| uint64_t valid | 1 | Whether a **HiTraceId** instance is valid.|
| uint64_t ver | 3 | Version number of **HiTraceId**.|
| uint64_t chainId | 60 | Trace chain ID of HiTraceId.|
| uint64_t flags | 12 | Trace flag of HiTraceId.|
| uint64_t spanId | 26 | Span ID of HiTraceId.|
| uint64_t parentSpanId | 26 | Parent span ID of HiTraceId.|

If the byte order is big endian, the structure sequence is as follows:

| Field| Number of Bits| Description|
| -------- | -------- | -------- |
| uint64_t chainId | 60 | Trace chain ID of HiTraceId.|
| uint64_t ver | 3 | Version number of **HiTraceId**.|
| uint64_t valid | 1 | Whether a **HiTraceId** instance is valid.|
| uint64_t parentSpanId | 26 | Parent span ID of HiTraceId.|
| uint64_t spanId | 26 | Span ID of HiTraceId.|
| uint64_t flags | 12 | Trace flag of HiTraceId.|
