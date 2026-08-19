# PictureDrawableDescriptor

支持通过传入Picture对象创建PictureDrawableDescriptor对象。继承自 [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。

**继承/实现关系：** PictureDrawableDescriptor extends [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class PictureDrawableDescriptor--><!--Device-unnamed-export declare class PictureDrawableDescriptor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(src: image.Picture)
```

PictureDrawableDescriptor的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PictureDrawableDescriptor-constructor(src: image.Picture)--><!--Device-PictureDrawableDescriptor-constructor(src: image.Picture)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | image.Picture | 是 | 用于创建PictureDrawableDescriptor的Picture对象。 |

## setHdrComposition

```TypeScript
setHdrComposition(config: HdrCompositionConfig): void
```

设置HDR合成配置。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PictureDrawableDescriptor-setHdrComposition(config: HdrCompositionConfig): void--><!--Device-PictureDrawableDescriptor-setHdrComposition(config: HdrCompositionConfig): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [HdrCompositionConfig](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-hdrcompositionconfig-i.md) | 是 | HDR合成配置。 |

