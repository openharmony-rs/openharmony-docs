# DepthComponent

Defines DepthComponent Component.


## DepthComponent

```TypeScript
DepthComponent(background: ResourceStr | PixelMap, options?: DepthComponentOptions)
```

创建景深组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthComponentInterface-(background: ResourceStr | PixelMap, options?: DepthComponentOptions): DepthComponentAttribute--><!--Device-DepthComponentInterface-(background: ResourceStr | PixelMap, options?: DepthComponentOptions): DepthComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| background | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| PixelMap | 是 | 背景资源。支持静态图片或3D模型。 * 静态图支持加载PixelMap和ResourceStr的数据源，引用方式请参考[加载图片资源](docroot://ui/arkts-graphics-display.md#加载图片资源)。 * 3D模型仅支持加载ResourceStr的数据源，仅支持glTF和glb的3D模型格式。ResourceStr包含Resource和string格式。其中string格式可用于加载本地3D模型，支持绝对路径或file://前缀的沙箱 URI，不支持网络资源的加载；Resource格式可以跨包/跨模块访问模型资源文件，推荐以该方式加载本地3D模型。  |
| options | [DepthComponentOptions](arkts-arkui-depthcomponentoptions-i-sys.md) | 否 | 景深组件配置项。默认值：`{ depthSpace: DepthSpaceType.INSTANCE }`。  |

## 汇总

- [CameraBufferCrop](arkts-arkui-depthcomponent-camerabuffercrop-i-sys.md)
- [CropOffset](arkts-arkui-depthcomponent-cropoffset-i-sys.md)
- [DepthCameraParams](arkts-arkui-depthcomponent-depthcameraparams-i-sys.md)
- [DepthComponentCompleteEvent](arkts-arkui-depthcomponent-depthcomponentcompleteevent-i-sys.md)
- [DepthComponentErrorEvent](arkts-arkui-depthcomponent-depthcomponenterrorevent-i-sys.md)
- [DepthComponentOptions](arkts-arkui-depthcomponent-depthcomponentoptions-i-sys.md)
- [DepthLightParams](arkts-arkui-depthcomponent-depthlightparams-i-sys.md)
- [DepthComponentCompleteCallback](arkts-arkui-depthcomponent-depthcomponentcompletecallback-t-sys.md)
- [DepthComponentErrorCallback](arkts-arkui-depthcomponent-depthcomponenterrorcallback-t-sys.md)
- [DepthMapCallback](arkts-arkui-depthcomponent-depthmapcallback-t-sys.md)
- [DepthSpaceType](arkts-arkui-depthcomponent-depthspacetype-e-sys.md)
