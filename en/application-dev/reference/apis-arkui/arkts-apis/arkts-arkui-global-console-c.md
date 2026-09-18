# console

Defines the console info.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
```

## assert

```TypeScript
static assert(value?: Object, ...arguments: Object[]): void
```

Prints assertion information.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | No | Result value. If value is false or left blank, the output starting with "Assertion failed" is printed. If value is true, no information is printed. |
| arguments | Object[] | Yes | Other information to be printed when value is false. If this parameter is left blank, other information is not printed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## count

```TypeScript
static count(label?: string): void
```

Maintains an internal counter. When this counter is invoked, its label name and the corresponding call count are printed.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| label | string | No | Counter label name. The default value is default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## countReset

```TypeScript
static countReset(label?: string): void
```

Resets a counter based on the specified label name.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| label | string | No | Counter label name. The default value is default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## debug

```TypeScript
static debug(message: string, ...arguments: any[]): void
```

Prints debugging information in formatted output mode.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | string | Yes | Text to print. |
| arguments | any[] | Yes | Arguments in the message or other information to be printed. |

## dir

```TypeScript
static dir(dir?: Object): void
```

Prints content of the specified object.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dir | Object | No | Object whose content needs to be printed. If this parameter is left blank, no information is printed. |

## dirxml

```TypeScript
static dirxml(...arguments: Object[]): void
```

Displays an interactive tree of the descendant elements of the specified XML element. This API is implemented by calling console.log() internally. It does not produce any XML elements. The usage method is the same as that of console.log().

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arguments | Object[] | Yes | Information to be printed. |

## error

```TypeScript
static error(message: string, ...arguments: any[]): void
```

Prints error information in formatted output mode.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | string | Yes | Error information to be printed. |
| arguments | any[] | Yes | Arguments in the message or other information to be printed. |

## group

```TypeScript
static group(...arguments: Object[]): void
```

Increases the indentation of subsequent lines by two spaces. If the information to be printed is provided, the information is printed without extra indentation.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arguments | Object[] | Yes | Information to be printed. |

## groupCollapsed

```TypeScript
static groupCollapsed(...arguments: Object[]): void
```

Creates a new inline group in collapsed mode. The usage and function of this API are the same as those of console.group().

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arguments | Object[] | Yes | Information to be printed. |

## groupEnd

```TypeScript
static groupEnd(): void
```

Reduces the indentation of subsequent lines by two spaces.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## info

```TypeScript
static info(message: string, ...arguments: any[]): void
```

Prints log information in formatted output mode. This API is the alias of console.log ().

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | string | Yes | Text to print. |
| arguments | any[] | Yes | Arguments in the message or other information to be printed. |

## log

```TypeScript
static log(message: string, ...arguments: any[]): void
```

Prints log information in formatted output mode.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | string | Yes | Text to print. |
| arguments | any[] | Yes | Arguments in the message or other information to be printed. |

## table

```TypeScript
static table(tableData?: Object): void
```

Prints data in a table.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tableData | Object | No | Data to be printed in a table. If this parameter is left blank, no information is printed. |

## time

```TypeScript
static time(label?: string): void
```

Starts a timer to track the duration of an operation. You can use console.timeEnd() to close the timer and print the elapsed time (in ms).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| label | string | No | Timer label. The default value is default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## timeEnd

```TypeScript
static timeEnd(label?: string): void
```

Stops the timer started by calling console.time() and prints the elapsed time (in ms).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| label | string | No | Timer label. The default value is default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## timeLog

```TypeScript
static timeLog(label?: string, ...arguments: Object[]): void
```

Prints the elapsed time and other data parameters for the timer started by console.time().

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| label | string | No | Timer label. The default value is default. |
| arguments | Object[] | Yes | Logs to be printed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## trace

```TypeScript
static trace(...arguments: Object[]): void
```

Creates a stack trace.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arguments | Object[] | Yes | Logs to be printed. If this parameter is left blank, only stack information is printed. |

## traceHybridStack

```TypeScript
static traceHybridStack(): void
```

Prints information about the current hybrid stack of the calling thread in the main thread or worker thread.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## warn

```TypeScript
static warn(message: string, ...arguments: any[]): void
```

Prints warning information in formatted output mode.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | string | Yes | Warning information to be printed. |
| arguments | any[] | Yes | Arguments in the message or other information to be printed. |
