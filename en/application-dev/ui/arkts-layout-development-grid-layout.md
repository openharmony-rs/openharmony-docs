# Responsive Grid Layout (GridRow/GridCol)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zju_ljz-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @HelloCrease-->


## Overview

As an auxiliary positioning tool, the responsive grid layout is handy in UI design on mobile devices. It exhibits the following advantages:

1. Provides rules for layout design and resolves issues of dynamic layout across devices with different sizes. By dividing a page into equal-width columns and rows, you can easily locate and typeset page elements.

2. Provides a unified positioning method for the system to ensure layout consistency across layouts on different devices. This can reduce the complexity of design and development and improve work efficiency.

3. Provides a flexible spacing adjustment method for applications to accommodate special layout requirements. You can adjust the spacing between columns and between rows to control the typesetting of the entire page.

4. Completes the wrapping and adaptation automatically when overflow occurs. When the number of page elements exceeds the capacity of a row or column, they automatically wrap to a new row or column and adapt the typesetting to different devices.

The [GridRow](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md) component is a responsive grid container and must have [GridCol](../reference/apis-arkui/arkui-ts/ts-container-gridcol.md) as its child component.


## GridRow


### Breakpoints

**GridRow** defines breakpoints, which are screen width types in effect, based on the horizontal width ([screen density pixels](../reference/apis-arkui/arkui-ts/ts-pixel-units.md), in vp) of the screens. You can use the breakpoints to meet specific layout requirements.

By default, the grid container divides the device width into four types: xs, sm, md, and lg. The size ranges are as follows:

| Breakpoint| Value Range (vp)       | Device Description     |
| ---- | --------------- | --------- |
| xs   | [0, 320)  | Minimum-width device.|
| sm   | [320, 600) | Small-width device. |
| md   | [600, 840) | Medium-width device.|
| lg   | [840, +∞)  | Large-width device. |

