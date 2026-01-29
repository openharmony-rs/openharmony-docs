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
> - 本模块接口仅可在Stage模型下使用。
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 20开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 导入模块

```js
import { ContentFormCard, FormType } from '@kit.ArkData';
import uniformDataStruct from '@ohos.data.uniformDataStruct';
import { PropRef } from '@ohos.arkui.stateManagement';
import { Component, Builder } from '@ohos.arkui.component';
```

## 子组件

无

## ContentFormCard

ArkTS-Dyn: ContentFormCard({contentFormData: uniformDataStruct.ContentForm, formType: FormType, formWidth?: number, formHeight?: number, handleOnClick?: Function})

ArkTS-Sta: ContentFormCard({contentFormData: uniformDataStruct.ContentForm, formType: FormType, formWidth?: double, formHeight?: double, handleOnClick?: Function, build(): void})

内容卡片控件，用于在应用内展示标题、描述、内容图片、应用信息等。

**装饰器类型：**\@Component

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 必填 | 装饰器类型 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| contentFormData | [uniformDataStruct.ContentForm](js-apis-data-uniformDataStruct.md#contentform14) | 是 | - | 内容卡片数据。 |
| formType | [FormType](#formtype) | 是 | @Prop | 内容卡片类型，影响内容卡片的大小。 |
| formWidth | ArkTS-Dyn: number  <br/>ArkTS-Sta: double | 否 | @Prop | 卡片宽度，其范围在设置的内容卡片类型默认宽度的0.8 ~ 1.2倍之间，当formType为TYPE_SMALL时，其范围在设置的内容卡片类型默认宽度的0.4 ~ 1.2倍之间。 |
| formHeight | ArkTS-Dyn: number  <br/>ArkTS-Sta: double | 否 | @Prop | 卡片高度，当contentFormData中的title为空字符串时，卡片高度为传入的值，否则其范围在设置的内容卡片类型默认宽度的0.8 ~ 1.2倍之间，当formType为TYPE_SMALL时，其范围在设置的内容卡片类型默认宽度的0.4 ~ 1.2倍之间。 |
| handleOnClick | Function | 否 | - | 点击事件回调函数。 |
| build | void | 是 | @Builder | 构建函数，用于绘制组件。<br>**ArkTS模式：**  该接口仅适用于ArkTS-Sta。|

## FormType

内容卡片类型枚举，提供了大、中、小三种尺寸。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

| 名称          | 值 | 说明                |
|-------------|---|-------------------|
| TYPE_BIG | 0 | 表示 4 x 4 的尺寸。默认卡片宽度为200，默认高度为200。 |
| TYPE_MID | 1 | 表示 4 x 2 的尺寸。默认卡片宽度为200，默认高度为100。 |
| TYPE_SMALL | 2 | 表示 2 x 1 的尺寸。默认卡片宽度为137， 默认高度为83。 |

```ts
import { State, Prop, Watch } from '@ohos.arkui.stateManagement'
import { FormType, ContentFormCard } from '@ohos.data.UdmfComponents';
import common from '@ohos.app.ability.common';
import { uniformDataStruct } from '@kit.ArkData';
import { Entry, Component, State, UIContext, Column, $rawfile, Flex, Row, Text, List, BusinessError, Button, UniformDataType, Image, $r, HorizontalAlign, ColumnOptions } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State contentForms: Array<uniformDataStruct.ContentForm> = new Array<uniformDataStruct.ContentForm>();
  @State formWidth = 200;
  @State formType: FormType = FormType.TYPE_SMALL;

  aboutToAppear(): void {
    this.initData();
  }

  async initData() {
    let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
    try {
      let appIcon = await context.resourceManager.getMediaContent($r('sys.media.ohos_app_icon').id);
      let thumb2 = await context.resourceManager.getMediaContent($r('app.media.thumb2').id);
      this.contentForms.push({
        uniformDataType: 'general.content-form',
        title: 'Content form title',
        thumbData: thumb2,
        description: 'Content form description',
        appName: 'com.test.demo',
        linkUri: 'https://appgallery.huawei.com/app/detail?id=com.huawei.hmos.wallet',
        appIcon: appIcon
      })
    } catch (err) {
      console.info(`failed getMediaContent.`);
    }
  }

  build() {
    Column({ space: 10 } as ColumnOptions) {
      if (this.contentForms.length > 0) {
        ContentFormCard({
          contentFormData: this.contentForms[0],
          formType: FormType.TYPE_SMALL,
          formWidth: this.formWidth
        })
      }
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#15000000')
    .alignItems(HorizontalAlign.Start)
  }
}
```
