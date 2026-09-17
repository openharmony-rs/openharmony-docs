# getAdRequestBody

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## getAdRequestBody

```TypeScript
function getAdRequestBody(adParams: AdRequestParams[], adOptions: AdOptions): Promise<string>
```

Obtains the body of an ad request. This API uses a promise to return the result (this API is only open to some pre-installed system applications).

**Since:** 12

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adParams | [AdRequestParams](arkts-ads-advertising-adrequestparams-i.md)[] | Yes | Ad request parameters. **Note:** The **adId** parameter of this API can be empty. |
| adOptions | [AdOptions](arkts-ads-advertising-adoptions-i.md) | Yes | Ad configuration parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the ad data of the string type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../errorcode-ads.md#401-incorrect-ads-request-parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../errorcode-ads.md#801-ad-request-failure) | Capability not supported. |
| [21800001](../errorcode-ads.md#21800001-internal-system-error) | System internal error. |

**Examples**

```TypeScript
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
