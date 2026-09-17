# registerApplicationStateObserver (System API)

## Modules to Import

```TypeScript
```

## registerApplicationStateObserver

```TypeScript
function registerApplicationStateObserver(observer: ApplicationStateObserver): number
```

Register application state observer.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-ability-appmanager-on-f.md)

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [ApplicationStateObserver](arkts-ability-applicationstateobserver-c.md) | Yes | The application state observer. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the number code of the observer. |

**Examples**

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
