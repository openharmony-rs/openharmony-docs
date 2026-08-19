# Radio

单选框，提供单选类型的用户交互选择项。 > **说明：** > > - API version 12开始，Radio选中默认样式由RadioIndicatorType.DOT变为RadioIndicatorType.TICK。 > - 该组件默认有margin间距，默认值为：{&nbsp;top: '14px',&nbsp;right: '14px',&nbsp;bottom: '14px',& > nbsp;left: '14px' }。

## 子组件 无

## Radio

```TypeScript
Radio(options: RadioOptions)
```

创建单选框组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RadioInterface-(options: RadioOptions): RadioAttribute--><!--Device-RadioInterface-(options: RadioOptions): RadioAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RadioOptions](arkts-arkui-radiooptions-i.md) | 是 | 配置单选框的参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RadioConfiguration](arkts-arkui-radioconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。 |
| [RadioOptions](arkts-arkui-radiooptions-i.md) | 单选框的信息。 |
| [RadioStyle](arkts-arkui-radiostyle-i.md) | 单选框的样式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnRadioChangeCallback](arkts-arkui-onradiochangecallback-t.md) | 单选框选中状态改变时触发的回调函数类型定义。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RadioIndicatorType](arkts-arkui-radioindicatortype-e.md) | 单选框的样式。 |

