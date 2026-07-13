# WithThemeOptions

设置WithTheme作用域内组件缺省样式及深浅色模式。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: ThemeColorMode
```

用于指定WithTheme作用域内组件配色深浅色模式。

默认值：ThemeColorMode.SYSTEM

**类型：** ThemeColorMode

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## theme

```TypeScript
theme?: CustomTheme
```

用于自定义WithTheme作用域内组件缺省配色。

默认值：undefined，缺省样式跟随系统[token默认样式](../../../../ui/theme_skinning.md#系统缺省token色值)。

**类型：** CustomTheme

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

