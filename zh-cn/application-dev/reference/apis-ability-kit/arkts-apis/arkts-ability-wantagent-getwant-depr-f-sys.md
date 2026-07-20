# getWant（系统接口）

<a id="getwant"></a>
## getWant

```TypeScript
function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void
```

获取WantAgent中的Want(callback形式)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getWant

<!--Device-wantAgent-function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void--><!--Device-wantAgent-function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | Indicates the {@link WantAgent} WantAgent信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Want&gt; | 是 | 获取WantAgent中的Want的回调方法。 |


<a id="getwant-1"></a>
## getWant

```TypeScript
function getWant(agent: WantAgent): Promise<Want>
```

获取WantAgent中的Want(Promise形式)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getWant

<!--Device-wantAgent-function getWant(agent: WantAgent): Promise<Want>--><!--Device-wantAgent-function getWant(agent: WantAgent): Promise<Want>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | WantAgent信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Want&gt; | 以Promise形式返回Want。 |

