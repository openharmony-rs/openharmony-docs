# MultiSlotsAdLoadListener

多广告位广告请求回调。

**起始版本：** 11

**系统能力：** SystemCapability.Advertising.Ads

## onAdLoadFailure

```TypeScript
onAdLoadFailure(errorCode: number, errorMsg: string): void
```

广告请求失败回调。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errorCode | number | 是 | 广告请求失败的错误码。 |
| errorMsg | string | 是 | 广告请求失败的错误信息。 |

**示例：**

```TypeScript
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const multiSlotsAdLoadListener: advertising.MultiSlotsAdLoadListener = {
  onAdLoadFailure: (errorCode: number, errorMsg: string) => {
    hilog.error(0x0000, 'testTag', `Failed to load ad. Code is ${errorCode}, message is ${errorMsg}`);
  },
  onAdLoadSuccess: (adsMap: Map<string, Array<advertising.Advertisement>>) => {
    hilog.info(0x0000, 'testTag', 'Succeeded in loading ad');
  }
}

```

## onAdLoadSuccess

```TypeScript
onAdLoadSuccess(adsMap: Map<string, Array<Advertisement>>): void
```

多广告位广告请求成功后回调。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adsMap | Map&lt;string, Array&lt;Advertisement&gt;&gt; | 是 | 广告数据，是以广告位ID为键，存储请求到的广告内容的映射集合。 |

**示例：**

```TypeScript
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const multiSlotsAdLoadListener: advertising.MultiSlotsAdLoadListener = {
  onAdLoadFailure: (errorCode: number, errorMsg: string) => {
    hilog.error(0x0000, 'testTag', `Failed to load ad. Code is ${errorCode}, message is ${errorMsg}`);
  },
  onAdLoadSuccess: (adsMap: Map<string, Array<advertising.Advertisement>>) => {
    hilog.info(0x0000, 'testTag', 'Succeeded in loading ad');
  }
}

```

