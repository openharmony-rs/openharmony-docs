# getAbilityRunningInfos（系统接口）

## 导入模块

```TypeScript
```

## getAbilityRunningInfos

```TypeScript
function getAbilityRunningInfos(): Promise<Array<AbilityRunningInfo>>
```

获取Ability运行相关信息。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAbilityRunningInfos](arkts-ability-abilitymanager-getabilityrunninginfos-f.md)

**需要权限：** ohos.permission.GET_RUNNING_INFO

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AbilityRunningInfo](arkts-ability-abilityrunninginfo-i.md)&gt;&gt; | Promise对象，返回Ability运行相关信息。 |

**示例**

```TypeScript
import abilityManager from '@ohos.application.abilityManager';
import { BusinessError } from '@ohos.base';

// 获取Ability运行信息
abilityManager.getAbilityRunningInfos().then((data) => {
  console.info(`getAbilityRunningInfos success, data: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`getAbilityRunningInfos error code : ${error.code}, error msg: ${error.message}.`);
});
```


## getAbilityRunningInfos

```TypeScript
function getAbilityRunningInfos(callback: AsyncCallback<Array<AbilityRunningInfo>>): void
```

获取Ability运行相关信息。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAbilityRunningInfos](arkts-ability-abilitymanager-getabilityrunninginfos-f.md)

**需要权限：** ohos.permission.GET_RUNNING_INFO

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AbilityRunningInfo](arkts-ability-abilityrunninginfo-i.md)&gt;&gt; | 是 | 回调函数，返回Ability运行相关信息。 |

**示例**

```TypeScript
import abilityManager from '@ohos.application.abilityManager';
import { BusinessError } from '@ohos.base';

// 获取Ability运行信息
abilityManager.getAbilityRunningInfos((error: BusinessError, data) => {
  if (error) {
    console.error(`GetAbilityRunningInfos failed, error code: ${error.code}, error msg: ${error.message}.`);
    return;
  }
  console.info(`GetAbilityRunningInfos success, data: ${JSON.stringify(data)}.`);
});
```
