# acquireFormState（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## acquireFormState

```TypeScript
function acquireFormState(want: Want, callback: AsyncCallback<formInfo.FormStateInfo>): void
```

获取卡片状态。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-formHost-function acquireFormState(want: Want, callback: AsyncCallback<formInfo.FormStateInfo>): void--><!--Device-formHost-function acquireFormState(want: Want, callback: AsyncCallback<formInfo.FormStateInfo>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 查询卡片状态时携带的want信息。需要包含bundle名、ability名、module名、卡片名、卡片规格等。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;formInfo.FormStateInfo&gt; | 是 | 回调函数。当获取卡片状态成功，error为undefined，data为获取到的卡片状态；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |


## acquireFormState

```TypeScript
function acquireFormState(want: Want): Promise<formInfo.FormStateInfo>
```

获取卡片状态。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-formHost-function acquireFormState(want: Want): Promise<formInfo.FormStateInfo>--><!--Device-formHost-function acquireFormState(want: Want): Promise<formInfo.FormStateInfo>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 查询卡片状态时携带的want信息。需要包含bundle名、ability名、module名、卡片名、卡片规格等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;formInfo.FormStateInfo&gt; | Promise对象。返回卡片状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

