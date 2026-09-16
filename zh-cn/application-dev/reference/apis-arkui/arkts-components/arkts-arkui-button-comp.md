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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Button

```TypeScript
Button(options: ButtonOptions)
```

创建可以包含单个子组件的按钮。未通过该接口设置时，则按照ButtonOptions中各参数的默认值配置。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ButtonOptions](arkts-arkui-buttonoptions-i.md) | 是 | 配置按钮的显示样式。 |

## Button

```TypeScript
Button(label: ResourceStr, options?: ButtonOptions)
```

使用文本内容创建相应的按钮组件，此时Button无法包含子组件。

文本内容默认单行显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 按钮文本内容。<br>**说明：** 当文本字符的长度超过按钮本身的宽度时，文本将会被截断。 |
| options | [ButtonOptions](arkts-arkui-buttonoptions-i.md) | 否 | 配置按钮的显示样式。<br> 未设置时，则按照ButtonOptions中各参数的默认值配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ButtonConfiguration](arkts-arkui-buttonconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [ButtonOptions](arkts-arkui-buttonoptions-i.md) | 按钮的样式。 |
| [LabelStyle](arkts-arkui-labelstyle-i.md) | Button组件的label文本及其字体样式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ButtonTriggerClickCallback](arkts-arkui-buttontriggerclickcallback-t.md) | 定义ButtonConfiguration中使用的回调类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ButtonRole](arkts-arkui-buttonrole-e.md) | 按钮的角色。 |
| [ButtonStyleMode](arkts-arkui-buttonstylemode-e.md) | 按钮的重要程度。 |
| [ButtonType](arkts-arkui-buttontype-e.md) | 按钮的类型。 |
| [ControlSize](arkts-arkui-controlsize-e.md) | 按钮的尺寸。 |

## 示例

```TypeScript
### 示例1（设置按钮的显示样式）

该示例展示两种创建按钮的方式：包含子组件或使用文本内容。


```

```TypeScript
### 示例2 （为按钮添加渲染控制）

该示例通过if/else控制按钮的显示文本。


```

```TypeScript
### 示例3 （设置按钮文本样式）

该示例通过配置labelStyle自定义按钮文本的显示样式。


```

```TypeScript
### 示例4（设置不同尺寸按钮的重要程度）

该示例通过配置controlSize、buttonStyle展示不同尺寸和样式的按钮。


```

```TypeScript
### 示例5（设置按钮的角色）

该示例通过配置role设置按钮的角色。


```

```TypeScript
### 示例6（设置自定义样式按钮）

该示例通过自定义样式用一个圆圈替换原本的按钮样式。如果按压，圆圈将变成红色，标题会显示按压字样；如果没有按压，圆圈将变成黑色，标题会显示非按压字样。


```

```TypeScript
### 示例7（设置圆角矩形按钮）

该示例展示圆角矩形按钮的创建、圆角大小设置及长文本截断效果。


```

```TypeScript
### 示例8（设置label文本水平对齐方式）

该示例通过配置[LabelStyle](#labelstyle10对象说明)的textAlign，设置文本对齐方式。

从API version 23开始，新增textAlign接口。


```

```TypeScript
### 示例9（设置按钮的沉浸光感效果）

该示例使用通用属性[systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial)接口来设置组件的系统材质，以实现沉浸光感效果。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

> 说明：
> 
> 如果开发者没有主动设置Button的背景色属性，即使用Button组件默认的背景色参数时，设置系统材质后会自动继承默认的背景色参数。如果开发者主动设置了背景色，且背景色参数设置在系统材质参数之前，则系统材质参数会强制清除开发者主动设置的背景色，将其改为透明色。 如果主动设置的背景色在系统材质之后，则背景色和系统材质会叠加显示（背景色层级更高）。

从API版本26.0.0开始，新增systemMaterial属性。
```
