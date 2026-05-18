# advertisement (广告内容)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->


本模块为请求的广告内容。


> **说明：**
> 
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```typescript
import { advertising } from '@kit.AdsKit';
```

## Advertisement

请求的广告内容。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

| 名称 | 类型 | 只读 | 可选 | 说明 | 
| -------- | -------- | -------- | -------- | -------- |
| adType | number | 否 | 否 | 广告类型。<br/>- 1：开屏广告。<br/>- 3：原生广告。<br/>- 7：激励广告。<br/>- 8：横幅广告。<br/>- 12：插屏广告。<br/>- 60：贴片广告。<br/>不填默认为原生广告类型。 | 
| uniqueId | string | 否 | 否 | 广告唯一标识。 | 
| rewarded | boolean | 否 | 否 | 广告是否获得奖励。<br/>- true：获得奖励。<br/>- false：没有获得奖励。 | 
| shown | boolean | 否 | 否 | 广告是否展示。<br/>- true：展示。<br/>- false：未展示。 | 
| clicked | boolean | 否 | 否 | 广告是否被点击。<br/>- true：被点击。<br/>- false：未被点击。 | 
| rewardVerifyConfig | Map&lt;string, string&gt; | 否 | 否 | 服务器验证参数。<br/>{<br/>customData: "test",<br/>userId: "12345"<br/>} | 
| [key: string] | Object | 否 | 是 | 自定义参数。<br/>- isFullScreen：类型boolean。开屏广告自定义参数，用于标识返回的广告是否为全屏，true为全屏广告，false为半屏广告。<br/>- biddingInfo：类型Object。用于获取实时竞价相关结果。<br/>- biddingInfo.price：类型number。本条广告的eCPM（Effective Cost Per Mille，每一千次展示可以获得的广告收入）。<br/>- biddingInfo.cur：类型string。 本条广告的价格币种。支持币种：CNY（单位：元）、USD（单位：美元）、EUR（单位：欧元）、GBP（单位：英镑）、JPY（单位：日元）。<br/>- biddingInfo.nurl：类型string。媒体回传竞价成功结果的URL。<br/>- biddingInfo.lurl：类型string。媒体回传竞价失败通知其他DSP竞价成功结果的URL。 | 