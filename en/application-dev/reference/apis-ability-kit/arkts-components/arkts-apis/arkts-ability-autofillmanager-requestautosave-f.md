# requestAutoSave

## Modules to Import

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

## requestAutoSave

```TypeScript
export function requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void
```

Requests to automatically save the widget data. This API uses an asynchronous callback to return the result. If the current widget does not support widget switching, you can call this API to save historical widget input data. The callback is triggered when the auto-save request is complete.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | UI context in which the auto-save operation will be performed. |
| callback | [AutoSaveCallback](arkts-ability-autofillmanager-autosavecallback-i.md) | No | Implements callbacks triggered when auto-save is complete. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Get instance id failed;<br>2. Parse instance id failed; 3. The second parameter is not of type callback. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window, UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    // Create a local storage instance.
    let localStorageData: Record<string, string | common.UIAbilityContext> = {
      'message': "AutoFill Page",
      'context': this.context,
    };
    let storage = new LocalStorage(localStorageData);
    // Load the page content.
    windowStage.loadContent('pages/Index', storage, (err, data) => {
      if (err && err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      // Obtain the main window.
      windowStage.getMainWindow((err: BusinessError, data: window.Window) => {
        if (err?.code) {
          console.error('Failed to obtain the main window. Cause: ' + JSON.stringify(err));
          return;
        }
        console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
        // Obtain the UIContext instance.
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        // Store the UIContext in AppStorage for access by other pages.
        AppStorage.setOrCreate("uiContext", uiContext);
      })
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```

```TypeScript
// Index.ets
import { autoFillManager } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let uiContext = AppStorage.get<UIContext>('uiContext');
// Define the AutoSave callback.
let callback: autoFillManager.AutoSaveCallback = {
  onSuccess: () => {
    console.info(`save request on success.`);
  },
  onFailure: () => {
    console.error(`save request on failure.`);
  }
};

@Entry
@Component
struct Index {
  @State userName: string = "";
  @State password: string = "";
  // Obtain the current UIContext instance.
  private uiContext: UIContext = this.getUIContext();
  build() {
    GridRow({ gutter: { y: 20 } }) {
      GridCol({ span: 20 }) {
        TextInput({ placeholder: 'Enter userName', text: this.userName })
          .type(InputType.USER_NAME)
          .width('90%')
          .onChange((value: string) => {
            this.userName = value
          })
      }
      GridCol({ span: 20 }) {
        TextInput({ placeholder: 'Enter password', text: this.password })
          .type(InputType.Password)
          .width('90%')
          .onChange((value: string) => {
            this.password = value
          })
      }
      GridCol({ span: 20 }) {
        Button('requestAutoSave')
          .onClick(() => {
            try {
              // Initiate the save request.
              autoFillManager.requestAutoSave(this.uiContext, callback);
            } catch (error) {
              console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          })
      }
    }
  }
}
```


<a id="requestautosave-1"></a>

## requestAutoSave

```TypeScript
export function requestAutoSave(context: UIContext, request: SaveRequest, callback?: AutoSaveCallback): void
```

Trigger an auto save request.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | Indicates the ui context where the save operation will be performed. |
| request | [SaveRequest](arkts-ability-autofillmanager-saverequest-t.md) | Yes | Indicates the struct of automatic save request. |
| callback | [AutoSaveCallback](arkts-ability-autofillmanager-autosavecallback-i.md) | No | Indicates the callback that used to receive the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
// Index.ets
import { autoFillManager } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Configure request based on the actual project.
let request: autoFillManager.SaveRequest = {
  viewData: {
    bundleName: "com.example.testBundleName",
    pageUrl: "testPageUrl",
    pageNodeInfos: [
      {
        id: 1,
        autoFillType: autoFillManager.AutoFillType.USER_NAME,
        value: "testValue1",
        placeholder: "testPlaceholder1",
        rect: {
          left: 1,
          top: 1,
          width: 1,
          height: 1,
        },
        isFocus: false
      },
      {
        id: 2,
        autoFillType: autoFillManager.AutoFillType.PASSWORD,
        value: "testValue2",
        placeholder: "testPlaceholder2",
        rect: {
          left: 1,
          top: 1,
          width: 1,
          height: 1,
        },
        isFocus: false
      }
    ],
    pageRect: {
      left: 1,
      top: 1,
      width: 1,
      height: 1
    }
  }
}
// Define the AutoSave callback.
let callback: autoFillManager.AutoSaveCallback = {
  onSuccess: () => {
    console.info(`save request on success.`);
  },
  onFailure: () => {
    console.error(`save request on failure.`);
  }
};

@Entry
@Component
struct Index {
  private uiContext: UIContext = this.getUIContext();
  build() {
    GridRow({ gutter: { y: 20 } }) {
      GridCol({ span: 20 }) {
        Button('requestAutoSave')
          .onClick(() => {
            try {
              // Initiate the save request.
              autoFillManager.requestAutoSave(this.uiContext, request, callback);
            } catch (error) {
              console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          })
      }
    }
  }
}
```
