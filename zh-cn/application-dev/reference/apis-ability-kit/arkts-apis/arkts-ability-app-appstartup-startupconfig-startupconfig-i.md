# StartupConfig

本模块提供[应用启动框架](../../../application-models/app-startup.md)配置信息的定义。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AppStartup

## 导入模块

```TypeScript
import { StartupConfig } from '@kit.AbilityKit';
```

## startupListener

```TypeScript
startupListener?: StartupListener
```

表示启动框架的监听器，该监听器将在所有启动任务完成时调用。

**类型：** [StartupListener](arkts-ability-app-appstartup-startuplistener-startuplistener-c.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppStartup

## timeoutMs

```TypeScript
timeoutMs?: number
```

执行所有启动任务的超时时间（单位：毫秒），默认值为10000毫秒。

**类型：** number

**默认值：** 10000

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppStartup

**示例**

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
    };
    let startupListener: StartupListener = {
      'onCompleted': onCompletedCallback
    };
    let config: StartupConfig = {
      'timeoutMs': 10000,
      'startupListener': startupListener
    };
    return config;
  }
}
```
