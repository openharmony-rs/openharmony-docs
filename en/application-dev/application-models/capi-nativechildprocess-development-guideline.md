# Child Process Development Guide (C/C++)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b09766262e176d598c6af77970ff4840525700ad translatedAt=2026-11-02T13:33:32.152Z pushedAt=2026-11-03T04:24:02.434Z nl=1 -->

## Overview

In Native-layer multi-process programming scenarios, developers often face issues such as complex parent-child process communication and difficult parameter passing. The [Native child process](../application-models/ability-terminology.md#native-child-process) mechanism allows applications to create child processes through the C API, supporting IPC communication and parameter passing, and is suitable for scenarios that require high-performance process isolation and cross-process communication. This module provides capabilities such as creating Native child processes, obtaining startup parameters, terminating child processes, and obtaining child process exit information. For interface selection and capability differences between the two creation methods, see [Child Process Creation Method Selection](#child-process-creation-method-selection).

> **NOTE** 
> 
> - The created child process exits when the parent process exits and cannot run independently of the parent process.
> - Before creating a child process, you can call [OH_Ability_IsNativeChildProcessSupported](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_isnativechildprocesssupported) to query whether the current device supports creating Native child processes.

## Child Process Creation Method Selection

| Comparison Item | Create a Native Child Process That Supports IPC | Create a Native Child Process That Supports Parameter Passing |
| --- | --- | --- |
| Involved API | [OH_Ability_CreateNativeChildProcessWithConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_createnativechildprocesswithconfigs)<sup>20+</sup> | [OH_Ability_StartNativeChildProcessWithConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocesswithconfigs)<sup>20+</sup> |
| Applicable Scenarios | Suitable for scenarios where the parent and child processes need to establish an IPC channel for communication, such as isolating high-risk operations or independent business logic into a child process and interacting through IPC. | Suitable for scenarios where parameters (strings, file descriptors) need to be passed to the child process and the child process performs computing tasks, such as audio/video encoding and decoding, and data processing. |
| Parent-Child Process Communication Method | IPC channel (the child process returns an IPC Stub through NativeChildProcess_OnConnect, and the main process communicates through OHIPCRemoteProxy) | Parameter passing (entryParams and fd list are passed in through [NativeChildProcess_Args](../reference/apis-ability-kit/capi-nativechildprocess-args.md), one-way parameter passing) |
| Child Process Entry Function | Needs to implement and export two functions: NativeChildProcess_OnConnect and NativeChildProcess_MainProc | Needs to implement and export an entry function that takes [NativeChildProcess_Args](../reference/apis-ability-kit/capi-nativechildprocess-args.md) as a parameter (the function name can be customized) |
| Startup Result Acquisition | Asynchronous, notified of the startup result and IPC Proxy object through the onProcessStarted callback | Synchronous, returns the child process ID through the output parameter pid |
| Whether It Depends on IPC Kit | Yes | No |
| Child Process Destruction Method | The child process exits after NativeChildProcess_MainProc returns | The child process exits after the entry function returns |

## Creating a Native Child Process That Supports IPC

Asynchronously create a Native child process through the [OH_Ability_CreateNativeChildProcessWithConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_createnativechildprocesswithconfigs) API. The child process needs to implement and export two functions: NativeChildProcess_OnConnect and NativeChildProcess_MainProc. After the child process starts, NativeChildProcess_OnConnect is first called to obtain the IPC Stub object, and then NativeChildProcess_MainProc is called to transfer the main thread control right. After the function returns, the child process exits immediately. This method depends on [IPC Kit](../ipc/ipc-rpc-overview.md).


1. Add dynamic library files and header file references.

    Add the dynamic library file in the CMakeLists.txt file.

    ```txt
    libipc_capi.so
    libchild_process.so
    ```

    Include the header file in the source file.

    <!-- @[child_process_head_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessIpc/entry/src/main/cpp/ChildProcessSample.cpp) -->
    
    ``` C++
    #include <IPCKit/ipc_kit.h>
    #include <AbilityKit/native_child_process.h>
    ```

2. Implement the necessary export functions in the child process.

    In the child process, implement and export the two necessary functions **NativeChildProcess_OnConnect** and **NativeChildProcess_MainProc** (assuming the code file is named ChildProcessSample.cpp). The OHIPCRemoteStub object returned by NativeChildProcess_OnConnect is responsible for IPC communication with the main process. For the specific implementation, refer to [IPC Communication Development Guide (C/C++)](../ipc/ipc-capi-development-guideline.md), which is not repeated here.

    After the child process is started, **NativeChildProcess_OnConnect** is invoked to obtain an IPC stub object, and then **NativeChildProcess_MainProc** is called to transfer the control right of the main thread. After the second function is returned, the child process exits.
    
    <!-- @[child_process_must_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessIpc/entry/src/main/cpp/ChildProcessSample.cpp) --> 
    
    ``` C++
    #include <IPCKit/ipc_kit.h>
    // ...
    #include <IPCKit/ipc_cremote_object.h>
    #include <IPCKit/ipc_cparcel.h>
    #include <IPCKit/ipc_error_code.h>
    
    class IpcCapiStubTest {
    public:
        explicit IpcCapiStubTest();
        ~IpcCapiStubTest();
        OHIPCRemoteStub *GetRemoteStub();
        static int OnRemoteRequest(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData);
    
    private:
        OHIPCRemoteStub *stub_{nullptr};
    };
    
    IpcCapiStubTest::IpcCapiStubTest()
    {
        // Create a stub object.
        stub_ = OH_IPCRemoteStub_Create("testIpc", &IpcCapiStubTest::OnRemoteRequest, nullptr, this);
    }
    
    IpcCapiStubTest::~IpcCapiStubTest()
    {
        if (stub_ != nullptr) {
            OH_IPCRemoteStub_Destroy(stub_);
        }
    }
    
    OHIPCRemoteStub *IpcCapiStubTest::GetRemoteStub() { return stub_; }
    
    int IpcCapiStubTest::OnRemoteRequest(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData)
    {
        return OH_IPC_SUCCESS;
    }
    
    IpcCapiStubTest g_ipcStubObj;
    
    extern "C" {
    OHIPCRemoteStub *NativeChildProcess_OnConnect()
    {
        // ipcRemoteStub points to the IPC stub object implemented by the child process. The object is used to receive and respond to IPC messages from the main process.
        // The child process controls its lifecycle according to the service logic.
        return g_ipcStubObj.GetRemoteStub();
    }
    
    void NativeChildProcess_MainProc()
    {
        // Equivalent to the Main function of the child process. It implements the service logic of the child process.
        // ...
        // After the function is returned, the child process exits.
    }
    
    } // extern "C"
    ```


3. Compile the dynamic link library.

    Modify the CMakeLists.txt file to compile the dynamic link library (assuming the library file to be compiled is named libchildprocesssample.so), and add the IPC dynamic library dependency.

    ```txt
    add_library(childprocesssample SHARED
        # Source code file that implements the necessary export functions
        ChildProcessSample.cpp
        
        # Other source code files
        # ...
    )

    target_link_libraries(childprocesssample PUBLIC
        # Add the dependency of the dynamic link library of IPC Kit.
    libipc_capi.so
     
    # Dependencies of other dynamic link libraries
    # ...
    )
    ```

4. Implement the child process startup result callback function in the main process.

    <!-- @[main_handle_child_start_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessIpc/entry/src/main/cpp/MainProcessSample.cpp) -->
    
    ``` C++
    #include <IPCKit/ipc_kit.h>
    #include <AbilityKit/native_child_process.h>
    // ···
    static void OnNativeChildProcessStarted(int errCode, OHIPCRemoteProxy *remoteProxy)
    {
        if (errCode != NCP_NO_ERROR) {
            // Exception handling when the child process is not started normally
            // ...
            return;
        }
    
        // Save the remoteProxy object for IPC with the child process based on the APIs provided by IPC Kit.
        // You are advised to transfer time-consuming operations to an independent thread to avoid blocking the callback thread for a long time.
        // When the IPC object is no longer needed, call OH_IPCRemoteProxy_Destroy to release it.
        // ···
    }
    ```

    The second parameter OHIPCRemoteProxy object passed by the callback function establishes an IPC channel with the OHIPCRemoteStub object returned by the **NativeChildProcess_OnConnect** method implemented by the child process. For specific usage, refer to [IPC Communication Development Guide (C/C++)](../ipc/ipc-capi-development-guideline.md), which is not repeated here. After the OHIPCRemoteProxy object is no longer used, call the [OH_IPCRemoteProxy_Destroy](../reference/apis-ipc-kit/capi-ipc-cremote-object-h.md#oh_ipcremoteproxy_destroy) function to release it.

5. Start the Native child process in the main process.

    Call the [OH_Ability_CreateNativeChildProcessWithConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_createnativechildprocesswithconfigs) API to start the Native child process. You can use [OH_Ability_CreateChildProcessConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_createchildprocessconfigs) to create a child process configuration information object, and set the process name, isolation mode, and uid isolation as needed. Note that a return value of NCP_NO_ERROR only indicates that the Native child process startup logic was successfully called; the actual startup result is asynchronously notified through the callback function. Note that **child processes can only be created in the main process**.

    <!-- @[main_processIpc_launch_native_child](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessIpc/entry/src/main/cpp/MainProcessSample.cpp) -->
    
    ``` C++
    #include <IPCKit/ipc_kit.h>
    #include <AbilityKit/native_child_process.h>
    // ...
    int32_t g_result = -1;
    // ...
    static void OnNativeChildProcessStarted(int errCode, OHIPCRemoteProxy *remoteProxy)
    {
        if (errCode != NCP_NO_ERROR) {
            // Exception handling when the child process is not started normally
            // ...
            return;
        }
    
        // Save the remoteProxy object for IPC with the child process based on the APIs provided by IPC Kit.
        // You are advised to transfer time-consuming operations to an independent thread to avoid blocking the callback thread for a long time.
        // When the IPC object is no longer needed, call OH_IPCRemoteProxy_Destroy to release it.
        // ...
    }
    
    void CreateNativeChildProcess()
    {
        // Create the child process configuration information object.
        Ability_ChildProcessConfigs *configs = OH_Ability_CreateChildProcessConfigs();
        // Set the process name of the child process.
        OH_Ability_ChildProcessConfigs_SetProcessName(configs, "childprocess_ipc");
        // The first parameter libchildprocesssample.so indicates the name of the dynamic link library that implements the necessary export functions of the child process.
        Ability_NativeChildProcess_ErrCode ret = OH_Ability_CreateNativeChildProcessWithConfigs("libchildprocesssample.so",
            configs, OnNativeChildProcessStarted);
        // The configs object must be destroyed after use to avoid memory leaks.
        OH_Ability_DestroyChildProcessConfigs(configs);
        if (ret != NCP_NO_ERROR) {
            // Exception handling when the child process is not started normally
            // ...
        }
        g_result = ret;
    }
    ```


6. Add compilation dependencies for the main process.

    Modify CMakeLists.txt to add the necessary dependency libraries. Assume the so where the main process is located is named libmainprocesssample.so (the main process and child process implementations can also be compiled into the same dynamic library file).

    ```txt
    target_link_libraries(mainprocesssample PUBLIC
        # Add dependencies of the dynamic link library of IPC Kit and Ability Kit.
    libipc_capi.so
    libchild_process.so
     
    # Dependencies of other dynamic link libraries
    # ...
    )
    ```

## Creating a Native Child Process That Supports Pass-by-Parameter

Synchronously create a Native child process through the [OH_Ability_StartNativeChildProcessWithConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocesswithconfigs) API. The child process needs to implement an entry function that takes [NativeChildProcess_Args](../reference/apis-ability-kit/capi-nativechildprocess-args.md) as a parameter. Pass the entryParams string and fd list through NativeChildProcess_Args. After the entry function returns, the child process exits automatically.


1. Add dynamic library files and header file references.

    Add the dynamic library file in the CMakeLists.txt file.

    ```txt
    libchild_process.so
    ```

    Include the header file in the source file.

    <!-- @[create_native_child_param_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessParams/entry/src/main/cpp/ChildProcessFunc.cpp) -->
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    ```

2. Implement the necessary export methods in the child process.

    In the child process, implement and export the entry function [NativeChildProcess_Args](../reference/apis-ability-kit/capi-nativechildprocess-args.md). (It is assumed that the code file is named **ChildProcessSample.cpp**.) After the child process is started, the entry function is invoked. After the second function is returned, the child process exits.

    <!-- @[child_process_necessary_export_impl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessParams/entry/src/main/cpp/ChildProcessFunc.cpp) --> 
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    #include <hilog/log.h>
    #include "loghelper.h"

    extern "C" {
    /**
     * Entry function of a child process, which implements the service logic of the child process.
     * The function name can be customized and is specified when the main process calls the OH_Ability_StartNativeChildProcessWithConfigs method. In this example, it is Main
     * After the function is returned, the child process exits.
     */
    void Main(NativeChildProcess_Args args)
    {
        OH_LOG_INFO(LOG_APP, "Main started");
        // Obtain the passed entryParams
        char *entryParams = args.entryParams;
        // Obtain the input FD list.
        NativeChildProcess_Fd *current = args.fdList.head;
        while (current != nullptr) {
            char *fdName = current->fdName;
            int32_t fd = current->fd;
            current = current->next;
            // Implement the service logic.
        }
    }
    } // extern "C"
    ```


3. Compile the dynamic link library.

    Modify the CMakeLists.txt file to compile it into a dynamic link library (assuming the library file to be compiled is named libchildprocesssample.so), and add the dependency of the Ability Kit dynamic library.

    ```txt
    add_library(childprocesssample SHARED
        # Source code file that implements the necessary export functions
        ChildProcessSample.cpp
        
        # Other source code files
        # ...
    )

    target_link_libraries(childprocesssample PUBLIC
        # Add the dependency of the dynamic link library of Ability Kit.
    libchild_process.so

    # Dependencies of other dynamic link libraries
    # ...
    )
    ```

4. Start the Native child process in the main process.

    Call the [OH_Ability_StartNativeChildProcessWithConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocesswithconfigs) API to start the Native child process. You can use [OH_Ability_CreateChildProcessConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_createchildprocessconfigs) to create a child process configuration information object, and set the process name, isolation mode, and uid isolation as needed. A return value of NCP_NO_ERROR indicates that the Native child process is started successfully.

    <!-- @[main_process_launch_native_child](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessParams/entry/src/main/cpp/MainProcessFunc.cpp) -->
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    #include <cstdlib>
    #include <cstring>
    #include <fcntl.h>
    // ...
    int32_t g_fdNameMaxLength = 20;
    
    void StartNativeChildProcess()
    {
        NativeChildProcess_Args args;
        // Set entryParams.
        const size_t entryParamsSize = 10;
        args.entryParams = (char *)malloc(sizeof(char) * entryParamsSize);
        if (args.entryParams != nullptr) {
            (void)strlcpy(args.entryParams, "testParam", entryParamsSize);
        }
    
        // Insert a node to the head node of the linked list.
        args.fdList.head = (NativeChildProcess_Fd *)malloc(sizeof(NativeChildProcess_Fd));
        // FD keyword, which contains a maximum of 20 characters.
        args.fdList.head->fdName = (char *)malloc(sizeof(char) * g_fdNameMaxLength);
        if (args.fdList.head->fdName != nullptr) {
            (void)strlcpy(args.fdList.head->fdName, "fd1", g_fdNameMaxLength);
        }
        // Obtain the FD logic.
        int32_t fd = open("/data/storage/el2/base/haps/entry/files/test.txt", O_RDWR | O_CREAT, 0644);
        args.fdList.head->fd = fd;
        // Insert only one FD record. You can insert a maximum of 16 FD records to the linked list as required.
        args.fdList.head->next = NULL;
        // Create a child process configuration object.
        Ability_ChildProcessConfigs *configs = OH_Ability_CreateChildProcessConfigs();
        // Set the process name of the child process.
        OH_Ability_ChildProcessConfigs_SetProcessName(configs, "child");

        // The first parameter libchildprocesssample.so:Main indicates the name of the dynamic link library file that implements the Main method of the child process and the name of the entry method.
        int32_t pid = -1;
        Ability_NativeChildProcess_ErrCode ret =
            OH_Ability_StartNativeChildProcessWithConfigs("libchildprocesssample.so:Main", args, configs, &pid);
        // Destroy the configs object after use to avoid memory leaks.
        OH_Ability_DestroyChildProcessConfigs(configs);
        if (ret != NCP_NO_ERROR) {
            // Release the memory space in NativeChildProcess_Args to prevent memory leakage.
            // Exception handling when the child process is not started normally
            // ...
        }
        // ...
        // Release the memory space in NativeChildProcess_Args to prevent memory leakage.
    }
    ```

5. Add compilation dependencies for the main process.

    Modify CMakeLists.txt to add the necessary dependency libraries. It is assumed that the .so where the main process is located is named libmainprocesssample.so (the implementation of the main process and the child process can also choose to compile to the same dynamic library file).

    ```txt
    target_link_libraries(mainprocesssample PUBLIC
        # Add the dependency of the dynamic link library of Ability Kit.
    libchild_process.so
     
    # Dependencies of other dynamic link libraries
    # ...
    )
    ```

## Child Threads Obtaining Startup Parameters

Starting from API version 17, child processes can obtain startup parameters.

1. Add dynamic library files and header file references.

    Add the dynamic library file in the CMakeLists.txt file.

    ```txt
    libchild_process.so
    ```

    Include the header file in the source file.

    <!-- @[child_get_start_params_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessParams/entry/src/main/cpp/ChildGetStartParams.cpp) -->
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    ```

2. Obtain the startup parameters in the child process.

    After [OH_Ability_StartNativeChildProcessWithConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocesswithconfigs) creates the child process, any so and any child thread in the child process can call [OH_Ability_GetCurrentChildProcessArgs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_getcurrentchildprocessargs)() to obtain the child process startup parameters [NativeChildProcess_Args](../reference/apis-ability-kit/capi-nativechildprocess-args.md), which facilitates operating the related file descriptors.

    <!-- @[child_get_start_params_main](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessParams/entry/src/main/cpp/ChildGetStartParams.cpp) --> 
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    #include <thread>
    
    extern "C" {
    void ThreadFunc()
    {
        // Obtain the startup parameters of the child process
        NativeChildProcess_Args *args = OH_Ability_GetCurrentChildProcessArgs();
        // Return nullptr when failing to obtain the startup parameters
        if (args == nullptr) {
            return;
        }
        // Obtain entryParams from the startup parameters
        char *entryParams = args->entryParams;
        // Obtain the fd list
        NativeChildProcess_Fd *current = args->fdList.head;
        while (current != nullptr) {
            char *fdName = current->fdName;
            int32_t fd = current->fd;
            current = current->next;
            // Implement the business logic
        }
    }
    
    /**
     * Entry function of the child process, implementing the business logic of the child process
     * args is the startup parameters of the child process
     */
    void Main(NativeChildProcess_Args args)
    {
        // Implement the service logic.
    
        // Create a thread
        std::thread tObj(ThreadFunc);
    }
    
    } // extern "C"
    ```

## Terminating a Child Process

Starting from API version 22, you can terminate a [native child process](../application-models/ability-terminology.md#native-child-process) or an [ArkTS child process](../application-models/ability-terminology.md#arkts-child-process) created by the current process based on the input PID.

1. Add the dynamic library file and header file reference.

    Add the dynamic library file in the CMakeLists.txt file.

    ```txt
    libchild_process.so
    ```

    Include the header file in the source file.

    <!-- @[kill_child_process_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/KillChildProcess/entry/src/main/cpp/MainProcessFile.cpp) -->
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    ```

2. Implement terminating the child process.

    After creating the child process through the interfaces in [native_child_process](../reference/apis-ability-kit/capi-native-child-process-h.md) and [childProcessManager](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md) (non-SELF_FORK mode), the main process can call [OH_Ability_KillChildProcess](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_killchildprocess)(int32_t pid) to terminate the corresponding child process based on the passed pid.

    <!-- @[kill_child_process_main](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/KillChildProcess/entry/src/main/cpp/MainProcessFile.cpp) -->
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    // ...
    void KillChildProcess(int32_t pid)
    {
        Ability_NativeChildProcess_ErrCode ret = OH_Ability_KillChildProcess(pid);
        if (ret != NCP_NO_ERROR) {
            // Exception handling when the child process is not killed successfully.
        }
        // ...
    }
    ```

## Obtaining Native Child Process Exit Information

Starting from API version 20, the parent process can register a callback function to listen to the child process and obtain abnormal exit information of the child process, so that the parent process can perform subsequent optimization processing. The child process that can be listened to here must be a child process created through the [OH_Ability_StartNativeChildProcess](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocess), [OH_Ability_StartNativeChildProcessWithConfigs](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocesswithconfigs), or [startNativeChildProcess](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md#childprocessmanagerstartnativechildprocess13) API.

1. Add dynamic library files and header file references.

    Add the dynamic library file in the CMakeLists.txt file.

    ```txt
    libchild_process.so
    ```

    Include the header file in the source file.

    <!-- @[native_child_process_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessExit/entry/src/main/cpp/MainProcessFile.cpp) -->
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    ```

2. Register and unregister the Native child process abnormal exit callback.

    Call [OH_Ability_RegisterNativeChildProcessExitCallback](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_registernativechildprocessexitcallback) to register the Native child process. If the return value is NCP_NO_ERROR, the registration is successful.

    Call [OH_Ability_UnregisterNativeChildProcessExitCallback](../reference/apis-ability-kit/capi-native-child-process-h.md#oh_ability_unregisternativechildprocessexitcallback) to unregister the Native child process. If the return value is NCP_NO_ERROR, the unregistration is successful.

    <!-- @[register_native_child_process_exit](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/NativeChildProcessExit/entry/src/main/cpp/MainProcessFile.cpp) -->
    
    ``` C++
    #include <AbilityKit/native_child_process.h>
    #include <hilog/log.h>
    
    // ...
    
    void OnNativeChildProcessExit(int32_t pid, int32_t signal)
    {
        OH_LOG_INFO(LOG_APP, "pid: %{public}d, signal: %{public}d", pid, signal);
    }
    
    void RegisterNativeChildProcessExitCallback()
    {
        Ability_NativeChildProcess_ErrCode ret =
            OH_Ability_RegisterNativeChildProcessExitCallback(OnNativeChildProcessExit);
        if (ret != NCP_NO_ERROR) {
            OH_LOG_ERROR(LOG_APP, "register failed.");
        }
        // ...
    }
    
    void UnregisterNativeChildProcessExitCallback()
    {
        Ability_NativeChildProcess_ErrCode ret =
            OH_Ability_UnregisterNativeChildProcessExitCallback(OnNativeChildProcessExit);
        if (ret != NCP_NO_ERROR) {
            OH_LOG_ERROR(LOG_APP, "unregister failed.");
        }
        // ...
    }
    ```

3. Add compilation dependencies.

    Modify CMakeLists.txt to add the necessary dependency library. Assume that the .so where the main process is located is named libmainprocesssample.so (the implementation of the main process and child process can also choose to compile to the same dynamic library file).

    ```txt
    target_link_libraries(mainprocesssample PUBLIC
        # Add the dependency ability dynamic library
        libchild_process.so

        # Other dependency dynamic libraries
        # ...
    )
    ```
