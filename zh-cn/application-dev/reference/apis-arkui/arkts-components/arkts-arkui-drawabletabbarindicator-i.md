# DrawableTabBarIndicator

使用图片资源作为下划线的对象。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

<!--Device-unnamed-declare interface DrawableTabBarIndicator--><!--Device-unnamed-declare interface DrawableTabBarIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Length
```

下划线的圆角半径（不支持百分比设置）。 默认值：0.0 单位：vp 取值范围：[0, +∞)。异常值时取默认值。

**类型：** Length

**默认值：** 0

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableTabBarIndicator-borderRadius?: Length--><!--Device-DrawableTabBarIndicator-borderRadius?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## drawable

```TypeScript
drawable?: DrawableDescriptor
```

下划线的图源。 支持[DrawableDescriptor]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、 [PixelMapDrawableDescriptor]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [LayeredDrawableDescriptor]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_和 [AnimatedDrawableDescriptor]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_类型。当传入无效图源时将显示默认的实线型下划 线。

**类型：** DrawableDescriptor

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableTabBarIndicator-drawable?: DrawableDescriptor--><!--Device-DrawableTabBarIndicator-drawable?: DrawableDescriptor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

下划线的高度（不支持百分比设置）。 默认值：2.0 单位：vp 取值范围：[0, +∞)。异常值时取默认值。

**类型：** Length

**默认值：** 2vp

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableTabBarIndicator-height?: Length--><!--Device-DrawableTabBarIndicator-height?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
marginTop?: Length
```

下划线与文字的间距（不支持百分比设置）。 默认值：8.0 单位：vp 取值范围：[0, +∞)。异常值时取默认值。

**类型：** Length

**默认值：** 8vp

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableTabBarIndicator-marginTop?: Length--><!--Device-DrawableTabBarIndicator-marginTop?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

下划线的宽度（不支持百分比设置）。 默认值：0.0 单位：vp 取值范围：[0, +∞)。异常值时取默认值。 宽度设置为0时，按页签文本宽度显示。

**类型：** Length

**默认值：** 0

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableTabBarIndicator-width?: Length--><!--Device-DrawableTabBarIndicator-width?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

