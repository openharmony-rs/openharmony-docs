# ipc_cskeleton.h
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=563b8be563e11a9d9d559f338c53d2269358d4f7 translatedAt=2026-11-04T03:40:59.974Z pushedAt=2026-11-04T10:13:14.845Z nl=1 -->

## Overview

This file provides C APIs for IPC framework features such as the token ID, credentials, PID/UID, and thread pool configuration. It is mainly used for context management and thread management in inter-process communication.

**File to include**: <IPCKit/ipc_cskeleton.h>

**Library**: libipc_capi.so

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCSkeleton](capi-ohipcskeleton.md)

## Summary

### Function

| Name| Description|
| ---- | ---- |
| [void OH_IPCSkeleton_JoinWorkThread(void)](#oh_ipcskeleton_joinworkthread) | Adds the current thread to the IPC worker thread pool so that it can participate in processing IPC requests. This is applicable to scenarios where a custom IPC request processing thread is required, for example, manually adding a worker thread when the IPC concurrent processing capability needs to be expanded, or using a dedicated thread to process IPC requests in specific business scenarios to improve response speed. After this function is called, the current thread is registered as an IPC worker thread and participates in processing IPC requests from other processes until OH_IPCSkeleton_StopWorkThread is called to exit the thread pool. |
| [void OH_IPCSkeleton_StopWorkThread(void)](#oh_ipcskeleton_stopworkthread) | Removes the current thread from the IPC worker thread pool so that it no longer participates in processing IPC requests. After this function is called, the current thread is removed from the IPC worker thread pool and is no longer assigned tasks for processing IPC requests, and the thread can perform other operations. |
| [uint64_t OH_IPCSkeleton_GetCallingTokenId(void)](#oh_ipcskeleton_getcallingtokenid) | Obtains the TokenId of the caller. This is applicable to scenarios such as permission verification and identity identification on the IPC server side, where identity-based access control can be implemented through the TokenId. This interface requires being called in the IPC context; otherwise, it returns the TokenId of the current process. |
| [uint64_t OH_IPCSkeleton_GetFirstTokenId(void)](#oh_ipcskeleton_getfirsttokenid) | Obtains the TokenId of the first caller in the IPC call chain. This interface requires being called in the IPC context; otherwise, it returns the TokenId of the current process. This is applicable to permission tracing and security audit scenarios in multi-level service calls, for example, tracing the identity of the original caller rather than the intermediate proxy service in permission auditing, and confirming the original permission source in cross-process permission inheritance verification. Returns the TokenId identifier of the first client that initiated the IPC call. |
| [uint64_t OH_IPCSkeleton_GetSelfTokenId(void)](#oh_ipcskeleton_getselftokenid) | Obtains the TokenId identifier of the current process itself. This is applicable to scenarios of process self-identity verification and permission status confirmation, for example, verifying the permission status of the process at service startup, confirming whether the process has the permission to access specific resources in permission checks, and identifying the current process identity in security audits. Returns the TokenId of the current process, regardless of whether it is called in the IPC context. |
| [uint64_t OH_IPCSkeleton_GetCallingPid(void)](#oh_ipcskeleton_getcallingpid) | Obtains the process ID of the caller. This is applicable to process-level permission control and security audit scenarios, for example, checking whether the caller process is in the allowed list in trustlist verification, recording the caller process information in audit logs for security tracing, and making permission decisions based on the process ID in cross-process access control. This interface requires being called in the IPC context; otherwise, it returns the current process ID. |
| [uint64_t OH_IPCSkeleton_GetCallingUid(void)](#oh_ipcskeleton_getcallinguid) | Obtains the user ID of the caller. This is applicable to user-level permission control and identity identification scenarios in multi-user environments, for example, determining access permissions based on the user ID in permission management, isolating data access of different users in multi-user systems, and recording the user identity in security audits for behavior tracing. This interface requires being called in the IPC context; otherwise, it returns the current user ID. |
| [int OH_IPCSkeleton_IsLocalCalling(void)](#oh_ipcskeleton_islocalcalling) | Checks whether the current IPC call is a local call. |
| [int OH_IPCSkeleton_SetMaxWorkThreadNum(const int maxThreadNum)](#oh_ipcskeleton_setmaxworkthreadnum) | Sets the maximum thread count of the IPC worker thread pool to control the concurrent processing capability of IPC requests. After this function is called, the IPC framework manages worker threads according to the set maximum thread count. When the number of concurrent IPC requests exceeds the thread count, the requests are queued and wait. |
| [int OH_IPCSkeleton_ResetCallingIdentity(char **identity, int32_t *len, OH_IPC_MemAllocator allocator)](#oh_ipcskeleton_resetcallingidentity) | Resets the caller identity credential to the identity credential of the current process (including TokenId, UID, and PID information), and returns the caller's credential information. This is applicable to scenarios where temporary privilege elevation or operations performed as the service process identity are required, for example, temporarily switching to the service identity when a system service needs to access protected resources, and performing privileged operations on behalf of the service in permission proxy scenarios. After this function is called, the identity credential of the current IPC context is switched to the credential of the current process, and the original caller's credential information is returned for subsequent restoration. |
| [int OH_IPCSkeleton_SetCallingIdentity(const char *identity)](#oh_ipcskeleton_setcallingidentity) | Restores the caller credential information to the IPC context. The identity credential of the IPC context is restored to the credential of the original caller. This function must be called in the IPC request processing context. This is applicable to scenarios where normal permissions are restored after a temporary privilege elevation operation is completed, for example, restoring the caller identity after the server completes access to protected resources, and restoring the caller's permission state after a permission proxy operation is completed. |
| [int OH_IPCSkeleton_IsHandlingTransaction(void)](#oh_ipcskeleton_ishandlingtransaction) | Checks whether an IPC request is being processed. This is applicable to scenarios where conditional judgment is required based on the current IPC processing state, such as avoiding re-entry and state checking. |

## Function Description

### OH_IPCSkeleton_JoinWorkThread()

```C
void OH_IPCSkeleton_JoinWorkThread(void)
```

**Description**

The current thread joins the IPC worker thread pool so that it can participate in processing IPC requests. This is applicable to scenarios where a custom IPC request processing thread is required. For example, worker threads are manually added when the IPC concurrent processing capability needs to be expanded, or a dedicated thread is used to process IPC requests in specific business scenarios to improve response speed. After this function is called, the current thread is registered as an IPC worker thread and participates in processing IPC requests from other processes until [OH_IPCSkeleton_StopWorkThread()](#oh_ipcskeleton_stopworkthread) is called to exit the thread pool.

- Call this function only in scenarios where IPC request processing is required.
- After this function is called, the thread blocks and waits to process IPC requests.
- It is recommended to use this function together with [OH_IPCSkeleton_StopWorkThread()](#oh_ipcskeleton_stopworkthread) to properly exit the thread pool.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

### OH_IPCSkeleton_StopWorkThread()

```C
void OH_IPCSkeleton_StopWorkThread(void)
```

**Description**

The current thread exits the IPC worker thread pool and no longer participates in processing IPC requests. After this function is called, the current thread is removed from the IPC worker thread pool, is no longer assigned tasks for processing IPC requests, and can perform other operations.

- Call this function when IPC request processing is no longer needed.
- Before calling this function, ensure that the current thread has joined the thread pool through [OH_IPCSkeleton_JoinWorkThread()](#oh_ipcskeleton_joinworkthread).
- Ensure that all IPC transactions are completed before the thread exits.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

### OH_IPCSkeleton_GetCallingTokenId()

```C
uint64_t OH_IPCSkeleton_GetCallingTokenId(void)
```

**Description**

Obtains the token ID of the caller. This is applicable to scenarios such as permission verification and identity identification on the IPC server side. Identity‑based access control can be implemented through the token ID. This API must be called in the IPC context. Otherwise, the local token ID is returned.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**

| Type| Description|
| ---- | ---- |
| uint64_t | Returns the caller token ID.|

### OH_IPCSkeleton_GetFirstTokenId()

```C
uint64_t OH_IPCSkeleton_GetFirstTokenId(void)
```

**Description**

Obtains the TokenId of the first caller in the IPC call chain. This API requires being called in the IPC context; otherwise, it returns the TokenId of the current process. This is applicable to permission tracing and security audit scenarios in multi-level service calls. For example, it is used in permission audits that need to trace the identity of the original caller rather than the intermediate proxy service, and in cross-process permission inheritance verification to confirm the original permission source. Returns the TokenId identifier of the first client that initiates the IPC call.

- This API is meaningful only in multi-level IPC call scenarios.
- In single-level call scenarios, the return value of this function is the same as that of [OH_IPCSkeleton_GetCallingTokenId()](#oh_ipcskeleton_getcallingtokenid).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**

| Type| Description|
| ---- | ---- |
| uint64_t | Returns the token ID of the first caller.|

### OH_IPCSkeleton_GetSelfTokenId()

```C
uint64_t OH_IPCSkeleton_GetSelfTokenId(void)
```

**Description**

Obtains the TokenId identifier of the current process. This is applicable to process self-identity verification and permission status confirmation scenarios. For example, it is used to verify the permission status of the process at service startup, to confirm in permission checks whether the process has the permission to access specific resources, and to identify the current process in security audits. Returns the TokenId of the current process, regardless of whether it is called in the IPC context.

- This function can be called in any context and does not depend on the IPC context.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**

| Type| Description|
| ---- | ---- |
| uint64_t | Returns the local token ID.|

### OH_IPCSkeleton_GetCallingPid()

```C
uint64_t OH_IPCSkeleton_GetCallingPid(void)
```

**Description**

Obtains the PID of the caller. This is applicable to process-level permission control and security audit scenarios, for example, checking whether the caller process is in the trustlist during trustlist verification, recording caller process information in audit logs for security tracing, and making permission decisions based on the PID in cross-process access control. This API must be called in the IPC context. Otherwise, the PID of the current process is returned.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**

| Type| Description|
| ---- | ---- |
| uint64_t | Returns the caller PID.|

### OH_IPCSkeleton_GetCallingUid()

```C
uint64_t OH_IPCSkeleton_GetCallingUid(void)
```

**Description**

Obtains the UID of the caller. This is applicable to user-level permission control and identity identification in multi-user environments, for example, determining access permissions based on the UID in permission management, isolating data access for different users in multi-user systems, and recording user identities in security audits for behavior tracing. This API must be called in the IPC context. Otherwise, the ID of the current user is returned.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**

| Type| Description|
| ---- | ---- |
| uint64_t | Returns the caller UID.|

### OH_IPCSkeleton_IsLocalCalling()

```C
int OH_IPCSkeleton_IsLocalCalling(void)
```

**Description**

Checks whether the current IPC call is a local call.

- This function must be called in the IPC context.
- This function is commonly used to adopt different processing strategies based on the call type.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns **1** if a local calling is in progress; returns **0** otherwise.|

### OH_IPCSkeleton_SetMaxWorkThreadNum()

```C
int OH_IPCSkeleton_SetMaxWorkThreadNum(const int maxThreadNum)
```

**Description**

Sets the maximum thread count of the IPC worker thread pool to control the concurrent processing capability of IPC requests. After this function is called, the IPC framework manages worker threads according to the set maximum thread count. When the number of concurrent IPC requests exceeds the thread count, the requests are queued and wait.

- It is recommended to call this function at app startup to avoid frequent modifications at runtime.
- This configuration should be completed before calling [OH_IPCSkeleton_JoinWorkThread()](#oh_ipcskeleton_joinworkthread) to join the worker thread pool, to ensure that the thread pool works at the configured size.
- This configuration affects the capacity control of threads that subsequently join the thread pool.
- Unless there are special requirements, it is not recommended to change the maximum number of threads.
- Too many threads increase system resource consumption, while too few may affect IPC concurrent processing performance.
- Set this value appropriately based on actual service scenarios and device capabilities.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const int maxThreadNum   | Maximum number of worker threads. Default value: 16. Value range: [1, 32]. This parameter controls the IPC concurrent processing capability. A smaller value saves system resources, while a larger value improves concurrent processing efficiency. If the value is out of range, the parameter error **OH_IPC_CHECK_PARAM_ERROR** is returned. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Result code.<br> Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) (value: **0**) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) (value: **-1**) if the parameter is invalid. Possible cause: **maxThreadNum** is not within the valid range [1, 32]. Solution: Check and adjust the parameter value.<br> Returns [OH_IPC_ErrorCode#OH_IPC_INNER_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) (value: **-2**) in other cases. Possible cause: Internal exception in the IPC framework. Solution: Check the IPC service status or restart the app. |

### OH_IPCSkeleton_ResetCallingIdentity()

```C
int OH_IPCSkeleton_ResetCallingIdentity(char **identity, int32_t *len, OH_IPC_MemAllocator allocator)
```

**Description**

Resets the caller identity credential to the identity credential of the current process (including TokenId, UID, and PID information), and returns the caller credential information. This is applicable to scenarios where the permission needs to be temporarily elevated or operations need to be performed as the service process. For example, it is used to temporarily switch to the service identity when a system service needs to access protected resources, and to perform privileged operations as the service identity in permission proxy scenarios. After this function is called, the identity credential of the current IPC context is switched to the credential of the current process, and the credential information of the original caller is returned for subsequent restoration.

- This function must be called in the IPC request processing context.
- The returned credential information must be properly managed by the caller and released after use.
- This function must be used in pair with [OH_IPCSkeleton_SetCallingIdentity()](#oh_ipcskeleton_setcallingidentity) to restore the original credential after the operation is completed.
- Avoid maintaining the reset state for a long time, as it may affect permission verification.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| char **identity | Pointer to the memory address for storing the calling credential. The credential contains identity information such as the caller's token ID, UID, and PID, and can be used later to restore the calling identity via [OH_IPCSkeleton_SetCallingIdentity()](#oh_ipcskeleton_setcallingidentity). The memory is allocated by the user-provided allocator, and the user must release it after use. This function must be called in an IPC request processing context. This parameter cannot be null. |
| int32_t *len | Pointer to the length (in bytes) of the data written to identity. It informs the caller of the actual size of the credential data for subsequent correct use and memory release. This function must be called in an IPC request processing context. This parameter cannot be null. |
| [OH_IPC_MemAllocator](capi-ipc-cparcel-h.md#oh_ipc_memallocator) allocator | User-specified memory allocator used to allocate memory for **identity**. A custom allocator allows control over the memory allocation strategy (for example, using shared memory or heap memory). This function must be called in an IPC request processing context. This parameter cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) (value: **0**) if successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) (value: **-1**) if the parameter is invalid. Possible cause: The **identity**, **len**, or **allocator** parameter is null. Solution: Ensure that the parameters are not null.<br> Returns [OH_IPC_ErrorCode#OH_IPC_MEM_ALLOCATOR_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) (value: **-3**) if memory allocation fails. Possible cause: Insufficient system memory or an abnormal memory allocator. Solution: Release memory and retry, or check the memory allocator.<br> Returns [OH_IPC_ErrorCode#OH_IPC_INNER_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) (value: **-2**) in other cases. Possible cause: Internal IPC framework exception. Solution: Check the IPC service status or restart the app. |

### OH_IPCSkeleton_SetCallingIdentity()

```C
int OH_IPCSkeleton_SetCallingIdentity(const char *identity)
```

**Description**

Restores the caller credential information to the IPC context. This function restores the identity credential in the IPC context to the original caller credential. It must be called in the IPC request processing context. This is applicable to scenarios where normal permissions are restored after temporary privilege escalation operations, for example, restoring the caller identity after accessing protected resources on the server side, and restoring the caller permission state after permission proxy operations are completed.

- After this function is called, the identity credential of the IPC context is restored to the caller credential previously saved through [OH_IPCSkeleton_ResetCallingIdentity()](#oh_ipcskeleton_resetcallingidentity).
- Call this function immediately after completing operations that require the server identity.
- Identity credentials should be properly managed to prevent credential leakage.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

| Name| Description|
| ------ | ---- |
| const char *identity | Caller credential, which cannot be empty. It is the return value of [OH_IPCSkeleton_ResetCallingIdentity()](#oh_ipcskeleton_resetcallingidentity) and must be used in pair with [OH_IPCSkeleton_ResetCallingIdentity()](#oh_ipcskeleton_resetcallingidentity). |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the parameters are incorrect.<br> Returns [OH_IPC_ErrorCode#OH_IPC_INNER_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) in other cases.|

### OH_IPCSkeleton_IsHandlingTransaction()

```C
int OH_IPCSkeleton_IsHandlingTransaction(void)
```

**Description**

Checks whether an IPC request is being processed. This is applicable to scenarios where conditional judgment is needed based on the current IPC processing status, such as avoiding re-entry and status checks.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**

| Type| Description|
| ---- | ---- |
| int | Whether an IPC request is being processed. The value **1** indicates that an IPC request is being processed, and **0** indicates that no IPC request is being processed. |
