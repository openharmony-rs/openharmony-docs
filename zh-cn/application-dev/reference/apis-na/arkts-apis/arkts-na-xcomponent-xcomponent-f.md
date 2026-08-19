# XComponent

## XComponent

```TypeScript
@ComponentBuilder
export declare function XComponent(
    params: XComponentParameters | XComponentOptions | NativeXComponentParameters
): XComponentAttribute
```

提供用于图形绘制和媒体数据写入的Surface，XComponent负责将其嵌入到视图中，支持应用自定义Surface位置和大小。 同时支持AI图像分析、HDR视频亮度调节、防截屏录屏隐私保护、画布自绘制等能力， 适用于视频播放、相机预览、游戏渲染、图像AI识别等需要高性能自绘制和媒体内容展示的场景。 创建XComponent组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function XComponent(    params: XComponentParameters | XComponentOptions | NativeXComponentParameters): XComponentAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function XComponent(    params: XComponentParameters | XComponentOptions | NativeXComponentParameters): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [XComponentParameters](arkts-na-xcomponent-xcomponentparameters-i.md) \| [XComponentOptions](arkts-na-xcomponent-xcomponentoptions-i.md) \| [NativeXComponentParameters](arkts-na-xcomponent-nativexcomponentparameters-i.md) | 是 | 用于 创建XComponent的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [XComponentAttribute](arkts-na-xcomponent-xcomponentattribute-i.md) | XComponent的属性。 |


## XComponent

```TypeScript
@Builder
export declare function XComponent(
    style: CustomBuilderT<XComponentAttribute>
): XComponentAttribute
```

定义XComponent组件。要求在组件属性设置开始时调用setXComponentOptions， 并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function XComponent(    style: CustomBuilderT<XComponentAttribute>): XComponentAttribute--><!--Device-unnamed-@Builderexport declare function XComponent(    style: CustomBuilderT<XComponentAttribute>): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[XComponentAttribute](arkts-na-xcomponent-xcomponentattribute-i.md)&gt; | 是 | 用于设置XComponent属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [XComponentAttribute](arkts-na-xcomponent-xcomponentattribute-i.md) | XComponent的属性。 |

