# @ohos.arkui.advanced.ChipGroupV2

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ChipGroupV2Item](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2item-c.md) | ChipGroupV2Item定义了ChipGroupV2组件中的单个操作块项。 |
| [ChipGroupV2Items](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2items-c.md) | ChipGroupV2Items定义了ChipGroupV2项的数组类，继承自Array&lt;[ChipGroupV2Item](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2item-c.md)&gt;。 |
| [ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md) | ChipGroupV2ItemStyleConfig定义了ChipV2的共通属性配置。 |
| [ChipGroupV2Padding](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2padding-c.md) | ChipGroupV2Padding定义了ChipGroupV2的上下内边距，用于控制其整体高度。 |
| [ChipGroupV2Space](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2space-c.md) | ChipGroupV2Space定义了ChipGroupV2左右内边距，以及ChipV2与ChipV2之间的间距。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md) | ChipGroupV2组件提供操作块群组容器，支持单选或多选、自定义样式和间距、以及尾部自定义内容。该组件适用于文件或资源内容的分类、标签选择、筛选等场景，可帮助开发者快速构建美观且交互丰富的标签组界面。 |
| [ChipGroupV2IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2icongroupsuffix-s.md) | ChipGroupV2组件提供操作块群组容器，支持单选或多选、自定义样式和间距、以及尾部自定义内容。该组件适用于文件或资源内容的分类、标签选择、筛选等场景，可帮助开发者快速构建美观且交互丰富的标签组界面。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChipGroupV2IconItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2iconitemconfig-i.md) | ChipGroupV2IconItemConfig定义了尾部图标项的配置，用于设置尾部图标的样式、交互和无障碍属性。 |
| [ChipGroupV2ItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemconfig-i.md) | ChipGroupV2ItemConfig定义每个ChipV2的非通用属性配置。 |
| [ChipGroupV2ItemStyleConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyleconfig-i.md) | ChipGroupV2ItemStyleConfig定义了ChipV2的共通属性配置。 |
| [ChipGroupV2PaddingConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2paddingconfig-i.md) | ChipGroupV2PaddingConfig定义了ChipGroupV2的上下内边距配置，用于控制其整体高度。 |
| [ChipGroupV2SpaceConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2spaceconfig-i.md) | ChipGroupV2SpaceConfig定义了ChipGroupV2左右内边距，以及ChipV2与ChipV2之间的间距配置。 |
| [ChipGroupV2SymbolItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2symbolitemconfig-i.md) | ChipGroupV2SymbolItemConfig定义了尾部Symbol图标的配置类型。 |

## 示例

### 示例1（ChipGroupV2无最右侧自定义组件）

该示例通过不设置suffix参数，实现了[ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md)没有最右侧自定义组件时的效果。



```TypeScript
import { ChipV2Size, ChipGroupV2, ChipGroupV2Items, ChipGroupV2ItemStyle, ChipGroupV2Space, ChipGroupV2Padding, ColorMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local selectedIndex: Array<number> = [0];

  build() {
    Column() {
      ChipGroupV2({
        // items内每个对象设置的都是每个ChipV2的特定属性。
        items: new ChipGroupV2Items([
          {
            // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: '操作块1' },
            suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') },
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: '操作块2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true
          },
        ]),
        // 设置ChipV2的style属性。
        itemStyle: new ChipGroupV2ItemStyle({
          size: ChipV2Size.SMALL,
          backgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_button_normal')),
          fontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary')),
          selectedBackgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_emphasize')),
          selectedFontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary_contrary')),
        }),
        selectedIndexes: this.selectedIndex,
        multiple: false,
        chipGroupSpace: new ChipGroupV2Space({ itemSpace: 8, endSpace: 0 }),
        chipGroupPadding: new ChipGroupV2Padding({ top: 10, bottom: 10 }),
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
      })
    }
  }
}
```

### 示例2（ChipGroupV2设置最右侧自定义组件）

该示例通过设置suffix参数，实现了[ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md)最右侧的自定义组件效果。

从API版本26.0.0开始，ChipGroupV2新增suffix属性。



