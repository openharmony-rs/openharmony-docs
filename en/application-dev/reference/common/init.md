# Init

<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @liveery-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=69652f17f0f35470200a92ce8bbafe60f757e6a7 translatedAt=2026-08-27T03:50:17.184Z pushedAt=2026-08-27T06:58:59.919Z -->

## Overview

Provides the API for querying the support for a SystemCapability (SysCap), which refers to a standalone feature in the operating system. Different devices support different SysCap sets. Each SysCap corresponds to one or more APIs.

The result is returned after the SysCap configuration file is checked.

**Since:** 8

## File Summary

| Name| Description| 
| -------- | -------- |
| [syscap_ndk.h](syscap__ndk_8h.md) | Provides the API for querying whether a SysCap is supported.<br>**File to include**: <syscap_ndk.h><br>**Library**: libdeviceinfo_ndk.z.so| 

### Functions

| Name| Description|
| -------- | -------- |
| [canIUse](syscap__ndk_8h.md#caniuse) (const char \*cap) | Queries whether the specified system capability is supported. A SysCap refers to each relatively independent feature in the operating system. Different devices correspond to different system capability sets, and each system capability corresponds to one or more APIs. Developers can determine whether an API can be used based on the system capability. |