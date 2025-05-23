# @ohos.advertising.AdsServiceExtensionAbility (广告扩展服务)

本模块为设备厂商提供广告扩展能力，设备厂商可自主实现请求广告的回调。

> **说明：**<br/>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { RespCallback } from '@kit.AdsKit';
```

## RespCallback

### (respData: Map&lt;string, Array&lt;advertising.Advertisement&gt;&gt;)

(respData: Map&lt;string, Array&lt;advertising.Advertisement&gt;&gt;): void

广告请求回调。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名   | 类型                                                                                              | 必填 | 说明              |
|----------|---------------------------------------------------------------------------------------------------|-----|-----------------|
| respData | Map&lt;string, Array&lt;advertising.[Advertisement](js-apis-advertising.md#advertisement)&gt;&gt; | 是   | 广告请求回调数据。 |

**示例：**

```ts
import { advertising, RespCallback } from '@kit.AdsKit';

function setRespCallback(respCallback: RespCallback) {
    const ads: Array<advertising.Advertisement> = [];
    const rewardVerifyConfig: Map<string, string> = new Map();
    ads.push({
        adType: 7,
        uniqueId: '111111',
        rewardVerifyConfig: rewardVerifyConfig,
        rewarded: false,
        shown: false,
        clicked: false
    })
    const slot: string = 'test';
    const respData: Map<string, Array<advertising.Advertisement>> = new Map();
    respData.set(slot, ads);
    respCallback(respData);
}
```