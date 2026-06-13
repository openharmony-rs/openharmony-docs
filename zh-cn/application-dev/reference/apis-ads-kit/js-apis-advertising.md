# @ohos.advertising (广告服务框架)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->


本模块提供广告操作能力，包括请求广告、展示广告。


> **说明：**
> 
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```typescript
import { advertising } from '@kit.AdsKit';
```


## advertising.showAd

showAd(ad: Advertisement, options: AdDisplayOptions, context?: common.UIAbilityContext): void

展示全屏广告。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| ad      | [Advertisement](#advertisement)                                                              | 是   | 广告对象。                                                          |
| options | [AdDisplayOptions](#addisplayoptions)                                                        | 是   | 广告展示参数。                                                      |
| context | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | 否   | UIAbility的上下文环境，不设置从api: [@ohos.app.ability.common](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/js-apis-app-ability-common)中获取。 |

**错误码：**

以下错误码的详细介绍请参见[广告服务框架错误码参考](errorcode-ads.md)。

| 错误码ID | 错误信息 | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified. | 
| 21800001 | System internal error.                                                                  |
| 21800004 | Failed to display the ad.                                                               |

> **说明：**
> 
> 1. 为了保证广告能正确展示，该接口必须和请求广告接口配套使用。
> 
> 2. 该接口仅支持展示激励广告和插屏广告。

**示例：**

其中context的获取方式参见[各类Context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```typescript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';

function showAd(ad: advertising.Advertisement, context?: common.UIAbilityContext): void {
  // 广告展示参数，开发者可根据项目实际情况设置
  const adDisplayOptions: advertising.AdDisplayOptions = {};
  // 调用全屏广告展示接口
  advertising.showAd(ad, adDisplayOptions, context);
}
```


## advertising.getAdRequestBody<sup>12+</sup>

getAdRequestBody(adParams: AdRequestParams[], adOptions: AdOptions): Promise&lt;string&gt;

获取广告请求体，使用Promise异步回调（该接口仅对部分系统预置应用开放）。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| adParams  | [AdRequestParams[]](#adrequestparams) | 是   | 广告请求参数。<br/>**说明：** 该接口体的adId参数可以为空。 |
| adOptions | [AdOptions](#adoptions)               | 是   | 广告配置参数。 |

**返回值：**

| 类型 | 说明 | 
| -------- | -------- |
| Promise&lt;string&gt; | Promise对象，返回字符类型的广告数据。 | 

**错误码：**

以下错误码的详细介绍请参见[广告服务框架错误码参考](errorcode-ads.md)。

| 错误码ID | 错误信息 | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. | 
| 801 | Device not supported. | 
| 21800001 | System internal error. | 

**示例：**

```typescript
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getAdRequestBody(adRequestParamsArray: advertising.AdRequestParams[]): Promise<void> {
  // 广告配置参数，开发者可根据项目实际情况设置
  const adOptions: advertising.AdOptions = {};
  await advertising.getAdRequestBody(adRequestParamsArray, adOptions).then((data: string) => {
    hilog.info(0x0000, 'testTag', `Succeeded in getting ad request body. Data is ${data}`);
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'testTag', `Failed to get ad request body. Code is ${error.code}, message is ${error.message}`);
  });
}
```


## advertising.parseAdResponse<sup>12+</sup>

parseAdResponse(adResponse: string, listener: MultiSlotsAdLoadListener, context: common.UIAbilityContext): void

解析并处理广告响应体（该接口仅对部分系统预置应用开放）。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| adResponse | string                                                                                       | 是   | 广告响应体。            |
| listener   | [MultiSlotsAdLoadListener](#multislotsadloadlistener)                                        | 是   | 请求广告回调监听。      |
| context    | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | 是   | UIAbility的上下文环境。 |

**错误码：**

以下错误码的详细介绍请参见[广告服务框架错误码参考](errorcode-ads.md)。

| 错误码ID | 错误信息 | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. | 
| 801      | Device not supported.                                                                                                                                   |
| 21800001 | System internal error.                                                                                                                                  |
| 21800005 | Failed to parse the ad response.                                                                                                                        |

**示例：**

其中context的获取方式参见[各类Context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```typescript
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


## advertising.registerWebAdInterface<sup>12+</sup>

registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext): void

注入广告JavaScript对象到Web组件中（该接口仅对部分系统预置应用开放）。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| controller | web_webview.[WebviewController](../apis-arkweb/arkts-apis-webview-WebviewController.md)         | 是   | Web组件控制器。         |
| context    | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | 是   | UIAbility的上下文环境。 |

**错误码：**

以下错误码的详细介绍请参见[广告服务框架错误码参考](errorcode-ads.md)。

| 错误码ID | 错误信息 | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified. | 
| 21800001 | System internal error.                                                                  |

**示例：**

```typescript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private webViewController: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('registerWebAdInterface')
        .onClick(() => {
          advertising.registerWebAdInterface(this.webViewController, this.context);
        })
      // ...

      Web({ src: 'https://www.example.com', controller: this.webViewController })
    }
    .width('100%')
    .height('100%')
  }
}
```


## advertising.registerWebAdInterface<sup>16+</sup>

registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext, needRefresh: boolean): void

注入广告JavaScript对象到Web组件中（该接口仅对部分系统预置应用开放）。

**元服务API：**  从API version 16开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| controller  | web_webview.[WebviewController](../apis-arkweb/arkts-apis-webview-WebviewController.md)         | 是   | Web组件控制器。                              |
| context     | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | 是   | UIAbility的上下文环境。                      |
| needRefresh | boolean                                                                                      | 是   | 是否需要刷新页面（true: 需要；false: 不需要）。 |

**错误码：**

以下错误码的详细介绍请参见[广告服务框架错误码参考](errorcode-ads.md)。

| 错误码ID | 错误信息 | 
| -------- | -------- |
| 401      | Invalid input parameter. Possible causes: Mandatory parameters are left unspecified. |
| 21800001 | System internal error.                                                  |

**示例：**

```typescript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private webViewController: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      // ...
      Button('registerWebAdInterface')
        .onClick(() => {
          advertising.registerWebAdInterface(this.webViewController, this.context, true);
        })

      Web({ src: 'https://www.example.com', controller: this.webViewController })
    }
    .width('100%')
    .height('100%')
  }
}
```


## advertising.deleteWebAdInterface<sup>16+</sup>

deleteWebAdInterface(controller: web_webview.WebviewController, needRefresh: boolean): void

删除通过registerWebAdInterface注入的广告JavaScript对象（该接口仅对部分系统预置应用开放）。

**元服务API：**  从API version  16开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| controller  | web_webview.[WebviewController](../apis-arkweb/arkts-apis-webview-WebviewController.md) | 是   | Web组件控制器。                              |
| needRefresh | boolean                                                                              | 是   | 是否需要刷新页面（true: 需要；false: 不需要）。 |

**错误码：**

以下错误码的详细介绍请参见[广告服务框架错误码参考](errorcode-ads.md)。

| 错误码ID | 错误信息 | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes: Mandatory parameters are left unspecified. | 
| 21800001 | System internal error. | 

**示例：**

```typescript
import { advertising } from '@kit.AdsKit';
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  private webViewController: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('deleteWebAdInterface')
        .onClick(() => {
          advertising.deleteWebAdInterface(this.webViewController, true);
        })

      Web({ src: 'https://www.example.com', controller: this.webViewController })
    }
    .width('100%')
    .height('100%')
  }
}
```


## AdLoader

提供加载广告的功能。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads


### constructor

constructor(context: common.Context)

构造函数。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| context | common.[Context](../apis-ability-kit/js-apis-inner-application-context.md) | 是   | ability或application的上下文环境。 |

**示例：**

其中context的获取方式参见[各类context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```typescript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
// ...

