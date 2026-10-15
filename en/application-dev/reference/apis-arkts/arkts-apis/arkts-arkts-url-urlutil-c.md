# URLUtil

```TypeScript
class URLUtil
```

The URLUtil class provides utility methods related to URLs.

**Since:** 26.2.0

<!--Device-url-class URLUtil--><!--Device-url-class URLUtil-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { url } from '@kit.ArkTS';
```

## toString

```TypeScript
static toString(urlParams: URLParams): string
```

Serializes the specified URLParams object into a string, in which spaces are percent-encoded as %20 (instead of '+').

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-URLUtil-static toString(urlParams: URLParams): string--><!--Device-URLUtil-static toString(urlParams: URLParams): string-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| urlParams | [URLParams](arkts-arkts-url-urlparams-c.md) | Yes | The URLParams object to serialize. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the serialized string in which spaces are encoded as %20. |
