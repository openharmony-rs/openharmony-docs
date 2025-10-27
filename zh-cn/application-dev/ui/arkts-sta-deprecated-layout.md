# UI组件适配（布局）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## @ohos.mediaquery

### matchMediaSync

ArkTS-Dyn接口声明：[matchMediaSync(condition: string): MediaQueryListener](../reference/apis-arkui/js-apis-mediaquery.md#mediaquerymatchmediasyncdeprecated)

替代的ArkTS-Sta接口声明：[matchMediaSync(condition: string): mediaQuery.MediaQueryListener](../reference/apis-arkui/js-apis-arkui-UIContext.md#matchmediasync)


ArkTS-Dyn示例：
<!--deprecated_code_no_check-->
```ts
import { mediaquery } from '@kit.ArkUI';

let listener: mediaquery.MediaQueryListener = mediaquery.matchMediaSync('(orientation: landscape)'); // 监听横屏事件
```

ArkTS-Sta示例：
```ts
'use static'
import mediaquery from '@kit.ArkUI';

let listener: mediaquery.MediaQueryListener = this.getUIContext().getMediaQuery().matchMediaSync('(orientation: landscape)'); // 监听横屏事件
```

## GridContainer

ArkTS-Dyn接口声明：[GridContainer(value?: GridContainerOptions)](../reference/apis-arkui/arkui-ts/ts-container-gridcontainer.md#接口)

替代的ArkTS-Sta接口声明：[GridCol(option?: GridColOptions)](../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#接口)和[GridRow(option?: GridRowOptions)](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#接口)

### GridContainerOptions

ArkTS-Dyn接口声明：[
    GridContainerOptions{
        columns?: number | "auto";
        sizeType?: SizeType;
        gutter?: number | string;
        margin?: number | string;
    }](../reference/apis-arkui/arkui-ts/ts-container-gridcontainer.md#gridcontaineroptions对象说明)

替代的ArkTS-Sta接口声明：[
    GridColOptions{
        span?: number | GridColColumnOption;
        offset?: number | GridColColumnOption;
        order?: number | GridColColumnOption;
    }](../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#gridcoloptions对象说明)
    [GridRowOptions{
        gutter?: Length | GutterOption;
        columns?: number | GridRowColumnOption;
        breakpoints?: BreakPoints;
        direction?: GridRowDirection;
    }](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#gridrowoptions对象说明)

### gridSpan

ArkTS-Dyn接口声明：[gridSpan(value: number): T](../reference/apis-arkui/arkui-ts/ts-universal-attributes-grid.md#属性)

替代的ArkTS-Sta接口声明：[GridCol(option?: GridColOptions)](../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#接口)和[GridRow(option?: GridRowOptions)](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#接口)

### gridOffset

ArkTS-Dyn接口声明：[gridOffset(value: number): T](../reference/apis-arkui/arkui-ts/ts-universal-attributes-grid.md#属性)

替代的ArkTS-Sta接口声明：[GridCol(option?: GridColOptions)](../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#接口)和[GridRow(option?: GridRowOptions)](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#接口)

### SizeType

ArkTS-Dyn接口声明：[enum SizeType {Auto, XS, SM, MD, LG}](../reference/apis-arkui/arkui-ts/ts-container-gridcontainer.md#sizetype枚举说明)

替代的ArkTS-Sta接口声明：[GridColColumnOption](../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#gridcolcolumnoption)和[GridRowColumnOption](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#gridrowcolumnoption)

### useSizeType

ArkTS-Dyn接口声明：[
    useSizeType(value: {
        xs?: number | { span: number; offset: number };
        sm?: number | { span: number; offset: number };
        md?: number | { span: number; offset: number };
        lg?: number | { span: number; offset: number };
    }): T](../reference/apis-arkui/arkui-ts/ts-universal-attributes-grid.md#属性)

替代的ArkTS-Sta接口声明：[GridColColumnOption](../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#gridcolcolumnoption)和[GridRowColumnOption](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#gridrowcolumnoption)


ArkTS-Dyn示例：
<!--deprecated_code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct GridContainerExample1 {
  build() {
    Column() {
      Text('useSizeType').fontSize(15).fontColor(0xCCCCCC).width('90%')
      GridContainer() {
        Row() {
          Row() {
            Text('Left').fontSize(25)
          }
          .useSizeType({
            xs: { span: 1, offset: 0 }, sm: { span: 1, offset: 0 },
            md: { span: 1, offset: 0 }, lg: { span: 2, offset: 0 }
          })
          .height("100%")
          .backgroundColor(0x66bbb2cb)

          Row() {
            Text('Center').fontSize(25)
          }
          .useSizeType({
            xs: { span: 1, offset: 0 }, sm: { span: 2, offset: 1 },
            md: { span: 5, offset: 1 }, lg: { span: 7, offset: 2 }
          })
          .height("100%")
          .backgroundColor(0x66b6c5d1)

          Row() {
            Text('Right').fontSize(25)
          }
          .useSizeType({
            xs: { span: 1, offset: 0 }, sm: { span: 1, offset: 3 },
            md: { span: 2, offset: 6 }, lg: { span: 3, offset: 9 }
          })
          .height("100%")
          .backgroundColor(0x66bbb2cb)
        }
        .height(200)

      }
      .backgroundColor(0xf1f3f5)
      .margin({ top: 10 })

      // 单独设置组件的span和offset,在sm尺寸大小的设备上使用useSizeType中sm的数据实现一样的效果
      Text('gridSpan,gridOffset').fontSize(15).fontColor(0xCCCCCC).width('90%')
      GridContainer() {
        Row() {
          Row() {
            Text('Left').fontSize(25)
          }
          .gridSpan(1)
          .height("100%")
          .backgroundColor(0x66bbb2cb)

          Row() {
            Text('Center').fontSize(25)
          }
          .gridSpan(2)
          .gridOffset(1)
          .height("100%")
          .backgroundColor(0x66b6c5d1)

          Row() {
            Text('Right').fontSize(25)
          }
          .gridSpan(1)
          .gridOffset(3)
          .height("100%")
          .backgroundColor(0x66bbb2cb)
        }.height(200)
      }
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { Entry, Component, GridRow, GridCol, Column, Row,  GridRowDirection, BreakpointsReference, Margin, Color, ForEach, State} from '@kit.ArkUI';

@Entry
@Component
struct GridColExample {
  @State bgColors: Color[] =
    [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Pink, Color.Grey, Color.Blue, Color.Brown];
  @State currentBp: string = 'unknown';

  build() {
    Column() {
      GridRow({
        columns: 5,
        gutter: { x: 5, y: 10 },
        breakpoints: {
          value: ["400vp", "600vp", "800vp"],
          reference: BreakpointsReference.WindowSize
        },
        direction: GridRowDirection.Row
      }) {
        ForEach(this.bgColors, (color: Color) => {
          GridCol({
            span: { xs: 1, sm: 2, md: 3, lg: 4 },
            offset: 0,
            order: 0
          }) {
            Row().width("100%").height("20vp")
          }.borderColor(color).borderWidth(2)
        })
      }.width("100%").height("100%")
      .onBreakpointChange((breakpoint) => {
        this.currentBp = breakpoint
      })
    }.width('80%').margin({ left: 10, top: 5, bottom: 5 } as Margin).height(200)
    .border({ color: '#880606', width: 2 })
  }
}
```

## 自定义布局

### LayoutChild

ArkTS-Dyn接口声明：[
    LayoutChild {
        name: string,
        id: string,
        constraint: ConstraintSizeOptions,
        borderInfo: LayoutBorderInfo,
        position: Position,
        measure(childConstraint: ConstraintSizeOptions),
        layout(childLayoutInfo: LayoutInfo),
    }](../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#layoutchilddeprecated)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

### LayoutInfo

ArkTS-Dyn接口声明：[LayoutInfo { position: Position, constraint: ConstraintSizeOptions}](../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#layoutinfodeprecated)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

### LayoutBorderInfo

ArkTS-Dyn接口声明：[LayoutBorderInfo { borderWidth: EdgeWidths; margin: Margin, padding: Padding,}](../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#layoutborderinfodeprecated)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

### onMeasure

ArkTS-Dyn接口声明：[onMeasure?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void](../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#onmeasuredeprecated)

替代的ArkTS-Sta接口声明：[onMeasureSize?(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions): SizeResult](../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#onmeasuresize10)

### onLayout

ArkTS-Dyn接口声明：[onLayout?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void](../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#onlayoutdeprecated)

替代的ArkTS-Sta接口声明：[onPlaceChildren?(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions):void](../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#onplacechildren10)


ArkTS-Dyn示例：
<!--deprecated_code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      CustomLayout() {
        ForEach([1, 2, 3], (index: number) => {
          Text('Sub' + index)
            .fontSize(30)
            .borderWidth(2)
        })
      }
    }
  }
}


@Component
struct CustomLayout {
  @Builder
  doNothingBuilder() {
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;

  onLayout(children: Array<LayoutChild>, constraint: ConstraintSizeOptions) {
    let pos = 0;
    children.forEach((child) => {
      child.layout({ position: { x: pos, y: pos }, constraint: constraint })
      pos += 70;
    })
  }

  onMeasure(children: Array<LayoutChild>, constraint: ConstraintSizeOptions) {
    let size = 100;
    children.forEach((child) => {
      child.measure({ minHeight: size, minWidth: size, maxWidth: size, maxHeight: size })
      size += 50;
    })
  }

  build() {
    this.builder()
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { Text, Column, Component, Position, Entry, Builder, BuilderParam, ForEach, SizeResult, GeometryInfo, Layoutable, ConstraintSizeOptions, Measurable, MeasureResult, CustomLayout, State} from '@kit.ArkUI';

@Entry
@Component
struct MyStateSample {
  build() {
    Column() {
      Custom1({ builder: ColumnChildren })
    }
  }
}

@Builder
function ColumnChildren() {
  ForEach([1, 2, 3], (item: Int, index: number) => { // 暂不支持lazyForEach的写法
    Text('S' + item)
      .fontSize(30)
      .width(100)
      .height(100)
      .borderWidth(2)
      .offset({ x: 10, y: 20 } as Position)
  })

}
@CustomLayout
@Component
struct Custom1 {

  @Builder
  doNothingBuilder() {
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;
  @State startSize: number = 100;
  result: SizeResult = {
    width: 0,
    height: 0
  } as SizeResult;

  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    let startPos = 300;
    children.forEach((child) => {
      let pos = startPos - child.measureResult.height;
      child.layout({ x: pos, y: pos })
    })
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size = 100;
    children.forEach((child) => {
      let result: MeasureResult = child.measure({ minHeight: size, minWidth: size, maxWidth: size, maxHeight: size })
      size += result.width / 2
      ;
    })
    this.result.width = 100;
    this.result.height = 400;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```