# @ohos.arkui.uiExtension

The **uiExtension** module provides APIs for the [EmbeddedUIExtensionAbility](../../../application-models/embeddeduiextensionability.md) (or [UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)) to obtain the host application window information or the information about the corresponding [EmbeddedComponent](../arkts-components/arkts-arkui-embeddedcomponent-comp.md#embedded_component)<!--Del--> (or [UIExtensionComponent](../arkts-components/arkts-arkui-uiextensioncomponent-comp-sys.md#ui_extension_componentsystem-api))<!--DelEnd--> component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiExtension } from '@kit.ArkUI';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md) | Represents the information about the avoidance area of the window. |
| [RectChangeOptions](arkts-arkui-uiextension-rectchangeoptions-i.md) | Provides the values and reasons returned when the rectangle (position and size) of the component (**EmbeddedComponent** or **UIExtensionComponent**) changes. |
| [WindowProxy](arkts-arkui-uiextension-windowproxy-i.md) | The proxy of the UIExtension window. |
| [WindowProxyProperties](arkts-arkui-uiextension-windowproxyproperties-i.md) | Provides information about a component. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [WindowProxy](arkts-arkui-uiextension-windowproxy-i-sys.md) | The proxy of the UIExtension window. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [EventFlag](arkts-arkui-uiextension-eventflag-e.md) | Enumerates event types. |
| [RectChangeReason](arkts-arkui-uiextension-rectchangereason-e.md) | Enumerates the reasons for changes in the rectangle (position and size) of the component (**EmbeddedComponent** or **UIExtensionComponent**). |

## Examples

This example shows how to use all the available APIs in the [EmbeddedUIExtensionAbility](../../../application-models/embeddeduiextensionability.md). The bundle name of the sample application is com.example.embeddeddemo, and the EmbeddedUIExtensionAbility to start is ExampleEmbeddedAbility.

The EntryAbility (UIAbility) of the sample application loads the pages/Index.ets file, whose content is as follows:

```TypeScript
// The UIAbility loads pages/Index.ets when started.
import { Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'Message: ';
  private want: Want = {
    bundleName: 'com.example.embeddeddemo',
    abilityName: 'ExampleEmbeddedAbility',
  };

  build() {
    Row() {
      Column() {
        Text(this.message).fontSize(30)
        EmbeddedComponent(this.want, EmbeddedType.EMBEDDED_UI_EXTENSION)
          .width('100%')
          .height('90%')
          .onTerminated((info) => {
            this.message = 'Termination: code = ' + info.code + ', want = ' + JSON.stringify(info.want);
          })
          .onError((error) => {
            this.message = 'Error: code = ' + error.code;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

The EmbeddedUIExtensionAbility to start by the EmbeddedComponent is implemented in the ets/extensionAbility/ExampleEmbeddedAbility file. The file content is as follows:

```TypeScript
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

const TAG: string = '[ExampleEmbeddedAbility]';

export default class ExampleEmbeddedAbility extends EmbeddedUIExtensionAbility {
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

The entry page file of the EmbeddedUIExtensionAbility is pages/extension.ets, whose content is as follows:

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { uiExtension, window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry()
@Component
struct Extension {
  @State message: string = 'EmbeddedUIExtensionAbility Index';
  private storage: LocalStorage | undefined = this.getUIContext()?.getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');
  private extensionWindow: uiExtension.WindowProxy | undefined = this.session?.getUIExtensionWindowProxy();
  private subWindow: window.Window | undefined = undefined;

  aboutToAppear(): void {
    this.extensionWindow?.on('windowSizeChange', (size: window.Size) => {
      console.info(`size = ${JSON.stringify(size)}`);
    });
    this.extensionWindow?.on('rectChange', uiExtension.RectChangeReason.HOST_WINDOW_RECT_CHANGE,
      (data: uiExtension.RectChangeOptions) => {
        console.info('Succeeded window rect changes. Data: ' + JSON.stringify(data));
      });
    this.extensionWindow?.on('avoidAreaChange', (info: uiExtension.AvoidAreaInfo) => {
      console.info(`type = ${JSON.stringify(info.type)}, area = ${JSON.stringify(info.area)}`);
    });
  }

  aboutToDisappear(): void {
    this.extensionWindow?.off('windowSizeChange');
    this.extensionWindow?.off('rectChange');
    this.extensionWindow?.off('avoidAreaChange');
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(20)
        .fontWeight(FontWeight.Bold)
      Button('Obtain Component Size').width('90%').margin({ top: 5, bottom: 5 }).fontSize(16).onClick(() => {
        let rect = this.extensionWindow?.properties.uiExtensionHostWindowProxyRect;
        console.info(`EmbeddedComponent position and size info: ${JSON.stringify(rect)}`);
      })
      Button('Obtain System Avoid Area Info').width('90%').margin({ top: 5, bottom: 5 }).fontSize(16).onClick(() => {
        let avoidArea: window.AvoidArea | undefined =
          this.extensionWindow?.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
        console.info(`System avoid area: ${JSON.stringify(avoidArea)}`);
      })
      Button('Create Subwindow').width('90%').margin({ top: 5, bottom: 5 }).fontSize(16).onClick(() => {
        let subWindowOpts: window.SubWindowOptions = {
          title: 'This is a subwindow',
          decorEnabled: true
        };
        this.extensionWindow?.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
          .then((subWindow: window.Window) => {
            this.subWindow = subWindow;
            this.subWindow?.loadContent('pages/Index', this.storage, (err, data) => {
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
          console.error(`Create subwindow failed. Cause code: ${error.code}, message: ${error.message}`);
        });
      })
    }.width('100%').height('100%')
  }
}
```

Add an item to extensionAbilities in the module.json5 file of the sample application. The details are as follows:

```TypeScript
{
  "name": "ExampleEmbeddedAbility",
  "srcEntry": "./ets/extensionAbility/ExampleEmbeddedAbility.ets",
  "type": "embeddedUI"
}
```
