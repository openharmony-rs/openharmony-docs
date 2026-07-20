# StartupConfigEntry

本模块提供[应用启动框架](docroot://application-models/app-startup.md)配置的能力。

**起始版本：** 12

<!--Device-unnamed-declare class StartupConfigEntry--><!--Device-unnamed-declare class StartupConfigEntry-End-->

**系统能力：** SystemCapability.Ability.AppStartup

## 导入模块

```TypeScript
import { StartupConfigEntry } from '@kit.AbilityKit';
```

<a id="onconfig"></a>
## onConfig

```TypeScript
onConfig?(): StartupConfig
```

在回调[AbilityStage.onCreate](arkts-ability-app-ability-abilitystage-abilitystage-c.md#oncreate-1)前，若该AbilityStage对应的HAP中启动框架配置文件中[定义了启动框架配置](docroot://application-models/app-startup.md#定义启动参数配置)，则会触发该回调。

开发者可以在该回调中设置启动框架配置信息，详细使用方法可参考[设置启动参数](docroot://application-models/app-startup.md#设置启动参数)章节。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupConfigEntry-onConfig?(): StartupConfig--><!--Device-StartupConfigEntry-onConfig?(): StartupConfig-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StartupConfig](arkts-ability-app-appstartup-startupconfig-startupconfig-i.md) | 启动框架配置信息。 |

**示例：**

```TypeScript
import { StartupConfig, StartupConfigEntry, StartupListener } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class MyStartupConfigEntry extends StartupConfigEntry {
  onConfig() {
    hilog.info(0x0000, 'testTag', `onConfig`);
    let onCompletedCallback = (error: BusinessError<void>) => {
      hilog.info(0x0000, 'testTag', `onCompletedCallback`);
      if (error) {
        hilog.error(0x0000, 'testTag', 'onCompletedCallback: %{public}d, message: %{public}s', error.code,
          error.message);
      } else {
        hilog.info(0x0000, 'testTag', `onCompletedCallback: success.`);
      }
    }
    let startupListener: StartupListener = {
      'onCompleted': onCompletedCallback
    }
    let config: StartupConfig = {
      'timeoutMs': 10000,
      'startupListener': startupListener
    }
    return config;
  }
}

```

<a id="onrequestcustommatchrule"></a>
## onRequestCustomMatchRule

```TypeScript
onRequestCustomMatchRule(want: Want): string
```

在回调[AbilityStage.onCreate](arkts-ability-app-ability-abilitystage-abilitystage-c.md#oncreate-1)前，若该AbilityStage对应的HAP中启动框架配置文件中[定义了启动框架配置](docroot://application-models/app-startup.md#定义启动参数配置)，则会在[StartupConfigEntry.onConfig](arkts-ability-app-appstartup-startupconfigentry-startupconfigentry-c.md#onconfig-1)后触发该回调。

开发者可以在该回调中，可以根据调用方传入启动UIAbility的Want中的不同参数来返回不同的自定义匹配规则。启动框架会将其与启动任务配置的matchRules中customization字段进行匹配。若匹配成功，任务将在自动模式执行。详细匹配规则请参考[添加任务匹配规则](docroot://application-models/app-startup.md#添加任务匹配规则)章节。

该接口通常用于无法直接通过uri、action或意图名称规则来匹配启动任务的场景，可以使用本接口对匹配规则进一步细化。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupConfigEntry-onRequestCustomMatchRule(want: Want): string--><!--Device-StartupConfigEntry-onRequestCustomMatchRule(want: Want): string-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动UIAbility的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回自定义匹配规则值，用于匹配启动任务是否自动执行。 |

**示例：**

```TypeScript
import { StartupConfigEntry, Want } from '@kit.AbilityKit';

export default class MyStartupConfigEntry extends StartupConfigEntry {
  // ...

  onRequestCustomMatchRule(want: Want): string {
    if (want?.parameters?.customParam == 'param1') {
      return 'customRule1';
    }
    return '';
  }
}

```

