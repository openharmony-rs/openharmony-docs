# ProcessManager

Provides APIs for throwing exceptions during the addition of a process.

Construct a **ProcessManager** object.

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## exit

```TypeScript
exit(code: number): void
```

Terminates this process.

Exercise caution when using this API. After this API is called, the application exits. If the input parameter is not 0, data loss or exceptions may occur.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Exit code of the process. |

**Examples**

```TypeScript
let pro = new process.ProcessManager();
pro.exit(0);
```

## getEnvironmentVar

```TypeScript
getEnvironmentVar(name: string): string
```

Obtains the value of an environment variable.

> **NOTE:** 
> 
> Obtains the value of an environment variable. If the environment variable does not exist, **undefined** is
> returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Environment variable name. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Value of the environment variable. |

**Examples**

```TypeScript
let pro = new process.ProcessManager();
let pres = pro.getEnvironmentVar("PATH");
```

## getSystemConfig

```TypeScript
getSystemConfig(name: number): number
```

Obtains the system configuration.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | number | Yes | System configuration parameter name. |

**Return value:**

| Type | Description |
| --- | --- |
| number | System configuration obtained. If the configuration does not exist, **-1** is returned. |

**Examples**

```TypeScript
let pro = new process.ProcessManager();
let _SC_ARG_MAX = 0;
let pres = pro.getSystemConfig(_SC_ARG_MAX);
```

## getThreadPriority

```TypeScript
getThreadPriority(v: number): number
```

Obtains the thread priority based on the specified TID.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | number | Yes | TID. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Priority of the thread. The priority depends on the operating system. |

**Examples**

```TypeScript
let pro = new process.ProcessManager();
let tid = process.tid;
let pres = pro.getThreadPriority(tid);
```

## getUidForName

```TypeScript
getUidForName(v: string): number
```

Obtains the UID of a user from the user database of the system based on the specified user name.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | string | Yes | User name. |

**Return value:**

| Type | Description |
| --- | --- |
| number | UID of the user. If the user does not exist, **-1** is returned. |

**Examples**

```TypeScript
let pro = new process.ProcessManager();
let pres = pro.getUidForName("tool");
```

## isAppUid

```TypeScript
isAppUid(v: number): boolean
```

Checks whether a UID belongs to this application.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | number | Yes | UID. which can be obtained by running **process.uid**. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the UID belongs to the application; otherwise, **false** is returned. |

**Examples**

```TypeScript
let pro = new process.ProcessManager();
// Use process.uid to obtain the UID.
let pres = process.uid;
let result = pro.isAppUid(pres);
console.info("result: " + result); // result: true
```

## kill

```TypeScript
kill(signal: number, pid: number): boolean
```

Sends a signal to the specified process to terminate it. Only the current process can be terminated.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| signal | number | Yes | Signal to send. Value range: 1 &lt;= signal &lt;= 64. |
| pid | number | Yes | PID of the process, to which the signal will be sent. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Signal sending result. The value **true** is returned if the signal is sent successfully; otherwise, **false** is returned. |

**Examples**

```TypeScript
let pro = new process.ProcessManager();
let pres = process.pid;
let result = pro.kill(28, pres);
```
