# ProcessData

```TypeScript
export type ProcessData = _ProcessData.default
```

进程数据信息。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**属性类型：** _ProcessData.default

**示例**

```TypeScript
import { appManager } from '@kit.AbilityKit';

let applicationStateObserver: appManager.ApplicationStateObserver = {
  onForegroundApplicationChanged(appStateData) {
    console.info(`onForegroundApplicationChanged, appStateData: ${JSON.stringify(appStateData)}.`);
  },
  onAbilityStateChanged(abilityStateData) {
    console.info(`onAbilityStateChanged, abilityStateData: ${JSON.stringify(abilityStateData)}.`);
  },
  onProcessCreated(processData) {
    console.info(`onProcessCreated, processData: ${JSON.stringify(processData)}.`);
  },
  onProcessDied(processData) {
    console.info(`onProcessDied, processData: ${JSON.stringify(processData)}.`);
  },
  onProcessStateChanged(processData) {
    console.info(`onProcessStateChanged, processData: ${JSON.stringify(processData)}.`);
  },
  onAppStarted(appStateData) {
    console.info(`onAppStarted, appStateData: ${JSON.stringify(appStateData)}.`);
  },
  onAppStopped(appStateData) {
    console.info(`onAppStopped, appStateData: ${JSON.stringify(appStateData)}.`);
  }
};
let observerCode = appManager.on('applicationState', applicationStateObserver);
```
