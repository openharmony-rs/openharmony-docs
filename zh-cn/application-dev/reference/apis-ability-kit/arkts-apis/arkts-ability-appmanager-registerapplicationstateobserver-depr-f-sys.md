# registerApplicationStateObserver（系统接口）

<a id="registerapplicationstateobserver"></a>
## registerApplicationStateObserver

```TypeScript
function registerApplicationStateObserver(observer: ApplicationStateObserver): number
```

注册全部应用程序状态观测器。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function registerApplicationStateObserver(observer: ApplicationStateObserver): number--><!--Device-appManager-function registerApplicationStateObserver(observer: ApplicationStateObserver): number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [ApplicationStateObserver](arkts-ability-applicationstateobserver-c.md) | 是 | 表示程序状态观测器，用于观测应用的生命周期变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 已注册观测器的数字代码。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';

const observerCode = appManager.registerApplicationStateObserver({
  onForegroundApplicationChanged(appStateData) {
    console.info(`onForegroundApplicationChanged, appStateData: ${appStateData}.`);
  },
  onAbilityStateChanged(abilityStateData) {
    console.info(`onAbilityStateChanged, abilityStateData: ${abilityStateData}.`);
  },
  onProcessCreated(processData) {
    console.info(`onProcessCreated, processData: ${processData}.`);
  },
  onProcessDied(processData) {
    console.info(`onProcessDied, processData: ${processData}.`);
  },
  onProcessStateChanged(processData) {
    console.info(`onProcessStateChanged, processData: ${processData}.`);
  },
  onAppStarted(appStateData) {
    console.info(`onAppStarted, appStateData: ${JSON.stringify(appStateData)}`);
  },
  onAppStopped(appStateData) {
    console.info(`onAppStopped, appStateData: ${JSON.stringify(appStateData)}`);
  }
});
console.info(`observerCode: ${observerCode}.`);

```

