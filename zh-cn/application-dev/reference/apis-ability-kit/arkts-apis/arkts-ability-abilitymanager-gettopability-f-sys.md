# getTopAbility（系统接口）

## getTopAbility

```TypeScript
function getTopAbility(): Promise<ElementName>
```

获取窗口焦点所在的Ability。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ElementName&gt; | Promise对象，返回接口运行结果及应用名。开发者可在此进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |


## getTopAbility

```TypeScript
function getTopAbility(callback: AsyncCallback<ElementName>): void
```

获取窗口焦点所在的Ability。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;ElementName&gt; | 是 | 回调函数。当获取窗口焦点所在的Ability成功，err为undefined，data为获取到的应用名；否则为错误对象。可进行错误处理或其他自<br/>定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

