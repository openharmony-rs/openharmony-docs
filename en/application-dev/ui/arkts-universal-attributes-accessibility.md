# Supporting Accessibility
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Accessibility service is a set of solutions aimed at providing seamless access to all scenarios. The screen reader can convert the UI elements and content of an application into voice output, helping visually impaired users access application information and navigate the UI smoothly.

ArkUI provides comprehensive accessibility capabilities, enabling you to create accessible application UIs that meet the needs of users with visual, auditory, motor, and cognitive impairments.

When the [accessibility attributes](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md) of a component change, it triggers the screen reader to re-read component information, accessibility service to rescan the component tree, state announcements, and dynamic updates of virtual nodes. These mechanisms ensure that assistive tools can promptly perceive and adapt to changes, providing a consistent user experience.

## Available Capabilities

- All user interaction scenarios are covered, such as button tapping, text browsing, chart interaction, and dynamic content update.

- This service is applicable to phones, tablets, and wearables.

## Highlights

  1. Wider user coverage: Applications with assistive tools can accurately reach millions of visually impaired users who rely on assistive technologies, breaking down digital barriers and making products accessible to more users.
  2. Compliance with regulations and design standards: Adapting to assistive tools is a core measure to comply with global accessibility design standards. It not only meets the digital inclusion regulations of various countries/regions, but also aligns with the modern product design concept of "accessible to all."
  3. Social responsibilities fulfillment and brand value enhancement: Adapting to assistive tools is a concrete action to promote digital equity, demonstrate the brand's responsibility to respect all users and help build an accessibility environment, and improve brand awareness.
  4. Optimized user experience: The core optimizations during the adaptation process (such as clear element description, reasonable focus order, and compliant contrast ratio) not only serve users with disabilities, but also provide a smoother user experience for regular users in complex scenarios (such as strong light environments and one-hand operations).
  5. Lightweight adaptation without affecting core experience: Adapting to assistive tools does not require any changes to the core logic or UI design of the application. Only lightweight features are added to the ArkUI accessibility service, ensuring that the innovative characteristics and visual style of the product are fully retained while providing accessibility support.

## Assistive tools

Assistive tools allow users with visual impairments to operate devices without looking at the screen. Based on the accessibility properties set by you, the enabled assistive tool can broadcast the details of the accessibility component through audio, including the component type, text content, operation result, and current status.

Accessibility information can be correctly set for all interactive UI components, which is the prerequisite for an assistive tool to have the accessibility capability. The following three conditions must be met:

  1. The component can be identified by the accessibility service, which can be set by [accessibilityLevel](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel).
  2. The component feature and operation information are provided (implemented by using the [accessibilityText](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitytext) and [accessibilityDescription](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitydescription) attributes).
  3. The actual status and behavior of the component can be transferred (implemented by using the [accessibilityChecked](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitychecked13), and [accessibilityRole](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityrole18) attributes).

<!--RP1--><!--RP1End-->

## Setting Accessibility Groups

The [accessibilityGroup](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitygroup) attribute is used to set whether to enable accessibility groups. If this feature is enabled, the component and all its child components are treated as a whole, and accessibility services no longer process child components individually. The **accessibilityGroup** attribute supports the following values:

- **false** (default): Accessibility grouping is disabled.

- **true**: Accessibility grouping is enabled.

Here is an example using the **Column** component to enable accessibility grouping:

<!-- @[accessibility_group_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) --> 

``` TypeScript
Column() {
  Text('HelloWorld').fontSize(50).fontWeight(FontWeight.Bold)
}
.accessibilityGroup(true)
```

## Setting the Accessibility Level

The [accessibilityLevel](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel) attribute indicates the accessibility importance of a component, which controls whether the component can be identified by the accessibility service. The following values are supported:

- **"auto"** (default): The component's recognizability is determined by the accessibility grouping service and ArkUI.

- **"yes"**: The component can be recognized by accessibility services.

- **"no"**: The component cannot be recognized by accessibility services.

- **"no-hide-descendants"**: Neither the component nor its child components can be recognized by accessibility services.

Here is an example using the **Column** component to set its accessibility level to **"yes"**:

