# Button

Defines Button Component instance.


## Button

```TypeScript
Button()
```

创建一个空按钮。

**起始版本：** 7

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为7.

## Button

```TypeScript
Button(options: ButtonOptions)
```

创建可以包含单个子组件的按钮。未通过该接口设置时，则按照ButtonOptions中各参数的默认值配置。

**起始版本：** 7

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为7.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ButtonOptions | 是 |  |

## Button

```TypeScript
Button(label: ResourceStr, options?: ButtonOptions)
```

使用文本内容创建相应的按钮组件，此时Button无法包含子组件。

文本内容默认单行显示。

**起始版本：** 7

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为7.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | ResourceStr | 是 |  |
| options | ButtonOptions | 否 |  |

## 汇总

- [ButtonConfiguration](arkts-arkui-button-buttonconfiguration-i.md)
- [ButtonOptions](arkts-arkui-button-buttonoptions-i.md)
- [LabelStyle](arkts-arkui-button-labelstyle-i.md)
- [ButtonTriggerClickCallback](arkts-arkui-button-buttontriggerclickcallback-t.md)
- [ButtonRole](arkts-arkui-button-buttonrole-e.md)
- [ButtonStyleMode](arkts-arkui-button-buttonstylemode-e.md)
- [ButtonType](arkts-arkui-button-buttontype-e.md)
- [ControlSize](arkts-arkui-button-controlsize-e.md)
