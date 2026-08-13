# ImageFrameNode

定义Image类型的FrameNode。

**继承/实现关系：** ImageFrameNode extends TypedFrameNode<ImageAttribute>

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-typeNode-abstract class ImageFrameNode--><!--Device-typeNode-abstract class ImageFrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
abstract initialize(src: image.PixelMap | ResourceStr | DrawableDescriptor): ImageAttribute
```

初始化Image类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameNode-abstract initialize(src: image.PixelMap | ResourceStr | DrawableDescriptor): ImageAttribute--><!--Device-ImageFrameNode-abstract initialize(src: image.PixelMap | ResourceStr | DrawableDescriptor): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | image.PixelMap \| ResourceStr \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageAttribute |  |

## initialize

```TypeScript
abstract initialize(src: image.PixelMap | ResourceStr | DrawableDescriptor | ImageContent): ImageAttribute
```

初始化Image类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameNode-abstract initialize(src: image.PixelMap | ResourceStr | DrawableDescriptor | ImageContent): ImageAttribute--><!--Device-ImageFrameNode-abstract initialize(src: image.PixelMap | ResourceStr | DrawableDescriptor | ImageContent): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | image.PixelMap \| ResourceStr \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| ImageContent | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageAttribute |  |

## initialize

```TypeScript
abstract initialize(src: image.PixelMap | ResourceStr | DrawableDescriptor, value: ImageAIOptions): ImageAttribute
```

初始化Image类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFrameNode-abstract initialize(src: image.PixelMap | ResourceStr | DrawableDescriptor, value: ImageAIOptions): ImageAttribute--><!--Device-ImageFrameNode-abstract initialize(src: image.PixelMap | ResourceStr | DrawableDescriptor, value: ImageAIOptions): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | image.PixelMap \| ResourceStr \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | 是 |  |
| value | ImageAIOptions | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageAttribute |  |

