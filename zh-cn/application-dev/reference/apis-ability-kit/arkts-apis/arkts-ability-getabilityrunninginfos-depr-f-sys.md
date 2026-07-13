# getAbilityRunningInfos（系统接口）

## getAbilityRunningInfos

```TypeScript
function getAbilityRunningInfos(): Promise<Array<AbilityRunningInfo>>
```

获取Ability运行相关信息。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAbilityRunningInfos

**需要权限：** ohos.permission.GET_RUNNING_INFO

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AbilityRunningInfo&gt;&gt; | Promise对象，返回Ability运行相关信息。 |


## getAbilityRunningInfos

```TypeScript
function getAbilityRunningInfos(callback: AsyncCallback<Array<AbilityRunningInfo>>): void
```

获取Ability运行相关信息。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAbilityRunningInfos

**需要权限：** ohos.permission.GET_RUNNING_INFO

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;AbilityRunningInfo&gt;&gt; | 是 | 回调函数，返回Ability运行相关信息。 |

