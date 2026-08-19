# XComponent

**XComponent**提供用于图形绘制和媒体数据写入的[surface](../../../ui/napi-xcomponent-guidelines.md#overview)，XComponent负责将其嵌入到视图中，支持应用自定义surface的位置和大小。同时支持AI图像分析、HDR视频亮度调节、防截屏录屏隐私保护、画布自绘制等能力，适用于视频播放、相机预览、游戏渲染、图像AI识别等需要高性能自绘制和媒体内容展示的场景。具体指南请参考[自定义渲染（XComponent）文档](../../../ui/napi-xcomponent-guidelines.md)。 > **说明：**

## 子组件 不支持

## XComponent

```TypeScript
XComponent(value: { id: string; type: string; libraryname?: string; controller?: XComponentController })
```

构造参数

**起始版本：** 8

**废弃版本：** 12

**替代接口：** (value: { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController })

<!--Device-XComponentInterface-(value: { id: string; type: string; libraryname?: string; controller?: XComponentController }): XComponentAttribute--><!--Device-XComponentInterface-(value: { id: string; type: string; libraryname?: string; controller?: XComponentController }): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { id: string; type: string; libraryname?: string; controller?: XComponentController } | 是 | 表示XComponent的选项。 |

## XComponent

```TypeScript
XComponent(value: { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController })
```

创建**XComponent**组件，其生命周期回调可以从native侧触发。 从API版本12开始，该接口不再维护。建议使用[XComponent(options: XComponentOptions)](../../../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#xcomponent12)替代。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentInterface-(value: { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController }): XComponentAttribute--><!--Device-XComponentInterface-(value: { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController }): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController } | 是 | 表示XComponent的选项。 |

## XComponent

```TypeScript
XComponent(options: XComponentOptions)
```

创建**XComponent**组件，允许您在ArkTS侧获取**SurfaceId**值，注册**XComponent**所持有的surface的生命周期回调以及触摸、鼠标、按键等组件事件的回调，并配置AI分析器功能。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentInterface-(options: XComponentOptions): XComponentAttribute--><!--Device-XComponentInterface-(options: XComponentOptions): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [XComponentOptions](arkts-arkui-xcomponentoptions-i.md) | 是 | 表示XComponent的选项。 |

## XComponent

```TypeScript
XComponent(params: NativeXComponentParameters)
```

在native侧获取**XComponent**节点实例，并注册**XComponent**所持有的surface的生命周期回调以及触摸、鼠标、按键等组件事件的回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentInterface-(params: NativeXComponentParameters): XComponentAttribute--><!--Device-XComponentInterface-(params: NativeXComponentParameters): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [NativeXComponentParameters](arkts-arkui-nativexcomponentparameters-i.md) | 是 | 表示用于native开发的XComponent构造参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [NativeXComponentParameters](arkts-arkui-nativexcomponentparameters-i.md) | 定义native xcomponent参数。使用此类构造参数创建的XComponent可以将其对应的FrameNode对象传递到Native侧，从而能够使用NDK接口进行surface生命周期相关设置和[组件事件监听](../../../ui/ndk-listen-to-component-events.md)。 |
| [SurfaceConfig](arkts-arkui-surfaceconfig-i.md) | Surface配置。 |
| [SurfaceRect](arkts-arkui-surfacerect-i.md) | 描述XComponent所持有的surface的矩形。 |
| [SurfaceRotationOptions](arkts-arkui-surfacerotationoptions-i.md) | 定义屏幕旋转时是否锁定当前XComponent所持有的surface的方向。 |
| [XComponentOptions](arkts-arkui-xcomponentoptions-i.md) | 定义XComponent的选项。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnNativeLoadCallback](arkts-arkui-onnativeloadcallback-t.md) | XComponent的Native加载完成后回调事件，用于向开发者传递XComponent实例对象的context。与[onSurfaceCreated](arkts-arkui-xcomponentcontroller-c.md#onsurfacecreated)的区别：onLoad回调参数为context对象，适用于设置libraryname参数的场景；onSurfaceCreated回调参数为surfaceId，适用于未设置libraryname参数的场景。onLoad触发时机早于onSurfaceCreated。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HdrType](arkts-arkui-hdrtype-e.md) | 设置XComponent的HDR类型。 |

