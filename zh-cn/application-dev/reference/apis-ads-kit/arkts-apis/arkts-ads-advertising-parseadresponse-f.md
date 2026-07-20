# parseAdResponse

## 导入模块

```TypeScript
import { advertising } from '@kit.AdsKit';
```

<a id="parseadresponse"></a>
## parseAdResponse

```TypeScript
function parseAdResponse(adResponse: string, listener: MultiSlotsAdLoadListener, context: common.UIAbilityContext): void
```

解析并处理广告响应体（该接口仅对部分系统预置应用开放）。

**起始版本：** 12

<!--Device-advertising-function parseAdResponse(adResponse: string, listener: MultiSlotsAdLoadListener, context: common.UIAbilityContext): void--><!--Device-advertising-function parseAdResponse(adResponse: string, listener: MultiSlotsAdLoadListener, context: common.UIAbilityContext): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adResponse | string | 是 | 广告响应体。 |
| listener | [MultiSlotsAdLoadListener](arkts-ads-advertising-multislotsadloadlistener-i.md) | 是 | 请求广告回调监听。 |
| context | common.UIAbilityContext | 是 | UIAbility的上下文环境。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter.Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Device not supported. |
| [21800001](../errorcode-ads.md#21800001-系统内部错误) | System internal error. |
| [21800005](../errorcode-ads.md#21800005-广告数据解析失败) | Failed to parse the ad response. |

**示例：**

其中context的获取方式参见[各类context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

function parseAdResponse(adResponse: string, context: common.UIAbilityContext): void {
  // 广告解析处理回调监听
  const multiSlotsAdLoaderListener: advertising.MultiSlotsAdLoadListener = {
    onAdLoadFailure: (errorCode: number, errorMsg: string) => {
      hilog.error(0x0000, 'testTag', `Failed to load multiSlots ad. Code is ${errorCode}, message is ${errorMsg}`);
    },
    onAdLoadSuccess: (ads: Map<string, Array<advertising.Advertisement>>) => {
      hilog.info(0x0000, 'testTag', 'Succeeded in loading multiSlots ad');
      // 保存解析处理完成的广告内容用于展示
      const returnAds: advertising.Advertisement[] = [];
      ads.forEach((adsArray) => returnAds.push(...adsArray));
    }
  };
  // 调用响应体解析接口
  advertising.parseAdResponse(adResponse, multiSlotsAdLoaderListener, context);
}

```

