# TextTimer

TextTimer是通过文本显示计时信息并控制其计时器状态的组件，支持正向计时与倒计时两种模式，可自定义显示格式，适用于秒表、活动倒计时等需要展示时间流逝的场景。常用于倒计时场景，如考试倒计时、限时活动、运动计时等。

组件不可见（非锁屏状态和应用后台状态）时，UI时间变动将停止（即该组件此时不会绘制），[onTimer](arkts-arkui-texttimer-comp-attribute.md#ontimer)仍然会正常触发。

## 子组件

无

## TextTimer

```TypeScript
TextTimer(options?: TextTimerOptions)
```

创建文本计时器组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextTimerOptions](arkts-arkui-texttimeroptions-i.md) | 否 | 通过文本显示计时信息并控制其计时器状态的组件参数。当需要自定义计时器配置（如设置倒计时开关、计时时间、初始时间、控制器等）时传入此参数；不传入时使用TextTimerOptions的默认配置。<br>默认值继承[TextTimerOptions](arkts-arkui-texttimeroptions-i.md) 。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextTimerConfiguration](arkts-arkui-texttimerconfiguration-i.md) | ContentModifier接口使用的TextTimer配置。 |
| [TextTimerOptions](arkts-arkui-texttimeroptions-i.md) | 用于构建TextTimer组件的选项。 |

## 示例

```TypeScript
### 示例1（支持手动启停的文本计时器）

该示例展示了TextTimer组件的基本使用方法，通过[format](#format)属性设置计时器的文本显示格式。

用户可以通过点击"start"、"pause"、"reset"按钮，开启、暂停、重置计时器。


```

```TypeScript
### 示例2（设定文本阴影样式）

该示例通过[textShadow](#textshadow11)属性设置计时器的文本阴影样式。


```

```TypeScript
### 示例3（设定自定义内容区）

该示例实现了两个简易秒表，使用浅灰色背景。计时器开始后，会实时显示时间变化。倒计时器开始后，背景会变成黑色，正计时器开始后，背景会变成灰色。


```

```TypeScript
### 示例4（创建之后立即执行计时）

该示例展示了TextTimer计时器如何在创建完成之后立即开始计时。


```

```TypeScript
### 示例5（设置文本样式）

该示例通过[fontColor](#fontcolor)、[fontSize](#fontsize)、[fontStyle](#fontstyle)、[fontWeight](#fontweight)、[fontFamily](#fontfamily)属性展示了不同样式的文本效果。


```

```TypeScript
### 示例6（设置初始计时时间）

该示例通过[TextTimerOptions](#texttimeroptions对象说明)的startTime属性设置计时器初始计时时间。

从API版本26.0.0开始，[TextTimerOptions](#texttimeroptions对象说明)新增了startTime属性。
```
