# Active Update of ArkTS Widgets

This section provides the development guidelines for active update. For details about the update process, see [Active Update](./arkts-ui-widget-interaction-overview.md#active-update).

## Active Update by Widget Provider
The widget provider can call [updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform) to actively update the widget. It is recommended that this API be used with the widget lifecycle callbacks [onFormEvent](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonformevent), [onUpdateForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform), and [onAddForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonaddform).

### How to Develop
The following demonstrates how to add a widget to the home screen and update the widget by tapping the update button on the widget.
1. [Create a widget](./arkts-ui-widget-creation.md).
2. Implement the widget layout, add an update button to the widget, and call the [postCardAction](../reference/apis-arkui/js-apis-postCardAction.md#postcardaction-1) API to trigger the **onFormEvent** callback.
    ```ts
    // entry/src/main/ets/updatebymessage/pages/UpdateByMessageCard.ets
    let storageUpdateByMsg = new LocalStorage();

    @Entry(storageUpdateByMsg)
    @Component
    struct UpdateByMessageCard {
      // Create two Text components to be updated. The initial content of the first Text is 'Title default' and that of the second Text is 'Description default'. For details about the resource file definition, see step 4.
      @LocalStorageProp('title') title: ResourceStr = $r('app.string.default_title');
      @LocalStorageProp('detail') detail: ResourceStr = $r('app.string.DescriptionDefault');

      build() {
        Column() {
          Column() {
            Text(this.title)
              .fontColor('#FFFFFF')
              .opacity(0.9)
              .fontSize(14)
              .margin({ top: '8%', left: '10%' })
            Text(this.detail)
              .fontColor('#FFFFFF')
              .opacity(0.6)
              .fontSize(12)
              .margin({ top: '5%', left: '10%' })
          }.width('100%').height('50%')
          .alignItems(HorizontalAlign.Start)

          Row() {
            // Add a button. For the resource file definition, see step 4.
            Button() {
              Text($r('app.string.update'))
                .fontColor('#45A6F4')
                .fontSize(12)
            }
            .width(120)
            .height(32)
            .margin({ top: '30%', bottom: '10%' })
            .backgroundColor('#FFFFFF')
            .borderRadius(16)
            .onClick(() => {
              postCardAction(this, {
                action: 'message',
                params: { msgTest: 'messageEvent' }
              });
            })
          }.width('100%').height('40%')
          .justifyContent(FlexAlign.Center)
        }
        .width('100%')
        .height('100%')
        .alignItems(HorizontalAlign.Start)
        .backgroundImage($r('app.media.CardEvent'))
        .backgroundImageSize(ImageSize.Cover)
      }
    }
    ```

3. In the implementation of **onFormEvent**, call the **updateForm** API to update the widget data.
    ```ts
    // entry/src/main/ets/entryformability/EntryFormAbility.ts
    import { formBindingData, FormExtensionAbility, formInfo, formProvider } from '@kit.FormKit';
    import { Configuration, Want } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';

    const TAG: string = 'EntryFormAbility';
    const DOMAIN_NUMBER: number = 0xFF00;

    export default class EntryFormAbility extends FormExtensionAbility {
      onAddForm(want: Want): formBindingData.FormBindingData {
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onAddForm');
        hilog.info(DOMAIN_NUMBER, TAG, want.parameters?.[formInfo.FormParam.NAME_KEY] as string);
        let formData: Record<string, string> = { };
        return formBindingData.createFormBindingData(formData);
      }

      onCastToNormalForm(formId: string): void {
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onCastToNormalForm');
      }

      onUpdateForm(formId: string): void {
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onUpdateForm');
        // ...
      }

      onChangeFormVisibility(newStatus: Record<string, number>): void {
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onChangeFormVisibility');
      }

      onFormEvent(formId: string, message: string): void {
        hilog.info(DOMAIN_NUMBER, TAG, `FormAbility onFormEvent, formId = ${formId}, message: ${JSON.stringify(message)}`);
        class FormDataClass {
          // Define the content for the two Text components as follows: 'Title Update' and 'Description update success' respectively.
          title: string = 'Title Update.';
          detail: string = 'Description update success.';
        }

        let formData = new FormDataClass();
        let formInfo: formBindingData.FormBindingData = formBindingData.createFormBindingData(formData);
        formProvider.updateForm(formId, formInfo).then(() => {
          hilog.info(DOMAIN_NUMBER, TAG, 'FormAbility updateForm success.');
        }).catch((error: BusinessError) => {
          hilog.error(DOMAIN_NUMBER, TAG, `Operation updateForm failed. Cause: ${JSON.stringify(error)}`);
        });
      }

      onRemoveForm(formId: string): void {
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onRemoveForm');
      }

      onConfigurationUpdate(config: Configuration) {
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onConfigurationUpdate:' + JSON.stringify(config));
      }

      onAcquireFormState(want: Want): formInfo.FormState {
        return formInfo.FormState.READY;
      }
    }
    ```

4. The resource file is as follows:
    ```ts
    // entry/src/main/resources/zh_CN/element/string.json
    {
      "string": [
        // ...
        {
          "name": "default_title",
          "value": "Title default."
        },
        {
          "name": "DescriptionDefault",
          "value": "Description default."
        },
        {
          "name": "update",
          "value": "update"
        }
      ]
    }
    ```
### Running Result
![WidgetPrinciple](figures/active-update-result.gif)
<!--Del-->

## Active Update by Widget Host (for System Applications Only)

Due to the time limit of interval-based and time-specific updates, the widget host can call [requestForm](../reference/apis-form-kit/js-apis-app-form-formHost-sys.md#requestform) to request the Widget Manager to actively update the widget. The Widget Manager calls the [onUpdateForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform) lifecycle callback in the FormExtensionAbility of the widget provider. In the callback, the [updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform) API can be called to update the widget content.

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let storage = new LocalStorage();

@Entry(storage)
@Component
struct Index {
  @StorageLink('formId') formId: number = 0;

  build() {
    Column() {
      Column() {
        //...
        Button() {
          //...
        }
        .onClick(() => {
          console.info(`click to check requestForm, formId: ${this.formId}`);
          // formId is the ID of the widget to be updated.
          formHost.requestForm(this.formId.toString()).then(() => {
            console.info('requestForm success.');
          }).catch((error: BusinessError) => {
            console.error(`requestForm fail, code: ${error?.code}, message: ${error?.message}`);
          })
        })
        .margin(5)
      }
      //...
    }
    //...
  }
}
```
<!--DelEnd-->
