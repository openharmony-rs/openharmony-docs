# @ohos.arkui.componentSnapshot

本模块提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。组件截图只能够截取组件大小的区域，如果组件的绘制超出了它的区域，或子组件的绘制超出了父组件的区域，这些在组件区域外绘制的内容不会在截图中呈现。兄弟节点堆叠在组件区域内，截图不会显示兄弟组件。

缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的仍然是图形变换前的效果。

组件截图典型使用场景（如长截图）及最佳实践请参考[使用组件截图](../../../ui/arkts-uicontext-component-snapshot.md)。
> **说明：**  
>  
> - 对于使用[XComponent](../arkts-components/arkts-arkui-xcomponent.md)的场景，例如：Video或者相机流媒体展示类组件，不建议使用组件截图相关接口，建议使用  
> [createPixelMapFromSurface](../../apis-image-kit/arkts-apis/arkts-image-image-createpixelmapfromsurface-f.md#createpixelmapfromsurface)  
> 直接获取图片。  
>  
> - 如果组件自身内容不能填满组件大小区域，那么剩余位置截图返回的内容为透明像素。如果组件使用了[图像效果](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)类属性或其他的效果类属性，则可能产生非用户预期的截图结果。请排查是否需要填充组件透明内容区域，或  
> 使用窗口截图接口[snapshot](arkts-arkui-window-window-i.md#snapshot)替代。  
>  
> - 示例效果请以真机运行为准，当前 DevEco Studio预览器不支持。

**起始版本：** 10

<!--Device-unnamed-declare namespace componentSnapshot--><!--Device-unnamed-declare namespace componentSnapshot-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createFromBuilder](arkts-arkui-componentsnapshot-createfrombuilder-f.md#createfrombuilder) | 在应用后台渲染CustomBuilder自定义组件，并输出其截图。通过回调返回结果并支持在回调中获取离屏组件绘制区域坐标和大小。 |
| [createFromBuilder](arkts-arkui-componentsnapshot-createfrombuilder-f.md#createfrombuilder-1) | 在应用后台渲染CustomBuilder自定义组件，并输出其截图。通过Promise返回结果，支持获取离屏组件绘制区域的坐标和大小。 |
| [get](arkts-arkui-componentsnapshot-get-f.md#get) | 获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。通过回调返回结果。 |
| [get](arkts-arkui-componentsnapshot-get-f.md#get-1) | 获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。通过Promise返回结果。 |
| [getSync](arkts-arkui-componentsnapshot-getsync-f.md#getsync) | 获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。同步等待截图完成返回[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColorModeOptions](arkts-arkui-componentsnapshot-colormodeoptions-i.md) | 定义截图时所使用的色彩空间。 |
| [DynamicRangeModeOptions](arkts-arkui-componentsnapshot-dynamicrangemodeoptions-i.md) | 定义截图所使用的动态范围模式。 |
| [LocalizedSnapshotRegion](arkts-arkui-componentsnapshot-localizedsnapshotregion-i.md) | 定义组件截图的矩形区域，start和end的值在布局方向为LTR时指定为left和right，在布局方向为RTL时指定为right和left。 |
| [SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | 定义截图额外选项。 |
| [SnapshotRegion](arkts-arkui-componentsnapshot-snapshotregion-i.md) | 定义组件截图的矩形区域。 |
| [SnapshotSizeLimitation](arkts-arkui-componentsnapshot-snapshotsizelimitation-i.md) | 定义组件截图的尺寸限制。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SnapshotRegionType](arkts-arkui-componentsnapshot-snapshotregiontype-t.md) | 表示组件截图区域。 |

