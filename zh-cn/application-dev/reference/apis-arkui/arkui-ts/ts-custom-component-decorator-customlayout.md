# @CustomLayout：自定义布局

在ArkTS-Sta中，自定义组件需要加上`@CustomLayout`装饰器，才能获得自定义布局能力。开发指南参考：[自定义组件需要加上`@CustomLayout`装饰器以获得自定义布局能力](../../../ui/arkts-dyn-sta-ui-rules.md#自定义组件需要加上customlayout装饰器以获得自定义布局能力)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 本装饰器首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```ts
'use static'

import {
  CustomLayout,
  Entry,
  Component,
  Column,
  Builder,
  ForEach,
  Text,
  Position,
  BuilderParam,
  State,
  SizeResult,
  GeometryInfo,
  Layoutable,
  ConstraintSizeOptions,
  Measurable,
  MeasureResult
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      MyComponent({ builder: ColumnChildren })
    }
  }
}

@Builder
function ColumnChildren() {
  ForEach([1, 2, 3], (item: int, index: int) => {
    Text('S' + index)
      .fontSize(30)
      .width(100)
      .height(100)
      .borderWidth(2)
      .offset({ x: 10, y: 20 } as Position)
  })
}

@Component
@CustomLayout
struct MyComponent {
  @Builder
  doNothingBuilder() {
  }

  @BuilderParam builder: () => void = this.doNothingBuilder;
  @State startSize: number = 100;
  result: SizeResult = {
    width: 0,
    height: 0
  } as SizeResult;

  // 自定义组件需要加上`@CustomLayout`装饰器，onPlaceChildren和onMeasureSize的重写才会生效。
  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    const startPos = 300;
    children.forEach((child) => {
      const pos = startPos - child.measureResult.height;
      child.layout({ x: pos, y: pos });
    });
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size: number = 100;
    children.forEach((child) => {
      let result: MeasureResult = child.measure({ minHeight: size, minWidth: size, maxWidth: size, maxHeight: size });
      size += result.width / 2;
    });
    this.result.width = 100;
    this.result.height = 400;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```