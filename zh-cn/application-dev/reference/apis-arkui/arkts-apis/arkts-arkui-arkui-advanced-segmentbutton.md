# @ohos.arkui.advanced.SegmentButton

## 导入模块

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md) | 分段按钮中的按钮选项。 |
| [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md) | 用于保存按钮信息的数组。 |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) |  |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SegmentButton](arkts-arkui-arkui-advanced-segmentbutton-segmentbutton-s.md) | 分段按钮组件包含页签类分段按钮和胶囊类分段按钮。页签类分段按钮适用于页面或内容区域的切换场景；胶囊类分段按钮适用于单选或多选的选择场景，包含胶囊类单选分段按钮和胶囊类多选分段按钮。该组件支持自定义文本颜色、字体大小、字体粗细、背景色、图片尺寸、内边距、背景模糊材质等外观属性，支持仅文本、仅图标和图标+文本三种按钮样式，并提供无障碍朗读、布局方向镜像、自定义圆角、属性动画等能力，适用于需要快速构建符合设计规范的分段选择界面的场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md) | 用于构建胶囊类的SegmentButtonOptions对象。 |
| [CapsuleSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonoptions-i.md) | 胶囊类分段按钮选项。继承自[CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md)。 |
| [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md) | 定义分段按钮组件的可自定义的属性。 |
| [SegmentButtonIconItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttoniconitem-i.md) | 图标按钮信息。 |
| [SegmentButtonIconTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonicontextitem-i.md) | 图标与文本按钮信息。 |
| [SegmentButtonItemOptionsConstructorOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsconstructoroptions-i.md) | 构造参数用于SegmentButtonItemOptions。 |
| [SegmentButtonTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttontextitem-i.md) | 文本按钮信息。 |
| [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md) | 构建页签类的SegmentButtonOptions对象。 |
| [TabSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonoptions-i.md) | 页签类分段按钮选项。继承自[TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md) | 不支持百分比类型的长度联合类型。 |
| [ItemRestriction](arkts-arkui-itemrestriction-t.md) | 保存按钮信息的元组类型。 |
| [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | 用于保存按钮信息的数组的联合类型。 |
| [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | 用于保存按钮信息的元组的联合类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BorderRadiusMode](arkts-arkui-arkui-advanced-segmentbutton-borderradiusmode-e.md) | 边框圆角模式枚举，用于控制分段按钮的圆角计算方式。 |

## 示例

### 示例1（设置分段按钮的类型）

通过配置SegmentButtonOptions的tab和capsule，创建两种不同类型的分段按钮。



```TypeScript
import {
  ItemRestriction,
  SegmentButton,
  SegmentButtonItemTuple,
  SegmentButtonOptions,
  SegmentButtonTextItem
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // 页签类分段按钮数组。
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: '页签按钮1' }, { text: '页签按钮2' }, {
      text: '页签按钮3'
    }] as ItemRestriction<SegmentButtonTextItem>,
    // 配置CommonSegmentButtonOptions，实现背景模糊样式。
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  // 胶囊类分段按钮数组。
  @State singleSelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: '单选按钮1' }, { text: '单选按钮2' }, { text: '单选按钮3' }] as SegmentButtonItemTuple,
    multiply: false,
    // 配置CommonSegmentButtonOptions，实现背景模糊样式。
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  // 可多选胶囊类分段按钮数组。
  @State multiplySelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: '多选按钮1' }, { text: '多选按钮2' }, { text: '多选按钮3' }] as SegmentButtonItemTuple,
    multiply: true
  });
  // 胶囊类分段按钮带选中非选中图标数组。
  @State iconCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: false,
    // 配置CommonSegmentButtonOptions，实现背景模糊样式。
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  // 可多选胶囊类分段按钮带选中非选中图标数组。
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: '图标1', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标2', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标3', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标4', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标5', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: true
  });
  @State tabSelectedIndexes: number[] = [1];
  @State singleSelectCapsuleSelectedIndexes: number[] = [0];
  @State multiplySelectCapsuleSelectedIndexes: number[] = [0, 1];
  @State singleSelectIconCapsuleSelectedIndexes: number[] = [3];
  @State multiplySelectIconTextCapsuleSelectedIndexes: number[] = [1, 2];

  build() {
    Row() {
      Column() {
        Column({ space: 25 }) {
          SegmentButton({
            options: this.tabOptions,
            selectedIndexes: $tabSelectedIndexes
          })
          SegmentButton({
            options: this.singleSelectCapsuleOptions,
            selectedIndexes: $singleSelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.multiplySelectCapsuleOptions,
            selectedIndexes: $multiplySelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconCapsuleOptions,
            selectedIndexes: $singleSelectIconCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconTextCapsuleOptions,
            selectedIndexes: $multiplySelectIconTextCapsuleSelectedIndexes
          })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例2（设置分段按钮样式）

通过配置CommonSegmentButtonOptions，实现自定义分段按钮的文本以及背景板样式。



```TypeScript
import {
  ItemRestriction,
  SegmentButton,
  SegmentButtonItemTuple,
  SegmentButtonOptions,
  SegmentButtonTextItem
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: '页签按钮1' }, { text: '页签按钮2' }, {
      text: '页签按钮3'
    }] as ItemRestriction<SegmentButtonTextItem>,
    backgroundColor: 'rgb(213,213,213)',
    selectedBackgroundColor: 'rgb(112,112,112)', // 配置CommonSegmentButtonOptions，实现选中背景色
    textPadding: {
      top: 10,
      right: 10,
      bottom: 10,
      left: 10
    }, // 配置CommonSegmentButtonOptions，实现文字内边距
  });
  @State singleSelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: '单选按钮1' }, { text: '单选按钮2' }, { text: '单选按钮3' }] as SegmentButtonItemTuple,
    multiply: false,
    fontColor: 'rgb(0,74,175)', // 配置CommonSegmentButtonOptions，实现文字颜色
    selectedFontColor: 'rgb(247,247,247)', // 配置CommonSegmentButtonOptions，实现选中文字颜色
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK // 配置CommonSegmentButtonOptions，实现背景模糊样式
  });
  @State multiplySelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: '多选按钮1' }, { text: '多选按钮2' }, { text: '多选按钮3' }] as SegmentButtonItemTuple,
    multiply: true,
    fontSize: 18,
    selectedFontSize: 18,
    fontWeight: FontWeight.Bolder, // 配置CommonSegmentButtonOptions，实现文字粗细
    selectedFontWeight: FontWeight.Lighter, // 配置CommonSegmentButtonOptions，实现选中文字粗细
  });
  @State iconCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: false,
    imageSize: { width: 40, height: 40 },
    buttonPadding: {
      top: 6,
      right: 10,
      bottom: 6,
      left: 10
    },
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: '图标1', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标2', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标3', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标4', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标5', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: true,
    imageSize: { width: 10, height: 10 },
  });
  @State tabSelectedIndexes: number[] = [0];
  @State singleSelectCapsuleSelectedIndexes: number[] = [0];
  @State multiplySelectCapsuleSelectedIndexes: number[] = [0, 1];
  @State singleSelectIconCapsuleSelectedIndexes: number[] = [3];
  @State multiplySelectIconTextCapsuleSelectedIndexes: number[] = [1, 2];

  build() {
    Row() {
      Column() {
        Column({ space: 20 }) {
          SegmentButton({ options: this.tabOptions, selectedIndexes: $tabSelectedIndexes })
          SegmentButton({
            options: this.singleSelectCapsuleOptions,
            selectedIndexes: $singleSelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.multiplySelectCapsuleOptions,
            selectedIndexes: $multiplySelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconCapsuleOptions,
            selectedIndexes: $singleSelectIconCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconTextCapsuleOptions,
            selectedIndexes: $multiplySelectIconTextCapsuleSelectedIndexes
          })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例3（分段按钮数组处理）

该示例通过pop、shift、unshift等函数实现分段按钮数组的添加、移除等操作。



```TypeScript
import {
  SegmentButton,
  SegmentButtonOptions,
  SegmentButtonItemOptionsArray,
  SegmentButtonItemTuple,
  SegmentButtonItemOptions
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // 胶囊类分段按钮数组。
  @State singleSelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: '1' }, { text: '2' }, { text: '3' },
      { text: '4' }, { text: '5' }] as SegmentButtonItemTuple,
    multiply: false,
    // 配置CommonSegmentButtonOptions，实现背景模糊样式。
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  @State capsuleSelectedIndexes: number[] = [0];

  build() {
    Row() {
      Column() {
        Column({ space: 10 }) {
          SegmentButton({
            options: this.singleSelectCapsuleOptions,
            selectedIndexes: $capsuleSelectedIndexes
          })
          // 点击“删除第一个按钮”，第一个按钮会删除。
          Button('删除第一个按钮')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.shift()
            })
          // 点击“删除最后一个按钮”，最后一个按钮会删除。
          Button('删除最后一个按钮')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.pop()
            })
          // 点击“末尾增加一个按钮push”，在按钮末尾会增加一个按钮。
          Button('末尾增加一个按钮push')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.push({ text: 'push' })
            })
          // 点击“开头增加一个按钮unshift”，在按钮开头会增加一个按钮。
          Button('开头增加一个按钮unshift')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.unshift(({ text: 'unshift' }))
            })
          // 点击“将按钮2、3替换为splice1、splice2”，按钮2、3会被替换成splice1、splice2。
          Button('将按钮2、3替换为splice1、splice2')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.splice(1, 2, new SegmentButtonItemOptions({
                text: 'splice1'
              }), new SegmentButtonItemOptions({ text: 'splice2' }))
            })
          // 点击“更改所有按钮文字”，按钮会由1、2、3、4、5替换成a、b、c、d、e。
          Button('更改所有按钮文字')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons =
                SegmentButtonItemOptionsArray.create([{ text: 'a' }, { text: 'b' },
                  { text: 'c' }, { text: 'd' }, { text: 'e' }])
            })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例4（设置镜像效果）

该示例通过配置direction属性设置分段按钮的布局方向，实现镜像效果。



```TypeScript
import { LengthMetrics, SegmentButton, SegmentButtonOptions } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // 页签类分段按钮数组。
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: '页签按钮1' }, { text: '页签按钮2' }, {
      text: '页签按钮3'
    }],
    direction: Direction.Rtl, // 设置分段按钮的布局方向。
    backgroundColor: Color.Green, // 设置分段按钮的背景板颜色。
    selectedBackgroundColor: Color.Orange, // 设置分段按钮组件的按钮选中态背景板颜色。
    // 设置文本内边距。
    localizedTextPadding: {
      end: LengthMetrics.vp(10),
      start: LengthMetrics.vp(10)
    },
  });
  // 胶囊类分段按钮数组。
  @State singleSelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: '单选按钮1' }, { text: '单选按钮2' }, { text: '单选按钮3' }],
    multiply: false, // 设置分段按钮组件是否可以多选。
    direction: Direction.Rtl, // 设置分段按钮的布局方向。
    fontColor: Color.Black, // 设置分段按钮组件的按钮未选中态的文本颜色。
    selectedFontColor: Color.Yellow, // 设置分段按钮组件的按钮选中态的文本颜色。
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK // 设置分段按钮组件的背景模糊材质。
  });
  // 胶囊类分段按钮数组。
  @State multiplySelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: '多选按钮1' }, { text: '多选按钮2' }, { text: '多选按钮3' }],
    multiply: true, // 设置分段按钮组件是否可以多选。
    direction: Direction.Rtl, // 设置分段按钮的布局方向。
    fontSize: 18, // 设置分段按钮组件的按钮未选中态的字体大小。
    selectedFontSize: 18, // 设置分段按钮组件的按钮选中态的字体大小。
    fontWeight: FontWeight.Bolder, // 设置分段按钮组件的按钮未选中态的字体粗细。
    selectedFontWeight: FontWeight.Lighter, // 设置分段按钮组件的按钮选中态的字体粗细。
  });
  // 胶囊类分段按钮数组。
  @State iconCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ],
    multiply: false, // 设置分段按钮组件是否可以多选。
    direction: Direction.Rtl, // 设置分段按钮的布局方向。
    imageSize: { width: 40, height: 40 }, // 设置分段按钮组件的图片尺寸。
    // 设置分段按钮组件的按钮内边距，支持随布局方向（LTR/RTL）自适应。
    localizedButtonPadding: {
      end: LengthMetrics.vp(10),
      start: LengthMetrics.vp(10)
    },
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK // 设置分段按钮组件的背景模糊材质。
  });
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: '图标1', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标2', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标3', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标4', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标5', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ],
    multiply: true, // 设置分段按钮组件是否可以多选。
    direction: Direction.Rtl, // 设置分段按钮的布局方向。
    imageSize: { width: 10, height: 10 }, // 设置分段按钮组件的图片尺寸。
  });
  @State tabSelectedIndexes: number[] = [0];
  @State singleSelectCapsuleSelectedIndexes: number[] = [0];
  @State multiplySelectCapsuleSelectedIndexes: number[] = [0, 1];
  @State singleSelectIconCapsuleSelectedIndexes: number[] = [3];
  @State multiplySelectIconTextCapsuleSelectedIndexes: number[] = [1, 2];

  build() {
    Row() {
      Column() {
        Column({ space: 20 }) {
          SegmentButton({ options: this.tabOptions, selectedIndexes: $tabSelectedIndexes })
          SegmentButton({
            options: this.singleSelectCapsuleOptions,
            selectedIndexes: $singleSelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.multiplySelectCapsuleOptions,
            selectedIndexes: $multiplySelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconCapsuleOptions,
            selectedIndexes: $singleSelectIconCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconTextCapsuleOptions,
            selectedIndexes: $multiplySelectIconTextCapsuleSelectedIndexes
          })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例5（设置无障碍朗读）

通过配置accessibilityLevel和selectedIconAccessibilityText等属性，实现了分段按钮的无障碍朗读功能。



```TypeScript
import {
  ItemRestriction,
  SegmentButton,
  SegmentButtonItemTuple,
  SegmentButtonOptions,
  SegmentButtonTextItem,
  SegmentButtonItemOptions
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: '页签按钮1', accessibilityLevel: 'yes', accessibilityDescription: '页签按钮1 新手提醒' },
      { text: '页签按钮2', accessibilityLevel: 'yes', accessibilityDescription: '页签按钮2 新手提醒' },
      {
        text: '页签按钮3', accessibilityLevel: 'yes', accessibilityDescription: '页签按钮3 新手提醒'
      }] as ItemRestriction<SegmentButtonTextItem>,
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  @State iconCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      {
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: '未选中图标无障碍文本', // 未选中态按钮图标的无障碍文本。
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: '选中图标无障碍文本', // 选中态按钮图标的无障碍文本。
        accessibilityLevel: 'yes', // 无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。
        accessibilityDescription: 'SegmentButtonIconItem 新手提醒' // 无障碍说明。
      },
      {
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: '未选中图标无障碍文本', // 未选中态按钮图标的无障碍文本。
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: '选中图标无障碍文本', // 选中态按钮图标的无障碍文本。
        accessibilityLevel: 'yes', // 无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。
        accessibilityDescription: 'SegmentButtonIconItem 新手提醒' // 无障碍说明。
      },
      {
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: '未选中图标无障碍文本', // 未选中态按钮图标的无障碍文本。
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: '选中图标无障碍文本', // 选中态按钮图标的无障碍文本。
        accessibilityLevel: 'yes', // 无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。
        accessibilityDescription: 'SegmentButtonIconItem 新手提醒' // 无障碍说明。
      },
      {
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: '未选中图标无障碍文本', // 未选中态按钮图标的无障碍文本。
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: '选中图标无障碍文本', // 选中态按钮图标的无障碍文本。
        accessibilityLevel: 'yes', // 无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。
        accessibilityDescription: 'SegmentButtonIconItem 新手提醒' // 无障碍说明。
      }
    ] as SegmentButtonItemTuple,
    multiply: false,
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      {
        text: '图标1',
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: '未选中图标无障碍文本', // 未选中态按钮图标的无障碍文本。
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: '选中图标无障碍文本', // 选中态按钮图标的无障碍文本。
        accessibilityLevel: 'yes', // 无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。
        accessibilityDescription: 'SegmentButtonIconTextItem 新手提醒' // 无障碍说明。
      },
      {
        text: '图标2',
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: '未选中图标无障碍文本', // 未选中态按钮图标的无障碍文本。
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: '选中图标无障碍文本', // 选中态按钮图标的无障碍文本。
        accessibilityLevel: 'yes', // 无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。
        accessibilityDescription: 'SegmentButtonIconTextItem 新手提醒' // 无障碍说明。
      },
      {
        text: '图标3',
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: '未选中图标无障碍文本', // 未选中态按钮图标的无障碍文本。
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: '选中图标无障碍文本', // 选中态按钮图标的无障碍文本。
        accessibilityLevel: 'yes', // 无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。
        accessibilityDescription: 'SegmentButtonIconTextItem 新手提醒' // 无障碍说明。
      },
      {
        text: '图标4',
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: '未选中图标无障碍文本', // 未选中态按钮图标的无障碍文本。
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: '选中图标无障碍文本', // 选中态按钮图标的无障碍文本。
        accessibilityLevel: 'yes', // 无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。
        accessibilityDescription: 'SegmentButtonIconTextItem 新手提醒' // 无障碍说明。
      }
    ] as SegmentButtonItemTuple,
    multiply: true
  });
  @State tabSelectedIndexes: number[] = [1];
  @State singleSelectIconCapsuleSelectedIndexes: number[] = [3];
  @State multiplySelectIconTextCapsuleSelectedIndexes: number[] = [1, 2];

  build() {
    Row() {
      Column() {
        Column({ space: 25 }) {
          SegmentButton({
            options: this.tabOptions,
            selectedIndexes: $tabSelectedIndexes
          })
          SegmentButton({
            options: this.iconCapsuleOptions,
            selectedIndexes: $singleSelectIconCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconTextCapsuleOptions,
            selectedIndexes: $multiplySelectIconTextCapsuleSelectedIndexes
          })
          Button('将按钮2、3替换为splice1、splice2')
            .onClick(() => {
              this.iconTextCapsuleOptions.buttons.splice(1, 2, new SegmentButtonItemOptions({
                text: 'splice1', accessibilityLevel: 'yes', accessibilityDescription: 'SegmentButtonItemOptions 新手提醒'
              }), new SegmentButtonItemOptions({
                text: 'splice2',
                icon: $r('sys.media.ohos_ic_public_email'),
                iconAccessibilityText: '未选中图标无障碍文本', // 未选中态按钮图标的无障碍文本。
                selectedIcon: $r('sys.media.ohos_ic_public_clock'),
                selectedIconAccessibilityText: '选中图标无障碍文本', // 选中态按钮图标的无障碍文本。
                accessibilityLevel: 'yes', // 无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。
                accessibilityDescription: 'SegmentButtonIconTextItem 新手提醒' // 无障碍说明。
              }))
            })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例6（设置自定义圆角）

该示例演示了如何为分段按钮组件设置自定义的边框圆角半径。



```TypeScript
import {
  BorderRadiusMode,
  ItemRestriction,
  LengthMetrics,
  SegmentButton,
  SegmentButtonOptions,
  SegmentButtonTextItem
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: '页签按钮1' }, { text: '页签按钮2' }, {
      text: '页签按钮3'
    }] as ItemRestriction<SegmentButtonTextItem>,
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK,
    borderRadiusMode: BorderRadiusMode.CUSTOM, // 设置自定义的边框圆角半径
    backgroundBorderRadius: LengthMetrics.vp(8),
    itemBorderRadius: LengthMetrics.vp(6)
  });
  @State tabSelectedIndexes: number[] = [1];

  build() {
    Row() {
      Column() {
        Column({ space: 25 }) {
          SegmentButton({
            options: this.tabOptions,
            selectedIndexes: $tabSelectedIndexes,
          })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例7（开启SegmentButton的属性动画）

本示例展示了SegmentButton开启属性动画，即enableStateAnimation设置为true后，修改选中项编号selectedIndexes值会触发按钮切换动画。并且选中项编号相同的两个SegmentButton组件，是否开启属性动画，也会呈现不同的切换动画。

从API version 24开始，[SegmentButton](#segmentbutton-1)新增enableStateAnimation属性。



```TypeScript
import { SegmentButton, SegmentButtonItemTuple, SegmentButtonOptions } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State singleSelectTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: '单选按钮1' }, { text: '单选按钮2' }, { text: '单选按钮3' }
    ] as SegmentButtonItemTuple,
    multiply: false
  });

  @State textCapsuleSingleSelected: number[] = [0]; // 单选按钮的选中索引值，默认选中第一个。

  enableStateAnimation: boolean[] = [false, true];
  @State enableStateAnimationIndex: number = 0;
  @State currentSelectedIndex: number = 0; // 切换选中项的索引计数器。

  build() {
    Row() {
      Column() {
        Column({ space: 25 }) {
          // 动画仅在手动点击切换选中项时生效，非点击类操作修改选中项均无动画。
          SegmentButton({
            options: this.singleSelectTextCapsuleOptions,
            selectedIndexes: this.textCapsuleSingleSelected // 未开启属性动画。
          })

          Text('enableStateAnimation: ' + this.enableStateAnimation[this.enableStateAnimationIndex])
            .fontSize(18)
            .fontWeight(FontWeight.Bold)

          Row({ space: 10 }) {
            Button('false')
              .onClick(() => {
                this.enableStateAnimationIndex = 0;
              })

            Button('true')
              .onClick(() => {
                this.enableStateAnimationIndex = 1;
              })
          }
          .width('100%')
          .justifyContent(FlexAlign.Center)
          .margin({ bottom: 10 })

          // enableStateAnimation为true时，切换选中项会触发按钮切换动画。enableStateAnimation为false时，动画仅在手动点击切换选中项时生效，非点击类操作修改选中项均无动画。
          SegmentButton({
            options: this.singleSelectTextCapsuleOptions,
            selectedIndexes: this.textCapsuleSingleSelected,
            enableStateAnimation: this.enableStateAnimation[this.enableStateAnimationIndex] // 开启属性动画。
          })

          Button('change selectedIndexes')
            .onClick(() => {
              // 对选中项的索引值进行自增操作，若超出最大索引则重置为0。
              this.currentSelectedIndex = this.currentSelectedIndex < 2 ? this.currentSelectedIndex + 1 : 0;
              this.textCapsuleSingleSelected = [this.currentSelectedIndex];
            })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例8（设置背景板材质）

以下示例通过backgroundSystemMaterial属性，为分段按钮设置了透明的背景板材质、开启自动反色和交互形变效果，并自定义反馈光感的颜色。

从API版本26.0.0开始，[SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md)和[CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md)中新增backgroundSystemMaterial属性。

该示例配图为高算力设备强档效果。



```TypeScript
import {
  ItemRestriction,
  SegmentButton,
  SegmentButtonOptions,
  SegmentButtonTextItem,
  uiMaterial
} from '@kit.ArkUI';


@Entry
@Component
struct Index {
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: '页签按钮1' }, { text: '页签按钮2' }, {
      text: '页签按钮3'
    }] as ItemRestriction<SegmentButtonTextItem>,
    backgroundColor: Color.Transparent,
    // 将fontColor设置为特殊系统资源值，启用自动反色能力。
    fontColor: $r('sys.color.font_primary'),
    // 设置为系统材质样式为ULTRA_THIN，并开启自动反色和交互形变效果、自定义反馈光感的颜色。
    backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      colorInvert: true,
      interactive: true,
      lightEffect: { color: undefined }
    })
  });
  @State tabSelectedIndexes: number[] = [0];

  @Builder
  NavigationTitle() {
    Column({ space: 20 }) {
      SegmentButton({
        options: this.tabOptions,
        selectedIndexes: $tabSelectedIndexes
      })
    }
    .width('100%')
    .height('20%')
    .padding(20)
    .linearGradient({
      angle: 90, // 渐变角度，90度是从左到右。
      colors: [
        ['#FF9A9E', 0.0], // 起始颜色及位置（0.0表示起点）。
        ['#FECFEF', 0.1], // 中间颜色及位置。
        ['#3B324C', 1.0] // 结束颜色及位置（1.0表示终点）。
      ]
    })
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

### 示例9（监听SegmentButtonOptions内属性的变化）

[SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md)使用了@Observed装饰器，SegmentButton组件通过@ObjectLink接收该对象。对于SegmentButtonOptions的一层基本类型属性（如fontColor、backgroundColor等），@Observed与@ObjectLink的联动机制已能观测到属性变化并触发UI刷新，无需额外处理。但对于SegmentButtonOptions中对象类型属性（如imageSize、buttonPadding等）的内部属性（如imageSize的width、height），属于更深层的嵌套属性，@State仅能观测到一层赋值变化，无法感知这类深层属性的修改，导致修改对象类型属性的内部属性时UI不会自动刷新。使用[makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved)接口对对象类型属性（如imageSize）进行包裹，可以为该对象的内部属性补充深度观察能力，使得修改内部属性（如width、height）时，框架能够监听到变化并触发UI刷新。makeObserved接口的详细说明请参考[makeObserved接口：将非观察数据变为可观察数据](../../../ui/state-management/arkts-new-makeObserved.md)。

以下示例对比了两种场景：点击“修改fontColor颜色”按钮修改iconTextCapsuleOptions的fontColor属性（一层基本类型属性，已通过@Observed与@ObjectLink支持观测），UI自动刷新；点击“修改图标大小”按钮修改iconTextCapsuleOptions.imageSize的width和height属性（imageSize对象的内部属性，需通过UIUtils.makeObserved包裹imageSize才能观测），UI同样自动刷新。

```TypeScript
import {
  SegmentButton,
  SegmentButtonOptions,
  SegmentButtonItemTuple,
  UIUtils
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: '图标1', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标2', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标3', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标4', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: '图标5', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: false,
    // 使用UIUtils.makeObserved包裹imageSize，使内部属性width和height可被观测。
    imageSize: UIUtils.makeObserved({ width: 30, height: 30 })
  });
  @State selectedIndexes: number[] = [0];
  @State currentFontColor: ResourceColor = Color.Blue;

  build() {
    Column({ space: 20 }) {
      SegmentButton({
        options: this.iconTextCapsuleOptions,
        selectedIndexes: $selectedIndexes
      })
      // 一层基本类型属性，已通过@Observed与@ObjectLink支持this.iconTextCapsuleOptions.fontColor的观测，UI自动刷新。
      Button('修改fontColor颜色')
        .onClick(() => {
          if (this.currentFontColor === Color.Blue) {
            this.currentFontColor = Color.Red;
          } else {
            this.currentFontColor = Color.Blue;
          }
          this.iconTextCapsuleOptions.fontColor = this.currentFontColor;
        })
      // 修改imageSize的内部属性，由于makeObserved包裹，UI会自动刷新。
      Button('修改图标大小')
        .onClick(() => {
          this.iconTextCapsuleOptions.imageSize.width = 10;
          this.iconTextCapsuleOptions.imageSize.height = 10;
        })
    }
    .width('100%')
    .height('50%')
    .padding({ top: 20 })
  }
}
```
