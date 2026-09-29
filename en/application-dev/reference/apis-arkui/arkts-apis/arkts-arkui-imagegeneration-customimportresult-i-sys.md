# CustomImportResult (System API)

```TypeScript
interface CustomImportResult
```

The result of import operation for custom import icon.

**Since:** 26.0.0

<!--Device-imageGeneration-interface CustomImportResult--><!--Device-imageGeneration-interface CustomImportResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

Text content for import operation.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CustomImportResult-content?: ResourceStr--><!--Device-CustomImportResult-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## images

```TypeScript
images?: Array<ImageItem>
```

Array of image items for import operation.

**Type:** Array&lt;[ImageItem](arkts-arkui-imagegeneration-imageitem-i-sys.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CustomImportResult-images?: Array<ImageItem>--><!--Device-CustomImportResult-images?: Array<ImageItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
