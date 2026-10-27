# ChildProcess

## Overview

The module provides APIs to manage child processes. You can call the APIs to create a native child process and establish an IPC channel between the parent and child processes to implement multi-process application development. The created child process does not support the UI or the calling of context-related APIs. A maximum of 512 child processes can be started through this module and childProcessManager, and the child processes started by childProcessManager in SELF_FORK mode are not counted toward the total.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 12

## Files

| Name | Description |
| -- | -- |
| [native_child_process.h](capi-native-child-process-h.md) | This module supports creating Native child processes and establishing IPC channels between parent and child processes. It is applicable to various scenarios where time-consuming tasks, high-risk operations, or independent business logic need to be isolated into independent processes. This module provides core capabilities such as process isolation, IPC communication, and flexible configuration, which can effectively improve application stability and security and prevent the main process from being blocked or crashing. Through the child process mechanism, developers can implement a multi-process architecture to run compute-intensive tasks, media processing, network requests, and other services independently, thereby improving application responsiveness and user experience.<br> A maximum of 512 child processes can be started through this module and childProcessManager (non-SELF_FORK mode).<br> **File to include:** <AbilityKit/native_child_process.h><br> ## Constraints<br> ### Functional Limitations<br> - The created child process does not support creating a UI. - The created child process does not support API calls that depend on Context (including the APIs of the Context module itself and APIs that take a Context instance as an input parameter). - Child processes can be created only in the main process. Creating a child process within a child process is not supported.<br> ### Specification Limits<br> - The total number of child processes started through the child process creation interfaces defined in this module and the child process creation interfaces defined in childProcessManager is up to 512 (when system resources are sufficient). Among them, child processes started by the startChildProcess interface in SELF_FORK mode are not counted in the total. |
