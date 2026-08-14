# PointLightStyle（系统接口）

通过设置光源和被照亮的类型实现点光源照亮周围组件的UI效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface PointLightStyle--><!--Device-unnamed-export declare interface PointLightStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## bloom

```TypeScript
bloom?: double
```

设置组件的发光强度，取值范围为[0, 1]，超出取值范围时会转换为默认值。 默认值：0

**类型：** double

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PointLightStyle-bloom?: double--><!--Device-PointLightStyle-bloom?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## illuminated

```TypeScript
illuminated?: IlluminatedType
```

设置当前组件是否可以被光源照亮，以及被照亮的类型。 默认值：IlluminatedType.NONE

**类型：** [IlluminatedType](../../apis-arkui/arkts-apis/arkts-arkui-illuminatedtype-e-sys.md)

**默认值：** IlluminatedType.NONE

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PointLightStyle-illuminated?: IlluminatedType--><!--Device-PointLightStyle-illuminated?: IlluminatedType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## lightSource

```TypeScript
lightSource?: LightSource
```

设置光源属性，光源会影响到周围标记为可以被照亮的组件，并在组件上产生光效。 默认值：无光源

**类型：** [LightSource](arkts-na-common-lightsource-i-sys.md)

**默认值：** undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PointLightStyle-lightSource?: LightSource--><!--Device-PointLightStyle-lightSource?: LightSource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

