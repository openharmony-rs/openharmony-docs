# Toggle

组件提供勾选框样式、状态按钮样式和开关样式。

> **说明：**

> - 从API版本26.0.0开始，Toggle组件支持新材质效果。Toggle组件使用通用新材质属性[systemMaterial]{@link CommonMethod#systemMaterial}时，不同
> [ToggleType]{@link ToggleType}类型的效果不同：    
> >   - ToggleType.Checkbox：当前未适配系统材质效果，设置系统材质不会出现系统材质相关的动效和视觉效果。
> >   - ToggleType.Switch：传入材质参数时，使用组件内部预设的视觉参数，传入的材质参数仅作为开启新材质的开关标记，不影响实际视觉效果。主要影响Toggle的滑块大小、滑块样式、阴影等视觉属性。设置
> [switchPointColor]{@link ToggleAttribute#switchPointColor}后会出现点光源效果，点光源颜色跟随switchPointColor的设置。传入undefined时，新材质不生效，
> 表现为原先的Toggle样式。
> >   - ToggleType.Button：设置系统材质的效果与[Button]{@link button}组件设置系统材质的效果相同，主要影响背景颜色、边框、阴影等视觉属性。

## 子组件

仅当ToggleType设置为Button时，可包含子组件。

## Toggle

```TypeScript
Toggle(options: ToggleOptions)
```

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ToggleInterface-(options: ToggleOptions): ToggleAttribute--><!--Device-ToggleInterface-(options: ToggleOptions): ToggleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ToggleOptions | 是 | Toggle组件的配置选项，用于配置开关的样式类型和初始状态。 |

## 汇总

- [SwitchStyle](arkts-arkui-toggle-switchstyle-i.md)
- [ToggleConfiguration](arkts-arkui-toggle-toggleconfiguration-i.md)
- [ToggleOptions](arkts-arkui-toggle-toggleoptions-i.md)
- [ToggleType](arkts-arkui-toggle-toggletype-e.md)
