# @ohos.advertising (Ads Service Framework)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=ea2d8082679fb01eb444ae8d25a7681c82490ad7 translatedAt=2026-05-25T07:02:07.946Z pushedAt=2026-05-27T13:10:01.965Z -->

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

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| ad      | [Advertisement](#advertisement)                                                              | Yes   | Ad object.                                                          |
| options | [AdDisplayOptions](#addisplayoptions)                                                        | Yes   | Ad display parameters.                                                      |
| context | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | No   | Context of the UIAbility. If not set, it is obtained from the api: [@ohos.app.ability.common](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-app-ability-common). |

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

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| adParams  | [AdRequestParams[]](#adrequestparams) | Yes   | Ad request parameters.<br/>**Note:** The **adId** parameter of this API can be empty. |
| adOptions | [AdOptions](#adoptions)               | Yes   | Ad configuration parameters. |

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

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| adResponse | string                                                                                       | Yes   | Ad response body.            |
| listener   | [MultiSlotsAdLoadListener](#multislotsadloadlistener)                                        | Yes   | Callback listener for ad requests.      |
| context    | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes   | Context of the UIAbility. |

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

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| controller | web_webview.[WebviewController](../apis-arkweb/arkts-apis-webview-WebviewController.md)         | Yes   | Web component controller.         |
| context    | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes   | Context of the UIAbility. |

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

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| controller  | web_webview.[WebviewController](../apis-arkweb/arkts-apis-webview-WebviewController.md)         | Yes   | Web component controller.                              |
| context     | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes   | Context of the UIAbility.                      |
| needRefresh | boolean                                                                                      | Yes   | Whether to refresh the page (true: yes; false: no). |

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

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| controller  | web_webview.[WebviewController](../apis-arkweb/arkts-apis-webview-WebviewController.md) | Yes   | Web component controller.                              |
| needRefresh | boolean                                                                              | Yes   | Whether to refresh the page (true: yes; false: no). |

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

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| context | common.[Context](../apis-ability-kit/js-apis-inner-application-context.md) | Yes   | Context of the ability or application. |

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

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| adParam   | [AdRequestParams](#adrequestparams) | Yes   | Ad request parameters.     |
| adOptions | [AdOptions](#adoptions)             | Yes   | Ad configuration parameters.     |
| listener  | [AdLoadListener](#adloadlistener)   | Yes   | Callback listener for ad requests. |

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| Error Code ID | Error Message | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. | 
| 801 | Device not supported. | 
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

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| adParams  | [AdRequestParams](#adrequestparams)[]                 | Yes   | Ad request parameters.     |
| adOptions | [AdOptions](#adoptions)                               | Yes   | Ad configuration parameters.     |
| listener  | [MultiSlotsAdLoadListener](#multislotsadloadlistener) | Yes   | Callback listener for ad requests. |

**Error codes**

For details about the following error codes, see [Ads Service Framework Error Codes](errorcode-ads.md).

| Error Code ID | Error Message | 
| -------- | -------- |
| 401 | Invalid input parameter. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. | 
| 801 | Device not supported. | 
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

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

### onAdLoadFailure

onAdLoadFailure(errorCode: number, errorMsg: string): void

Called when an ad request fails.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

| Name | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| errorCode | number | Yes | Error code for the ad request failure. | 
| errorMsg | string | Yes | Error message for the ad request failure. | 

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

| Name | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| ads    | Array&lt;[Advertisement](#advertisement)&gt; | Yes   | Ad data. |

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

| Name | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| errorCode | number | Yes | Error code for the ad request failure. | 
| errorMsg | string | Yes | Error message for the ad request failure. | 

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

| **Parameter Name** | **Type** | Mandatory | **Description** | 
| -------- | -------- | -------- | -------- |
| adsMap | Map&lt;string, Array&lt;[Advertisement](#advertisement)&gt;&gt; | Yes   | Ad data, which is a mapping set that uses ad slot IDs as keys to store the requested ad content. |

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
| ad     | [Advertisement](#advertisement) | Yes  | Content of the ad.                                                    |
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

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| tagForChildProtection | number | No | Whether you want your content to be treated as child-directed for purposes of COPPA.<br/> -1: Default value, unspecified.<br/> 0: No.<br/> 1: Yes.<br/>The default value is -1. | 
| adContentClassification | string | No | Sets the maximum ad content rating.<br/> W: 3+, all audiences.<br/> PI: 7+, parental guidance.<br/> J: 12+, teen.<br/> A: 16+/18+, adult audience.<br/>If not set, the business logic prevails. | 
| nonPersonalizedAd | number | No | Sets whether to request only non-personalized ads.<br/> 0: Request both personalized and non-personalized ads.<br/> 1: Request only non-personalized ads.<br/>If not set, the business logic prevails. | 
| [key: string] | number \| boolean \| string \| undefined | No | Custom parameter.<br/>- totalDuration: Type number, unit: s. A mandatory custom parameter for roll ads, used to set the display duration of the roll ad.<br/>- allowMobileTraffic: Type number. An optional custom parameter that sets whether to allow downloading ad creatives using mobile data. 0: not allowed, 1: allowed. If not set, the advertiser's settings prevail.<br/>- tagForUnderAgeOfPromise: Type number. An optional custom parameter that sets the underage protection tag. Whether you want the ad request to be processed in a manner suitable for EEA users who have not reached the legal age of consent. -1: Default value, unspecified, 0: No, 1: Yes. | 

## AdRequestParams

Defines the ad request parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| adId | string | Yes | Ad slot ID.<br/>Note: The getAdRequestBody API can omit this parameter. | 
| adType | number | No | Requested ad type.<br/>- 1: Splash ad.<br/>- 3: Native ad.<br/>- 7: Rewarded ad.<br/>- 8: Banner ad.<br/>- 12: Interstitial ad.<br/>- 60: Roll ad.<br/>If not set, the default is the native ad type. | 
| adCount | number | No | Number of ads requested. If not set, the business logic prevails. | 
| adWidth | number | No | Expected creative width when requesting an ad, in vp (mandatory for banner ads). If not set, the business logic prevails. | 
| adHeight | number | No | Expected creative height when requesting an ad, in vp (mandatory for banner ads). If not set, the business logic prevails. | 
| adSearchKeyword | string | No | Ad keyword. Defaults to "" if not set.<br/>Note: Not supported for use currently. | 
| [key: string] | number \| boolean \| string \| undefined | No | Custom parameter.<br/>- isPreload: Type boolean. When requesting a roll ad, used to distinguish between a normal online request and a creative preload request. true: creative preload request, false: normal online request. The default value is false. Only effective for roll ads; other ad requests do not parse this parameter.<br/>- enableDirectReturnVideoAd: Type boolean. A custom extension parameter for native ads, indicating whether to return the ad directly without waiting for all ad creatives to download. true: do not wait for ad creatives to download; load creatives online when displaying the ad; false: wait for ad creatives to download, and load creatives from the local cache when displaying the ad. If not set, the cloud-side configuration prevails. Only effective for native ads; other ad requests do not parse this parameter.<br/>- oaid: Type string. Open Anonymous Device Identifier (OAID), used for precise ad delivery. If not set, personalized ads cannot be obtained. The default value is "".<br/>- tMax: Type number. Maximum timeout for the transaction (including network latency), in ms.<br/>- cur: Type string. Currencies supported by the bidding request. Multiple currencies can be passed, separated by commas. Currently supports five currencies: CNY, USD, EUR, GBP, and JPY. If not set, the default is CNY.<br/>- bidFloor: Type number or string. Floor price for the real-time bidding ad slot. If the floor price is a decimal, please pass it as a string to avoid precision loss.<br/>- bidFloorCur: Type string. Currency used for the ad slot floor price. If bidFloor is not empty, bidFloorCur must also be non-empty. Currently supports only one of the five currencies: CNY, USD, EUR, GBP, and JPY. If not set, the default is CNY.<br/>- bpkgName: Type string. APP package names banned from the ad slot. Multiple names can be passed, separated by commas.<br/>- orientation: Type number. The screen orientation for which the media requests ads. 1 indicates portrait, 0 indicates landscape. If not set, the default is 1. Currently, no landscape splash creatives are available; if the requested screen orientation is set to landscape, the splash ad will not be displayed. If the media sets the application to a fixed landscape display, but this parameter is not set or is set to 1, the display effect will be affected. | 

## AdDisplayOptions

Defines the ad display parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

| Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| customData | string | No | Media custom data. Used for the server to notify the media server that a user should be rewarded for interacting with a rewarded video ad, thereby preventing fraudulent behavior (no notification will be sent if not set). | 
| userId | string | No | Media custom user ID. Used for the server to notify the media server that a user should be rewarded for interacting with a rewarded video ad, thereby preventing fraudulent behavior (no notification will be sent if not set). | 
| useMobileDataReminder | boolean | No | Whether to display a pop-up notification to the user when using mobile data to play videos or download apps.<br/>- true: Display pop-up notification.<br/>- false: Do not display pop-up notification.<br/>- This parameter depends on the traffic pop-up feature, which currently does not support full functionality, so the default value is temporarily uncertain. | 
| mute | boolean | No | Whether to mute the ad video playback.<br/>- true: Mute playback.<br/>- false: Non-mute playback.<br/>If not set, the business logic prevails. | 
| audioFocusType | number | No | Scenario type for obtaining audio focus during video playback.<br/>- 0: Obtain focus during both muted and non-muted video playback.<br/>- 1: Do not obtain focus during muted video playback.<br/>- 2: Do not obtain focus during either muted or non-muted video playback.<br/>- The related features that this API depends on are currently not supported for use, so the default value is temporarily uncertain. | 
| [key: string] | number \| boolean \| string \| undefined | No | Custom parameter.<br/>- refreshTime: An optional custom parameter for the AutoAdComponent, used to control the ad rotation interval. Type number, unit: ms, value range [30000, 120000]. If not set or the value is non-numeric or less than or equal to 0, no rotation occurs, and only the first ad content in the ad response is displayed. Values less than 30000 are set to 30000, and values greater than 120000 are set to 120000.<br/>- colorMode: The theme color of the ad. Type number. 0: dark theme, 1: light theme, 2: follow system. The theme color setting feature is supported starting from version 8.4.80.300. To check the version: On the device, go to "Settings > Apps & services", tap "More apps" in the upper right corner, and view the Intelligent Promotion Service version on the app interface. | 

## Advertisement

type Advertisement = _Advertisement

Defines the requested ad content.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

| Type                                                        | Description                  |
|--------------------------------------------------------------|----------------------|
| [_Advertisement](js-apis-inner-advertising-advertisement.md) | Advertisement object.|