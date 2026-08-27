# Hyperlink属性/事件

除支持[通用属性](arkts-arkui-commonmethod-c.md)外，还支持以下属性。支持[通用事件](arkts-arkui-commonmethod-c.md)。

**继承/实现关系：** HyperlinkAttribute extends CommonMethod<HyperlinkAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## color

```TypeScript
color(value: Color | number | string | Resource)
```

设置超链接文本的颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Color \| number \| string \| Resource | 是 | 超链接文本的颜色。<!--RP1-->默认值：'#ff007dff'，显示为蓝色。<!--RP1End--> |
