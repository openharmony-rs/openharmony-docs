# AutoAdComponent

本模块提供展示轮播广告的能力。

**起始版本：** 11

**装饰器类型：** @Component

**系统能力：** SystemCapability.Advertising.Ads

## 导入模块

```TypeScript
import { AutoAdComponent } from '@kit.AdsKit';
```

## build

```TypeScript
build(): void
```

用于创建AutoAdComponent对象的构造函数。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

## adOptions

```TypeScript
adOptions: advertising.AdOptions
```

广告配置参数。

**类型：** [advertising.AdOptions](arkts-ads-advertising-adoptions-i.md)

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

## adParam

```TypeScript
adParam: advertising.AdRequestParams
```

广告请求参数。

**类型：** [advertising.AdRequestParams](arkts-ads-advertising-adrequestparams-i.md)

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

## displayOptions

```TypeScript
displayOptions: advertising.AdDisplayOptions
```

广告展示参数。

**类型：** [advertising.AdDisplayOptions](arkts-ads-advertising-addisplayoptions-i.md)

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

## interactionListener

```TypeScript
interactionListener: advertising.AdInteractionListener
```

广告状态变化回调。

**类型：** [advertising.AdInteractionListener](arkts-ads-advertising-adinteractionlistener-i.md)

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Advertising.Ads
