# @ohos.arkui.advanced.SubHeader

## 导入模块

```TypeScript
import { OperationOption, OperationType, SelectOptions, SubHeader, SymbolOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md) | Declare type OperationOption |
| [SelectOptions](arkts-arkui-arkui-advanced-subheader-selectoptions-c.md) | Declare type SelectOption |
| [SymbolOptions](arkts-arkui-arkui-advanced-subheader-symboloptions-c.md) | Declare type SymbolOptions |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SubHeader](arkts-arkui-arkui-advanced-subheader-subheader-s.md) | 子标题组件，用于列表项或内容项顶部，将该列表或内容划分为一个区块，子标题名称用来概括该区块内容。支持多种样式配置，包括图标、主副标题、下拉选择器和操作按钮等，可满足不同场景下的内容分区和导航需求，提升界面的信息层次感和用户体验。适用于列表分组、内容分类展示、表单分区等场景。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [OperationType](arkts-arkui-arkui-advanced-subheader-operationtype-e.md) | 定义子标题操作区的元素样式。 |

## 示例

### 示例1（效率型子标题）

该示例主要演示子标题左侧为icon、secondaryTitle，右侧operationType为按钮类型。



```TypeScript
import { Prompt, OperationType, SubHeader } from '@kit.ArkUI';

@Entry
@Component
struct SubHeaderExample {
  build() {
    Column() {
      SubHeader({
        icon: $r('sys.media.ohos_ic_public_email'),
        secondaryTitle: '二级标题',
        operationType: OperationType.BUTTON,
        operationItem: [{
          value: '操作',
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }]
      })
    }
  }
}
```

### 示例2（双行文本内容型子标题）

该示例主要演示子标题左侧为primaryTitle、secondaryTitle，右侧operationType类型为TEXT_ARROW。



```TypeScript
import { Prompt, OperationType, SubHeader } from '@kit.ArkUI';

@Entry
@Component
struct SubHeaderExample {
  build() {
    Column() {
      SubHeader({
        primaryTitle: '一级标题',
        secondaryTitle: '二级标题',
        operationType: OperationType.TEXT_ARROW,
        operationItem: [{
          value: '更多',
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }]
      })
    }
  }
}
```

### 示例3（spinner型内容型子标题）

该示例主要演示子标题左侧为select，右侧operationType类型为ICON_GROUP。



```TypeScript
import { Prompt, OperationType, SubHeader } from '@kit.ArkUI';

@Entry
@Component
struct SubHeaderExample {
  build() {
    Column() {
      SubHeader({
        // 左侧为select选择器
        select: {
          options: [{ value: 'aaa' }, { value: 'bbb' }, { value: 'ccc' }],
          value: 'selectDemo',
          selected: 2,
          onSelect: () => {
            Prompt.showToast({ message: 'demo' });
          }
        },
        operationType: OperationType.ICON_GROUP,
        // 右侧为三个icon图标
        operationItem: [{
          value: $r('sys.media.ohos_ic_public_email'),
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }, {
          value: $r('sys.media.ohos_ic_public_email'),
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }, {
          value: $r('sys.media.ohos_ic_public_email'),
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }]
      })
    }
  }
}
```

### 示例4（设置左侧symbol图标）

该示例主要演示子标题左侧icon设置symbol图标。



```TypeScript
import { Prompt, OperationType, SubHeader } from '@kit.ArkUI';

@Entry
@Component
struct SubHeaderExample {
  build() {
    Column() {
      SubHeader({
        // 设置icon为symbol图标
        icon: $r('sys.symbol.ohos_wifi'),
        iconSymbolOptions: {
          effectStrategy: SymbolEffectStrategy.HIERARCHICAL,
        },
        secondaryTitle: '标题',
        operationType: OperationType.BUTTON,
        operationItem: [{
          value: '操作',
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }]
      })
    }
  }
}
```

### 示例5（设置右侧symbol图标）

该示例主要演示子标题operationType设置为OperationType.ICON_GROUP，operationItem的value设置为symbol图标。



```TypeScript
import { Prompt, OperationType, SubHeader } from '@kit.ArkUI';

@Entry
@Component
struct SubHeaderExample {
  build() {
    Column() {
      SubHeader({
        // 设置左侧select
        select: {
          options: [{ value: 'aaa' }, { value: 'bbb' }, { value: 'ccc' }],
          value: 'selectDemo',
          selected: 2,
          onSelect: () => {
            Prompt.showToast({ message: 'demo' });
          }
        },
        operationType: OperationType.ICON_GROUP,
        // 设置右侧icon
        operationItem: [{
          value: $r('sys.symbol.ohos_lungs'),
          action: () => {
            Prompt.showToast({ message: 'icon1' });
          }
        }, {
          value: $r('sys.symbol.ohos_lungs'),
          action: () => {
            Prompt.showToast({ message: 'icon2' });
          }
        }, {
          value: $r('sys.symbol.ohos_lungs'),
          action: () => {
            Prompt.showToast({ message: 'icon3' });
          }
        }],
        // 设置右侧icon图标symbol样式
        operationSymbolOptions: [{
          fontWeight: FontWeight.Lighter,
        }, {
          renderingStrategy: SymbolRenderingStrategy.MULTIPLE_COLOR,
          fontColor: [Color.Blue, Color.Grey, Color.Green],
        }, {
          renderingStrategy: SymbolRenderingStrategy.MULTIPLE_OPACITY,
          fontColor: [Color.Blue, Color.Grey, Color.Green],
        }]
      })
    }
  }
}
```

### 示例6（自定义标题内容）

该示例主要演示SubHeader设置titleBuilder自定义标题内容的效果。设置titleBuilder后，primaryTitle、secondaryTitle属性将不生效。



```TypeScript
import { Prompt, OperationType, SubHeader } from '@kit.ArkUI';

