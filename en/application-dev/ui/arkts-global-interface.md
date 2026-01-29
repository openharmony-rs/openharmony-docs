# Using the UI Context API for UI Operations (UIContext)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

This document describes the concepts related to multiple UI instances, the reasons for replacing global APIs with [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md) APIs, and the corresponding replacement solutions.

## Concepts

UI instance: An object used to manage UI functions, such as components, layouts, animations, and interaction events. Each window object creates and manages a UI instance.

UI context: An abstract concept of the running environment of a UI instance. UI functions run in the UI context, and the effect is finally reflected in the corresponding UI instance.

Global APIs: A series of global APIs provided by ArkUI. These APIs do not need to explicitly specify UI instances or components when they are called. They automatically apply to the corresponding UI instance based on the UI context where the call occurs.

## Ambiguous UI Context

Ambiguous UI context refers to the issue where the calling point cannot clearly identify the target UI instance when invoking ArkUI global APIs.

Currently, the system supports two application models: FA model and stage model. For details, see [Application Models](../application-models/application-models.md). In the FA model, each UI instance has an independent ArkTS engine. The global APIs can be traced to the corresponding UI instance through the ArkTS engine. Therefore, the UI context is clear.
In the stage model, multiple ArkUI instances can run in an ArkTS engine. The global APIs determine the current UI context by analyzing the context information in the call chain. The asynchronous APIs and non-UI APIs may cause UI context tracing failures.

To ensure that the functions of global APIs are normal, you need to replace global APIs with UIContext APIs.

**Figure 1** Multi-instance relationship

![multi-instance](figures/multi-instance.png)

## Replacing global APIs with UIContext APIs

The table below lists some of the alternative APIs to replace in multi-instance scenarios. The full range of APIs supported is described in [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md).

