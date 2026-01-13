# AbilityRunningInfo

AbilityRunningInfo模块提供对Ability运行的相关信息和状态的定义。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 14开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { abilityManager } from '@kit.AbilityKit';
```

## 使用说明

通过abilityManager中[getAbilityRunningInfos](js-apis-app-ability-abilityManager.md#abilitymanagergetabilityrunninginfos14)方法获取。

## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| ability | ElementName | 否 | 否 | Ability匹配信息  |
| pid | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 否 | 进程ID。 |
| uid | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 否 | 用户ID。  |
| processName | string | 否 | 否 | 进程名称。  |
| startTime | ArkTS-Dyn: number<br/>ArkTS-Sta: long | 否 | 否 | Ability启动时间。  |
| abilityState | [abilityManager.AbilityState](js-apis-app-ability-abilityManager.md#abilitystate14) | 否 | 否 | Ability状态。  |

**示例：**

```ts
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  abilityManager.getAbilityRunningInfos()
    .then((data: abilityManager.AbilityRunningInfo[]) => {
      for (let i = 0; i < data.length; i++) {
        let abilityInfo = data[i];
        console.info(`getAbilityRunningInfos success, data: ${JSON.stringify(abilityInfo)}`);
      }
    })
    .catch((err: Error) => {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      console.error(`getAbilityRunningInfos fail, error code: ${code}, error msg: ${msg}`);
    })
} catch (e) {
  let code = (e as BusinessError).code;
  let msg = (e as BusinessError).message;
  console.error(`getAbilityRunningInfos fail, error code: ${code}, error msg: ${msg}`);
}
```
