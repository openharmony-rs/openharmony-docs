# ContinueCallback (系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->

表示跨设备迁移Mission完成后，返回迁移结果的回调函数，迁移Mission详见：[continueMission接口](js-apis-distributedMissionManager-sys.md#distributedmissionmanagercontinuemission)。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块接口为系统接口。
> 本模块接口仅可在Stage模型下使用。

## ContinueCallback.onContinueDone

onContinueDone(result: number): void;

Mission迁移完成后调用，通过回调参数result返回迁移结果。开发者应根据返回的result参数判断迁移是否成功，并据此执行相应的后续操作，如提示用户、重试或终止任务。

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| result |  number | 是 | 迁移任务的结果，0表示迁移成功，非0值表示迁移失败。 |

**示例：**

```ts
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 调用continueMission方法，发起任务迁移 
distributedMissionManager.continueMission(
  {
    srcDeviceId: '123', // 源设备ID 
    dstDeviceId: '456', // 目标设备ID
    missionId: 123, // 任务ID
    wantParam: {
      'key': 'value' // 迁移数据
    }
  },
  {
    // 迁移完成回调函数，接收迁移结果  
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
