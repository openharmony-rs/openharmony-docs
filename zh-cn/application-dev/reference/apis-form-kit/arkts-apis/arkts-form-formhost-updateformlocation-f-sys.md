# updateFormLocation（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## updateFormLocation

```TypeScript
function updateFormLocation(formId: string, location: formInfo.FormLocation): void
```

更新卡片位置。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formHost-function updateFormLocation(formId: string, location: formInfo.FormLocation): void--><!--Device-formHost-function updateFormLocation(formId: string, location: formInfo.FormLocation): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| location | formInfo.FormLocation | 是 | 卡片位置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | caller is not system app. |

