# 融合效果（系统接口）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

本模块介绍如何设置使用融合效果。

> **说明：**
>
> - 从API version 23开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本模块为系统接口。

## useUnionEffect

useUnionEffect(value: boolean | undefined): T;

表示是否使用祖先组件[UnionEffectContainer](ts-container-unioneffectcomponent-sys.md)的融合效果，是否作为UnionEffectContainer做形状融合的一部分。

不设置该属性时，默认不使用祖先组件UnionEffectContainer的融合效果。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | boolean \| undefined | 是 | 表示是否使用祖先组件UnionEffectContainer的融合效果。<br/>useUnionEffect为true时，当前组件使用祖先组件UnionEffectContainer的融合效果，在祖先组件UnionEffectContainer计算形状时会作为UnionEffectContainer的一部分。<br/>useUnionEffect为false时，当前组件不使用祖先组件UnionEffectContainer的融合效果。<br/>设置为undefined时恢复为不使用祖先组件UnionEffectContainer的融合效果。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## useUnionEffect<sup>26+</sup>

useUnionEffect(value: boolean | undefined, options?: GravityCenterOptions): T;

表示是否使用祖先组件[UnionEffectContainer](ts-container-unioneffectcomponent-sys.md)的融合效果，是否作为UnionEffectContainer做形状融合的一部分。

不设置该属性时，默认不使用祖先组件UnionEffectContainer的融合效果。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | boolean \| undefined | 是 | 表示是否使用祖先组件UnionEffectContainer的融合效果。<br/>useUnionEffect为true时，当前组件使用祖先组件UnionEffectContainer的融合效果，在祖先组件UnionEffectContainer计算形状时会作为UnionEffectContainer的一部分。<br/>useUnionEffect为false时，当前组件不使用祖先组件UnionEffectContainer的融合效果。<br/>设置为undefined时恢复为不使用祖先组件UnionEffectContainer的融合效果。|
| options | [GravityCenterOptions](#gravitycenteroptions26对象说明) | 否 | 引力中心参数。<br/>**说明：**<br/>此参数必须与[unionMode](./ts-container-unioneffectcomponent-sys.md#unionmode26)并选择类型为[UnionMode.GRAVITY_UNION](./ts-container-unioneffectcomponent-sys.md#unionmode26枚举说明)一起使用，单独设置不生效。      |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## GravityCenterOptions<sup>26+</sup>对象说明

定义引力中心参数。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

| 名称               | 类型                              | 只读 | 可选 | 说明                                                    |
| ------------------ | -------------------------------- | ---- | ---- |------------------------------------------------------- |
| gravityCenter      | boolean                          | 否   | 是   | 指定当前组件是否为引力中心。<br/>默认值：false                                           |
| gravityIntensity   | number                           | 否   | 是   | 定义引力中心处吸引/排斥力的引力强度。<br/>默认值：0<br/>**说明：**<br/>负数表示排斥，正数表示吸引。 |

**示例：**

示例请参考[UnionEffectContainer示例](ts-container-unioneffectcomponent-sys.md#示例)。