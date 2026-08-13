# terminateMission（系统接口）

## terminateMission

```TypeScript
function terminateMission(missionId: int): Promise<void>
```

关闭指定的任务。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.KILL_APP_PROCESSES

<!--Device-appManager-function terminateMission(missionId: int): Promise<void>--><!--Device-appManager-function terminateMission(missionId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | int | 是 | 任务ID，可通过 [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md#getMissionInfos（系统接口）) 获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Button('start link', { type: ButtonType.Capsule, stateEffect: true })
      .width('87%')
      .height('5%')
      .margin({ bottom: '12vp' })
      .onClick(() => {
        let missionId: number = 0;
        try {
          appManager.terminateMission(missionId).then(()=>{
              console.info('terminateMission success.');
            }).catch((err: BusinessError)=>{
              console.error(`terminateMission failed. err: ${err.code}, ${err.message}`);
            })
        } catch (paramError) {
          let code = (paramError as BusinessError).code;
          let message = (paramError as BusinessError).message;
          console.error(`[appManager] error: ${code}, ${message}`);
        }
      })
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { Entry, Text, Component, Button, ButtonType, State } from '@kit.ArkUI';
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Button('start link', { type: ButtonType.Capsule, stateEffect: true })
      .width('87%')
      .height('5%')
      .onClick(() => {
        let missionId: int = 0;
        try {
          appManager.terminateMission(missionId).then(() => {
            console.info('terminateMission success.');
          }).catch((e) => {
            let err = e as BusinessError;
            console.error(`terminateMission failed. err: ${err.code}, ${err.message}`);
          })
        } catch (paramError) {
          let code = (paramError as BusinessError).code;
          let message = (paramError as BusinessError).message;
          console.error(`[appManager] error: ${code}, ${message}`);
        }
      })
  }
}
```

