# setRestartWant

## 导入模块

```TypeScript
import { appRecovery } from '@kit.AbilityKit';
```

## setRestartWant

```TypeScript
function setRestartWant(want: Want): void
```

设置下次恢复主动拉起场景下的Ability。该Ability必须为当前包下的UIAbility。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-appRecovery-function setRestartWant(want: Want): void--><!--Device-appRecovery-function setRestartWant(want: Want): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 通过设置Want中"bundleName"和"abilityName"字段来指定恢复重启的Ability。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { appRecovery, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  build() {
    Button("启动到恢复Ability")
      .fontSize(40)
      .fontWeight(FontWeight.Bold)
      .onClick(() => {
        // set restart want
        let want: Want = {
          bundleName: "ohos.samples.recovery",
          abilityName: "RecoveryAbility"
        };

        appRecovery.setRestartWant(want);
      })
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { appRecovery, Want } from '@kit.AbilityKit';
import { Entry, Component, Button, FontWeight } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Button("启动到恢复Ability")
      .fontSize(40)
      .fontWeight(FontWeight.Bold)
      .onClick(() => {
        // set restart want
        let want: Want = {
          bundleName: "ohos.samples.recovery",
          abilityName: "RecoveryAbility"
        };

        appRecovery.setRestartWant(want);
      })
  }
}
```

