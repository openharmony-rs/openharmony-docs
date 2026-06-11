# 空间效果 (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

用于为组件设置空间效果参数。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 空间效果仅作用于[DepthComponent](./ts-basic-components-depthcomponent-sys.md)的子组件，且仅当DepthComponent相关参数设置正确才能生效。
>
> - 空间效果不支持[Web](../../../web/web-component-overview.md)、[XComponent](./ts-basic-components-xcomponent.md)、[RichEditor](./ts-basic-components-richeditor.md)、[RichText](./ts-basic-components-richtext.md)、[Video](./ts-media-components-video.md)、[Component3D](./ts-basic-components-component3d.md)、[EmbeddedComponent](./ts-container-embedded-component.md)组件。
>
> - 本模块为系统接口。

**起始版本：** 26.0.0

## spatialEffect

ArkTS-Dyn: spatialEffect(params: SpatialEffectParams | undefined): T

ArkTS-Sta: spatialEffect(params: SpatialEffectParams | undefined): this

为组件设置空间效果。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| params | [SpatialEffectParams](#spatialeffectparams) \| undefined | 是 | 空间效果参数。参数为undefined时，移除空间效果。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: T</br>ArkTS-Sta: this | 返回当前组件。 |

## SpatialEffectParams

空间效果参数。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| position | ArkTS-Dyn: [SpatialPosition](#spatialposition) \| number</br>ArkTS-Sta: [SpatialPosition](#spatialposition) \| double | 否 | 否 | 组件空间位置。支持结构体类型或数值类型的深度信息。<br/> 结构体类型[SpatialPosition](#spatialposition)，由四个角定义空间位置。 <br/> 数值类型，定义组件空间深度信息。|
| occlusionWeight | ArkTS-Dyn: number</br>ArkTS-Sta: double | 否 | 是 | 空间效果的遮挡权重。取值范围：[0, 1]，默认值：0。<br>0表示不会被遮挡，1表示会被完全遮挡，中间值表示部分遮挡。 |

## SpatialPosition

三维空间中的四角位置。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| leftTop | [DepthVector3](#depthvector3) | 否 | 否 | 左上角在三维空间中的位置。无单位，其值表示3D空间中的坐标。 |
| rightTop | [DepthVector3](#depthvector3) | 否 | 否 | 右上角在三维空间中的位置。无单位，其值表示3D空间中的坐标。 |
| leftBottom | [DepthVector3](#depthvector3) | 否 | 否 | 左下角在三维空间中的位置。无单位，其值表示3D空间中的坐标。 |
| rightBottom | [DepthVector3](#depthvector3) | 否 | 否 | 右下角在三维空间中的位置。无单位，其值表示3D空间中的坐标。 |

## DepthVector3

景深空间中的三维向量。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| x | ArkTS-Dyn: number</br>ArkTS-Sta: double | 否 | 否 | X分量。无单位，其值表示3D空间中的坐标。 |
| y | ArkTS-Dyn: number</br>ArkTS-Sta: double | 否 | 否 | Y分量。无单位，其值表示3D空间中的坐标。 |
| z | ArkTS-Dyn: number</br>ArkTS-Sta: double | 否 | 否 | Z分量。无单位，其值表示3D空间中的坐标。 |

## DepthVector4

景深空间中的四维向量。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| x | ArkTS-Dyn: number</br>ArkTS-Sta: double | 否 | 否 | X分量。无单位，其值表示3D空间中的坐标。 |
| y | ArkTS-Dyn: number</br>ArkTS-Sta: double | 否 | 否 | Y分量。无单位，其值表示3D空间中的坐标。 |
| z | ArkTS-Dyn: number</br>ArkTS-Sta: double | 否 | 否 | Z分量。无单位，其值表示3D空间中的坐标。 |
| w | ArkTS-Dyn: number</br>ArkTS-Sta: double | 否 | 否 | W分量。无单位，其值表示3D空间中的坐标。 |

## DepthColorRGB

景深空间中的RGB颜色。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| red | ArkTS-Dyn: number</br>ArkTS-Sta: int | 否 | 否 | 红色分量，取值范围：[0, 255]。 |
| green | ArkTS-Dyn: number</br>ArkTS-Sta: int | 否 | 否 | 绿色分量，取值范围：[0, 255]。 |
| blue | ArkTS-Dyn: number</br>ArkTS-Sta: int | 否 | 否 | 蓝色分量，取值范围：[0, 255]。 |

## 示例

见DepthComponent[示例](./ts-basic-components-depthcomponent-sys.md#示例)。
