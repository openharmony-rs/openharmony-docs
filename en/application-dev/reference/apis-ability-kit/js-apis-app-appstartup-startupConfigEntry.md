# @ohos.app.appstartup.StartupConfigEntry (AppStartup Configuration Entry)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a914ec5c20531defc3768aa8242b62bbe2d1d08f translatedAt=2026-09-03T10:45:17.436Z pushedAt=2026-09-05T11:31:25.463Z -->


This module provides the capability of configuring the [application startup framework](../../application-models/app-startup.md), including setting the execution timeout of the startup framework, registering a startup completion listener, and customizing startup task matching rules. It applies to scenarios where the execution behavior of startup tasks needs to be controlled on demand during the AbilityStage startup phase of different HAPs, helping developers flexibly configure the running policy of the startup framework.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { StartupConfigEntry } from '@kit.AbilityKit';
```

## StartupConfigEntry

### onConfig

onConfig?(): StartupConfig

This callback is triggered before [AbilityStage.onCreate](js-apis-app-ability-abilityStage.md#oncreate) if the [HAP](../../../application-dev/quick-start/hap-package.md) corresponding to the AbilityStage has [defined the startup framework configuration](../../application-models/app-startup.md#defining-startup-parameter-configuration) in its startup framework configuration file. This method is optional.

Developers can set the startup framework configuration information within this callback. For details, see [Setting Startup Parameters](../../application-models/app-startup.md#setting-startup-parameters). If custom matching rules are required, the [onRequestCustomMatchRule](#onrequestcustommatchrule20) callback is triggered after this callback completes.

**System capability**: SystemCapability.Ability.AppStartup

**Return value**

| Type| Description|
| -------- | -------- |
| [StartupConfig](js-apis-app-appstartup-startupConfig.md#startupconfig) | AppStartup configuration.|

**Example**

```ts
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

### onRequestCustomMatchRule<sup>20+</sup>

onRequestCustomMatchRule(want: Want): string

If the [startup framework configuration is defined](../../application-models/app-startup.md#defining-startup-parameter-configuration) in the startup framework configuration file of the HAP corresponding to the AbilityStage, this callback is triggered before [AbilityStage.onCreate](js-apis-app-ability-abilityStage.md#oncreate) and after [StartupConfigEntry.onConfig](#onconfig).

Developers can use this callback to return different custom matching rules based on different parameters in the Want object passed by the caller to start the [UIAbility](js-apis-app-ability-uiAbility.md). The startup framework matches these rules with the **customization** field in the matchRules of the startup task configuration. If the match succeeds, the task is executed in automatic mode. For details about the matching rules, see [Adding Task Matching Rules](../../application-models/app-startup.md#adding-task-matching-rules).

This API is typically used in scenarios where tasks cannot be matched directly using URI, action, or intent name rules. It allows for further refinement of matching rules.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|

**Return value**

| Type| Description|
| -------- | -------- |
| string | Custom matching rule, which is used to determine whether to automatically execute the task.|

**Example**

```ts
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
