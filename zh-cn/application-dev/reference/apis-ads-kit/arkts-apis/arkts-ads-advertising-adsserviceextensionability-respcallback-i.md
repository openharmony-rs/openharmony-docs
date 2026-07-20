# RespCallback

广告请求回调。

**起始版本：** 11

<!--Device-unnamed-export interface RespCallback--><!--Device-unnamed-export interface RespCallback-End-->

**系统能力：** SystemCapability.Advertising.Ads

## 导入模块

```TypeScript
import { RespCallback } from '@kit.AdsKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
(respData: Map<string, Array<advertising.Advertisement>>): void
```

广告请求回调。

**起始版本：** 11

<!--Device-RespCallback-(respData: Map<string, Array<advertising.Advertisement>>): void--><!--Device-RespCallback-(respData: Map<string, Array<advertising.Advertisement>>): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| respData | Map&lt;string, Array&lt;advertising.Advertisement&gt;&gt; | 是 | 广告请求回调数据，是以广告位ID为键，存储请求到的广告内容的映射集合。 |

