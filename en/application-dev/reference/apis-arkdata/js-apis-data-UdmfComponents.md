# @ohos.data.UdmfComponents (Content Card)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

A content card designed in the [ContentForm](js-apis-data-uniformDataStruct.md#contentform14) struct. You can set the title (mandatory), description, application icon, application name, redirection link, and content image for the content card. When a user taps the card, a callback of the pass event is triggered to redirect the user to the specified page if the target link is set.

**Use scenarios**:
- Display of shared content in social applications
- Instant message card
- Content recommendation card

> **NOTE**
>
> This component is supported since API version 20. Updates will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Module to Import

```js
import { ContentFormCard, FormType } from '@kit.ArkData';
```

## Child Component

N/A

## ContentFormCard

ContentFormCard({contentFormData: uniformDataStruct.ContentForm, formType: FormType, formWidth?: number, formHeight?: number, handleOnClick?: Function})

Defines the information of a content card component that displayed in an application, including the title, description, content image, application information, and the like. It is applicable to scenarios such as content distribution, social updates, and message notifications.

**Decorator**: \@Component

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name| Type| Mandatory| Decorator| Description|
| -------- | -------- | -------- | -------- | -------- |
| contentFormData | [uniformDataStruct.ContentForm](js-apis-data-uniformDataStruct.md#contentform14) | Yes| - | Content card data, which is used to set the title, description, application icon, application name, redirection link, or content image to be displayed on the card.|
| formType | [FormType](#formtype) | Yes| @Prop | Content card type, which affects the size of the content card.|
| formWidth | number | No| @Prop | Card width. The value ranges from 0.8 to 1.2 times the default width of the content card type. If **formType** is set to **TYPE_SMALL**, the value ranges from 0.4 to 1.2 times the default width of the content card type. The unit is vp. If this parameter is not specified, the default width of the content card type is used.|
| formHeight | number | No| @Prop | Card height. If title in **contentFormData** is an empty string, the card height is the passed value. Otherwise, the value ranges from 0.8 to 1.2 times the default width of the content card type. If **formType** is set to **TYPE_SMALL**, the value ranges from 0.4 to 1.2 times the default width of the content card type. The unit is vp. If this parameter is not specified, the default height of the content card type is used.|
| handleOnClick | Function | No| - | Callback for the click event. When a user taps the card, the passed callback is executed to implement the custom tap behavior.|

## FormType

Enumerates content card types, including large, medium, and small.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name         | Value| Description               |
|-------------|---|-------------------|
| TYPE_BIG | 0 | 4 × 4. The default card width is 200 vp, and the default height is 200 vp.|
| TYPE_MID | 1 | 4 × 2. The default card width is 200 vp, and the default height is 100 vp.|
| TYPE_SMALL | 2 | 2 × 1. The default card width is 137 vp, and the default height is 83 vp.|

## Example

```ts
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

## Preview

The effect of this example is as follows.<br>
![showContentFormCard](../../ui/figures/showContentFormCard.jpeg)
