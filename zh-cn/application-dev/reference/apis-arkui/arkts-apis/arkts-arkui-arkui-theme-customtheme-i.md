# CustomTheme

自定义主题风格对象。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Colors, CustomColors, Theme, ThemeControl, CustomTheme, CustomDarkColors } from '@kit.ArkUI';
```

## colors

```TypeScript
colors?: CustomColors
```

自定义浅色主题颜色资源。&lt;/br&gt;

**类型：** [CustomColors](arkts-arkui-customcolors-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## darkColors

```TypeScript
darkColors?: CustomDarkColors
```

自定义深色主题颜色资源。  
**说明：**如果未设置darkColors，则使用浅色模式下的colors配置，并且不会随着系统深浅色模式的切换而变化；如果对应颜色通过dark目录下的资源进行设置，则会优先使用dark目录下的资源。

**类型：** [CustomDarkColors](arkts-arkui-customdarkcolors-t.md)

**默认值：** If not set darkColors, color value will same as colors under light mode and will not change with color mode, unless the color is setted by resource in dark directory.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
