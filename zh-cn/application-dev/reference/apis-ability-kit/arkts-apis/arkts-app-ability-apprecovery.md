# @ohos.app.ability.appRecovery

appRecovery模块提供了应用在故障状态下的恢复能力。

> **说明：**  
>  
> API9仅支持单进程中单Ability的应用恢复。  
>  
> API10支持进程中包含多个Ability的场景。  
>  
> API24支持发生CPP_CRASH时应用恢复。

**起始版本：** 9

<!--Device-unnamed-declare namespace appRecovery--><!--Device-unnamed-declare namespace appRecovery-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { appRecovery } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md#enableapprecovery-1) | 使能应用恢复功能，参数按顺序填入。该接口调用后，应用从启动器启动时第一个Ability支持恢复。 |
| [restartApp](arkts-ability-apprecovery-restartapp-f.md#restartapp-1) | 重启当前进程，并拉起应用启动时第一个Ability，如果该Ability存在已经保存的状态，这些状态数据会在Ability的onCreate生命周期回调的want参数中作为wantParam属性传入。API10时将启动由[setRestartWant](arkts-ability-apprecovery-setrestartwant-f.md#setrestartwant-1)指定的Ability。如果没有指定则按以下规则启动：如果当前应用前台的Ability支持恢复，则重新拉起该Ability。如果存在多个支持恢复的Ability处于前台，则只拉起最后一个。如果没有Ability处于前台，则不拉起。可以配合[errorManager](arkts-app-ability-errormanager.md)相关接口使用。两次重启的间隔应大于一分钟，一分钟之内重复调用此接口只会退出应用不会重启应用。自动重启的行为与主动重启一致。 |
| [saveAppState](arkts-ability-apprecovery-saveappstate-f.md#saveappstate-1) | 保存当前App状态，可以配合[errorManager](arkts-app-ability-errormanager.md)相关接口使用。 |
| [saveAppState](arkts-ability-apprecovery-saveappstate-f.md#saveappstate-2) | 主动保存Ability的状态，这个状态将在下次恢复启动时使用。可以配合[errorManager](arkts-app-ability-errormanager.md)相关接口使用。 |
| [setRestartWant](arkts-ability-apprecovery-setrestartwant-f.md#setrestartwant-1) | 设置下次恢复主动拉起场景下的Ability。该Ability必须为当前包下的UIAbility。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RestartFlag](arkts-ability-apprecovery-restartflag-e.md) | 应用重启标志，[enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md#enableapprecovery-1)接口重启选项参数，该类型为枚举。 |
| [SaveModeFlag](arkts-ability-apprecovery-savemodeflag-e.md) | 状态保存标志，[enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md#enableapprecovery-1)接口状态保存方式的参数，该类型为枚举。 |
| [SaveOccasionFlag](arkts-ability-apprecovery-saveoccasionflag-e.md) | 保存条件标志，[enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md#enableapprecovery-1)接口状态保存时的选项参数，该类型为枚举。 |

