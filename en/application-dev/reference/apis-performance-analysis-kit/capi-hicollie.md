# HiCollie

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=af38d625c1d34891902382d10d5522cf91cb53e5 translatedAt=2026-09-21T02:26:08.533Z pushedAt=2026-09-22T01:29:30.370Z -->

## Overview

Provides the capability to detect business thread stuck and jank events, and to report stuck events. The functions of this module support the following:<br>(1) Register a periodic detection task for application business thread stuck.<br>(2) Register a callback function for application business thread jank detection.<br>(3) Report application business thread stuck events.<br> Use scenarios: locating application jank issues, monitoring thread health status, diagnosing stuck issues during development and debugging, and collecting and analyzing jank data.

**Since**: 12

**System capability**: SystemCapability.HiviewDFX.HiCollie

## Files

| Name| Description|
| -- | -- |
| [hicollie.h](capi-hicollie-h.md) | The HiCollie module provides the capability to detect stuck and jank of business threads, and report stuck events. |
