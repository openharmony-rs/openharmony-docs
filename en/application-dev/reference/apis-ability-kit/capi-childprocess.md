# ChildProcess
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b64fba1a3bfa56ac6a22a458a141c3f45d9c160b translatedAt=2026-09-03T08:40:03.384Z pushedAt=2026-09-05T10:47:30.091Z -->

## Overview

The module provides APIs to manage child processes. You can call the APIs to create a native child process and establish an IPC channel between the parent and child processes to implement multi-process application development.

The created child process does not support the UI or the calling of context-related APIs. A maximum of 512 child processes can be started through this module and [childProcessManager](js-apis-app-ability-childProcessManager.md), and the child processes started by childProcessManager in SELF_FORK mode are not counted toward the total.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 12

## Files

| Name| Description|
| -- | -- |
| [native_child_process.h](capi-native-child-process-h.md) | Declares the APIs used to create a native child process and establish an IPC channel between the main process and child process.<br>File to include: <AbilityKit/native_child_process.h><br>Library: libchild_process.so|
