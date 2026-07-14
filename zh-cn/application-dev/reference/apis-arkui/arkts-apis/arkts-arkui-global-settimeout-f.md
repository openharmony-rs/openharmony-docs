# setTimeout

## setTimeout

```TypeScript
export declare function setTimeout(handler: Function | string, delay?: number, ...arguments: any[]): number
```

Sets a timer for the system to call a function after the timer goes off.
The timer is automatically deleted after callback execution, or you may manually delete it via the **clearTimeout()**
API.

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Function \| string | 是 | When the type is function, this parameter specifies the callback function tobe invoked upon the timer's expiration. <br>When the type is string, error information is printed with noadditional processing. |
| delay | number | 否 | Number of milliseconds delayed before the execution. It is recommended that an integer bepassed in; a decimal will be rounded down.<br>If this parameter is omitted, the default value of **0** is used.&lt;br&gt;**NOTE**<br>1. This timer is not a precise timer, and there may be a discrepancy between the actual delay andthe expected delay.<br>2. If the value is less than 1, it will be defaulted to **0**.<br>3. The value is subjectto system limitations. If it exceeds 2^31 – 1, the value will be **0**. |
| arguments | any[] | 是 | Additional parameters that are passed to **handler** only when **handler** is of thefunction type.<br>If the number of arguments is less than that of the **handler** function parameters, theparameters that are not overwritten by arguments are set to **undefined**.<br>If the number of arguments exceedsthat of the **handler** function parameters, the excess arguments will be ignored. However, they can still beaccessed via the built-in arguments object within the **handler** function.<br>**起始版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ID of the timer. The timer ID is shared by processes and is an integer starting from 0 inascending order. |

