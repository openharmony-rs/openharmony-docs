# off

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## off('applicationState')

```TypeScript
function off(type: 'applicationState', observerId: number, callback: AsyncCallback<void>): void
```

注销应用状态监听器。使用callback异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'applicationState' | 是 | 调用接口类型，固定填'applicationState'字符串。 |
| observerId | number | 是 | 注册的应用状态监听器ID，即[on('applicationState')](arkts-ability-appmanager-on-f.md#onapplicationstate)返回的监听器ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当取消注册应用程序状态观测器成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |


## off('applicationState')

```TypeScript
function off(type: 'applicationState', observerId: number): Promise<void>
```

注销应用状态监听器。使用Promise异步回调。

**起始版本：** 14

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'applicationState' | 是 | 调用接口类型，固定填'applicationState'字符串。 |
| observerId | number | 是 | 注册的应用状态监听器ID，即[on('applicationState')](arkts-ability-appmanager-on-f.md#onapplicationstate)返回的监听器ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
