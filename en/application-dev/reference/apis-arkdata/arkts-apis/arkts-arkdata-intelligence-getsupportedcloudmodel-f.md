# getSupportedCloudModel

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getSupportedCloudModel

```TypeScript
function getSupportedCloudModel(): Promise<Array<CloudModelInfo>>
```

Obtains the supported cloud model information. This API uses a promise to return the result.

**Device behavior differences:** This API can be properly called on PC/2-in-1, Phone, and Tablet devices. If it is called on other device types, error code 801 is returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-intelligence-function getSupportedCloudModel(): Promise<Array<CloudModelInfo>>--><!--Device-intelligence-function getSupportedCloudModel(): Promise<Array<CloudModelInfo>>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[CloudModelInfo](arkts-arkdata-intelligence-cloudmodelinfo-i.md)&gt;&gt; | Promise object, which returns the supported cloud model information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

intelligence.getSupportedCloudModel()
  .then((info: Array<intelligence.CloudModelInfo>) => {
    console.info("Succeeded in getting CloudModelInfo");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to get CloudModelInfo. Code: ${err.code}, message: ${err.message}`);
  });
```