In the sample code, [isAvailable](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#isavailable20) takes effect from API version 20, and other APIs take effect from API version 18.

|               Global API               |               Substitute API               |            Description           |
| :-----------------------------------: | :-----------------------------------: | :------------------------: |
|            @ohos.animator             |            createAnimator             |      Custom animation controller.     |
|     @ohos.arkui.componentSnapshot     |         getComponentSnapshot          |          Component snapshot.         |
|      @ohos.arkui.componentUtils       |           getComponentUtils           |         Component utility class.        |
|      @ohos.arkui.dragController       |           getDragController           |         Drag controller.        |
|         @ohos.arkui.inspector         |            getUIInspector             |        Component layout callback.       |
|         @ohos.arkui.observer          |             getUIObserver             |          Observer.         |
|              @ohos.font               |                getFont                |         Custom font registration.        |
|             @ohos.measure             |            getMeasureUtil             |          Text measurement.         |
|           @ohos.mediaquery            |             getMediaQuery             |          Media query.         |
|          @ohos.promptAction           |            getPromptAction            |            Popup.           |
|             @ohos.router              |               getRouter               |          Page routing.         |
|              AlertDialog              |            showAlertDialog            |          Alert dialog box.         |
|              ActionSheet              |            showActionSheet            |        Action sheet.       |
|         CalendarPickerDialog          |                Not supported                |       Calendar picker dialog box.      |
|           DatePickerDialog            |         showDatePickerDialog          |      Date picker dialog box.     |
|           TimePickerDialog            |         showTimePickerDialog          |     Time picker dialog box.    |
|           TextPickerDialog            |         showTextPickerDialog          |     Text picker dialog box.    |
|              ContextMenu              |       getContextMenuController        |          Menu control.         |
| vp2px/px2vp/fp2px/px2fp/lpx2px/px2lpx | vp2px/px2vp/fp2px/px2fp/lpx2px/px2lpx |        Pixel unit conversion.       |
|             focusControl              |            getFocusControl            |          Focus control.         |
|             cursorControl             |           getCursorControl            |          Cursor control.         |
|              getContext               |            getHostContext             | Obtains the context of the current ability.|
|        LocalStorage.getShared         |         getSharedLocalStorage         |  Obtains the storage passed by the current ability. |
|               animateTo               |               animateTo               |          Explicit animation.         |
|         animateToImmediately          |                Not supported                |        Explicit instant animation.       |

## Replacing Global APIs with Common UIContext APIs

The following uses the **Pixel unit** (in ./ui-js-custom-components.md) as an example to describe how to replace global APIs with common UIContext APIs.

### Obtaining UIContext Object Through a Custom Component

When a global API is in another scope such as a member method or component lifecycle method of a custom component ([getUIContext](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext)), and this points to the custom component, you can call the [getUIContext](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext) member method of the custom component to obtain the UIContext object.

>**NOTE**
> 1. If you use getUIContext in the callback method of asynchronous calling, or the start calling of this API is not on the current page, the API may be called after the custom component is destroyed. As a result, undefined is returned.
> 2. This method can be invoked only through this and cannot be invoked through the custom component object created using the new keyword.
> 3. The UIContext obtained through the custom node created in the [custom declarative node (BuilderNode)](./arkts-user-defined-arktsNode-builderNode.md) points to the same UI instance as the UIContext created by BuilderNode.

Use the global API:
<!--deprecated_code_no_check-->

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text('Calculate 20vp to px')
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let pxValue = vp2px(20);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

Use the UIContext API instead:
```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text('Calculate 20vp to px')
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let uiContext = this.getUIContext();
          let pxValue = uiContext.vp2px(20);
          hilog.info(DOMAIN, 'testTag', `20vp equals to ${pxValue}px`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Obtaining the UIContext Object Through the Window Object

You can use the [getUIContext](../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10) method of the window object to obtain the UIContext object.

>**NOTE**
>
>1. The UIContext can be obtained through the getUIContext method of the window object only after the UI instance is created. You are advised to call this method in the success callback of loadContent to ensure that the UI instance is ready.
>2. When the UI instance is not created, the default value of vp2px/px2vp is obtained for calculation. During replacement, the logical pixel density of the current default [Display](../reference/apis-arkui/js-apis-display.md#display) object can be obtained for calculation. For details, see [Replacing Pixel Unit Conversion APIs with UIContext APIs](#replacing-pixel-unit-conversion-apis-with-uicontext-apis).

Using a global interface:
<!--deprecated_code_no_check-->

```ts
import { AbilityConstant, ConfigurationConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    // When this API is called before loadContent, vp2px returns the calculation result based on the default pixel density of the screen.
    let pxValue = vp2px(20);
    hilog.info(DOMAIN, 'testTag', `20vp equals to ${pxValue}px`);
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(DOMAIN, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      // This API needs to be called in the callback.
      let pxValue = vp2px(20);
      hilog.info(DOMAIN, 'testTag', `20vp equals to ${pxValue}px`);
    });
    // loadContent is an asynchronous API. Calling this API here cannot ensure that the UI instance has been created.
    pxValue = vp2px(20);
    hilog.info(DOMAIN, 'testTag', `20vp equals to ${pxValue}px`);
  }

  // ...
}
```
Use the UIContext API instead:
```ts
import { AbilityConstant, ConfigurationConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let window = windowStage.getMainWindowSync();
    // When getUIContext is called before loadContent, the UI instance is not created, and an exception occurs.
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(DOMAIN, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      // This callback needs to be called in the callback.
      try {
        let uiContext = window.getUIContext();
        if (!uiContext) {
          hilog.error(DOMAIN, 'testTag', `Can't get UIContext`);
          return;
        }
        let pxValue = uiContext.vp2px(20);
        hilog.info(DOMAIN, 'testTag', `20vp equals to ${pxValue}px`);
      } catch(e) {
        hilog.error(DOMAIN, 'testTag', `Can't get UIContext, ${e}`);
      }
    });
    // loadContent is an asynchronous API. Calling this API here cannot ensure that the UI instance has been created.
  }

  onWindowStageDestroy(): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
    // Remove the invalid UIContext when the window is destroyed.
    PixelUtils.removeUIContext();
  }

  // ...
}
```

### Obtaining the UI Context Object in the Encapsulated API

Developers usually use global APIs in encapsulated APIs. In this scenario, you are advised to add input parameters of the UIContext type. If an application has only one window, you can use the global storage object to save the UIContext.

>**NOTE**
>1. The UI instance creation is an asynchronous process. You need to call the getUIContext method of the window object in the callback to obtain the UIContext object.
>2. You are advised to add optional input parameters of the UIContext type so that the caller can pass the UIContext.
>3. When the UI instance is not created, vp2px/px2vp obtains the default value for calculation. You can obtain the logical pixel density of the default display object for calculation. For details, see [Replacing Pixel Unit Conversion APIs with UIContext APIs](#replacing-pixel-unit-conversion-apis-with-uicontext-apis).

Use the global interface:
<!--deprecated_code_no_check-->

```ts
class PixelUtils {
  static vp2px(vpValue: number) : number {
    return vp2px(vpValue);
  }

