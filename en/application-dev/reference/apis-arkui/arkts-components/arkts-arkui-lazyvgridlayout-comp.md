# LazyVGridLayout

Implements a grid layout that supports lazy loading.

In versions earlier than API version 26.0.0, the parent component of the **LazyVGridLayout** component supports the WaterFlow and FlowItem components. You can also encapsulate the parent component using a custom component or NodeContainer component and use it in **WaterFlow** or **FlowItem**.

Since API version 26.0.0, the parent component of this component also supports List, Scroll, or [LazyColumnLayout](../../../reference/apis-arkui/arkui-ts/ts-container-lazycolumnlayout.md). Additionally, custom components or NodeContainer components can be encapsulated and then used in **List**, **Scroll**, or **LazyColumnLayout**.

> **NOTE** > > - This component is supported since API version 19. Updates will be marked with a superscript to indicate their > earliest API version. > > - This component's height adapts to content by default. Setting the height, height constraints, or aspect ratio > causes display anomalies. > > - The lazy loading conditions of this component in different parent components are as follows: > > 1. In the **WaterFlow** component, lazy loading is supported only when it uses single-column mode or single- > column segments in segmented layout and [FlexDirection](../arkts-apis/arkts-arkui-flexdirection-e.md) is set to **FlexDirection.Column**. > Lazy loading is not supported if the **WaterFlow** component is in multi-column mode or the layout direction is > **FlexDirection.Row** or **FlexDirection.RowReverse**. Using this component with **FlexDirection.ColumnReverse** in > the **WaterFlow** component causes display anomalies. > > 2. In the **List** component, the layout direction must be vertical (that is, the > [listDirection](arkts-arkui-list-comp-attribute.md#listdirection) property is set to **Axis.Vertical**). Using this component in a > non-vertical **List** component will cause an application crash. If any of the **lanes**, **chainAnimation**, and > **scrollSnapAlign** properties is set for the **List** component, the lazy loading of this component will become > invalid. > > 3. In the **Scroll** component, the layout direction must be vertical (that is, the value of the > scrollable property is **ScrollDirection.Vertical**). Using this component in a > non-vertical **Scroll** component will cause an application crash. > > - When lazy loading is enabled, the component only loads child components within the visible area of the parent > component, with pre-loading of half-screen content above and below the viewport during frame idle periods.

## LazyVGridLayout

```TypeScript
LazyVGridLayout()
```

Creates a vertical lazy-loading grid layout container.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

## Examples

```TypeScript
### Example 1: Implementing a Lazy-Loading Grid Layout

This example uses [WaterFlow](ts-container-waterflow.md) and LazyVGridLayout to implement a lazy loading grid layout, and triggers a callback through [onVisibleIndexesChange](#onvisibleindexeschange) when the visible area changes, returning the start index and end index of the child components in the current visible area.

MyDataSource implements the [IDataSource](ts-rendering-control-lazyforeach.md#idatasource) API for [LazyForEach](ts-rendering-control-lazyforeach.md), which provides child components for LazyVGridLayout through LazyForEach.

The onVisibleIndexesChange event is added since API version 26.0.0.
```

```TypeScript

```

```TypeScript
### Example 2: Setting a Header or Footer Component and Sticky Styles

This example nests LazyVGridLayout inside [WaterFlow](ts-container-waterflow.md), and implements sticky styles at the top and bottom of the grid through [header](#header), [footer](#footer), and [sticky](#sticky). During scrolling, the header sticks to the top of the visible area, and the footer sticks to the bottom of the visible area.

Since API version 26.0.0, the header, footer, and sticky attributes are newly supported.


```

```TypeScript
### Example 3: Setting Adaptive Column Count

This example implements adaptive column count for the LazyVGridLayout component by setting the [columnsTemplate](#columnstemplate) attribute, and uses auto-fill, auto-fit, and auto-stretch in the [columnsTemplate](#columnstemplate) attribute.

Since API version 19, the [columnsTemplate](#columnstemplate) API is newly supported.
```
