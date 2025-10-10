# GPU/CPU Memory Access Sync (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang; @li_hui180; @dingpy-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
## Scenario Introduction

NativeFence is a module that provides **synchronization management fenceFd**. You can use the `NativeFence` API to block fenceFd for a specified period of time, block fenceFd permanently, close fenceFd, and check whether fenceFd is valid.

## Available APIs

| Name| Description|
| -------- | -------- |
| OH_NativeFence_IsValid (int fenceFd) | Checks whether **fenceFd** is valid.|
| OH_NativeFence_Wait (int fenceFd, uint32_t timeout) | Blocks the input fenceFd. The maximum blocking time is determined by the timeout parameter.|
| OH_NativeFence_WaitForever (int fenceFd) | Permanently blocks the input fenceFd.|
| OH_NativeFence_Close (int fenceFd) | Closes **fenceFd**.|

For details about the APIs, see [NativeFence](../reference/apis-arkgraphics2d/capi-nativefence.md).

## How to Develop

The following describes how to use the Native API provided by `NativeFence`.

**Adding dynamic link libraries**

Add the following library to **CMakeLists.txt**.
```txt
libnative_fence.so
```

**Including header files**
```c++
#include <native_fence/native_fence.h>
#include <cstring>
#include <iostream>
#include <linux/sync_file.h>
#include <signal.h>
#include <sys/signalfd.h>
#include <unistd.h>
```
1. **Create fenceFd through signalfd.**
    ```c++
    sigset_t mask;
    sigemptyset(&mask);
    sigprocmask(SIG_BLOCK, &mask, NULL);

    int fenceFd = signalfd(-1, &mask, 0);
    ```

2. **Check whether the input fenceFd is valid.**
    ```c++
    //Check whether fenceFd is valid.
    bool isValid = OH_NativeFence_IsValid(fenceFd);
    if (!isValid) {
        std::cout << "fenceFd is invalid" << std::endl;
    }
    ```

3. **Call the OH_NativeFence_Wait blocking API.**
    ```c++
    constexpr uint32_t TIMEOUT_MS = 5000;
    bool resultWait = OH_NativeFence_Wait(fenceFd, TIMEOUT_MS);
    if (!resultWait) {
        std::cout << "OH_NativeFence_Wait Failed" << std::endl;
    }
    ```

4. **Call the OH_NativeFence_WaitForever blocking API.**
    ```c++
    bool resultWaitForever = OH_NativeFence_WaitForever(fenceFd);
    if (!resultWaitForever) {
        std::cout << "OH_NativeFence_WaitForever Failed" << std::endl;
    }
    ```

5. **Trigger a signal on the GPU or CPU to notify fenceFd of unblocking.**

6. **Close fenceFd.**
    ```c++
    OH_NativeFence_Close(fenceFd);
    ```
