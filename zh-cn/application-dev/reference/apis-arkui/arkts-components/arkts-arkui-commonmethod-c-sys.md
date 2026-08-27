# CommonMethod

CommonMethod.

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## advancedBlendMode

```TypeScript
advancedBlendMode(effect: BlendMode | Blender, type?: BlendApplyType): T
```

将当前组件的内容（包含子节点内容）与下方画布（可能为离屏画布）已有内容进行混合。不能与 [blendMode](arkts-arkui-commonmethod-c.md#blendmode)接口同时使用。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本13开始，该接口支持在ArkTS卡片中使用。

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [BlendMode](arkts-arkui-blendmode-e.md) \| [Blender](arkts-arkui-blender-t-sys.md) | 是 | 入参类型为BlendMode时表示混合模式。默认值：BlendMode.NONE 入参类型为Blender时表示混合器类型，用于描 述混合效果。需要使用uiEffect模块中的方法创建Blender实例。例如： [uiEffect.createBrightnessBlender](../../../reference/apis-arkgraphics2d/js-apis-uiEffect-sys.md#uieffectcreatebrightnessblender)。 使用自定义object作为入参不会生效。 |
| type | [BlendApplyType](arkts-arkui-blendapplytype-e.md) | 否 | blendMode实现方式是否离屏。默认值：BlendApplyType.FAST   **说明：** 1. 设置为 BlendApplyType.FAST，不离屏。 2. 设置为BlendApplyType.OFFSCREEN，会创建当前组件大小的离屏画布，再将当前组件（含子组件）的内容绘制到离屏画布上，再用指定的混合模式与下方 画布已有内容进行混合。 3. 不离屏情况下对文字类组件中emoji表情不生效。 4. 相比BlendApplyType.OFFSCREEN，设置为 BlendApplyType.OFFSCREEN_WITH_BACKGROUND，系统在创建与当前组件大小一致的离屏画布时，会先复制一份带有背景的画布作为初始化底色（BlendApplyType.OFFSCREEN类型的画 布初始为透明背景），随后在此基础上进行混合操作。两者在其他功能特性上保持一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## constructor

```TypeScript
constructor()
```

constructor.

**起始版本：** 9

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
@Builder
function myBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

// 使用WrappedBuilder封装myBuilder
let builderVar: WrappedBuilder<[string, number]> = new WrappedBuilder<[string, number]>(myBuilder);
```

## edgeLight

```TypeScript
edgeLight(params: EdgeLightParams | undefined): T
```

为组件添加边缘流光效果。边缘流光效果会在组件的边缘创建发光效果，从指定位置开始并沿边缘延伸，此效果可以增强组件的视觉吸引力并突出显示重要组件。

> **说明：**
> 
> - 仅设置edgeLight不会产生边缘流光效果，需结合
> animateTo更改position参数达到流光效果。可参考
> [示例4（设置组件边缘流光效果）](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect-sys.md#示例4设置组件边缘流光效果)。
> 
> 
> - 当position参数以对角线方式变更时，边缘流光将沿倾斜角45°的方式运行。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [EdgeLightParams](arkts-arkui-edgelightparams-i-sys.md) \| undefined | 是 | 定义边缘流光效果的位置、长度、强度、颜色和厚度。当params的值为undefined时，移除边缘流光效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## excludeFromRenderGroup

```TypeScript
excludeFromRenderGroup(exclude: boolean | undefined): T
```

设置当前组件和其子组件是否从祖先组件的节点组中剔除。需搭配祖先组件设置节点组[renderGroup](arkts-arkui-commonmethod-c.md#rendergroup)属性使 用，单独使用无效果。从节点组剔除后，当前组件和子组件不再影响祖先组件的离屏画布，不会引起节点组的缓存失效，从而达到复用节点组缓存的目的。如果当前组件的显示区域只占节点组绘制内容显示区域的一部分，且当前组件及子组件的显示效果频繁更新，设置 excludeFromRenderGroup属性有助于绘制性能优化。不设置该属性时，默认当前组件和其子组件不从祖先组件的节点组中剔除。

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

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exclude | boolean \| undefined | 是 | 设置当前组件及其子组件是否从祖先组件的节点组中剔除。true表示当前组件及其子组件从祖先组件的节点组中剔除，不属于祖先组件的节点组； false表示当前组件及其子组件归属于祖先组件的节点组。当exclude的值为undefined时，按false处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## spatialEffect

```TypeScript
spatialEffect(params: SpatialEffectParams | undefined): T
```

将空间效果应用于组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SpatialEffectParams](arkts-arkui-spatialeffectparams-i-sys.md) \| undefined | 是 | 空间效果参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## systemMaterial

```TypeScript
systemMaterial(material: SystemUiMaterial | undefined): T
```

Set system-styled materials for the component. The material effect behaves differently on devices with different level of computing powers. On devices with lower computing power, it affects attributes such as the backgroundColor, borderWidth, borderColor, shadow. On devices with higher computing power, it adds a filter effect at the system material layer, which can produce an effect similar to glass.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| material | [SystemUiMaterial](arkts-arkui-systemuimaterial-t-sys.md) \| undefined | 是 | 组件的系统材质对象。设置为undefined时恢复为无材质的效果，若同时设置了材质对象影响的通用属性，会恢复至对应通用属性设置的 值，冲突的属性由材质对象决定，参考 ImmersiveMaterial。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## useUnionEffect

```TypeScript
useUnionEffect(value: boolean | undefined): T
```

指定当前组件是否参与祖先组件UnionEffectContainer的融合效果

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | Whether the component participates in the fusion effect of the ancestor component **UnionEffectContainer**.The value **true** means that the component participates in the fusion effect of the ancestor component **UnionEffectContainer**, and **false** means the opposite. Default value: **false**. Undefined means to default value. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | return the component attribute. |

## useUnionEffect

```TypeScript
useUnionEffect(value: boolean | undefined, options?: GravityCenterOptions): T
```

指定当前组件是否参与祖先组件UnionEffectContainer的融合效果

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 组件是否参与融合效果祖先组件**UnionEffectContainer**.值为**true**表示组件参与在祖先组件**UnionEffectContainer**的融合效果中，而**false**表示相反。 值为**t rue**表示该组件参与祖先组件**UnionEffectContainer**的融合效果，**false**表示相反。 |
| options | [GravityCenterOptions](arkts-arkui-gravitycenteroptions-i-sys.md) | 否 | 引力中心参数。 需要配合UnionMode.GRAVITY_UNION使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回组件属性。 |
