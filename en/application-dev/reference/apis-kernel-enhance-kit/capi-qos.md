# QoS
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=84e5c687623c619df721fa927b62d6782396d98d translatedAt=2026-11-04T01:24:55.372Z pushedAt=2026-11-04T03:24:28.473Z nl=1 -->

## Overview

This module provides QoS (Quality of Service) APIs for setting, canceling, and querying the QoS level of a thread, thereby affecting the system's scheduling priority and resource allocation for the thread. It also provides C APIs related to the Gewu Service (on-device AI inference acceleration service) for on-device inference session management. QoS is applicable to scenarios where critical tasks must be distinguished from ordinary tasks by priority and the response performance of critical tasks must be improved, such as real-time audio and video processing, game rendering, and user interaction response. QoS implements priority control by adjusting the thread scheduling policy. For details about the APIs, see [qos.h](capi-qos-h.md).

**Since**: 12
## Files

| Name| Description|
| -- | -- |
| [qos.h](capi-qos-h.md) | Declares the C APIs related to QoS and Gewu Service. |
