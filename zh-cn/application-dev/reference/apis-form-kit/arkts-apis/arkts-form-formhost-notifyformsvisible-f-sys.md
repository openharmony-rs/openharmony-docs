# notifyFormsVisible（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## notifyFormsVisible

```TypeScript
function notifyFormsVisible(formIds: Array<string>, isVisible: boolean, callback: AsyncCallback<void>): void
```

通知卡片是否可见。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function notifyFormsVisible(formIds: Array<string>, isVisible: boolean, callback: AsyncCallback<void>): void--><!--Device-formHost-function notifyFormsVisible(formIds: Array<string>, isVisible: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识列表。 |
| isVisible | boolean | 是 | 表示卡片是否可见。 <br>true: 表示卡片可见。 <br>false: 表示卡片不可见。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当通知卡片是否可见成功，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |


## notifyFormsVisible

```TypeScript
function notifyFormsVisible(formIds: Array<string>, isVisible: boolean): Promise<void>
```

通知卡片是否可见。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function notifyFormsVisible(formIds: Array<string>, isVisible: boolean): Promise<void>--><!--Device-formHost-function notifyFormsVisible(formIds: Array<string>, isVisible: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识列表。 |
| isVisible | boolean | 是 | 表示卡片是否可见。 <br>true: 表示卡片可见。 <br>false: 表示卡片不可见。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

