# updateFormLockedState（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## updateFormLockedState

```TypeScript
function updateFormLockedState(formId: string, isLocked: boolean): Promise<void>
```

通知卡片管控状态更新。使用Promise异步回调。

卡片管控状态是指，应用使能了应用锁管控，对应应用的卡片也会跟随使能应用锁管控，此时卡片页面会使用加锁的蒙板样式遮罩卡片。在管控状态下，操作和使用卡片需要输入加锁时设置的密码。

**起始版本：** 22

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| isLocked | boolean | 是 | 标识卡片是否为管控状态，true表示管控状态，false表示非管控状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | caller is not system app. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |

**示例**

```TypeScript
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
let isLocked: boolean = true;

try {
  formHost.updateFormLockedState(formId, isLocked).then(() => {
    console.info(`formHost updateFormLockedState success`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