function createAdLoader(context: common.Context): void {
  const adLoader: advertising.AdLoader = new advertising.AdLoader(context);
}
```


### loadAd

loadAd(adParam: AdRequestParams, adOptions: AdOptions, listener: AdLoadListener): void

请求单广告位广告。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| adParam   | [AdRequestParams](#adrequestparams) | 是   | 广告请求参数。     |
| adOptions | [AdOptions](#adoptions)             | 是   | 广告配置参数。     |
| listener  | [AdLoadListener](#adloadlistener)   | 是   | 请求广告回调监听。 |

**错误码：**

以下错误码的详细介绍请参见[广告服务框架错误码参考](errorcode-ads.md)。

| 错误码ID | 错误信息 | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. | 
| 801 | Device not supported. | 
| 21800001 | System internal error. | 
| 21800003 | Failed to load the ad request. | 

**示例：**

其中context的获取方式参见[各类context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```typescript
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


### loadAdWithMultiSlots

loadAdWithMultiSlots(adParams: AdRequestParams[], adOptions: AdOptions, listener: MultiSlotsAdLoadListener): void

请求多广告位广告。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| adParams  | [AdRequestParams](#adrequestparams)[]                 | 是   | 广告请求参数。     |
| adOptions | [AdOptions](#adoptions)                               | 是   | 广告配置参数。     |
| listener  | [MultiSlotsAdLoadListener](#multislotsadloadlistener) | 是   | 请求广告回调监听。 |

**错误码：**

以下错误码的详细介绍请参见[广告服务框架错误码参考](errorcode-ads.md)。

| 错误码ID | 错误信息 | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. | 
| 801 | Device not supported. | 
| 21800001 | System internal error. | 
| 21800003 | Failed to load the ad request. | 

**示例：**

其中context的获取方式参见[各类Context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```typescript
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


## AdLoadListener

单广告位广告请求回调。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads


### onAdLoadFailure

onAdLoadFailure(errorCode: number, errorMsg: string): void

广告请求失败回调。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

| 名称 | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| errorCode | number | 是 | 广告请求失败的错误码。 | 
| errorMsg | string | 是 | 广告请求失败的错误信息。 | 

**示例：**

```typescript
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

### onAdLoadSuccess

onAdLoadSuccess(ads: Array&lt;Advertisement&gt;): void

广告请求成功后回调。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads


| 名称 | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| ads    | Array&lt;[Advertisement](#advertisement)&gt; | 是   | 广告数据。 |

**示例：**

```typescript
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


## MultiSlotsAdLoadListener

多广告位广告请求回调。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads


### onAdLoadFailure

onAdLoadFailure(errorCode: number, errorMsg: string): void

多广告位广告请求失败回调。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

| 名称 | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| errorCode | number | 是 | 广告请求失败的错误码。 | 
| errorMsg | string | 是 | 广告请求失败的错误信息。 | 

**示例：**

```typescript
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

### onAdLoadSuccess

onAdLoadSuccess(adsMap: Map&lt;string, Array&lt;Advertisement&gt;&gt;): void

多广告位广告请求成功后回调。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads


| **参数名** | **类型** | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| adsMap | Map&lt;string, Array&lt;[Advertisement](#advertisement)&gt;&gt; | 是   | 广告数据，是以广告位ID为键，存储请求到的广告内容的映射集合。 |

**示例：**

```typescript
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


## AdInteractionListener

广告状态变化回调。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads


### onStatusChanged

onStatusChanged(status: string, ad: Advertisement, data: string)

广告状态回调。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| status | string | 是 | 广告展示状态。<br/>- onAdLoad：广告加载成功。<br/>- onAdFail：广告加载失败。<br/>- onAdOpen：打开广告。<br/>- onAdClick：点击广告。<br/>- onAdClose：关闭广告。<br/>- onMediaProgress：广告播放进度。<br/>- onMediaStart：广告开始播放。<br/>- onMediaPause：广告暂停播放。<br/>- onMediaStop：广告停止播放。<br/>- onMediaComplete：广告播放完成。<br/>- onMediaCountDown：广告倒计时。<br/>- onMediaError：广告播放失败。<br/>- onLandscape：竖屏状态下点击全屏按钮。<br/>- onPortrait：全屏状态下点击返回按钮。<br/>- onBackClicked：点击返回按钮。<br/>- onAdSubWindow：打开半模态。 | 
| ad     | [Advertisement](#advertisement) | 是   | 发生状态变化的广告内容。                                                     |
| data | string | 是 | 扩展信息。<br/>当status参数为onAdClose时，data值为关闭原因，关闭原因描述如下：<br/>- adShowEnded：广告展示结束。<br/>- adCloseBtnClicked：点击关闭按钮。<br/>- adSkipBtnClicked：点击跳过。<br/>- adFeedbackClosed：负反馈关闭。<br/>- adBackgroundClosed：开屏切后台关闭。| 

**示例：**

```typescript
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const adInteractionListener: advertising.AdInteractionListener = {
  onStatusChanged: (status: string, ad: advertising.Advertisement, data: string) => {
    switch (status) {
      case 'onAdLoad':
        hilog.info(0x0000, 'testTag', 'Status is onAdLoad');
        break;
      case 'onAdFail':
        hilog.error(0x0000, 'testTag', 'Status is onAdFail');
        break;
      case 'onAdOpen':
        hilog.info(0x0000, 'testTag', 'Status is onAdOpen');
        break;
      case 'onAdClick':
        hilog.info(0x0000, 'testTag', 'Status is onAdClick');
        break;
      case 'onAdClose':
        // data值为关闭原因
        hilog.info(0x0000, 'testTag', `Status is onAdClose, Close Reason is ${data}`);
        if (data === 'adShowEnded') {
          // 关闭原因为广告展示结束，可根据实际场景添加处理逻辑
        }
        break;
      case 'onMediaProgress':
        hilog.info(0x0000, 'testTag', 'Status is onMediaProgress');
        break;
      case 'onMediaStart':
        hilog.info(0x0000, 'testTag', 'Status is onMediaStart');
        break;
      case 'onMediaPause':
        hilog.info(0x0000, 'testTag', 'Status is onMediaPause');
        break;
      case 'onMediaStop':
        hilog.info(0x0000, 'testTag', 'Status is onMediaStop');
        break;
      case 'onMediaComplete':
        hilog.info(0x0000, 'testTag', 'Status is onMediaComplete');
        break;
      case 'onMediaCountDown':
        hilog.info(0x0000, 'testTag', 'Status is onMediaCountDown');
        break;
      case 'onMediaError':
        hilog.info(0x0000, 'testTag', 'Status is onMediaError');
        break;
      case 'onLandscape':
        hilog.info(0x0000, 'testTag', 'Status is onLandscape');
        break;
      case 'onPortrait':
        hilog.info(0x0000, 'testTag', 'Status is onPortrait');
        break;
      case 'onBackClicked':
        hilog.info(0x0000, 'testTag', 'Status is onBackClicked');
        break;
      default:
        break;
    }
  }
}
```

## AdOptions

广告配置参数。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

| 名称 | 类型 | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| tagForChildProtection | number | 否 | 是否希望根据 COPPA 的规定将您的内容视为面向儿童的内容。<br/> -1：默认值，不确定。<br/> 0：不希望。<br/> 1：希望。<br/>默认为-1。 | 
| adContentClassification | string | 否 | 设置广告内容分级上限。<br/> W：3+，所有受众。<br/> PI：7+，家长指导。<br/> J：12+，青少年。<br/> A：16+/18+，成人受众。<br/>不填以业务逻辑为准。 | 
| nonPersonalizedAd | number | 否 | 设置是否只请求非个性化广告。<br/> 0：请求个性化广告与非个性化广告。<br/> 1：只请求非个性化广告。<br/>不填以业务逻辑为准。 | 
| [key: string] | number \| boolean \| string \| undefined | 否 | 自定义参数。<br/><!--RP1--><!--RP1End--> | 


## AdRequestParams

广告请求参数。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

| 名称 | 类型 | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| adId | string | 是 | 广告位ID。<br/>说明：getAdRequestBody接口可以不传该参数。 | 
| adType | number | 否 | 请求的广告类型。<br/>- 1：开屏广告。<br/>- 3：原生广告。<br/>- 7：激励广告。<br/>- 8：横幅广告。<br/>- 12：插屏广告。<br/>- 60：贴片广告。<br/>不填默认为原生广告类型。 | 
| adCount | number | 否 | 请求的广告数量。不填以业务逻辑为准。 | 
| adWidth | number | 否 | 请求广告时期望的创意宽度，单位vp（横幅广告必填）。不填以业务逻辑为准。 | 
| adHeight | number | 否 | 请求广告时期望的创意高度，单位vp（横幅广告必填）。不填以业务逻辑为准。 | 
| adSearchKeyword | string | 否 | 广告关键字。不填默认""。<br/>说明：暂不支持使用。 | 
| [key: string] | number \| boolean \| string \| undefined | 否 | 自定义参数。<br/><!--RP2--><!--RP2End--> | 


## AdDisplayOptions

广告展示参数。

**元服务API：** 从API version 12开始，该接口支持在元服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

| 名称 | 类型 | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| customData | string | 否 | 媒体自定义数据。用于服务端通知媒体服务器某位用户因为与激励视频广告互动而应予以奖励，从而规避欺骗的行为（不填则不会通知）。 | 
| userId | string | 否 | 媒体自定义用户id。用于服务端通知媒体服务器某位用户因为与激励视频广告互动而应予以奖励，从而规避欺骗的行为（不填则不会通知）。 | 
| useMobileDataReminder | boolean | 否 | 使用移动数据播放视频或下载应用时是否弹框通知用户。<br/>- true：弹框通知。<br/>- false：不弹框通知。<br/>- 该参数依赖流量弹窗功能，当前不支持完整功能的使用，暂不确定默认值。 | 
| mute | boolean | 否 | 广告视频播放是否静音。<br/>- true：静音播放。<br/>- false：非静音播放。<br/>不填以业务逻辑为准。 | 
| audioFocusType | number | 否 | 视频播放过程中获得音频焦点的场景类型。<br/>- 0：视频播放静音、非静音时都获取焦点。<br/>- 1：视频静音播放时不获取焦点。<br/>- 2：视频播放静音、非静音时都不获取焦点。<br/>- 该接口依赖的相关功能当前不支持使用，暂不确定默认值。 | 
| [key: string] | number \| boolean \| string \| undefined | 否 | 自定义参数。<br/>- refreshTime：AutoAdComponent组件可选自定义参数，用于控制广告的轮播时间间隔。类型number，单位：ms，取值范围[30000, 120000]。如果不设置或取值为非数字或小于等于0的数字，则不轮播，只会展示广告响应中的第一个广告内容。设置小于30000的数字取值30000，设置大于120000的数字取值120000。<br/><!--RP3--><!--RP3End--> | 


## Advertisement

type Advertisement = _Advertisement

请求的广告内容。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

| 类型                                                         | 说明                   |
|--------------------------------------------------------------|----------------------|
| [_Advertisement](js-apis-advertisement.md) | 表示Advertisement对象。 |