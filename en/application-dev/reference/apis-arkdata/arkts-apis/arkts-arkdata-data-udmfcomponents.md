# @ohos.data.UdmfComponents

## Modules to Import

```TypeScript
import { ContentFormCard, FormType } from '@kit.ArkData';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [ContentFormCard](arkts-arkdata-data-udmfcomponents-contentformcard-s.md) | Defines the information of a content card component that is displayed in an application, including the title, description, content image, application information, and the like. It is applicable to scenarios such as content distribution, social updates, and message notifications. |

### Enums

| Name | Description |
| --- | --- |
| [FormType](arkts-arkdata-data-udmfcomponents-formtype-e.md) | Enumerates content card types, including large, medium, and small. |

## Examples

```TypeScript
// Import required modules.
import { uniformDataStruct } from '@kit.ArkData'

@Entry
@Component
struct Index {
  // Define the content card data.
  @State contentForm: uniformDataStruct.ContentForm = {
    uniformDataType: 'general.content-form',
    title: ''
  };
  // Control the card display status.
  @State startToShow: boolean = false;

  // Initialize data when the component is about to be displayed.
  aboutToAppear(): void {
    this.initData();
  }

  // Initialize the content card data.
  async initData() {
    // Obtain the application context.
    let context = this.getUIContext().getHostContext();
    if (!context) {
      return;
    }
    try {
      // Load the application icon and thumbnail resources.
      let appIcon = await context.resourceManager.getMediaContent($r('app.media.startIcon').id);
      let thumbImage = await context.resourceManager.getMediaContent($r('app.media.foreground').id);
      // Build the content card data object.
      this.contentForm = {
        uniformDataType: 'general.content-form',
        title: 'Content form title',
        thumbData: appIcon,
        description: 'Content form description',
        appIcon: thumbImage,
        appName: 'com.test.demo'
      };
    } catch (err) {
      console.error(`Init data error`);
    }
  }

  // Build the UI.
  build() {
    Column() {
      // Display a button. After the button is tapped, the content card is displayed.
      Button('show card')
        .onClick(() => {
          this.startToShow = true;
        })
      // Conditionally render the content card component.
      if (this.startToShow) {
        ContentFormCard({
          contentFormData: this.contentForm,
          formType: FormType.TYPE_SMALL,
          formWidth: 110,
          formHeight: 50,
          // Callback for tapping the card.
          handleOnClick: () => {
            console.info(`Clicked card`);
          }
        })
      }
    }
  }
}
```
