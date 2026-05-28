# Custom Extension Capability Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

The ArkUI framework offers a range of custom extension capabilities that enable the enhancement and customization of UI components in a way that is decoupled from the UI. With these capabilities, known as modifiers, you can quickly adjust the appearance and behavior of UI components without changing the underlying implementation of UI components. The available modifiers include [AttributeModifier](arkts-user-defined-extension-attributeModifier.md), [GestureModifier](../reference/apis-arkui/arkui-ts/ts-universal-attributes-gesture-modifier.md#gesturemodifier-1), and [ContentModifier](arkts-common-attributes-content-modifier.md). Among them, [AttributeModifier](arkts-user-defined-extension-attributeModifier.md) and [AttributeUpdater](arkts-user-defined-extension-attributeUpdater.md) specifically enable attribute configuration through custom classes. This expands the implementation methods for attribute settings and supports combination with the standard component attribute setting methods. For example, you can use custom extensions to handle specific logic or complex interactions, while using the standard component setting method to manage simple static attributes. 

## AttributeModifier
Although [@Styles](../ui/state-management/arkts-style.md) and [@Extend](../ui/state-management/arkts-extend.md) introduced by the declarative syntax enable reuse of custom styles, they have limitations such as inability to be exported across files. To address the above issues, ArkUI introduces the **AttributeModifier** mechanism, which allows dynamic modification of attributes through a **Modifier** object. When compared to @Styles and @Extend, **AttributeModifier** provides superior capabilities and flexibility. As it continues to evolve to encompass a full spectrum of attribute and event settings, **AttributeModifier** is the preferred choice for implementation.

## AttributeUpdater
As a special type of **AttributeModifier**, **AttributeUpdater** not only inherits all the functionality of **AttributeModifier** but also extends its capabilities by allowing access to the attribute object. By using the attribute object, you can update specific attributes without relying on state variables. With **AttributeUpdater**, you can implement custom update strategies, further improving the performance of attribute updates.

## ContentModifier

**ContentModifier** provides the capability to customize the content area of a component. This function can be used when you want to customize the content area of a component, for example, displaying a five-pointed star inside a [Checkbox](../reference/apis-arkui/arkui-ts/ts-basic-components-checkbox.md) component.
