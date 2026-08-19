# PixelMapDrawableDescriptor

支持通过传入PixelMap创建PixelMapDrawableDescriptor对象。继承自[DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。

**继承/实现关系：** PixelMapDrawableDescriptor extends [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class PixelMapDrawableDescriptor--><!--Device-unnamed-export declare class PixelMapDrawableDescriptor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(src?: image.PixelMap | ResourceStr)
```

PixelMapDrawableDescriptor的构造函数，通过PixelMap类型或者ResourceStr创建。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PixelMapDrawableDescriptor-constructor(src?: image.PixelMap | ResourceStr)--><!--Device-PixelMapDrawableDescriptor-constructor(src?: image.PixelMap | ResourceStr)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | image.PixelMap \| ResourceStr | 否 | PixelMap类型参数，存储PixelMap图片数据。 支持应用资源、系统资源、沙箱路径（file://&lt;bundleName&gt;/&lt;sandboxPath&gt;）和Base64字符串 用于创建PixelMapDrawableDescriptor。<br>**起始版本：** 26.0.0 |

