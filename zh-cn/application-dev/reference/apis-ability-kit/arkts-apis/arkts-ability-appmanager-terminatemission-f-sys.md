# terminateMission（系统接口）

## terminateMission

```TypeScript
function terminateMission(missionId: int): Promise<void>
```

关闭指定的任务。使用Promise异步回调。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.KILL_APP_PROCESSES

<!--Device-appManager-function terminateMission(missionId: int): Promise<void>--><!--Device-appManager-function terminateMission(missionId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 任务ID，可通过[getMissionInfos]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

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

