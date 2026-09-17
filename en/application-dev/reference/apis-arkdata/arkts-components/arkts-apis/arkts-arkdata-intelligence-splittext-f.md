# splitText

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## splitText

```TypeScript
function splitText(text: string, config: SplitConfig): Promise<Array<string>>
```

Splits text.

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text for chunking. The length of the text is no longer then 100k tokens. |
| config | [SplitConfig](arkts-arkdata-intelligence-splitconfig-i.md) | Yes | Configurations of text chunking. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | The promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
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
