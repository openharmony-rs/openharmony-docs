# PreferredCompatibleMode

Preferred compatible mode.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DEFAULT

```TypeScript
DEFAULT = 0
```

Performs transcoding based on the configured asset compatibility capabilities.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## CURRENT

```TypeScript
CURRENT = 1
```

No transcoding is performed. The asset is returned in its original format.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## COMPATIBLE

```TypeScript
COMPATIBLE = 2
```

All assets are transcoded to the most widely compatible format.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
