# native_child_process.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=f0ca4679538114d37c428618ebeb98dcc5067c5b translatedAt=2026-09-03T09:03:55.864Z pushedAt=2026-09-05T10:47:30.139Z -->

## Overview

This module supports creating Native child processes and establishing IPC channels between parent and child processes. It is applicable to various scenarios where time-consuming tasks, high-risk operations, or independent business logic need to be isolated into independent processes. This module provides core capabilities such as process isolation, IPC communication, and flexible configuration, which can effectively improve application stability and security and prevent the main process from being blocked or crashing. Through the child process mechanism, developers can implement a multi-process architecture to run compute-intensive tasks, media processing, network requests, and other services independently, thereby improving application responsiveness and user experience.

A maximum of 512 child processes can be started through this module and [childProcessManager](js-apis-app-ability-childProcessManager.md) (non-SELF_FORK mode).

**File to include**: <AbilityKit/native_child_process.h>

**Library**: libchild_process.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 12

**Related module**: [ChildProcess](capi-childprocess.md)

## Constraints

### Functional Limitations

- The created child process does not support creating a UI.
- The created child process does not support API calls that depend on Context (including the APIs of the Context module itself and APIs that take a Context instance as an input parameter).
- Child processes can be created only in the main process. Creating a child process within a child process is not supported.

### Specification Limits