@Entry
@Component
struct SubHeaderExample {
  // 自定义左侧标题
  @Builder
  TitleBuilder(): void {
    Text('自定义标题')
      .fontSize(24)
      .fontColor(Color.Blue)
      .fontWeight(FontWeight.Bold)
  }

  build() {
    Column() {
      SubHeader({
        // 调用TitleBuilder
        titleBuilder: () => {
          this.TitleBuilder();
        },
        primaryTitle: '一级标题',
        secondaryTitle: '二级标题',
        icon: $r('sys.symbol.ohos_star'),
        operationType: OperationType.TEXT_ARROW,
        operationItem: [{
          value: '更多信息',
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }]
      })
    }
  }
}
```

### 示例7（自定义标题样式）

该示例主要演示SubHeader设置标题和副标题字体样式以及标题内外边距的效果。



```TypeScript
import { Prompt, OperationType, SubHeader, LengthMetrics, TextModifier } from '@kit.ArkUI';

@Entry
@Component
struct SubHeaderExample {
  // 设置主副标题文本颜色
  @State primaryModifier: TextModifier = new TextModifier().fontColor(Color.Blue);
  @State secondaryModifier: TextModifier = new TextModifier().fontColor(Color.Blue);

  build() {
    Column() {
      SubHeader({
        primaryTitle: 'primaryTitle',
        secondaryTitle: 'secondaryTitle',
        primaryTitleModifier: this.primaryModifier,
        secondaryTitleModifier: this.secondaryModifier,
        operationType: OperationType.TEXT_ARROW,
        operationItem: [{
          value: '更多信息',
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }],
        // 标题内外间距
        contentMargin: { start: LengthMetrics.vp(20), end: LengthMetrics.vp(20) },
        contentPadding: { start: LengthMetrics.vp(20), end: LengthMetrics.vp(20) }
      })
    }
  }
}
```

### 示例8（右侧按钮自定义播报）

从API version 18开始，该示例通过设置SubHeader的右侧按钮属性accessibilityText、accessibilityDescription、accessibilityLevel自定义屏幕朗读播报文本。



```TypeScript
import { Prompt, OperationType, SubHeader } from '@kit.ArkUI';

@Entry
@Component
struct SubHeaderExample {
  build() {
    Column() {
      Divider().color('grey').width('100%').height('2vp')
      SubHeader({
        // 图标+二级标题, 右侧button
        icon: $r('sys.media.ohos_ic_public_email'),
        secondaryTitle: '二级标题',
        operationType: OperationType.BUTTON,
        operationItem: [{
          value: '操作',
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }]
      })
      Divider().color('grey').width('100%').height('2vp')
      SubHeader({
        // 右侧text_arrow
        primaryTitle: '一级标题',
        secondaryTitle: '二级标题',
        operationType: OperationType.TEXT_ARROW,
        operationItem: [{
          value: '更多',
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }]
      })
      Divider().color('grey').width('100%').height('2vp')
      SubHeader({
        // 左侧select 右侧是icon_(依次获焦)
        select: {
          options: [{ value: 'aaa' }, { value: 'bbb' }, { value: 'ccc' }],
          value: 'selectDemo',
          selected: 0,
          onSelect: (index: number, value?: string) => {
            console.info(`SubHeader onSelect index : ${index}, value: ${value}`);
          }
        },
        operationType: OperationType.ICON_GROUP,
        operationItem: [{
          value: $r('sys.media.ohos_ic_public_email'),
          accessibilityText: '图标1',
          accessibilityLevel: 'yes',
        }, {
          value: $r('sys.media.ohos_ic_public_email'),
          accessibilityText: '图标2',
          accessibilityLevel: 'no',
        }, {
          value: $r('sys.media.ohos_ic_public_email'),
          accessibilityText: '图标3',
          accessibilityDescription: '点击操作图标3',
        }]
      })
      Divider().color('grey').width('100%').height('2vp')
    }
  }
}
```

### 示例9（右侧按钮设置默认获焦）

在获焦状态下，该示例通过设置SubHeader的右侧按钮属性defaultFocus使其默认获焦。

从API version 18开始，在[OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md)中新增defaultFocus接口。

```TypeScript
import { Prompt, OperationType, SubHeader } from '@kit.ArkUI';

@Entry
@Component
struct SubHeaderExample {
  build() {
    Column() {
      SubHeader({
        // 图标+二级标题, 右侧button
        icon: $r('sys.media.ohos_ic_public_email'),
        secondaryTitle: '二级标题',
        operationType: OperationType.BUTTON,
        operationItem: [{
          value: '操作',
          defaultFocus: true,
          action: () => {
            Prompt.showToast({ message: 'demo' });
          }
        }]
      })
    }
  }
}
```
