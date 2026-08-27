# MissionSnapshot（系统接口）

一个任务的任务快照对象，可以通过 [missionManager.getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-f-sys.md) 获取。

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## ability

```TypeScript
ability: ElementName
```

表示该任务的组件信息。

**类型：** [ElementName](arkts-ability-elementname-i.md)

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## snapshot

```TypeScript
snapshot: image.PixelMap
```

表示任务快照。

**类型：** image.PixelMap

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取任务快照信息
  missionManager.getMissionInfos('', 10, (error, missions) => {
    if (error) {
      console.error(`getMissionInfos failed, error.code: ${JSON.stringify(error.code)}, error.message: ${JSON.stringify(error.message)}`);
      return;
    }
    console.info(`size = ${missions.length}`);
    console.info(`missions = ${JSON.stringify(missions)}`);
    if (missions.length === 0) {
      console.error('missions is empty');
      return;
    }
    let id = missions[0].missionId;

    missionManager.getMissionSnapShot('', id, (err, snapshot) => {
      if (err) {
        console.error(`getMissionSnapShot failed, err.code: ${JSON.stringify(err.code)}, err.message: ${JSON.stringify(err.message)}`);
        return;
      }
      // 执行正常业务
      console.info(`bundleName = ${snapshot.ability.bundleName}`);
    });
  });
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```
