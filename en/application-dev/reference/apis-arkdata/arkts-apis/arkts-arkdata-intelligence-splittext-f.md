# splitText

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## splitText

```TypeScript
function splitText(text: string, config: SplitConfig): Promise<Array<string>>
```

Splits text. This API uses a promise to return the result.

**Device behavior differences:** This API can be properly called on PC/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Since:** 15

<!--Device-intelligence-function splitText(text: string, config: SplitConfig): Promise<Array<string>>--><!--Device-intelligence-function splitText(text: string, config: SplitConfig): Promise<Array<string>>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to be chunked. The maximum length of a single text is 100000 characters. An exception is thrown when the length exceeds the limit. |
| config | [SplitConfig](arkts-arkdata-intelligence-splitconfig-i.md) | Yes | Configuration for splitting the text. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise object that returns an array of chunking results. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Sync] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [31300000](../errorcode-intelligence.md#31300000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let splitConfig: intelligence.SplitConfig = {
  size: 10,
  overlapRatio: 0.1
}
let textToSplit = 'text';

intelligence.splitText(textToSplit, splitConfig)
  .then((data: Array<string>) => {
    console.info("Succeeded in splitting Text");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to split Text. Code: ${err.code}, message: ${err.message}`);
  })
```
