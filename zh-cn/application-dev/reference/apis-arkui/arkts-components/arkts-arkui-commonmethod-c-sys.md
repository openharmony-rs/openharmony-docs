# CommonMethod

CommonMethod.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-unnamed-declare class CommonMethod<T>--><!--Device-unnamed-declare class CommonMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## advancedBlendMode

```TypeScript
advancedBlendMode(effect: BlendMode | Blender, type?: BlendApplyType): T
```

将当前组件的内容（包含子节点内容）与下方画布（可能为离屏画布）已有内容进行混合。不能与 [blendMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口同时使用。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本13开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-advancedBlendMode(effect: BlendMode | Blender, type?: BlendApplyType): T--><!--Device-CommonMethod-advancedBlendMode(effect: BlendMode | Blender, type?: BlendApplyType): T-End-->

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Blender | 是 | 入参类型为BlendMode时表示混合模式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：BlendMode.NONE \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_入参类型为Blender时表示混合器类型，用于描述混合效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_需要使用uiEffect模块中的方法创建Blender实例。例如：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。使用自定义object作为入参不会生效。 |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | blendMode实现方式是否离屏。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：BlendApplyType.FAST\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1. 设置为BlendApplyType.FAST，不离屏。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. 设置为BlendApplyType.OFFSCREEN，会创建当前组件大小的离屏画布，再将当前组件（含子组件）的内容绘制到离屏画布上，再用指定的混合模式与下方画布已有内容进行混合。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_3. 不离屏情况下对文字类组件中emoji表情不生效。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_4. 相比BlendApplyType.OFFSCREEN，设置为BlendApplyType.OFFSCREEN\_\_\_ESCAPED\_UNDERSCORE\_\_\_WITH\_\_\_ESCAPED\_UNDERSCORE\_\_\_BACKGROUND，系统在创建与当前组件大小一致的离屏画布时，会先复制一份带有背景的画布作为初始化底色（BlendApplyType.OFFSCREEN类型的画布初始为透明背景），随后在此基础上进行混合操作。两者在其他功能特性上保持一致。 |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-constructor()--><!--Device-CommonMethod-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLight

```TypeScript
edgeLight(params: EdgeLightParams | undefined): T
```

为组件添加边缘流光效果。边缘流光效果会在组件的边缘创建发光效果，从指定位置开始并沿边缘延伸，此效果可以增强组件的视觉吸引力并突出显示重要组件。 > **说明：** > > - 仅设置edgeLight不会产生边缘流光效果，需结合 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_更改position参数达到流光效果。可参考 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_。 > > > - 当position参数以对角线方式变更时，边缘流光将沿倾斜角45°的方式运行。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-edgeLight(params: EdgeLightParams | undefined): T--><!--Device-CommonMethod-edgeLight(params: EdgeLightParams | undefined): T-End-->

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 定义边缘流光效果的位置、长度、强度、颜色和厚度。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当params的值为undefined时，移除边缘流光效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## excludeFromRenderGroup

```TypeScript
excludeFromRenderGroup(exclude: boolean | undefined): T
```

设置当前组件和其子组件是否从祖先组件的节点组中剔除。需搭配祖先组件设置节点组[renderGroup]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_属性使 用，单独使用无效果。 从节点组剔除后，当前组件和子组件不再影响祖先组件的离屏画布，不会引起节点组的缓存失效，从而达到复用节点组缓存的目的。如果当前组件的显示区域只占节点组绘制内容显示区域的一部分，且当前组件及子组件的显示效果频繁更新，设置 excludeFromRenderGroup属性有助于绘制性能优化。 不设置该属性时，默认当前组件和其子组件不从祖先组件的节点组中剔除。 > **说明：** > > 设置excludeFromRenderGroup为true的组件及其子组件的绘制内容不能超过该组件本身的边界范围，否则会出现显示内容被裁剪的问题。例如当子组件通过 > [translate]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_或 > [scale]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_等属性导致子组件超出当前组件范围，或当前组件上有 > [shadow]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、 > [pixelStretchEffect]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_等属性导致当前组件的绘制内容超出组件 > 边界时，可能出现显示内容被裁剪的问题。此类场景不应设置excludeFromRenderGroup属性为true。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-excludeFromRenderGroup(exclude: boolean | undefined): T--><!--Device-CommonMethod-excludeFromRenderGroup(exclude: boolean | undefined): T-End-->

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exclude | boolean \| undefined | 是 | 设置当前组件及其子组件是否从祖先组件的节点组中剔除。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true表示当前组件及其子组件从祖先组件的节点组中剔除，不属于祖先组件的节点组；false表示当前组件及其子组件归属于祖先组件的节点组。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当exclude的值为undefined时，按false处理。 |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-spatialEffect(params: SpatialEffectParams | undefined): T--><!--Device-CommonMethod-spatialEffect(params: SpatialEffectParams | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 空间效果参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## useUnionEffect

```TypeScript
useUnionEffect(value: boolean | undefined): T
```

指定当前组件是否参与祖先组件UnionEffectContainer的融合效果

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-useUnionEffect(value: boolean | undefined): T--><!--Device-CommonMethod-useUnionEffect(value: boolean | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | Whether the component participates in the fusion effect of the ancestor component **UnionEffectContainer**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The value **true** means that the component participates in the fusion effect of the ancestor component **UnionEffectContainer**, and **false** means the opposite.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **false**. Undefined means to default value. |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-useUnionEffect(value: boolean | undefined, options?: GravityCenterOptions): T--><!--Device-CommonMethod-useUnionEffect(value: boolean | undefined, options?: GravityCenterOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 组件是否参与融合效果祖先组件**UnionEffectContainer**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_值为**true**表示组件参与在祖先组件**UnionEffectContainer**的融合效果中，而**false**表示相反。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_值为**t rue**表示该组件参与祖先组件**UnionEffectContainer**的融合效果，**false**表示相反。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 引力中心参数。 需要配合UnionMode.GRAVITY\_\_\_ESCAPED\_UNDERSCORE\_\_\_UNION使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回组件属性。 |

