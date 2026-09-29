# RequestOptions

```TypeScript
interface RequestOptions
```

Represents request options.

**Since:** 11

<!--Device-photoAccessHelper-interface RequestOptions--><!--Device-photoAccessHelper-interface RequestOptions-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## compatibleMode

```TypeScript
compatibleMode?: CompatibleMode
```

HDR video transcoding policy, which can be **FAST_ORIGINAL_FORMAT_MODE** (maintaining the original HDR format) or **COMPATIBLE_FORMAT_MODE** (converting HDR content to SDR format). The default value is **FAST_ORIGINAL_FORMAT_MODE**.

**Type:** [CompatibleMode](arkts-medialibrary-photoaccesshelper-compatiblemode-e.md)

**Since:** 15

<!--Device-RequestOptions-compatibleMode?: CompatibleMode--><!--Device-RequestOptions-compatibleMode?: CompatibleMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## deliveryMode

```TypeScript
deliveryMode: DeliveryMode
```

Delivery mode of the requested asset. The value can be **FAST_MODE**, **HIGH_QUALITY_MODE**, or **BALANCE_MODE**.

**Type:** [DeliveryMode](arkts-medialibrary-photoaccesshelper-deliverymode-e.md)

**Since:** 11

<!--Device-RequestOptions-deliveryMode: DeliveryMode--><!--Device-RequestOptions-deliveryMode: DeliveryMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mediaAssetProgressHandler

```TypeScript
mediaAssetProgressHandler?: MediaAssetProgressHandler
```

Callback used to return the HDR-to-SDR conversion progress.

**Type:** [MediaAssetProgressHandler](arkts-medialibrary-photoaccesshelper-mediaassetprogresshandler-i.md)

**Since:** 15

<!--Device-RequestOptions-mediaAssetProgressHandler?: MediaAssetProgressHandler--><!--Device-RequestOptions-mediaAssetProgressHandler?: MediaAssetProgressHandler-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
