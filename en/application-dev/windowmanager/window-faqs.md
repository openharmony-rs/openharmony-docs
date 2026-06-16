# Window Development FAQs
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## How to Launch Application B During the Startup of Application A

**Solution**

Application A can call the [on('windowStageEvent')](../reference/apis-arkui/arkts-apis-window-WindowStage.md#onwindowstageevent9) API to listen for the [WindowStageEvent.ACTIVE](../reference/apis-arkui/arkts-apis-window-e.md#windowstageeventtype9) event and then call the [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) API to launch application B.

**Code Example**

```ts
// applicationA EntryAbility.ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, StartOptions } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage): void {
        let want: Want = {
            deviceId: '',
            bundleName: 'com.example.applicationB',
            abilityName: 'EntryAbility'
        };

        let options: StartOptions = {
            displayId: 0
        };

        windowStage.on('windowStageEvent', (data) => {
            let eventType: window.WindowStageEventType = data;
            // Listen for Application A switching to the ACTIVE state.
            if (eventType === window.WindowStageEventType.ACTIVE) {
                try {
                    // Launch application B.
                    this.context.startAbility(want, options, (err: BusinessError) => {
                        if (err.code) {
                            // Handle service logic errors.
                            console.error(`Failed to start ability, code is ${err.code}, message is ${err.message}.`);
                            return;
                        }
                        // Carry out normal service processing.
                        console.info('Succeeded in starting Ability.');
                    });
                } catch (err) {
                    // Handle input parameter errors.
                    let code = (err as BusinessError).code;
                    let message = (err as BusinessError).message;
                    console.error(`Failed to start ability, code is ${code}, message is ${message}.`);
                }
            }
        });
    }
}
```

## How to Dynamically Obtain the Window Width and Height

In application development, dynamically obtaining the window width and height is mainly used to implement responsive layout to adapt to devices of different sizes or window status changes (such as split-screen, maximization, restoration, and drag resizing).

You are advised to use [getMainWindowSync()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#getmainwindowsync9), [getMainWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#getmainwindow9-1), or [getSubWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#getsubwindow9-1) to obtain the window instance (windowClass), and then call the [getWindowProperties()](../reference/apis-arkui//arkts-apis-window-Window.md#getwindowproperties9) API through the instance to obtain the **WindowProperties** attribute. You can obtain the window width and height based on the attribute. The sample code snippet is as follows:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window = windowStage.getMainWindowSync(); // Obtain the main window of the application.
    if (!windowClass) {
      console.info('windowClass is null');
    }
    try {
      let properties = windowClass.getWindowProperties();
      let rect = properties.windowRect;
      let windowWidth = rect.width;  // Window width, in px.
      let windowHeight = rect.height; // Window height, in px.
      console.info(`Window Size: ${windowWidth} x ${windowHeight}`);
    } catch (exception) {
      console.error('Failed to obtain the window properties. Cause: ' + JSON.stringify(exception));
    }
  }
}
```


## How to Listen for Soft Keyboard Height Changes

The fixed soft keyboard is a specific type of avoid area, which corresponds to the **TYPE_KEYBOARD** type in [AvoidAreaType](../reference/apis-arkui/arkts-apis-window-e.md#avoidareatype7). You can use [getWindowAvoidArea()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowavoidarea9) and [on('avoidAreaChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onavoidareachange9) to dynamically listen for changes in the soft keyboard avoid area height.

You can also use the [on('keyboardHeightChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onkeyboardheightchange7) API to listen for changes in the soft keyboard height. Unlike the avoid area, the callback of this API returns only the height (number) of the soft keyboard, while the [on('avoidAreaChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onavoidareachange9) callback returns the entire soft keyboard area ([Rect](../reference/apis-arkui/arkts-apis-window-i.md#rect7)).

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    // Obtain the main window.
    let windowClass: window.Window = windowStage.getMainWindowSync();
    if (!windowClass) {
      console.info('windowClass is null');
    }
    try {
      // Obtain the height of the soft keyboard avoid area.
      let keyboardHeight = windowClass.getWindowAvoidArea(window.AvoidAreaType.TYPE_KEYBOARD).bottomRect.height;
      // Dynamically listen for changes in the soft keyboard avoid area height.
      windowClass.on('avoidAreaChange', (data) => {
        if (data.type == window.AvoidAreaType.TYPE_KEYBOARD) {
          keyboardHeight = data.area.bottomRect.height;
        }
      });
    } catch (exception) {
      console.error(`Failed to enable the listener for system avoid area changes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```


## How to Obtain the Height of the PC's Default System Title Bar

Call [getWindowDecorHeight()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowdecorheight11) to obtain the height of the title bar.

The example code is as follows:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    // Obtain the main window.
    let windowClass: window.Window = windowStage.getMainWindowSync();
    if (!windowClass) {
      console.info('windowClass is null');
    }
    windowClass.setUIContent('pages/WindowPage').then(() => {
      try {
        let height = windowClass?.getWindowDecorHeight();
        console.info(`Succeeded in getting the height of window decor: ${height}`);
      } catch (exception) {
        console.error(`Failed to get the height of window decor. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    })
  }
}
```


## How to Implement or Determine Immersive Window Layout

An [immersive layout](window-terminology.md#immersive-layout) is a window state that helps an application UI focus on content by reducing distractions from irrelevant elements.

For a non-[freeform window](window-terminology.md#freeform-window), immersive layout can be set by calling [setWindowLayoutFullScreen()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowlayoutfullscreen9). For a freeform window, you can call [setWindowDecorVisible()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowdecorvisible11) to control the title bar visibility. When the title bar is hidden, the window is in immersive layout.

You can use [isImmersiveLayout()](../reference/apis-arkui/arkts-apis-window-Window.md#isimmersivelayout20) to check whether the window is in immersive layout.

The example code is as follows:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    // Obtain the main window.
    let windowClass: window.Window = windowStage.getMainWindowSync(); 
    if (!windowClass) {
      console.info('windowClass is null');
    }
    try {
      // Set the immersive layout.
      let promise = windowClass.setWindowLayoutFullScreen(true); 
      // Check whether the current window is in immersive layout.
      let isImmersiveLayout = windowClass.isImmersiveLayout();
      console.info(`isImmersiveLayout: ${isImmersiveLayout}`);
    } catch (exception) {
      console.error('Failed to obtain isImmersiveLayout. Cause: ' + JSON.stringify(exception));
    }
  }
}
```


