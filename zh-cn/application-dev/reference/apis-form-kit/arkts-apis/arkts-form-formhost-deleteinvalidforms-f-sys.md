# deleteInvalidForms（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## deleteInvalidForms

```TypeScript
function deleteInvalidForms(formIds: Array<string>, callback: AsyncCallback<number>): void
```

根据有效的卡片列表，删除应用程序不在有效列表中的卡片。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 有效卡片列表。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当根据列表删除应用程序的无效卡片成功，error为undefined，data为删除的卡片个数；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |

**示例**

```TypeScript
import { formHost } from '@kit.FormKit';

try {
  let formIds: string[] = new Array('12400633174999288', '12400633174999289');
  formHost.deleteInvalidForms(formIds, (error: BusinessError, data: number) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formHost deleteInvalidForms, data: ${data}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```


## deleteInvalidForms

```TypeScript
function deleteInvalidForms(formIds: Array<string>): Promise<number>
```

根据列表删除应用程序的无效卡片。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 有效卡片标识列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象。返回删除的卡片个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |

**示例**

```TypeScript
import { formHost } from '@kit.FormKit';

try {
  let formIds: string[] = new Array('12400633174999288', '12400633174999289');
  formHost.deleteInvalidForms(formIds).then((data: number) => {
    console.info(`formHost deleteInvalidForms, data: ${data}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```
