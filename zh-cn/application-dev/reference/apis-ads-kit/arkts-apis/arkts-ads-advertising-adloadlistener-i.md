# AdLoadListener

单广告位广告请求回调。

**起始版本：** 11

<!--Device-advertising-export interface AdLoadListener--><!--Device-advertising-export interface AdLoadListener-End-->

**系统能力：** SystemCapability.Advertising.Ads

## 导入模块

```TypeScript
import { advertising } from '@kit.AdsKit';
```

<a id="onadloadfailure"></a>
## onAdLoadFailure

```TypeScript
onAdLoadFailure(errorCode: number, errorMsg: string): void
```

广告请求失败回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdLoadListener-onAdLoadFailure(errorCode: number, errorMsg: string): void--><!--Device-AdLoadListener-onAdLoadFailure(errorCode: number, errorMsg: string): void-End-->

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

const adLoaderListener: advertising.AdLoadListener = {
  onAdLoadFailure: (errorCode: number, errorMsg: string) => {
    hilog.error(0x0000, 'testTag', `Failed to load ad. Code is ${errorCode}, message is ${errorMsg}`);
  },
  onAdLoadSuccess: (ads: Array<advertising.Advertisement>) => {
    hilog.info(0x0000, 'testTag', 'Succeeded in loading ad');
  }
}

```

<a id="onadloadsuccess"></a>
## onAdLoadSuccess

```TypeScript
onAdLoadSuccess(ads: Array<Advertisement>): void
```

广告请求成功后回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdLoadListener-onAdLoadSuccess(ads: Array<Advertisement>): void--><!--Device-AdLoadListener-onAdLoadSuccess(ads: Array<Advertisement>): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ads | Array&lt;Advertisement&gt; | 是 | 广告数据。 |

**示例：**

```TypeScript
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const adLoaderListener: advertising.AdLoadListener = {
  onAdLoadFailure: (errorCode: number, errorMsg: string) => {
    hilog.error(0x0000, 'testTag', `Failed to load ad. Code is ${errorCode}, message is ${errorMsg}`);
  },
  onAdLoadSuccess: (ads: Array<advertising.Advertisement>) => {
    hilog.info(0x0000, 'testTag', 'Succeeded in loading ad');
  }
}

```

