# setFormsRecyclable（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## setFormsRecyclable

```TypeScript
function setFormsRecyclable(formIds: Array<string>): Promise<void>
```

设置卡片可回收。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formHost-function setFormsRecyclable(formIds: Array<string>): Promise<void>--><!--Device-formHost-function setFormsRecyclable(formIds: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | caller is not system app. |


## setFormsRecyclable

```TypeScript
function setFormsRecyclable(formIds: Array<string>, callback: AsyncCallback<void>): void
```

设置卡片可回收。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formHost-function setFormsRecyclable(formIds: Array<string>, callback: AsyncCallback<void>): void--><!--Device-formHost-function setFormsRecyclable(formIds: Array<string>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当设置卡片可回收成功时，error为undefined；否则抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | caller is not system app. |

