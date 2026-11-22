# Ddk
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=6be4fce6dcc641d6f56c59a16ae6449540255825 translatedAt=2026-10-14T04:35:08.738Z pushedAt=2026-10-19T06:28:16.845Z -->

## Overview

Provides BASE DDK APIs for creating, mapping, unmapping, and destroying the shared memory.

**Since**: 12

## Files

| Name| Description|
| -- | -- |
| [ddk_api.h](capi-ddk-api-h.md) | Declares the BASE DDK APIs used by the host and provides APIs for creating, mapping, unmapping, and destroying the shared memory. This module helps you efficiently manage shared memory resources in drivers. It is applicable to scenarios where data needs to be shared with the driver, helping simplify memory management and improve data transmission efficiency. |
| [ddk_types.h](capi-ddk-types-h.md) | Provides BASE DDK types and declares enums and data structures required by the BASE DDK APIs. |
