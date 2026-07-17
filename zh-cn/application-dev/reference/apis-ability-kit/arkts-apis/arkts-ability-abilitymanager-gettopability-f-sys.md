# getTopAbility（系统接口）

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## getTopAbility

```TypeScript
function getTopAbility(): Promise<ElementName>
```

获取窗口焦点所在的Ability。使用Promise异步回调。

**起始版本：** 9

<!--Device-abilityManager-function getTopAbility(): Promise<ElementName>--><!--Device-abilityManager-function getTopAbility(): Promise<ElementName>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ElementName> | Promise对象，返回接口运行结果及应用名。开发者可在此进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |


## getTopAbility

```TypeScript
function getTopAbility(callback: AsyncCallback<ElementName>): void
```

获取窗口焦点所在的Ability。使用callback异步回调。

**起始版本：** 9

<!--Device-abilityManager-function getTopAbility(callback: AsyncCallback<ElementName>): void--><!--Device-abilityManager-function getTopAbility(callback: AsyncCallback<ElementName>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<ElementName> | 是 | 回调函数。当获取窗口焦点所在的Ability成功，err为undefined，data为获取到的应用名；否则为错误对象。可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

