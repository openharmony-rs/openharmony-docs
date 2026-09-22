# getCalendarManager

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## getCalendarManager

```TypeScript
function getCalendarManager(context: Context) : CalendarManager
```

Obtains a CalendarManager object based on the context.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. For details about the application context of the stage model, see Context. |

**Return value:**

| Type | Description |
| --- | --- |
| [CalendarManager](arkts-calendar-calendarmanager-calendarmanager-i.md) | CalendarManager object obtained. |

**Examples**

> NOTE
> 
> For details about how to obtain an mContext object in the example, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
// Obtain an mContext object.
// Obtain a calendarMgr object.
// The file is auto-generated: entry/src/main/ets/entryability/EntryAbility.ets
// The file must be configured for the subsequent sample code in the document to run properly.
import {
  abilityAccessCtrl,
  AbilityConstant, 
  common, 
  PermissionRequestResult, 
  Permissions, 
  UIAbility, 
  Want
} from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { calendarManager } from '@kit.CalendarKit';
import { window } from '@kit.ArkUI';

export let calendarMgr: calendarManager.CalendarManager | null = null;
export let mContext: common.UIAbilityContext | null = null;
export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    console.info('Ability onCreate');
  }

  onDestroy(): void {
    console.info('Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // The main window has been created. Set the main page for the Ability.
    console.info('Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
    mContext = this.context;
    const permissions: Permissions[] = ['ohos.permission.READ_CALENDAR', 'ohos.permission.WRITE_CALENDAR'];
    let atManager = abilityAccessCtrl.createAtManager();
    atManager.requestPermissionsFromUser(mContext, permissions).then((result: PermissionRequestResult) => {
      console.info(`get Permission success, result: ${JSON.stringify(result)}`);
      calendarMgr = calendarManager.getCalendarManager(mContext);
    }).catch((error: BusinessError) => {
      console.error(`get Permission error, error. Code: ${error.code}, message: ${error.message}`);
    })
  }

  onWindowStageDestroy(): void {
    // The main window is destroyed. It is time to release UI resources.
    console.info('Ability onWindowStageDestroy');
  }

  onForeground(): void {
    // Switch the ability to the foreground.
    console.info('Ability onForeground');
  }

  onBackground(): void {
    // Switch the ability to the background.
    console.info('Ability onBackground');
  }
}
```
