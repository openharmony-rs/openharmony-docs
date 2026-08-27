# Select

提供下拉选择菜单，让用户在多个选项间选择。Select组件支持设置选项图标、自定义样式、分割线等，适用于需要在有限空间内展示多个选项供用户选择的场景。
> **说明：**

## 子组件

无

## Select

```TypeScript
Select(options: Array<SelectOption>)
```

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | Array&lt;[SelectOption](arkts-arkui-selectoption-i.md)&gt; | 是 | 设置下拉选项。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [MenuItemConfiguration](arkts-arkui-menuitemconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [MenuOutlineOptions](arkts-arkui-menuoutlineoptions-i.md) | 下拉菜单框的外描边参数对象。 |
| [SelectOption](arkts-arkui-selectoption-i.md) | 下拉菜单项的信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnSelectCallback](arkts-arkui-onselectcallback-t.md) | 下拉菜单选中某一项时触发的回调函数类型定义。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ArrowPosition](arkts-arkui-arrowposition-e.md) | 箭头的位置。 |
| [AvoidanceMode](arkts-arkui-avoidancemode-e.md) | 下拉菜单避让模式的枚举选项。 |
| [MenuAlignType](arkts-arkui-menualigntype-e.md) | 下拉菜单的对齐方式。 |

## 示例

