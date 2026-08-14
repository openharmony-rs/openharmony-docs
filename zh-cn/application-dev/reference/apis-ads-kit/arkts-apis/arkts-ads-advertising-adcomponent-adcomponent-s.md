# AdComponent

本模块提供展示广告的能力，覆盖了原生、贴片、开屏等广告样式。 > **说明：** > > 为了保证广告能正确展示，该接口必须和请求广告接口配套使用。效果和使用方法可参考 > [原生广告](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ads-publisher-service-native)、 > [贴片广告](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ads-publisher-service-roll)、 > [开屏广告](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ads-publisher-service-splash) > 接入和展示。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-declare struct AdComponent--><!--Device-unnamed-declare struct AdComponent-End-->

**系统能力：** SystemCapability.Advertising.Ads

## build

```TypeScript
build(): void
```

用于创建AdComponent对象的构造函数。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdComponent-build(): void--><!--Device-AdComponent-build(): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

## adRenderer

```TypeScript
@BuilderParam
  adRenderer?: () => void
```

应用自渲染广告样式。应用自渲染广告样式为受限使用能力，具体请前往 [流量变现官网客服支持](https://developer.huawei.com/consumer/cn/doc/monetize/kefuzhichi-0000001104461922)进行咨询。

**类型：** () =&gt; void

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AdComponent-@BuilderParam  adRenderer?: () => void--><!--Device-AdComponent-@BuilderParam  adRenderer?: () => void-End-->

**系统能力：** SystemCapability.Advertising.Ads

## ads

```TypeScript
ads: advertising.Advertisement[]
```

广告对象数组。 说明：非贴片广告类型，组件只展示数组第一个数据。

**类型：** advertising.Advertisement[]

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdComponent-ads: advertising.Advertisement[]--><!--Device-AdComponent-ads: advertising.Advertisement[]-End-->

**系统能力：** SystemCapability.Advertising.Ads

## displayOptions

```TypeScript
displayOptions: advertising.AdDisplayOptions
```

广告展示参数。

**类型：** advertising.AdDisplayOptions

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdComponent-displayOptions: advertising.AdDisplayOptions--><!--Device-AdComponent-displayOptions: advertising.AdDisplayOptions-End-->

**系统能力：** SystemCapability.Advertising.Ads

## interactionListener

```TypeScript
interactionListener: advertising.AdInteractionListener
```

广告状态变化回调。

**类型：** advertising.AdInteractionListener

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdComponent-interactionListener: advertising.AdInteractionListener--><!--Device-AdComponent-interactionListener: advertising.AdInteractionListener-End-->

**系统能力：** SystemCapability.Advertising.Ads

## rollPlayState

```TypeScript
@Prop
  rollPlayState?: number
```

用于对外提供贴片广告播放状态，设置1为播放，2为暂停，默认值为2，其他值为非法值，不改变之前的播放状态。 在贴片广告所在页面需要通过@State关联属性，使用方法参考 [示例代码](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ads-publisher-service-roll#展示广告)。

**类型：** number

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AdComponent-@Prop  rollPlayState?: number--><!--Device-AdComponent-@Prop  rollPlayState?: number-End-->

**系统能力：** SystemCapability.Advertising.Ads