  static fp2px(fpValue: number) : number | undefined {
    return fp2px(fpValue);
  }

  static lpx2px(lpxValue: number) : number | undefined {
    return lpx2px(lpxValue);
  }
}
```

Use the UIContext interface:
```ts
// common/Utils.ets
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

export class PixelUtils {
  static uiContext : UIContext | undefined;
  static setUIContext(uiContext : UIContext): void {
    PixelUtils.uiContext = uiContext;
  }

  static removeUIContext(): void {
    PixelUtils.uiContext = undefined;
  }

  static vp2px(vpValue: number, uiContext?: UIContext): number | undefined {
    let _uiContext = uiContext??PixelUtils.uiContext;
    if (!_uiContext || !_uiContext.isAvailable()) {
      hilog.error(DOMAIN, 'testTag', `Can't get UIContext`);
      return undefined;
    }
    return _uiContext.vp2px(vpValue)
  }

  static fp2px(fpValue: number, uiContext?: UIContext): number | undefined {
    let _uiContext = uiContext??PixelUtils.uiContext;
    if (!_uiContext || !_uiContext.isAvailable()) {
      hilog.error(DOMAIN, 'testTag', `Can't get UIContext`);
      return undefined;
    }
    return _uiContext.fp2px(fpValue)
  }

  lpx2px(lpxValue: number, uiContext?: UIContext): number | undefined {
    let _uiContext = uiContext??PixelUtils.uiContext;
    if (!_uiContext || !_uiContext.isAvailable()) {
      hilog.error(DOMAIN, 'testTag', `Can't get UIContext`);
      return undefined;
    }
    return _uiContext.lpx2px(lpxValue)
  }
}
```
```ts
// entryability/EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';
import { PixelUtils } from '../common/Utils';

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let window = windowStage.getMainWindowSync();
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(DOMAIN, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      // This callback needs to be called in the callback.
      try {
        let uiContext = window.getUIContext();
        PixelUtils.setUIContext(uiContext);
      } catch(e) {
        hilog.error(DOMAIN, 'testTag', `Can't get UIContext, ${e}`);
      }
    });
  }

  onWindowStageDestroy(): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
    // Remove the invalid UIContext when the window is destroyed.
    PixelUtils.removeUIContext();
  }
  // ...
}
```

When using the encapsulated replacement API, you are advised to pass the UIContext parameter when the UIContext can be obtained.
```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import { PixelUtils } from '../common/Utils';

