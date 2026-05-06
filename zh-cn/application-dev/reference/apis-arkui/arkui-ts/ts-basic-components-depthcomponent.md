# DepthComponent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

景深组件利用背景与深度图，生成具有景深空间效果的内容。

> **说明：**
>
> 子组件需要设置[空间效果](./ts-universal-attributes-spatial-effect.md)，才能与景深组件的背景产生交互效果。
>
> 具备基本的计算机图形学知识有助于更好地使用该组件。

**起始版本：** 26.0.0

## 子组件

可以包含子组件。

## 接口

DepthComponent(background: ResourceStr | PixelMap, options?: DepthComponentOptions)

创建景深组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| background | [ResourceStr](ts-types.md#resourcestr) \| [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) | 是 | 背景资源。支持静态图片或3D模型。<br>静态图支持加载PixelMap和ResourceStr的数据源，引用方式请参考[加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。<br>3D模型仅支持加载ResourceStr的数据源，仅支持glTF和glb的3D模型格式。ResourceStr包含Resource和string格式。其中string格式可用于加载本地3D模型，支持绝对路径或file://前缀的沙箱URI，不支持网络资源的加载；Resource格式可以跨包/跨模块访问模型资源文件，推荐以该方式加载本地3D模型。 |
| options | [DepthComponentOptions](#depthcomponentoptions) | 否 | 景深组件配置项。默认值：`{ depthSpace: DepthSpaceType.INSTANCE }`。 |

## DepthComponentOptions

景深组件配置项。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| depthSpace | [DepthSpaceType](#depthspacetype) | 否 | 是 | 景深空间类型。 |

## DepthSpaceType

景深空间类型枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| INSTANCE | 0 | 实例模式。使用当前进程的背景、深度图、相机参数及光照参数。 |

## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### depthMap

depthMap(depthMap: ResourceStr | PixelMap)

设置用于景深计算和渲染的深度图。

> **说明：**
>
> 深度图是用于描述在3D空间中，背景中每个像素点与相机距离的二维矩阵图像。
> 其数据格式为灰阶图，灰度值越大（颜色越白）的像素点距离相机越近。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| depthMap | [ResourceStr](ts-types.md#resourcestr) \| [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) | 是 | 深度图资源或PixelMap对象，引用方式与静态背景图一致。仅背景为静态图时需要设置深度图。深度图需要与背景图的分辨率保持一致。 |

### camera

camera(camera: DepthCameraParams)

设置景深渲染使用的相机参数。

> **说明：**
>
> 以图片作为背景时，相机参数更新不会引起背景的变化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| camera | [DepthCameraParams](#depthcameraparams) | 是 | 相机参数。 |

### light

light(light: DepthLightParams)

设置景深渲染使用的光照参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| light | [DepthLightParams](#depthlightparams) | 是 | 光照参数，包含方向、颜色和强度。 |

### backgroundOffset

backgroundOffset(offset: Position | Edges | LocalizedEdges)

设置背景偏移量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| offset | [Position](ts-types.md#position) \| [Edges](ts-types.md#edges12) \| [LocalizedEdges](ts-types.md#localizededges12) | 是 | 背景偏移量。 |

### backgroundScale

backgroundScale(scale?: ScaleOptions)

设置背景缩放比例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| scale | [ScaleOptions](ts-universal-attributes-transformation.md#scaleoptions对象说明) | 否 | 背景缩放参数。默认值：{ x: 1, y: 1, z: 1, centerX: '50%', centerY: '50%' } |

## DepthCameraParams

相机参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| position | [DepthVector3](ts-universal-attributes-spatial-effect.md#depthvector3) | 否 | 否 | 相机在三维空间中的位置。无单位，其值表示3D空间中的坐标。 |
| quaternion | [DepthVector4](ts-universal-attributes-spatial-effect.md#depthvector4) | 否 | 否 | 相机旋转四元数，按(x, y, z, w)表示。无单位。 |
| yFov | number | 否 | 否 | 相机垂直方向视场角，单位为弧度。 |
| zNear | number | 否 | 否 | 近裁剪面距离。无单位。必须为正数。 |
| zFar | number | 否 | 否 | 远裁剪面距离。无单位。必须为正数。 |

## DepthLightParams

光照参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| direction | [DepthVector3](ts-universal-attributes-spatial-effect.md#depthvector3) | 否 | 否 | 光照方向向量。无单位，其值表示3D空间中的坐标。 |
| color | [DepthColorRGB](ts-universal-attributes-spatial-effect.md#depthcolorrgb) | 否 | 否 | 光照颜色。 |
| intensity | number | 否 | 否 | 光照强度。无单位，取值范围[0, +∞)。<br>建议取值范围[0, 1]，当设置为0时，无光照。 |

## 示例

```ts
// xxx.ets
@Entry
@Component
struct DepthComponentExample {
  build() {
    Column() {
      // 请开发者替换为实际的资源文件
      DepthComponent($r('app.media.background')) {
        Text('Spatial Effect')
          .fontSize(100)
          .spatialEffect({
            position: {
              leftTop: { x: -0.355, y: 0.915, z: -1.941 },
              rightTop: { x: 0.483, y: 1.259, z: -2.295 },
              leftBottom: { x: -0.355, y: -0.281, z: -1.941 },
              rightBottom: { x: 0.483, y: 0.063, z: -2.295 }
            },
            occlusionWeight: 0.5
          })
      }
        .width('100%')
        .height('100%')
        .depthMap($r('app.media.depth_map')) // 请开发者替换为实际的资源文件
        .camera({
          position: { x: 0, y: 0, z: 0 },
          quaternion: { x: 0, y: 0, z: 0, w: 1 },
          yFov: 1.05,
          zNear: 0.1,
          zFar: 100
        })
        .light({
          direction: { x: 0, y: 0, z: -1 },
          color: { red: 255, green: 255, blue: 255 },
          intensity: 1
        })
        .backgroundOffset({ x: 0, y: 0 })
        .backgroundScale({ x: 1, y: 1, z: 1, centerX: '50%', centerY: '50%' })
    }
    .width('100%')
    .padding(16)
  }
}
```
