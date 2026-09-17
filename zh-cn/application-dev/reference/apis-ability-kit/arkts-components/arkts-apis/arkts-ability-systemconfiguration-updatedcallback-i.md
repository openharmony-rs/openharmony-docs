# UpdatedCallback

UpdatedCallback是监听系统环境变化的回调函数，开发者可通过[ApplicationContext.onSystemConfigurationUpdated](arkts-ability-applicationcontext-c.md#onsystemconfigurationupdated)方法注册自定义的UpdatedCallback，来监听系统环境变化。

**起始版本：** 24

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
import { systemConfiguration } from '@kit.AbilityKit';
```

## onColorModeUpdated

```TypeScript
onColorModeUpdated?: OnColorModeUpdatedFn
```

在注册系统环境变化的监听后，当系统深浅色模式变化时会触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onFontIdUpdated

```TypeScript
onFontIdUpdated?: OnFontIdUpdatedFn
```

在注册系统环境变化的监听后，当系统字体ID变化时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onFontSizeScaleUpdated

```TypeScript
onFontSizeScaleUpdated?: OnFontSizeScaleUpdatedFn
```

在注册系统环境变化的监听后，当系统字体大小缩放比例变化时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onFontWeightScaleUpdated

```TypeScript
onFontWeightScaleUpdated?: OnFontWeightScaleUpdatedFn
```

在注册系统环境变化的监听后，当系统字体粗细缩放比例变化时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onHasPointerDeviceUpdated

```TypeScript
onHasPointerDeviceUpdated?: OnHasPointerDeviceUpdatedFn
```

在注册系统环境变化的监听后，当指针设备连接或者断开时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onLanguageUpdated

```TypeScript
onLanguageUpdated?: OnLanguageUpdatedFn
```

在注册系统环境变化的监听后，当系统语言变化时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onLocaleUpdated

```TypeScript
onLocaleUpdated?: OnLocaleUpdatedFn
```

在注册系统环境变化的监听后，当系统区域设置变化时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onMCCUpdated

```TypeScript
onMCCUpdated?: OnMCCUpdatedFn
```

在注册系统环境变化的监听后，当移动设备国家代码变化时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onMNCUpdated

```TypeScript
onMNCUpdated?: OnMNCUpdatedFn
```

在注册系统环境变化的监听后，当移动设备网络代码变化时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
