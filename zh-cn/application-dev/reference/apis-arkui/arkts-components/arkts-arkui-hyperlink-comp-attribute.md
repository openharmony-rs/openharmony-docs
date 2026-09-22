# Hyperlink属性/事件

```TypeScript
declare class HyperlinkAttribute extends CommonMethod<HyperlinkAttribute>
```

除支持[通用属性](arkts-arkui-common-comp-commonmethod-c.md)外，还支持以下属性。

支持[通用事件](arkts-arkui-common-comp-commonmethod-c.md)。

**继承/实现关系：** HyperlinkAttribute extends CommonMethod<HyperlinkAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: Color | number | string | Resource)
```

设置超链接文本的颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | 是 | 超链接文本的颜色。<br>&lt;!--RP1--&gt;默认值：'#ff007dff'，显示为蓝色。&lt;!--RP1End--&gt; |