该示例通过配置[SelectOption](#selectoption对象说明)实现下拉菜单，并从API version 19开始通过设置[avoidance](arkts-arkui-select-attribute.md#avoidance)属性实现菜单的避让方式。

```TypeScript
// xxx.ets
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = 2;
  @State space: number = 8;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;

  build() {
    Column() {
      // $r('app.media.selection')需要替换为开发者所需的图像资源文件。
      Select([{ value: 'aaa', icon: $r("app.media.selection") },
        { value: 'bbb', icon: $r("app.media.selection") },
        { value: 'ccc', icon: $r("app.media.selection") },
        { value: 'ddd', icon: $r("app.media.selection") }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .space(this.space)
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        .optionWidth(200)
        .optionHeight(300)
        /**
         * 选中下拉项回调
         * index：选中项下标
         * text：选中项文本（可选参数）
         */
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          // 更新选中索引状态
          this.index = index;
          // 存在文本则更新选择框展示文字
          if (text) {
            this.text = text;
          }
        })
        // 组件下方无足够空间时，覆盖目标组件
        .avoidance(AvoidanceMode.COVER_TARGET);
    }.width('100%')
  }
}
```

该示例实现了一个下拉菜单中图片为Symbol的Select组件，并从API version 19开始通过设置[avoidance](arkts-arkui-select-attribute.md#avoidance)属性实现菜单的避让方式。

```TypeScript
// xxx.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = 2;
  @State space: number = 8;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;
  @State symbolModifier1: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')).fontColor([Color.Green]);
  @State symbolModifier2: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]);
  @State symbolModifier3: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_trash')).fontColor([Color.Gray]);
  @State symbolModifier4: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.exposure')).fontColor([Color.Gray]);

  build() {
    Column() {
      Select([{ value: 'aaa', symbolIcon: this.symbolModifier1 },
        { value: 'bbb', symbolIcon: this.symbolModifier2 },
        { value: 'ccc', symbolIcon: this.symbolModifier3 },
        { value: 'ddd', symbolIcon: this.symbolModifier4 }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .space(this.space)
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        /**
         * 选中下拉项回调
         * index：选中项下标
         * text：选中项文本（可选参数）
         */
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          // 更新选中索引状态
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        // 组件下方无足够空间时，覆盖目标组件
        .avoidance(AvoidanceMode.COVER_TARGET);
    }.width('100%')
  }
}
```

该示例实现了一个自定义下拉菜单选项的Select组件。自定义下拉菜单选项样式为“文本 + Symbol图片 + 空白间隔 + 文本 + 绘制三角形”，点击菜单选项后Select组件显示菜单选项的文本内容。

```TypeScript
import { SymbolGlyphModifier } from '@kit.ArkUI';

/**
 * 自定义下拉菜单项内容修饰器
 * 实现ContentModifier标准接口，用于替换Select下拉面板默认Item布局
 * 可传入自定义文本，在菜单项尾部额外展示文字
 */
class MyMenuItemContentModifier implements ContentModifier<MenuItemConfiguration> {
  modifierText: string = "";

  constructor(text: string) {
    this.modifierText = text;
  }

  applyContent(): WrappedBuilder<[MenuItemConfiguration]> {
    return wrapBuilder(MenuItemBuilder);
  }
}

/**
 * 自定义Select下拉菜单项UI构建器
 * 完全重写MenuItem布局：左侧文字 + 图标 + 自定义文本 + 三角形边框图形
 * @param configuration Select内部菜单项配置对象，包含value、索引、图标、自定义修饰器等信息
 */
@Builder
function MenuItemBuilder(configuration: MenuItemConfiguration) {
  Row() {
    Text(configuration.value)
    Blank()
    // 优先渲染系统矢量Symbol图标
    if (configuration.symbolIcon) {
      SymbolGlyph().attributeModifier(configuration.symbolIcon).fontSize(24)
    } else if (configuration.icon) {
      Image(configuration.icon).size({ width: 24, height: 24 })
    }
    Blank(30)
    // 读取自定义修饰器传入的尾部文本并展示
    Text((configuration.contentModifier as MyMenuItemContentModifier).modifierText)
    Blank(30)
    // 绘制自定义三角形路径图形，仅描边无填充
    Path()
      .width('100px')
      .height('150px')
      .commands('M40 0 L80 100 L0 100 Z')
      .fillOpacity(0)
      .stroke(Color.Black)
      .strokeWidth(3)
  }
  .padding({left: 8, top: 8})
  .onClick(() => {
    configuration.triggerSelect(configuration.index, configuration.value.valueOf().toString());
  })
}

@Entry
@Component
struct SelectExample {
  @State text: string = "Content Modifier Select";
  @State symbolModifier1: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_trash')).fontColor([Color.Gray]);
  @State symbolModifier2: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.exposure')).fontColor([Color.Gray]);

  build() {
    Column() {
      Row() {
        // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
        Select([{ value: 'item1', icon: $r('app.media.icon'), symbolIcon: this.symbolModifier1 },
          { value: 'item1', icon: $r('app.media.icon'), symbolIcon: this.symbolModifier2 }])
          .value(this.text)
          .onSelect((index: number, text?: string) => {
            console.info('Select index:' + index);
            console.info('Select text:' + text);
          })
          // 绑定自定义菜单项修饰器，替换下拉面板默认布局
          .menuItemContentModifier(new MyMenuItemContentModifier("Content Modifier"))

      }.alignItems(VerticalAlign.Center).height('50%')
    }
  }
}
```

该示例通过配置divider的DividerOptions类型实现分割线样式的下拉菜单，并从API version 19开始通过设置[avoidance](arkts-arkui-select-attribute.md#avoidance)属性实现菜单的避让方式。

```TypeScript
// xxx.ets
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = -1;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;

  build() {
    Column() {
      // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
      Select([{ value: 'aaa', icon: $r("app.media.icon") },
        { value: 'bbb', icon: $r("app.media.icon") },
        { value: 'ccc', icon: $r("app.media.icon") },
        { value: 'ddd', icon: $r("app.media.icon") }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        .optionWidth(200)
        .optionHeight(300)
        /**
         * 下拉选项之间分割线自定义配置
         * strokeWidth：分割线粗细
         * color：分割线颜色
         * startMargin/endMargin：分割线左右两侧边距
         */
        .divider({
          strokeWidth: 5,
          color: Color.Blue,
          startMargin: 10,
          endMargin: 10
        })
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        .avoidance(AvoidanceMode.COVER_TARGET);
    }.width('100%')
  }
}
```

该示例通过配置divider为null实现无分割线样式的下拉菜单，并从API version 19开始通过设置[avoidance](arkts-arkui-select-attribute.md#avoidance)属性实现菜单的避让方式。

```TypeScript
// xxx.ets
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = -1;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;

  build() {
    Column() {
      // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
      Select([{ value: 'aaa', icon: $r("app.media.icon") },
        { value: 'bbb', icon: $r("app.media.icon") },
        { value: 'ccc', icon: $r("app.media.icon") },
        { value: 'ddd', icon: $r("app.media.icon") }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        .optionWidth(200)
        .optionHeight(300)
        // divider传null，隐藏选项之间的分割线
        .divider(null)
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        .avoidance(AvoidanceMode.COVER_TARGET);
    }.width('100%')
  }
}
```

从API version 20开始，该示例通过[textModifier](#textmodifier20)和[arrowModifier](arkts-arkui-select-attribute.md#arrowmodifier)属性设置文本以及箭头样式。

```TypeScript
import { TextModifier, SymbolGlyphModifier } from "@kit.ArkUI";

/**
 * 使用TextModifier统一控制选择框展示文本样式
 * 使用SymbolGlyphModifier自定义右侧下拉箭头图标尺寸、颜色
 */
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTTTTTTT".repeat(3);
  @State index: number = 2;
  textModifier: TextModifier = new TextModifier();
  symbolGlyphModifier: SymbolGlyphModifier = new SymbolGlyphModifier();

  aboutToAppear(): void {
    // 初始化主文本全局样式
    this.textModifier
      .maxLines(2)
      .fontSize(18)
      .textAlign(TextAlign.Center)
      .fontColor('#333333')
      .fontWeight(FontWeight.Medium)
      .textOverflow({overflow:TextOverflow.Clip})

    // 初始化下拉箭头图标样式
    this.symbolGlyphModifier
      .fontSize(25)
      .fontColor(['#999999'])
  }

  build() {
    Column() {
      Select([
        // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
        { value: 'A very long option text that should be truncated nicely'.repeat(3), icon: $r("app.media.startIcon") },
        { value: 'Option B', icon: $r("app.media.startIcon") },
        { value: 'Option C', icon: $r("app.media.startIcon") },
        { value: 'Option D', icon: $r("app.media.startIcon") }
      ])
        .selected(this.index)
        .value(this.text)
        // 绑定自定义文本修饰器，统一控制文字样式
        .textModifier(this.textModifier)
        // 绑定修饰器自定义下拉箭头
        .arrowModifier(this.symbolGlyphModifier)
        .onSelect((index: number, text?: string) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        .margin({ top: 20,left:30 })
        .borderRadius(12)
        .width(200)
        .padding(9)
        .backgroundColor(Color.White)
        .shadow({ radius: 10, color: '#888888', offsetX: 0, offsetY: 10 })
    }
    .alignItems(HorizontalAlign.Start)
    .padding(10)
    .backgroundColor('#F0F2F5')
    .width('100%')
    .height('100%')
  }
}
```

从API version 20开始，该示例通过[optionTextModifier](arkts-arkui-select-attribute.md#optiontextmodifier)和[selectedOptionTextModifier](arkts-arkui-select-attribute.md#selectedoptiontextmodifier)属性设置下拉菜单选中和非选中项文本样式。

```TypeScript
import { TextModifier } from "@kit.ArkUI";

/**
 * 通过两个独立TextModifier分别控制下拉面板【普通选项文字】和【已选中选项文字】样式
 */
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTTTTTTT".repeat(3);
  @State index: number = 2;
  optionTextModifier: TextModifier = new TextModifier();
  selectedOptionTextModifier: TextModifier = new TextModifier();
  aboutToAppear(): void {
    // 初始化普通下拉选项文字样式
    this.optionTextModifier
      .maxLines(1)
      .fontSize(16)
      .textAlign(TextAlign.Start)
      .fontColor('#666666')
      .fontWeight(FontWeight.Normal)
      .width(200)

    // 初始化已选中下拉选项文字样式（高亮区分）
    this.selectedOptionTextModifier
      .maxLines(1)
      .fontSize(18)
      .textAlign(TextAlign.Start)
      .fontColor('#007BFF')
      .fontWeight(FontWeight.Bold)
      .width(200)
  }

  build() {
    Column() {
      Select([
        // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
        { value: 'A very long option text that should be truncated nicely'.repeat(3), icon: $r("app.media.startIcon") },
        { value: 'Option B', icon: $r("app.media.startIcon") },
        { value: 'Option C', icon: $r("app.media.startIcon") },
        { value: 'Option D', icon: $r("app.media.startIcon") }
      ])
        .selected(this.index)
        .value(this.text)
        .onSelect((index: number, text?: string) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
        // 绑定普通选项文字修饰器
        .optionTextModifier(this.optionTextModifier)
        // 绑定选中选项文字修饰器，实现选中高亮差异化样式
        .selectedOptionTextModifier(this.selectedOptionTextModifier)
        .margin({ top: 20,left:30 })
        .borderRadius(12)
        .width(200)
        .padding(9)
        .backgroundColor(Color.White)
        .shadow({ radius: 10, color: '#888888', offsetX: 0, offsetY: 10 })
    }
    .alignItems(HorizontalAlign.Start)
    .padding(10)
    .backgroundColor('#F0F2F5')
    .width('100%')
    .height('100%')
  }
}
```

从API version 19开始，该示例通过配置[DividerStyleOptions](ts-types.md#dividerstyleoptions12)的mode属性设置分割线模式。

```TypeScript
import { LengthMetrics } from '@kit.ArkUI'

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Select([{ value: "SelectItem" }, { value: "SelectItem" }, { value: "SelectItem" },])
        .value("请选择")
        /**
         * 自定义下拉选项分割线完整样式
         * strokeWidth：分割线粗细，使用vp单位统一适配不同屏幕
         * color：分割线浅灰色
         * mode: EMBEDDED_IN_MENU 嵌入式模式
         */
        .dividerStyle({
          strokeWidth: LengthMetrics.vp(5),
          color: '#d5d5d5',
          mode: DividerMode.EMBEDDED_IN_MENU
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

从API version 20开始该示例通过配置menuOutline的width和color属性设置下拉菜单外描边样式。

```TypeScript
// xxx.ets
@Entry
@Component
struct SelectExample {
  @State text: string = "TTTTT";
  @State index: number = -1;
  @State arrowPosition: ArrowPosition = ArrowPosition.END;

  build() {
    Column() {
      Select([{ value: 'aaa' },
        { value: 'bbb' },
        { value: 'ccc' },
        { value: 'ddd' }])
        .selected(this.index)
        .value(this.text)
        .font({ size: 16, weight: 500 })
        .fontColor('#182431')
        .selectedOptionFont({ size: 16, weight: 400 })
        .optionFont({ size: 16, weight: 400 })
        .arrowPosition(this.arrowPosition)
        .menuAlign(MenuAlignType.START, { dx: 0, dy: 0 })
        .optionWidth(200)
        .optionHeight(300)
        /**
         * 下拉菜单外描边样式配置
         * width：边框粗细5vp
         * color：边框颜色蓝色
         */
        .menuOutline({
          width: '5vp',
          color: Color.Blue
        })
        .onSelect((index: number, text?: string | undefined) => {
          console.info('Select:' + index);
          this.index = index;
          if (text) {
            this.text = text;
          }
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F0F2F5')
  }
}
```

从API version 23开始，新增keyboardAvoidMode、minKeyboardAvoidDistance接口。

```TypeScript
import { inputMethod } from '@kit.IMEKit';
import { LengthMetrics } from '@kit.ArkUI';

/**
 * Select下拉组件 + 输入法自动挂载示例页面
 * 配置弹出菜单键盘避让策略，点击下拉框延迟2秒主动挂载输入法
 */
@Entry
@Component
struct Index {
  private inputController: inputMethod.InputMethodController | null = null;
  onPageShow(): void {
    try {
      this.inputController = inputMethod.getController();
    } catch (err) {
      console.error("get input method controller fail：", JSON.stringify(err));
    }
  }

  build() {
    RelativeContainer() {
      Select([{ value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' }])
        .value('Click Show Options')
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center },
        })
        // 软键盘弹出避让模式：平移+缩放下拉弹窗，避免被键盘遮挡
        .keyboardAvoidMode(MenuKeyboardAvoidMode.TRANSLATE_AND_RESIZE)
        // 弹窗与软键盘最小预留间距20vp
        .minKeyboardAvoidDistance(LengthMetrics.vp(20))
        .onClick(() => {
          setTimeout(() => {
            this.attachAndListener()
          }, 2000)
        })
    }
    .height('100%')
    .width('100%')
  }

  /**
   * 挂载输入法监听，异步方法
   * 1. 主动给页面Index标识设置焦点
   * 2. 校验输入法控制器实例有效性
   * 3. 挂载输入法，配置文本输入类型、搜索回车按键
   */
  async attachAndListener() {
    focusControl.requestFocus('Index')
    if (!this.inputController) {
      console.error('inputController instance is null!');
      return;
    }
    try {
      await this.inputController.attach(true, {
        inputAttribute: {
          textInputType: inputMethod.TextInputType.TEXT, // 普通文本输入类型
          enterKeyType: inputMethod.EnterKeyType.SEARCH // 回车键显示搜索文案
        }
      })
    } catch (err) {
      console.error('Fail to attach')
    }
  }
}
```

从API版本26.0.0开始，新增menuSystemMaterial接口。

```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Select([{ value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' }])
        .value('Click Show Options')
        /**
         * 配置选择框自身沉浸式磨砂材质
         * ULTRA_THIN：超薄通透磨砂，透明度高，底层画面透出更明显
         */
        .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN
          }))
        /**
         * 配置下拉弹出面板的沉浸式磨砂材质
         * THICK：厚重磨砂，透明度更低，遮挡感更强
         */
        .menuSystemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.THICK
          }))
    }
    // $r('app.media.img')需要替换为开发者所需的图像资源文件。
    .backgroundImage($r('app.media.img'))
  }
}
```
