# BlanklessInfo

Prediction information about the first screen loading of the page, mainly including the predicted first screen similarity, predicted first screen loading duration, and predicted error code. The app determines whether to enable the White-Screen-Free Loading frame interpolation scheme based on this information.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## errCode

```TypeScript
errCode: WebBlanklessErrorCode
```

Error code of blankless loading. For details, see [WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md).

**Type:** [WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md)

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## loadingTime

```TypeScript
loadingTime: number
```

Predicts the loading time of the current load based on the first screen loading time of historical loads. Unit: ms. Value range: greater than 0.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## similarity

```TypeScript
similarity: number
```

Similarity of the first screen. The similarity is calculated based on the first screen content of historical loads. The value ranges from [0, 1.0], where **1.0** indicates a complete match. The closer the value is to 1, the higher the similarity. This value has a lagging nature, meaning the similarity of a local load will only be reflected in the next load. It is recommended that the app does not enable the white-screen-free loading frame insertion solution when the similarity is below a specific threshold (for example, 0.33).

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core
