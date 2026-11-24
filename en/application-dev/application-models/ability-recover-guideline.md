---
kits: ["Ability Kit"]
description: "Describes the operating mechanism and development steps of the UIAbility backup and restore feature, helping applications restore the page stack and business data on the next startup after an abnormal exit to ensure user experience continuity."
keywords: [UIAbility, backup and restore, setRestoreEnabled, onSaveState, page stack restoration, data recovery, state restore]
doctype: guide
status: active
---
# UIAbility Backup and Restore

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel; @Luobniz21-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=f92d5a4fab1366fe913ccd9c81db56ab439390df translatedAt=2026-11-23T07:45:00.004Z pushedAt=2026-11-24T08:02:58.562Z nl=1 -->

## When to Use

When an application runs in the background, it may be closed or its process may exit due to reasons such as system resource control. Direct application exit may cause user data loss. If the application enables the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) backup and restore feature in [UIAbilityContext](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) and saves temporary data, it can restore the previous state and data on the next startup after the application exits. This includes the application's page stack and the data saved in the [onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate) interface, thereby ensuring user experience continuity.

> **NOTE**
>
> If the application is stopped normally, the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) backup process is not triggered. If the application is started normally (for example, by calling the **startAbility** API or clicking the icon), the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) restore process is not triggered.

For page stack restoration configuration and deep stack backfill of multi-page applications such as Navigation/router, see [UIAbility Backup and Restore Adaptation Guide](app-restore-adaptation.md).

## Working Mechanism
- [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) data backup: When an application runs in the background and exits abnormally due to system resource management, process kill, unexpected crash, or other reasons, the system automatically calls [onSaveState()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate) to perform backup.
- [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) data restore: The restored [Want](../reference/apis-ability-kit/js-apis-app-ability-want.md) data can be obtained in the [onCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate) lifecycle of the application, and the page stack data is restored in the [onWindowStageCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate) lifecycle of the application.

## Constraints

- The [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) backup and restore feature supports multiple instances. Backup data is stored in the application sandbox path as files for seven days.

- Backup data is stored in the parameters field of [Want](../reference/apis-ability-kit/js-apis-app-ability-want.md#want). Due to serialization size limits, the maximum supported data size is 200 KB.

- Data restore is unavailable after device restart.

- The backup and restore mechanism depends on the mission retention mechanism. If the application sets [removeMissionAfterTerminate](../quick-start/module-configuration-file.md#abilities) to true, or the device does not support mission retention (for example, PC/2-in-1 devices), the backup and restore mechanism does not take effect.

- The data backup and restore feature is unavailable for a [UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md).

## Available APIs

The [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) backup and restore interface is provided by the [UIAbilityContext](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) module. The developer can call it directly through **this.context** in [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md). For details, see [How to Develop](#how-to-develop).

| API                                                      | Description                                                |
| ------------------------------------------------------------ | ---------------------------------------------------- |
| setRestoreEnabled(enabled: boolean): void | Sets whether to enable backup and restore for the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md).|

The [setRestoreEnabled()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setrestoreenabled14) API must be called during application initialization (before [onForeground()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onforeground)), for example, in the [onCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate) call of [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md).


## How to Develop

To enable [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) backup and restore during application module initialization, refer to the code snippet below.

<!-- @[onCreate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/EntryAbility.ets) -->

``` TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
// ···

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(DOMAIN, 'EntryAbility', '[Demo] EntryAbility onCreate');
    this.context.setRestoreEnabled(true);
    // ···
  }

// ···
}
```

To proactively save data and restore the data when the UIAbility is started, refer to the code snippet below.

<!-- @[onSaveState](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityRecover/entry/src/main/ets/entryability/EntryAbility.ets) -->

``` TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
// ···

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(DOMAIN, 'EntryAbility', '[Demo] EntryAbility onCreate');
    this.context.setRestoreEnabled(true);
    if (want && want.parameters) {
      let recoveryMyData = want.parameters['myData'];
    }
  }

  onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>): AbilityConstant.OnSaveResult {
    // Save the application data.
    hilog.info(DOMAIN, 'EntryAbility', '[Demo] EntryAbility onSaveState');
    wantParam['myData'] = 'my1234567';
    return AbilityConstant.OnSaveResult.ALL_AGREE;
  }

// ···
}
```