```TypeScript
import { ChipV2Size, ChipGroupV2, ChipGroupV2Items, ChipGroupV2IconGroupSuffix, ChipGroupV2ItemStyle, ChipGroupV2Space, ChipGroupV2Padding, ColorMetrics, LengthMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local selectedIndex: Array<number> = [0, 1, 2, 3, 4, 5];
  @Local selectedState: boolean = true;

  @Builder
  ChipGroupSuffix(): void {
    // 开发者通过引用ChipGroupV2IconGroupSuffix，实现组件最右侧的自定义组件效果。
    ChipGroupV2IconGroupSuffix({
      items: [{
        icon: { src: $r('sys.media.ohos_ic_public_search_filled'), size: { width: LengthMetrics.fp(36), height: LengthMetrics.fp(36) } },
        action: () => {
          if (this.selectedState === false) {
            this.selectedIndex = [0, 1, 2, 3, 4, 5];
            this.selectedState = true;
          } else {
            this.selectedIndex = [];
            this.selectedState = false;
          }
        }
      }
      ]
    })
  }

  build() {
    Column() {
      ChipGroupV2({
        // items内每个对象设置的都是每个ChipV2的特定属性。
        items: new ChipGroupV2Items([
          {
            // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: '操作块1' },
            suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') },
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: '操作块2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true
          },
        ]),
        // 设置ChipV2的style属性。
        itemStyle: new ChipGroupV2ItemStyle({
          size: ChipV2Size.NORMAL,
          backgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_button_normal')),
          fontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary')),
          selectedBackgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_emphasize')),
          selectedFontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary_contrary')),
        }),
        selectedIndexes: this.selectedIndex,
        multiple: true,
        chipGroupSpace: new ChipGroupV2Space({ itemSpace: 8, endSpace: 0 }),
        chipGroupPadding: new ChipGroupV2Padding({ top: 10, bottom: 10 }),
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
        // ChipGroupV2最右侧显示的自定义组件。
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

### 示例3（设置Symbol类型图标）

该示例通过[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier)实现了[ChipGroupV2IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2icongroupsuffix-s.md)和[ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md)设置Symbol类型图标。

从API版本26.0.0开始，新增ChipGroupV2IconGroupSuffix和ChipGroupV2。



```TypeScript
import { ChipV2Size, ChipGroupV2, ChipGroupV2Items, ChipGroupV2IconGroupSuffix, SymbolGlyphModifier, ChipGroupV2ItemStyle, ChipGroupV2Space, ChipGroupV2Padding, ColorMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local selectedIndex: Array<number> = [0, 1, 2, 3, 4, 5];
  @Local selectedState: boolean = true;
  @Local prefixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_star'));
  @Local prefixModifierActivated: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]);
  @Local suffixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_wifi'));
  @Local suffixModifierActivated: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')).fontColor([Color.Red]);

  @Builder
  ChipGroupSuffix(): void {
    // 开发者通过引用ChipGroupV2IconGroupSuffix，实现组件最右侧的自定义组件效果。
    ChipGroupV2IconGroupSuffix({
      items: [
        new SymbolGlyphModifier($r('sys.symbol.magnifyingglass'))
          .onClick(() => {
            if (this.selectedState === false) {
              this.selectedIndex = [0, 1, 2, 3, 4, 5];
              this.selectedState = true;
            } else {
              this.selectedIndex = [];
              this.selectedState = false;
            }
          })
      ]
    })
  }

  build() {
    Column() {
      ChipGroupV2({
        // items内每个对象设置的都是每个ChipV2的特定属性。
        items: new ChipGroupV2Items([
          {
            prefixSymbolIcon: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
            label: { text: '操作块1' },
            suffixSymbolIcon: { normal: this.suffixModifierNormal, activated: this.suffixModifierActivated },
            allowClose: false,
          },
          {
            prefixSymbolIcon: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
            label: { text: '操作块2' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true,
          },
        ]),
        // 设置ChipV2的style属性。
        itemStyle: new ChipGroupV2ItemStyle({
          size: ChipV2Size.NORMAL,
          backgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_button_normal')),
          fontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary')),
          selectedBackgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_emphasize')),
          selectedFontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary_contrary')),
        }),
        selectedIndexes: this.selectedIndex,
        multiple: true,
        chipGroupSpace: new ChipGroupV2Space({ itemSpace: 8, endSpace: 0 }),
        chipGroupPadding: new ChipGroupV2Padding({ top: 10, bottom: 10 }),
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
        // ChipGroupV2最右侧显示的自定义组件。
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

### 示例4（监听ChipGroupV2内对象类型属性的内部属性变化）

[ChipGroupV2Items](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2items-c.md)、[ChipGroupV2Item](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2item-c.md)、[ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md)等类使用了@ObservedV2装饰器，ChipGroupV2组件通过@Param接收各属性参数。对于@Trace装饰的基本类型属性（如ChipGroupV2Space的itemSpace等），@Param已能观测到属性变化并触发UI刷新，无需额外处理。但对于这些类中对象类型属性（如ChipGroupV2Item中prefixIcon的size）的内部属性，这些对象类型本身未被@ObservedV2装饰，其内部属性变化无法被@Param感知，导致修改内部属性时UI不会自动刷新。使用[makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved)接口对对象类型属性进行包裹，可以为该对象的内部属性补充深度观察能力。makeObserved接口的详细说明请参考[makeObserved接口：将非观察数据变为可观察数据](../../../ui/state-management/arkts-new-makeObserved.md)。

以下示例对比了两种场景：点击“修改itemSpace间距”按钮修改chipGroupSpace的itemSpace属性（@Trace装饰的基本类型属性，已支持观测），UI自动刷新；点击“修改图标大小”按钮修改ChipGroupV2Item中prefixIcon的size内部属性（对象类型属性的内部属性，需通过UIUtils.makeObserved包裹size才能观测），UI同样自动刷新。



```TypeScript
import {
  ChipGroupV2,
  ChipGroupV2Items,
  ChipGroupV2ItemStyle,
  ChipGroupV2Space,
  ChipGroupV2Padding,
  LengthMetrics,
  UIUtils
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local items: ChipGroupV2Items = new ChipGroupV2Items([
    {
      // 使用UIUtils.makeObserved包裹size，使内部属性width和height可被观测。
      prefixIcon: {
        src: $r('sys.media.ohos_ic_public_clock'),
        size: UIUtils.makeObserved({ width: LengthMetrics.fp(16), height: LengthMetrics.fp(16) })
      },
      label: { text: '操作块1' }
    },
    {
      label: { text: '操作块2' }
    },
    {
      label: { text: '操作块3' }
    }
  ]);
  // ChipGroupV2Space的内部属性已被@Trace装饰，无需makeObserved。
  @Local chipGroupSpace: ChipGroupV2Space = new ChipGroupV2Space({ itemSpace: 8 });
  @Local chipGroupPadding: ChipGroupV2Padding = new ChipGroupV2Padding({ top: 10, bottom: 10 });
  @Local itemStyle: ChipGroupV2ItemStyle = new ChipGroupV2ItemStyle({});
  @Local selectedIndexes: number[] = [];
  @Local currentIconSize: number = 16;
  @Local currentItemSpace: number = 8;

  build() {
    Column({ space: 10 }) {
      ChipGroupV2({
        items: this.items,
        $items: (items: ChipGroupV2Items) => { this.items = items; },
        itemStyle: this.itemStyle,
        chipGroupSpace: this.chipGroupSpace,
        chipGroupPadding: this.chipGroupPadding,
        selectedIndexes: this.selectedIndexes,
        $selectedIndexes: (indexes: number[]) => { this.selectedIndexes = indexes; },
      })
      // 修改@Trace装饰的基本类型属性，UI自动刷新。
      Button('修改itemSpace间距')
        .onClick(() => {
          this.currentItemSpace = this.currentItemSpace === 8 ? 16 : 8;
          this.chipGroupSpace.itemSpace = this.currentItemSpace;
        })
      // 修改对象类型属性的内部属性，由于makeObserved包裹，UI同样自动刷新。
      Button('修改图标大小')
        .onClick(() => {
          if (this.items.length >= 1 && this.items[0] && this.items[0].prefixIcon && this.items[0].prefixIcon.size) {
            this.currentIconSize = this.currentIconSize === 16 ? 30 : 16;
            this.items[0].prefixIcon.size.width = LengthMetrics.fp(this.currentIconSize);
            this.items[0].prefixIcon.size.height = LengthMetrics.fp(this.currentIconSize);
          }
        })
    }
  }
}
```

### 示例5（设置系统材质样式）

该示例通过设置[ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md)的backgroundSystemMaterial属性，实现了[ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md)的系统材质样式效果，包括沉浸式材质和自动反色功能。组件需放置在Navigation的标题栏中，沉浸光感效果才会生效。

从API版本26.0.0开始，[ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md)新增backgroundSystemMaterial属性。

```TypeScript
import {
  ChipGroupV2,
  ChipGroupV2Items,
  ChipGroupV2ItemStyle,
  ChipGroupV2Space,
  ChipGroupV2Padding,
  LengthMetrics,
  UIUtils,
  uiMaterial,
  ColorMetrics
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local items: ChipGroupV2Items = new ChipGroupV2Items([
    {
      label: { text: '操作块1' }
    },
    {
      label: { text: '操作块2' }
    },
    {
      label: { text: '操作块3' }
    },
    {
      label: { text: '操作块4' }
    },
    {
      label: { text: '操作块5' }
    }
  ]);
  @Local chipGroupSpace: ChipGroupV2Space = new ChipGroupV2Space({ itemSpace: 8 });
  @Local chipGroupPadding: ChipGroupV2Padding = new ChipGroupV2Padding({ top: 10, bottom: 10 });
  @Local itemStyle: ChipGroupV2ItemStyle = new ChipGroupV2ItemStyle({
    backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      colorInvert: true
    }),
  });
  @Local selectedIndexes: number[] = [];

  @Builder
  NavigationTitle() {
    Column({ space: 10 }) {
      ChipGroupV2({
        items: this.items,
        $items: (items: ChipGroupV2Items) => { this.items = items; },
        itemStyle: this.itemStyle,
        chipGroupSpace: this.chipGroupSpace,
        chipGroupPadding: this.chipGroupPadding,
        selectedIndexes: this.selectedIndexes,
        $selectedIndexes: (indexes: number[]) => { this.selectedIndexes = indexes; },
      })
    }
    .linearGradient({
      angle: 90, // 渐变角度，90度是从左到右。
      colors: [
        ['#FF9A9E', 0.0], // 起始颜色及位置（0.0表示起点）。
        ['#FECFEF', 0.5], // 中间颜色及位置。
        ['#3B324C', 1.0] // 结束颜色及位置（1.0表示终点）。
      ]
    })
    .padding(12)
    .width('100%')
  }


  build() {
    Column() {
      Navigation() {
        // 页面内容
      }
      .title({ builder: this.NavigationTitle, height: '100%' })
    }.width('100%').height('100%')
  }

}
```
