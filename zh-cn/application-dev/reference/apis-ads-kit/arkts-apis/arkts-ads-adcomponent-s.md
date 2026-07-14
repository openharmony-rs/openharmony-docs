# AdComponent

本模块提供展示广告的能力，覆盖了原生、贴片、开屏等广告样式。

**起始版本：** 11

**系统能力：** SystemCapability.Advertising.Ads

## build

```TypeScript
build(): void
```

用于创建AdComponent对象的构造函数。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## adRenderer

```TypeScript
adRenderer?: () => void
```

应用自渲染广告样式。应用自渲染广告样式为受限使用能力，具体请前往
[流量变现官网客服支持](https://developer.huawei.com/consumer/cn/doc/monetize/kefuzhichi-0000001104461922)进行咨询。

**类型：** () => void

**起始版本：** 12

**装饰器类型：** @BuilderParam

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## ads

```TypeScript
ads: advertising.Advertisement[]
```

广告对象数组。

说明：非贴片广告类型，组件只展示数组第一个数据。

**类型：** advertising.Advertisement[]

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## displayOptions

```TypeScript
displayOptions: advertising.AdDisplayOptions
```

广告展示参数。

**类型：** advertising.AdDisplayOptions

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## interactionListener

```TypeScript
interactionListener: advertising.AdInteractionListener
```

广告状态变化回调。

**类型：** advertising.AdInteractionListener

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## rollPlayState

```TypeScript
rollPlayState?: number
```

用于对外提供贴片广告播放状态，设置1为播放，2为暂停，默认值为2，其他值为非法值，不改变之前的播放状态。
在贴片广告所在页面需要通过@State关联属性，使用方法参考
[示例代码](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ads-publisher-service-roll#展示广告)。

**类型：** number

**起始版本：** 15

**装饰器类型：** @Prop

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

