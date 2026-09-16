# Blank属性/事件

支持[通用属性](arkts-arkui-commonmethod-c.md)。

支持[通用事件](arkts-arkui-commonmethod-c.md)。

**继承/实现关系：** BlankAttribute extends CommonMethod<BlankAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor)
```

设置空白填充的填充颜色，支持attributeModifier动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 空白填充的填充颜色。<br>默认值：Color.Transparent <br>非法值：按默认值处理。 |