<!-- @[accessibility_level_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
Column() {
  Text('HelloWorld').fontSize(50).fontWeight(FontWeight.Bold)
}
.accessibilityGroup(true)
  .accessibilityLevel('yes')
```

## Setting the Accessibility Text

The [accessibilityText](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitytext) attribute is used to provide text to be read for components without text content and provide information for visual-only elements in accessibility scenarios. It is recommended that the text be concise and convey the key information of the component. For example, the description "play" can be provided for a play button without text. If the component already has text content and the **accessibilityText** attribute is also set, only the content set by **accessibilityText** is read.

**accessibilityText** is mainly used to briefly describe the feature of a component, rather than specific operations or prompt messages. You are not advised to set lengthy information in **accessibilityText**, such as operation guidance like "Double-tap with one finger to play" or status information like "This feature is not supported."

This attribute supports strings or resource references.

In this example, the accessibility text of the play icon is set to "play".

<!-- @[accessibility_text_group_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
Column() {
  Image($r('app.media.play')) // Only an icon is displayed. No default text is provided.
  .width(60)
  .height(60)
  .accessibilityText($r('app.string.UniversalAttributesAccessibility_text12'))
  .onClick(() => {
      // Core logic for playing audio and video.
  })
}
```

## Setting Accessibility Description

The [accessibilityDescription](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitydescription) attribute is used to provide more detailed component description, for example, the reason why the component is currently unavailable, or the meaning that cannot be expressed by the system guide for beginners, helping users understand the operation to be performed and the operation result. After the text content is broadcasted, this accessibility description will be broadcasted. If the current component has a default guide for beginners (for example, for a component that can be tapped, the default content is "double-tap with one finger to execute"), the content of **accessibilityDescription** will be broadcasted instead of the system guide.

In this example, **accessibilityDescription** of the **Button** component is set to **Double-tap with one finger to play**.

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
      // Core logic for playing audio and video.
  })
}
```

## Setting Accessibility Virtual Nodes

The [accessibilityVirtualNode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityvirtualnode11) attribute is used to add virtual accessibility nodes to the custom drawing component. The assistive tool reads the information about these nodes instead of the actual displayed content.

<!-- @[virtual_node_example_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/VirtualNodeExample.ets) -->

``` TypeScript
@Entry
@Component
struct VirtualNodeExample {
  @Builder customAccessibilityNode() {
    // Replace $r('app.string.UniversalAttributesAccessibility_text6') with the actual resource file. In this example, the value in the resource file is "Text 2."
    Text($r('app.string.UniversalAttributesAccessibility_text6'))
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
  build() {
    Column() {
      // Replace $r('app.string.UniversalAttributesAccessibility_text5') with the actual resource file. In this example, the value in the resource file is "Text 1."
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

## Setting Whether an Accessibility Node Is Selected

[accessibilityChecked](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitychecked13) and [accessibilitySelected](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityselected13) are two attributes mainly used to convey the selection status of a component to assistive tools like screen readers, enhancing accessibility experience.

### Setting Selection State for Multi-Select Scenarios

The [accessibilityChecked](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitychecked13) attribute is used to indicate whether a component (for example, two-state or three-state component like check box or toggle button) is checked in multi-select scenarios. It applies to scenarios requiring clear "selected/unselected" semantics and supports the following values:

- **undefined** (default): automatically determined by the system (depending on the component's own state, such as the **isOn** attribute of a **Toggle** component).

- **false**: not selected.

- **true**: selected (for example, check box checked).

Here is an example using the **Column** component to set it as checked when multi-select is supported:

<!-- @[accessibility_checked_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
Column() {
  Text('HelloWorld').fontSize(50).fontWeight(FontWeight.Bold)
}
.accessibilityGroup(true)
  .accessibilityLevel('yes')
  // Replace $r('app.string.UniversalAttributesAccessibility_text7') with the actual resource file. In this example, the value in the resource file is "Group."
  .accessibilityText($r('app.string.UniversalAttributesAccessibility_text7'))
  // Replace $r('app.string.UniversalAttributesAccessibility_text8') with the actual resource file.
     In this example, the value in the resource file is "The Column component can be selected, and the content to be announced is 'Group'." */
  .accessibilityDescription($r('app.string.UniversalAttributesAccessibility_text8'))
  .accessibilityChecked(true)
```

### Setting Selection State for Single-Select Scenarios

The [accessibilitySelected](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityselected13) attribute is used to indicate whether a component (for example, a single-select list or tab) is selected in single-select scenarios. It applies to scenarios requiring differentiation of "current selected items" (for example, single-select groups and navigation menus) and supports the following values:

- **undefined** (default): automatically determined by the system.

- **false**: not selected.

- **true**: currently selected.

Here is an example using the **Column** component to let the system determine its selection state when single-select is supported:

<!-- @[accessibility_selected_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility/entry/src/main/ets/pages/UniversalAttributesAccessibility/AccessibilityText.ets) -->

``` TypeScript
Column() {
  Text('HelloWorld').fontSize(50).fontWeight(FontWeight.Bold)
}
.accessibilityGroup(true)
  .accessibilityLevel('yes')
  // Replace $r('app.string.UniversalAttributesAccessibility_text7') with the actual resource file. In this example, the value in the resource file is "Group."
  .accessibilityText($r('app.string.UniversalAttributesAccessibility_text7'))
  // Replace $r('app.string.UniversalAttributesAccessibility_text8') with the actual resource file.
     In this example, the value in the resource file is "The Column component can be selected, and the content to be announced is 'Group'." */
  .accessibilityDescription($r('app.string.UniversalAttributesAccessibility_text8'))
  .accessibilitySelected(undefined)
```

### Key Differences Between accessibilityChecked and accessibilitySelected

In ArkUI accessibility attributes, both [accessibilityChecked](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitychecked13) and [accessibilitySelected](../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilityselected13) are used to indicate the state of a component, but they have fundamentally different application scenarios and semantic meanings. The following table provides a comparison of these two.

| Attribute   | accessibilityChecked     | accessibilitySelected |
| ------- | ------------------------ | --------------------- |
| Use cases| Binary or ternary components, such as check boxes and toggles.| Mutually exclusive selection scenarios, such as single-select lists and tabs.|
| Semantic objectives| Physical state of components (for example, whether a switch is on).| Navigation focus item (for example, current selected item in a list).|
| State persistence| Usually requires explicit saving (such as form submission).| Temporary (changes with focus movement).|
| Typical components| **Checkbox** and **Toggle**.        | **List** and **Tabs**.       |

## Recommendations

- Priority control

  Use **accessibilityLevel** to ensure key operations are recognizable.

- Semantic descriptions

  Add **accessibilityText** and **accessibilityDescription** for non-text elements like icons and images.

- Grouping optimization

  Use **accessibilityGroup** to reduce redundant announcements for complex layouts.

## Scenario Example

This example demonstrates how to use **accessibilityText** and **accessibilityDescription** to customize the content announced by screen readers.

If a component has both text and accessibility text attributes, only the accessibility text is announced when the component is selected.

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
          // Replace $r('app.string.UniversalAttributesAccessibility_text5') with the actual resource file. In this example, the value in the resource file is "Text 1."
          Text($r('app.string.UniversalAttributesAccessibility_text5'))
            .fontSize(50)
            .fontWeight(FontWeight.Bold)
          // Replace $r('app.string.UniversalAttributesAccessibility_text6') with the actual resource file. In this example, the value in the resource file is "Text 2."
          Text($r('app.string.UniversalAttributesAccessibility_text6'))
            .fontSize(50)
            .fontWeight(FontWeight.Bold)
        }
        .width('100%')
          .accessibilityGroup(true)
          .accessibilityLevel('yes')
          // Replace $r('app.string.UniversalAttributesAccessibility_text7') with the actual resource file. In this example, the value in the resource file is "Group."
          .accessibilityText($r('app.string.UniversalAttributesAccessibility_text7'))
          // Replace $r('app.string.UniversalAttributesAccessibility_text8') with the actual resource file.
             In this example, the value in the resource file is "The Column component can be selected, and the content to be announced is 'Group'." */
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

![en-us_image_0000001745415556](figures/en-us_image_0000001745415556.jpg)
