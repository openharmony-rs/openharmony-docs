# Checkbox

提供多选框组件，用于在多个选项中进行选择。 > **说明：** > > API version 11开始，Checkbox默认样式由圆角方形变为圆形。

## 子组件 无

## Checkbox

```TypeScript
Checkbox(options?: CheckboxOptions)
```

提供多选框组件，用于在多个选项中进行选择。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxInterface-(options?: CheckboxOptions): CheckboxAttribute--><!--Device-CheckboxInterface-(options?: CheckboxOptions): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CheckboxOptions](arkts-arkui-checkboxoptions-i.md) | 否 | 配置多选框的参数。不传入该参数时，多选框使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CheckBoxConfiguration](arkts-arkui-checkboxconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。 |
| [CheckboxOptions](arkts-arkui-checkboxoptions-i.md) | 多选框的信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnCheckboxChangeCallback](arkts-arkui-oncheckboxchangecallback-t.md) | 选中的状态。 |

