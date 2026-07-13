# @ohos.arkui.componentSnapshot

本模块提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。组件截图只能够截取组件大小的区域，如果组件的绘制超出了它的区域，或子组件的绘制超出了父组件的区域，这些在组件区域外绘制的内容不会在截图中呈现。兄弟节点堆叠在组
件区域内，截图不会显示兄弟组件。

缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的仍然是图形变换前的效果。

组件截图典型使用场景（如长截图）及最佳实践请参考[使用组件截图](../../../../ui/arkts-uicontext-component-snapshot.md)。

> **说明：**
>
> - 对于使用[XComponent](xcomponent)的场景，例如：Video或者相机流媒体展示类组件，不建议使用组件截图相关接口，建议使用
> [createPixelMapFromSurface](../../apis-image-kit/arkts-apis/arkts-image-createpixelmapfromsurface-f.md#createpixelmapfromsurface-1)
> 直接获取图片。
>
> - 如果组件自身内容不能填满组件大小区域，那么剩余位置截图返回的内容为透明像素。如果组件使用了[图像效果](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)类属性或其他的效果类属性，则可能产生非用户预期的截图结果。请排查是否需要填充组件透明内容区域，或
> 使用窗口截图接口[snapshot](arkts-arkui-window-i.md#snapshot-1)替代。
>
> - 示例效果请以真机运行为准，当前 DevEco Studio预览器不支持。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createFromBuilder](arkts-arkui-createfrombuilder-f.md#createfrombuilder-1) | 在应用后台渲染CustomBuilder自定义组件，并输出其截图。通过回调返回结果并支持在回调中获取离屏组件绘制区域坐标和大小。@link @ohos.arkui.UIContext}中的&gt; [getComponentSnapshot](arkts-arkui-uicontext-c.md#getcomponentsnapshot-1)方法&gt; 获取当前UI上下文关联的[ComponentSnapshot](arkts-arkui-componentsnapshot-c.md)对象。&gt;&gt; - 由于需要等待组件构建、渲染成功，离屏截图的回调有500ms以内的延迟。&gt;&gt; - builder中的组件不支持设置动画相关的属性，如[transition](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。&gt;&gt; - 部分执行耗时任务的组件可能无法及时在截图前加载完成，因此会截取不到加载成功后的图像。例如：加载网络图片的[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)组件、[Web](../../apis-arkweb/arkts-components/arkts-arkweb-web.md)组件。 |
| [createFromBuilder](arkts-arkui-createfrombuilder-f.md#createfrombuilder-2) | 在应用后台渲染CustomBuilder自定义组件，并输出其截图。通过Promise返回结果，支持获取离屏组件绘制区域的坐标和大小。@link @ohos.arkui.UIContext}中的&gt; [getComponentSnapshot](arkts-arkui-uicontext-c.md#getcomponentsnapshot-1)方法&gt; 获取当前UI上下文关联的[ComponentSnapshot](arkts-arkui-componentsnapshot-c.md)对象。&gt;&gt; - 由于需要等待组件构建、渲染成功，离屏截图的回调有500ms以内的延迟。&gt;&gt; - builder中的组件不支持设置动画相关的属性，如[transition](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。&gt;&gt; - 部分执行耗时任务的组件可能无法及时在截图前加载完成，因此会截取不到加载成功后的图像。例如：加载网络图片的[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)组件、[Web](../../apis-arkweb/arkts-components/arkts-arkweb-web.md)组件。 |
| [get](arkts-arkui-get-f.md#get-1) | 获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。通过回调返回结果。@link @ohos.arkui.UIContext}中的&gt; [getComponentSnapshot](arkts-arkui-uicontext-c.md#getcomponentsnapshot-1)方法&gt; 获取当前UI上下文关联的[ComponentSnapshot](arkts-arkui-componentsnapshot-c.md)对象。&gt;&gt; - 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。 |
| [get](arkts-arkui-get-f.md#get-2) | 获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。通过Promise返回结果。@link @ohos.arkui.UIContext}中的&gt; [getComponentSnapshot](arkts-arkui-uicontext-c.md#getcomponentsnapshot-1)方法&gt; 获取当前UI上下文关联的[ComponentSnapshot](arkts-arkui-componentsnapshot-c.md)对象。&gt;&gt; - 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。 |
| [getSync](arkts-arkui-getsync-f.md#getsync-1) | 获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。同步等待截图完成返回[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColorModeOptions](arkts-arkui-colormodeoptions-i.md) | 定义截图时所使用的色彩空间。 |
| [DynamicRangeModeOptions](arkts-arkui-dynamicrangemodeoptions-i.md) | 定义截图所使用的动态范围模式。 |
| [LocalizedSnapshotRegion](arkts-arkui-localizedsnapshotregion-i.md) | 定义组件截图的矩形区域，start和end的值在布局方向为LTR时指定为left和right，在布局方向为RTL时指定为right和left。@link @ohos.arkui.UIContext}实例，并使用[getComponentSnapshot](arkts-arkui-uicontext-c.md#getcomponentsnapshot-1)&gt; 获取绑定实例的componentSnapshot。 |
| [SnapshotOptions](arkts-arkui-snapshotoptions-i.md) | 定义截图额外选项。 |
| [SnapshotRegion](arkts-arkui-snapshotregion-i.md) | 定义组件截图的矩形区域。 |
| [SnapshotSizeLimitation](arkts-arkui-snapshotsizelimitation-i.md) | 定义组件截图的尺寸限制。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SnapshotRegionType](arkts-arkui-snapshotregiontype-t.md) | 表示组件截图区域。 |

