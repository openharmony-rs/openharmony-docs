# 支持无障碍
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

无障碍服务是一套以“全场景无障碍访问”为核心目标的解决方案。其中屏幕朗读功能可通过语音反馈将应用界面元素与内容转化为语音输出，助力视觉障碍用户顺畅访问应用信息、导航界面等。

ArkUI提供了丰富的无障碍能力，使开发者能够创建可访问的应用界面，满足视觉、听觉、运动和认知障碍等用户的需求。

组件的[无障碍属性](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md)变化时，会触发辅助工具重新读取组件信息、无障碍服务重新扫描组件树、状态播报、虚拟节点动态更新，这些机制确保辅助工具能及时感知并适配变化，为用户提供连贯的体验。

## 能力范围

- 覆盖所有用户交互场景（如按钮点击、文本浏览、图表交互、动态内容更新）。

- 适用于Phone、Tablet、Wearable设备。

## 亮点特征

  1. 拓宽用户覆盖边界：适配辅助工具的应用，能精准触达数百万依赖辅助技术的视觉障碍用户，打破数字适用壁垒，让产品受众覆盖更全面。
  2. 契合合规与设计规范：适配辅助工具是遵循全球无障碍设计标准的核心举措，既符合各国数字包容相关法规要求，也契合现代产品“人人可用”的设计理念。
  3. 践行社会责任与品牌价值：适配辅助工具本质是促进数字公平的具体行动，彰显品牌尊重所有用户、助力无障碍环境建设的责任担当，提升品牌好感度。
  4. 优化全用户群体体验：适配过程中的核心优化（如清晰地元素描述、合理地焦点顺序、达标对比度），不仅服务障碍用户，也能让普通用户在复杂场景（如强光环境、单手操作）下获得更流畅的使用体验。
  5. 轻量级适配不影响核心体验：适配辅助工具无需改动应用核心逻辑或UI设计，ArkUI的无障碍属性仅添加轻量级功能，在实现无障碍支持的同时，完全保留产品的创新特点与视觉风格。

## 无障碍辅助工具

辅助工具的支持让视觉障碍用户无需查看屏幕即可操作设备。基于开发者设置的无障碍属性，辅助工具启用后，可以通过音频播报组件详情，包括组件类型、文本内容、操作结果及当前状态。

一个辅助工具具备无障碍能力的前提：所有可交互UI组件均能正确设置无障碍信息，即需要满足以下三点。

  1. 可被无障碍服务识别，即支持通过[accessibilityLevel](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel)设置某个组件是否可被无障碍辅助服务所识别。
  2. 提供组件功能及操作信息（通过[accessibilityText](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitytext)、[accessibilityDescription](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitydescription)属性实现）。
  3. 支持传递组件实际状态与行为（通过[accessibilityChecked](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitychecked13)、[accessibilityRole](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityrole18)属性实现）。

<!--RP1--><!--RP1End-->

## 设置无障碍分组

[accessibilityGroup](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitygroup)属性，用于设置是否启用无障碍分组。若启用，则该组件及其所有子组件将作为一个整体处理，无障碍服务不再单独处理各子组件。accessibilityGroup属性支持以下值：

- false（默认）：不启用无障碍分组。

- true：启用无障碍分组。

这里以Column组件为例，启用无障碍分组：

<!-- @[accessibility_group_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) --> 

``` TypeScript
Column() {
  Text('HelloWorld').fontSize(50).fontWeight(FontWeight.Bold)
}
.accessibilityGroup(true)
```

## 设置无障碍重要性

[accessibilityLevel](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel)属性表示组件的无障碍重要性，用于控制组件是否能被无障碍服务识别，支持以下值：

- "auto"（默认）：当前组件由无障碍分组服务和ArkUI进行综合判断组件是否可被无障碍辅助服务所识别。

- "yes"：当前组件可被无障碍辅助服务所识别。

- "no"：当前组件不可被无障碍辅助服务所识别。

- "no-hide-descendants"：当前组件及其所有子组件均不可被无障碍辅助服务所识别。

这里以Column组件为例，设置其无障碍重要性为可被无障碍辅助服务所识别：

