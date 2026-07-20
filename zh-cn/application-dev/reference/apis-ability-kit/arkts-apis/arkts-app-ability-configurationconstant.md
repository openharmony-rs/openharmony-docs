# @ohos.app.ability.ConfigurationConstant

ConfigurationConstant模块提供了[Configuration](arkts-ability-app-ability-configuration-configuration-i.md)操作相关的系统预置枚举。

**起始版本：** 9

<!--Device-unnamed-declare namespace ConfigurationConstant--><!--Device-unnamed-declare namespace ConfigurationConstant-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## 导入模块

```TypeScript
import { ConfigurationConstant } from '@kit.AbilityKit';
```

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ColorMode](arkts-ability-configurationconstant-colormode-e.md) | 表示深浅色模式的枚举，用于[Configuration.colorMode](arkts-ability-app-ability-configuration-configuration-i.md)字段。开发者可以使用这些预置枚举设置或获取系统/应用的深浅色模式。 |
| [Direction](arkts-ability-configurationconstant-direction-e.md) | 表示屏幕方向的枚举，用于[Configuration.direction](arkts-ability-app-ability-configuration-configuration-i.md)字段。开发者可以使用这些预置枚举设置或获取系统/应用的显示方向。 |
| [ScreenDensity](arkts-ability-configurationconstant-screendensity-e.md) | 表示屏幕像素密度的枚举，用于[Configuration.screenDensity](arkts-ability-app-ability-configuration-configuration-i.md)字段。开发者可以使用这些预置枚举设置或获取屏幕的像素密度。  字体显示大小与屏幕像素密度呈正相关关系。通过监听屏幕像素密度变化，可以感知字体显示大小的调整。通常情况下，对于相同的物理尺寸，屏幕像素密度越高，字体显示效果越大。 |

