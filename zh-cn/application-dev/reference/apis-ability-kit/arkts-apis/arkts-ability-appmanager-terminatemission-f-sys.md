# terminateMission（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## terminateMission

```TypeScript
function terminateMission(missionId: number): Promise<void>
```

关闭指定的任务。使用Promise异步回调。

**起始版本：** 13

**需要权限：** ohos.permission.KILL_APP_PROCESSES

<!--Device-appManager-function terminateMission(missionId: int): Promise<void>--><!--Device-appManager-function terminateMission(missionId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 任务ID，可通过[getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md#getmissioninfos-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

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
              console.error('terminateMission failed. err: ' + JSON.stringify(err));
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

