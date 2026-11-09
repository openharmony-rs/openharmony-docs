# Window Rotation Practical Cases

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @lizihao_73-->
<!--Designer: @zhoulin_-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=4402824db11205a9032b004db265a09ab8d67bc8 translatedAt=2026-11-05T10:55:31.314Z pushedAt=2026-11-06T01:46:04.700Z nl=1 -->

Window rotation is an important capability for adapting an app to different device forms and usage scenarios. It allows the app to automatically adjust the UI layout based on the device orientation, improving the user experience.

When developing an app, developers need to consider the rotation policy experience across multiple device types. To help developers get started quickly, adaptation examples are provided for the following typical scenarios.

## Rotation Policy Configuration for Differentiated Device Adaptation

Currently, there is a wide variety of device forms, including bar phones, foldables, tri-fold devices, wide-fold devices, and more. If an app's rotation policy is adapted for only one type of device, the experience on other devices may be degraded. To eliminate the extra adaptation effort caused by new device types, a device-type-independent approach must be adopted for configuring rotation policies.

You can sort out the rotation requirements for different device forms based on your own business. If a single strategy (for example, `FOLLOW_DESKTOP` or `AUTO_ROTATION_UNSPECIFIED`) meets the requirements, it is recommended to use a single strategy. If a single strategy does not meet the requirements, you can refer to the [breakpoint mechanism](../ui/arkts-layout-development-grid-layout.md#breakpoints) (a responsive design mechanism that divides device sizes into different ranges based on thresholds such as window width and aspect ratio, and applies different adaptation strategies in different ranges) to implement differentiated adaptation.

For example, on a tri-fold device, portrait display is expected in the F state (fully folded state, showing only one outer screen), portrait display is expected in the M state (intermediate unfolded state, showing only two inner screens), and landscape display is expected in the G state (fully unfolded state, showing all three inner screens). For the fold status enumeration of tri-fold devices, see [FoldStatus](../reference/apis-arkui/js-apis-display.md#foldstatus10). On a tablet, landscape display is expected. On a bar phone, portrait display is expected. In this scenario, you can use the [WidthBreakpoint](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#widthbreakpoint13) width breakpoint and the [HeightBreakpoint](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#heightbreakpoint13) height breakpoint to implement differentiated adaptation.

The sample code is as follows:

<!-- @[quick_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/DeviceDifferentiationSample/entry/src/main/ets/pages/Index.ets) -->  

``` TypeScript
import { window } from '@kit.ArkUI';
import { common } from '@kit.AbilityKit';
import { Callback, BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State currentOrientation: string = 'UNSPECIFIED';
  private stage: window.WindowStage = (this.getUIContext().getHostContext() as common.UIAbilityContext).windowStage;
  private foldDisplayModeCallback: Callback<display.FoldDisplayMode> = (data: display.FoldDisplayMode) => {
    console.info(`Succeeded in listening fold display mode change, data is ${data}`);
    this.getBreakPointAndSetOrientation();
  };

  aboutToAppear() {
    try {
      const ret = display.isFoldable();
      if (ret) {
        display.on('foldDisplayModeChange', this.foldDisplayModeCallback);
      } else {
        this.getBreakPointAndSetOrientation();
      }
    } catch (err) {
      console.error(`aboutToAppear error: ${(err as BusinessError).message}`);
    }
  }

  aboutToDisappear() {
    try {
      display.off('foldDisplayModeChange', this.foldDisplayModeCallback);
    } catch (err) {
      console.error(`aboutToDisappear error: ${(err as BusinessError).message}`);
    }
  }

  private getBreakPointAndSetOrientation(): void {
    try {
      let displayInfo = display.getDefaultDisplaySync();
      let displayWidth = displayInfo.width;
      let displayHeight = displayInfo.height;
      let heightBp = displayHeight / displayWidth;
      if (displayWidth > displayHeight) {
        let temp = displayWidth;
        displayWidth = displayHeight;
        displayHeight = temp;
      }
      // It is recommended to prioritize a single strategy (such as "FOLLOW_DESKTOP") to accommodate device differences. If a single strategy cannot meet the requirements, use the breakpoint mechanism to mask device differences.
      // This is a special example. In principle, for an application that supports landscape orientation, the rotation strategy should support rotation in all four directions. This example is provided only to illustrate how breakpoints are used.
      // 600 is a boundary value of the width breakpoint enumeration, and 0.8 is a boundary value of the aspect ratio breakpoint enumeration.
      if (displayWidth >= 600 && heightBp < 0.8) {
        this.stage.getMainWindowSync().setPreferredOrientation(window.Orientation.LANDSCAPE)
          .catch((err: BusinessError) => {
            console.error(`setPreferredOrientation error: ${err.message}`);
          });
        this.currentOrientation = 'LANDSCAPE';
      } else {
        this.stage.getMainWindowSync().setPreferredOrientation(window.Orientation.PORTRAIT)
          .catch((err: BusinessError) => {
            console.error(`setPreferredOrientation error: ${err.message}`);
          });
        this.currentOrientation = 'PORTRAIT';
      }
    } catch (err) {
      console.error(`getBreakPointAndSetOrientation error: ${(err as BusinessError).message}`);
    }
  }

  build() {
    RelativeContainer() {
      Text(this.currentOrientation)
        .fontWeight(600)
        .fontSize(30)
        .textAlign(TextAlign.Center)
        .position({ y: 300 })
        .width('100%')
    }
    .height('100%')
    .width('100%')
  }
}
```


## Landscape/Portrait Switching for Video Apps

Landscape/portrait switching for video apps refers to the scenario where the details page of the playback UI is displayed in portrait mode, and users can switch the page to landscape mode via a full-screen button for a better viewing experience.

You can implement landscape/portrait switching for the video playback UI in the following two ways:

- Set the main window orientation by [calling the setPreferredOrientation() API of window management](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-landscape-and-portrait-development#section188583141719).

- Set the video window orientation by navigating to a page with a different display orientation. For implementation details, see [Implementing Landscape/Portrait Mode Switching Through Page Redirection](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-landscape-and-portrait-development#section161651074615).

> **NOTE**
>
> Before calling [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1), make sure that a valid main window instance has been obtained through [getMainWindowSync()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#getmainwindowsync9).

## Converting Between Screen Orientation and Window Orientation

There are three related but distinct concepts: screen [orientation](../reference/apis-arkui/js-apis-display.md#attributes), screen [rotation](../reference/apis-arkui/js-apis-display.md#attributes), and window [orientation](../reference/apis-arkui/arkts-apis-window-i.md#rotationchangeinfo19).

In multi-device and multi-form scenarios (for example, foldable phones, tablets, and external monitors), the screen [rotation](../reference/apis-arkui/js-apis-display.md#attributes) (physical angle) and the screen [orientation](../reference/apis-arkui/js-apis-display.md#attributes) (logical landscape/portrait state) do not always correspond one-to-one.

The following table shows the correspondence among the screen angle, screen orientation, and window orientation for bar phones and the unfolded state of dual-fold devices:

| Screen Angle | Screen Orientation | Window Orientation |
| -------- | -------- | -------- |
| 0 | PORTRAIT | PORTRAIT |
| 90 | LANDSCAPE | LANDSCAPE_INVERTED |
| 180 | PORTRAIT_INVERTED | PORTRAIT_INVERTED |
| 270 | LANDSCAPE_INVERTED | LANDSCAPE |

The following table shows the correspondence among the screen angle, screen orientation, and window orientation for the unfolded state of wide-fold devices and the fully unfolded state of tri-fold devices (under certain features, the actual behavior may differ from the table; the actual behavior prevails):

| Screen Angle | Screen Orientation | Window Orientation |
| -------- | -------- | -------- |
| 90 | PORTRAIT | PORTRAIT |
| 180 | LANDSCAPE | LANDSCAPE_INVERTED |
| 270 | PORTRAIT_INVERTED | PORTRAIT_INVERTED |
| 0 | LANDSCAPE_INVERTED | LANDSCAPE |

The definitions of screen orientation and window orientation in the landscape direction are not consistent. For example, on a bar phone, the landscape window orientation corresponds to the inverted landscape screen orientation, while the inverted landscape window orientation corresponds to the landscape screen orientation. The screen angle and screen orientation also do not always correspond one-to-one. For example, in the fully unfolded state of a tri-fold device, when the screen angle is 0, the screen orientation is not portrait but inverted landscape. If you directly use [display.rotation](../reference/apis-arkui/js-apis-display.md#attributes) or [display.orientation](../reference/apis-arkui/js-apis-display.md#attributes) to determine the actual display orientation of the window, the app may display in a misaligned orientation. Therefore, you cannot simply determine the window [orientation](../reference/apis-arkui/arkts-apis-window-i.md#rotationchangeinfo19) based on the screen [orientation](../reference/apis-arkui/js-apis-display.md#attributes) or [rotation](../reference/apis-arkui/js-apis-display.md#attributes).

If you want to accurately know the current window orientation to select a rotation policy (for example, locking the current orientation on a video playback page), it is recommended to first obtain [display.rotation](../reference/apis-arkui/js-apis-display.md#attributes) or [display.orientation](../reference/apis-arkui/js-apis-display.md#attributes), and then use [convertOrientationAndRotation()](../reference/apis-arkui/arkts-apis-window-Window.md#convertorientationandrotation23) to convert the screen orientation to the window orientation. The following is a specific example:

1. Obtain the target screen orientation. Call [getDefaultDisplaySync()](../reference/apis-arkui/js-apis-display.md#displaygetdefaultdisplaysync9) to obtain the **Display** object of the target screen, and then obtain the screen orientation through [display.orientation](../reference/apis-arkui/js-apis-display.md#attributes).

2. Convert the screen orientation to the window orientation. Call [convertOrientationAndRotation()](../reference/apis-arkui/arkts-apis-window-Window.md#convertorientationandrotation23) to convert [display.orientation](../reference/apis-arkui/js-apis-display.md#attributes) to the window [orientation](../reference/apis-arkui/arkts-apis-window-i.md#rotationchangeinfo19).

3. Convert the window orientation to a rotation strategy. The window orientation must be further converted to the window [Orientation](../reference/apis-arkui/arkts-apis-window-e.md#orientation9) that the system can recognize as a rotation strategy before it can be passed to [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1).

4. Call [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) to set the rotation policy and lock the display orientation.

<!-- @[quick_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/ConvertOrientationAndRotationSample/entry/src/main/ets/pages/Index.ets) --> 

``` TypeScript
import { display, window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct SpecificSceneSetOrientationIndex {
  mainWindow: window.Window | undefined;

  aboutToAppear() {
    // Save the main window in EntryAbility.ets through windowStage.getMainWindowSync().
    this.mainWindow = AppStorage.get('mainWindow_SetOrientation') as window.Window;
  }

  setOrientationByDisplay() {
    if (!this.mainWindow) {
      console.error('Main window is not available.');
      return;
    }
    try {
      // 1. Obtain the current default Display.
      const disp = display.getDefaultDisplaySync();
      const displayOrientation = disp.orientation; // Current screen orientation (0/1/2/3).

      console.info(`Succeeded in getting display orientation, orientation is ${displayOrientation}`);
      // 2. Convert displayOrientation to windowOrientation.
      let windowOrientation: number =
        this.mainWindow.convertOrientationAndRotation(
          window.RotationInfoType.DISPLAY_ORIENTATION,
          window.RotationInfoType.WINDOW_ORIENTATION,
          displayOrientation
        );
      // 3. Map windowOrientation to window.Orientation.
      let orientation: window.Orientation = window.Orientation.UNSPECIFIED;

      switch (windowOrientation) {
        case 0:
          orientation = window.Orientation.PORTRAIT;
          break;
        case 1:
          orientation = window.Orientation.LANDSCAPE_INVERTED;
          break;
        case 2:
          orientation = window.Orientation.PORTRAIT_INVERTED;
          break;
        case 3:
          orientation = window.Orientation.LANDSCAPE;
          break;
        default:
          throw new Error('Invalid orientation value');
      }
      // 4. Set the rotation policy to lock the window orientation.
      this.mainWindow.setPreferredOrientation(orientation).then(() => {
        console.info('Succeeded in setting preferred orientation.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set preferred orientation. Code is ${err.code}, message is ${err.message}`);
      });
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to set orientation by display. Code is ${err.code}, message is ${err.message}`);
    }
  }
  build() {
    Column() {
      Text('Lock the display orientation')
        .fontSize(17)
      Button('Set orientation from display')
        .onClick(() => {
          console.info('Click: Set orientation from display');
          this.setOrientationByDisplay();
        })
        .margin({ top: 20 })
    }
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
    .height('100%')
    .width('100%')
  }
}
```