const DOMAIN = 0x0000;

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text('Calculate 20vp to px')
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let pxValue = PixelUtils.vp2px(20, this.getUIContext());
          hilog.info(DOMAIN, 'testTag', `20vp equals to ${pxValue}px`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
If the UIContext cannot be obtained, you can directly call this method.
```ts
let pxValue = PixelUtils.vp2px(20);
hilog.info(DOMAIN, 'testTag', `20vp equals to ${pxValue}px`);
```


### Obtaining the UIContext Object Through the Window That Recently Gains Focus

If an app has multiple windows and the UIContext cannot be directly obtained, you can obtain the UIContext through the window that recently gains focus.

>**NOTE**
> 1. This solution traces the window that recently gains focus. When a specific function is called, the window may be out of focus.
> 2. When creating a window, you need to call registerWindowCallback to register a callback.

Replace the UIContext interface with the following:
```ts
// common/WindowUtils.ets
import { display, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

export class WindowUIContextUtils {
  static activeUIContext : UIContext | undefined;

  static registerWindowCallback(windowClass: window.Window) : void {
    try {
      windowClass.on('windowEvent', (event: window.WindowEventType) => {
        if (event === window.WindowEventType.WINDOW_ACTIVE) {
          try {
            let uiContext = windowClass.getUIContext();
            WindowUIContextUtils.activeUIContext = uiContext;
          } catch(exception) {
            hilog.error(DOMAIN, 'testTag', `Can't get UIContext, ${exception}`);
          }
        }
      });
    } catch (exception) {
      console.error(`Failed to unregister callback. Cause: ${exception}`);
    }
  }

  static unregisterWindowCallback(windowClass: window.Window): void {
    windowClass.off('windowEvent');
  }

  static setActiveUIContext(uiContext: UIContext) : void {
    WindowUIContextUtils.activeUIContext = uiContext;
  }

  static vp2px(vpValue: number, uiContext?: UIContext): number {
    let _uiContext = uiContext??WindowUIContextUtils.activeUIContext;
    if (!_uiContext || !_uiContext.isAvailable()) {
      let displayClass = display.getDefaultDisplaySync();
      let density = displayClass.densityPixels;
      return vpValue * density;
    }

    return _uiContext.vp2px(vpValue);
  }
}
```
```ts
// entryability/EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';
import { WindowUIContextUtils } from '../common/WindowUtils';

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let window = windowStage.getMainWindowSync();
    // Register the callback for the main window.
    WindowUIContextUtils.registerWindowCallback(window);
    windowStage.loadContent('pages/WindowTestPage', (err) => {
      // The UI context needs to be obtained after loadContent is complete.
      if (err.code) {
        hilog.error(DOMAIN, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      try {
        let uiContext = window.getUIContext();
        // The main window may be focused before loadContent is complete. Therefore, the main window needs to be set to ensure that the main window is valid after the main window is focused.
        WindowUIContextUtils.setActiveUIContext(uiContext)
      } catch(exception) {
        hilog.error(DOMAIN, 'testTag', 'Failed to getUIContext in loadContent. Cause: %{public}s', JSON.stringify(exception));
      }
    });
  }

  onWindowStageWillDestroy(windowStage: window.WindowStage) {
    let window = windowStage.getMainWindowSync();
    hilog.info(DOMAIN, 'testTag', '%{public}s', `The main window: ${window}`);
    // Unregister the callback of the main window.
    WindowUIContextUtils.unregisterWindowCallback(window);
  }

  // ...
}
```
```ts
// pages/WindowTestPage.ets
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { WindowUIContextUtils } from '../common/WindowUtils';

const DOMAIN = 0x0000;

@Entry
@Component
struct Index {
  private subWindow : window.Window | undefined;

