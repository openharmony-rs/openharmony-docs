# Hyperlink属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** HyperlinkAttribute extends [CommonMethod<HyperlinkAttribute>](CommonMethod<HyperlinkAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class HyperlinkAttribute extends CommonMethod<HyperlinkAttribute>--><!--Device-unnamed-declare class HyperlinkAttribute extends CommonMethod<HyperlinkAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="color"></a>
## color

```TypeScript
color(value: Color | number | string | Resource)
```

设置超链接文本的颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HyperlinkAttribute-color(value: Color | number | string | Resource): HyperlinkAttribute--><!--Device-HyperlinkAttribute-color(value: Color | number | string | Resource): HyperlinkAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Color](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md) \| number \| string \| Resource | 是 | 超链接文本的颜色。<br/><!--RP1-->默认值：'#ff007dff'，显示为蓝色。<!--RP1End--> |

