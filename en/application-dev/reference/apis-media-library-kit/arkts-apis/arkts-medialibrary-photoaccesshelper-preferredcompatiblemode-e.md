# PreferredCompatibleMode

```TypeScript
enum PreferredCompatibleMode
```

Preferred compatible mode.

**Since:** 26.0.0

<!--Device-photoAccessHelper-enum PreferredCompatibleMode--><!--Device-photoAccessHelper-enum PreferredCompatibleMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DEFAULT

```TypeScript
DEFAULT = 0
```

Performs transcoding based on the configured asset compatibility capabilities.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-PreferredCompatibleMode-DEFAULT = 0--><!--Device-PreferredCompatibleMode-DEFAULT = 0-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## CURRENT

```TypeScript
CURRENT = 1
```

No transcoding is performed. The asset is returned in its original format.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-PreferredCompatibleMode-CURRENT = 1--><!--Device-PreferredCompatibleMode-CURRENT = 1-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## COMPATIBLE

```TypeScript
COMPATIBLE = 2
```

All assets are transcoded to the most widely compatible format.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-PreferredCompatibleMode-COMPATIBLE = 2--><!--Device-PreferredCompatibleMode-COMPATIBLE = 2-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
