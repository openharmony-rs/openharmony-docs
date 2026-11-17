# killProcessWithAccountSafely（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## killProcessWithAccountSafely

```TypeScript
function killProcessWithAccountSafely(bundleName: string, accountId: number, clearPageStack: boolean, appIndex?: number):
    Promise<void>
```

根据包名、账号ID和应用分身ID安全终止进程。如果目标进程受到保护，则无法终止。使用Promise异步回调。

> **说明：** 
> 
> 当accountId为当前用户时，不需要校验ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-appManager-function killProcessWithAccountSafely(bundleName: string, accountId: int, clearPageStack: boolean, appIndex?: int):    Promise<void>--><!--Device-appManager-function killProcessWithAccountSafely(bundleName: string, accountId: int, clearPageStack: boolean, appIndex?: int):    Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| accountId | number | 是 | 系统账号的账号ID。 |
| clearPageStack | boolean | 是 | 表示是否清除页面堆栈。true表示清除，false表示不清除。 |
| appIndex | number | 否 | 应用分身ID。默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server failed. |
| [16000210](../errorcode-ability.md#16000210-目标进程受mdm应用保护无法终止) | The target process is protected by an MDM application and cannot be terminated. |
