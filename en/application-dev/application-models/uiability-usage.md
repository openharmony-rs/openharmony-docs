# UIAbility Usage


When using the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) component, you must specify a startup page and obtain the context, [UIAbilityContext](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md).


## Specifying the Startup Page of UIAbility

If no startup page is specified, a white screen occurs after the application is started. You can use [loadContent()](../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9) of [WindowStage](../reference/apis-arkui/arkts-apis-window-WindowStage.md) to set the startup page in the [onWindowStageCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate) callback of the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) instance.


```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created. Set a main page for this ability.
    windowStage.loadContent('pages/Index', (err, data) => {
      // ...
    });
  }
  // ...
}
```

> **NOTE**
>
> When you create UIAbility in DevEco Studio, the UIAbility instance loads the **Index** page as its startup page. Therefore, you only need to replace the **Index** page path with the required startup page path.


## Obtaining the Context of UIAbility

The [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) class has its own context, which is an instance of the [UIAbilityContext](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) class. The [UIAbilityContext](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) class has attributes such as **abilityInfo** and **currentHapModuleInfo**. UIAbilityContext can be used to obtain the UIAbility configuration information, such as the code path, bundle name, ability name, and environment status required by the application. It can also be used to obtain methods to operate the UIAbility instance, such as [startAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability), [connectServiceExtensionAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability), and [terminateSelf()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself).

The [getHostContext](../reference/apis-arkui/js-apis-arkui-UIContext.md#gethostcontext12) API enables you to obtain the context of the ability (either UIAbilityContext or [ExtensionContext](../reference/apis-ability-kit/js-apis-inner-application-extensionContext.md)) on the current page.

- You can use **this.context** to obtain the context of a UIAbility instance.
  
  ```ts
  import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';

  export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
      // Obtain the context of the UIAbility instance.
      let context = this.context;
      // ...
    }
  }
  ```
  
- Import the context module and define the **context** variable in the component.
  
  ```ts
  import { common, Want } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Page_EventHub {
    private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

    startAbilityTest(): void {
      let want: Want = {
        // Want parameter information.
      };
      this.context.startAbility(want);
    }

    // Page display.
    build() {
      // ...
    }
  }
  ```

  You can also define variables after importing the context module but before using [UIAbilityContext](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md).

  
  ```ts
  import { common, Want } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Page_UIAbilityComponentsBasicUsage {
    startAbilityTest(): void {
      let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      let want: Want = {
        // Want parameter information.
      };
      context.startAbility(want);
    }

    // Page display.
    build() {
      // ...
    }
  }
  ```

- To stop the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) instance after the service is not needed, call [terminateSelf()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself).

  ```ts
  import { common } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  @Entry
  @Component
  struct Page_UIAbilityComponentsBasicUsage {
    // Page display.
    build() {
      Column() {
        //...
        Button('FuncAbilityB')
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            try {
              context.terminateSelf((err: BusinessError) => {
                if (err.code) {
                  // Process service logic errors.
                  console.error(`terminateSelf failed, code is ${err.code}, message is ${err.message}.`);
                  return;
                }
                // Carry out normal service processing.
                console.info(`terminateSelf succeed.`);
              });
            } catch (err) {
              // Capture the synchronization parameter error.
              let code = (err as BusinessError).code;
              let message = (err as BusinessError).message;
              console.error(`terminateSelf failed, code is ${code}, message is ${message}.`);
            }
          })
      }
    }
  }
  ```


## Obtaining Information About the UIAbility Launcher

When the launcher ability (UIAbilityA) starts the target ability (UIAbilityB) using **startAbility**, UIAbilityB can obtain information about UIAbilityA, such as its PID, bundle name, and ability name, through the [parameters](../reference/apis-ability-kit/js-apis-app-ability-want.md) parameter.


1. Tap the **Start UIAbilityB** button in UIAbilityA to start UIAbilityB.

    ```ts
    import { common, Want } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';

    @Entry
    @Component
    struct Index {
      @State message: string = 'Hello World';
      @State context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;

      build() {
        Scroll() {
          Column() {
            Text(this.message)
              .id('HelloWorld')
              .fontSize(50)
              .fontWeight(FontWeight.Bold)
              .alignRules({
                center: { anchor: '__container__', align: VerticalAlign.Center },
                middle: { anchor: '__container__', align: HorizontalAlign.Center }
              })
              .onClick(() => {
                this.message = 'Welcome';
              })
            Button('terminateSelf').onClick(() => {
              this.context.terminateSelf()
            })

            Button('Start UIAbilityB').onClick((event: ClickEvent) => {
              let want: Want = {
                bundleName: this.context.abilityInfo.bundleName,
                abilityName: 'UIAbilityB',
              }

              this.context.startAbility(want, (err: BusinessError) => {
                if (err.code) {
                  console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}.`);
                }
              });
            })
          }
        }
      }
    }
    ```

2. In the [onCreate](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate) lifecycle of UIAbilityB, obtain and print the PID, bundle name, and ability name of UIAbilityA.

    ```ts
    import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
    import { window } from '@kit.ArkUI';

    export default class UIAbilityB extends UIAbility {
      onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // The caller does not need to manually pass parameters. The system automatically passes the caller's information to the Want object.
        console.log(`onCreate, callerPid: ${want.parameters?.['ohos.aafwk.param.callerPid']}.`);
        console.log(`onCreate, callerBundleName: ${want.parameters?.['ohos.aafwk.param.callerBundleName']}.`);
        console.log(`onCreate, callerAbilityName: ${want.parameters?.['ohos.aafwk.param.callerAbilityName']}.`);
      }

      onDestroy(): void {
        console.log(`UIAbilityB onDestroy.`);
      }

      onWindowStageCreate(windowStage: window.WindowStage): void {
        console.log(`Ability onWindowStageCreate.`);

        windowStage.loadContent('pages/Index', (err) => {
          if (err.code) {
            console.error(`Failed to load the content, error code: ${err.code}, error msg: ${err.message}.`);
            return;
          }
          console.log(`Succeeded in loading the content.`);
        });
      }
    }
    ```
