# off（系统接口）

## off('printerStateChange')

```TypeScript
function off(type: 'printerStateChange', callback?: Callback<boolean>): void
```

取消注册打印机状态变化事件回调，使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'printerStateChange' | 是 | 表示打印机状态改变。 |
| callback | Callback&lt;boolean&gt; | 否 | 表示取消注册打印机状态变化事件是否成功。true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-the) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-not) | not system application |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.off('printerStateChange', (data: boolean) => {
    console.info('off printerStateChange data : ' + JSON.stringify(data));
})

```


## off('jobStateChange')

```TypeScript
function off(type: 'jobStateChange', callback?: Callback<boolean>): void
```

取消注册打印任务状态变化事件回调，使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'jobStateChange' | 是 | 表示打印任务状态改变。 |
| callback | Callback&lt;boolean&gt; | 否 | 表示取消注册打印任务状态变化事件是否成功。true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-the) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-not) | not system application |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.off('jobStateChange', (data: boolean) => {
    console.info('offJobStateChanged data : ' + JSON.stringify(data));
})

```


## off('extInfoChange')

```TypeScript
function off(type: 'extInfoChange', callback?: Callback<boolean>): void
```

取消注册打印扩展信息变化事件回调，使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'extInfoChange' | 是 | 表示打印扩展信息改变。 |
| callback | Callback&lt;boolean&gt; | 否 | 表示取消注册打印扩展信息变化事件是否成功。true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-the) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-not) | not system application |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.off('extInfoChange', (data: boolean) => {
    console.info('offExtInfoChange data : ' + JSON.stringify(data));
})

```