## How to Hide the Status Bar and Bottom Navigation Area

Call [setSpecificSystemBarEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setspecificsystembarenabled11) to hide the status bar and bottom navigation bar.

The example code is as follows:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    // Obtain the main window.
    let windowClass: window.Window = windowStage.getMainWindowSync();
    if (!windowClass) {
      console.info('windowClass is null');
    }
    try {
      // Hide the status bar.
      windowClass.setSpecificSystemBarEnabled('status', false);
      // Hide the bottom navigation area.
      windowClass.setSpecificSystemBarEnabled('navigationIndicator', false);
    } catch (exception) {
      console.error('Failed to obtain isImmersiveLayout. Cause: ' + JSON.stringify(exception));
    }
  }
}
```


## How to Obtain the Status Bar Height

The status bar is a specific avoid area type, which corresponds to the system bar (TYPE_SYSTEM) in [AvoidAreaType](../reference/apis-arkui/arkts-apis-window-e.md#avoidareatype7).

When the main window is displayed in full screen, you can obtain the [avoid area](../reference/apis-arkui/arkts-apis-window-i.md#avoidarea7) that includes a status bar through [getWindowAvoidArea()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowavoidarea9) to indirectly obtain the height of the status bar.

The example code is as follows:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window = windowStage.getMainWindowSync(); // Obtain the main window of the application.
    if (!windowClass) {
      console.info('windowClass is null');
    }
    try {
      // Obtain the height of the status bar avoid area.
      let statusBarHeight = windowClass.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM).topRect.height;
    } catch (exception) {
      console.error(`Failed to enable the listener for system avoid area changes. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## How to Set the Window Background to Transparent

