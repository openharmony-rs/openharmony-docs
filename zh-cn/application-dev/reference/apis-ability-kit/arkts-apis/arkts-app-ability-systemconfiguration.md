# @ohos.app.ability.systemConfiguration(系统环境模块)

systemConfiguration模块提供系统环境变化监听回调能力，包括系统深浅色模式、系统语言、系统字体大小缩放比例等变化的回调。例如，通过对系统深浅色模式变化的监听，应用可感知系统的深浅色模式变化，并动态调整自身应用的深浅色主题以适配系统环境。该模块与[EnvironmentCallback](arkts-ability-app-ability-environmentcallback-environmentcallback-c.md)模块的区别在于：  
- systemConfiguration模块：用于监听系统环境变量[Configuration](arkts-ability-app-ability-configuration-configuration-i.md)的变化。  
- [EnvironmentCallback](arkts-ability-app-ability-environmentcallback-environmentcallback-c.md)模块：用于监听某个应用环境变量  
[Configuration](arkts-ability-app-ability-configuration-configuration-i.md)的变化。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { systemConfiguration } from '@kit.AbilityKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [UpdatedCallback(系统环境模块)](arkts-ability-systemconfiguration-updatedcallback-i.md) | UpdatedCallback是监听系统环境变化的回调函数，开发者可通过 [ApplicationContext.onSystemConfigurationUpdated](arkts-ability-applicationcontext-c.md#onsystemconfigurationupdated) 方法注册自定义的UpdatedCallback，来监听系统环境变化。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnColorModeUpdatedFn(系统环境模块)](arkts-ability-systemconfiguration-oncolormodeupdatedfn-t.md) | 在注册系统环境变化的监听后，当系统深浅色模式变化时会触发回调。 |
| [OnFontIdUpdatedFn(系统环境模块)](arkts-ability-systemconfiguration-onfontidupdatedfn-t.md) | 在注册系统环境变化的监听后，当系统字体ID变化时触发回调。 |
| [OnFontSizeScaleUpdatedFn(系统环境模块)](arkts-ability-systemconfiguration-onfontsizescaleupdatedfn-t.md) | 在注册系统环境变化的监听后，当系统字体大小缩放比例变化时触发回调。 |
| [OnFontWeightScaleUpdatedFn(系统环境模块)](arkts-ability-systemconfiguration-onfontweightscaleupdatedfn-t.md) | 在注册系统环境变化的监听后，当系统字体粗细缩放比例变化时触发回调。 |
| [OnHasPointerDeviceUpdatedFn(系统环境模块)](arkts-ability-systemconfiguration-onhaspointerdeviceupdatedfn-t.md) | 在注册系统环境变化的监听后，当指针设备连接或者断开时触发回调。 |
| [OnLanguageUpdatedFn(系统环境模块)](arkts-ability-systemconfiguration-onlanguageupdatedfn-t.md) | 在注册系统环境变化的监听后，当系统语言变化时触发回调。 |
| [OnLocaleUpdatedFn(系统环境模块)](arkts-ability-systemconfiguration-onlocaleupdatedfn-t.md) | 在注册系统环境变化的监听后，当系统区域设置变化时触发回调。 |
| [OnMCCUpdatedFn(系统环境模块)](arkts-ability-systemconfiguration-onmccupdatedfn-t.md) | 在注册系统环境变化的监听后，当移动设备国家代码变化时触发回调。 |
| [OnMNCUpdatedFn(系统环境模块)](arkts-ability-systemconfiguration-onmncupdatedfn-t.md) | 在注册系统环境变化的监听后，当移动设备网络代码变化时触发回调。 |
