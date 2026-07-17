# StartupListener

本模块提供[应用启动框架](../../../../application-models/app-startup.md)任务监听器的定义。

**起始版本：** 12

<!--Device-unnamed-declare class StartupListener--><!--Device-unnamed-declare class StartupListener-End-->

**系统能力：** SystemCapability.Ability.AppStartup

## 导入模块

```TypeScript
import { StartupListener } from '@kit.AbilityKit';
```

## onCompleted

```TypeScript
onCompleted?(error: BusinessError<void>): void
```

在所有启动任务完成时调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupListener-onCompleted?(error: BusinessError<void>): void--><!--Device-StartupListener-onCompleted?(error: BusinessError<void>): void-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [BusinessError](../../apis-arkui/arkts-components/arkts-arkui-businesserror-t.md)<void> | 是 | 错误信息。 |

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

