# ImmersiveStyle

沉浸式材质样式枚举。不同的材质样式对应不同的材质参数，主要包括材质的模糊程度、高光效果等。开发者可根据UI场景需要选择合适的材质样式：悬浮按钮和轻量提示建议使用`ULTRA_THIN`或`THIN`样式，常规内容区域和卡片建议使用`REGULAR`样式，需要强调层次感或遮挡背景的场景建议使用`THICK`或`ULTRA_THICK`样式。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ULTRA_THIN_EC

```TypeScript
ULTRA_THIN_EC = 5
```

超薄样式。材质层超薄，具有很强的透明效果。

适用于EffectComponent。配合对应的ULTRA_THICK_EC_SUB后缀样式枚举一起使用，以实现材质效果绘制的合并优化。设置在EffectComponent上的材质模糊最终将生效在子组件上。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## THIN_EC

```TypeScript
THIN_EC = 6
```

薄样式。材质层薄，具有较强的透明效果。

适用于EffectComponent。配合对应的THIN_EC_SUB后缀样式枚举一起使用，以实现材质效果绘制的合并优化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## REGULAR_EC

```TypeScript
REGULAR_EC = 7
```

常规样式。材质层厚度适中，具有适度的透明与模糊效果。

适用于EffectComponent。配合对应的REGULAR_EC_SUB后缀样式枚举一起使用，以实现材质效果绘制的合并优化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## THICK_EC

```TypeScript
THICK_EC = 8
```

厚样式。模糊效果强。

适用于EffectComponent。配合对应的THICK_EC_SUB后缀样式枚举一起使用，以实现材质效果绘制的合并优化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## ULTRA_THICK_EC

```TypeScript
ULTRA_THICK_EC = 9
```

超厚样式。模糊效果很强。

适用于EffectComponent。配合对应的ULTRA_THICK_EC_SUB后缀样式枚举一起使用，以实现材质效果绘制的合并优化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## ULTRA_THIN_EC_SUB

```TypeScript
ULTRA_THIN_EC_SUB = 10
```

超薄样式。材质层超薄，具有很强的透明效果。

适用于EffectComponent的子组件。配合对应的ULTRA_THIN_EC样式枚举一起使用，以实现材质效果绘制的合并优化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## THIN_EC_SUB

```TypeScript
THIN_EC_SUB = 11
```

薄样式。材质层薄，具有较强的透明效果。

适用于EffectComponent的子组件。配合对应的THIN_EC样式枚举一起使用，以实现材质效果绘制的合并优化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## REGULAR_EC_SUB

```TypeScript
REGULAR_EC_SUB = 12
```

常规样式。材质层厚度适中，具有适度的透明与模糊效果。

适用于EffectComponent的子组件。配合对应的REGULAR_EC样式枚举一起使用，以实现材质效果绘制的合并优化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## THICK_EC_SUB

```TypeScript
THICK_EC_SUB = 13
```

厚样式。模糊效果强。

适用于EffectComponent的子组件。配合对应的THICK_EC样式枚举一起使用，以实现材质效果绘制的合并优化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## ULTRA_THICK_EC_SUB

```TypeScript
ULTRA_THICK_EC_SUB = 14
```

超厚样式。模糊效果很强。

适用于EffectComponent的子组件。配合对应的ULTRA_THICK_EC样式枚举一起使用，以实现材质效果绘制的合并优化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
