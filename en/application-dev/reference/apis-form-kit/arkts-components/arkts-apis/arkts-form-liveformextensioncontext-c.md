# LiveFormExtensionContext

**LiveFormExtensionContext**, inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md), is the context of [LiveFormExtensionAbility](arkts-form-app-form-liveformextensionability-liveformextensionability-c.md).

**Inheritance/Implementation:** LiveFormExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 20

**System capability:** SystemCapability.Ability.Form

## startAbilityByLiveForm

```TypeScript
startAbilityByLiveForm(want: Want): Promise<void>
```

Starts the widget provider (application) page. This API uses a promise to return the result. <br>This API can only be used to start the page of the interactive widget provider (application). If this API is used to start the page of another application, error code 16501011 will be reported. <br>You are advised to call this API in click event callbacks. Calling it in callbacks of other gesture events is not recommended, and direct calls in non-gesture events are not allowed. Otherwise, the error code 16501011 will be reported. <br>In addition, this API can be directly called in the click event callback but cannot be called after a delay. Otherwise, the error code 16501011 will be reported.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Information about the application page to be started. [Only explicit Want is supported](../../../application-models/ability-startup-with-explicit-want.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported due to limited device capabilities. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | An IPC connection error happened. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501011](../errorcode-form.md#16501011-api-not-supported) | The form can not support this operation |

**Examples**

```TypeScript
// MyLiveFormExtensionAbility.ets
import { LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
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

```TypeScript
// pages/MyLiveFormPage.ets
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct MyLiveFormPage {
  private storageForMyLiveFormPage: LocalStorage | undefined = undefined;
  private liveFormContext: common.LiveFormExtensionContext | undefined = undefined;

  aboutToAppear(): void {
    // 2. Obtain LiveFormExtensionContext.
    this.storageForMyLiveFormPage = this.getUIContext().getSharedLocalStorage();
    this.liveFormContext = this.storageForMyLiveFormPage?.get<common.LiveFormExtensionContext>('context');
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
    } catch (err) {
      console.error(`startAbilityByLiveForm failed, code is ${err?.code}, message is ${err?.message}`);
    }
  }

  build() {
    // Replace the page with the actual one.
    Stack() {
      Column()
        .width('50%')
        .height('50%')
        .backgroundColor('#2875F5')
    }
    .width('100%')
    .height('100%')
    .onClick(() => {
      // 3. Use the API in the click event callback.
      console.info('MyLiveFormPage click to start ability');
      if (!this.liveFormContext) {
        console.info('MyLiveFormPage liveFormContext is empty');
        return;
      }
      this.startAbilityByLiveForm();
    });
  }
}
```
