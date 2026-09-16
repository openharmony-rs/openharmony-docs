# Toggle

组件提供勾选框样式、状态按钮样式和开关样式，适用于需要快速切换状态或进行单选确认的场景，能够有效提升交互体验与界面的直观性。

> **说明：**

> - 从API版本26.0.0开始，Toggle组件支持新材质效果。Toggle组件使用通用新材质属性systemMaterial时，不同 > [ToggleType](arkts-arkui-toggletype-e.md)类型的效果不同： > > - ToggleType.Checkbox：当前未适配系统材质效果，设置系统材质不会出现系统材质相关的动效和视觉效果。 > > - ToggleType.Switch：传入材质参数时，使用组件内部预设的视觉参数，传入的材质参数仅作为开启新材质的开关标记，不影响实际视觉效果。主要影响Toggle的滑块大小、滑块样式、阴影等视觉属性。设置 > [switchPointColor](arkts-arkui-toggle-comp-attribute.md#switchpointcolor)后会出现点光源效果，点光源颜色跟随switchPointColor的设置。传入undefined时，新材质不生效， > 表现为原先的Toggle样式。 > > - ToggleType.Button：设置系统材质的效果与Button组件设置系统材质的效果相同，主要影响背景颜色、边框、阴影等视觉属性。

## 子组件

仅当ToggleType设置为Button时，可包含子组件。

## Toggle

```TypeScript
Toggle(options: ToggleOptions)
```

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ToggleOptions](arkts-arkui-toggleoptions-i.md) | 是 | Toggle组件的配置选项，用于配置开关的样式类型和初始状态。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [SwitchStyle](arkts-arkui-switchstyle-i.md) | Switch类型的样式。 |
| [ToggleConfiguration](arkts-arkui-toggleconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [ToggleOptions](arkts-arkui-toggleoptions-i.md) | Toggle组件的配置信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ToggleType](arkts-arkui-toggletype-e.md) | Toggle的样式。 |

## 示例

```TypeScript
### 示例1（设置开关的样式）

该示例通过配置ToggleType设置Toggle的勾选框样式、状态按钮样式及开关样式。


```

```TypeScript
### 示例2（自定义开关类型的样式）

该示例实现了自定义设置Toggle组件Switch样式，包括圆形滑块半径、关闭状态的背景颜色、圆形滑块颜色、滑轨的圆角。


```

```TypeScript
### 示例3（自定义Toggle样式）

该示例实现自定义Toggle样式，通过按钮切换圆形背景颜色：点击蓝圆按钮，背景变蓝色；点击黄圆按钮，背景变黄色。


```

```TypeScript
### 示例4（Toggle沉浸光感效果）

该示例展示了Toggle组件Switch类型在开启沉浸光感前后的效果对比。示例使用通用属性[systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial)接口来实现沉浸光感效果。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，新增systemMaterial属性。

> 说明：
> 
> 系统材质的实际显示效果与设备的算力档位相关，相同的代码在不同算力档位的设备上显示效果存在差异，低算力设备上会显示简化后的材质效果。算力档位由系统根据设备硬件能力自动划分和管理，应用无需感知，也无需进行额外设置，系统会根据当前设备的算力档位自动适配材质的显示效果。
```
