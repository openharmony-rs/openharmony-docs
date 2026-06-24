# on（系统接口）

## on('printerStateChange')

```TypeScript
function on(type: 'printerStateChange', callback: (state: PrinterState, info: PrinterInfo) => void): void
```

注册打印机状态变化事件回调，使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'printerStateChange' | 是 | 表示打印机状态改变。 |
| callback | (state: PrinterState, info: PrinterInfo) =&gt; void | 是 | 打印机状态改变之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-the) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-not) | not system application |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.on('printerStateChange', (state: print.PrinterState, info: print.PrinterInfo) => {
    if (state === null || info === null) {
        console.error('printer state changed state is null or info is null');
        return;
    } else {
        console.info('on printer state changed, state : ' + JSON.stringify(state));
        console.info('on printer state changed, info : ' + JSON.stringify(info));
    }
})

```


## on('jobStateChange')

```TypeScript
function on(type: 'jobStateChange', callback: (state: PrintJobState, job: PrintJob) => void): void
```

注册打印任务状态变化事件回调，使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'jobStateChange' | 是 | 表示打印任务状态改变。 |
| callback | (state: PrintJobState, job: PrintJob) =&gt; void | 是 | 打印任务状态改变之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-the) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-not) | not system application |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.on('jobStateChange', (state: print.PrintJobState, job: print.PrintJob) => {
    console.info('onJobStateChange, state : ' + JSON.stringify(state) + ', job : ' + JSON.stringify(job));
})

```


## on('extInfoChange')

```TypeScript
function on(type: 'extInfoChange', callback: (extensionId: string, info: string) => void): void
```

注册打印扩展信息变化事件回调，使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'extInfoChange' | 是 | 表示打印扩展信息改变。 |
| callback | (extensionId: string, info: string) =&gt; void | 是 | 打印扩展信息改变之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-the) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-not) | not system application |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.on('extInfoChange', (extensionId: string, info: string) => {
    console.info('onExtInfoChange, extensionId : ' + JSON.stringify(extensionId) + ', info : ' + JSON.stringify(info));
})

```

