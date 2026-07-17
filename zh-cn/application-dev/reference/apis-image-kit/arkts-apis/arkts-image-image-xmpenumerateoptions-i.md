# XMPEnumerateOptions

表示XMP枚举选项。

**起始版本：** 26.0.0

<!--Device-image-interface XMPEnumerateOptions--><!--Device-image-interface XMPEnumerateOptions-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## isRecursive

```TypeScript
isRecursive?: boolean
```

表示是否进行递归遍历。

true表示进行递归遍历。false表示仅遍历直接子节点。默认为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XMPEnumerateOptions-isRecursive?: boolean--><!--Device-XMPEnumerateOptions-isRecursive?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## onlyQualifier

```TypeScript
onlyQualifier?: boolean
```

表示是否仅遍历限定符节点。

true表示仅遍历限定符节点。false表示遍历所有节点。默认为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XMPEnumerateOptions-onlyQualifier?: boolean--><!--Device-XMPEnumerateOptions-onlyQualifier?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

