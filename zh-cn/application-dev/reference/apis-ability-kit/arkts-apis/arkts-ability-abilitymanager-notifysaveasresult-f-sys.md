# notifySaveAsResult（系统接口）

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## notifySaveAsResult

```TypeScript
function notifySaveAsResult(parameter: AbilityResult, requestCode: number, callback: AsyncCallback<void>): void
```

该接口仅供[DLP](../../apis-data-protection-kit/arkts-apis/arkts-dlppermission.md)（Data Loss Prevention, 数据丢失防护）管理应用使用，其他应用禁止使用，DLP管理应用通过该接口通知沙箱应用另存为结果。使用callback异步回调。

> **说明：**  
>  
> 从API version 10开始支持，从API version 24开始废弃。

**起始版本：** 10

**废弃版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityManager-function notifySaveAsResult(parameter: AbilityResult, requestCode: int, callback: AsyncCallback<void>): void--><!--Device-abilityManager-function notifySaveAsResult(parameter: AbilityResult, requestCode: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | 是 | 返回给调用startAbilityForResult?接口调用方的相关信息。 |
| requestCode | number | 是 | DLP管理应用传入的请求代码。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当另存为结果通知成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |


## notifySaveAsResult

```TypeScript
function notifySaveAsResult(parameter: AbilityResult, requestCode: number): Promise<void>
```

该接口仅供[DLP](../../apis-data-protection-kit/arkts-apis/arkts-dlppermission.md)（Data Loss Prevention, 数据丢失防护）管理应用使用，其他应用禁止使用，DLP管理应用通过该接口通知沙箱应用另存为结果。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityManager-function notifySaveAsResult(parameter: AbilityResult, requestCode: int): Promise<void>--><!--Device-abilityManager-function notifySaveAsResult(parameter: AbilityResult, requestCode: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | 是 | 返回给调用startAbilityForResult?接口调用方的相关信息。 |
| requestCode | number | 是 | DLP管理应用传入的请求代码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