<!-- @[accessibility_level_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
Column() {
  Text('HelloWorld').fontSize(50).fontWeight(FontWeight.Bold)
}
.accessibilityGroup(true)
  .accessibilityLevel('yes')
```

## 设置无障碍文本

[accessibilityText](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitytext)属性用于为无文本内容的组件提供朗读文本，为纯视觉元素提供无障碍场景下的信息。建议设置的文本内容简洁达意，传递本组件的关键信息。例如为无文本的播放按钮提供“播放”功能描述。如果组件已有文本内容，同时又设置了accessibilityText属性，此时仅播报accessibilityText的内容。

accessibilityText主要用于组件的功能简述，而不是具体的操作和提示信息。不建议在accessibilityText中添加冗长的信息，例如添加“单指双击即可播放”这种操作引导、“当前场景不支持”等状态信息。

accessibilityText支持字符串或资源引用。

本示例以播放图标为例，设置其无障碍文本为“播放”。

<!-- @[accessibility_text_group_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
Column() {
  Image($r('app.media.play')) // 仅图标，无默认文本
  .width(60)
  .height(60)
  .accessibilityText($r('app.string.UniversalAttributesAccessibility_text12'))
  .onClick(() => {
      // 播放音频、视频的核心逻辑
  })
}
```

## 设置无障碍说明

[accessibilityDescription](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitydescription)属性用于提供更详细的组件说明，帮助用户理解将要执行的操作及结果。例如组件状态当前不可使用的原因，系统默认的新手提醒不能表达的含义等场景。文本内容播报完成之后，会播报该信息。如果当前控件有默认的新手提醒（如支持点击的组件，默认新手提醒为：单指双击即可执行），accessibilityDescription会替代系统的新手提醒，即仅播报accessibilityDescription的内容。

本示例以Button组件的播放场景为例，设置其无障碍说明为“单指双击即可播放”。

<!-- @[accessibility_description_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
Column() {
  Button()
  .width(120)
  .height(40)
  .accessibilityLevel('yes')
  .accessibilityText($r('app.string.UniversalAttributesAccessibility_text12'))
  .accessibilityDescription($r('app.string.UniversalAttributesAccessibility_text13'))
  .onClick(() => {
      // 播放音频、视频的核心逻辑
  })
}
```

## 设置无障碍虚拟子节点

[accessibilityVirtualNode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityvirtualnode11)属性，用于为自绘制组件添加虚拟无障碍节点，辅助工具会读取这些节点的信息而非实际显示内容。

<!-- @[virtual_node_example_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/VirtualNodeExample.ets) -->

``` TypeScript
@Entry
@Component
struct VirtualNodeExample {
  @Builder customAccessibilityNode() {
    // 请将$r('app.string.UniversalAttributesAccessibility_text6')替换为实际资源文件，在本示例中该资源文件的value值为"文本2"
    Text($r('app.string.UniversalAttributesAccessibility_text6'))
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
  build() {
    Column() {
      // 请将$r('app.string.UniversalAttributesAccessibility_text5')替换为实际资源文件，在本示例中该资源文件的value值为"文本1"
      Text($r('app.string.UniversalAttributesAccessibility_text5'))
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
    .accessibilityGroup(true)
    .accessibilityLevel('yes')
    .accessibilityVirtualNode(this.customAccessibilityNode)
  }
}
```

## 设置无障碍节点是否被选中

[accessibilityChecked](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitychecked13)和[accessibilitySelected](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityselected13)是两个用于增强无障碍体验的属性，主要用于向屏幕朗读等辅助工具传达组件的选中状态。

### 在支持多选的情况下，设置无障碍节点是否被选中

[accessibilityChecked](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitychecked13)属性，用于表示组件在支持多选的情况下是否被勾选（如复选框、开关按钮等二态或三态组件），适用于需要明确“选中/未选中”语义的场景，支持以下值：

- undefined（默认）：由系统自动判断（依赖组件自身的状态，如Toggle组件的isOn属性）。

- false：未选中。

- true：选中（如复选框打勾）。

这里以Column组件为例，设置其在支持多选的情况下被选中：

<!-- @[accessibility_checked_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
Column() {
  Text('HelloWorld').fontSize(50).fontWeight(FontWeight.Bold)
}
.accessibilityGroup(true)
  .accessibilityLevel('yes')
  // 请将$r('app.string.UniversalAttributesAccessibility_text7')替换为实际资源文件，在本示例中该资源文件的value值为"分组"
  .accessibilityText($r('app.string.UniversalAttributesAccessibility_text7'))
  /* 请将$r('app.string.UniversalAttributesAccessibility_text8')替换为实际资源文件，
     在本示例中该资源文件的value值为"Column组件可以被选中，播报的内容是“分组”" */
  .accessibilityDescription($r('app.string.UniversalAttributesAccessibility_text8'))
  .accessibilityChecked(true)
```

### 在支持单选的情况下，设置无障碍节点是否被选中

[accessibilitySelected](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityselected13)属性，用于表示组件在支持单选的情况下是否被选择（如单选列表项、标签页等），适用于需要区分“当前选中项”的场景（如单选组、导航菜单），支持以下值：

- undefined（默认）：由系统自动判断。

- false：未选中。

- true：当前选中。

这里以Column组件为例，设置在支持单选的情况下由系统自行确定其选中状态：

<!-- @[accessibility_selected_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
Column() {
  Text('HelloWorld').fontSize(50).fontWeight(FontWeight.Bold)
}
.accessibilityGroup(true)
  .accessibilityLevel('yes')
  // 请将$r('app.string.UniversalAttributesAccessibility_text7')替换为实际资源文件，在本示例中该资源文件的value值为"分组"
  .accessibilityText($r('app.string.UniversalAttributesAccessibility_text7'))
  /* 请将$r('app.string.UniversalAttributesAccessibility_text8')替换为实际资源文件，
     在本示例中该资源文件的value值为"Column组件可以被选中，播报的内容是“分组”" */
  .accessibilityDescription($r('app.string.UniversalAttributesAccessibility_text8'))
  .accessibilitySelected(undefined)
```

### accessibilityChecked属性与accessibilitySelected属性的关键区别

在ArkUI无障碍属性中，[accessibilityChecked](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitychecked13)和[accessibilitySelected](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityselected13)均用于表示组件的状态，但二者应用场景与语义含义存在本质差异。以下是二者的对比：

| 属性    | accessibilityChecked     | accessibilitySelected |
| ------- | ------------------------ | --------------------- |
| 常见场景 | 复选框、开关等二态/三态组件。 | 单选列表、标签页等互斥选择场景。 |
| 语义目标 | 控件物理状态（如开关是否打开）。 | 导航焦点项（如列表当前选中项）。 |
| 状态持久性 | 通常需显式保存（如表单提交）。 | 临时性（随焦点移动变化）。 |
| 典型组件 | Checkbox，Toggle。         | List，Tabs。        |

## 使用建议

- 优先级控制

  通过accessibilityLevel确保关键操作可被识别。

- 语义化描述

  为图标、图片等非文本元素添加accessibilityText和accessibilityDescription。

- 分组优化

  对复杂布局使用accessibilityGroup减少冗余播报。

## 场景示例

该示例主要演示accessibilityText无障碍文本和accessibilityDescription无障碍说明的播报内容。

其中，对于该组件的无障碍文本的内容，在既拥有文本属性又拥有无障碍文本属性的情况下，当组件被选中时，仅播报无障碍文本内容。

<!-- @[accessibility_text_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
@Component
export struct AccessibilityText {
  @Builder
  customAccessibilityNode() {
    Column() {
      Text(`virtual node`)
    }
    .width(10)
      .height(10)
  }

  build() {
    // ...
      Row() {
        // ...
        Column() {
          // 请将$r('app.string.UniversalAttributesAccessibility_text5')替换为实际资源文件，在本示例中该资源文件的value值为"文本1"
          Text($r('app.string.UniversalAttributesAccessibility_text5'))
            .fontSize(50)
            .fontWeight(FontWeight.Bold)
          // 请将$r('app.string.UniversalAttributesAccessibility_text6')替换为实际资源文件，在本示例中该资源文件的value值为"文本2"
          Text($r('app.string.UniversalAttributesAccessibility_text6'))
            .fontSize(50)
            .fontWeight(FontWeight.Bold)
        }
        .width('100%')
          .accessibilityGroup(true)
          .accessibilityLevel('yes')
          // 请将$r('app.string.UniversalAttributesAccessibility_text7')替换为实际资源文件，在本示例中该资源文件的value值为"分组"
          .accessibilityText($r('app.string.UniversalAttributesAccessibility_text7'))
          /* 请将$r('app.string.UniversalAttributesAccessibility_text8')替换为实际资源文件，
             在本示例中该资源文件的value值为"Column组件可以被选中，播报的内容是“分组”" */
          .accessibilityDescription($r('app.string.UniversalAttributesAccessibility_text8'))
          .accessibilityVirtualNode(this.customAccessibilityNode)
          .accessibilityChecked(true)
          .accessibilitySelected(undefined)
      }
      .height('100%')
      // ...
  }
}
```

![zh-cn_image_0000001745415556](figures/zh-cn_image_0000001745415556.jpg)
