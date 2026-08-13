# AbilityForegroundStateObserver（系统接口）

定义应用前后台状态监听。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-export default class AbilityForegroundStateObserver--><!--Device-unnamed-export default class AbilityForegroundStateObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onAbilityStateChanged

```TypeScript
onAbilityStateChanged(abilityStateData: AbilityStateData): void
```

当Ability前后台状态发生变化时，系统会触发该回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-AbilityForegroundStateObserver-onAbilityStateChanged(abilityStateData: AbilityStateData): void--><!--Device-AbilityForegroundStateObserver-onAbilityStateChanged(abilityStateData: AbilityStateData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityStateData | [AbilityStateData](arkts-ability-abilitystatedata-c.md) | 是 | Ability状态信息。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: abilityManager.AbilityForegroundStateObserver = {
  onAbilityStateChanged(abilityStateData) {
    console.info(`onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  },
};
try {
  abilityManager.on('abilityForegroundState', observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error code: ${code}, error msg: ${message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class ObserverCustom implements abilityManager.AbilityForegroundStateObserver {
  onAbilityStateChanged(abilityStateData: abilityManager.AbilityStateData) {
    console.info(`onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  }
}
;
try {
  let observer = new ObserverCustom();
  abilityManager.onAbilityForegroundState(observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error code: ${code}, error msg: ${message}`);
}
```

