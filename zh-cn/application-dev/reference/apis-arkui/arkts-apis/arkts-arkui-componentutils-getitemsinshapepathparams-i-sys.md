# GetItemsInShapePathParams（系统接口）

需要获取图像对象时设置的图像选项。

**起始版本：** 23

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

图片信息

**类型：** Array&lt;ImageItem&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetItemsInShapePathParams-images: Array<ImageItem>--><!--Device-GetItemsInShapePathParams-images: Array<ImageItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## ratio

```TypeScript
ratio?: number
```

所选区域中非透明空白像素的比例相对于图像总像素的比例。默认值为0.15。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetItemsInShapePathParams-ratio?: double--><!--Device-GetItemsInShapePathParams-ratio?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## shapePath

```TypeScript
shapePath: Array<common2D.Point>
```

表示路径的点信息

**类型：** Array&lt;common2D.Point&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetItemsInShapePathParams-shapePath: Array<common2D.Point>--><!--Device-GetItemsInShapePathParams-shapePath: Array<common2D.Point>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

