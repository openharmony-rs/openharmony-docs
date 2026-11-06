# HiCollie

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=325a101029ad09501d4d8294a812c2f4976c5510 translatedAt=2026-09-16T10:28:42.115Z pushedAt=2026-09-20T09:01:52.236Z -->

## Overview

Provides the capability to detect business thread stuck and jank events, and to report stuck events. The functions of this module support the following:<br>(1) Register a periodic detection task for application business thread stuck.<br>(2) Register a callback function for application business thread jank detection.<br>(3) Report application business thread stuck events.<br> Use scenarios: locating application jank issues, monitoring thread health status, diagnosing stuck issues during development and debugging, and collecting and analyzing jank data.

**Since**: 12

**System capability**: SystemCapability.HiviewDFX.HiCollie

## Files

| Name| Description|
| -- | -- |
| [hicollie.h](capi-hicollie-h.md) | The HiCollie module provides the capability to detect stuck and jank of business threads, and report stuck events. |
