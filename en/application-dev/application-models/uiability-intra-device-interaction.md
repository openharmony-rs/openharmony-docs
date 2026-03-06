# Starting UIAbility Within the Same Application

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) is the minimum unit that can be scheduled by the system. Redirection between functional modules in a device involves starting of specific UIAbility components, which belong to the same or a different application (for example, starting the UIAbility of a third-party payment application).


This topic describes how to start the UIAbility component that belongs to the same application. For details about component redirection between applications, see [Application Redirection](link-between-apps-overview.md). <!--Del-->For details about cross-device application component interaction, see [Inter-Device Application Component Interaction (Hopping)](inter-device-interaction-hop-overview.md).<!--DelEnd-->


- [Starting UIAbility in the Same Application](#starting-uiability-in-the-same-application)
- [Starting UIAbility in the Same Application and Obtaining the Return Result](#starting-uiability-in-the-same-application-and-obtaining-the-return-result)
- [Starting a Specified Page of UIAbility](#starting-a-specified-page-of-uiability)
<!--Del-->
- [Starting UIAbility with Window Mode Specified (for System Applications Only)](#starting-uiability-with-window-mode-specified-for-system-applications-only)
<!--DelEnd-->


## Starting UIAbility in the Same Application

This scenario is possible when an application contains multiple [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) components. For example, in a payment application, you may need to start the payment UIAbility from the entry UIAbility.

Assume that your application has two UIAbility components: EntryAbility and FuncAbility, either in the same module or different modules. To start FuncAbility from EntryAbility, proceed as follows:

1. In EntryAbility, call [startAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) and pass the [want](../reference/apis-ability-kit/js-apis-app-ability-want.md) parameter to start the UIAbility instance. In the **want** parameter, **bundleName** indicates the bundle name of the application to start; **abilityName** indicates the name of the UIAbility to start; **moduleName** is required only when the target UIAbility belongs to a different module from EntryAbility; **parameters** is used to carry custom information. For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](uiability-usage.md#obtaining-the-context-of-uiability).

    <!-- @[FuncAbilityA](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/pages/MainPage.ets) -->
    
    ``` TypeScript
    import { common, Want } from '@kit.AbilityKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    
    const TAG: string = '[MainPage]';
    const DOMAIN_NUMBER: number = 0xFF00;
    
    @Entry
    @Component
    struct MainPage {
      private context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    
      build() {
        Column() {
          List({ initialIndex: 0, space: 8 }) {
    
            ListItem() {
              Row() {
                // ...
              }
              .onClick(() => {
                // Context is a member of the ability object and is required for invoking inside a non-ability object.
                // Pass in the Context object.
                let wantInfo: Want = {
                  deviceId: '', // An empty deviceId indicates the local device.
                  bundleName: 'com.samples.uiabilityinteraction',
                  moduleName: 'entry', // moduleName is optional.
                  abilityName: 'FuncAbilityA',
                  parameters: {
                    // Custom information.
                    // Replace $r('app.string.main_page_return_info') with the actual resource file. In this example, the value in the resource file is "From the MainPage page of EntryAbility".
                    info: $r('app.string.main_page_return_info')
                  },
                };
                // context is the UIAbilityContext of the initiator UIAbility.
                this.context.startAbility(wantInfo).then(() => {
                  hilog.info(DOMAIN_NUMBER, TAG, 'startAbility success.');
                }).catch((error: BusinessError) => {
                  hilog.error(DOMAIN_NUMBER, TAG, 'startAbility failed.');
                });
              })
            }
    
            // ...
          }
          // ...
        }
        // ...
      }
    }
    ```

2. In FuncAbility, use [onCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate) or [onNewWant()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onnewwant) to receive the parameters passed in by EntryAbility.

    <!-- @[Ability_FuncAbilityA](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/innerability/FuncAbilityA.ets) -->

    ``` TypeScript
    import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
    // ···

    export default class FuncAbilityA extends UIAbility {
      onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Receive the parameters passed by the initiator UIAbility.
        let funcAbilityWant = want;
        let info = funcAbilityWant?.parameters?.info;
        // ···
      }

    // ···
    }
    ```

    > **NOTE**
    >
    > In FuncAbility started, you can obtain the PID and bundle name of the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) through **parameters** in the passed [want](../reference/apis-ability-kit/js-apis-app-ability-want.md) parameter.

3. To stop the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) instance after the FuncAbility service is not needed, call [terminateSelf()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself) in FuncAbility.

    <!-- @[FuncAbilityAPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/innerability/FuncAbilityAPage.ets) -->
    
    ``` TypeScript
    import { common } from '@kit.AbilityKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    
    const TAG: string = '[FuncAbilityAPage]';
    const DOMAIN_NUMBER: number = 0xFF00;
    
    @Entry
    @Component
    struct FuncAbilityAPage {
    
      build() {
        Column() {
          // Replace $r('app.string.Stop_AbilityA') with the actual resource file. In this example, the value in the resource file is "StopFuncAbilityA".
          Button($r('app.string.Stop_AbilityA'))
            .onClick(() => {
              let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext
              // context is the UIAbilityContext of the UIAbility instance to stop.
              context.terminateSelf((err) => {
                if (err.code) {
                  hilog.error(DOMAIN_NUMBER, TAG, `Failed to terminate self. Code is ${err.code}, message is ${err.message}`);
                  return;
                }
              });
            })
            // ...
        }
        // ...
      }
    }
    ```

    > **NOTE**
    >
    > When **terminateSelf()** is called to stop the UIAbility instance, the snapshot of the instance is retained by default. That is, the mission corresponding to the instance is still displayed in the recent task list. If you do not want to retain the snapshot, set **removeMissionAfterTerminate** under the [abilities](../quick-start/module-configuration-file.md#abilities) tag to **true** in the [module.json5 file](../quick-start/module-configuration-file.md) of the corresponding UIAbility.

4. To stop all [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) instances of the application, call [killAllProcesses()](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextkillallprocesses) of [ApplicationContext](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md).


## Starting UIAbility in the Same Application and Obtaining the Return Result

When starting FuncAbility from EntryAbility, you may want the result to be returned after the FuncAbility service is finished. For example, after the sign-in operation is finished in the sign-in [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) of your application, you want the sign-in result to be returned to the entry UIAbility.

1. In EntryAbility, call [startAbilityForResult()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilityforresult-2) to start FuncAbility. Use **data** in the asynchronous callback to receive information returned after FuncAbility stops itself. For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](uiability-usage.md#obtaining-the-context-of-uiability).

    <!-- @[FuncAbilityA_Result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/pages/MainPage.ets) -->
    
    ``` TypeScript
    import { common, Want } from '@kit.AbilityKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    
    const TAG: string = '[MainPage]';
    const DOMAIN_NUMBER: number = 0xFF00;
    
    @Entry
    @Component
    struct MainPage {
      private context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    
      build() {
        Column() {
          List({ initialIndex: 0, space: 8 }) {
    
            // ...
    
            ListItem() {
              Row() {
                // ...
              }
              .onClick(() => {
                let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext
                const RESULT_CODE: number = 1001;
                let want: Want = {
                  deviceId: '', // An empty deviceId indicates the local device.
                  bundleName: 'com.samples.uiabilityinteraction',
                  moduleName: 'entry', // moduleName is optional.
                  abilityName: 'FuncAbilityA',
                  parameters: {
                    // Custom information.
                    // Replace $r('app.string.main_page_return_info') with the actual resource file. In this example, the value in the resource file is "From the MainPage page of EntryAbility".
                    info: $r('app.string.main_page_return_info')
                  }
                };
                context.startAbilityForResult(want).then((data) => {
                  if (data?.resultCode === RESULT_CODE) {
                    // Parse the information returned by the target UIAbility.
                    let info = data.want?.parameters?.info;
                    hilog.info(DOMAIN_NUMBER, TAG, JSON.stringify(info) ?? '');
                    if (info !== null) {
                      this.getUIContext().getPromptAction().showToast({
                        message: JSON.stringify(info)
                      });
                    }
                  }
                  hilog.info(DOMAIN_NUMBER, TAG, JSON.stringify(data.resultCode) ?? '');
                }).catch((err: BusinessError) => {
                  hilog.error(DOMAIN_NUMBER, TAG, `Failed to start ability for result. Code is ${err.code}, message is ${err.message}`);
                });
              })
            }
    
            // ...
          }
          // ...
        }
        // ...
      }
    }
    ```

2. Call [terminateSelfWithResult()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) to stop FuncAbility. Use the input parameter [abilityResult](../reference/apis-ability-kit/js-apis-inner-ability-abilityResult.md) to carry the information that FuncAbility needs to return to EntryAbility.

    <!-- @[FuncAbilityB](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/innerability/FuncAbilityAPage.ets) -->
    
    ``` TypeScript
    import { common } from '@kit.AbilityKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    
    const TAG: string = '[FuncAbilityAPage]';
    const DOMAIN_NUMBER: number = 0xFF00;
    
    @Entry
    @Component
    struct FuncAbilityAPage {
    
      build() {
        Column() {
          // ...
    
          List({ initialIndex: 0 }) {
            ListItem() {
              Row() {
                // ...
              }
              .onClick(() => {
                let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext
                const RESULT_CODE: number = 1001; // Result returned by FuncAbilityA.
                let abilityResult: common.AbilityResult = {
                  resultCode: RESULT_CODE,
                  want: {
                    bundleName: 'com.samples.uiabilityinteraction',
                    moduleName: 'entry', // moduleName is optional.
                    abilityName: 'FuncAbilityA',
                    parameters: {
                      // Replace $r('app.string.ability_return_info') with the actual resource file. In this example, the value in the resource file is "From the Index page of FuncAbility".
                      info: context.resourceManager.getStringSync($r('app.string.ability_return_info').id)
                    },
                  },
                };
                context.terminateSelfWithResult(abilityResult, (err) => {
                  if (err.code) {
                    hilog.error(DOMAIN_NUMBER, TAG, `Failed to terminate self with result. Code is ${err.code}, message is ${err.message}`);
                    return;
                  }
                });
              })
            }
          }
          // ...
        }
        // ...
      }
    }
    ```

3. After FuncAbility stops itself, EntryAbility uses [startAbilityForResult()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilityforresult-2) to receive the information returned by FuncAbility. The value of **RESULT_CODE** must be the same as that specified in the preceding step.

    <!-- @[FuncAbilityA_For_Result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/pages/MainPage.ets) -->
    
    ``` TypeScript
    import { common, Want } from '@kit.AbilityKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    
    const TAG: string = '[MainPage]';
    const DOMAIN_NUMBER: number = 0xFF00;
    
    @Entry
    @Component
    struct MainPage {
      private context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    
      build() {
        Column() {
          List({ initialIndex: 0, space: 8 }) {
    
            // ...
    
            ListItem() {
              Row() {
                // ...
              }
              .onClick(() => {
                let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext
                const RESULT_CODE: number = 1001;
                let want: Want = {
                  deviceId: '', // An empty deviceId indicates the local device.
                  bundleName: 'com.samples.uiabilityinteraction',
                  moduleName: 'entry', // moduleName is optional.
                  abilityName: 'FuncAbilityA',
                  parameters: {
                    // Custom information.
                    // Replace $r('app.string.main_page_return_info') with the actual resource file. In this example, the value in the resource file is "From the MainPage page of EntryAbility".
                    info: $r('app.string.main_page_return_info')
                  }
                };
                context.startAbilityForResult(want).then((data) => {
                  if (data?.resultCode === RESULT_CODE) {
                    // Parse the information returned by the target UIAbility.
                    let info = data.want?.parameters?.info;
                    hilog.info(DOMAIN_NUMBER, TAG, JSON.stringify(info) ?? '');
                    if (info !== null) {
                      this.getUIContext().getPromptAction().showToast({
                        message: JSON.stringify(info)
                      });
                    }
                  }
                  hilog.info(DOMAIN_NUMBER, TAG, JSON.stringify(data.resultCode) ?? '');
                }).catch((err: BusinessError) => {
                  hilog.error(DOMAIN_NUMBER, TAG, `Failed to start ability for result. Code is ${err.code}, message is ${err.message}`);
                });
              })
            }
    
            // ...
          }
          // ...
        }
        // ...
      }
    }
    ```


## Starting a Specified Page of UIAbility

### Overview

A [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) component can have multiple pages that each display in specific scenarios.

A UIAbility component can be started in two modes:

- Cold start: The UIAbility instance is totally closed before being started. This requires that the code and resources of the UIAbility instance be completely loaded and initialized.
- Hot start: The UIAbility instance has been started, running in the foreground, and then switched to the background before being started again. In this case, the status of the UIAbility instance can be quickly restored.

This section describes how to start a specified page in both modes: [cold start](#cold-starting-uiability) and [hot start](#hot-starting-uiability). Before starting a specified page, you will learn how to specify a startup page on the initiator UIAbility.


### Specifying a Startup Page

When the initiator [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) starts another UIAbility, it usually needs to redirect to a specified page of the target UIAbility. For example, with FuncAbility, which contains two pages, starting FuncAbility means to redirect to either of the pages: Index (corresponding to the home page) and Second (corresponding to feature A page). You can configure the specified page URL in the want parameter by adding a custom parameter to parameters in [want](../reference/apis-ability-kit/js-apis-app-ability-want.md). For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](uiability-usage.md#obtaining-the-context-of-uiability).


<!-- @[FuncAbility_Cold](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/pages/MainPage.ets) -->

``` TypeScript
import { common, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[MainPage]';
const DOMAIN_NUMBER: number = 0xFF00;

@Entry
@Component
struct MainPage {
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      List({ initialIndex: 0, space: 8 }) {

        // ...

        ListItem() {
          Row() {
            // ...
          }
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext
            let want: Want = {
              deviceId: '', // An empty deviceId indicates the local device.
              bundleName: 'com.samples.uiabilityinteraction',
              moduleName: 'entry', // moduleName is optional.
              abilityName: 'ColdStartAbility',
              parameters: { // Custom parameter used to pass the page information.
                router: 'funcA'
              }
            };
            // context is the UIAbilityContext of the initiator UIAbility.
            context.startAbility(want).then(() => {
              hilog.info(DOMAIN_NUMBER, TAG, 'Succeeded in starting ability.');
            }).catch((err: BusinessError) => {
              hilog.error(DOMAIN_NUMBER, TAG, `Failed to start ability. Code is ${err.code}, message is ${err.message}`);
            });
          })
        }

        // ...
      }
      // ...
    }
    // ...
  }
}
```


### Cold Starting UIAbility

In cold start mode, obtain the parameters from the initiator [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) through the [onCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate) callback of the target UIAbility. Then, in the [onWindowStageCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate) callback of the target UIAbility, parse the [want](../reference/apis-ability-kit/js-apis-app-ability-want.md) parameter passed by the EntryAbility to obtain the URL of the page to be loaded, and pass the URL to the [windowStage.loadContent()](../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9) method.


<!-- @[ColdAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/specifiedability/ColdStartAbility.ets) -->

``` TypeScript
import { AbilityConstant, Want, UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window, UIContext } from '@kit.ArkUI';

const DOMAIN_NUMBER: number = 0xFF00;
const TAG: string = '[ColdStartAbility]';

export default class ColdStartAbility extends UIAbility {
  private funcAbilityWant: Want | undefined = undefined;
  private uiContext: UIContext | undefined = undefined;

  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // Receive the parameters passed by the initiator UIAbility.
    this.funcAbilityWant = want;
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created. Set a main page for this UIAbility.
    hilog.info(DOMAIN_NUMBER, TAG, '%{public}s', 'Ability onWindowStageCreate');
    // Main window is created. Set a main page for this UIAbility.
    let url = 'pages/Index';
    if (this.funcAbilityWant?.parameters?.router && this.funcAbilityWant.parameters.router === 'funcA') {
      url = 'pages/ColdPage';
    }
    windowStage.loadContent(url, (err, data) => {
    // ···
    });
  }
}
```

### Hot Starting UIAbility

If the target [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) has been started, the initialization logic is not executed again. Instead, the [onNewWant()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onnewwant) lifecycle callback is directly triggered. To implement redirection, parse the required parameters in **onNewWant()**.

An example scenario is as follows:

1. A user opens the SMS application. The UIAbility instance of the SMS application is started, and the home page of the application is displayed.
2. The user returns to the home screen, and the SMS application switches to the background.
3. The user opens the Contacts application and finds a contact.
4. The user touches the SMS button next to the contact. The UIAbility instance of the SMS application is restarted.
5. Since the UIAbility instance of the SMS application has been started, the onNewWant() callback of the UIAbility is triggered, and the initialization logic such as [onCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate) and [onWindowStageCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate) is skipped.

**Figure 1** Hot starting the target UIAbility

![](figures/uiability-hot-start.png)

The development procedure is as follows:

1. When the UIAbility instance of the SMS application is cold started, call [getUIContext()](../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10) in the [onWindowStageCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate) lifecycle callback to obtain the [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md).

    <!-- @[HotAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/specifiedability/HotStartAbility.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { Want, UIAbility } from '@kit.AbilityKit';
    import { window, UIContext } from '@kit.ArkUI';
    const DOMAIN_NUMBER: number = 0xFF00;
    const TAG: string = '[HotStartAbility]';
    
    export default class HotStartAbility extends UIAbility {
      private funcAbilityWant: Want | undefined = undefined;
      private uiContext: UIContext | undefined = undefined;
     // ···
     
      onWindowStageCreate(windowStage: window.WindowStage): void {
        // Main window is created. Set a main page for this UIAbility.
        hilog.info(DOMAIN_NUMBER, TAG, '%{public}s', 'Ability onWindowStageCreate');
        let url = 'pages/Index';
        windowStage.loadContent(url, (err, data) => {
          if (err.code) {
            return;
          }
    
          let windowClass: window.Window;
          windowStage.getMainWindow((err, data) => {
            if (err.code) {
              hilog.error(DOMAIN_NUMBER, TAG, `Failed to obtain the main window. Code is ${err.code}, message is ${err.message}`);
              return;
            }
            windowClass = data;
            this.uiContext = windowClass.getUIContext();
          });
          hilog.info(DOMAIN_NUMBER, TAG, 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
        });
      }
    
    // ···
    }
    ```

2. In the [onNewWant()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onnewwant) callback of the UIAbility instance of the SMS application, set the value of the global variable **nameForNavi** through AppStorage, and perform the specified page navigation. When the UIAbility instance of the SMS application is started again, the specified page of the UIAbility instance of the SMS application is displayed.

    1. Import the required modules, and set the global variable **nameForNavi** in the **onNewWant()** lifecycle callback.

        <!-- @[onNewWant](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/specifiedability/HotStartAbility.ets) -->
        
        ``` TypeScript
        import { hilog } from '@kit.PerformanceAnalysisKit';
        import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';
        // ···
        const DOMAIN_NUMBER: number = 0xFF00;
        const TAG: string = '[HotStartAbility]';
        
        export default class HotStartAbility extends UIAbility {
        // ···
        
          onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam): void {
            hilog.info(DOMAIN_NUMBER, TAG, '%{public}s', 'onNewWant');
            AppStorage.setOrCreate<string>('nameForNavi', 'pageOne');
          }
        }
        ```

    2. When the Index page is displayed, trigger the **onPageShow** callback to obtain the value of **nameForNavi**, and execute the page navigation.

        <!-- @[Index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/pages/Index.ets) -->
        
        ``` TypeScript
        @Entry
        @Component
        struct Index {
          @State message: string = 'Index';
          pathStack: NavPathStack = new NavPathStack();
        
          onPageShow(): void {
            let somePage = AppStorage.get<string>('nameForNavi')
            if (somePage) {
              this.pathStack.pushPath({ name: somePage }, false);
              AppStorage.delete('nameForNavi');
            }
          }
        
          build() {
            Navigation(this.pathStack) {
              Text(this.message)
                .id('Index')
                // Replace $r('app.float.page_text_font_size') with the actual resource file. In this example, the value in the resource file is "50fp".
                .fontSize($r('app.float.page_text_font_size'))
                .fontWeight(FontWeight.Bold)
                .alignRules({
                  center: { anchor: '__container__', align: VerticalAlign.Center },
                  middle: { anchor: '__container__', align: HorizontalAlign.Center }
                })
            }
            .mode(NavigationMode.Stack)
            .height('100%')
            .width('100%')
            .margin({top:250})
          }
        }
        ```

    3. Implement the **Navigation** subpage.

        <!-- @[PageOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/ets/pages/PageOne.ets) -->
        
        ``` TypeScript
        @Builder
        export function PageOneBuilder() {
          PageOne();
        }
        
        @Component
        export struct PageOne {
          @State message: string = 'PageOne';
          pathStack: NavPathStack = new NavPathStack();
        
          build() {
            NavDestination() {
              Text(this.message)
                .id('PageOne')
                // Replace $r('app.float.page_text_font_size') with the actual resource file. In this example, the value in the resource file is "50fp".
                .fontSize($r('app.float.page_text_font_size'))
                .fontWeight(FontWeight.Bold)
                .alignRules({
                  center: { anchor: '__container__', align: VerticalAlign.Center },
                  middle: { anchor: '__container__', align: HorizontalAlign.Center }
                })
            }
            .onReady((context: NavDestinationContext) => {
              this.pathStack = context.pathStack;
            })
            .height('100%')
            .width('100%')
            .margin({top:250})
          }
        }
        ```

    4. Configure subpages in the system configuration file **route_map.json**. For details, see [System Routing Table](../ui/arkts-navigation-cross-package.md#system-routing-table).

        ```ts
        // route_map.json
        {
          "routerMap": [
            {
              "name": "pageOne",
              "pageSourceFile": "src/main/ets/pages/PageOne.ets",
              "buildFunction": "PageOneBuilder",
              "data": {
                "description": "this is pageOne"
              }
            }
          ]
        }
        ```

    5. Configure **routerMap** in the [module.json5](../quick-start/module-configuration-file.md#routermap) file.

        <!-- @[routerMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityInteraction/entry/src/main/module.json5) -->
        
        ``` JSON5
        {
          "module": {
            // ···
            "routerMap": "$profile:router_map",
            // ···
          }
        }
        ```

> **NOTE**
>
> When the [launch type of the target UIAbility](uiability-launch-type.md) is set to **multiton**, a new instance is created each time the target UIAbility is started. In this case, the **onNewWant()** callback will not be invoked.


<!--Del-->
## Starting UIAbility with Window Mode Specified (for System Applications Only)

By specifying the window mode when starting the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) of an application, you can have the application displayed in the specified window mode, which can be full-screen, floating window, or split-screen.

In full-screen mode, an application occupies the entire screen after being started. Users cannot view other windows or applications. This mode is suitable for an application that requires users to focus on a specific task or UI.

In floating window mode, an application is displayed on the screen as a floating window after being started. Users can easily switch to other windows or applications. This mode is suitable for an application that allows users to process multiple tasks at the same time.

In split-screen mode, two applications occupy the entire screen, side by side, horizontally or vertically. This mode helps users improve multi-task processing efficiency.

The window mode is specified by the **windowMode** field in the [StartOptions](../reference/apis-ability-kit/js-apis-app-ability-startOptions.md) parameter of [startAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability).

> **NOTE**
>
> 1. If the **windowMode** field is not specified, the UIAbility is started in the default window mode.
> 2. To ensure that the application can be displayed in the required window mode, check the **supportWindowMode** field under [abilities](../quick-start/module-configuration-file.md#abilities) in the [module.json5 file](../quick-start/module-configuration-file.md) of the UIAbility and make sure the specified window mode is supported.

The following describes how to start the FuncAbility from the EntryAbility page and display it in floating window mode.

1. Add the **StartOptions** parameter in **startAbility()**.
2. Set the **windowMode** field in the **StartOptions** parameter to **WINDOW_MODE_FLOATING**. This setting applies only to a system application.
3. In the case of a third-party application, set the **displayId** field instead.

For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](uiability-usage.md#obtaining-the-context-of-uiability).

```ts
import { AbilityConstant, common, Want, StartOptions } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Page_UIAbilityComponentsInteractive]';
const DOMAIN_NUMBER: number = 0xFF00;

@Entry
@Component
struct Page_UIAbilityComponentsInteractive {
  build() {
    Column() {
      // ...
      List({ initialIndex: 0 }) {
        ListItem() {
          Row() {
            // ...
          }
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext
            let want: Want = {
              deviceId: '', // An empty deviceId indicates the local device.
              bundleName: 'com.samples.stagemodelabilitydevelop',
              moduleName: 'entry', // moduleName is optional.
              abilityName: 'FuncAbilityB',
              parameters: {
                // Custom information.
                info: 'From the Index page of EntryAbility'
              }
            };
            let options: StartOptions = {
              windowMode: AbilityConstant.WindowMode.WINDOW_MODE_FLOATING
            };
            // context is the UIAbilityContext of the initiator UIAbility.
            context.startAbility(want, options).then(() => {
              hilog.info(DOMAIN_NUMBER, TAG, 'Succeeded in starting ability.');
            }).catch((err: BusinessError) => {
              hilog.error(DOMAIN_NUMBER, TAG, `Failed to start ability. Code is ${err.code}, message is ${err.message}`);
            });
          })
        }
        // ...
      }
      // ...
    }
    // ...
  }
}
```

The display effect is shown below.

![](figures/start-uiability-floating-window.png)

<!--DelEnd-->

## Samples

The following samples are provided to help you better understand how to develop intra-device interaction between UIAbility components:

- [Intra-UIAbility and Inter-UIAbility Page Redirection (ArkTS, API version 9)](https://gitcode.com/openharmony/codelabs/tree/master/Ability/StageAbility)
- [Intra-UIAbility Page Redirection (ArkTS, API version 9)](https://gitcode.com/openharmony/codelabs/tree/master/Ability/PagesRouter)
