# Button

按钮组件，可快速创建不同样式的按钮。

> **说明：**

## 子组件

可以包含单个子组件。

## Button

```TypeScript
Button()
```

创建一个空按钮。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonInterface-(): ButtonAttribute--><!--Device-ButtonInterface-(): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Button

```TypeScript
Button(options: ButtonOptions)
```

创建可以包含单个子组件的按钮。未通过该接口设置时，则按照ButtonOptions中各参数的默认值配置。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonInterface-(options: ButtonOptions): ButtonAttribute--><!--Device-ButtonInterface-(options: ButtonOptions): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ButtonOptions](arkts-arkui-buttonoptions-i.md) | 是 | 配置按钮的显示样式。  |

## Button

```TypeScript
Button(label: ResourceStr, options?: ButtonOptions)
```

使用文本内容创建相应的按钮组件，此时Button无法包含子组件。

文本内容默认单行显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonInterface-(label: ResourceStr, options?: ButtonOptions): ButtonAttribute--><!--Device-ButtonInterface-(label: ResourceStr, options?: ButtonOptions): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 按钮文本内容。<br/>**说明：** 当文本字符的长度超过按钮本身的宽度时，文本将会被截断。  |
| options | [ButtonOptions](arkts-arkui-buttonoptions-i.md) | 否 | 配置按钮的显示样式。 <br/> 未设置时，则按照ButtonOptions中各参数的默认值配置。  |

## 汇总

- [ButtonConfiguration](arkts-arkui-button-buttonconfiguration-i.md)
- [ButtonOptions](arkts-arkui-button-buttonoptions-i.md)
- [LabelStyle](arkts-arkui-button-labelstyle-i.md)
- [ButtonTriggerClickCallback](arkts-arkui-button-buttontriggerclickcallback-t.md)
- [ButtonRole](arkts-arkui-button-buttonrole-e.md)
- [ButtonStyleMode](arkts-arkui-button-buttonstylemode-e.md)
- [ButtonType](arkts-arkui-button-buttontype-e.md)
- [ControlSize](arkts-arkui-button-controlsize-e.md)
