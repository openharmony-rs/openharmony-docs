# GetItemsInShapePathParams（系统接口）

Image options setted when need to get the image objects.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-componentUtils-interface GetItemsInShapePathParams--><!--Device-componentUtils-interface GetItemsInShapePathParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## images

```TypeScript
images: Array<ImageItem>
```

image information.

**类型：** Array&lt;[ImageItem](arkts-arkui-componentutils-imageitem-i-sys.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetItemsInShapePathParams-images: Array<ImageItem>--><!--Device-GetItemsInShapePathParams-images: Array<ImageItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## ratio

```TypeScript
ratio?: double
```

The proportion of non-transparent blank pixels in the selected area relative to the total pixels of the image. Default value is 0.15.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetItemsInShapePathParams-ratio?: double--><!--Device-GetItemsInShapePathParams-ratio?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## shapePath

```TypeScript
shapePath: Array<common2D.Point>
```

Indicates the path points information.

**类型：** Array&lt;common2D.Point&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetItemsInShapePathParams-shapePath: Array<common2D.Point>--><!--Device-GetItemsInShapePathParams-shapePath: Array<common2D.Point>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