In the GridRow component, you can use [BreakPoints](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#breakpoints) to customize the breakpoint value range. A maximum of six breakpoints are supported. In addition to the default four breakpoints, the xl and xxl breakpoints can be enabled. The layout of six devices (xs, sm, md, lg, xl, and xxl) can be set.

| Breakpoint| Device Description     |
| ---- | --------- |
| xs   | Minimum-width device.|
| sm   | Small-width device. |
| md   | Medium-width device.|
| lg   | Large-width device. |
| xl   | Extra-large-width device.|
| xxl  | Extra-extra-large-width device.|

- You can set the breakpoint position using a monotonically increasing array based on the actual application scenario. By default, the grid container supports four breakpoints. If no breakpoint position is set, the monotonically increasing array configured for the default breakpoints is ["320vp", "600vp", "840vp"]. You can use [BreakPoints](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#breakpoints) to support a maximum of six breakpoints. Therefore, the maximum length of the monotonically increasing array is 5.

  If the input array is [n0, n1, n2, n3, n4], the values of each breakpoint are as follows:

  |Breakpoint|Value Range|
  |---|-----------|
  |xs |[0, n0)    |
  |sm |[n0, n1)   |
  |md |[n1, n2)   |
  |lg |[n2, n3)   |
  |xl |[n3, n4)   |
  |xxl|[n4, INF)  |

  ```ts
  breakpoints: {value: ['100vp', '200vp']} // xs, sm, and md breakpoints are used. If the value is less than 100vp, the xs breakpoint is used. If the value is greater than 100vp and less than 200vp, the sm breakpoint is used. If the value is greater than 200vp, the md breakpoint is used.
  breakpoints: {value: ['320vp', '600vp']} // xs, sm, and md breakpoints are used. If the value is less than 320vp, the xs breakpoint is used. If the value is greater than 320vp and less than 600vp, the sm breakpoint is used. If the value is greater than 600vp, the md breakpoint is used.
  breakpoints: {value: ['320vp', '600vp', '840vp', '1440vp']} // Five breakpoints are used, which are xs, sm, md, lg, and xl. If the window width is less than 320 vp, the xs breakpoint is used. If the window width is between 320 vp and 600 vp, the sm breakpoint is used. If the window width is between 600 vp and 840 vp, the md breakpoint is used. If the window width is between 840 vp and 1440 vp, the lg breakpoint is used. If the window width is greater than 1440 vp, the xl breakpoint is used.
  ```

- The grid container listens to the size change of the window or container to determine breakpoints. reference is used to set the reference object for breakpoint switching. Since the application may be displayed in non-full-screen mode, it is better to design the breakpoints with the application window width as the reference.

  For example, you can set breakpoints to divide the application width into six ranges, and set columns to configure the number of columns in the grid container at each breakpoint.


  ```ts
  // xxx.ets
  @Entry
  @Component
  struct Index {
    @State bgColors: ResourceColor[] =
      ['rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)', 'rgb(61,157,180)', 'rgb(23,169,141)',
        'rgb(255,192,0)', 'rgb(170,10,33)'];
    build() {
      GridRow({
        columns: {
          xs: 2, // If the window width is within the xs breakpoint range, the grid container is divided into two columns.
          sm: 4, // If the window width is within the sm breakpoint range, the grid container is divided into four columns.
          md: 8, // If the window width is within the md breakpoint range, the grid container is divided into eight columns.
          lg: 12, // If the window width is within the lg breakpoint range, the grid container is divided into 12 columns.
          xl: 12, // If the window width is within the xl breakpoint range, the grid container is divided into 12 columns.
          xxl: 12 // If the window width is within the xxl breakpoint range, the grid container is divided into 12 columns.
        },
        breakpoints: {
          value: ['320vp', '600vp', '840vp', '1440vp', '1600vp'], // Default breakpoints ['320vp', '600vp', '840vp'] are retained, and breakpoints '1440vp' and '1600vp' are added. In actual development, you need to set breakpoint values based on the actual application scenario to implement multi-device adaptation with one-time development.
          reference: BreakpointsReference.WindowSize
        }
      }) {
        ForEach(this.bgColors, (color:ResourceColor, index?:number|undefined) => {
          GridCol({ span: 1 }) { // All child components occupy one column.
            Row() {
              Text(`${index}`)
            }.width("100%").height('50vp')
          }.backgroundColor(color)
        })
      }
    }
  }                                
  ```

  ![en-us_image_0000001511421272](figures/en-us_image_0000001511421272.gif)


### Columns

In the **GridRow**, **columns** is used to set the total number of columns in the responsive grid layout.

- Before API version 20, the default value of columns is 12. That is, if columns is not set, the grid layout is divided into 12 columns at any breakpoint.
- For API version 20 and later, the default value of columns is { xs: 2, sm: 4, md: 8, lg: 12, xl: 12, xxl: 12 }.


  ```ts
  // xxx.ets
  @Entry
  @Component
  struct Index {
    @State bgColors: ResourceColor[] =
      ['rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)', 'rgb(61,157,180)', 'rgb(23,169,141)',
        'rgb(255,192,0)', 'rgb(170,10,33)', 'rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)'];
    build() {
      GridRow() {
        ForEach(this.bgColors, (item:ResourceColor, index?:number|undefined) => {
          GridCol({span: 1}) {
            Row() {
              Text(`${index}`)
            }.width('100%').height('50')
          }.backgroundColor(item)
        })
      }
    }
  }
  ```

    Layout display before API version 20:

    ![en-us_image_0000001563060709](figures/en-us_image_0000001563060709.png)
    
    Layout display in API version 20 or later (using the SM device as an example, the default number of columns is 4):
    
    ![en-us_image_0000001563060710](figures/en-us_image_0000001563060710.png)


The columns attribute supports two types: number and [GridRowColumnOption](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#gridrowcolumnoption). You can set the total number of columns in the grid layout in either of the following ways:
- When the columns attribute is set to number, the grid layout is divided into the same number of columns on devices of any size. The following figures show the effect of setting the number of columns in the grid layout to 4 and 8, respectively, and the subelements occupy one column.

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct Index {
    @State bgColors: ResourceColor[] =
      ['rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)', 'rgb(61,157,180)', 'rgb(23,169,141)',
        'rgb(255,192,0)', 'rgb(170,10,33)'];
    @State currentBp: string = 'unknown';
    build() {
      Row() {
        GridRow({ columns: 4 }) {
          ForEach(this.bgColors, (item: ResourceColor, index?: number | undefined) => {
            GridCol({ span: 1 }) {
              Row() {
                Text(`${index}`)
              }.width('100%').height('50')
            }.backgroundColor(item)
          })
        }
        .width('100%').height('100%')
      }
      .height(160)
      .border({ color: 'rgb(39,135,217)', width: 2 })
      .width('90%')
    }
  }
  ```

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct Index {
    @State bgColors: ResourceColor[] =
      ['rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)', 'rgb(61,157,180)', 'rgb(23,169,141)',
        'rgb(255,192,0)', 'rgb(170,10,33)'];
    @State currentBp: string = 'unknown';
    build() {
      Row() {
        GridRow({ columns: 8 }) {
          ForEach(this.bgColors, (item: ResourceColor, index?: number | undefined) => {
            GridCol({ span: 1 }) {
              Row() {
                Text(`${index}`)
              }.width('100%').height('50')
            }.backgroundColor(item)
          })
        }
        .width('100%').height('100%')
      }
      .height(160)
      .border({ color: 'rgb(39,135,217)', width: 2 })
      .width('90%')
    }
  }
  ```

    ![en-us_image_0000001511421268](figures/en-us_image_0000001511421268.png)

- When columns is set to [GridRowColumnOption](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#gridrowcolumnoption), the number of grid columns can be set for devices of the following six sizes (xs, sm, md, lg, xl, and xxl). You can configure different numbers of grid columns for devices of different sizes.

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct Index {
    @State bgColors: ResourceColor[] =
      ['rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)', 'rgb(61,157,180)', 'rgb(23,169,141)',
        'rgb(255,192,0)', 'rgb(170,10,33)'];
    build() {
      GridRow({
        columns: { sm: 4, md: 8 },
        breakpoints: {
          value: ['320vp', '600vp', '840vp', '1440vp', '1600vp'] // Keep the default breakpoints ['320vp', '600vp', '840vp'] and add breakpoints '1440vp' and '1600vp'. In actual development, you need to set the breakpoint values based on the actual application scenario to implement multi-device adaptation with one development.
        }
      }) {
        ForEach(this.bgColors, (item: ResourceColor, index?: number | undefined) => {
          GridCol({ span: 1 }) {
            Row() {
              Text(`${index}`)
            }.width('100%').height('50')
          }.backgroundColor(item)
        })
      }
      .height(200)
      .border({ color: 'rgb(39,135,217)', width: 2 })
    }
  }
  ```
    Layout display before API version 20 (if the number of grid columns is not configured for xs devices, the default number of columns 12 is used):

    ![en-us_image_0000001563060689](figures/en-us_image_0000001563060689.gif)

    Layout display in API version 20 and later (xs devices inherit the number of grid columns of sm devices):

    ![en-us_image_0000001563060689](figures/en-us_image_0000001563060690.gif)

  If the number of grid columns is set only for sm and md devices, the default values are used for xs, lg, xl, and xxl devices according to [Grid Column Number Completion](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md#gridrowcolumnoption).


### Alignment

In the responsive grid layout, you can set the **direction** attribute of **GridRow** to define the direction in which child components are arranged. The options are **GridRowDirection.Row** (from left to right) or **GridRowDirection.RowReverse** (from right to left). An appropriate **direction** value can make the page layout more flexible and meet the design requirements.

- When child components are arranged from left to right (default):


    ```ts
    GridRow({ direction: GridRowDirection.Row }){ /* ... */ }
    ```

    ![en-us_image_0000001511740488](figures/en-us_image_0000001511740488.png)

- When child components are arranged from right to left (default):


    ```ts
    GridRow({ direction: GridRowDirection.RowReverse }){ /* ... */ }
    ```

    ![en-us_image_0000001562940517](figures/en-us_image_0000001562940517.png)


### Gutters

In the **GridRow** component, **gutter** is used to set the spacing between adjacent child components in the horizontal and vertical directions.

- When **gutter** is set to a number, the number applies to both the horizontal and vertical directions. In the following example, the horizontal and vertical spacing between adjacent child components is set to **10**.


    ```ts
    GridRow({ gutter: 10 }){ /* ... */ }
    ```

    ![en-us_image_0000001511740476](figures/en-us_image_0000001511740476.png)

- When **gutter** is set to a value of the **GutterOption** type, the **x** attribute of the value indicates the horizontal gutter, and the **y** attribute indicates the vertical gutter.


    ```ts
    GridRow({ gutter: { x: 20, y: 50 } }){ /* ... */ }
    ```

    ![en-us_image_0000001511900456](figures/en-us_image_0000001511900456.png)


## GridCol

The **\GridCol** component is a child component of the **GridRow** component. You can set the **span**, **offset**, and **order** attributes of this component by passing parameters or using setters.

- Setting **span**


    ```ts
  let Gspan:Record<string,number> = { 'xs': 1, 'sm': 2, 'md': 3, 'lg': 4 }
  GridCol({ span: 2 }){}
  GridCol({ span: { xs: 1, sm: 2, md: 3, lg: 4 } }){}
  GridCol(){}.span(2)
  GridCol(){}.span(Gspan)
    ```

- Setting **offset**


    ```ts
  let Goffset:Record<string,number> = { 'xs': 1, 'sm': 2, 'md': 3, 'lg': 4 }
  GridCol({ offset: 2, span: 1 }){}
  GridCol({ offset: { xs: 2, sm: 2, md: 2, lg: 2 }, span: 1 }){}
  GridCol({ span: 1 }){}.offset(Goffset) 
    ```

- Setting **order**


    ```ts
  let Gorder:Record<string,number> = { 'xs': 1, 'sm': 2, 'md': 3, 'lg': 4 }
  GridCol({ order: 2, span: 1 }){}
  GridCol({ order: { xs: 1, sm: 2, md: 3, lg: 4 }, span: 1 }){}
  GridCol({ span: 1 }){}.order(2)
  GridCol({ span: 1 }){}.order(Gorder)
    ```


### span

Sets the number of columns occupied by a child component in the grid layout, which determines the child component width. The default value is **1**.

The span can be of the number or [GridColColumnOption](../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#gridcolcolumnoption) type. You can set the number of columns occupied by a child component in the grid container in either of the following ways:
- When the value type is number, the number of columns occupied by the child component is the same across screen sizes.


    ```ts
    @Entry
    @Component
    struct Index {
      @State bgColors: ResourceColor[] =
        ['rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)', 'rgb(61,157,180)', 'rgb(23,169,141)',
          'rgb(255,192,0)', 'rgb(170,10,33)'];
      build() {
        GridRow({ columns: 8 }) {
          ForEach(this.bgColors, (color:ResourceColor, index?:number|undefined) => {
            GridCol({ span: 2 }) {
              Row() {
                Text(`${index}`)
              }.width('100%').height('50vp')
            }
            .backgroundColor(color)
          })
        }
      }
    }               
    ```

    ![en-us_image_0000001511421264](figures/en-us_image_0000001511421264.png)

- When span is set to GridColColumnOption, the number of columns occupied by child components can be set on devices of six different sizes (xs, sm, md, lg, xl, and xxl). Child components can be configured with different numbers of columns on devices of different sizes. If the number of columns is set only for sm and md, the default values are used for xs, lg, xl, and xxl devices according to GridColColumnOption.


    ```ts
    @Entry
    @Component
    struct Index {
      @State bgColors: ResourceColor[] =
        ['rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)', 'rgb(61,157,180)', 'rgb(23,169,141)',
          'rgb(255,192,0)', 'rgb(170,10,33)'];
      build() {
        GridRow({ columns: 8 }) {
          ForEach(this.bgColors, (color:ResourceColor, index?:number|undefined) => {
            GridCol({ span: { xs: 1, sm: 2, md: 3, lg: 4 } }) {
              Row() {
                Text(`${index}`)
              }.width('100%').height('50vp')
            }
            .backgroundColor(color)
          })
        }
      }
    }
    ```

    ![en-us_image_0000001511740492](figures/en-us_image_0000001511740492.gif)


### offset

Sets the column offset of a child component relative to the previous child component. The default value is **0**.

- When the value type is number, the column offset of the child component is the same across screen sizes.


    ```ts
    @Entry
    @Component
    struct Index {
      @State bgColors: ResourceColor[] =
        ['rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)', 'rgb(61,157,180)', 'rgb(23,169,141)',
          'rgb(255,192,0)', 'rgb(170,10,33)'];
      build() {
        GridRow() {
          ForEach(this.bgColors, (color:ResourceColor, index?:number|undefined) => {
            GridCol({ offset: 2, span: 1 }) {
              Row() {
                Text('' + index)
              }.width('100%').height('50vp')
            }
            .backgroundColor(color)
          })
        }
      }
    }                
    ```

    ![en-us_image_0000001563060705](figures/en-us_image_0000001563060705.png)

  A grid is divided into 12 columns. Each child component occupies one column and is offset by two columns. Each child component and spacing occupy three columns. Four child components are placed in one row.

- When the value type is **GridColColumnOption**, you can assign values specific to the screen size (xs, sm, md, lg, xl, xxl).


    ```ts
    @Entry
    @Component
    struct Index {
      @State bgColors: ResourceColor[] =
        ['rgb(213,213,213)', 'rgb(150,150,150)', 'rgb(0,74,175)', 'rgb(39,135,217)', 'rgb(61,157,180)', 'rgb(23,169,141)',
          'rgb(255,192,0)', 'rgb(170,10,33)'];
      build() {
        GridRow({ columns: 12 }) {
          ForEach(this.bgColors, (color: ResourceColor, index?: number | undefined) => {
            GridCol({ offset: { xs: 1, sm: 2, md: 3, lg: 4 }, span: 1 }) {
              Row() {
                Text('' + index)
              }.width('100%').height('50vp')
            }
            .backgroundColor(color)
          })
        }
        .height(200)
        .border({ color: 'rgb(39,135,217)', width: 2 })
      }
    }         
    ```

    ![en-us_image_0000001562700433](figures/en-us_image_0000001562700433.gif)


### order

Sets the sequence number of a child component in the grid layout. If a child component shares an **order** value with another child component or does not have **order** set, it is displayed based on its code sequence number. A child component with a smaller **order** value is placed before the one with a larger **order** value.

If **order** is not set for all child components, those that have **order** set are displayed after those that do not have **order** set and are sorted in ascending order based on the value.

- When the value type is number, child components are sorted in the same order across screen sizes.


    ```ts
    GridRow({ columns: 12 }) {
      GridCol({ order: 4, span: 1 }) {
        Row() {
          Text('1')
        }.width('100%').height('50vp')
      }.backgroundColor('rgb(213,213,213)')
      GridCol({ order: 3, span: 1 }) {
        Row() {
          Text('2')
        }.width('100%').height('50vp')
      }.backgroundColor('rgb(150,150,150)')
      GridCol({ order: 2, span: 1 }) {
        Row() {
          Text('3')
        }.width('100%').height('50vp')
      }.backgroundColor('rgb(0,74,175)')
      GridCol({ order: 1, span: 1 }) {
        Row() {
          Text('4')
        }.width('100%').height('50vp')
      }.backgroundColor('rgb(39,135,217)')
    }
    ```

    ![en-us_image_0000001511580892](figures/en-us_image_0000001511580892.png)

- When the value type is **GridColColumnOption**, you can assign values specific to the screen size (xs, sm, md, lg, xl, xxl). You can set 1234 for xs, 2341 for sm, 3412 for md, and 2431 for lg.


    ```ts
    GridRow({ columns: 12 }) {
      GridCol({ order: { xs:1, sm:5, md:3, lg:7}, span: 1 }) {
        Row() {
          Text('1')
        }.width('100%').height('50vp')
      }.backgroundColor(Color.Red)
      GridCol({ order: { xs:2, sm:2, md:6, lg:1}, span:1 }) {
        Row() {
          Text('2')
        }.width('100%').height('50vp')
      }.backgroundColor(Color.Orange)
      GridCol({ order: { xs:3, sm:3, md:1, lg:6}, span:1 }) {
        Row() {
          Text('3')
        }.width('100%').height('50vp')
      }.backgroundColor(Color.Yellow)
      GridCol({ order: { xs:4, sm:4, md:2, lg:5}, span:1 }) {
        Row() {
          Text('4')
        }.width('100%').height('50vp')
      }.backgroundColor(Color.Green)
    }
    ```

    ![en-us_image_0000001511900444](figures/en-us_image_0000001511900444.gif)


## Nesting of Responsive Grid Components

Responsive grid components can be contained in other responsive grid components.

In the following example, the responsive grid divides the entire space into 12 parts. At the first layer, **\GridCol** is nested in **GridRow**, and the space is divided into the large area in the center and the footer area. At the second layer, **\GridCol** is nested in **GridRow**, and the space is divided into the left and right areas. The child components take up the space allocated by the parent component at the upper layer. In this example, the pink area is made up of 12 columns of the screen space, and the green and blue areas take up the 12 columns of the parent component proportionally.

```ts
@Entry
@Component
struct GridRowExample {
  build() {
    GridRow({ columns: 12 }) {
      GridCol({ span: 12 }) {
        GridRow({ columns: 12 }) {
          GridCol({ span: 2 }) {
            Row() {
              Text('left').fontSize(24)
            }
            .justifyContent(FlexAlign.Center)
            .height('90%')
          }.backgroundColor('#ff41dbaa')

          GridCol({ span: 10 }) {
            Row() {
              Text('right').fontSize(24)
            }
            .justifyContent(FlexAlign.Center)
            .height('90%')
          }.backgroundColor('#ff4168db')
        }
        .backgroundColor('#19000000')
      }

      GridCol({ span: 12 }) {
        Row() {
          Text('footer').width('100%').textAlign(TextAlign.Center)
        }.width('100%').height('10%').backgroundColor(Color.Pink)
      }
    }.width('100%').height(300)
  }
}
```


![en-us_image_0000001563060697](figures/en-us_image_0000001563060697.png)


To sum up, the responsive grid components are powerful tools with a wide range of customization capabilities. With the required attributes set at different breakpoints, such as **Columns**, **Margin**, **Gutter**, and **span**, the layout is created automatically. You do not need to pay attention to the specific device type and device state (such as landscape and portrait).
