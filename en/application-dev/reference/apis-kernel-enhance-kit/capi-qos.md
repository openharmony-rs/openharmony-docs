# QoS
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->

## Overview

This module provides Quality of Service (QoS) APIs for setting, canceling, and querying thread QoS levels, thereby affecting the system's scheduling priority and resource allocation for threads. It also provides C APIs related to the Gewu service (on-device AI inference acceleration service) for inference session management on the device side. QoS is applicable to scenarios where it is necessary to distinguish the priority of critical tasks from that of ordinary tasks and improve the response performance of critical tasks, such as real-time audio/video processing, game rendering, and user interaction response. QoS achieves priority control by adjusting thread scheduling policies. For details about the API description, please refer to [qos.h](capi-qos-h.md).

**Since**: 12
## Files

| Name| Description|
| -- | -- |
| [qos.h](capi-qos-h.md) | Declares the C APIs related to QoS and Gewu service.|
