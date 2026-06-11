# Application Restart

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1630992de2f5af1dcca3ca27d11e23e0321182c9 translatedAt=2026-05-30T07:46:28.056Z pushedAt=2026-06-01T11:40:44.952Z -->

Application restart is used to re-initialize an application or restore it to a normal state in different scenarios. The system provides application active restart, atomic service active restart, and application fault recovery passive restart. Developers can choose an appropriate solution based on actual requirements.

## Application Active Restart for Re-initialization

The system provides two methods for actively restarting an application: "restart without retaining application window" and "restart with application window retained". The following is a capability comparison of the two application active restart methods. Developers can choose based on their service requirements.

| Comparison Dimension | Restart Without Retaining Application Window | Restart with Application Window Retained |
| --------- | ------------------- | ----------------- |
| Applicable Scenario | The application encounters an internal state issue and requires complete re-initialization; the application has completed a dynamic update and needs to start from the initial state. | The application encounters an internal state issue and requires complete re-initialization without exposing the home screen; the application has completed a dynamic update and needs to start from the initial state without exposing the home screen. |
| User Experience | Lacks continuity; the home screen is visible in the user view. The user may experience a sense of disruption. | Provides continuity; the application remains in the user view. This avoids a sense of disruption in the user experience. |
| Calling Interface | ApplicationContext.restartApp<sup>12+</sup> | UIAbilityContext.restartApp<sup>22+</sup> |

### Restart without Retaining Application Window

Starting from API version 12, ApplicationContext provides the [restartApp](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextrestartapp12) interface for actively restarting the application and launching a specified UIAbility. The current application window is not retained during the restart process, which is equivalent to a complete application restart. The onDestroy lifecycle callback of the Ability in the application is not triggered during the restart process.

The following constraints and limitations exist:

- This interface can only be called from the main thread.

- The application to be restarted must be in the focused state.

- Repeatedly calling the restart API within 3 seconds is not supported.

