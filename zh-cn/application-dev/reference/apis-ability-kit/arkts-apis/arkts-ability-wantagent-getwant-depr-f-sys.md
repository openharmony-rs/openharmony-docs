# getWant（系统接口）

## getWant

```TypeScript
function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void
```

获取WantAgent中的Want(callback形式)。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.app.ability.wantAgent/wantAgent#getWant

<!--Device-wantAgent-function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void--><!--Device-wantAgent-function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates the \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ WantAgent信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 获取WantAgent中的Want的回调方法。 |


## getWant

```TypeScript
function getWant(agent: WantAgent): Promise<Want>
```

获取WantAgent中的Want(Promise形式)。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.app.ability.wantAgent/wantAgent#getWant

<!--Device-wantAgent-function getWant(agent: WantAgent): Promise<Want>--><!--Device-wantAgent-function getWant(agent: WantAgent): Promise<Want>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | WantAgent信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 以Promise形式返回Want。 |

