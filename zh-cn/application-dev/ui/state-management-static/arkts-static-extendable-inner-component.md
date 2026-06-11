# 内置组件扩展
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

开发者可以使用现有的内置组件实现预期的UI效果，但无法在其之上进行扩展，无法添加自定义的行为。当存在多处均需要相同属性的内置组件时，开发者只能编写类似代码，无法实现代码复用。从API版本26.0.0开始，内置组件扩展支持开发者重写已有属性和新增自定义属性。

> **说明：**
>
> 在ArkTS-Sta上下文中，从API版本26.0.0开始，支持内置组件扩展，具体范围详见[支持扩展的内置组件](#支持扩展的内置组件)。

在静态语言上下文中使用时，需要导入内置组件扩展类，以ExtendableButton为例，导入方式如下：

```ts
import { ExtendableButton } from '@kit.ArkUI';
```

## 创建自定义内置组件扩展类

开发者可以按需创建内置组件扩展类，并在其中重写现有的属性和新增自定义属性。以Text为例，创建内置组件扩展类MyText继承ExtendableText，在该类中重写了Text中的属性`fontSize`以及通用属性`width`，同时新增了自定义属性`newAttribute`。重写属性和新增属性中均可以添加自定义行为。

内置组件扩展类MyText中可以按需重写Text中的属性和通用属性，若属性未重写，在扩展组件调用时则遵循该属性的默认行为。

```ts
'use static'

import { ExtendableText } from '@kit.ArkUI';

class MyText extends ExtendableText {
  // Text中的属性
  fontSize(): this {
    super.fontSize(30);
    return this;
  }

  // 通用属性
  width(): this {
    super.width('100%');
    return this;
  }

  // 自定义属性
  newAttribute(): this {
    super.height('50%');
    super.width('50%');
    return this;
  }
}
```

## 内置组件扩展类的使用

开发者自定义的扩展组件与对应的内置组件使用方式基本一致，包括调用位置、可包含的子组件等。

如下示例中，创建MyText扩展组件，并调用fontSize、height、width属性，其中height属性未被重写，则遵循默认规格。

<!-- @[extendable_text_usage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ExtendableInnerComponent/entry/src/main/ets/pages/ExtendableTextUsage.ets) -->

``` TypeScript
import { ExtendableText, TextOptions, Length, Entry, Component, Text, Column } from '@kit.ArkUI';

class MyText extends ExtendableText {
  // Text中的属性
  fontSize(): this {
    super.fontSize(30);
    return this;
  }

  // 通用属性
  width(): this {
    super.width('100%');
    return this;
  }
}

@Entry
@Component
struct ExtendableTextUsageExample {
  build() {
    Column() {
      MyText('Hello World')
        .fontSize()
        .height('30%')
        .width()
    }
  }
}
```

## 内置组件扩展类的模板化使用

开发者可以在自定义的内置组件扩展类中定义模板化的属性设置，如下示例中，在MyText中定义了newAttribute属性和fixedNewAttribute属性。其中newAttribute可以接收参数，批量设置属性，实现可变属性样式的模板组件。fixedNewAttribute可以批量设置相同属性，实现固定样式的模板组件。

<!-- @[extendable_text_template](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ExtendableInnerComponent/entry/src/main/ets/pages/ExtendableTextTemplate.ets) -->

``` TypeScript
import { ExtendableText, TextOptions, Length, Entry, Component, Text, Column } from '@kit.ArkUI';

class MyText extends ExtendableText {
  // 可变属性样式
  newAttribute(fontSize: double, height: Length, width: Length): this {
    // 批量设置属性
    super.fontSize(fontSize);
    super.height(height);
    super.width(width);
    return this;
  }

  // 固定属性样式
  fixedNewAttribute(): this {
    // 批量设置属性
    super.fontSize(50);
    super.height('20%');
    super.width('100%');
    return this;
  }
}

@Entry
@Component
struct ExtendableTextTemplateExample {
  build() {
    Column() {
      MyText('Hello World')
        .newAttribute(20, '20%', '50%')
      MyText('Hello ArkUI')
        .newAttribute(30, '20%', '75%')
      MyText('Hello Today')
        .fixedNewAttribute()
      MyText('Hello Tomorrow')
        .fixedNewAttribute()
    }
  }
}
```

## 支持扩展的内置组件

| 内置组件                                                     | 扩展内置组件                                                 | 起始版本 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | -------- |
| [Button](../../reference/apis-arkui/arkui-ts/ts-basic-components-button.md) | [ExtendableButton](../../reference/apis-arkui/arkui-ts/ts-basic-components-extendablebutton.md) | 26.0.0   |
| [Column](../../reference/apis-arkui/arkui-ts/ts-container-column.md) | [ExtendableColumn](../../reference/apis-arkui/arkui-ts/ts-container-extendablecolumn.md) | 26.0.0   |
| [Grid](../../reference/apis-arkui/arkui-ts/ts-container-grid.md) | [ExtendableGrid](../../reference/apis-arkui/arkui-ts/ts-container-extendablegrid.md) | 26.0.0   |
| [GridItem](../../reference/apis-arkui/arkui-ts/ts-container-griditem.md) | [ExtendableGridItem](../../reference/apis-arkui/arkui-ts/ts-container-extendablegriditem.md) | 26.0.0   |
| [Image](../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md) | [ExtendableImage](../../reference/apis-arkui/arkui-ts/ts-basic-components-extendableimage.md) | 26.0.0   |
| [List](../../reference/apis-arkui/arkui-ts/ts-container-list.md) | [ExtendableList](../../reference/apis-arkui/arkui-ts/ts-container-extendablelist.md) | 26.0.0   |
| [ListItem](../../reference/apis-arkui/arkui-ts/ts-container-listitem.md) | [ExtendableListItem](../../reference/apis-arkui/arkui-ts/ts-container-extendablelistitem.md) | 26.0.0   |
| [RelativeContainer](../../reference/apis-arkui/arkui-ts/ts-container-relativecontainer.md) | [ExtendableRelativeContainer](../../reference/apis-arkui/arkui-ts/ts-container-extendablerelativecontainer.md) | 26.0.0   |
| [Row](../../reference/apis-arkui/arkui-ts/ts-container-row.md) | [ExtendableRow](../../reference/apis-arkui/arkui-ts/ts-container-extendablerow.md) | 26.0.0   |
| [Stack](../../reference/apis-arkui/arkui-ts/ts-container-stack.md) | [ExtendableStack](../../reference/apis-arkui/arkui-ts/ts-container-extendablestack.md) | 26.0.0   |
| [Text](../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md) | [ExtendableText](../../reference/apis-arkui/arkui-ts/ts-basic-components-extendabletext.md) | 26.0.0   |
| [Toggle](../../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md) | [ExtendableToggle](../../reference/apis-arkui/arkui-ts/ts-basic-components-extendabletoggle.md) | 26.0.0   |

