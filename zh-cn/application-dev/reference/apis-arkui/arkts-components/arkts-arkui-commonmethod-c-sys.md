# CommonMethod

CommonMethod.

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## advancedBlendMode

```TypeScript
advancedBlendMode(effect: BlendMode | Blender, type?: BlendApplyType): T
```

将当前组件的内容（包含子节点内容）与下方画布（可能为离屏画布）已有内容进行混合。不能与[blendMode](arkts-arkui-commonmethod-c.md#blendmode)接口同时使用，同时设置时仅advancedBlendMode效果生效。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本13开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [BlendMode](arkts-arkui-blendmode-e.md) &#124; [Blender](arkts-arkui-blender-t-sys.md) | 是 | 入参类型为BlendMode时表示混合模式，默认不进行混合操作。默认值：BlendMode.NONE，即不应用特殊混合效果，组件内容按默认方式绘制。<br>入参类型为Blender时表示混合器类型，用于描述混合效果。<br>需要使用uiEffect模块中的方法创建Blender实例。例如：[uiEffect.createBrightnessBlender](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-uieffect-createbrightnessblender-f-sys.md)。使用自定义object作为入参不会生效。 |
| type | [BlendApplyType](arkts-arkui-blendapplytype-e.md) | 否 | 混合效果blendMode实现方式是否离屏。<br>默认值：BlendApplyType.FAST <br>**说明：** <br>1. 设置为BlendApplyType.FAST，不离屏。<br>2. 设置为BlendApplyType.OFFSCREEN，会创建当前组件大小的离屏画布，再将当前组件（含子组件）的内容绘制到离屏画布上，再用指定的混合效果（BlendMode或Blender）与下方画布已有内容进行混合。<br>3. 不离屏情况下对文字类组件中emoji表情不生效。<br>4. 相比BlendApplyType.OFFSCREEN，设置为BlendApplyType.OFFSCREEN_WITH_BACKGROUND，系统在创建与当前组件大小一致的离屏画布时，会先复制一份带有背景的画布作为初始化底色（BlendApplyType.OFFSCREEN类型的画布初始为透明背景），随后在此基础上进行混合操作。两者在其他功能特性上保持一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件，用于链式调用。 |

## constructor

```TypeScript
constructor()
```

constructor.

**起始版本：** 9

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLight

```TypeScript
edgeLight(params: EdgeLightParams | undefined): T
```

为组件添加边缘流光效果。边缘流光效果会在组件的边缘创建发光效果，从指定位置开始并沿边缘延伸，此效果可以增强组件的视觉吸引力并突出显示重要组件。

> **说明：** 
> 
> - 仅设置edgeLight不会产生边缘流光效果，需结合[animateTo](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#animateto)更改position参数达到流光效果。可参考[示例4（设置组件边缘流光效果）](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect-sys.md#示例4设置组件边缘流光效果)。
> 
> - 当position参数以对角线方式变更时（如从TOP_LEFT变更到BOTTOM_RIGHT），边缘流光将沿倾斜角45°的方式运行。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [EdgeLightParams](arkts-arkui-edgelightparams-i-sys.md) &#124; undefined | 是 | 定义边缘流光效果的位置、长度、强度、颜色和厚度。<br>当params的值为undefined时，移除边缘流光效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件，用于链式调用。 |

## excludeFromRenderGroup

```TypeScript
excludeFromRenderGroup(exclude: boolean | undefined): T
```

设置当前组件和其子组件是否从祖先组件的节点组中剔除。需搭配祖先组件设置节点组[renderGroup](arkts-arkui-commonmethod-c.md#rendergroup)属性使用，单独使用无效果。

从节点组剔除后，当前组件和子组件不再影响祖先组件的离屏画布，不会引起节点组的缓存失效，从而达到复用节点组缓存的目的。如果当前组件的显示区域只占节点组绘制内容显示区域的一部分，且当前组件及子组件的显示效果频繁更新，设置excludeFromRenderGroup属性有助于绘制性能优化。

不设置该属性时，默认当前组件和其子组件不从祖先组件的节点组中剔除。

> **说明：** 
> 
> 设置excludeFromRenderGroup为true的组件及其子组件的绘制内容不能超过该组件本身的边界范围，否则会出现显示内容被裁剪的问题。例如当子组件通过
> [translate](arkts-arkui-commonmethod-c.md#translate)或
> [scale](arkts-arkui-commonmethod-c.md#scale)等属性导致子组件超出当前组件范围，或当前组件上有
> [shadow](arkts-arkui-commonmethod-c.md#shadow)、
> [pixelStretchEffect](arkts-arkui-commonmethod-c.md#pixelstretcheffect)等属性导致当前组件的绘制内容超出组件
> 边界时，可能出现显示内容被裁剪的问题。此类场景不应设置excludeFromRenderGroup属性为true。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exclude | boolean &#124; undefined | 是 | 设置当前组件及其子组件是否从祖先组件的节点组中剔除。<br>true表示当前组件及其子组件从祖先组件的节点组中剔除，不属于祖先组件的节点组；false表示当前组件及其子组件归属于祖先组件的节点组。<br>当exclude的值为undefined时，按false处理。<br>**说明：** <br>需搭配祖先组件设置节点组renderGroup属性使用，单独使用无效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件，用于链式调用。 |

## spatialEffect

```TypeScript
spatialEffect(params: SpatialEffectParams | undefined): T
```

将空间效果应用于组件。用于为组件设置空间效果参数。

> **说明：** 
> 
> - 空间效果仅作用于[DepthComponent](./ts-basic-components-depthcomponent-sys.md)的子组件，且仅当DepthComponent相关参数设置正确才能生效。
> 
> - 空间效果不支持[Web](../../../web/web-component-overview.md)、[XComponent](./ts-basic-components-xcomponent.md)、[RichEditor](./ts-basic-components-richeditor.md)、[RichText](./ts-basic-components-richtext.md)、[Video](./ts-media-components-video.md)、[Component3D](./ts-basic-components-component3d.md)、[EmbeddedComponent](./ts-container-embedded-component.md)组件。
> 
> - 本模块为系统接口。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SpatialEffectParams](arkts-arkui-spatialeffectparams-i-sys.md) &#124; undefined | 是 | 空间效果参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## useUnionEffect

```TypeScript
useUnionEffect(value: boolean | undefined): T
```

表示是否使用祖先组件UnionEffectContainer的融合效果，即是否作为UnionEffectContainer做形状融合的一部分，参与融合形态计算。

未设置时，默认不使用祖先组件UnionEffectContainer的融合效果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean &#124; undefined | 是 | 表示是否使用祖先组件UnionEffectContainer的融合效果。<br>取值为true时，当前组件使用祖先组件UnionEffectContainer的融合效果，在祖先组件UnionEffectContainer计算形状时会作为UnionEffectContainer的一部分；若当前组件不存在祖先UnionEffectContainer，则设置useUnionEffect为true不产生融合效果。<br>取值为false时，当前组件不使用祖先组件UnionEffectContainer的融合效果。<br>设置为undefined时恢复为不使用祖先组件UnionEffectContainer的融合效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件，用于链式调用。 |

## useUnionEffect

```TypeScript
useUnionEffect(value: boolean | undefined, options?: GravityCenterOptions): T
```

表示是否使用祖先组件UnionEffectContainer的融合效果，是否作为UnionEffectContainer做形状融合的一部分，参与融合形态计算。当不存在祖先组件UnionEffectContainer时，设置该属性不产生效果。

未设置时，默认不使用祖先组件UnionEffectContainer的融合效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean &#124; undefined | 是 | 是否使用祖先组件UnionEffectContainer的融合效果。<br>取值为true时，当前组件使用祖先组件UnionEffectContainer的融合效果，在祖先组件UnionEffectContainer计算形状时会作为UnionEffectContainer的一部分；若当前组件不存在祖先UnionEffectContainer，则取值为true不产生融合效果。<br>取值为false时，当前组件不使用祖先组件UnionEffectContainer的融合效果。<br>设置为undefined时，恢复为不使用祖先组件UnionEffectContainer的融合效果。 |
| options | [GravityCenterOptions](arkts-arkui-gravitycenteroptions-i-sys.md) | 否 | 引力中心参数。<br>未设置时，不启用引力中心功能。<br>**说明：** <br>此参数必须与[unionMode](arkts-arkui-unioneffectcontainer-comp-attribute.md#unionmode)一起使用，且unionMode须为UnionMode.GRAVITY_UNION，同时value须为true时才生效，单独设置或不满足前提条件时不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件，用于链式调用。 |
