# @ohos.advertising

本模块提供广告操作能力，包括请求广告、展示广告。

> **说明：**
>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 11

**系统能力：** SystemCapability.Advertising.Ads

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [deleteWebAdInterface](arkts-ads-deletewebadinterface-f.md#deletewebadinterface-1) | 删除通过registerWebAdInterface注入的广告JavaScript对象（该接口仅对部分系统预置应用开放）。 |
| [getAdRequestBody](arkts-ads-getadrequestbody-f.md#getadrequestbody-1) | 获取广告请求体，使用Promise异步回调（该接口仅对部分系统预置应用开放）。 |
| [parseAdResponse](arkts-ads-parseadresponse-f.md#parseadresponse-1) | 解析并处理广告响应体（该接口仅对部分系统预置应用开放）。 |
| [registerWebAdInterface](arkts-ads-registerwebadinterface-f.md#registerwebadinterface-1) | 注入广告JavaScript对象到Web组件中（该接口仅对部分系统预置应用开放）。 |
| [registerWebAdInterface](arkts-ads-registerwebadinterface-f.md#registerwebadinterface-2) | 注入广告JavaScript对象到Web组件中（该接口仅对部分系统预置应用开放）。 |
| [showAd](arkts-ads-showad-f.md#showad-1) | 展示全屏广告。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [AdLoader](arkts-ads-adloader-c.md) | 提供加载广告的功能。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AdDisplayOptions](arkts-ads-addisplayoptions-i.md) | 广告展示参数。 |
| [AdInteractionListener](arkts-ads-adinteractionlistener-i.md) | 广告状态变化回调。 |
| [AdLoadListener](arkts-ads-adloadlistener-i.md) | 单广告位广告请求回调。 |
| [AdOptions](arkts-ads-adoptions-i.md) | 广告配置参数。 |
| [AdRequestParams](arkts-ads-adrequestparams-i.md) | 广告请求参数。 |
| [MultiSlotsAdLoadListener](arkts-ads-multislotsadloadlistener-i.md) | 多广告位广告请求回调。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Advertisement](arkts-ads-advertisement-t.md) | 请求的广告内容。 |

