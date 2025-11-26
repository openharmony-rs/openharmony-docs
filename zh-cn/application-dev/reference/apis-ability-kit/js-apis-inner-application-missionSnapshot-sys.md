# MissionSnapshot (系统接口)

一个任务的任务快照对象，可以通过[missionManager.getMissionSnapShot](js-apis-app-ability-missionManager-sys.md#missionmanagergetmissionsnapshot)获取。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口均为系统接口，三方应用不支持调用。

## 导入模块

```ts
import { missionManager } from '@kit.AbilityKit';
```

## 属性

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| ability | ElementName | 否 | 否 | 表示该任务的组件信息。 |
| snapshot | [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 否 | 否 | 表示任务快照。 |

## 使用说明

通过missionManager中的getMissionSnapShot来获取。

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfo('', 1, (error, data) => {
    if (error) {
      // 处理业务逻辑错误
      console.error(`getMissionInfo failed, error.code: ${error.code}, error.message: ${error.message}`);
      return;
    }

    if (!data) {
      console.error('getMissionInfo failed: data is undefined');
      return;
    }

    console.info(`getMissionInfo missionId is: ${data.missionId}`);
    console.info(`getMissionInfo runningState is: ${data.runningState}`);
    console.info(`getMissionInfo lockedState is: ${data.lockedState}`);
    console.info(`getMissionInfo timestamp is: ${data.timestamp}`);
    console.info(`getMissionInfo want is: ${data.want}`);
    console.info(`getMissionInfo label is: ${data.label}`);
    console.info(`getMissionInfo iconPath is: ${data.iconPath}`);
    console.info(`getMissionInfo continuable is: ${data.continuable}`);
    console.info(`getMissionInfo unclearable is: ${data.unclearable}`);

    missionManager.getMissionSnapShot('', data.missionId).then(snapshot => {
      // 执行正常业务
      console.info(`bundleName = ${snapshot.ability.bundleName}`);
    });
  });
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```

