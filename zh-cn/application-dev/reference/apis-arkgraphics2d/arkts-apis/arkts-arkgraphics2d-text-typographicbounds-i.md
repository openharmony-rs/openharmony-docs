# TypographicBounds

文本行的排版边界。文本行排版边界与排版字体、排版字号有关，与字符本身无关，例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，排版边界就包括行首和末尾空格的边界。例如字符串为"j"或"E"，排版边界相同 ，即与字符本身无关。 > **说明：** > > 示意图展示文本行排版参数：width（包含左右空格的文本行宽度）、ascent（上升高度最高点）、descent（下降高度最低点）、leading（行间距）、top（当前行最高点）、baseline（字符基线）、bottom（ > 当前行最低点）、next line top（下一行最高点）。 > > !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > > 示意图展示了字符串为" a b "的排版边界。 > > ! > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ > > 示意图展示了字符串为"j"或"E"的排版边界。 > > ! > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-text-interface TypographicBounds--><!--Device-text-interface TypographicBounds-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## ascent

```TypeScript
ascent: double
```

文本行的上升高度，浮点数，单位为物理像素px。

**类型：** double

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypographicBounds-ascent: double--><!--Device-TypographicBounds-ascent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## descent

```TypeScript
descent: double
```

文本行的下降高度，浮点数，单位为物理像素px。

**类型：** double

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypographicBounds-descent: double--><!--Device-TypographicBounds-descent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## leading

```TypeScript
leading: double
```

文本行的行间距，浮点数，单位为物理像素px。

**类型：** double

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypographicBounds-leading: double--><!--Device-TypographicBounds-leading: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## width

```TypeScript
width: double
```

排版边界的总宽度，浮点数，单位为物理像素px。

**类型：** double

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypographicBounds-width: double--><!--Device-TypographicBounds-width: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

