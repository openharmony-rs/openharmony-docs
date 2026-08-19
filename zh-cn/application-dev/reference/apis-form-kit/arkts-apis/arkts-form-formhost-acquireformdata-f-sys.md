# acquireFormData（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## acquireFormData

```TypeScript
function acquireFormData(formId: string, callback: AsyncCallback<Record<string, Object>>): void
```

请求卡片提供方数据。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formHost-function acquireFormData(formId: string, callback: AsyncCallback<Record<string, Object>>): void--><!--Device-formHost-function acquireFormData(formId: string, callback: AsyncCallback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Record&lt;string, Object&gt;&gt; | 是 | 以callback方式返回接口运行结果及卡片提供方数据。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. invalid input parameter during form operation |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |


## acquireFormData

```TypeScript
function acquireFormData(formId: string): Promise<Record<string, Object>>
```

请求卡片提供方数据。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formHost-function acquireFormData(formId: string): Promise<Record<string, Object>>--><!--Device-formHost-function acquireFormData(formId: string): Promise<Record<string, Object>>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;{ [key: string]: Object | > } 以Promise方式返回接口运行结果及卡片提供方数据。<br>**适用版本：** 10+ |
| Promise&lt;Record&lt;string, Object&gt;&gt; | Promise used to return the API call result and the shared data.<br>**适用版本：** 11+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. invalid input parameter during form operation |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