- The total number of child processes started through the child process creation interfaces defined in this module and the child process creation interfaces defined in [childProcessManager](js-apis-app-ability-childProcessManager.md) is up to 512 (when system resources are sufficient). Among them, child processes started by the [startChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess) interface in SELF_FORK mode are not counted in the total.

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [NativeChildProcess_Fd](capi-nativechildprocess-fd.md) | NativeChildProcess_Fd | Describes the information about the file descriptor passed to the child process.|
| [NativeChildProcess_FdList](capi-nativechildprocess-fdlist.md) | NativeChildProcess_FdList | Describes the list of file descriptors passed to the child process. A maximum of 16 file descriptors are supported.|
| [NativeChildProcess_Options](capi-nativechildprocess-options.md) | NativeChildProcess_Options | Describes the options used by the child process.|
| [NativeChildProcess_Args](capi-nativechildprocess-args.md) | NativeChildProcess_Args | Describes the parameters passed to the child process.|
| [Ability_ChildProcessConfigs](capi-ability-childprocessconfigs.md) | Ability_ChildProcessConfigs | Describes the configuration information about a child process, including the child process name and the sharing mode of the data sandbox and network environment.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | Ability_NativeChildProcess_ErrCode | Defines an enum for the error codes used by the native child process module.|
| [NativeChildProcess_IsolationMode](#nativechildprocess_isolationmode) | NativeChildProcess_IsolationMode | Enumerates the sharing modes available for the data sandbox and network environment of a native child process.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Ability_ChildProcessConfigs* OH_Ability_CreateChildProcessConfigs()](#oh_ability_createchildprocessconfigs) | - | Creates a child process configuration information object. After the object is created, call [OH_Ability_DestroyChildProcessConfigs](#oh_ability_destroychildprocessconfigs) to destroy it to avoid memory leaks. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_DestroyChildProcessConfigs(Ability_ChildProcessConfigs* configs)](#oh_ability_destroychildprocessconfigs) | - | Destroys a child process configuration object and releases its memory. After this function is called, do not use the destroyed object.|
| [Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetIsolationMode(Ability_ChildProcessConfigs* configs, NativeChildProcess_IsolationMode isolationMode)](#oh_ability_childprocessconfigs_setisolationmode) | - | Sets the sharing mode of the data sandbox and network environment in the child process configuration information object. For details, see [NativeChildProcess_IsolationMode](#nativechildprocess_isolationmode). This setting only takes effect when the [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs) and [OH_Ability_CreateNativeChildProcessWithConfigs](#oh_ability_createnativechildprocesswithconfigs) interfaces are called. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetProcessName(Ability_ChildProcessConfigs* configs,const char* processName)](#oh_ability_childprocessconfigs_setprocessname) | - | Sets the process name in a child process configuration object.|
| [typedef void (\*OH_Ability_OnNativeChildProcessStarted)(int errCode, OHIPCRemoteProxy *remoteProxy)](#oh_ability_onnativechildprocessstarted) | OH_Ability_OnNativeChildProcessStarted | Callback function used to notify the child process startup result. |
| [int OH_Ability_CreateNativeChildProcess(const char* libName,OH_Ability_OnNativeChildProcessStarted onProcessStarted)](#oh_ability_createnativechildprocess) | - | Creates a child process and loads the dynamic link library file specified by the parameter. The process startup result is returned through the callback parameter as an asynchronous notification. Note that the callback notification runs in an independent thread, so the callback function implementation must ensure thread synchronization and must not perform time-consuming operations to avoid long-time blocking. The dynamic library specified by the parameter must implement and export the following functions:<br>1. OHIPCRemoteStub* NativeChildProcess_OnConnect()<br>2. void NativeChildProcess_MainProc()<br>The processing logic sequence is as follows, as shown in the pseudo-code:<br>Main process:<br>1. OH_Ability_CreateNativeChildProcess(libName, onProcessStartedCallback)<br>Child process:<br>2. dlopen(libName)<br>3. dlsym("NativeChildProcess_OnConnect")<br>4. dlsym("NativeChildProcess_MainProc")<br>5. ipcRemote = NativeChildProcess_OnConnect()<br>6. NativeChildProcess_MainProc()<br>Main process:<br>7. onProcessStartedCallback(errCode, ipcRemote)<br>Child process:<br>8. After the NativeChildProcess_MainProc() function returns, the child process exits.<br>**Device behavior:** For API version 13 and earlier versions, this interface can work normally in PC/2in1, returns the [NCP_ERR_NOT_SUPPORTED](#ability_nativechildprocess_errcode) error code in Tablet devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other devices. For API version 14 and later versions, this interface can work normally in PC/2in1 and Tablet devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other devices.<br>**Note:** For API version 14 and earlier versions, a single process can start only 1 Native child process. Since API version 15, a single process can start up to 50 Native child processes. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_CreateNativeChildProcessWithConfigs(const char* libName,Ability_ChildProcessConfigs* configs, OH_Ability_OnNativeChildProcessStarted onProcessStarted)](#oh_ability_createnativechildprocesswithconfigs) | - | Creates a child process based on the passed child process configuration information and loads the dynamic link library file specified by the parameter. The child process startup result is returned to the caller through the callback parameter as an asynchronous notification. This callback runs in an independent thread, so thread synchronization must be ensured and time-consuming operations must not be performed to avoid long-time blocking. The dynamic library specified by the parameter must implement and export the following functions:<br>1. OHIPCRemoteStub* NativeChildProcess_OnConnect()<br>2. void NativeChildProcess_MainProc()<br>The processing logic sequence is as follows, as shown in the pseudo-code:<br>Main process:<br>1. OH_Ability_CreateNativeChildProcessWithConfigs(libName, configs, onProcessStartedCallback)<br>Child process:<br>2. dlopen(libName)<br>3. dlsym("NativeChildProcess_OnConnect")<br>4. dlsym("NativeChildProcess_MainProc")<br>5. ipcRemote = NativeChildProcess_OnConnect()<br>6. NativeChildProcess_MainProc()<br>Main process:<br>7. onProcessStartedCallback(errCode, ipcRemote)<br>Child process:<br>8. After the NativeChildProcess_MainProc() function returns, the child process exits.<br>**Device behavior:** This interface can be called normally in PC/2in1 and Tablet devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other devices. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_StartNativeChildProcess(const char* entry, NativeChildProcess_Args args,NativeChildProcess_Options options, int32_t *pid)](#oh_ability_startnativechildprocess) | - | Starts a Native child process and loads the specified dynamic link library file. The specified dynamic library must implement a function that takes NativeChildProcess_Args as its parameter (the function name can be customized) and export that function. An example is as follows:<br>1. void Main(NativeChildProcess_Args args);<br>The processing logic sequence is as follows, as shown in the pseudo-code:<br>Main process:<br>1. OH_Ability_StartNativeChildProcess(entryPoint, args, options)<br>Child process:<br>2. dlopen(libName)<br>3. dlsym("Main")<br>4. Main(args)<br>5. The child process exits after the Main(args) function returns.<br>**Device behavior:** In API version 13 and earlier, this interface can work normally in PC/2in1 devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other device types. Since API version 14, this interface can work normally in PC/2in1 and Tablet devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other device types. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_StartNativeChildProcessWithConfigs(const char* entry, NativeChildProcess_Args args, Ability_ChildProcessConfigs* configs, int32_t *pid)](#oh_ability_startnativechildprocesswithconfigs) | - | Starts a native child process based on the child process configuration object, loads the specified DLL file, and calls the entry function. Arguments can be passed to the child process. The specified DLL must implement and export a function that accepts **NativeChildProcess_Args** as its parameter (you can customize the function name). The following is an example:<br>1. void Main(NativeChildProcess_Args args);<br>The processing logic sequence is shown in the following pseudocode:<br>Parent process:<br>1. OH_Ability_StartNativeChildProcessWithConfigs(entryPoint, args, configs, &pid)<br>Child process:<br>2. dlopen(libName)<br>3. dlsym("Main")<br>4. Main(args)<br>5. The child process exits after the Main(args) function returns.<br>**Device behavior differences**: This function can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code [NCP_ERR_NOT_SUPPORTED](#ability_nativechildprocess_errcode) is returned.|
| [NativeChildProcess_Args* OH_Ability_GetCurrentChildProcessArgs()](#oh_ability_getcurrentchildprocessargs) | - | Obtains the startup parameters of the child process.|
| [typedef void (\*OH_Ability_OnNativeChildProcessExit)(int32_t pid, int32_t signal)](#oh_ability_onnativechildprocessexit) | OH_Ability_OnNativeChildProcessExit | Callback function used to detect child process exit. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_RegisterNativeChildProcessExitCallback(OH_Ability_OnNativeChildProcessExit onProcessExit)](#oh_ability_registernativechildprocessexitcallback) | - | Registers a callback for child process exit. The registered callback function is triggered only when a child process started by [OH_Ability_StartNativeChildProcess](#oh_ability_startnativechildprocess), [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs), or [childProcessManager.startNativeChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartnativechildprocess13) exits. Registering the same callback function repeatedly keeps only one copy. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_UnregisterNativeChildProcessExitCallback(OH_Ability_OnNativeChildProcessExit onProcessExit)](#oh_ability_unregisternativechildprocessexitcallback) | - | Unregisters the callback used to listen for child process exit.|
| [Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetIsolationUid(Ability_ChildProcessConfigs* configs, bool isolationUid)](#oh_ability_childprocessconfigs_setisolationuid) | - | Sets whether the UID in the child process configuration information object is isolated. This setting only takes effect when NativeChildProcess_IsolationMode is NCP_ISOLATION_MODE_ISOLATED, and only when the [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs) and [OH_Ability_CreateNativeChildProcessWithConfigs](#oh_ability_createnativechildprocesswithconfigs) interfaces are called. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_KillChildProcess(int32_t pid)](#oh_ability_killchildprocess) | - | Terminates the child process created by the current process. |
| [bool OH_Ability_IsNativeChildProcessSupported()](#oh_ability_isnativechildprocesssupported) | - | Checks whether the caller is allowed to create a Native child process on this device. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_AcquireChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle* infos, uint32_t* count)](#oh_ability_acquirechildprocessinfos) | - | Obtains the information about all child processes of the current application. |

## Enum Description

### Ability_NativeChildProcess_ErrCode

```c
enum Ability_NativeChildProcess_ErrCode
```

**Description**

Defines an enum for the error codes used by the native child process module.

**Since**: 12

| Value| Description|
| -- | -- |
| NCP_NO_ERROR = 0 | Operation successful.|
| NCP_ERR_INVALID_PARAM = 401 | Invalid parameter. Check the type, value range, and whether the passed parameter is nullptr. |
| NCP_ERR_NOT_SUPPORTED = 801 | The current device type does not support creating a Native child process. Use another device type. |
| NCP_ERR_INTERNAL = 16000050 | Internal error. Restart the application or device and try again. |
| NCP_ERR_BUSY = 16010001 | A new child process cannot be created during the startup of another native child process. You can try again after the child process is started. This function is deprecated since API version 15.|
| NCP_ERR_TIMEOUT = 16010002 | Timeout for starting the Native child process. This may be caused by insufficient system resources or a time-consuming dynamic library loading. Check the system resource status and optimize the dynamic library loading logic. |
| NCP_ERR_SERVICE_ERROR = 16010003 | Server error. Try the operation again. If the problem persists, restart the application or device and try again. |
| NCP_ERR_MULTI_PROCESS_DISABLED = 16010004 | The multi-process mode is disabled, so starting a child process is not allowed. Use another device type. |
| NCP_ERR_ALREADY_IN_CHILD = 16010005 | Creating a process again in a child process is not allowed. Create the child process in the main process and avoid nested creation in a child process. |
| NCP_ERR_MAX_CHILD_PROCESSES_REACHED = 16010006 | The maximum number of child processes has been reached, so no more child processes can be created. Terminate the child processes that are no longer needed before creating new ones. |
| NCP_ERR_LIB_LOADING_FAILED = 16010007 | Failed to load the dynamic library in the child process. The file does not exist or the corresponding method is not implemented and exported. Check whether the dynamic library file path and name are correct, and ensure that the dynamic library implements and exports the corresponding method. |
| NCP_ERR_CONNECTION_FAILED = 16010008 | Failed to call the OnConnect method of the dynamic library in the child process. An invalid IPC object pointer may have been returned. Check the implementation of the NativeChildProcess_OnConnect function and ensure that a valid IPC object pointer is returned. |
| NCP_ERR_CALLBACK_NOT_EXIST = 16010009 | The parent process called to unregister the Native child process exit callback, but the registered callback function was not found. Check whether the callback function has been registered, and ensure that it is successfully registered before unregistering.<br>**Since:** 20 |
| NCP_ERR_INVALID_PID = 16010010 | The passed process pid does not exist, or is not the pid of a child process created by the current process, or belongs to a child process started by the [childProcessManager.startChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess) interface in SELF_FORK mode.<br>**Since:** 22 |

### NativeChildProcess_IsolationMode

```c
enum NativeChildProcess_IsolationMode
```

**Description**

Defines the sharing mode of the data sandbox and network environment of a Native child process. The data sandbox is the file system isolation environment of a process, which controls the process's access to files and data. The network environment is the network access configuration of a process, which controls the process's network connection and communication capabilities.

**Since**: 13

| Value| Description|
| -- | -- |
| NCP_ISOLATION_MODE_NORMAL = 0 | In normal isolation mode, the parent process and child process share the same sandbox environment and network environment. |
| NCP_ISOLATION_MODE_ISOLATED = 1 | In isolated mode, the parent and child processes each have their own separate sandbox and network environment.|


## Function Description

### OH_Ability_CreateChildProcessConfigs()

```c
Ability_ChildProcessConfigs* OH_Ability_CreateChildProcessConfigs()
```

**Description**

Creates a child process configuration information object. When you need to use [OH_Ability_CreateNativeChildProcessWithConfigs](#oh_ability_createnativechildprocesswithconfigs) or [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs) to start a child process, you must first create a configuration information object to set parameters such as the process name and isolation mode of the child process.

After the object is created successfully, call [OH_Ability_DestroyChildProcessConfigs](#oh_ability_destroychildprocessconfigs) to destroy the object and avoid memory leaks.

**Since**: 20

**Returns**

| Type                              | Description|
|----------------------------------| -- |
| [Ability_ChildProcessConfigs](capi-ability-childprocessconfigs.md)* | Pointer to the [Ability_ChildProcessConfigs](capi-ability-childprocessconfigs.md) object: The call is successful.<br>         nullptr: An internal error occurs or memory allocation fails.|

### OH_Ability_DestroyChildProcessConfigs()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_DestroyChildProcessConfigs(Ability_ChildProcessConfigs* configs)
```

**Description**

Destroys a child process configuration information object and releases its memory. After this interface is called, avoid continuing to use the pointer.

**Since**: 20


**Parameters**

| Parameter | Type | Mandatory | Description |
| -- | -- | -- | -- |
| configs | [Ability_ChildProcessConfigs](capi-ability-childprocessconfigs.md)* | Yes | Pointer to the child process configuration information object to be destroyed. After this interface is called, the object pointer becomes invalid. Avoid continuing to use the pointer. If a null pointer is passed in, the [NCP_ERR_INVALID_PARAM](#ability_nativechildprocess_errcode) error code is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | NCP_NO_ERROR - The operation is successful.<br>NCP_ERR_INVALID_PARAM - The input parameter is nullptr. |

### OH_Ability_ChildProcessConfigs_SetIsolationMode()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetIsolationMode(Ability_ChildProcessConfigs* configs, NativeChildProcess_IsolationMode isolationMode)
```

**Description**

Sets the sharing mode of the data sandbox and network environment of a child process configuration information object. For details, see [NativeChildProcess_IsolationMode](#nativechildprocess_isolationmode). This setting only takes effect when [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs) or [OH_Ability_CreateNativeChildProcessWithConfigs](#oh_ability_createnativechildprocesswithconfigs) is called.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [Ability_ChildProcessConfigs](capi-ability-childprocessconfigs.md)* configs | Pointer to the child process configuration information object. It cannot be nullptr. |
| [NativeChildProcess_IsolationMode](#nativechildprocess_isolationmode) isolationMode | Sharing mode of the data sandbox and network environment to set. NCP_ISOLATION_MODE_NORMAL is applicable to scenarios where the parent and child processes need to share the data sandbox or network environment (for example, accessing parent process files or sharing network connections). NCP_ISOLATION_MODE_ISOLATED is applicable to scenarios where enhanced security isolation is required (for example, processing untrusted data or running untrusted code). If not set, the default value is NCP_ISOLATION_MODE_NORMAL. |

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | NCP_NO_ERROR: success.<br>NCP_ERR_INVALID_PARAM: the input parameter configs is nullptr. |

### OH_Ability_ChildProcessConfigs_SetIsolationUid()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetIsolationUid(Ability_ChildProcessConfigs* configs, bool isolationUid)
```

**Description**

Sets whether the child process uses an independent UID. For example, in browser security hardening scenarios, you can isolate the UIDs of the main process and its child processes.

This setting takes effect only when **NativeChildProcess_IsolationMode** is set to **NCP_ISOLATION_MODE_ISOLATED**. If this function is not called to set **isolationUid**, the default value is **false**, meaning the child process will share the same UID as the main process.

This setting only takes effect when [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs) or [OH_Ability_CreateNativeChildProcessWithConfigs](#oh_ability_createnativechildprocesswithconfigs) is called.

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| [Ability_ChildProcessConfigs](capi-ability-childprocessconfigs.md)* configs | Pointer to the child process configuration information object. It cannot be nullptr. |
| bool isolationUid | Whether the child process uses an independent UID. The value true means the child process has an independent UID (applicable to scenarios that require enhanced security isolation, such as browser security hardening and processing untrusted data), and false means the child process has the same UID as the main process (applicable to scenarios where the parent and child processes need to share resources). The default value is false when this interface is not called. This setting only takes effect when NativeChildProcess_IsolationMode is NCP_ISOLATION_MODE_ISOLATED. |

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | NCP_NO_ERROR - execution succeeded.<br>NCP_ERR_INVALID_PARAM - the input parameter configs is nullptr. |

### OH_Ability_ChildProcessConfigs_SetProcessName()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetProcessName(Ability_ChildProcessConfigs* configs,const char* processName)
```

**Description**

Sets the process name in the child process configuration information object. This setting only takes effect when the [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs) or [OH_Ability_CreateNativeChildProcessWithConfigs](#oh_ability_createnativechildprocesswithconfigs) interface is called.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [Ability_ChildProcessConfigs](capi-ability-childprocessconfigs.md)* configs | Pointer to the child process configuration information object. It cannot be nullptr. |
| const char* processName | The child process name to set. It must be a non-empty string consisting of letters, digits, and underscores only, with a maximum length of 64 characters. The final process name is {bundleName}:{processName}. If no process name is set, the system default process name is used. |

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | NCP_NO_ERROR - The operation is successful.<br>NCP_ERR_INVALID_PARAM - Returns NCP_ERR_INVALID_PARAM if configs is nullptr, processName contains characters other than letters, digits, and underscores, processName exceeds 64 characters, or processName is an empty string. |

### OH_Ability_OnNativeChildProcessStarted()

```c
typedef void (*OH_Ability_OnNativeChildProcessStarted)(int errCode, OHIPCRemoteProxy *remoteProxy)
```

**Description**

Defines a callback function for notifying the child process startup result.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| int errCode | Error code returned by the callback function. The available values are as follows:<br>[NCP_NO_ERROR](#ability_nativechildprocess_errcode) - The child process is created successfully.<br>[NCP_ERR_LIB_LOADING_FAILED](#ability_nativechildprocess_errcode) - Failed to load the dynamic link library file, or the dynamic link library does not implement the required exported functions.<br>[NCP_ERR_CONNECTION_FAILED](#ability_nativechildprocess_errcode) - The OnConnect method implemented in the dynamic link library does not return a valid IPC Stub pointer.<br>For details, see [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode). |
| [OHIPCRemoteProxy](../apis-ipc-kit/capi-ohipcparcel-ohipcremoteproxy.md) *remoteProxy | Pointer to the IPC object of the child process. It may be nullptr when an exception occurs. Call [OH_IPCRemoteProxy_Destroy](../apis-ipc-kit/capi-ipc-cremote-object-h.md#oh_ipcremoteproxy_destroy) to release it after use. |

**Reference**

[OH_IPCRemoteProxy_Destroy](../apis-ipc-kit/capi-ipc-cremote-object-h.md#oh_ipcremoteproxy_destroy)

### OH_Ability_CreateNativeChildProcess()

```c
int OH_Ability_CreateNativeChildProcess(const char* libName,OH_Ability_OnNativeChildProcessStarted onProcessStarted)
```

**Description**

Creates a child process and loads the dynamic link library file specified by the parameter. The child process startup result is notified to the caller asynchronously through a callback. The callback is executed in an independent thread, so thread synchronization must be ensured, and it must not perform time-consuming operations to avoid long-time blocking. Creating the ArkTS basic runtime environment is not supported in the child process.

The DLL specified must implement and export the following functions:<br>1. OHIPCRemoteStub* NativeChildProcess_OnConnect()<br>2. void NativeChildProcess_MainProc()<br>The processing logic sequence is shown in the following pseudocode:<br>Parent process:<br>1. OH_Ability_CreateNativeChildProcess(libName, onProcessStartedCallback)<br>Child process:<br>2. dlopen(libName)<br>3. dlsym("NativeChildProcess_OnConnect")<br>4. dlsym("NativeChildProcess_MainProc")<br>5. ipcRemote = NativeChildProcess_OnConnect()<br>6. NativeChildProcess_MainProc()<br>Parent process:<br>7. onProcessStartedCallback(ipcRemote, errCode)<br>Child process:<br>8. The child process exits after the NativeChildProcess_MainProc() function is returned.

**Device behavior difference:** For API version 13 and earlier versions, this interface can work normally in PC/2in1 devices, returns the [NCP_ERR_NOT_SUPPORTED](#ability_nativechildprocess_errcode) error code in Tablet devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other devices. For API version 14 and later versions, this interface can work normally in PC/2in1 and Tablet devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other devices.

> **NOTE**
>
> For API version 14 and earlier versions, a single process can start only one Native child process. Starting from API version 15, a single process can start a maximum of 50 Native child processes using this interface. Starting from API version 20, a single process can start a maximum of 50 Native child processes using this interface and the [OH_Ability_CreateNativeChildProcessWithConfigs](#oh_ability_createnativechildprocesswithconfigs) interface combined. Calling this interface beyond this limit returns the [NCP_ERR_MAX_CHILD_PROCESSES_REACHED](#ability_nativechildprocess_errcode) error code.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* libName | Pointer to the name of the DLL file loaded in the child process. The value cannot be nullptr.|
| [OH_Ability_OnNativeChildProcessStarted](#oh_ability_onnativechildprocessstarted) onProcessStarted | Pointer to the callback function used to notify the child process of the startup result. It cannot be nullptr. For details, see [OH_Ability_OnNativeChildProcessStarted](#oh_ability_onnativechildprocessstarted). |

**Returns**

| Type| Description|
| -- | -- |
| int | [NCP_NO_ERROR](#ability_nativechildprocess_errcode) - The call is successful, but the actual startup result of the child process is notified by the callback function.<br>[NCP_ERR_INVALID_PARAM](#ability_nativechildprocess_errcode) - Invalid dynamic library name or callback function pointer.<br>[NCP_ERR_NOT_SUPPORTED](#ability_nativechildprocess_errcode) - The current device does not support creating a Native child process.<br>[NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) - The multi-process mode is disabled on the current device.<br>[NCP_ERR_ALREADY_IN_CHILD](#ability_nativechildprocess_errcode) - Creating a child process again within a child process is not allowed.<br>[NCP_ERR_MAX_CHILD_PROCESSES_REACHED](#ability_nativechildprocess_errcode) - The maximum number of Native child processes has been reached.<br>For details, see [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode). |

**Reference**

[OH_Ability_OnNativeChildProcessStarted](#oh_ability_onnativechildprocessstarted)

### OH_Ability_CreateNativeChildProcessWithConfigs()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_CreateNativeChildProcessWithConfigs(const char* libName,Ability_ChildProcessConfigs* configs, OH_Ability_OnNativeChildProcessStarted onProcessStarted)
```

**Description**

Creates a child process based on the passed child process configuration information and loads the dynamic link library file specified by the parameter. The child process startup result is notified to the caller asynchronously through a callback. The callback is executed in an independent thread, so thread synchronization must be ensured, and it must not perform time-consuming operations to avoid long-time blocking. Creating the ArkTS basic runtime environment is not supported in the child process.

The dynamic library specified by the parameter must implement and export the following functions:<br>1. OHIPCRemoteStub* NativeChildProcess_OnConnect()<br>2. void NativeChildProcess_MainProc()<br>The processing logic sequence is as shown in the following pseudo-code:<br>Main process:<br>1. OH_Ability_CreateNativeChildProcessWithConfigs(libName, configs, onProcessStartedCallback)<br>Child process:<br>2. dlopen(libName)<br>3. dlsym("NativeChildProcess_OnConnect")<br>4. dlsym("NativeChildProcess_MainProc")<br>5. ipcRemote = NativeChildProcess_OnConnect()<br>6. NativeChildProcess_MainProc()<br>Main process:<br>7. onProcessStartedCallback(errCode, ipcRemote)<br>Child process:<br>8. After the NativeChildProcess_MainProc() function returns, the child process exits.

**Device behavior difference:** This interface can be called normally in PC/2in1 and Tablet devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other devices.

> **NOTE**
>
> A single process can start a maximum of 50 Native child processes using this interface and the [OH_Ability_CreateNativeChildProcess](#oh_ability_createnativechildprocess) interface combined. Calling this interface beyond this limit returns the [NCP_ERR_MAX_CHILD_PROCESSES_REACHED](#ability_nativechildprocess_errcode) error code.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char* libName | Pointer to the name of the DLL file loaded in the child process. The value cannot be nullptr.|
| [Ability_ChildProcessConfigs](capi-ability-childprocessconfigs.md)* configs | Pointer to a child process configuration object. The value cannot be nullptr.|
| [OH_Ability_OnNativeChildProcessStarted](#oh_ability_onnativechildprocessstarted) onProcessStarted | Callback function pointer for notifying the child process startup result. It cannot be nullptr. For details, see OH_Ability_OnNativeChildProcessStarted. |

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | Result code.<br>Returns NCP_NO_ERROR if the operation is successful.<br>Returns NCP_ERR_INVALID_PARAM if the input parameter is invalid.<br>Returns NCP_ERR_NOT_SUPPORTED if the current device does not support creating a Native child process.<br>Returns NCP_ERR_MULTI_PROCESS_DISABLED if the multi-process mode is disabled on the current device and starting a child process is not allowed.<br>Returns NCP_ERR_ALREADY_IN_CHILD if creating a child process again within a child process is not allowed.<br>Returns NCP_ERR_MAX_CHILD_PROCESSES_REACHED if the maximum number of Native child processes is exceeded.<br>For details, see Ability_NativeChildProcess_ErrCode. |

**Reference**

[OH_Ability_OnNativeChildProcessStarted](#oh_ability_onnativechildprocessstarted)

### OH_Ability_StartNativeChildProcess()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_StartNativeChildProcess(const char* entry, NativeChildProcess_Args args,NativeChildProcess_Options options, int32_t *pid)
```

**Description**

Starts a native child process, loads the dynamic link library file specified by the parameter, and calls the entry function. The specified dynamic library must implement and export a function (the function name can be customized) that takes [NativeChildProcess_Args](capi-nativechildprocess-args.md) as the parameter. Arguments can be passed to the child process. Creating the ArkTS basic runtime environment is not supported in the child process.

The following is an example:<br>void Main(NativeChildProcess_Args args);<br>The processing logic sequence is shown in the following pseudocode:<br>Parent process:<br>1. OH_Ability_StartNativeChildProcess(entryPoint, args, options)<br>Child process:<br>2. dlopen(libName)<br>3. dlsym("Main")<br>4. Main(args)<br>5. The child process exits after the Main(args) function returns.

**Device behavior difference:** In API version 13 and earlier versions, this interface can work normally in PC/2in1 devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other device types. Starting from API version 14, this interface can work normally in PC/2in1 and Tablet devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other device types.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| const char* entry | Symbol and entry function of the dynamic library called in the child process, separated by a colon (for example, "libentry.so:Main"). It cannot be nullptr. |
| [NativeChildProcess_Args](capi-nativechildprocess-args.md) args | Parameters passed to the child process.|
| [NativeChildProcess_Options](capi-nativechildprocess-options.md) options | Child process options.|
| int32_t *pid | Output parameter, which cannot be nullptr. It indicates the PID of the started child process, and is valid only when the interface is called successfully. |

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | NCP_NO_ERROR - Returns NCP_NO_ERROR if the call is successful.<br>NCP_ERR_INVALID_PARAM - Returns NCP_ERR_INVALID_PARAM if the dynamic library name or callback function pointer is invalid.<br>NCP_ERR_NOT_SUPPORTED - Returns NCP_ERR_NOT_SUPPORTED if the current device does not support creating a Native child process.<br>NCP_ERR_MULTI_PROCESS_DISABLED - Returns NCP_ERR_MULTI_PROCESS_DISABLED if the current device has disabled the multi-process mode and does not allow starting a child process.<br>NCP_ERR_ALREADY_IN_CHILD - Returns NCP_ERR_ALREADY_IN_CHILD if creating a child process again in a child process is not allowed.<br>NCP_ERR_MAX_CHILD_PROCESSES_REACHED - Returns NCP_ERR_MAX_CHILD_PROCESSES_REACHED if the maximum number of Native child processes is reached.<br>For details, see the definition of Ability_NativeChildProcess_ErrCode. |

**Reference**

[OH_Ability_OnNativeChildProcessStarted](#oh_ability_onnativechildprocessstarted)

### OH_Ability_StartNativeChildProcessWithConfigs()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_StartNativeChildProcessWithConfigs(const char* entry, NativeChildProcess_Args args, Ability_ChildProcessConfigs* configs, int32_t *pid)
```

**Description**

Starts a native child process based on the child process configuration information in the parameter, loads the specified dynamic link library file, and calls the entry function. Arguments can be passed to the child process. Creating the ArkTS basic runtime environment is not supported in the child process. The specified dynamic library must implement and export a function (the function name can be customized) that takes [NativeChildProcess_Args](capi-nativechildprocess-args.md) as the parameter.

The following is an example:<br>void Main(NativeChildProcess_Args args);<br>The processing logic sequence is shown in the following pseudocode:<br>Parent process:<br>1. OH_Ability_StartNativeChildProcessWithConfigs(entryPoint, args, configs, &pid)<br>Child process:<br>2. dlopen(libName)<br>3. dlsym("Main")<br>4. Main(args)<br>5. The child process exits after the Main(args) function returns.

**Device behavior difference:** This interface can be called normally in PC/2in1 and Tablet devices, and returns the [NCP_ERR_MULTI_PROCESS_DISABLED](#ability_nativechildprocess_errcode) error code in other device types.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char* entry | Pointer to the symbol and entry function of the dynamic library called in the child process, separated by a colon (:), for example, **libentry.so:Main**. The value cannot be nullptr.|
| [NativeChildProcess_Args](capi-nativechildprocess-args.md) args | Arguments passed to the child process, which cannot be nullptr. |
| [Ability_ChildProcessConfigs](capi-ability-childprocessconfigs.md)* configs | Pointer to the child process configuration information, which cannot be nullptr. This parameter can be used to set the data sandbox and network environment sharing mode, UID isolation, process name, and other configurations of the child process. |
| int32_t *pid | Pointer to the output parameter, which cannot be nullptr. It indicates the PID of the started child process, which is valid only when the interface is called successfully. |

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | NCP_NO_ERROR - The operation is successful.<br>NCP_ERR_INVALID_PARAM - The input parameter is invalid.<br>NCP_ERR_NOT_SUPPORTED - The current device does not support creating a Native child process.<br>NCP_ERR_MULTI_PROCESS_DISABLED - The multi-process mode is disabled on the current device, and starting a child process is not allowed.<br>NCP_ERR_ALREADY_IN_CHILD - Creating a child process again in a child process is not allowed.<br>NCP_ERR_MAX_CHILD_PROCESSES_REACHED - The maximum number of Native child processes is reached.<br>For details, see Ability_NativeChildProcess_ErrCode. |

### OH_Ability_GetCurrentChildProcessArgs()

```c
NativeChildProcess_Args* OH_Ability_GetCurrentChildProcessArgs()
```

**Description**

After a child process is started by calling [OH_Ability_StartNativeChildProcess](#oh_ability_startnativechildprocess) or [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs), the child process can obtain the startup parameter [NativeChildProcess_Args](capi-nativechildprocess-args.md) in any so and any child thread. The parameter is passed when the child process is started and stored in the process global context. Its lifecycle spans the entire running period of the child process, and it can be obtained at any location in the child process at any time.

**Since**: 17

**Returns**

| Type                          | Description|
|------------------------------| -- |
| [NativeChildProcess_Args](capi-nativechildprocess-args.md)* | Pointer to the startup parameters of the child process.|

### OH_Ability_OnNativeChildProcessExit()

```c
typedef void (*OH_Ability_OnNativeChildProcessExit)(int32_t pid, int32_t signal)
```

**Description**

Callback function used to obtain the exit information of a native child process.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| int32_t pid | ID of the exited child process. |
| int32_t signal | Exit signal value of the child process, indicating the reason for the child process exit. Common signal values include: 1 (SIGHUP, hangup), 2 (SIGINT, interrupt), 9 (SIGKILL, forced termination), 15 (SIGTERM, termination), and so on. |

**See**

[OH_Ability_RegisterNativeChildProcessExitCallback](#oh_ability_registernativechildprocessexitcallback)

[OH_Ability_UnregisterNativeChildProcessExitCallback](#oh_ability_unregisternativechildprocessexitcallback)

### OH_Ability_RegisterNativeChildProcessExitCallback()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_RegisterNativeChildProcessExitCallback(OH_Ability_OnNativeChildProcessExit onProcessExit)
```

**Description**

Registers the callback function for native child process exit. The registered callback function is triggered only when a child process started by [OH_Ability_StartNativeChildProcess](#oh_ability_startnativechildprocess), [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs), or [childProcessManager.startNativeChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartnativechildprocess13) exits. The callback function is executed in an independent thread, and is triggered after the child process exits. The signal parameter indicates the exit signal type of the child process. When the same callback function is registered repeatedly, it is executed only once when the child process exits. The callback function implementation must ensure thread synchronization and must not perform time-consuming operations.

The parameter must implement the entry function [OH_Ability_OnNativeChildProcessExit](#oh_ability_onnativechildprocessexit). For details, see [Registering the Native Child Process Exit Callback](../../application-models/capi-nativechildprocess-development-guideline.md#obtaining-native-child-process-exit-information).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Ability_OnNativeChildProcessExit](#oh_ability_onnativechildprocessexit) onProcessExit | Entry of the callback function for child process exit, which cannot be nullptr. |

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | Returns NCP_NO_ERROR if the call is successful.<br>Returns NCP_ERR_INVALID_PARAM if the input parameter onProcessExit is nullptr or invalid.<br>Returns NCP_ERR_INTERNAL if an internal error occurs.<br>For details, see Ability_NativeChildProcess_ErrCode. |

### OH_Ability_UnregisterNativeChildProcessExitCallback()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_UnregisterNativeChildProcessExitCallback(OH_Ability_OnNativeChildProcessExit onProcessExit)
```

**Description**

Unregisters the callback used to listen for child process exit.

The parameter must implement the entry function [OH_Ability_OnNativeChildProcessExit](#oh_ability_onnativechildprocessexit). For details, see [Unregistering the Native Child Process Exit Callback](../../application-models/capi-nativechildprocess-development-guideline.md#obtaining-native-child-process-exit-information).

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Ability_OnNativeChildProcessExit](#oh_ability_onnativechildprocessexit) onProcessExit | Entry of the callback function for child process exit. It cannot be nullptr. |

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | NCP_NO_ERROR - The call is successful.<br>NCP_ERR_INVALID_PARAM - Invalid parameter. The passed parameter onProcessExit is nullptr or invalid.<br>NCP_ERR_INTERNAL - Internal error.<br>NCP_ERR_CALLBACK_NOT_EXIST - The callback function is not found.<br>For details, see Ability_NativeChildProcess_ErrCode. |

### OH_Ability_KillChildProcess()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_KillChildProcess(int32_t pid)
```

**Description**

Terminates the child process created by the current process. This interface forcibly ends the child process by sending a termination signal, and the child process immediately stops execution and exits. After termination, the child process resources are reclaimed by the system, and the exit callback is triggered if it has been registered.

> **NOTE**
>
> This function cannot be used to terminate a child process started in SELF_FORK mode by calling [childProcessManager.startChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess).

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| int32_t pid | PID of the child process to terminate.|

**Returns**

| Type| Description|
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | NCP_NO_ERROR - The call is successful.<br> NCP_ERR_SERVICE_ERROR - The server is faulty.<br>NCP_ERR_INVALID_PID - The passed child process PID is invalid. The passed process PID does not exist, or is not the PID of a child process created by the current process, or belongs to a child process started by the [childProcessManager.startChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess) interface in SELF_FORK mode.<br>For details, see Ability_NativeChildProcess_ErrCode. |

### OH_Ability_IsNativeChildProcessSupported()

```c
bool OH_Ability_IsNativeChildProcessSupported()
```

**Description**

Queries whether the caller is allowed to create a [Native child process](../../application-models/ability-terminology.md#native-child-process) on this device.

**Since:** 26.0.0

**Return**

| Type | Description |
| -- | -- |
| bool | Whether the caller is allowed to create a Native child process.<br>true: the caller is allowed to create a Native child process.<br>false: the caller is not allowed to create a Native child process.<br>Default value: false. |

### OH_Ability_AcquireChildProcessInfos()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_AcquireChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle* infos, uint32_t* count)
```

**Description**

Obtains the information about all child processes of the current application, including the child processes started in the following ways:
- [OH_Ability_CreateNativeChildProcess](#oh_ability_createnativechildprocess) / [OH_Ability_CreateNativeChildProcessWithConfigs](#oh_ability_createnativechildprocesswithconfigs)
- [OH_Ability_StartNativeChildProcess](#oh_ability_startnativechildprocess) / [OH_Ability_StartNativeChildProcessWithConfigs](#oh_ability_startnativechildprocesswithconfigs)
- [childProcessManager.startChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess) (non-SELF_FORK mode)
- [childProcessManager.startArkChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartarkchildprocess12)
- [childProcessManager.startNativeChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartnativechildprocess13)

After the obtained `infos` is no longer needed, call [OH_AbilityRuntime_ReleaseChildProcessInfos](capi-child-process-info-h.md#oh_abilityruntime_releasechildprocessinfos) to release it and avoid memory leaks.

**Since:** 26.1.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfosHandle](capi-nativechildprocess-infos.md)* infos | Output parameter. Pointer to the handle of the child process information set. It cannot be nullptr. After the call succeeds, `*infos` points to the child process information set. After it is no longer needed, call [OH_AbilityRuntime_ReleaseChildProcessInfos](capi-child-process-info-h.md#oh_abilityruntime_releasechildprocessinfos) to release it. |
| uint32_t* count | Output parameter. Pointer to the number of child processes. It cannot be nullptr. After the call succeeds, `*count` indicates the number of child processes of the current application. If there is no child process, `*count` is 0. |

**Returns:**

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | Result code.<br>NCP_NO_ERROR - The operation is successful.<br>NCP_ERR_INVALID_PARAM - The input parameter infos or count is nullptr.<br>NCP_ERR_INTERNAL - An internal error occurs, for example, failing to connect to the system service.<br>For details, see Ability_NativeChildProcess_ErrCode. |