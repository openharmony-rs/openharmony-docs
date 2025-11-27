# LiveFormExtensionContext
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @chenmingze-->
<!--Adviser: @HelloShuo-->
**LiveFormExtensionContext**, inherited from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md), is the context of [LiveFormExtensionAbility](./js-apis-app-form-LiveFormExtensionAbility.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import
```ts
import { LiveFormExtensionAbility } from '@kit.FormKit';
```

## LiveFormExtensionContext

LiveFormExtensionContext, inherited from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md), allows you to access resources specific to LiveFormExtensionAbility.

### startAbilityByLiveForm

startAbilityByLiveForm(want: Want): Promise&lt;void&gt;

Starts the widget provider (application) page. This API uses a promise to return the result.

This API can only be used to start the page of the interactive widget provider (application). If this API is used to start the page of another application, error code 16501011 will be reported.

You are advised to call this API in click event callbacks. Calling it in callbacks of other gesture events is not recommended, and direct calls in non-gesture events are not allowed. Otherwise, the error code 16501011 will be reported.

In addition, this API can be directly called in the click event callback but cannot be called after a delay. Otherwise, the error code 16501011 will be reported.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.Form

**Atomic service API**: This API can be used in atomic services since API version 20.

**Parameters**

  | Name| Type   | Mandatory| Description                                  |
  | ------ | ------ | ---- | ------------------------------------- |
  | want  |  [Want](../apis-ability-kit/js-apis-app-ability-want.md)  | Yes  | Information about the application page to be started. [Only explicit Want is supported](../../../application-dev/application-models/ability-startup-with-explicit-want.md).  |

**Return value** 
  | Type| Description   |
  | ------ | ------ |
  | Promise&lt;void&gt;  |  Promise that returns no value. | 

**Error codes**

For details about the error codes, see [Form Error Codes](errorcode-form.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported due to limited device capabilities.                 |
| 16500050 | An IPC connection error happened.                            |
| 16500100 | Failed to obtain the configuration information.                        |
| 16501000 | An internal functional error occurred.                       |
| 16501011 | The form can not support this operation.                       |

**Example**

```ts
// MyLiveFormExtensionAbility.ets
import { formInfo, LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    // 1. Pass LiveFormExtensionContext to the widget page component.
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('context', this.context);
    session.loadContent('pages/MyLiveFormPage', storage);
  }
};
```
```ts
// pages/MyLiveFormPage.ets
import { BusinessError } from '@kit.BasicServicesKit';
import LiveFormExtensionContext from 'application/LiveFormExtensionContext';

@Entry
@Component
struct MyLiveFormPage {
  private storageForMyLiveFormPage: LocalStorage | undefined = undefined;
  private liveFormContext: LiveFormExtensionContext | undefined = undefined;

  aboutToAppear(): void {
    // 2. Obtain LiveFormExtensionContext.
    this.storageForMyLiveFormPage = this.getUIContext().getSharedLocalStorage();
    this.liveFormContext = this.storageForMyLiveFormPage?.get<LiveFormExtensionContext>('context');
  }

   private startAbilityByLiveForm(): void {
    try {
      // Replace the Want information with the actual one.
      this.liveFormContext?.startAbilityByLiveForm({
        bundleName: 'com.example.liveformdemo',
        abilityName: 'EntryAbility',
      })
        .then(() => {
          console.info('startAbilityByLiveForm succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`startAbilityByLiveForm failed, code is ${err?.code}, message is ${err?.message}`);
        });
    } catch (e) {
      console.error(`startAbilityByLiveForm failed, code is ${e?.code}, message is ${e?.message}`);
    }
  }

  build() {
    Stack() {
      // Replace the page with the actual one.
    }
    .onClick(() => {
      // 3. Use the API in the click event callback.
      console.info('MyLiveFormPage click to start ability');
      if (!this.liveFormContext) {
        console.info('MyLiveFormPage liveFormContext is empty');
        return;
      }
      this.startAbilityByLiveForm();
    })
  }
}
```
