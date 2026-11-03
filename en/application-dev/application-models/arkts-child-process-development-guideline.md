# Child Process Development Guide (ArkTS)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=d8d5f4c1f966c7814e24a47d5d7dfb3a096abfae translatedAt=2026-11-02T13:26:41.964Z pushedAt=2026-11-03T08:04:20.446Z nl=1 -->

## Overview

In multitasking scenarios, developers often face issues such as an overloaded main process and tasks blocking the UI thread. The child process mechanism allows an application to create independently running child processes, isolating time-consuming tasks, data processing, and other business logic into child processes for execution, thereby improving the application's responsiveness and stability. This module provides a way to create child processes through the ArkTS API. For the interface selection and capability differences among the three creation methods, see [Child Process Creation Method Selection](#child-process-creation-method-selection).

> **Note:**
>
> The created child process exits when the parent process exits and cannot run independently of the parent process.

## Child Process Creation Method Selection

| Comparison Item | Creating a Basic ArkTS Child Process | Creating an ArkTS Child Process with Parameter Passing | Create a Native Child Process with Parameter Passing Support |
| --- | --- | --- | --- |
| Involved Interface | [startChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess) | [startArkChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartarkchildprocess12)<sup>12+</sup> | [startNativeChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartnativechildprocess13)<sup>13+</sup> |
| Applicable Scenarios | Suitable for lightweight ArkTS background tasks that do not require parameter passing, such as local log archiving, configuration parsing, and startup-phase data preprocessing. | Suitable for ArkTS tasks that require parameter passing or long-running execution, such as receiving a file fd for document or image parsing, and performing long-running data processing based on parameters. | Suitable for high-performance C/C++ computation or reusing existing Native libraries, such as audio/video codec, image processing, and compute-intensive tasks. |
| Child Process Runtime Environment | ArkTS runtime, can call ArkTS APIs | ArkTS runtime, can call ArkTS APIs | C/C++ runtime, no ArkTS runtime |
| Whether Parent Process Resources Are Inherited | Inherited only in SELF_FORK mode, not inherited in APP_SPAWN_FORK mode | Not inherited | Not inherited |
| Whether Binder IPC Is Supported | Not supported in SELF_FORK mode, supported in APP_SPAWN_FORK mode | Supported | Supported |
| Child Process Destruction Method | Automatically destroyed after [onStart](../reference/apis-ability-kit/js-apis-app-ability-childProcess.md#childprocessonstart) finishes execution | Not automatically destroyed; the child process must call [process.abort](../reference/apis-arkts/js-apis-process.md#processabort) to destroy itself | Automatically destroyed after the entry function returns |
| Whether Asynchronous ArkTS APIs Are Supported | Not supported, only synchronous APIs are supported | Supported | Not applicable (the child process is a C/C++ environment) |
| Process Isolation Mode Configuration | Not supported | Supported ([ChildProcessOptions](../reference/apis-ability-kit/js-apis-app-ability-childProcessOptions.md) isolationMode) | Supported ([ChildProcessOptions](../reference/apis-ability-kit/js-apis-app-ability-childProcessOptions.md) isolationMode) |
| Query Whether the Device Supports Child Process Creation | [childProcessManager.isArkChildProcessSupported](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerisarkchildprocesssupported) | [childProcessManager.isArkChildProcessSupported](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerisarkchildprocesssupported) | [childProcessManager.isNativeChildProcessSupported](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerisnativechildprocesssupported) |

> **Note:**
>
> None of the three creation methods above provides an IPC channel between the parent and child processes. The "Whether Binder IPC Is Supported" item in the table only indicates that the child process runtime environment has this capability; it does not mean that the interface itself has exposed a parent-child communication API to the application layer. To implement Binder IPC communication between parent and child processes, directly call the [OH_Ability_CreateNativeChildProcessWithConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_createnativechildprocesswithconfigs) interface.

## Creating a Basic ArkTS Child Process

To create an [ArkTS child process](ability-terminology.md#arkts-child-process) through the [startChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess) interface, you need to define an entry class that inherits [ChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcess.md) and implement the [onStart](../reference/apis-ability-kit/js-apis-app-ability-childProcess.md#childprocessonstart) method. The child process automatically exits after the onStart method finishes execution.


1. Create the child process class.

    Create a child process source file under the entry module, inherit the [ChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcess.md) class, and implement the [onStart](../reference/apis-ability-kit/js-apis-app-ability-childProcess.md#childprocessonstart) method.

    <!-- @[arkts_child_process_noarg_child](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ArkTsChildProcess/entry/src/main/ets/process/DemoProcessNoArg.ets) -->
    
    ``` TypeScript
    import { ChildProcess } from '@kit.AbilityKit';
    
    export default class DemoProcessNoArg extends ChildProcess {
      onStart() {
        console.info('DemoProcess onStart');
        // Implement the child process business logic.
        // ...
      }
    }
    ```

2. Start the child process from the main process.

    In the main process, import the child process class and call [startChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess) to start the child process. Note that the child process class must be referenced in the code to prevent the child process source file from being optimized out by the build tool.

    [startChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess) supports two child process startup modes:
    - **SELF_FORK**: Forks a child process from the app's own process. A child process started in this mode inherits the parent process resources and cannot use Binder IPC to communicate with other processes. Otherwise, the child process will crash and exit.
    - **APP_SPAWN_FORK**: Forks a child process from AppSpawn. A child process started in this mode does not inherit the parent process resources and can use Binder IPC to communicate with other processes.

    After startup, you can search for the "startChildProcess" keyword in HiLog. Viewing the "startChildProcess success, pid: xxx" log indicates that the child process creation is successful. Search for the "DemoProcess onStart" keyword again; viewing that log indicates that the child process entry function has been executed.

    Use a promise to return the result:

    <!-- @[arkts_child_process_noarg_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ArkTsChildProcess/entry/src/main/ets/pages/Index.ets) --> 
    
    ``` TypeScript
    import { childProcessManager } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import DemoProcessNoArg from '../process/DemoProcessNoArg';
    // ...
    @Entry
    @Component
    struct Index {
    
      build() {
        Scroll() {
          Column() {
            Text("StartArkChildProcessNoArg_Promise")
              .fontSize($r('app.float.page_text_font_size'))
              .fontWeight(FontWeight.Bold)
              .alignRules({
                center: { anchor: '__container__', align: VerticalAlign.Center },
                middle: { anchor: '__container__', align: HorizontalAlign.Center }
              })
              .onClick(() => {
                try {
                  DemoProcessNoArg.toString(); // Reference the child process class to prevent it from being optimized away by the build tool.
                  childProcessManager.startChildProcess("./ets/process/DemoProcessNoArg.ets", childProcessManager.StartMode.SELF_FORK)
                    .then((pid) => {
                      console.info(`startChildProcess success, pid: ${pid}`);
                    })
                    .catch((err: BusinessError) => {
                      console.error(`startChildProcess error, errorCode: ${err.code}`);
                    });
                } catch (err) {
                  console.error(`startChildProcess error, errorCode: ${(err as BusinessError).code}`);
                }
              })
    // ...
          }
          .width('100%')
        }
        .height('100%')
      }
    }
    ```

    Use the callback for asynchronous invocation:

    <!-- @[arkts_child_process_noarg_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ArkTsChildProcess/entry/src/main/ets/pages/Index.ets) --> 
    
    ``` TypeScript
    import { childProcessManager } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import DemoProcessNoArg from '../process/DemoProcessNoArg';
    // ...
    @Entry
    @Component
    struct Index {
    
      build() {
        Scroll() {
          Column() {
    // ...
            Text("StartArkChildProcessNoArg_Callback")
              .fontSize($r('app.float.page_text_font_size'))
              .fontWeight(FontWeight.Bold)
              .alignRules({
                center: { anchor: '__container__', align: VerticalAlign.Center },
                middle: { anchor: '__container__', align: HorizontalAlign.Center }
              })
              .onClick(() => {
                try {
                  DemoProcessNoArg.toString(); // Reference the child process class to prevent it from being optimized away by the build tool.
                  childProcessManager.startChildProcess("./ets/process/DemoProcessNoArg.ets", childProcessManager.StartMode.SELF_FORK, (err, data) => {
                    if (data) {
                      console.info(`startChildProcess success, pid: ${data}`);
                    } else {
                      console.error(`startChildProcess error, errorCode: ${err.code}`);
                    }
                  });
                } catch (err) {
                  console.error(`startChildProcess error, errorCode: ${(err as BusinessError).code}`);
                }
              })
    // ...
          }
          .width('100%')
        }
        .height('100%')
      }
    }
    ```

## Creating an ArkTS Child Process with Parameter Passing

To create an ArkTS child process through the [startArkChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartarkchildprocess12) interface, you need to define an entry class that inherits [ChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcess.md), and pass string parameters and fd handles through [ChildProcessArgs](../reference/apis-ability-kit/js-apis-app-ability-childProcessArgs.md). The child process does not exit automatically; you must actively call [process.abort](../reference/apis-arkts/js-apis-process.md#processabort) to destroy it.


1. Create the child process class.

    Create a child process source file under the module, inherit the [ChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcess.md) class, and implement the [onStart](../reference/apis-ability-kit/js-apis-app-ability-childProcess.md#childprocessonstart) method. The parameter of the onStart method is [ChildProcessArgs](../reference/apis-ability-kit/js-apis-app-ability-childProcessArgs.md), which is used to receive the parameters passed by the main process.

    <!-- @[arkts_child_process_arg_child](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ArkTsChildProcess/entry/src/main/ets/process/DemoProcessArg.ets) -->
    
    ``` TypeScript
    import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';
    
    export default class DemoProcessArg extends ChildProcess {
      onStart(args?: ChildProcessArgs) {
        // Obtain the entryParams passed by the main process.
        let entryParams = args?.entryParams;
        console.info(`DemoProcess onStart, entryParams: ${entryParams}`);
        // Obtain the fd handle passed from the main process.
        let fd = args?.fds?.key1;
        // Implement the child process business logic.
        // ...
      }
    }
    ```

2. Start the child process from the main process.

    In the main process, import the child process class and call the [startArkChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartarkchildprocess12) method to start the child process. Note that you must reference the child process class in the code to prevent the child process source file from being optimized out by the build tool. For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](uiability-usage.md#obtaining-the-context-of-uiability).

    After startup, search for the "startArkChildProcess" keyword in HiLog. Viewing the "startArkChildProcess success, pid: xxx" log indicates that child process creation is successful. Search again for the "DemoProcess onStart" keyword. Viewing this log indicates that the child process entry function has been executed.

    <!-- @[arkts_child_process_arg](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ArkTsChildProcess/entry/src/main/ets/pages/Index.ets) --> 
    
    ``` TypeScript
    import { common, ChildProcessArgs, ChildProcessOptions, childProcessManager } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    // ...
    import DemoProcessArg from  '../process/DemoProcessArg';
    import { fileIo } from '@kit.CoreFileKit';
    @Entry
    @Component
    struct Index {
    
      build() {
        Scroll() {
          Column() {
    // ...
            Text("StartArkChildProcessWithArg")
              .fontSize($r('app.float.page_text_font_size'))
              .fontWeight(FontWeight.Bold)
              .alignRules({
                center: { anchor: '__container__', align: VerticalAlign.Center },
                middle: { anchor: '__container__', align: HorizontalAlign.Center }
              })
              .onClick(() => {
                try {
                  DemoProcessArg.toString(); // Reference the child process class to prevent it from being optimized away by the build tool.
                  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                  let path = context.filesDir + "/test.txt";
                  let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
                  let args: ChildProcessArgs = {
                    entryParams: "testParam",
                    fds: {
                      "key1": file.fd
                    }
                  };
                  let options: ChildProcessOptions = {
                    isolationMode: false
                  };
                  childProcessManager.startArkChildProcess("module1/ets/process/DemoProcessArg.ets", args, options)
                    .then((pid) => {
                      console.info(`startArkChildProcess success, pid: ${pid}`);
                    })
                    .catch((err: BusinessError) => {
                      console.error(`startArkChildProcess error, errorCode: ${err.code}, errorMsg:${err.message}`);
                    });
                } catch (err) {
                  console.error(`startArkChildProcess error, errorCode: ${(err as BusinessError).code}`);
                }
              })
          }
          .width('100%')
        }
        .height('100%')
      }
    }
    ```

## Creating a Native Child Process with Parameter Passing Support

Use the [startNativeChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartnativechildprocess13) interface to create a [Native child process](ability-terminology.md#native-child-process). You need to implement the entry function in C/C++ and compile it into a dynamic link library, and pass string parameters and fd handles through [ChildProcessArgs](../reference/apis-ability-kit/js-apis-app-ability-childProcessArgs.md). The child process exits automatically after the entry function returns.


1. Implement the entry function in the child process.

    In the child process, implement and export the entry function whose parameter is [NativeChildProcess_Args](../reference/apis-ability-kit/capi-nativechildprocess-args.md) (assuming the file containing the code is named ChildProcessSample.cpp). After the child process starts, it calls this entry function, and the child process exits immediately after the function returns.

    <!-- @[child_process_necessary_export_impl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessParams/entry/src/main/cpp/ChildProcessFunc.cpp) -->
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    #include <hilog/log.h>
    #include "loghelper.h"

    extern "C" {
    /**
     * Entry function of the child process, implementing the business logic of the child process
     * The function name can be customized and is specified when the main process calls the OH_Ability_StartNativeChildProcess method. In this example, it is Main
     * The child process exits after the function returns
     */
    void Main(NativeChildProcess_Args args)
    {
        OH_LOG_INFO(LOG_APP, "Main started");
        // Obtain the passed entryParams
        char *entryParams = args.entryParams;
        // Obtain the passed fd list
        NativeChildProcess_Fd *current = args.fdList.head;
        while (current != nullptr) {
            char *fdName = current->fdName;
            int32_t fd = current->fd;
            current = current->next;
            // Implement the business logic
        }
    }
    } // extern "C"
    ```

2. Compile the dynamic link library.

    Modify the CMakeLists.txt file to compile it into a dynamic link library (assuming the library file name to be generated is libchildprocesssample.so), and add the ability dynamic library dependency.

    ```txt
    add_library(childprocesssample SHARED
        # Source file that implements the required export methods
        ChildProcessSample.cpp
        
        # Other code source files
        # ...
    )

    target_link_libraries(childprocesssample PUBLIC
        # Add the dependent ability framework dynamic library
        libchild_process.so

        # Other dependent dynamic libraries
        # ...
    )
    ```

3. Start the Native child process in the main process.

    In the main process, call the [startNativeChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartnativechildprocess13) method to start the Native child process. For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](uiability-usage.md#obtaining-the-context-of-uiability).

    After startup, you can search for the "startNativeChildProcess" keyword in HiLog. Viewing the "startNativeChildProcess success, pid: xxx" log indicates that the child process creation is successful. Search for the "Main started" keyword again. Viewing this log indicates that the child process entry function has been executed.
    
    <!-- @[child_get_start_params_index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessParams/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { common, ChildProcessArgs, ChildProcessOptions, childProcessManager } from '@kit.AbilityKit';
    import { fileIo } from '@kit.CoreFileKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    
    @Entry
    @Component
    struct Index {
      build() {
        Scroll() {
          Column() {
            Text("StartNativeChildProcess")
              .fontSize($r('app.float.page_text_font_size'))
              .fontWeight(FontWeight.Bold)
              .alignRules({
                center: { anchor: '__container__', align: VerticalAlign.Center },
                middle: { anchor: '__container__', align: HorizontalAlign.Center }
              })
              .onClick(() => {
                try {
                  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                  let path = context.filesDir + "/test.txt";
                  let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
                  let args: ChildProcessArgs = {
                    entryParams: "testParam",
                    fds: {
                      "key1": file.fd
                    }
                  };
                  let options: ChildProcessOptions = {
                    isolationMode: false
                  };
                  childProcessManager.startNativeChildProcess("libchildprocesssample.so:Main", args, options)
                    .then((pid) => {
                      console.info(`startNativeChildProcess success, pid: ${pid}`);
                    })
                    .catch((err: BusinessError) => {
                      console.error(`startNativeChildProcess error, errorCode: ${err.code}, errorMsg:${err.message}`);
                    });
                } catch (err) {
                  console.error(`startNativeChildProcess error, errorCode: ${(err as BusinessError).code}`);
                }
              })
          }
          .width('100%')
        }
        .height('100%')
      }
    }
    ```
