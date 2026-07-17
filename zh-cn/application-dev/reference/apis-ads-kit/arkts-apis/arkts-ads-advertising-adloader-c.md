# AdLoader

提供加载广告的功能。

**起始版本：** 11

<!--Device-advertising-export class AdLoader--><!--Device-advertising-export class AdLoader-End-->

**系统能力：** SystemCapability.Advertising.Ads

## 导入模块

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## constructor

```TypeScript
constructor(context: common.Context)
```

构造函数。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdLoader-constructor(context: common.Context)--><!--Device-AdLoader-constructor(context: common.Context)-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | common.Context | 是 | ability或application的上下文环境。 |

**示例：**

其中context的获取方式参见[各类context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
// ...

function createAdLoader(context: common.Context): void {
  const adLoader: advertising.AdLoader = new advertising.AdLoader(context);
}

```

## loadAd

```TypeScript
loadAd(adParam: AdRequestParams, adOptions: AdOptions, listener: AdLoadListener): void
```

请求单广告位广告。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdLoader-loadAd(adParam: AdRequestParams, adOptions: AdOptions, listener: AdLoadListener): void--><!--Device-AdLoader-loadAd(adParam: AdRequestParams, adOptions: AdOptions, listener: AdLoadListener): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adParam | [AdRequestParams](arkts-ads-advertising-adrequestparams-i.md) | 是 | 广告请求参数。 |
| adOptions | [AdOptions](arkts-ads-advertising-adoptions-i.md) | 是 | 广告配置参数。 |
| listener | [AdLoadListener](arkts-ads-advertising-adloadlistener-i.md) | 是 | 请求广告回调监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3.Parameter verification failed |
| [21800001](../errorcode-ads.md#21800001-系统内部错误) | System internal error. |
| [21800003](../errorcode-ads.md#21800003-广告请求加载失败) | Failed to load the ad request. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Device not supported.<br>**适用版本：** 12+ |

**示例：**

其中context的获取方式参见[各类context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// ...
function loadAd(context: common.Context, adRequestParams: advertising.AdRequestParams): void {
  // 广告配置参数，开发者可根据项目实际情况设置
  const adOptions: advertising.AdOptions = {};
  // 广告请求回调监听
  const adLoaderListener: advertising.AdLoadListener = {
    onAdLoadFailure: (errorCode: number, errorMsg: string) => {
      hilog.error(0x0000, 'testTag', `Failed to load ad. Code is ${errorCode}, message is ${errorMsg}`);
    },
    onAdLoadSuccess: (ads: Array<advertising.Advertisement>) => {
      hilog.info(0x0000, 'testTag', 'Succeeded in loading ad');
      // 保存请求到的广告内容用于展示
      const returnAds: advertising.Advertisement[] = ads;
    }
  };
  // 创建AdLoader广告对象
  const adLoader: advertising.AdLoader = new advertising.AdLoader(context);
  // 调用广告请求接口
  adLoader.loadAd(adRequestParams, adOptions, adLoaderListener);
}

```

## loadAdWithMultiSlots

```TypeScript
loadAdWithMultiSlots(adParams: AdRequestParams[], adOptions: AdOptions, listener: MultiSlotsAdLoadListener): void
```

请求多广告位广告。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdLoader-loadAdWithMultiSlots(adParams: AdRequestParams[], adOptions: AdOptions, listener: MultiSlotsAdLoadListener): void--><!--Device-AdLoader-loadAdWithMultiSlots(adParams: AdRequestParams[], adOptions: AdOptions, listener: MultiSlotsAdLoadListener): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adParams | [AdRequestParams](arkts-ads-advertising-adrequestparams-i.md)[] | 是 | 广告请求参数。 |
| adOptions | [AdOptions](arkts-ads-advertising-adoptions-i.md) | 是 | 广告配置参数。 |
| listener | [MultiSlotsAdLoadListener](arkts-ads-advertising-multislotsadloadlistener-i.md) | 是 | 请求广告回调监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3.Parameter verification failed |
| [21800001](../errorcode-ads.md#21800001-系统内部错误) | System internal error. |
| [21800003](../errorcode-ads.md#21800003-广告请求加载失败) | Failed to load the ad request. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Device not supported.<br>**适用版本：** 12+ |

**示例：**

其中context的获取方式参见[各类context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// ...
function loadAdWithMultiSlots(context: common.Context, adRequestParamsArray: advertising.AdRequestParams[]): void {
  // 广告配置参数，开发者可根据项目实际情况设置
  const adOptions: advertising.AdOptions = {};
  // 广告请求回调监听
  const multiSlotsAdLoaderListener: advertising.MultiSlotsAdLoadListener = {
    onAdLoadFailure: (errorCode: number, errorMsg: string) => {
      hilog.error(0x0000, 'testTag', `Failed to load multiSlots ad. Code is ${errorCode}, message is ${errorMsg}`);
    },
    onAdLoadSuccess: (ads: Map<string, Array<advertising.Advertisement>>) => {
      hilog.info(0x0000, 'testTag', 'Succeeded in loading multiSlots ad');
      // 保存请求到的广告内容用于展示
      const returnAds: advertising.Advertisement[] = [];
      ads.forEach((adsArray) => returnAds.push(...adsArray));
    }
  };
  // 创建AdLoader广告对象
  const adLoader: advertising.AdLoader = new advertising.AdLoader(context);
  // 调用广告请求接口
  adLoader.loadAdWithMultiSlots(adRequestParamsArray, adOptions, multiSlotsAdLoaderListener);
}

```

