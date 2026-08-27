# Toggle

组件提供勾选框样式、状态按钮样式和开关样式，适用于需要快速切换状态或进行单选确认的场景，能够有效提升交互体验与界面的直观性。
> **说明：**
> - 从API版本26.0.0开始，Toggle组件支持新材质效果。Toggle组件使用通用新材质属性systemMaterial时，不同 > [ToggleType](arkts-arkui-toggletype-e.md)类型的效果不同： > > - ToggleType.Checkbox：当前未适配系统材质效果，设置系统材质不会出现系统材质相关的动效和视觉效果。 > > - ToggleType.Switch：传入材质参数时，使用组件内部预设的视觉参数，传入的材质参数仅作为开启新材质的开关标记，不影响实际视觉效果。主要影响Toggle的滑块大小、滑块样式、阴影等视觉属性。设置 > [switchPointColor](arkts-arkui-toggle-attribute.md#switchpointcolor)后会出现点光源效果，点光源颜色跟随switchPointColor的设置。传入undefined时，新材质不生效， > 表现为原先的Toggle样式。 > > - ToggleType.Button：设置系统材质的效果与Button组件设置系统材质的效果相同，主要影响背景颜色、边框、阴影等视觉属性。

## 子组件

仅当ToggleType设置为Button时，可包含子组件。

## Toggle

```TypeScript
Toggle(options: ToggleOptions)
```

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

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

该示例通过配置ToggleType设置Toggle的勾选框样式、状态按钮样式及开关样式。

```TypeScript
// xxx.ets
@Entry
@Component
struct ToggleExample {
  build() {
    Column({ space: 10 }) {
      Text('type: Switch').fontSize(12).fontColor(0xcccccc).width('90%')
      Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
        Toggle({ type: ToggleType.Switch, isOn: false })
          .selectedColor('#007DFF')
          .switchPointColor('#FFFFFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })

        Toggle({ type: ToggleType.Switch, isOn: true })
          .selectedColor('#007DFF')
          .switchPointColor('#FFFFFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })
      }

      Text('type: Checkbox').fontSize(12).fontColor(0xcccccc).width('90%')
      Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
        Toggle({ type: ToggleType.Checkbox, isOn: false })
          .size({ width: 20, height: 20 })
          .selectedColor('#007DFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })

        Toggle({ type: ToggleType.Checkbox, isOn: true })
          .size({ width: 20, height: 20 })
          .selectedColor('#007DFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })
      }

      Text('type: Button').fontSize(12).fontColor(0xcccccc).width('90%')
      Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
        Toggle({ type: ToggleType.Button, isOn: false }) {
          Text('status button').fontColor('#182431').fontSize(12)
        }.width(106)
        .selectedColor('rgba(0,125,255,0.20)')
        .onChange((isOn: boolean) => {
          console.info('Component status:' + isOn);
        })

        Toggle({ type: ToggleType.Button, isOn: true }) {
          Text('status button').fontColor('#182431').fontSize(12)
        }.width(106)
        .selectedColor('rgba(0,125,255,0.20)')
        .onChange((isOn: boolean) => {
          console.info('Component status:' + isOn);
        })
      }
    }.width('100%').padding(24)
  }
}
```

该示例实现了自定义设置Toggle组件Switch样式，包括圆形滑块半径、关闭状态的背景颜色、圆形滑块颜色、滑轨的圆角。

```TypeScript
// xxx.ets
@Entry
@Component
struct ToggleExample {
  build() {
    Column({ space: 10 }) {
      Text('type: Switch').fontSize(12).fontColor(0xcccccc).width('90%')
      Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
        Toggle({ type: ToggleType.Switch, isOn: false })
          .selectedColor('#007DFF')
          .switchStyle({
            pointRadius: 15,
            trackBorderRadius: 10,
            pointColor: '#D2B48C',
            unselectedColor: Color.Pink })
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })

        Toggle({ type: ToggleType.Switch, isOn: true })
          .selectedColor('#007DFF')
          .switchStyle({
            pointRadius: 15,
            trackBorderRadius: 10,
            pointColor: '#D2B48C',
            unselectedColor: Color.Pink })
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })
      }
    }.width('100%').padding(24)
  }
}
```

该示例实现自定义Toggle样式，通过按钮切换圆形背景颜色：点击蓝圆按钮，背景变蓝色；点击黄圆按钮，背景变黄色。

```TypeScript
// xxx.ets
// 自定义Switch样式修改器，实现ContentModifier接口定制Toggle内容区
class MySwitchStyle implements ContentModifier<ToggleConfiguration> {
  // 开关打开时的背景颜色
  selectedColor: Color = Color.White;
  // 用于按钮显示的文本
  lamp: string = 'string';

  constructor(selectedColor: Color, lamp: string) {
    this.selectedColor = selectedColor;
    this.lamp = lamp;
  }

  applyContent(): WrappedBuilder<[ToggleConfiguration]> {
    return wrapBuilder(buildSwitch);
  }
}

@Builder
function buildSwitch(config: ToggleConfiguration) {
  Column({ space: 50 }) {
    Circle({ width: 150, height: 150 })
      .fill(config.isOn ? (config.contentModifier as MySwitchStyle).selectedColor : Color.Blue)
    Row() {
      Button('蓝' + JSON.stringify((config.contentModifier as MySwitchStyle).lamp))
        .onClick(() => {
          config.triggerChange(false);
        })
      Button('黄' + JSON.stringify((config.contentModifier as MySwitchStyle).lamp))
        .onClick(() => {
          config.triggerChange(true);
        })
    }
  }
}

@Entry
@Component
struct Index {
  build() {
    Column({ space: 50 }) {
      // 使用自定义样式修改器定制Toggle内容，并通过onChange监听状态变化
      Toggle({ type: ToggleType.Switch })
        .enabled(true)
        .contentModifier(new MySwitchStyle(Color.Yellow, '灯'))
        .onChange((isOn: boolean) => {
          console.info('Switch Log:' + isOn);
        })
    }.height('100%').width('100%')
  }
}
```

从API版本26.0.0开始，新增systemMaterial属性。

```TypeScript
import { uiMaterial } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct ToggleMaterialTest {
  build() {
    Column({ space: 10 }) {
      // 不设置系统材质接口，无系统材质效果
      Toggle({ type: ToggleType.Switch, isOn: true })
        .size({ width: 80, height: 40 })

      // systemMaterial设置undefined，恢复为无材质的效果
      Toggle({ type: ToggleType.Switch, isOn: true })
        .size({ width: 80, height: 40 })
        .systemMaterial(undefined)

      // 开启系统材质效果（systemMaterial参数任意仅作为系统材质开关，最终使用组件侧固定参数），无点光源效果
      Toggle({ type: ToggleType.Switch, isOn: true })
        .size({ width: 80, height: 40 })
        .systemMaterial(new uiMaterial.Material())

      // 开启系统材质效果（systemMaterial参数任意仅作为系统材质开关，最终使用组件侧固定参数），有点光源效果
      Toggle({ type: ToggleType.Switch, isOn: true })
        .size({ width: 80, height: 40 })
        .systemMaterial(new uiMaterial.Material())
        .switchPointColor(Color.White)
    }
    .width('100%')
  }
}
```
