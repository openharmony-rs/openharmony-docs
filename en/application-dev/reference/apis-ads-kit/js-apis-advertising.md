# @ohos.advertising (Ads Service Framework)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @ctssss-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=3af2c2640a0dfa1285ceb6197505adab556ff3bb translatedAt=2026-09-02T02:15:31.403Z pushedAt=2026-09-03T04:01:27.054Z -->


The advertising module provides APIs for requesting and displaying ads.


> **Note:**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```typescript
import { advertising } from '@kit.AdsKit';
```


## advertising.showAd

showAd(ad: Advertisement, options: AdDisplayOptions, context?: common.UIAbilityContext): void

Shows a full-screen ad.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| ad | [Advertisement](js-apis-advertisement.md#advertisement) | Yes | Ad object. | 
| options | [AdDisplayOptions](js-apis-advertising.md#addisplayoptions) | Yes | Ad display parameters. | 
| context | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | No | Context of the UIAbility. If not set, it is obtained from api: [@ohos.app.ability.common](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-app-ability-common). |

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| ID| Error Message                                                                               |
|----------|-----------------------------------------------------------------------------------------|
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified. |
| 21800001 | System internal error.                                                                  |
| 21800004 | Failed to display the ad.                                                               |

> **Note:**
> 
> 1. To ensure that ads can be displayed correctly, this API must be used together with the ad request API.
> 
> 2. This API only supports displaying rewarded ads and interstitial ads.

**Example**

For details about how to obtain the context, see [Acquisition of Context](../../application-models/application-context-stage.md#acquisition-of-context).

```typescript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';

function showAd(ad: advertising.Advertisement, context?: common.UIAbilityContext): void {
  // Ad display parameters. You can set the parameters based on the project requirements.
  const adDisplayOptions: advertising.AdDisplayOptions = {};
  // Show the ad.
  advertising.showAd(ad, adDisplayOptions, context);
}
```


## advertising.getAdRequestBody<sup>12+</sup>

getAdRequestBody(adParams: AdRequestParams[], adOptions: AdOptions): Promise&lt;string&gt;

Obtains the body of an ad request. This API uses a promise to return the result (this API is only open to some pre-installed system applications).

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| adParams | [AdRequestParams](js-apis-advertising.md#adrequestparams)[] | Yes | Ad request parameters.<br/>**Note**: The adId parameter in the request body can be empty. | 
| adOptions | [AdOptions](js-apis-advertising.md#adoptions) | Yes | Ad configuration parameters. | 

**Return value**

| Type                 | Description                               |
|-----------------------|-----------------------------------|
| Promise&lt;string&gt; | Promise used to return the ad data of the string type.|

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| Error Code ID | Error Message | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. | 
| 801 | Device not supported. | 
| 21800001 | System internal error. | 

**Example**

```typescript
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getAdRequestBody(adRequestParamsArray: advertising.AdRequestParams[]): Promise<void> {
  // Ad configuration options. You can set the options based on the project requirements.
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

Parses and processes the body of an ad response (this API is only open to some pre-installed system applications).

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| adResponse | string | Yes | Ad response body. | 
| listener | [MultiSlotsAdLoadListener](js-apis-advertising.md#multislotsadloadlistener) | Yes | Callback listener for requesting ads. | 
| context    | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes | Context of the UIAbility. | 

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| Error Code ID | Error Message | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. | 
| 801      | Device not supported.                                                                                                                                   |
| 21800001 | System internal error.                                                                                                                                  |
| 21800005 | Failed to parse the ad response.                                                                                                                        |

**Example**

For details about how to obtain the context, see [Acquisition of Context](../../application-models/application-context-stage.md#acquisition-of-context).

```typescript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

function parseAdResponse(adResponse: string, context: common.UIAbilityContext): void {
  // Listen for the ad parsing callback.
  const multiSlotsAdLoaderListener: advertising.MultiSlotsAdLoadListener = {
    onAdLoadFailure: (errorCode: number, errorMsg: string) => {
      hilog.error(0x0000, 'testTag', `Failed to load multiSlots ad. Code is ${errorCode}, message is ${errorMsg}`);
    },
    onAdLoadSuccess: (ads: Map<string, Array<advertising.Advertisement>>) => {
      hilog.info(0x0000, 'testTag', 'Succeeded in loading multiSlots ad');
      // Save the parsed ad content for display.
      const returnAds: advertising.Advertisement[] = [];
      ads.forEach((adsArray) => returnAds.push(...adsArray));
    }
  };
  // Call the API to parse the response body.
  advertising.parseAdResponse(adResponse, multiSlotsAdLoaderListener, context);
}
```


## advertising.registerWebAdInterface<sup>12+</sup>

registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext): void

Injects an ad JavaScript object to the **Web** component (this API is only open to some pre-installed system applications).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| controller | web_webview.[WebviewController](../apis-arkweb/arkts-apis-webview-WebviewController.md) | Yes | Web component controller. |
| context    | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes | Context of the UIAbility. |

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| ID| Error Message                                                                               |
|----------|-----------------------------------------------------------------------------------------|
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified. |
| 21800001 | System internal error.                                                                  |

**Example**

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

Injects an ad JavaScript object to the **Web** component (this API is only open to some pre-installed system applications).

**Atomic service API**: This API can be used in atomic services since API version 16.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| controller  | web_webview.[WebviewController](../apis-arkweb/arkts-apis-webview-WebviewController.md) | Yes | Web component controller. |
| context     | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes | Context of the UIAbility. |
| needRefresh | boolean | Yes | Whether to refresh the page (true: yes; false: no). | 

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| ID| Error Message                                                                            |
|----------|--------------------------------------------------------------------------------------|
| 401      | Invalid input parameter. Possible causes: Mandatory parameters are left unspecified. |
| 21800001 | System internal error.                                                  |

**Example**

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

Deletes the ad JavaScript object injected through **registerWebAdInterface** (this API is only open to some pre-installed system applications).

**Atomic service API**: This API can be used in atomic services since API version 16.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| controller  | web_webview.[WebviewController](../apis-arkweb/arkts-apis-webview-WebviewController.md) | Yes | Web component controller. |
| needRefresh | boolean | Yes | Whether to refresh the page (true: yes; false: no). | 

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| ID| Error Message                                                                            |
|----------|--------------------------------------------------------------------------------------|
| 401      | Invalid input parameter. Possible causes: Mandatory parameters are left unspecified. |
| 21800001 | System internal error.                                                  |

**Example**

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

Provides the APIs for loading ads.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads


### constructor

constructor(context: common.Context)

Constructor.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| context | common.[Context](../apis-ability-kit/js-apis-inner-application-context.md) | Yes | Context of the ability or application. |

**Example**

For details about how to obtain the context, see [Acquisition of Various Contexts](../../application-models/application-context-stage.md#acquisition-of-context).

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

Loads an ad.

**Atomic service API**: Since API version 12, this API is supported in atomic services.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| adParam | [AdRequestParams](js-apis-advertising.md#adrequestparams) | Yes | Advertising request parameters. | 
| adOptions | [AdOptions](js-apis-advertising.md#adoptions) | Yes | Advertising configuration parameters. | 
| listener | [AdLoadListener](js-apis-advertising.md#adloadlistener) | Yes | Listener for advertising request callbacks. | 

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| Error Code ID | Error Message |
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| 801 | Device not supported.<br>Applicable version: 12+ |
| 21800001 | System internal error. |
| 21800003 | Failed to load the ad request. |

**Example**

For details about how to obtain the context, see [Acquisition of Various Contexts](../../application-models/application-context-stage.md#acquisition-of-context).

```typescript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// ...
function loadAd(context: common.Context, adRequestParams: advertising.AdRequestParams): void {
  // Ad configuration options. You can set the options based on the project requirements.
  const adOptions: advertising.AdOptions = {};
  // Listener for the ad loading status.
  const adLoaderListener: advertising.AdLoadListener = {
    onAdLoadFailure: (errorCode: number, errorMsg: string) => {
      hilog.error(0x0000, 'testTag', `Failed to load ad. Code is ${errorCode}, message is ${errorMsg}`);
    },
    onAdLoadSuccess: (ads: Array<advertising.Advertisement>) => {
      hilog.info(0x0000, 'testTag', 'Succeeded in loading ad');
      // Save the requested ad content for display.
      const returnAds: advertising.Advertisement[] = ads;
    }
  };
  // Create an AdLoader object.
  const adLoader: advertising.AdLoader = new advertising.AdLoader(context);
  // Load the ad.
  adLoader.loadAd(adRequestParams, adOptions, adLoaderListener);
}
```


### loadAdWithMultiSlots

loadAdWithMultiSlots(adParams: AdRequestParams[], adOptions: AdOptions, listener: MultiSlotsAdLoadListener): void

Loads multiple ads.

**Atomic service API**: Since API version 12, this API is supported in atomic services.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| adParams | [AdRequestParams](js-apis-advertising.md#adrequestparams)[] | Yes | Advertising request parameters. | 
| adOptions | [AdOptions](js-apis-advertising.md#adoptions) | Yes | Advertising configuration parameters. | 
| listener | [MultiSlotsAdLoadListener](js-apis-advertising.md#multislotsadloadlistener) | Yes | Listener for advertising request callbacks. | 

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| Error Code ID | Error Message |
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| 801 | Device not supported.<br>Applicable version: 12+ |
| 21800001 | System internal error. |
| 21800003 | Failed to load the ad request. |

**Example**

For details about how to obtain the context, see [Acquisition of Context](../../application-models/application-context-stage.md#acquisition-of-context).

```typescript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// ...
function loadAdWithMultiSlots(context: common.Context, adRequestParamsArray: advertising.AdRequestParams[]): void {
  // Ad configuration options. You can set the options based on the project requirements.
  const adOptions: advertising.AdOptions = {};
  // Listener for the ad loading status.
  const multiSlotsAdLoaderListener: advertising.MultiSlotsAdLoadListener = {
    onAdLoadFailure: (errorCode: number, errorMsg: string) => {
      hilog.error(0x0000, 'testTag', `Failed to load multiSlots ad. Code is ${errorCode}, message is ${errorMsg}`);
    },
    onAdLoadSuccess: (ads: Map<string, Array<advertising.Advertisement>>) => {
      hilog.info(0x0000, 'testTag', 'Succeeded in loading multiSlots ad');
      // Save the requested ad content for display.
      const returnAds: advertising.Advertisement[] = [];
      ads.forEach((adsArray) => returnAds.push(...adsArray));
    }
  };
  // Create an AdLoader object.
  const adLoader: advertising.AdLoader = new advertising.AdLoader(context);
  // Load the ad.
  adLoader.loadAdWithMultiSlots(adRequestParamsArray, adOptions, multiSlotsAdLoaderListener);
}
```


## AdLoadListener

Enumerates the callbacks used for the request for loading an ad.

**Atomic service API**: Since API version 12, this API is supported in atomic services.

**System capability**: SystemCapability.Advertising.Ads


### onAdLoadFailure

onAdLoadFailure(errorCode: number, errorMsg: string): void

Called when an ad request fails.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| errorCode | number | Yes | Error code for the ad request failure. | 
| errorMsg | string | Yes | Error information for the ad request failure. |

**Example:**

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

Called when an ad request is successful.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters** 

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| ads | Array&lt;[Advertisement](js-apis-advertisement.md#advertisement)&gt; | Yes | Ad data. |

**Example**

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

Enumerates the callbacks used for the request for loading multiple ads.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads


### onAdLoadFailure

onAdLoadFailure(errorCode: number, errorMsg: string): void

Called when a request for loading multiple ads fails.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**  

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| errorCode | number | Yes | Error code for the ad request failure. | 
| errorMsg | string | Yes | Error information for the ad request failure. |

**Example:**

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

Called when a request for loading multiple ads is successful.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters** 

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| adsMap | Map&lt;string, Array&lt;[Advertisement](js-apis-advertisement.md#advertisement)&gt;&gt; | Yes | Ad data, which is a mapping set that uses ad slot IDs as keys and stores the requested ad content. |

**Example**

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

Defines the ad status change callback.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads


### onStatusChanged

onStatusChanged(status: string, ad: Advertisement, data: string)

Called when the ad display status changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name| Type                           | Mandatory| Description                                                                        |
|--------|---------------------------------|------|------------------------------------------------------------------------------|
| status | string | Yes | Ad show status.<br/>- onAdLoad: Ad loaded successfully.<br/>- onAdFail: Ad failed to load.<br/>- onAdOpen: Ad opened.<br/>- onAdClick: Ad clicked.<br/>- onAdClose: Ad closed.<br/>- onMediaProgress: Ad playback progress.<br/>- onMediaStart: Ad playback started.<br/>- onMediaPause: Ad playback paused.<br/>- onMediaStop: Ad playback stopped.<br/>- onMediaComplete: Ad playback completed.<br/>- onMediaCountDown: Ad countdown.<br/>- onMediaError: Ad playback failed.<br/>- onLandscape: Full-screen button clicked in portrait mode.<br/>- onPortrait: Back button clicked in full-screen mode.<br/>- onBackClicked: Back button clicked. |
| ad | [Advertisement](js-apis-advertisement.md#advertisement) | Yes | Ad content whose status changes. |
| data | string | Yes | Extended information.<br/>When **status** is **onAdClose**, the data value is the close reason, described as follows:<br/>- adShowEnded: Ad show ended.<br/>- adCloseBtnClicked: Close button clicked.<br/>- adSkipBtnClicked: Skip button clicked.<br/>- adFeedbackClosed: The ad is closed due to negative feedback.<br/>- adBackgroundClosed: The splash ad is closed when the app switches to the background. |

**Example**

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
        // The data value is the close reason.
        hilog.info(0x0000, 'testTag', `Status is onAdClose, Close Reason is ${data}`);
        if (data === 'adShowEnded') {
          // The close reason is that the ad show has ended. You can add processing logic based on the actual scenario.
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

Defines the ad configuration.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters** 

| Name | Type | Read-only | Optional | Description | 
| -------- | -------- | -------- | -------- | -------- |
| tagForChildProtection | number | No | Yes | Whether to treat your content as child-directed content in accordance with COPPA.<br/> -1: Default value, undetermined.<br/> 0: No.<br/> 1: Yes.<br/>The default value is -1. | 
| adContentClassification | string | No | Yes | Sets the upper limit of the ad content rating.<br/> W: 3+, all audiences.<br/> PI: 7+, parental guidance.<br/> J: 12+, teens.<br/> A: 16+/18+, adult audiences.<br/>If not set, the business logic prevails. | 
| nonPersonalizedAd | number | No | Yes | Sets whether to request only non-personalized ads.<br/> 0: Request personalized ads and non-personalized ads.<br/> 1: Request only non-personalized ads.<br/>If not set, the business logic prevails. | 
| [key: string] | number \| boolean \| string \| undefined | No | Yes | Custom parameters.<br/><!--RP1--><!--RP1End--> | 


## AdRequestParams

Defines the ad request parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Read-only | Optional | Description | 
| -------- | -------- | -------- | -------- | -------- |
| adId | string | No | No | Ad slot ID.<br/>Note: The [getAdRequestBody](js-apis-advertising.md#advertisinggetadrequestbody12) API can be called without this parameter. | 
| adType | number | No | Yes | Type of the requested ad.<br/>- 1: Splash ad.<br/>- 3: Native ad.<br/>- 7: Rewarded ad.<br/>- 8: Banner ad.<br/>- 12: Interstitial ad.<br/>- 60: Roll ad.<br/>If not set, the default value is the native ad type. | 
| adCount | number | No | Yes | Number of requested ads. If not set, the business logic prevails. | 
| adWidth | number | No | Yes | Expected creative width when requesting ads, in vp (mandatory for banner ads). If not set, the business logic prevails. | 
| adHeight | number | No | Yes | Expected creative height when requesting ads, in vp (mandatory for banner ads). If not set, the business logic prevails. | 
| adSearchKeyword | string | No | Yes | Ad keyword. If not set, the default value is "".<br/>Note: This parameter is not supported for use currently. | 
| [key: string] | number \| boolean \| string \| undefined | No | Yes | Custom parameters.<br/><!--RP2--><!--RP2End--> | 


## AdDisplayOptions

Defines the ad display parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name | Type | Read-only | Optional | Description | 
| -------- | -------- | -------- | -------- | -------- |
| customData | string | No | Yes | Media custom data. Used for the server to notify the media server that a user should be rewarded for interacting with a rewarded video ad, thereby preventing fraudulent behavior (if not set, no notification is sent). | 
| userId | string | No | Yes | Media custom user ID. Used for the server to notify the media server that a user should be rewarded for interacting with a rewarded video ad, thereby preventing fraudulent behavior (if not set, no notification is sent). | 
| useMobileDataReminder | boolean | No | Yes | Whether to display a dialog to notify the user when playing a video or downloading an app using mobile data.<br/>- true: Display a dialog.<br/>- false: Do not display a dialog.<br/>- This parameter depends on the data usage dialog feature, which currently does not support full functionality, so the default value is not yet determined. | 
| mute | boolean | No | Yes | Whether to mute the ad video playback.<br/>- true: Muted playback.<br/>- false: Non-muted playback.<br/>If not set, the business logic prevails. | 
| audioFocusType | number | No | Yes | Type of scenario in which audio focus is obtained during video playback.<br/>- 0: Obtain focus in both muted and non-muted video playback.<br/>- 1: Do not obtain focus during muted video playback.<br/>- 2: Do not obtain focus in either muted or non-muted video playback.<br/>- The related features that this API depends on are not supported for use currently, so the default value is not yet determined. | 
| [key: string] | number \| boolean \| string \| undefined | No | Yes | Custom parameters.<br/>- refreshTime: Optional custom parameter of the AutoAdComponent component, used to control the ad carousel interval. Type: number, unit: ms, value range [30000, 120000]. If not set, or if the value is a non-number or a number less than or equal to 0, no carousel is performed and only the first ad content in the ad response is displayed. If the value is set to a number less than 30000, 30000 is used. If the value is set to a number greater than 120000, 120000 is used.<br/><!--RP3--><!--RP3End--> | 