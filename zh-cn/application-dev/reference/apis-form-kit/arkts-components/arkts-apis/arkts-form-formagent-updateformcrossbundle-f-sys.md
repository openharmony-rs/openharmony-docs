# updateFormCrossBundle（系统接口）

## 导入模块

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## updateFormCrossBundle

```TypeScript
function updateFormCrossBundle(formId: string, formBindingData: formBindingData.FormBindingData): Promise<void>
```

跨应用更新卡片，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.UPDATE_FORM_CROSS_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 待更新的卡片标识。 |
| formBindingData | [formBindingData.FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | 是 | 用于更新的卡片数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | Possible cause IPC connection error. Such as the remote object dose not exist. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Possible cause Service State error. Such as the form is recovering. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | Possible cause internal functional error. Such as virtualization failed. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form to be operated has been deleted already. |
| [16501007](../errorcode-form.md#16501007-卡片不可信) | The form to be operated is not trusted. |

**示例**

```TypeScript
import { formBindingData, formAgent } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '123456789'; // 卡片的formId，请替换为实际的formId。
try {
  let param: Record<string, string> = {
    'temperature': '22c',
    'time': '22:00'
  };
  let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
  formAgent.updateFormCrossBundle(formId, obj).then(() => {
    console.info('formAgent updateFormCrossBundle success');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error?.code}, message: ${error?.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error?.code}, message: ${error?.message}`);
}
```