You can call [setWindowBackgroundColor()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowavoidarea9) and pass **'\#00XXXXXX'** (X indicates any hexadecimal digit) or transparent [ColorMetrics](../reference/apis-arkui/js-apis-arkui-graphics.md#colormetrics12) to make the window background transparent.

> **NOTE**
> 
> - On devices that support [free windows](window-terminology.md#free-windows), a window container is available. Its background color covers the entire window, including both the title bar and content area. If the [setWindowBackgroundColor()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowavoidarea9) API is called, the background color of the window container is displayed, because this API only sets the background color of the application content.
> 
> - You can call the [setWindowContainerColor()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowcontainercolor20) API to set the container to be transparent on 2-in-1 and tablets. Currently, the container background color cannot be set on other devices.

The example code is as follows:

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ColorMetrics } from '@kit.ArkUI';
import { window } from '@kit.ArkUI';

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
windowClass.loadContent("pages/page2", storage, (err: BusinessError) => {
  let errCode: number = err.code;
  if (errCode) {
  console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
  return;
  }
  console.info('Succeeded in loading the content.');
  // Use the ARGB mode.
  let color1: string = '#0000FF33'; 
  // Use the ColorMetrics mode.
  let color2: ColorMetrics = ColorMetrics.numeric(0x00112233);  
  try {
    windowClass?.setWindowBackgroundColor(color1);
    windowClass?.setWindowBackgroundColor(color2);
  } catch (exception) {
    console.error(`Failed to set the background color. Cause code: ${exception.code}, message: ${exception.message}`);
  };
});
```

## How to Implement Landscape/Portrait Switching

Obtain the main window instance and call the [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API to set the window orientation. For details, see [Window Rotation](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/window-rotation).

The example code is as follows:

```ts
import { BusinessError } from '@kit.BasicServicesKit'
import { common } from '@kit.AbilityKit'
import { window } from '@kit.ArkUI'

@Entry
@Component
struct OrientationTestView {
  private orientation: number =  1;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private windowClass = (this.context as common.UIAbilityContext).windowStage.getMainWindowSync();
  setOrientation(orientation: number) {
    this.windowClass.setPreferredOrientation(orientation).then(() => {
      console.log('setWindowOrientation: ' + orientation + ' Succeeded.');
    }).catch((err: BusinessError) => {
      console.log('setWindowOrientation: ' + orientation + ' Failed. Cause: ' + JSON.stringify(err));
    })
  }
  build() {
    Column() {
      Button('changeOrientation')
        .onClick(() => {
          this.setOrientation(this.orientation++ % 4 + 1)
        })
    }
    .height('100%')
    .width('100%')
    .margin({'top' : 100})
  }
}
```

For more information, see:

- [Best Practice: Display Orientation Switching](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-landscape-and-portrait-development)

- [setPreferredOrientation() parameter enum: Orientation](../reference/apis-arkui/arkts-apis-window-e.md#orientation9)

## How to Keep the Screen in Landscape/Portrait Mode Without Rotating with the Sensors 

Set the application's rotation policy to LANDSCAPE via the [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API to keep the application in landscape mode; set it to **PORTRAIT** to keep it in portrait mode; set it to **LOCKED** to lock the current application orientation without rotating with the screen (using LOCKED is not recommended as it may cause unexpected orientation changes).

To disable rotation for a single page (Navigation), you can set the [preferredOrientation](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#preferredorientation19) attribute of the component. If the attribute is set to a specific orientation such as landscape, portrait, reverse landscape, or reverse portrait, the page cannot be rotated to other directions.

## How to Obtain the Screen Orientation

Call [display.getDefaultDisplaySync()](../reference/apis-arkui/js-apis-display.md#displaygetdefaultdisplaysync9) to obtain the default display instance.

Then, obtain the [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) attribute of the instance to determine the screen orientation of the device.

The following table lists the values of the **Orientation** attribute.

| Name| Value| Description|
| -------- | -------- | -------- |
| PORTRAIT | 0 | The screen is in portrait mode.|
| LANDSCAPE | 1 | The screen is in landscape mode.|
| PORTRAIT_INVERTED | 2 | The screen is in reverse portrait mode.|
| LANDSCAPE_INVERTED | 3 | The screen is in reverse landscape mode.|

> **NOTE**
> 
> If you set the rotation policy to **LANDSCAPE** through the [setPreferredOrientation](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API, the [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) attribute obtained in the preceding steps is **LANDSCAPE_INVERTED**. This is because the window direction is different from the screen direction. You can also use [convertOrientationAndRotation()](../reference/apis-arkui/arkts-apis-window-Window.md#convertorientationandrotation23) to obtain the rotation result.

The example code is as follows:

```ts
import { display } from '@kit.ArkUI';

let displayClass: display.Display | null = null;
try {
  displayClass = display.getDefaultDisplaySync();
  let orientation = displayClass.Orientation;
} catch (exception) {
  console.error(`Failed to get default display. Code: ${exception.code}, message: ${exception.message}`);
}
```

## How to Set the Default Aspect Ratio of an Application in Landscape Mode

You are advised to use [setContentAspectRatio()](../reference/apis-arkui/arkts-apis-window-Window.md#setcontentaspectratio21) to set the aspect ratio of the window content layout.

> **NOTE**
> 
> - When you adjust the window width and height using the same **ratio** parameter, the window dimensions will adjust according to changes in the border decoration size or visibility.
> 
> - When the window title bar is set to invisible by using [setWindowDecorVisible](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowdecorvisible11), the window content area will occupy the height space originally taken by the title bar.
> 
> - When the window size is set by using other APIs such as [resize](../reference/apis-arkui/arkts-apis-window-Window.md#resize9-1) and [resizeAsync](../reference/apis-arkui/arkts-apis-window-Window.md#resizeasync12), the window size is not restricted by the ratio.
> 
> - This setting is available only for the main window and takes effect only in floating window mode (**window.WindowStatusType.FLOATING** mode).
> 
> - For versions earlier than API version 21, use [setAspectRatio()](../reference/apis-arkui/arkts-apis-window-Window.md#setaspectratio10) to set the window content layout.

The sample code snippet is as follows:

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    try {
      let windowClass = windowStage.getMainWindowSync();
      let ratio = 1.0;
      let promise = windowClass.setContentAspectRatio(ratio, true, true);
      promise.then(() => {
        console.info('Succeeded in setting aspect ratio of window.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set the aspect ratio of window. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to set the aspect ratio of window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## How to Set the Display Modes Supported by a Window

During application development, it is recommended that the **supportWindowMode** field in the [abilities](../quick-start/module-configuration-file.md#abilities) tag within the [module.json5](../quick-start/module-configuration-file.md) configuration file be used to set the display mode supported by the window.

The options are as follows:

| Value| Description|
| -------- | -------- |
| "fullscreen" | Full screen.|
| "split" | Split screen.|
| "floating" | Floating window.|

> **NOTE**
> 
> - The value of **supportWindowMode** is a string array. The default value is **["fullscreen", "split", "floating"]**.
> 
> - When **fullscreen** and **split** are both configured for a [freeform window](window-terminology.md#freeform-window), the window will be started in floating window mode if the value of [targetAPIVersion](../quick-start/app-configuration-file.md#tags-in-the-configuration-file) is less than 15, and in full-screen mode if the value is greater than or equal to 15.

The following is a configuration example of the module.json5 file:

```json
{
  "module": {
    "abilities": [
      {
        "name": "EntryAbility",
        "srcEntry": "./ets/entryability/EntryAbility.ets",
        "description": "$string:EntryAbility_desc",
        "displayName": "$string:EntryAbility_displayName",
        "windowSize": {
          "minWidth": 320,
          "minHeight": 240
        },
        // Control the window modes supported.
        "supportWindowMode": ["fullscreen", "split", "floating"],
        "launchType": "standard",
        "excludeFromMissions": false
      }
    ]
  }
}
```

In addition to the preceding configuration methods, you can also configure the window modes supported by the application in the following ways:

- Use the [metadata](window-config-m.md) tag, with the name **'ohos.ability.window.supportWindowModeInFreeMultiWindow'**. This field takes effect only in free windows mode.

- When starting **UIAbility**, use the **supportWindowModes** field in [StartOptions](../reference/apis-ability-kit/js-apis-app-ability-startOptions.md#startoptions) to specify whether to display the maximum, window-based, or split-screen button.

- After startup, call the [setSupportedWindowModes()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#setsupportedwindowmodes15) API to dynamically change the window mode supported by the current main window.

> **NOTE**
> 
> Supported window modes in free windows mode can be configured using multiple methods. The configuration priority is:
>
> Configuration via the [setSupportedWindowModes](../reference/apis-arkui/arkts-apis-window-WindowStage.md#setsupportedwindowmodes15) API &gt; Configuration via the **SupportWindowMode** in [StartOption](../reference/apis-ability-kit/js-apis-app-ability-startOptions.md#startoptions) using **StartAbility** &gt; Configuration using metadata &gt; Configuration via the **SupportWindowMode** property under the [abilities](../quick-start/module-configuration-file.md#abilities) tag in **module.json5**

## How to Determine If the Current Window is in Floating Window Mode

In application development, there are two ways to determine whether an application is in floating window mode.

- Call [getWindowStatus()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowstatus12) to query the current window mode. If the value of **WindowStatusType** is **FLOATING**, the application is in floating window mode.

  The following table lists the return values and their meanings.

  | Name| Value| Description|
  | -------- | -------- | -------- |
  | UNDEFINED | 0 | The window mode is not defined.|
  | FULL_SCREEN | 1 | The application is displayed in full screen.<br>In [freeform window](window-terminology.md#freeform-window) state, the window occupies the entire screen with no dock, title bar, or status bar displayed by default.<br>You can use [maximize()](../reference/apis-arkui/arkts-apis-window-Window.md#maximize12) and [setTitleAndDockHoverShown()](../reference/apis-arkui/arkts-apis-window-Window.md#settitleanddockhovershown14) to configure whether the title bar and dock are displayed when hovering over hot zones.<br>The last call takes precedence when both the **maximize()** and **setTitleAndDockHoverShown()** APIs are called.<br>In non-[freeform window](window-terminology.md#freeform-window) state, the window occupies the entire screen with no title bar or dock displayed. You can use [setSpecificSystemBarEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setspecificsystembarenabled11) to configure whether to display the status bar.|
  | MAXIMIZE | 2 | The application window is maximized. On 2-in-1 devices, the window covers the entire screen with a dock and a status bar.|
  | MINIMIZE | 3 | The application window is minimized.|
  | FLOATING | 4 | The application is displayed in a floating window.|
  | SPLIT_SCREEN | 5 | The application is displayed in split-screen mode.|

- Call the [on('windowStatusChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowstatuschange11) API to listen for window mode changes.

  If the application needs to respond immediately when the window mode changes (for example, from full-screen to floating window), this API can be used to listen for window mode changes for service adaptation.

  ```ts
  import { UIAbility } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  
  export default class EntryAbility extends UIAbility {
    // ...
    onWindowStageCreate(windowStage: window.WindowStage) {
      console.info('onWindowStageCreate');
      let windowClass: window.Window = windowStage.getMainWindowSync(); // Obtain the main window of the application.
      if (!windowClass) {
        console.info('windowClass is null');
      }
      try {
        // Register a listener for window status changes.
        windowClass.on('windowStatusChange', (windowStatusType: window.WindowStatusType) => {
          console.log(`status change, new status: ${windowStatusType}`);
        });
      } catch (error) {
        console.error(`status listen err: ${JSON.stringify(error)}`);
      }
      // Remember to unregister the listener at an appropriate time, for example, when the component is destroyed.
      // windowClass.off('windowStatusChange');
    }
  }
  ```

- Call the [on('windowStatusDidChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowstatusdidchange20) API to listen for window mode changes.

  After enabling the listener for window mode changes using this API, a notification is sent when the window's **windowStatus** changes (at which point the window's [Rect](../reference/apis-arkui/arkts-apis-window-i.md#rect7) property has already been updated).

  ```ts
  import { window } from '@kit.ArkUI';
  
  try {
    // Obtain the Window instance.
    windowClass.on('windowStatusDidChange', (WindowStatusType) => {
      console.info(`Succeeded in enabling the listener for window status changes. Data: ${JSON.stringify(WindowStatusType)}`);
    });
  } catch (exception) {
    console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
  }
  ```

> **NOTE**
> 
> Both [on('windowStatusChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowstatuschange11) and [on('windowStatusDidChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowstatusdidchange20) are called when the window status changes. [on('windowStatusChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowstatuschange11) does not ensure that the window attributes are updated when the callback is called. If your application needs to obtain the new window size and position immediately after receiving the window status change notification, you are advised to use [on('windowStatusDidChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowstatusdidchange20).

## How to Set the Global Floating Window Background to Transparent

You can call [setWindowBackgroundColor()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowavoidarea9) and pass **'\#00XXXXXX'** (X indicates any hexadecimal digit) or transparent [ColorMetrics](../reference/apis-arkui/js-apis-arkui-graphics.md#colormetrics12) to make the window background transparent.

## How to Determine Whether an Application is Partially or Fully Obscured

Currently, there are two APIs for determining whether the current window is obscured:

- [on('windowVisibilityChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowvisibilitychange11): Listens for window visibility. If the callback returns **false**, the current window is completely obscured. If the callback returns **true**, the current window is visible, but it cannot be determined whether the window is partially or fully obscured.

- [on('occlusionStateChanged')](../reference/apis-arkui/arkts-apis-window-Window.md#onocclusionstatechanged22): Listens for window visibility. There are three visibility states: **0** (visible), **1** (partially visible), and **2** (invisible).

## How to Determine Whether the Free Windows Mode Is Enabled

Call the [isInFreeWindowMode()](../reference/apis-arkui/arkts-apis-window-Window.md#isinfreewindowmode22) API to check whether the freeform window mode is enabled. If the return value is **true**, the current window is in the freeform window mode. If the return value is **false**, the current window is not in the freeform window mode.

Call the [on('freeWindowModeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onfreewindowmodechange22) API to listen for freeform window mode changes.

## How to Set a Privacy Window

Call the [setWindowPrivacyMode()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9-1) API to set a window to the privacy mode. In this mode, the window content cannot be captured or recorded.

For the PiP and floating ball windows, their privacy mode follows the parent window.

To take a screenshot of a privacy window, you can use the [snapshotIgnorePrivacy()](../reference/apis-arkui/arkts-apis-window-Window.md#snapshotignoreprivacy18) API.

## What Are the Position/Size Restrictions for APIs Such as resize and moveWindowTo

When calling the [resize()](../reference/apis-arkui/arkts-apis-window-Window.md#resize9-1) API to adjust the window size, the window size range is constrained by [WindowLimits](../reference/apis-arkui/arkts-apis-window-i.md#windowlimits11). The specific size limit range can be queried via the [getWindowLimits](https://developer.huawei.com/consumer/en/doc/harmonyos-references/arkts-apis-window-window#getwindowlimits11) API.

There is no restriction on the window position when [moveWindowTo()](../reference/apis-arkui/arkts-apis-window-Window.md#movewindowto9-1) is called to adjust the window position.

> **NOTE**
> 
> **Other restrictions on the resize API**:
> 
> - In the [freeform window](window-terminology.md#freeform-window) state, this API takes effect only when the window is in floating window mode (that is, the window mode is **window.WindowStatusType.FLOATING**, which can be obtained by [getWindowStatus()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowstatus12)). Otherwise, the error code 1300002 is returned.
> 
> - In non-[freeform window](window-terminology.md#freeform-window) mode, this API does not work for the main window.
> 
> **Other restrictions on the moveWindowTo API**:
> 
> - This API is best suited for the floating window mode (when the window mode is **window.WindowStatusType.FLOATING**, which you can check using [getWindowStatus()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowstatus12)). You are not advised to use it in other window modes.
> 
> - In [freeform window](window-terminology.md#freeform-window) mode, the window moves relative to the screen. In non-freeform window mode, the window moves relative to the parent window.
> 
> - To move the window relative to the screen while in non-freeform window mode, call [moveWindowToGlobal()](../reference/apis-arkui/arkts-apis-window-Window.md#movewindowtoglobal15).
> 
> - In non-[freeform window](window-terminology.md#freeform-window) mode, this API does not work for the main window.

## How to Set or Remove Watermarks

<!--Del-->
Watermarks are classified into the following types by scope:

- Window-level watermark: You can call [setWaterMarkFlag()](../reference/apis-arkui/js-apis-window-sys.md#setwatermarkflag10) to add or remove a security watermark for the current window.
<!--DelEnd-->

- Process-level watermark: You can call [setWatermarkImageForAppWindows()](../reference/apis-arkui/arkts-apis-window-f.md#windowsetwatermarkimageforappwindows21) to set or cancel a process-level watermark, which takes effect for the windows of the current process, including the windows newly created by the process.

<!--Del-->
- Screen-level watermark: You can call [setWaterMarkImage()](../reference/apis-arkui/js-apis-window-sys.md#setwatermarkflag10) to set or cancel a screen-level watermark.
<!--DelEnd-->

## How to Move a Created Window to an Extended Screen

- An application can call [moveWindowToGlobal()](../reference/apis-arkui/arkts-apis-window-Window.md#movewindowtoglobal15) to move the current window to an extended screen. You can specify the target extended screen by setting the API parameter [MoveConfiguration](../reference/apis-arkui/arkts-apis-window-i.md#moveconfiguration15).

- An application can also call [startMoving()](../reference/apis-arkui/arkts-apis-window-Window.md#startmoving14) to move the current window to the target screen using mouse or touch point dragging. The window moves along with the cursor or touch point only when this API is called in the callback of the [onTouch](../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch) event (event type is **TouchType.Down**).

## How to Achieve a Semi-Transparent Background for a Child Window

A child window can call the [setWindowBackgroundColor()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowbackgroundcolor9) API, passing **'\#XXYYYYYY'** (where **XX** represents any non-zero hexadecimal value and **Y** represents any hexadecimal digit) or a semi-transparent **ColorMetrics**.

The example code is as follows:

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ColorMetrics } from '@kit.ArkUI';
import { window } from '@kit.ArkUI';

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
windowClass.loadContent("pages/page2", storage, (err: BusinessError) => {
  let errCode: number = err.code;
  if (errCode) {
  console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
  return;
  }
  console.info('Succeeded in loading the content.');
  let color1: string = '#8800FF33'; // Use the ARGB mode.
  let color2: ColorMetrics = ColorMetrics.numeric(0x88112233); // Use the ColorMetrics mode.
  try {
    windowClass?.setWindowBackgroundColor(color1);
    windowClass?.setWindowBackgroundColor(color2);
  } catch (exception) {
    console.error(`Failed to set the background color. Cause code: ${exception.code}, message: ${exception.message}`);
  };
});
```

## How to Set Page-Level Brightness

Currently, brightness can be set only at the window level.

[setWindowBrightness()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowbrightness9-1) can be called on a specific page on the main window to achieve page-level brightness adjustment. Calling this API with value **-1** passed when exiting the page will restore the system default brightness.

## How to Restore System Default Brightness

For phones and tablets, the application can call [setWindowBrightness()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowbrightness9-1) with **-1** passed to restore the system default brightness.

For PCs and 2-in-1 devices, the window brightness and system brightness have been normalized. Therefore, after the [setWindowBrightness()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowbrightness9-1) API is called, the system brightness is directly changed. Currently, there is no method to restore the window brightness.
