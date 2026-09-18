# ChildProcess (System API)

The childprocess object can be used to create a new process.

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## close

```TypeScript
close(): void
```

Close the target process

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## getErrorOutput

```TypeScript
getErrorOutput(): Promise<Uint8Array>
```

Return it as 'Uint8Array of the stderr until EOF

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Return subprocess standard error output. |

## getOutput

```TypeScript
getOutput(): Promise<Uint8Array>
```

Return it as 'Uint8Array' of the stdout until EOF

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Return subprocess standard output. |

## kill

```TypeScript
kill(signal: number | string): void
```

Send a signal to process

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| signal | number &#124; string | Yes | Number or string represents the signal sent. |

## wait

```TypeScript
wait(): Promise<number>
```

Return 'number' is the target process exit code

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Return the target process exit code. |

## exitCode

```TypeScript
readonly exitCode: number
```

Return exitCode is the exit code of the current child process

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## killed

```TypeScript
readonly killed: boolean
```

Return boolean is whether the current process signal is sent successfully

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## pid

```TypeScript
readonly pid: number
```

Return pid is the pid of the current process

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## ppid

```TypeScript
readonly ppid: number
```

Return ppid is the pid of the current child process

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.
