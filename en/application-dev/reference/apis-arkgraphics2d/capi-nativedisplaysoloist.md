# NativeDisplaySoloist

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @wh_qwe-->
<!--Designer: @wh_qwe-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=ccdbec13380fdf227c4a20f5bde9cc05c16badee translatedAt=2026-08-24T09:16:36.961Z pushedAt=2026-08-31T11:56:59.222Z -->

## Overview

NativeDisplaySoloist is a native-side module used to implement frame rate control in an independent thread. This module allows developers to precisely control the frame generation cadence in an independent thread, making it suitable for scenarios that require high-performance graphics rendering. With this module, developers can implement custom frame scheduling logic to meet the requirements of different scenarios.

**Since**: 12

## Files

| Name| Description|
| -- | -- |
| [native_display_soloist.h](capi-native-display-soloist-h.md) | Declares the functions for obtaining and using native display soloist.|