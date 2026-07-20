# off（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

<a id="off"></a>
## off('printerStateChange')

```TypeScript
function off(type: 'printerStateChange', callback?: Callback<boolean>): void
```

取消注册打印机状态变化事件回调，使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function off(type: 'printerStateChange', callback?: Callback<boolean>): void--><!--Device-print-function off(type: 'printerStateChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'printerStateChange' | 是 | 表示打印机状态改变。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt; | 否 | 表示取消注册打印机状态变化事件是否成功。true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.off('printerStateChange', (data: boolean) => {
    console.info('off printerStateChange data : ' + JSON.stringify(data));
})

```


<a id="off-1"></a>
## off('jobStateChange')

```TypeScript
function off(type: 'jobStateChange', callback?: Callback<boolean>): void
```

取消注册打印任务状态变化事件回调，使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function off(type: 'jobStateChange', callback?: Callback<boolean>): void--><!--Device-print-function off(type: 'jobStateChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'jobStateChange' | 是 | 表示打印任务状态改变。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt; | 否 | 表示取消注册打印任务状态变化事件是否成功。true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.off('jobStateChange', (data: boolean) => {
    console.info('offJobStateChanged data : ' + JSON.stringify(data));
})

```


<a id="off-2"></a>
## off('extInfoChange')

```TypeScript
function off(type: 'extInfoChange', callback?: Callback<boolean>): void
```

取消注册打印扩展信息变化事件回调，使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function off(type: 'extInfoChange', callback?: Callback<boolean>): void--><!--Device-print-function off(type: 'extInfoChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'extInfoChange' | 是 | 表示打印扩展信息改变。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt; | 否 | 表示取消注册打印扩展信息变化事件是否成功。true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.off('extInfoChange', (data: boolean) => {
    console.info('offExtInfoChange data : ' + JSON.stringify(data));
})

```

