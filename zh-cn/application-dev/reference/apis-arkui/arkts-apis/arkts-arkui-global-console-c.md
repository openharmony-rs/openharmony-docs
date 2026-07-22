# console

Defines the console info.

**起始版本：** 7

<!--Device-unnamed-export declare class console--><!--Device-unnamed-export declare class console-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## assert

```TypeScript
static assert(value?: Object, ...arguments: Object[]): void
```

Prints a message if value is false or omitted.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static assert(value?: Object, ...arguments: Object[]): void--><!--Device-console-static assert(value?: Object, ...arguments: Object[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 否 | The value tested for being truthy. |
| arguments | Object[] | 是 | Used as error message to print. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

## count

```TypeScript
static count(label?: string): void
```

Maintains an internal counter specific to label and print the number of times console.count() has been called with the given label.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static count(label?: string): void--><!--Device-console-static count(label?: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 否 | Counter name. Default: "default". |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

## countReset

```TypeScript
static countReset(label?: string): void
```

Reset the internal counter specific to label.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static countReset(label?: string): void--><!--Device-console-static countReset(label?: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 否 | Counter name. Default: "default". |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

## debug

```TypeScript
static debug(message: string, ...arguments: any[]): void
```

Prints "debug" logs.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-console-static debug(message: string, ...arguments: any[]): void--><!--Device-console-static debug(message: string, ...arguments: any[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | string | 是 | Text to print. |
| arguments | any[] | 是 | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform<br>**起始版本：** 10 |

## dir

```TypeScript
static dir(dir?: Object): void
```

Prints properties of the specified JavaScript object.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static dir(dir?: Object): void--><!--Device-console-static dir(dir?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dir | Object | 否 | A JavaScript object whose properties should be output. |

## dirxml

```TypeScript
static dirxml(...arguments: Object[]): void
```

This method calls console.log() passing it the arguments received.This method does not produce any XML formatting.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static dirxml(...arguments: Object[]): void--><!--Device-console-static dirxml(...arguments: Object[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arguments | Object[] | 是 | Text to print. |

## error

```TypeScript
static error(message: string, ...arguments: any[]): void
```

Prints "error" logs.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-console-static error(message: string, ...arguments: any[]): void--><!--Device-console-static error(message: string, ...arguments: any[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | string | 是 | Text to print. |
| arguments | any[] | 是 | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform<br>**起始版本：** 10 |

## group

```TypeScript
static group(...arguments: Object[]): void
```

Creates a new inline group, causing any subsequent console messages to be indented by an additional level.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static group(...arguments: Object[]): void--><!--Device-console-static group(...arguments: Object[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arguments | Object[] | 是 | messages to print first. |

## groupCollapsed

```TypeScript
static groupCollapsed(...arguments: Object[]): void
```

Same as console.group()

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static groupCollapsed(...arguments: Object[]): void--><!--Device-console-static groupCollapsed(...arguments: Object[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arguments | Object[] | 是 | messages to print first. |

## groupEnd

```TypeScript
static groupEnd(): void
```

Exit current inline group.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static groupEnd(): void--><!--Device-console-static groupEnd(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## info

```TypeScript
static info(message: string, ...arguments: any[]): void
```

Prints "info" logs.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-console-static info(message: string, ...arguments: any[]): void--><!--Device-console-static info(message: string, ...arguments: any[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | string | 是 | Text to print. |
| arguments | any[] | 是 | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform<br>**起始版本：** 10 |

## log

```TypeScript
static log(message: string, ...arguments: any[]): void
```

Prints "log" logs.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-console-static log(message: string, ...arguments: any[]): void--><!--Device-console-static log(message: string, ...arguments: any[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | string | 是 | Text to print. |
| arguments | any[] | 是 | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform<br>**起始版本：** 10 |

## table

```TypeScript
static table(tableData?: Object): void
```

Prints tabular data as a table.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static table(tableData?: Object): void--><!--Device-console-static table(tableData?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tableData | Object | 否 | tabular data. |

## time

```TypeScript
static time(label?: string): void
```

Start a timer.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static time(label?: string): void--><!--Device-console-static time(label?: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 否 | Timer name. Default: "default". |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

## timeEnd

```TypeScript
static timeEnd(label?: string): void
```

End a timer and print time duration.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static timeEnd(label?: string): void--><!--Device-console-static timeEnd(label?: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 否 | Timer name. Default: "default". |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

## timeLog

```TypeScript
static timeLog(label?: string, ...arguments: Object[]): void
```

Print the elapsed time and other data arguments.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static timeLog(label?: string, ...arguments: Object[]): void--><!--Device-console-static timeLog(label?: string, ...arguments: Object[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 否 | Timer name. Default: "default". |
| arguments | Object[] | 是 | Text to print. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

## trace

```TypeScript
static trace(...arguments: Object[]): void
```

Prints stack information for the current code location.

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static trace(...arguments: Object[]): void--><!--Device-console-static trace(...arguments: Object[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arguments | Object[] | 是 | message to print. |

## traceHybridStack

```TypeScript
static traceHybridStack(): void
```

Prints information about the current hybrid stack of the calling thread in the main thread or worker thread.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-console-static traceHybridStack(): void--><!--Device-console-static traceHybridStack(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## warn

```TypeScript
static warn(message: string, ...arguments: any[]): void
```

Prints "warn" logs.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-console-static warn(message: string, ...arguments: any[]): void--><!--Device-console-static warn(message: string, ...arguments: any[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | string | 是 | Text to print. |
| arguments | any[] | 是 | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform<br>**起始版本：** 10 |

