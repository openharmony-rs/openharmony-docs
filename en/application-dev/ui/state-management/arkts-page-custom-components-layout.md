# Custom Component Layout
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @song-song-song-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

If the layout components (such as [Flex](../../reference/apis-arkui/arkui-ts/ts-container-flex.md), [Column](../../reference/apis-arkui/arkui-ts/ts-container-column.md) and [Row](../../reference/apis-arkui/arkui-ts/ts-container-row.md)) provided by the system cannot meet complex layout requirements, or you want to customize the size and position of child components in a component, you are advised to use the following APIs in custom components:

- [onMeasureSize](../../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#onmeasuresize10): This callback is triggered each time the component is laid out. You can add the logic for calculating the size of child components in the custom component to this callback and return the size information of the custom component. The execution time of this callback is earlier than that of onPlaceChildren.

- [onPlaceChildren](../../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#onplacechildren10): This callback is triggered each time the component is laid out. You can add the logic for placing child components in the custom component to this callback.

In the following example, the Index page contains a custom component that implements a custom layout, and the child components of the custom component are passed through the builder mode on the Index page.

**onMeasureSize** and **onPlaceChildren** are called in the custom component to set the size and position of its child components. In **onMeasureSize**, the initial size is set at 100, and the size of each child component is increased by half of the size of the previous child component, leading to component size increment. In onPlaceChildren, set startPos to 300, and set the position of each child component to startPos minus the height of the child component. The lower right corner of all child components is at the vertex position (300, 300), implementing a Stack component that displays components from the lower right corner.

**Example**

```
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      CustomLayout({ builder: ColumnChildren })
    }
  }
}

// Pass multiple components in a builder as level-1 child components of the custom component (that is, container components for example, <Column>, are not included).
@Builder
function ColumnChildren() {
  ForEach([1, 2, 3], (index: number) => { // LazyForEach is not supported.
    Text('S' + index)
      .fontSize(30)
      .width(100)
      .height(100)
      .borderWidth(2)
      .offset({ x: 10, y: 20 })
  })
}

@Component
struct CustomLayout {
  @Builder
  doNothingBuilder() {
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;
  @State startSize: number = 100;
  result: SizeResult = {
    width: 0,
    height: 0
  };

  // Step 1: Calculate the size of each child component.
  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size = 100;
    children.forEach((child) => {
      let result: MeasureResult = child.measure({ minHeight: size, minWidth: size, maxWidth: size, maxHeight: size })
      size += result.width / 2;
    })
    // this.result represents the custom component's own size.
    this.result.width = 100;
    this.result.height = 400;
    return this.result;
  }
  // Step 2: Place the child components.
  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    let startPos = 300;
    children.forEach((child) => {
      let pos = startPos - child.measureResult.height;
      child.layout({ x: pos, y: pos })
    })
  }

  build() {
    this.builder()
  }
}
```

![custom-component-custom-layout](figures/custom-component-custom-layout.png)
