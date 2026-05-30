# @ohos.advertising.AdComponent (广告展示组件)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

本模块提供展示广告的能力，覆盖了原生、贴片、开屏等广告样式。


> **说明：**
> 
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```typescript
import { AdComponent } from '@kit.AdsKit';
```

## AdComponent

```typescript
AdComponent({
  ads: advertising.Advertisement[], 
  displayOptions: advertising.AdDisplayOptions,
  interactionListener: advertising.AdInteractionListener,
  @BuilderParam adRenderer?: () => void,   
  @Prop rollPlayState?: number
})
```

广告展示组件，提供展示原生、贴片、开屏等广告的能力。

**装饰器类型：**\@Component

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| ads                         | advertising.[Advertisement](js-apis-advertising.md#advertisement)[]               | 是   | 广告对象数组。<br/>说明：非贴片广告类型，组件只展示数组第一个数据。<br/>元服务API：从API version 12开始，该接口支持在元服务中使用。                                                                                                            |
| displayOptions              | advertising.[AdDisplayOptions](js-apis-advertising.md#addisplayoptions)           | 是   | 广告展示参数。<br/>元服务API：从API version 12开始，该接口支持在元服务中使用。                                                                                                            |
| interactionListener         | advertising.[AdInteractionListener](js-apis-advertising.md#adinteractionlistener) | 是   | 广告状态变化回调。<br/>元服务API：从API version 12开始，该接口支持在元服务中使用。                                                                                                        |
| adRenderer<sup>12+</sup>    | () =&gt; void                                                                        | 否   | 应用自渲染广告样式。应用自渲染广告样式为受限使用能力，具体请前往[流量变现官网客服支持](https://developer.huawei.com/consumer/cn/doc/monetize/kefuzhichi-0000001104461922)进行咨询。<br/>元服务API：从API version 20开始，该接口支持在元服务中使用。<br/>装饰器类型：\@BuilderParam   |
| rollPlayState<sup>15+</sup> | number                                                                            | 否   | 用于对外提供贴片广告播放状态，设置1为播放，2为暂停，默认值为2，其他值为非法值，不改变之前的播放状态。在贴片广告所在页面需要通过\@State关联属性，使用方法参考[示例代码](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ads-publisher-service-roll#展示广告)。<br/>元服务API：从API version 20开始，该接口支持在元服务中使用。<br/>装饰器类型：\@Prop  |

> **说明：**
> 
> 为了保证广告能正确展示，该接口必须和请求广告接口配套使用。效果和使用方法可参考[原生广告](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ads-publisher-service-native)、[贴片广告](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ads-publisher-service-roll)、[开屏广告](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ads-publisher-service-splash)接入和展示。

**示例：**

```typescript
import { AdComponent, advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  // 请求到的广告内容
  private ads: advertising.Advertisement[] = [];
  // 广告展示参数
  private adDisplayOptions: advertising.AdDisplayOptions = {};

  build() {
    Column() {
      AdComponent({
        ads: this.ads,
        displayOptions: this.adDisplayOptions,
        interactionListener: {
          onStatusChanged: (status: string, ad: advertising.Advertisement, data: string) => {
            switch (status) {
              case 'onAdOpen':
                hilog.info(0x0000, 'testTag', 'onAdOpen');
                break;
              case 'onAdClick':
                hilog.info(0x0000, 'testTag', 'onAdClick');
                break;
              case 'onAdClose':
                hilog.info(0x0000, 'testTag', 'onAdClose');
                break;
            }
          }
        }
      })
        .width('100%')
        .height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```


### build


build(): void


用于创建AdComponent对象的构造函数。


**元服务API：** 从API version 12开始，该接口支持在元服务中使用。


**系统能力：** SystemCapability.Advertising.Ads