# RespCallback

广告请求回调。

**起始版本：** 11

**系统能力：** SystemCapability.Advertising.Ads

## 导入模块

```TypeScript
import { AdsServiceExtensionAbility, RespCallback } from '@kit.AdsKit';
```

## [[Call]]

```TypeScript
(respData: Map<string, Array<advertising.Advertisement>>): void
```

广告请求回调。

**起始版本：** 11

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| respData | Map & lt;string, Array & lt;advertising.Advertisement & gt; & gt; | 是 | 广告请求回调数据，是以广告位ID为键， 存储请求到的广告内容的映射集合。 |

**示例**

```TypeScript
import { advertising, RespCallback } from '@kit.AdsKit';

function setRespCallback(respCallback: RespCallback) {
  const respData: Map<string, Array<advertising.Advertisement>> = new Map();
  // 设置广告返回数据
  // ...
  respCallback(respData);
}
```
