# AdsServiceExtensionAbility（系统接口）

```TypeScript
export default class AdsServiceExtensionAbility
```

本模块为设备厂商提供广告扩展能力，设备厂商可自主实现单广告位请求和多广告位请求的业务逻辑。

**起始版本：** 11

<!--Device-unnamed-export default class AdsServiceExtensionAbility--><!--Device-unnamed-export default class AdsServiceExtensionAbility-End-->

**系统能力：** SystemCapability.Advertising.Ads

**系统接口：** 此接口为系统接口。

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止AdsServiceExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { AdsServiceExtensionAbility, RespCallback } from '@kit.AdsKit';
```

## onLoadAd

```TypeScript
onLoadAd(adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, respCallback: RespCallback)
```

单广告位请求业务实现方法，设备厂商需在该方法中实现广告请求业务逻辑并将结果回调给媒体。

**起始版本：** 11

<!--Device-AdsServiceExtensionAbility-onLoadAd(adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, respCallback: RespCallback)--><!--Device-AdsServiceExtensionAbility-onLoadAd(adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, respCallback: RespCallback)-End-->

**系统能力：** SystemCapability.Advertising.Ads

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adParam | [advertising.AdRequestParams](arkts-ads-advertising-adrequestparams-i.md) | 是 | 广告请求参数。 |
| adOptions | [advertising.AdOptions](arkts-ads-advertising-adoptions-i.md) | 是 | 广告配置参数。 |
| respCallback | [RespCallback](arkts-ads-advertising-adsserviceextensionability-respcallback-i.md) | 是 | 广告请求回调。 |

<!--Del-->
**示例**

```TypeScript
import { AdsServiceExtensionAbility, advertising, RespCallback } from '@kit.AdsKit';

export default class AdsExtensionAbility extends AdsServiceExtensionAbility {
  onLoadAd(adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, respCallback: RespCallback) {
    const respData: Map<string, Array<advertising.Advertisement>> = new Map();
    // 设置广告返回数据
    // ...
    respCallback(respData);
  }
}
```

<!--DelEnd-->

## onLoadAdWithMultiSlots

```TypeScript
onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions, 
    respCallback: RespCallback)
```

多广告位请求业务实现方法，设备厂商需在该方法中实现广告请求业务逻辑并将结果回调给媒体。

**起始版本：** 11

<!--Device-AdsServiceExtensionAbility-onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions,     respCallback: RespCallback)--><!--Device-AdsServiceExtensionAbility-onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions,     respCallback: RespCallback)-End-->

**系统能力：** SystemCapability.Advertising.Ads

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adParams | [advertising.AdRequestParams](arkts-ads-advertising-adrequestparams-i.md)[] | 是 | 广告请求参数。 |
| adOptions | [advertising.AdOptions](arkts-ads-advertising-adoptions-i.md) | 是 | 广告配置参数。 |
| respCallback | [RespCallback](arkts-ads-advertising-adsserviceextensionability-respcallback-i.md) | 是 | 广告请求回调。 |

<!--Del-->
**示例**

```TypeScript
import { AdsServiceExtensionAbility, advertising, RespCallback } from '@kit.AdsKit';

export default class AdsExtensionAbility extends AdsServiceExtensionAbility {
  onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions,
    respCallback: RespCallback) {
    const respData: Map<string, Array<advertising.Advertisement>> = new Map();
    // 设置广告返回数据
    // ...
    respCallback(respData);
  }
}
```

<!--DelEnd-->

## 附录

AdsServiceExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
