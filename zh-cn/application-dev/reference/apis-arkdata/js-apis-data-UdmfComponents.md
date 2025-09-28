# @ohos.data.UdmfComponents(内容卡片)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

针对[ContentForm](js-apis-data-uniformDataStruct.md#contentform14)标准数据结构的内容卡片，支持设置标题（必选）、描述、应用图标、应用名称、跳转链接、内容图片。用户点击卡片时，执行传入的回调事件函数，若设置的跳转链接不为空，则跳转到指定的页面。

> **说明：**
>
> 该组件从API Version 20开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 导入模块

```js
import { ContentFormCard, FormType } from '@kit.ArkData';
```

## 子组件

无

## ContentFormCard

ContentFormCard({contentFormData: uniformDataStruct.ContentForm, formType: FormType, formWidth?: number, formHeight?: number, handleOnClick?: Function})

内容卡片控件，用于在应用内展示标题、描述、内容图片、应用信息等。

**装饰器类型：**\@Component

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

| 名称 | 类型 | 必填 | 装饰器类型 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| contentFormData | [uniformDataStruct.ContentForm](js-apis-data-uniformDataStruct.md#contentform14) | 是 | - | 内容卡片数据。 |
| formType | [FormType](#formtype) | 是 | @Prop | 内容卡片类型，影响内容卡片的大小。 |
| formWidth | number | 否 | @Prop | 卡片宽度，其范围在设置的内容卡片类型默认宽度的0.8 ~ 1.2倍之间，当formType为TYPE_SMALL时，其范围在设置的内容卡片类型默认宽度的0.4 ~ 1.2倍之间。 |
| formHeight | number | 否 | @Prop | 卡片高度，当contentFormData中的title为空字符串时，卡片高度为传入的值，否则其范围在设置的内容卡片类型默认宽度的0.8 ~ 1.2倍之间，当formType为TYPE_SMALL时，其范围在设置的内容卡片类型默认宽度的0.4 ~ 1.2倍之间。 |
| handleOnClick | Function | 否 | - | 点击事件回调函数。 |

## FormType

内容卡片类型枚举，提供了大、中、小三种尺寸。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

| 名称          | 值 | 说明                |
|-------------|---|-------------------|
| TYPE_BIG | 0 | 表示 4 x 4 的尺寸。默认卡片宽度为200，默认高度为200。 |
| TYPE_MID | 1 | 表示 4 x 2 的尺寸。默认卡片宽度为200，默认高度为100。 |
| TYPE_SMALL | 2 | 表示 2 x 1 的尺寸。默认卡片宽度为137， 默认高度为83。 |

## 示例

```ts
import { uniformDataStruct } from '@kit.ArkData'

@Entry
@Component
struct Index {
  @State contentForm: uniformDataStruct.ContentForm = {
    uniformDataType: 'general.content-form',
    title: ''
  };
  @State startToShow: boolean = false;

  aboutToAppear(): void {
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
        title: "Content form title",
        thumbData: appIcon,
        description: "Content form description",
        appIcon: thumbImage,
        appName: "com.test.demo"
      };
    } catch (err) {
      console.error("Init data error");
    }
  }

  build() {
    Column() {
      Button('show card')
        .onClick(() => {
          this.startToShow = true;
        })
      if (this.startToShow) {
        ContentFormCard({
          contentFormData: this.contentForm,
          formType: FormType.TYPE_SMALL,
          formWidth: 110,
          formHeight: 50,
          handleOnClick: () => {
            console.info("Clicked card");
          }
        })
      }
    }
  }
}
```

