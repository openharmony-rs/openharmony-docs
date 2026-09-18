# native_child_process.h

## Overview

Declares the APIs used to create a native child process and establish an IPC channel between the parent and child processes.

**Library**: libchild_process.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 12

**Related module**: [ChildProcess](capi-childprocess.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NativeChildProcess_Fd](capi-childprocess-nativechildprocess-fd.md) | NativeChildProcess_Fd | The struct describes the information about the file descriptor passed to the child process. |
| [NativeChildProcess_FdList](capi-childprocess-nativechildprocess-fdlist.md) | NativeChildProcess_FdList | The struct describes a list of file descriptors passed to the child process. The list can contain a maximum of 16 entries. |
| [NativeChildProcess_Options](capi-childprocess-nativechildprocess-options.md) | NativeChildProcess_Options | The struct describes the options used for starting a child process. |
| [NativeChildProcess_Args](capi-childprocess-nativechildprocess-args.md) | NativeChildProcess_Args | The struct describes the parameters passed to the child process. |
| [Ability_ChildProcessConfigs](capi-childprocess-ability-childprocessconfigs.md) | Ability_ChildProcessConfigs | The struct describes the configuration information about a child process, including the child process name and the sharing mode of the data sandbox and network environment. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Ability_NativeChildProcess_ErrCode](#ability_nativechildprocess_errcode) | Ability_NativeChildProcess_ErrCode | Defines an enum for the error codes used by the native child process module. |
| [NativeChildProcess_IsolationMode](#nativechildprocess_isolationmode) | NativeChildProcess_IsolationMode | Enumerates the sharing modes available for the data sandbox and network environment of a native child process. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Ability_ChildProcessConfigs* OH_Ability_CreateChildProcessConfigs()](#oh_ability_createchildprocessconfigs) | - | Creates a child process configuration object. When this object is no longer needed, call [OH_Ability_DestroyChildProcessConfigs](capi-native-child-process-h.md#oh_ability_destroychildprocessconfigs) to destroy the object to prevent memory leakage. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_DestroyChildProcessConfigs(Ability_ChildProcessConfigs* configs)](#oh_ability_destroychildprocessconfigs) | - | Destroys a child process configuration object and releases its memory. After this function is called, do not use the destroyed object. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetIsolationMode(Ability_ChildProcessConfigs* configs, NativeChildProcess_IsolationMode isolationMode)](#oh_ability_childprocessconfigs_setisolationmode) | - | Sets the sharing mode of the data sandbox and network environment for a child process configuration object. For details, see [NativeChildProcess_IsolationMode](capi-native-child-process-h.md#nativechildprocess_isolationmode). This setting takes effect only when [OH_Ability_StartNativeChildProcessWithConfigs](capi-native-child-process-h.md#oh_ability_startnativechildprocesswithconfigs) or [OH_Ability_CreateNativeChildProcessWithConfigs](capi-native-child-process-h.md#oh_ability_createnativechildprocesswithconfigs) is called. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetIsolationUid(Ability_ChildProcessConfigs* configs, bool isolationUid)](#oh_ability_childprocessconfigs_setisolationuid) | - | Sets whether the child process uses an independent UID. For example, in browser security hardening scenarios, you can isolate the UIDs of the main process and its child processes. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetProcessName(Ability_ChildProcessConfigs* configs, const char* processName)](#oh_ability_childprocessconfigs_setprocessname) | - | Sets the process name in a child process configuration object. |
| [typedef void (\*OH_Ability_OnNativeChildProcessStarted)(int errCode, OHIPCRemoteProxy *remoteProxy)](#oh_ability_onnativechildprocessstarted) | OH_Ability_OnNativeChildProcessStarted | Defines a callback function for notifying the child process startup result. |
| [int OH_Ability_CreateNativeChildProcess(const char* libName, OH_Ability_OnNativeChildProcessStarted onProcessStarted)](#oh_ability_createnativechildprocess) | - | Creates a child process, loads the specified dynamic library file, and returns the startup result asynchronously through a callback parameter. The callback notification is an independent thread. When implementing the callback function, pay attention to thread synchronization and do not perform time-consuming operations to avoid long-time blocking. The dynamic library specified must implement and export the following functions: 1. OHIPCRemoteStub* NativeChildProcess_OnConnect() 2. void NativeChildProcess_MainProc()<br> The processing logic sequence is shown in the following pseudocode: Main process: 1. OH_Ability_CreateNativeChildProcess(libName, onProcessStartedCallback) Child process: 2. dlopen(libName) 3. dlsym("NativeChildProcess_OnConnect") 4. dlsym("NativeChildProcess_MainProc") 5. ipcRemote = NativeChildProcess_OnConnect() 6. NativeChildProcess_MainProc() Main process: 7. onProcessStartedCallback(ipcRemote, errCode) Child process: 8. The child process exits after the NativeChildProcess_MainProc() function is returned. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_CreateNativeChildProcessWithConfigs(const char* libName, Ability_ChildProcessConfigs* configs, OH_Ability_OnNativeChildProcessStarted onProcessStarted)](#oh_ability_createnativechildprocesswithconfigs) | - | Creates a child process based on a child process configuration object and loads the specified dynamic library file. The startup result is asynchronously communicated to the caller via a callback. The callback runs in a separate thread. You must ensure thread synchronization and avoid time-consuming operations to prevent delays. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_StartNativeChildProcess(const char* entry, NativeChildProcess_Args args, NativeChildProcess_Options options, int32_t *pid)](#oh_ability_startnativechildprocess) | - | Starts a native child process, loads the specified dynamic library file, and calls the entry function. The specified dynamic library must implement and export a function that accepts [NativeChildProcess_Args](capi-childprocess-nativechildprocess-args.md) as its parameter (you can customize the function name). Arguments can be passed to the child process. The ArkTS basic runtime environment cannot be created in the child process.<br> The processing logic sequence is shown in the following pseudocode: Main process: 1. OH_Ability_StartNativeChildProcess(entryPoint, args, options) Child process: 2. dlopen(libName) 3. dlsym("Main") 4. Main(args) 5. The child process exits after the Main(args) function is returned |
| [Ability_NativeChildProcess_ErrCode OH_Ability_StartNativeChildProcessWithConfigs(const char* entry, NativeChildProcess_Args args, Ability_ChildProcessConfigs* configs, int32_t *pid)](#oh_ability_startnativechildprocesswithconfigs) | - | Starts a native child process based on the child process configuration object, loads the specified dynamic library file, and calls the entry function. Arguments can be passed to the child process. The specified dynamic library must implement and export a function that accepts [NativeChildProcess_Args](capi-childprocess-nativechildprocess-args.md) as its parameter (you can customize the function name).<br> The processing logic sequence is shown in the following pseudocode: Main process: 1. OH_Ability_StartNativeChildProcessWithConfigs(entryPoint, args, configs, &pid) Child process: 2. dlopen(libName) 3. dlsym("Main") 4. Main(args) 5. The child process exits after the Main(args) function is returned |
| [NativeChildProcess_Args* OH_Ability_GetCurrentChildProcessArgs()](#oh_ability_getcurrentchildprocessargs) | - | Used by a child process, after being started by calling [OH_Ability_StartNativeChildProcess](capi-native-child-process-h.md#oh_ability_startnativechildprocess), to obtain the startup parameter [NativeChildProcess_Args](capi-childprocess-nativechildprocess-args.md) from any .so file or child thread. |
| [typedef void (\*OH_Ability_OnNativeChildProcessExit)(int32_t pid, int32_t signal)](#oh_ability_onnativechildprocessexit) | OH_Ability_OnNativeChildProcessExit | Defines a callback to listen for child process exit. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_RegisterNativeChildProcessExitCallback(OH_Ability_OnNativeChildProcessExit onProcessExit)](#oh_ability_registernativechildprocessexitcallback) | - | Registers a callback to listen for child process exit. When a child process started by calling [OH_Ability_StartNativeChildProcess](capi-native-child-process-h.md#oh_ability_startnativechildprocess) or {@link startNativeChildProcess in @ohos.app.ability.childProcessManager} exits abnormally, the callback function is invoked. If the same callback function is registered multiple times, the callback function is executed only once when the child process exits. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_UnregisterNativeChildProcessExitCallback(OH_Ability_OnNativeChildProcessExit onProcessExit)](#oh_ability_unregisternativechildprocessexitcallback) | - | Unregisters the callback used to listen for child process exit. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_KillChildProcess(int32_t pid)](#oh_ability_killchildprocess) | - | Terminates a child process created by the current process. |
| [bool OH_Ability_IsNativeChildProcessSupported()](#oh_ability_isnativechildprocesssupported) | - | Check whether the caller is allowed to use native process capabilities. |
| [Ability_NativeChildProcess_ErrCode OH_Ability_AcquireChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle* infos, uint32_t* count)](#oh_ability_acquirechildprocessinfos) | - | Acquires child process infos of the current application.<br> Includes child processes created via: - OH_Ability_CreateNativeChildProcess / OH_Ability_CreateNativeChildProcessWithConfigs - OH_Ability_StartNativeChildProcess / OH_Ability_StartNativeChildProcessWithConfigs - childProcessManager.startChildProcess (non-SELF_FORK mode) - childProcessManager.startArkChildProcess - childProcessManager.startNativeChildProcess |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_Ability_OnNativeChildProcessStarted)(int errCode, OHIPCRemoteProxy *remoteProxy) | Defines a callback function for notifying the child process startup result.<br>**Since**: 12 |
| void (*OH_Ability_OnNativeChildProcessExit)(int32_t pid, int32_t signal) | Defines a callback to listen for child process exit.<br>**Since**: 20 |

## Enum type description

### Ability_NativeChildProcess_ErrCode

```c
enum Ability_NativeChildProcess_ErrCode
```

**Description**

Defines an enum for the error codes used by the native child process module.

**Since**: 12

| Enum item | Description |
| -- | -- |
| NCP_NO_ERROR = 0 |  |
| NCP_ERR_INVALID_PARAM = 401 |  |
| NCP_ERR_NOT_SUPPORTED = 801 |  |
| NCP_ERR_INTERNAL = 16000050 |  |
| NCP_ERR_BUSY = 16010001 |  |
| NCP_ERR_TIMEOUT = 16010002 |  |
| NCP_ERR_SERVICE_ERROR = 16010003 |  |
| NCP_ERR_MULTI_PROCESS_DISABLED = 16010004 |  |
| NCP_ERR_ALREADY_IN_CHILD = 16010005 |  |
| NCP_ERR_MAX_CHILD_PROCESSES_REACHED = 16010006 |  |
| NCP_ERR_LIB_LOADING_FAILED = 16010007 |  |
| NCP_ERR_CONNECTION_FAILED = 16010008 |  |
| NCP_ERR_CALLBACK_NOT_EXIST = 16010009 |  |
| NCP_ERR_INVALID_PID = 16010010 |  |

### NativeChildProcess_IsolationMode

```c
enum NativeChildProcess_IsolationMode
```

**Description**

Enumerates the sharing modes available for the data sandbox and network environment of a native child process.

**Since**: 13

| Enum item | Description |
| -- | -- |
| NCP_ISOLATION_MODE_NORMAL = 0 |  |
| NCP_ISOLATION_MODE_ISOLATED = 1 |  |


## Function description

### OH_Ability_CreateChildProcessConfigs()

```c
Ability_ChildProcessConfigs* OH_Ability_CreateChildProcessConfigs()
```

**Description**

Creates a child process configuration object. When this object is no longer needed, call [OH_Ability_DestroyChildProcessConfigs](capi-native-child-process-h.md#oh_ability_destroychildprocessconfigs) to destroy the object to prevent memory leakage.

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_ChildProcessConfigs*](capi-childprocess-ability-childprocessconfigs.md) | Pointer to the [Ability_ChildProcessConfigs](capi-childprocess-ability-childprocessconfigs.md) object: The call is successful.       nullptr: An internal error occurs or memory allocation fails. |

### OH_Ability_DestroyChildProcessConfigs()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_DestroyChildProcessConfigs(Ability_ChildProcessConfigs* configs)
```

**Description**

Destroys a child process configuration object and releases its memory. After this function is called, do not use the destroyed object.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Ability_ChildProcessConfigs](capi-childprocess-ability-childprocessconfigs.md)* configs | Pointer to a child process configuration object. After this function is called, the object pointer becomes invalid. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | NCP_NO_ERROR: The call is successful.       NCP_ERR_INVALID_PARAM: An input parameter is nullptr. |

### OH_Ability_ChildProcessConfigs_SetIsolationMode()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetIsolationMode(Ability_ChildProcessConfigs* configs, NativeChildProcess_IsolationMode isolationMode)
```

**Description**

Sets the sharing mode of the data sandbox and network environment for a child process configuration object. For details, see [NativeChildProcess_IsolationMode](capi-native-child-process-h.md#nativechildprocess_isolationmode). This setting takes effect only when [OH_Ability_StartNativeChildProcessWithConfigs](capi-native-child-process-h.md#oh_ability_startnativechildprocesswithconfigs) or [OH_Ability_CreateNativeChildProcessWithConfigs](capi-native-child-process-h.md#oh_ability_createnativechildprocesswithconfigs) is called.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Ability_ChildProcessConfigs](capi-childprocess-ability-childprocessconfigs.md)* configs | Pointer to a child process configuration object. The value cannot be nullptr. |
| [NativeChildProcess_IsolationMode](capi-native-child-process-h.md#nativechildprocess_isolationmode) isolationMode | Sharing mode of the data sandbox and network environment. For details, see **<br>NativeChildProcess_IsolationMode**. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | NCP_NO_ERROR: The call is successful.       NCP_ERR_INVALID_PARAM: The parameter configs is nullptr. |

### OH_Ability_ChildProcessConfigs_SetIsolationUid()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetIsolationUid(Ability_ChildProcessConfigs* configs, bool isolationUid)
```

**Description**

Sets whether the child process uses an independent UID. For example, in browser security hardening scenarios, you can isolate the UIDs of the main process and its child processes.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Ability_ChildProcessConfigs](capi-childprocess-ability-childprocessconfigs.md)* configs | Pointer to a child process configuration object. The value cannot be nullptr. |
| bool isolationUid | Whether the child process uses an independent UID. **true** if the child process uses an independent UID; **false** if the child process and the main process share the same UID. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | NCP_NO_ERROR: The call is successful.       NCP_ERR_INVALID_PARAM: The parameter configs is nullptr. |

### OH_Ability_ChildProcessConfigs_SetProcessName()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_ChildProcessConfigs_SetProcessName(Ability_ChildProcessConfigs* configs, const char* processName)
```

**Description**

Sets the process name in a child process configuration object.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Ability_ChildProcessConfigs](capi-childprocess-ability-childprocessconfigs.md)* configs | Pointer to a child process configuration object. The pointer cannot be null. |
| const char* processName | Pointer to the process name, which must be a non-empty string accepting only letters, digits, and underscores (_). The string contains a maximum of 64 characters. The final process name is in the format of {<br>     bundleName}:{processName}. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | <ul>       <li>[NCP_NO_ERROR](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if the call is successful.</li>       <li>[NCP_ERR_INVALID_PARAM](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if the input parameter configs is nullptr, or processName contains       characters other than letters, digits, and underscores (_).</li>       </ul> |

### OH_Ability_OnNativeChildProcessStarted()

```c
typedef void (*OH_Ability_OnNativeChildProcessStarted)(int errCode, OHIPCRemoteProxy *remoteProxy)
```

**Description**

Defines a callback function for notifying the child process startup result.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int errCode | Error code returned by the callback function. [NCP_NO_ERROR](capi-native-child-process-h.md#ability_nativechildprocess_errcode): The child process is created successfully. [NCP_ERR_LIB_LOADING_FAILED](capi-native-child-process-h.md#ability_nativechildprocess_errcode): Loading the dynamic library file fails or the necessary export function is not implemented in the dynamic library. [NCP_ERR_CONNECTION_FAILED](capi-native-child-process-h.md#ability_nativechildprocess_errcode): The **OnConnect** method implemented in the dynamic library does not return a valid IPC stub pointer. For details, see [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode). |
| OHIPCRemoteProxy \*remoteProxy | Pointer to the IPC object of the child process. If an exception occurs, the value may be nullptr. The object must be released by calling {@link OH_IPCRemoteProxy_Destroy} when it is no longer needed. |

**Reference**:

[OH_Ability_CreateNativeChildProcess](capi-native-child-process-h.md#oh_ability_createnativechildprocess)
OH_IPCRemoteProxy_Destroy


### OH_Ability_CreateNativeChildProcess()

```c
int OH_Ability_CreateNativeChildProcess(const char* libName, OH_Ability_OnNativeChildProcessStarted onProcessStarted)
```

**Description**

Creates a child process, loads the specified dynamic library file, and returns the startup result asynchronously through a callback parameter. The callback notification is an independent thread. When implementing the callback function, pay attention to thread synchronization and do not perform time-consuming operations to avoid long-time blocking. The dynamic library specified must implement and export the following functions: 1. OHIPCRemoteStub* NativeChildProcess_OnConnect() 2. void NativeChildProcess_MainProc()<br> The processing logic sequence is shown in the following pseudocode: Main process: 1. OH_Ability_CreateNativeChildProcess(libName, onProcessStartedCallback) Child process: 2. dlopen(libName) 3. dlsym("NativeChildProcess_OnConnect") 4. dlsym("NativeChildProcess_MainProc") 5. ipcRemote = NativeChildProcess_OnConnect() 6. NativeChildProcess_MainProc() Main process: 7. onProcessStartedCallback(ipcRemote, errCode) Child process: 8. The child process exits after the NativeChildProcess_MainProc() function is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* libName | Pointer to the name of the dynamic library file loaded in the child process. The value cannot be nullptr. |
| [OH_Ability_OnNativeChildProcessStarted](capi-native-child-process-h.md#oh_ability_onnativechildprocessstarted) onProcessStarted | Pointer to the callback function for notifying the child process startup result. The value cannot be nullptr. For details, see [OH_Ability_OnNativeChildProcessStarted](capi-native-child-process-h.md#oh_ability_onnativechildprocessstarted). |

**Returns**:

| Type | Description |
| -- | -- |
| int | [NCP_NO_ERROR](capi-native-child-process-h.md#ability_nativechildprocess_errcode): The call is successful, but the actual startup result is notified by the callback       function.       [NCP_ERR_INVALID_PARAM](capi-native-child-process-h.md#ability_nativechildprocess_errcode): The dynamic library name or callback function pointer is invalid.       [NCP_ERR_NOT_SUPPORTED](capi-native-child-process-h.md#ability_nativechildprocess_errcode): The device does not support the creation of native child processes.       [NCP_ERR_MULTI_PROCESS_DISABLED](capi-native-child-process-h.md#ability_nativechildprocess_errcode): Multi-process mode is disabled on the device.       [NCP_ERR_ALREADY_IN_CHILD](capi-native-child-process-h.md#ability_nativechildprocess_errcode): A process cannot be created in a child process.       [NCP_ERR_MAX_CHILD_PROCESSES_REACHED](capi-native-child-process-h.md#ability_nativechildprocess_errcode): The number of native child processes reaches the maximum.       For details, see [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode). |

**Reference**:

[OH_Ability_OnNativeChildProcessStarted](capi-native-child-process-h.md#oh_ability_onnativechildprocessstarted)


### OH_Ability_CreateNativeChildProcessWithConfigs()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_CreateNativeChildProcessWithConfigs(const char* libName, Ability_ChildProcessConfigs* configs, OH_Ability_OnNativeChildProcessStarted onProcessStarted)
```

**Description**

Creates a child process based on a child process configuration object and loads the specified dynamic library file. The startup result is asynchronously communicated to the caller via a callback. The callback runs in a separate thread. You must ensure thread synchronization and avoid time-consuming operations to prevent delays.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* libName | Pointer to the name of the dynamic library file loaded in the child process. The value cannot be nullptr. |
| [Ability_ChildProcessConfigs](capi-childprocess-ability-childprocessconfigs.md)* configs | Pointer to a child process configuration object. The value cannot be nullptr. |
| [OH_Ability_OnNativeChildProcessStarted](capi-native-child-process-h.md#oh_ability_onnativechildprocessstarted) onProcessStarted | Pointer to the callback function for notifying the child process startup result. The value cannot be nullptr. For details, see **OH_Ability_OnNativeChildProcessStarted**. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | <ul>       <li>[NCP_NO_ERROR](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if the call is successful.</li>       <li>[NCP_ERR_INVALID_PARAM](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if an input parameter is invalid.</li>       <li>[NCP_ERR_NOT_SUPPORTED](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if the device does not support the creation of native child processes.</li>       <li>[NCP_ERR_MULTI_PROCESS_DISABLED](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if multi-process mode is disabled on the device, and the child       process cannot be started.</li>       <li>[NCP_ERR_ALREADY_IN_CHILD](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if a process cannot be created in a child process.</li>       <li>[NCP_ERR_MAX_CHILD_PROCESSES_REACHED](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if the maximum number of native child processes has been       reached.</li>       </ul> |

**Reference**:

[OH_Ability_OnNativeChildProcessStarted](capi-native-child-process-h.md#oh_ability_onnativechildprocessstarted)


### OH_Ability_StartNativeChildProcess()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_StartNativeChildProcess(const char* entry, NativeChildProcess_Args args, NativeChildProcess_Options options, int32_t *pid)
```

**Description**

Starts a native child process, loads the specified dynamic library file, and calls the entry function. The specified dynamic library must implement and export a function that accepts [NativeChildProcess_Args](capi-childprocess-nativechildprocess-args.md) as its parameter (you can customize the function name). Arguments can be passed to the child process. The ArkTS basic runtime environment cannot be created in the child process.<br> The processing logic sequence is shown in the following pseudocode: Main process: 1. OH_Ability_StartNativeChildProcess(entryPoint, args, options) Child process: 2. dlopen(libName) 3. dlsym("Main") 4. Main(args) 5. The child process exits after the Main(args) function is returned

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* entry | Pointer to the dynamic library and entry function to be loaded by the child process, for example, **libEntry.so: Main**. The value cannot be nullptr. |
| [NativeChildProcess_Args](capi-childprocess-nativechildprocess-args.md) args | Parameters passed to the child process. |
| [NativeChildProcess_Options](capi-childprocess-nativechildprocess-options.md) options | Child process options. |
| int32_t *pid | Pointer to the ID of the child process. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | NCP_NO_ERROR: The call is successful.       NCP_ERR_INVALID_PARAM: The dynamic library name or callback function pointer is invalid.       NCP_ERR_NOT_SUPPORTED: The device does not support the creation of native child processes.       NCP_ERR_ALREADY_IN_CHILD: Multi-process mode is disabled on the device.       NCP_ERR_MAX_CHILD_PROCESSES_REACHED: The maximum number of native child processes has been reached.       For details about the error codes, see Ability_NativeChildProcess_ErrCode. |

**Reference**:

[OH_Ability_OnNativeChildProcessStarted](capi-native-child-process-h.md#oh_ability_onnativechildprocessstarted)


### OH_Ability_StartNativeChildProcessWithConfigs()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_StartNativeChildProcessWithConfigs(const char* entry, NativeChildProcess_Args args, Ability_ChildProcessConfigs* configs, int32_t *pid)
```

**Description**

Starts a native child process based on the child process configuration object, loads the specified dynamic library file, and calls the entry function. Arguments can be passed to the child process. The specified dynamic library must implement and export a function that accepts [NativeChildProcess_Args](capi-childprocess-nativechildprocess-args.md) as its parameter (you can customize the function name).<br> The processing logic sequence is shown in the following pseudocode: Main process: 1. OH_Ability_StartNativeChildProcessWithConfigs(entryPoint, args, configs, &pid) Child process: 2. dlopen(libName) 3. dlsym("Main") 4. Main(args) 5. The child process exits after the Main(args) function is returned

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* entry | Pointer to the symbol and entry function of the dynamic library called in the child process, separated by a colon (:), for example, **libentry.so:Main**. The value cannot be nullptr. |
| [NativeChildProcess_Args](capi-childprocess-nativechildprocess-args.md) args | Parameters passed to the child process. |
| [Ability_ChildProcessConfigs](capi-childprocess-ability-childprocessconfigs.md)* configs | Pointer to a child process configuration object. |
| int32_t *pid | Pointer to the ID of the child process. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | NCP_NO_ERROR: The call is successful.       NCP_ERR_INVALID_PARAM: An input parameter is invalid.       NCP_ERR_NOT_SUPPORTED: The device does not support the creation of native child processes.       NCP_ERR_ALREADY_IN_CHILD: A process cannot be created in a child process.       NCP_ERR_MAX_CHILD_PROCESSES_REACHED: The maximum number of native child processes has been reached.       For details about the error codes, see Ability_NativeChildProcess_ErrCode. |

### OH_Ability_GetCurrentChildProcessArgs()

```c
NativeChildProcess_Args* OH_Ability_GetCurrentChildProcessArgs()
```

**Description**

Used by a child process, after being started by calling [OH_Ability_StartNativeChildProcess](capi-native-child-process-h.md#oh_ability_startnativechildprocess), to obtain the startup parameter [NativeChildProcess_Args](capi-childprocess-nativechildprocess-args.md) from any .so file or child thread.

**Since**: 17

**Returns**:

| Type | Description |
| -- | -- |
| [NativeChildProcess_Args*](capi-childprocess-nativechildprocess-args.md) | Pointer to the startup parameters of the child process. |

### OH_Ability_OnNativeChildProcessExit()

```c
typedef void (*OH_Ability_OnNativeChildProcessExit)(int32_t pid, int32_t signal)
```

**Description**

Defines a callback to listen for child process exit.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t pid | Pointer to the ID of the child process. |
| int32_t signal | Signal for child process exit. |

### OH_Ability_RegisterNativeChildProcessExitCallback()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_RegisterNativeChildProcessExitCallback(OH_Ability_OnNativeChildProcessExit onProcessExit)
```

**Description**

Registers a callback to listen for child process exit. When a child process started by calling [OH_Ability_StartNativeChildProcess](capi-native-child-process-h.md#oh_ability_startnativechildprocess) or {@link startNativeChildProcess in @ohos.app.ability.childProcessManager} exits abnormally, the callback function is invoked. If the same callback function is registered multiple times, the callback function is executed only once when the child process exits.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Ability_OnNativeChildProcessExit](capi-native-child-process-h.md#oh_ability_onnativechildprocessexit) onProcessExit | Entry point of the callback function to be called when the child process exits. The value cannot be nullptr. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | NCP_NO_ERROR: The call is successful.       NCP_ERR_INVALID_PARAM: An input parameter is invalid.       NCP_ERR_INTERNAL: An internal error occurs.       For details, see Ability_NativeChildProcess_ErrCode. |

### OH_Ability_UnregisterNativeChildProcessExitCallback()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_UnregisterNativeChildProcessExitCallback(OH_Ability_OnNativeChildProcessExit onProcessExit)
```

**Description**

Unregisters the callback used to listen for child process exit.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Ability_OnNativeChildProcessExit](capi-native-child-process-h.md#oh_ability_onnativechildprocessexit) onProcessExit | Entry point of the callback function to be called when the child process exits. The value cannot be nullptr. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | NCP_NO_ERROR: The call is successful.       NCP_ERR_INVALID_PARAM: An input parameter is invalid.       NCP_ERR_INTERNAL: An internal error occurs.       NCP_ERR_CALLBACK_NOT_EXIST: The callback function is not found.       For details, see Ability_NativeChildProcess_ErrCode. |

### OH_Ability_KillChildProcess()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_KillChildProcess(int32_t pid)
```

**Description**

Terminates a child process created by the current process.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t pid | PID of the child process to terminate. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | NCP_NO_ERROR: The call is successful.       NCP_ERR_SERVICE_ERROR: Server error.       NCP_ERR_INVALID_PID: The input PID is invalid.       For details, see Ability_NativeChildProcess_ErrCode. |

### OH_Ability_IsNativeChildProcessSupported()

```c
bool OH_Ability_IsNativeChildProcessSupported()
```

**Description**

Check whether the caller is allowed to use native process capabilities.

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if the caller is allowed to create native child processes, false otherwise. |

### OH_Ability_AcquireChildProcessInfos()

```c
Ability_NativeChildProcess_ErrCode OH_Ability_AcquireChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle* infos, uint32_t* count)
```

**Description**

Acquires child process infos of the current application.<br> Includes child processes created via: - OH_Ability_CreateNativeChildProcess / OH_Ability_CreateNativeChildProcessWithConfigs - OH_Ability_StartNativeChildProcess / OH_Ability_StartNativeChildProcessWithConfigs - childProcessManager.startChildProcess (non-SELF_FORK mode) - childProcessManager.startArkChildProcess - childProcessManager.startNativeChildProcess

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfosHandle* infos | [out] Pointer to child process info collection. It must not be NULL. When no child processes exist, the dereferenced value of the pointer **infos** is set to nullptr. |
| uint32_t* count | [out] Pointer to the number of child processes. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [Ability_NativeChildProcess_ErrCode](capi-native-child-process-h.md#ability_nativechildprocess_errcode) | <ul>       <li>[NCP_NO_ERROR](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if the operation is successful.</li>       <li>[NCP_ERR_INVALID_PARAM](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if infos or count is nullptr.</li>       <li>[NCP_ERR_INTERNAL](capi-native-child-process-h.md#ability_nativechildprocess_errcode) if an internal error occurs, such as connect system service failed.</li>       </ul> |


