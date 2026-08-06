# StartupListener

本模块提供\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_任务监听器的定义。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class StartupListener--><!--Device-unnamed-declare class StartupListener-End-->

**系统能力：** SystemCapability.Ability.AppStartup

## onCompleted

```TypeScript
onCompleted?(error: BusinessError<void>): void
```

在所有启动任务完成时调用。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupListener-onCompleted?(error: BusinessError<void>): void--><!--Device-StartupListener-onCompleted?(error: BusinessError<void>): void-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 错误信息。 |

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

## onCompleted

```TypeScript
onCompleted?: OnCompletedFn
```

所有启动任务完成时的回调函数。

**类型：** OnCompletedFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupListener-onCompleted?: OnCompletedFn--><!--Device-StartupListener-onCompleted?: OnCompletedFn-End-->

**系统能力：** SystemCapability.Ability.AppStartup

