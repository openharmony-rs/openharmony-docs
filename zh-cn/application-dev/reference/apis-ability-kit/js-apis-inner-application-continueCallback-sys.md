# ContinueCallback (系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @w_Machine_cc-->

表示跨设备迁移Mission完成后，返回迁移结果的回调函数，迁移Mission详见：[continueMission接口](js-apis-distributedMissionManager-sys.md#distributedmissionmanagercontinuemission)。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。  
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
> 本模块接口为系统接口。

## ContinueCallback.onContinueDone

ArkTS-Dyn：onContinueDone(result: number): void

ArkTS-Sta：onContinueDone(result: int): void

Mission迁移完成后调用，返回迁移结果。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| result |  number | 是 | 迁移任务的结果，0表示迁移成功，其他表示迁移失败。 |

**示例：**

ArkTS-Dyn示例:

```ts
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

distributedMissionManager.continueMission(
  {
    srcDeviceId: '123',
    dstDeviceId: '456',
    missionId: 123,
    wantParam: {
      'key': 'value'
    }
  },
  {
    onContinueDone(result: number) {
      console.info(`onContinueDone, result: ${JSON.stringify(result)}`);
    }
  }, (error: BusinessError) => {
  if (error && error.code) {
    console.error(`continueMission failed, error.code: ${error.code}, error.message: ${error.message}`);
  }
  console.info(`continueMission finished`);
});
```

ArkTS-Sta示例：

```ts
import distributedMissionManager from '@ohos.distributedMissionManager';
import { BusinessError } from '@ohos.base';

function onContinueDone(result: int) {
  console.info(`onContinueDone, result: ${JSON.stringify(result)}`);
}
let options:distributedMissionManager.ContinueCallback={
  onContinueDone: onContinueDone
}
let continueDeviceInfo:distributedMissionManager.ContinueDeviceInfo={
  srcDeviceId: '123',
  dstDeviceId: '456',
  missionId: 123,
  wantParam: {
    'key': 'value'
  }
}
distributedMissionManager.continueMission(
  continueDeviceInfo,
  options,
  (error: BusinessError|null,data:string[]|undefined) => {
  if (error && error.code) {
    console.error(`continueMission failed, error.code: ${error.code}, error.message: ${error.message}`);
  }
  console.info(`continueMission finished`);
});
```
