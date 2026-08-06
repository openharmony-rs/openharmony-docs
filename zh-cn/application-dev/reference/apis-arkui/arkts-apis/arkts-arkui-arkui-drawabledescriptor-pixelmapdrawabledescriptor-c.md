# PixelMapDrawableDescriptor

支持通过传入PixelMap创建PixelMapDrawableDescriptor对象。继承自[DrawableDescriptor]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** PixelMapDrawableDescriptor extends [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class PixelMapDrawableDescriptor extends DrawableDescriptor--><!--Device-unnamed-export declare class PixelMapDrawableDescriptor extends DrawableDescriptor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(src?: image.PixelMap | ResourceStr)
```

PixelMapDrawableDescriptor的构造函数，通过PixelMap类型或者ResourceStr创建。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PixelMapDrawableDescriptor-constructor(src?: image.PixelMap | ResourceStr)--><!--Device-PixelMapDrawableDescriptor-constructor(src?: image.PixelMap | ResourceStr)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | image.PixelMap \| ResourceStr | 否 | PixelMap类型参数，存储PixelMap图片数据。支持应用资源、系统资源、沙箱路径（file://\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_/\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_）和Base64字符串用于创建PixelMapDrawableDescriptor。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 26.0.0 |