Sample code:
<!-- @[restartapp_withoutWindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/restartapp/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'restartApp';
  private context = this.getUIContext().getHostContext()?.getApplicationContext() as common.ApplicationContext;

  build() {
    RelativeContainer() {
      Button(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          // Specify the current UIAbility
          let want: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility'
          };
          if (this.context) {
            try {
              // Trigger restart of the UIAbility specified by want
              this.context.restartApp(want);
            } catch (err) {
              hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
            }
          } else {
            hilog.error(0x0000, 'testTag', "%{public}s", 'AppContext is null');
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Restart with Application Window Retained

Starting from API version 22, UIAbilityContext provides the [restartApp](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#restartapp22) API, which is used to restart the process where the current UIAbility resides and launch a specified UIAbility within the application. Unlike the restartApp of ApplicationContext, this API can choose to retain the current window or jump to a new window. The onDestroy lifecycle callback of the Ability in the process is not triggered during the restart process.

The following constraints and limitations apply:

- This API can only be called from the main thread.

- The application to be restarted must be in the focused state.

- Repeatedly calling the restart API within 3 seconds is not supported.

Sample code:

1. Specify the current UIAbility, and refresh the current window to its initial state after the restart.

   <!-- @[restartapp_withOldWindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/restartapp/entry/src/main/ets/pages/Index2.ets) -->

   ``` TypeScript
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { common, Want } from '@kit.AbilityKit';

   @Entry
   @Component
   struct Index {
     @State message: string = 'restartApp with window';

     build() {
       RelativeContainer() {
         Button(this.message)
           .id('HelloWorld')
           .fontSize($r('app.float.page_text_font_size'))
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(async () => {
             // Specify the current UIAbility and refresh the current window
             let want: Want = {
               bundleName: 'com.example.myapplication',
               abilityName: 'EntryAbility'
             };
             let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
             try {
               // Trigger the restart of the UIAbility specified by want
               await context.restartApp(want);
               hilog.info(0x0000, 'testTag', 'restart success');
             } catch (err) {
               hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
             }
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```

2. Specify another UIAbility within the application, and redirect to and open a new Ability window after the restart.

   <!-- @[restartapp_withNewWindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/restartapp/entry/src/main/ets/pages/Index3.ets) -->

   ``` TypeScript
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { common, Want } from '@kit.AbilityKit';

   @Entry
   @Component
   struct Index {
     @State message: string = 'restartApp to new page';

     build() {
       RelativeContainer() {
         Button(this.message)
           .id('HelloWorld')
           .fontSize($r('app.float.page_text_font_size'))
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(async () => {
             // Specify another UIAbility in the application and switch to a new window
             let want: Want = {
               bundleName: 'com.example.myapplication',
               abilityName: 'SecondAbility'
             };
             let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
             try {
               // Trigger the restart of the UIAbility specified by want
               await context.restartApp(want);
               hilog.info(0x0000, 'testTag', 'restart to new page success');
             } catch (err) {
               hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
             }
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```

## Atomic Service Active Restart

Starting from API version 20, the system provides a dedicated restart API [restartSelfAtomicService](../reference/apis-ability-kit/js-apis-app-ability-abilityManager.md#abilitymanagerrestartselfatomicservice20) for Atomic Service, which is used to trigger an Atomic Service update and restart the current Atomic Service. The current Atomic Service window is not retained during the restart process, and the onDestroy lifecycle callback of the old Ability is not triggered.

The following constraints and limitations apply:

- Only pulling up an atomic service in independent window mode is supported.

- Repeatedly calling the restart API within 3 seconds is not supported.

An atomic service is a special form of application and can also be restarted using [Application Active Restart for Re-initialization](#application-active-restart-for-re-initialization).

The following compares the capabilities of the three methods for actively restarting an atomic service. Developers can choose based on their service requirements.

| Comparison Dimension | Atomic Service Active Restart | Restart Without Retaining Atomic Service Window | Restart with Atomic Service Window Retained |
| --------- | ----------------  | ------------------- | ----------------- |
| Applicable Scenario | The atomic service actively triggers an update and re-initialization; the atomic service encounters an internal state issue and requires a complete re-initialization. | The atomic service encounters an internal state issue and requires a complete re-initialization; the atomic service completes a dynamic update and needs to start from the initial state. | The atomic service encounters an internal state issue and requires a complete re-initialization without exposing the home screen; the atomic service completes a dynamic update and needs to start from the initial state without exposing the home screen. |
| User Experience | Not continuous; the home screen is visible in the user view. The user may experience a sense of discontinuity. | Not continuous; the home screen is visible in the user view. The user may experience a sense of discontinuity. | Continuous; the user view stays on the application. This avoids a sense of discontinuity in the user experience. |
| Install-free Update | Supported                          | Not supported                           | Not supported                      |
| API | AbilityManager.restartSelfAtomicService<sup>20+</sup> | ApplicationContext.restartApp<sup>12+</sup> | UIAbilityContext.restartApp<sup>22+</sup> |

Sample code:

``` TypeScript
import { AbilityConstant, EmbeddableUIAbility, Want, abilityManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

const DOMAIN = 0x0000;

export default class DemoAbility extends EmbeddableUIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(DOMAIN, 'DemoAbility', 'DemoAbility onCreate');
    try {
      // Trigger restart of the current atomic service
      abilityManager.restartSelfAtomicService(this.context);
      hilog.info(DOMAIN, 'DemoAbility', 'restartSelfAtomicService success');
    } catch (e) {
      hilog.error(DOMAIN, 'DemoAbility', `restartSelfAtomicService error: ${JSON.stringify(e as BusinessError)}`);
    }
  }
}
```

## Passive Restart for Application Fault Recovery

The application fault recovery restart API is provided by the appRecovery module. For details, see [Development of Application Recovery](../dfx/apprecovery-guidelines.md).