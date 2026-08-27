# notifyFormsEnableUpdate（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## notifyFormsEnableUpdate

```TypeScript
function notifyFormsEnableUpdate(
    formIds: Array<string>,
    isEnableUpdate: boolean,
    callback: AsyncCallback<void>
  ): void
```

通知卡片是否启用更新状态。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 卡片标识列表。 |
| isEnableUpdate | boolean | 是 | 表示卡片是否启用更新状态。 true: 表示卡片启用更新状态。false: 表示卡片没有启用更新状态。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当通知卡片是否启用更新状态成功，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |

**示例**

```TypeScript
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
try {
  formHost.notifyFormsEnableUpdate(formIds, true, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


## notifyFormsEnableUpdate

```TypeScript
function notifyFormsEnableUpdate(formIds: Array<string>, isEnableUpdate: boolean): Promise<void>
```

通知卡片是否启用更新状态。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 卡片标识列表。 |
| isEnableUpdate | boolean | 是 | 表示卡片是否启用更新状态。 true: 表示卡片启用更新状态。 false: 表示卡片没有启用更新状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |

**示例**

```TypeScript
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
try {
  formHost.notifyFormsEnableUpdate(formIds, true).then(() => {
    console.info('formHost notifyFormsEnableUpdate success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
