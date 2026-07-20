# AdRequestParams

广告请求参数。

**起始版本：** 11

<!--Device-advertising-export interface AdRequestParams--><!--Device-advertising-export interface AdRequestParams-End-->

**系统能力：** SystemCapability.Advertising.Ads

## 导入模块

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## adCount

```TypeScript
adCount?: number
```

请求的广告数量。不填以业务逻辑为准。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdRequestParams-adCount?: number--><!--Device-AdRequestParams-adCount?: number-End-->

**系统能力：** SystemCapability.Advertising.Ads

## adHeight

```TypeScript
adHeight?: number
```

请求广告时期望的创意高度，单位vp（横幅广告必填）。不填以业务逻辑为准。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdRequestParams-adHeight?: number--><!--Device-AdRequestParams-adHeight?: number-End-->

**系统能力：** SystemCapability.Advertising.Ads

## adId

```TypeScript
adId: string
```

广告位ID。

说明：getAdRequestBody接口可以不传该参数。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdRequestParams-adId: string--><!--Device-AdRequestParams-adId: string-End-->

**系统能力：** SystemCapability.Advertising.Ads

## adSearchKeyword

```TypeScript
adSearchKeyword?: string
```

广告关键字。不填默认""。

说明：暂不支持使用。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdRequestParams-adSearchKeyword?: string--><!--Device-AdRequestParams-adSearchKeyword?: string-End-->

**系统能力：** SystemCapability.Advertising.Ads

## adType

```TypeScript
adType?: number
```

请求的广告类型。

- 1：开屏广告。  
- 3：原生广告。  
- 7：激励广告。  
- 8：横幅广告。  
- 12：插屏广告。  
- 60：贴片广告。

不填默认为原生广告类型。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdRequestParams-adType?: number--><!--Device-AdRequestParams-adType?: number-End-->

**系统能力：** SystemCapability.Advertising.Ads

## adWidth

```TypeScript
adWidth?: number
```

请求广告时期望的创意宽度，单位vp（横幅广告必填）。不填以业务逻辑为准。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdRequestParams-adWidth?: number--><!--Device-AdRequestParams-adWidth?: number-End-->

**系统能力：** SystemCapability.Advertising.Ads

## key

```TypeScript
[key: string]: number | boolean | string | undefined
```

自定义参数。

<!--RP2--><!--RP2End-->

**类型：** number \| boolean \| string \| undefined

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdRequestParams-[key: string]: number | boolean | string | undefined--><!--Device-AdRequestParams-[key: string]: number | boolean | string | undefined-End-->

**系统能力：** SystemCapability.Advertising.Ads

