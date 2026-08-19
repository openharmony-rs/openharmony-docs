# DepthComponent（系统接口）

## DepthComponent

```TypeScript
@ComponentBuilder
export declare function DepthComponent(
    background: ResourceStr | PixelMap,
    options?: DepthComponentOptions,
    content_?: CustomBuilder,
): DepthComponentAttribute
```

创建景深组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function DepthComponent(    background: ResourceStr | PixelMap,    options?: DepthComponentOptions,    content_?: CustomBuilder,): DepthComponentAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function DepthComponent(    background: ResourceStr | PixelMap,    options?: DepthComponentOptions,    content_?: CustomBuilder,): DepthComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| background | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) | 是 | 背景资源。支持静态图片或3D模型。  静态图支持加载PixelMap和ResourceStr的数据源，引用方式请参考[加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。  3D模型仅支持加载ResourceStr的数据源，仅支持glTF和glb的3D模型格式。ResourceStr包含Resource和string格式。其中string格式可用于加载本地3D模型，支持绝对路径或file://前缀的沙箱 URI，不支持网络资源的加载；Resource格式可以跨包/跨模块访问模型资源文件，推荐以该方式加载本地3D模型。 |
| options | [DepthComponentOptions](arkts-na-depthcomponent-depthcomponentoptions-i-sys.md) | 否 | 景深组件配置项。默认值：`{ depthSpace: DepthSpaceType.INSTANCE }`。 |
| content_ | CustomBuilder | 否 | Subcomponents of DepthComponent. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DepthComponentAttribute](arkts-na-depthcomponent-depthcomponentattribute-i.md) | 景深组件属性配置项 |

