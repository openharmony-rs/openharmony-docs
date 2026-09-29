# GetItemsInShapePathParams (System API)

```TypeScript
interface GetItemsInShapePathParams
```

Image options setted when need to get the image objects.

@interface GetItemsInShapePathParams

**Since:** 23

<!--Device-componentUtils-interface GetItemsInShapePathParams--><!--Device-componentUtils-interface GetItemsInShapePathParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## images

```TypeScript
images: Array<ImageItem>
```

image information.

**Type:** Array&lt;[ImageItem](arkts-arkui-componentutils-imageitem-i-sys.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GetItemsInShapePathParams-images: Array<ImageItem>--><!--Device-GetItemsInShapePathParams-images: Array<ImageItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## ratio

```TypeScript
ratio?: number
```

The proportion of non-transparent blank pixels in the selected area relative to the total pixels of the image. Default value is 0.15.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GetItemsInShapePathParams-ratio?: double--><!--Device-GetItemsInShapePathParams-ratio?: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## shapePath

```TypeScript
shapePath: Array<common2D.Point>
```

Indicates the path points information.

**Type:** Array&lt;[common2D.Point](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-common2d-point-i.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GetItemsInShapePathParams-shapePath: Array<common2D.Point>--><!--Device-GetItemsInShapePathParams-shapePath: Array<common2D.Point>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
