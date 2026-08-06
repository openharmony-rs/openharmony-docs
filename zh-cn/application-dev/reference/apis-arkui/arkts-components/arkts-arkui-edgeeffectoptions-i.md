# EdgeEffectOptions

\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_属性参数对象。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface EdgeEffectOptions--><!--Device-unnamed-declare interface EdgeEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alwaysEnabled

```TypeScript
alwaysEnabled: boolean
```

组件内容大小小于组件自身时，设置是否开启滑动效果。设置为true开启滑动效果，设置为false关闭滑动效果。[List]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、[Grid]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_和 [WaterFlow]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_组件默认值是false，[Scroll]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_组件默认值是true。

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EdgeEffectOptions-alwaysEnabled: boolean--><!--Device-EdgeEffectOptions-alwaysEnabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## effectEdge

```TypeScript
effectEdge?: number
```

设置边缘效果生效的边缘。 如果设置[EffectEdge]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_.START表示只有起始边生效。如果设置[EffectEdge]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_.END表示只有末尾边生效。 默认值为[EffectEdge]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_.START | [EffectEdge]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_.END表示双边同时生效。当设置为其它异常值时，则默认双边同时生效。 如果需要双边都不生效，可将edgeEffect设置为EdgeEffect.None。

**类型：** number

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-EdgeEffectOptions-effectEdge?: number--><!--Device-EdgeEffectOptions-effectEdge?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

