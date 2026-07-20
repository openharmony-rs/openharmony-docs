# enableAppRecovery

## 导入模块

```TypeScript
import { appRecovery } from '@kit.AbilityKit';
```

<a id="enableapprecovery"></a>
## enableAppRecovery

```TypeScript
function enableAppRecovery(restart?: RestartFlag, saveOccasion?: SaveOccasionFlag, saveMode?: SaveModeFlag) : void
```

使能应用恢复功能，参数按顺序填入。该接口调用后，应用从启动器启动时第一个Ability支持恢复。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-appRecovery-function enableAppRecovery(restart?: RestartFlag, saveOccasion?: SaveOccasionFlag, saveMode?: SaveModeFlag) : void--><!--Device-appRecovery-function enableAppRecovery(restart?: RestartFlag, saveOccasion?: SaveOccasionFlag, saveMode?: SaveModeFlag) : void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| restart | [RestartFlag](arkts-ability-apprecovery-restartflag-e.md) | 否 | 枚举类型，发生对应故障时是否重启，默认为重启。 |
| saveOccasion | [SaveOccasionFlag](arkts-ability-apprecovery-saveoccasionflag-e.md) | 否 | 枚举类型，状态保存时机，默认为故障时保存。 |
| saveMode | [SaveModeFlag](arkts-ability-apprecovery-savemodeflag-e.md) | 否 | 枚举类型，状态保存方式， 默认为文件缓存。 |

