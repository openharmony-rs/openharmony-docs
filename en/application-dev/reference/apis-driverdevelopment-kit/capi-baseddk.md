# Ddk
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-04T03:38:33.709Z pushedAt=2026-11-04T10:12:49.961Z nl=1 -->

## Overview

Provides BASE DDK APIs for creating, mapping, unmapping, and destroying the shared memory.

**Since**: 12

## Files

| Name| Description|
| -- | -- |
| [ddk_api.h](capi-ddk-api-h.md) | Declares the BASE DDK APIs used by the host and provides APIs for creating, mapping, unmapping, and destroying the shared memory. This module helps you efficiently manage shared memory resources in drivers. It is applicable to scenarios where data needs to be shared with the driver, helping simplify memory management and improve data transmission efficiency. |
| [ddk_types.h](capi-ddk-types-h.md) | Provides BASE DDK types and declares enums and data structures required by the BASE DDK APIs. |
