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
| background | ResourceStr \| PixelMap | 是 | 背景资源。支持静态图片或3D模型。  静态图支持加载PixelMap和ResourceStr的数据源，引用方式请参考[加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。  3D模型仅支持加载ResourceStr的数据源，仅支持glTF和glb的3D模型格式。ResourceStr包含Resource和string格式。其中string格式可用于加载本地3D模型，支持绝对路径或file://前缀的沙箱 URI，不支持网络资源的加载；Resource格式可以跨包/跨模块访问模型资源文件，推荐以该方式加载本地3D模型。 |
| options | [DepthComponentOptions](arkts-arkui-depthcomponentoptions-i-sys.md) | 否 | 景深组件配置项。默认值：`{ depthSpace: DepthSpaceType.INSTANCE }`。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CameraBufferCrop](arkts-arkui-camerabuffercrop-i-sys.md) | 相机移轴裁剪参数。 |
| [CropOffset](arkts-arkui-cropoffset-i-sys.md) | 裁剪偏移量。 |
| [DepthCameraParams](arkts-arkui-depthcameraparams-i-sys.md) | 相机参数。 |
| [DepthComponentCompleteEvent](arkts-arkui-depthcomponentcompleteevent-i-sys.md) | 背景资源加载成功的事件信息。 |
| [DepthComponentErrorEvent](arkts-arkui-depthcomponenterrorevent-i-sys.md) | 背景资源加载失败的事件信息。 |
| [DepthComponentOptions](arkts-arkui-depthcomponentoptions-i-sys.md) | 景深组件配置项。 |
| [DepthLightParams](arkts-arkui-depthlightparams-i-sys.md) | 光照参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DepthComponentCompleteCallback](arkts-arkui-depthcomponentcompletecallback-t-sys.md) | 背景资源加载成功的回调函数。使用callback异步回调。 |
| [DepthComponentErrorCallback](arkts-arkui-depthcomponenterrorcallback-t-sys.md) | 背景资源加载失败的回调函数。使用callback异步回调。 |
| [DepthMapCallback](arkts-arkui-depthmapcallback-t-sys.md) | 深度图资源加载完成时的回调函数。使用callback异步回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DepthSpaceType](arkts-arkui-depthspacetype-e-sys.md) | 景深空间类型枚举。 |

