# Content Cards Based on Uniform Data Structs (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=fadd7d812e259ee0411353f410f7f8f5e48ebdff translatedAt=2026-09-01T02:10:34.224Z pushedAt=2026-09-01T11:35:27.068Z -->

## When to Use

Preset cards provided by the system allow you to quickly display data of uniform data structs.

## Content Card

When you need to display content, such as a title, description, image, and app information, and redirect users to the corresponding source when they tap the content, you can use a content card to quickly present the information. Simply call [ContentFormCard](../reference/apis-arkdata/js-apis-data-UdmfComponents.md#contentformcard) and pass in [ContentForm](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#contentform14) data, the card width and height, and a callback for the tap event to achieve a good display effect.

Starting from API version 20, you can use the content card component [UdmfComponents](../reference/apis-arkdata/js-apis-data-UdmfComponents.md).

### Available APIs

The following table describes the **ContentFormCard** API.

| Name                                                                                   | Description                                         |
|-----------------------------------------------------------------------------------------|---------------------------------------------|
| ContentFormCard({contentFormData: uniformDataStruct.ContentForm, formType: FormType, formWidth?: number, formHeight?: number, handleOnClick?: Function}) | Displays the passed content card data in a fixed style, invokes the callback upon a tap, and redirects to the configured page.|

### How to Develop

<!-- @[components_based_on_uniform_data_structure](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/ContentForm/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// 1. Import required modules.
import { ContentFormCard, FormType, uniformDataStruct } from '@kit.ArkData';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State contentForm: uniformDataStruct.ContentForm = {
    uniformDataType: 'general.content-form',
    title: ''
  };
  @State startToShow: boolean = false;

  aboutToAppear(): void {
    // 2. Initialize data.
    this.initData();
  }

  async initData() {
    let context = this.getUIContext().getHostContext();
    if (!context) {
      return;
    }
    try {
      let appIcon = await context.resourceManager.getMediaContent($r('app.media.startIcon').id);
      let thumbImage = await context.resourceManager.getMediaContent($r('app.media.foreground').id);
      this.contentForm = {
        uniformDataType: 'general.content-form',
        title: 'Content form title',
        thumbData: thumbImage,
        description: 'Content form description',
        appIcon: appIcon,
        appName: 'com.test.demo'
      };
    } catch (err) {
      hilog.error(0xFF00, '[Sample_Udmf]', 'Init data error');
    }
  }

  build() {
    Column() {
      Button('show card').fontSize(30)
        .onClick(() => {
          // 3. startToShow is changed to true upon a tap, and the page is re-rendered.
          this.startToShow = true;
        })
      if (this.startToShow) {
        // 4. Pass in corresponding parameters to the ContentFormCard API.
        ContentFormCard({
          contentFormData: this.contentForm,
          formType: FormType.TYPE_SMALL,
          formWidth: 220,
          formHeight: 100,
          handleOnClick: () => {
            hilog.info(0xFF00, '[Sample_Udmf]', 'Clicked card');
          }
        })
      }
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```