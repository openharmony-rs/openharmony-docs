# StepperItem属性/事件

**继承/实现关系：** StepperItemAttribute extends [CommonMethod<StepperItemAttribute>](CommonMethod<StepperItemAttribute>)

**起始版本：** 8

**废弃版本：** 22

**替代接口：** SwiperAttribute

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nextLabel

```TypeScript
nextLabel(value: string)
```

设置右侧文本按钮内容，最后一页默认值为“开始”，其余页默认值为“下一步”。

> **说明：**

> 从API version 8开始支持，从API version 22开始废弃，建议使用[showNext](arkts-arkui-swipercontroller-c.md#shownext-1)替代。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** showNext

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 右侧文本按钮内容。字符串超长时，先缩小再换行（2行）最后截断。 |

## prevLabel

```TypeScript
prevLabel(value: string)
```

设置左侧文本按钮内容，第一页没有左侧文本按钮，当步骤导航器大于一页时，除第一页外默认值都为“返回”。

> **说明：**

> 从API version 8开始支持，从API version 22开始废弃，建议使用[showPrevious](arkts-arkui-swipercontroller-c.md#showprevious-1)替代。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** showPrevious

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 左侧文本按钮内容。字符串超长时，先缩小再换行（2行）最后截断。 |

## status

```TypeScript
status(value?: ItemState)
```

设置步骤导航器nextLabel的显示状态。

> **说明：**

> 从API version 8开始支持，从API version 22开始废弃，建议使用[indicatorInteractive](SwiperAttribute#indicatorInteractive)替代。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** indicatorInteractive

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ItemState | 否 | 步骤导航器nextLabel的显示状态。<br/>默认值：ItemState.Normal |

