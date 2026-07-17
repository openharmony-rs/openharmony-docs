# MultiSlotsAdLoadListener

多广告位广告请求回调。

**起始版本：** 11

<!--Device-advertising-export interface MultiSlotsAdLoadListener--><!--Device-advertising-export interface MultiSlotsAdLoadListener-End-->

**系统能力：** SystemCapability.Advertising.Ads

## 导入模块

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## onAdLoadFailure

```TypeScript
onAdLoadFailure(errorCode: number, errorMsg: string): void
```

广告请求失败回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MultiSlotsAdLoadListener-onAdLoadFailure(errorCode: number, errorMsg: string): void--><!--Device-MultiSlotsAdLoadListener-onAdLoadFailure(errorCode: number, errorMsg: string): void-End-->

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MultiSlotsAdLoadListener-onAdLoadSuccess(adsMap: Map<string, Array<Advertisement>>): void--><!--Device-MultiSlotsAdLoadListener-onAdLoadSuccess(adsMap: Map<string, Array<Advertisement>>): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adsMap | [Map](../../apis-arkts/arkts-apis/arkts-arkts-collections-map-c.md)<string, Array<Advertisement>> | 是 | 广告数据，是以广告位ID为键，存储请求到的广告内容的映射集合。 |

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

