# @ohos.uiExtensionHost

Intended only for the **UIExtensionComponent** that has process isolation requirements, the **uiExtensionHost** module provides APIs for obtaining the host application window information and information about the component itself.

> **NOTE:** 
> 
> No new function will be added to this module. Related functions will be provided in the
> [uiExtension](arkts-arkui-arkui-uiextension.md) interface.
> 
> The APIs provided by this module are system APIs.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiExtensionHost } from '@kit.ArkUI';
```

## Summary

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [UIExtensionHostWindowProxy](arkts-arkui-uiextensionhost-uiextensionhostwindowproxy-i-sys.md) | Transition Controller |
| [UIExtensionHostWindowProxyProperties](arkts-arkui-uiextensionhost-uiextensionhostwindowproxyproperties-i-sys.md) | Defines information about the host application window and **UIExtensionComponent**. |
<!--DelEnd-->

## Examples

This example shows how to use all the available APIs in the UIExtensionAbility. The bundle name of the sample application, which requires a system signature, is com.example.uiextensiondemo, and the UIExtensionAbility to start is ExampleUIExtensionAbility.

The EntryAbility (UIAbility) of the sample application loads the pages/Index.ets file, whose content is as follows:

```TypeScript
// The UIAbility loads pages/Index.ets when started.
import { Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'Message: ';
  private want: Want = {
    bundleName: 'com.example.uiextensiondemo',
    abilityName: 'ExampleUIExtensionAbility',
    parameters: {
      'ability.want.params.uiExtensionType': 'sys/commonUI'
    }
  }

  build() {
    Row() {
      Column() {
        Text(this.message).fontSize(30)
        UIExtensionComponent(this.want)
          .width('100%')
          .height('90%')
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

The UIExtensionAbility to start by the UIExtensionComponent is implemented in the ets/extensionAbility/ExampleUIExtensionAbility file. The file content is as follows:

```TypeScript
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

const TAG: string = '[ExampleUIExtensionAbility]';
export default class ExampleUIExtensionAbility extends UIExtensionAbility {
  onCreate() {
    console.info(TAG, `onCreate`);
  }

  onForeground() {
    console.info(TAG, `onForeground`);
  }

  onBackground() {
    console.info(TAG, `onBackground`);
  }

  onDestroy() {
    console.info(TAG, `onDestroy`);
  }

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    console.info(TAG, `onSessionCreate, want: ${JSON.stringify(want)}`);
    let param: Record<string, UIExtensionContentSession> = {
      'session': session
    };
    let storage: LocalStorage = new LocalStorage(param);
    session.loadContent('pages/extension', storage);
  }
}
```

The entry page file of the UIExtensionAbility is pages/extension.ets, whose content is as follows:

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uiExtensionHost, window } from '@kit.ArkUI';

@Entry()
@Component
struct Extension {
  @State message: string = 'UIExtensionAbility Index';
  private storage: LocalStorage | undefined = this.getUIContext()?.getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');
  private extensionHostWindow: uiExtensionHost.UIExtensionHostWindowProxy | undefined = this.session?.getUIExtensionHostWindowProxy();
  private subWindow: window.Window | undefined = undefined;

  aboutToAppear(): void {
    this.extensionHostWindow?.on('windowSizeChange', (size) => {
        console.info(`size = ${JSON.stringify(size)}`);
    });
    this.extensionHostWindow?.on('avoidAreaChange', (info) => {
        console.info(`type = ${JSON.stringify(info.type)}, area = ${JSON.stringify(info.area)}`);
    });
    this.extensionHostWindow?.hideNonSecureWindows(true)?.then(() => {
      console.info(`Succeeded in hiding the non-secure windows.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to hide the non-secure windows. Code: ${err.code}, message: ${err.message}`);
    });
    this.extensionHostWindow?.hidePrivacyContentForHost(true)?.then(() => {
      console.info(`Succeeded in enabling privacy protection for non-system screenshots.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to enable privacy protection for non-system screenshots. Code: ${err.code}, message: ${err.message}`);
    });
  }

  aboutToDisappear(): void {
    this.extensionHostWindow?.off('windowSizeChange');
    this.extensionHostWindow?.off('avoidAreaChange');
    this.extensionHostWindow?.hideNonSecureWindows(false)?.then(() => {
      console.info(`Succeeded in showing the non-secure windows.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to show the non-secure windows. Code: ${err.code}, message: ${err.message}`);
    });
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(20)
        .fontWeight(FontWeight.Bold)
      Button('Obtain Component Size').width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
        let rect = this.extensionHostWindow?.properties.uiExtensionHostWindowProxyRect;
        console.info(`EmbeddedComponent position and size info: ${JSON.stringify(rect)}`);
      })
      Button('Obtain System Avoid Area Info').width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
        let avoidArea: window.AvoidArea | undefined = this.extensionHostWindow?.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
        console.info(`System avoid area: ${JSON.stringify(avoidArea)}`);
      })
      Button('Create Subwindow').width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
        let subWindowOpts: window.SubWindowOptions = {
          title: 'This is a subwindow',
          decorEnabled: true
        };
        this.extensionHostWindow?.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
          .then((subWindow: window.Window) => {
            this.subWindow = subWindow;
            this.subWindow.loadContent('pages/Index', this.storage, (err, data) => {
              if (err && err.code) {
                return;
              }
              this.subWindow?.resize(300, 300, (err, data) => {
                if (err && err.code) {
                  return;
                }
                this.subWindow?.moveWindowTo(100, 100, (err, data) => {
                  if (err && err.code) {
                    return;
                  }
                  this.subWindow?.showWindow((err, data) => {
                    if (err && err.code) {
                      console.error(`Failed to show the subwindow. Code: ${err.code}, message: ${err.message}`);
                    } else {
                      console.info(`The subwindow has been shown!`);
                    }
                  });
                });
              });
            });
          }).catch((error: BusinessError) => {
            console.error(`Create subwindow failed. Code: ${error.code}, message: ${error.message}`);
          });
      })
    }.width('100%').height('100%')
  }
}
```

Add an item to extensionAbilities in the module.json5 file of the sample application. The details are as follows:

```TypeScript
{
  "name": "ExampleUIExtensionAbility",
  "srcEntry": "./ets/extensionAbility/ExampleUIExtensionAbility.ets",
  "type": "sys/commonUI"
}
```