  build() {
    Column() {
      Text('Create SubWindow')
        .onClick(() => {
          let config: window.Configuration = {
            name: "test",
            windowType: window.WindowType.TYPE_DIALOG,
            ctx: this.getUIContext().getHostContext()
          };
          try {
            window.createWindow(config, (err: BusinessError, windowClass: window.Window) => {
              const errCode: number = err.code;
              if (errCode) {
                hilog.error(DOMAIN, 'testTag', `Failed to create the window. Cause: ${errCode}`);
                return;
              }
              // Register the callback after the window is created.
              this.subWindow = windowClass;
              try {
                windowClass.setUIContent('pages/Index', () => {
                  WindowUIContextUtils.registerWindowCallback(windowClass);
                  windowClass.resize(500, 1000);
                  windowClass.showWindow();
                });
              } catch(exception) {
                hilog.error(DOMAIN, 'testTag', `Failed to setUIContent. Cause : ${exception}`);
              }
            });
          } catch (exception) {
            hilog.error(DOMAIN, 'testTag', `Failed to create the window. Cause : ${exception}`);
          }
        })
      Text('Destroy SubWindow')
        .onClick(() => {
          if (this.subWindow) {
            // Unregister the callback before the window is destroyed.
            WindowUIContextUtils.unregisterWindowCallback(this.subWindow);
            this.subWindow.destroyWindow();
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Executing the Closure Bound to the UI Instance

If the UIContext does not provide an alternative API (for example, CalendarPickerDialog) or the service behavior implemented by the developer is related to multiple instances and needs to be bound to the instance (for example, a code segment), you can use the [runScopedTask](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#runscopedtask) method of the UIContext object to execute the closure.

Replace the UIContext API:

```ts
@Entry
@Component
struct CalendarPickerDialogPage {
  private selectedDate: Date = new Date('2025-10-01');

  build() {
    RelativeContainer() {
      Button('Show CalendarPicker Dialog')
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let uiContext = this.getUIContext();
          uiContext.runScopedTask(() => {
            CalendarPickerDialog.show({
              selected: this.selectedDate,
              backgroundColor: Color.White,
              backgroundBlurStyle: BlurStyle.NONE,
              shadow: ShadowStyle.OUTER_FLOATING_SM
            });
          });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```



## Replacing Special Global APIs

When replacing some global APIs with UIContext APIs, you need to consider some special calling scenarios.

### Replacing Pixel Unit Conversion APIs with UIContext APIs

Different UI instances can have different conversion coefficients. The calculation results of [pixel unit conversion APIs](../reference/apis-arkui/arkui-ts/ts-pixel-units.md) depend on the specific UI instance. The fp2px, px2fp, lpx2px, and px2lpx APIs return undefined when there is no valid UI context. The vp2px and px2vp APIs obtain the default screen pixel density for calculation when there is no valid UI context.

| Calling time of the pixel unit conversion API                                    | API Behavior                                                    | Possible Scenario Where the Result Is Not as Expected                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Before the main window is created and loadContent or setUIContent is called               | No proper UI instance is available.<br>The px2vp and vp2px APIs use the density of the default screen for conversion and return the result.<br>The fp2px, px2fp, lpx2px, and px2lpx APIs return undefined.| The px2vp and vp2px APIs may not work as expected in multi-screen scenarios. For example, the result is calculated based on the logical pixel density of the extended screen instead of the main screen.|
| After loadContent or setUIContent is called, and in the UI callback function         | Find the specific UI instance based on the calling scope traced by the UI, and use the information associated with the UI instance for calculation.| None                                                          |
| In the single-ability single-window scenario of an application, the API is called after loadContent or setUIContent is called, but in a non-UI asynchronous callback.| The specific UI instance cannot be found based on the calling scope traced by the UI, but the unique UI instance can be determined based on the current singleton scenario. The information associated with the UI instance is used for calculation.| None                                                          |
| In the multi-ability or multi-window multi-UI instance scenario, the API is called after loadContent or setUIContent is called, but in another asynchronous callback.| The specific UI instance cannot be found based on the calling scope traced by the UI, and the unique instance cannot be determined. The API searches for the matched UI instance based on the priorities of the latest focus, latest foreground, and latest creation, and performs calculation based on the information associated with the UI instance.| In the multi-instance scenario, the function instance may be inconsistent with the expected one. For example, the result is calculated based on the pixel density of the screen where the child window is located instead of the logical pixel density of the screen where the main window is located.|
| After all windows are destroyed and no UI instance is available                                | No proper UI instance is available.<br>The px2vp and vp2px APIs use the density of the default screen for conversion and return the result.<br>The fp2px, px2fp, lpx2px, and px2lpx APIs return undefined.| The px2vp and vp2px APIs may not work as expected in multi-screen scenarios. For example, the result is calculated based on the pixel density of the main screen instead of the logical pixel density of the extended screen.|

In actual development scenarios, global APIs may be called before UI instances are created. When replacing vp2px/px2vp, you can use [display.getDefaultDisplaySync](../reference/apis-arkui/js-apis-display.md#displaygetdefaultdisplaysync9) to obtain the logical pixel density calculation result of the current default screen. When replacing fp2px/px2fp/lpx2px/px2lpx, you can directly return undefined to ensure consistent behavior.

Use the global API:
<!--deprecated_code_no_check-->

```ts
export class PixelUtils {
  static vp2px(vpValue: number) : number {
    return vp2px(vpValue);
  }

  static fp2px(fpValue: number) : number | undefined {
    return fp2px(fpValue);
  }

  static lpx2px(lpxValue: number) : number | undefined {
    return lpx2px(lpxValue);
  }
}
```

Use the UIContext interface:
```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import { display } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export class PixelUtils {
  static uiContext : UIContext | undefined;
  static setUIContext(uiContext : UIContext) : void {
    PixelUtils.uiContext = uiContext;
  }

  static removeUIContext(): void {
    PixelUtils.uiContext = undefined;
  }

 static vp2px(vpValue: number, uiContext?: UIContext): number | undefined {
   let _uiContext = uiContext??PixelUtils.uiContext;
    if (!_uiContext || !_uiContext.isAvailable()) {
      let displayClass = display.getDefaultDisplaySync();
      let density = displayClass.densityPixels;
      return vpValue * density;
    }
    return _uiContext.vp2px(vpValue)
  }

  static fp2px(fpValue: number, uiContext?: UIContext): number | undefined {
    let _uiContext = uiContext??PixelUtils.uiContext;
    if (!_uiContext || !_uiContext.isAvailable()) {
      hilog.error(DOMAIN, 'testTag', `Can't get UIContext`);
      return undefined;
    }
    return _uiContext.fp2px(fpValue)
  }

  lpx2px(lpxValue: number, uiContext?: UIContext): number | undefined {
    let _uiContext = uiContext??PixelUtils.uiContext;
    if (!_uiContext || !_uiContext.isAvailable()) {
      hilog.error(DOMAIN, 'testTag', `Can't get UIContext`);
      return undefined;
    }
    return _uiContext.lpx2px(lpxValue)
  }
}
```

### Obtaining the Context of an Ability

The [getContext] (../reference/apis-arkui/js-apis-getContext.md) API is used to obtain the context of the ability to which the corresponding UI instance belongs on the UI page. Therefore, this API depends on the UI instance.

| getContext API Calling Time                                    | API Behavior                                                    | Possible Scenario Where the Result Is Not as Expected                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Before the main window is created and loadContent or setUIContent is called.               | If no proper UI instance is available, undefined is returned.                           | None                                                          |
| After the main window is created and loadContent or setUIContent is called, and a custom component object is passed.| The context of the ability to which the UI instance to which the custom component belongs is returned.| None                                                          |
| After loadContent or setUIContent is called, and in the UI callback function.         | The context of the ability to which the UI instance is returned based on the UI tracing scope.| None                                                          |
| In the single-ability single-window scenario of an application, after loadContent or setUIContent is called, and in the asynchronous callback of a non-UI component, and no custom component object is passed.| The context of the ability to which the UI instance is returned based on the UI tracing scope. If the UI instance cannot be found based on the UI tracing scope, the context of the ability to which the unique UI instance belongs is returned based on the current singleton scenario.| None                                                          |
| In the multi-ability or multi-window scenario with multiple UI instances, after loadContent or setUIContent is called, and in the asynchronous callback, and no custom component object is passed.| The context of the ability to which the UI instance is returned based on the UI tracing scope. If the UI instance cannot be found based on the UI tracing scope, the context of the ability to which the unique UI instance belongs cannot be determined. The API searches for the matched UI instance based on the following priorities: latest focused UI instance, latest foreground UI instance, and latest created UI instance. The context of the ability to which the UI instance belongs is returned.| The result may be different from the expected result in the multi-instance scenario. For example, if there are two abilities, the context of the first created ability is expected to be returned, but the context of the second created ability is actually returned.|
| After all windows are destroyed and no UI instance is available.                                | If no proper UI instance is available, undefined is returned.                           | None                                                        |

In the single-ability scenario, you are advised to directly obtain the context attribute of the ability.

Global API:

<!--deprecated_code_no_check-->

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

@Entry
@Component
struct GetContextPage {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          // Ensure that the input is a custom component object.
          let context = getContext(this);
          hilog.info(DOMAIN, 'testTag', `The context is ${context}`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```



Use the UIContext API instead:

```ts
// common/ContextUtils.ets
export class ContextUtils {
  static context: Context | undefined;

  static setContext(context: Context): void {
    ContextUtils.context = context;
  }

  static removeContext(): void {
    ContextUtils.context = undefined;
  }

  static getContext(uiContext?: UIContext): Context | undefined {
    if (uiContext) {
      return uiContext.getHostContext();
    }

    return ContextUtils.context;
  }
}
```

The default return value of the API is set to the member attribute context of the ability.

```ts
// entryAbility/EntryAbility.ets
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { ContextUtils } from '../common/ContextUtils';

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onCreate');
    ContextUtils.setContext(this.context);
  }

  onDestroy(): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onDestroy');
    ContextUtils.removeContext();
  }

  // ...
}
```

You are advised to pass UIContext on the UI to ensure that the operation meets the expectation or directly call getHostContext.

```ts
import { ContextUtils } from '../common/ContextUtils';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

@Entry
@Component
struct ContextPage {
  build() {
    Column() {
      Text('getContext')
        .onClick(() => {
          let context = ContextUtils.getContext(this.getUIContext());
          hilog.info(DOMAIN, 'testTag', `The context is ${context}`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

In the non-UI scenario, the default return value set during window creation is returned.

```ts
let context = ContextUtils.getContext();
hilog.info(DOMAIN, 'testTag', `The context is ${context}`);
```



### Replacing LocalStorage with UIContext

LocalStorage is the page-level UI state storage. Parameters received through the @Entry decorator can share the same LocalStorage instance on a page. When using the global API, you can use [getShared](../reference/apis-arkui/arkui-ts/ts-state-management.md#getshareddeprecated) to pass the LocalStorage object to the @Entry decorator. After using the UIContext API, you cannot directly obtain the UIContext object. You can set the useSharedStorage parameter of [EntryOptions](../reference/apis-arkui/arkui-ts/ts-universal-entry.md#entryoptions10) to true to use the shared LocalStorage instance object.

Use the global API:

<!--deprecated_code_no_check-->

```ts
// pages/LocalStoragePage
@Entry({storage: LocalStorage.getShared()})
@Component
struct LocalStoragePage {
  @LocalStorageLink('message') message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('LocalStoragePageHelloWorld')
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let storage = LocalStorage.getShared();
          if (storage) {
            storage.setOrCreate('message', 'onClick is called.')
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

Use the UIContext API instead:

```ts
// pages/LocalStoragePage
@Entry({useSharedStorage: true})
@Component
struct LocalStoragePage {
  @LocalStorageLink('message') message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('LocalStoragePageHelloWorld')
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let uiContext = this.getUIContext();
          let storage = uiContext.getSharedLocalStorage();
          if (storage) {
            storage.setOrCreate('message', 'onClick is called.')
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

To use the shared LocalStorage object, you need to pass the LocalStorage object when loading content. For details, see [LocalStorage: Page-Level UI State Storage](./state-management/arkts-localstorage.md).

```ts
import { AbilityConstant, UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let localStorage = new LocalStorage();
    localStorage.setOrCreate('message', 'Message from Storage')
    windowStage.loadContent('pages/LocalStoragePage', localStorage, (err) => {
      if (err.code) {
        hilog.error(DOMAIN, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      hilog.info(DOMAIN, 'testTag', `loadContent success.`);
    });
  }

  // ...
}
```
