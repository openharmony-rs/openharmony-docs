# @ohos.atomicservice.InterstitialDialogAction(This section describes the interfaces used by InterstitialDialogAction)

## Child Components

Not supported

## Attributes

The [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Events

The [universal events](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Modules to Import

```TypeScript
import { InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [InterstitialDialogAction](arkts-arkui-atomicservice-interstitialdialogaction-interstitialdialogaction-c.md) | The **InterstitialDialogAction** component is a dialog box used in atomic services to temporarily display information that requires user attention or actions to be taken while maintaining the current context. Users can trigger corresponding actions by clicking different areas of the dialog box. |

### Interfaces

| Name | Description |
| --- | --- |
| [DialogOptions](arkts-arkui-atomicservice-interstitialdialogaction-dialogoptions-i.md) | Defines the attributes specific to the dialog box and custom click actions for the user. |

### Enums

| Name | Description |
| --- | --- |
| [BottomOffset](arkts-arkui-atomicservice-interstitialdialogaction-bottomoffset-e.md) | Defines the distance between the popup and the bottom in different scenario modes, based on the presence or absence of a menu bar, with the default being the distance when there is no menu bar. |
| [IconStyle](arkts-arkui-atomicservice-interstitialdialogaction-iconstyle-e.md) | Sets the color style of the close button. By default, the close button is set to light color. |
| [TitlePosition](arkts-arkui-atomicservice-interstitialdialogaction-titleposition-e.md) | Defines the vertical position of the title relative to the subtitle in the dialog box. By default, the title is above the subtitle. |

## Examples

### Example 1

In this example, color values are assigned to the title and subtitle using two different parameter types; the close button is set to dark color; the title is set above the subtitle; and the distance type is set to the distance used when there is no menu bar.

```TypeScript
// ../entryability/EntryAbility
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let dialogUIContext: UIContext | null = null;

export function getDialogUIContext(): UIContext | null {
  if (dialogUIContext === null) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'dialogUIContext is null');
  }
  return dialogUIContext;
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content, code: ${err.code}, message: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content.');
    });

    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      let errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window, code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
      dialogUIContext = windowClass.getUIContext();
    });

    // Obtain the main window.
    windowStage.getMainWindow((err, data) => {
      if (err.code) {
        console.error(`Failed to obtain the main window, code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
      // Set the window to non-full-screen.
      windowClass.setWindowLayoutFullScreen(false);
    })
  }

  onWindowStageDestroy(): void {
    // Main window is destroyed, release UI related resources
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
  }

  onForeground(): void {
    // Ability has brought to foreground
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onBackground(): void {
    // Ability has back to background
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
  }
}
```



```TypeScript
// Index.ets
import { getDialogUIContext } from '../entryability/EntryAbility';
import { UIContext, InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('show dialog')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let ctx: UIContext | null = getDialogUIContext();
            let interstitialDialogAction: InterstitialDialogAction = new InterstitialDialogAction({
              uiContext: ctx as UIContext,
              title: 'Title',
              subtitle: 'Subtitle',
              titleColor: 'rgb(255, 192, 0)',
              subtitleColor: Color.Red,
              backgroundImage: $r('app.media.testBackgroundImg'),
              foregroundImage: $r('app.media.testForegroundImg'),
              iconStyle: IconStyle.DARK,
              titlePosition: TitlePosition.TOP,
              bottomOffsetType: BottomOffset.OFFSET_FOR_NONE,
              onDialogClick: () => { console.info('outer dialog click action') },
              onDialogClose: () => { console.info('outer close action') }
            });
            interstitialDialogAction.openDialog();
          })
      }
      .width('100%')
    }
    .height('100%')
    .backgroundColor('rgba(0, 0, 0, 0.1)')
  }
}
```

### Example 2

In this example, color values are assigned to the title and subtitle using two different parameter types; the close button is set to light color; the title is set below the subtitle; and the distance type is set to the distance used when there is a menu bar.

```TypeScript
// ../entryability/EntryAbility
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let dialogUIContext: UIContext | null = null;

export function getDialogUIContext(): UIContext | null {
  if (dialogUIContext === null) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'dialogUIContext is null');
  }
  return dialogUIContext;
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content, code: ${err.code}, message: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content.');
    });

    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      let errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window, code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
      dialogUIContext = windowClass.getUIContext();
    });

    // Obtain the main window.
    windowStage.getMainWindow((err, data) => {
      if (err.code) {
        console.error(`Failed to obtain the main window, code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
      // Set the window to non-full-screen.
      windowClass.setWindowLayoutFullScreen(false);
    })
  }

  onWindowStageDestroy(): void {
    // Main window is destroyed, release UI related resources
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
  }

  onForeground(): void {
    // Ability has brought to foreground
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onBackground(): void {
    // Ability has back to background
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
  }
}
```

```TypeScript
// Index.ets
import { getDialogUIContext } from '../entryability/EntryAbility';
import { UIContext, InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('show dialog')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let ctx: UIContext | null = getDialogUIContext();
            let interstitialDialogAction: InterstitialDialogAction = new InterstitialDialogAction({
              uiContext: ctx as UIContext,
              title: 'Title',
              subtitle: 'Subtitle',
              titleColor: 'rgb(255, 192, 0)',
              subtitleColor: Color.Red,
              backgroundImage: $r('app.media.testBackgroundImg'),
              foregroundImage: $r('app.media.testForegroundImg'),
              iconStyle: IconStyle.LIGHT,
              titlePosition: TitlePosition.BOTTOM,
              bottomOffsetType: BottomOffset.OFFSET_FOR_BAR,
              onDialogClick: () => { console.info('outer dialog click action') },
              onDialogClose: () => { console.info('outer close action') }
            });
            interstitialDialogAction.openDialog();
          })
      }
      .width('100%')
    }
    .height('100%')
    .backgroundColor('rgba(0, 0, 0, 0.1)')
  }
}
```
