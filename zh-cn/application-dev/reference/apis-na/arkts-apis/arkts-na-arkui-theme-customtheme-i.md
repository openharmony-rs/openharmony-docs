# CustomTheme

自定义主题风格对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface CustomTheme--><!--Device-unnamed-export declare interface CustomTheme-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## colors

```TypeScript
colors?: CustomColors
```

自定义浅色主题颜色资源。&lt;/br&gt;

**类型：** [CustomColors](../../apis-arkui/arkts-apis/arkts-arkui-customcolors-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomTheme-colors?: CustomColors--><!--Device-CustomTheme-colors?: CustomColors-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## darkColors

```TypeScript
darkColors?: CustomDarkColors
```

自定义深色主题颜色资源。 **说明：**如果未设置darkColors，颜色值将与浅色模式下的colors配置相同，并且不会随着颜色模式的变化而变化，除非该颜色是通过dark目录下的资源进行设置的。&lt;/br&gt;

**类型：** [CustomDarkColors](../../apis-arkui/arkts-apis/arkts-arkui-customdarkcolors-t.md)

**默认值：** If not set darkColors, color value will same as colors under light mode and will not change with color mode, unless the color is setted by resource in dark directory.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomTheme-darkColors?: CustomDarkColors--><!--Device-CustomTheme-darkColors?: CustomDarkColors-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

