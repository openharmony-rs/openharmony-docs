# getWant（系统接口）

## getWant

```TypeScript
function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void
```

获取WantAgent对象的want。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-wantAgent-function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void--><!--Device-wantAgent-function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-t.md) | 是 | WantAgent对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | 是 | 回调函数。当获取WantAgent对象want成功，err中code为0，data为获取到的Want数据；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000007](../errorcode-ability.md#16000007-服务未响应) | Service busy. There are concurrent tasks. Try again later. |
| [16000151](../errorcode-ability.md#16000151-无效wantagent对象) | Invalid wantAgent object. |
| [16000015](../errorcode-ability.md#16000015-服务超时) | Service timeout. |


## getWant

```TypeScript
function getWant(agent: WantAgent): Promise<Want>
```

获取WantAgent对象的want。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-wantAgent-function getWant(agent: WantAgent): Promise<Want>--><!--Device-wantAgent-function getWant(agent: WantAgent): Promise<Want>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-t.md) | 是 | WantAgent对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Promise对象，返回WantAgent对象的want。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000007](../errorcode-ability.md#16000007-服务未响应) | Service busy. There are concurrent tasks. Try again later. |
| [16000151](../errorcode-ability.md#16000151-无效wantagent对象) | Invalid wantAgent object. |
| [16000015](../errorcode-ability.md#16000015-服务超时) | Service timeout. |

