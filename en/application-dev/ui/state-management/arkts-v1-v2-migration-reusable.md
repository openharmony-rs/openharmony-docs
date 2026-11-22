# Migration for Component Reuse
<!--Kit: ArkUI--> 
<!--Subsystem: ArkUI--> 
<!--Owner: @jiyujia926--> 
<!--Designer: @zhangboren--> 
<!--Tester: @zhangwenhan12--> 
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7860d2a947413b5f8775dab763bab3b6b2651151 translatedAt=2026-10-28T04:14:20.023Z pushedAt=2026-10-28T08:20:13.119Z nl=1 -->

This document describes how to migrate components from V1 to V2, involving the following decorators.


| V1 Decorator| V2 Decorator|
| -------- | -------- |
| [@Reusable](./arkts-reusable.md) | [@ReusableV2](./arkts-new-reusableV2.md) |


## \@Reusable->\@ReusableV2 Migration Rule


### V1 -> V2 Component Migration

**Migration Rules**

- Migrate the parent custom component decorated by \@Component to \@ComponentV2.

- Migrate the child custom component decorated by \@Reusable to \@ReusableV2.

- For details about the migration of state variables in a component, see [Migration for Component State Variables](./arkts-v1-v2-migration-inner-component.md)


### aboutToRecycle and aboutToReuse Migration

**Migration Rules**

- The [aboutToRecycle](../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttorecycle10) lifecycle does not require any changes, and the original implementation can be retained.

- The [aboutToReuse](../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse18) lifecycle has been optimized in component reuse V2. Parameters have been removed, and all state variables are automatically reset before reuse (for details, refer to [Resetting State Variables in Components Before Reuse](./arkts-new-reusableV2.md#resetting-state-variables-in-components-before-reuse)), eliminating the need for developers to manually assign them back to their initial values in **aboutToReuse**.

``` TypeScript
// Original V1 component.
@Reusable
@Component
struct ReusableComponent {
  // There is a possibility of external value transfer. The value can be transferred to @Local or @Param @Once.
  @State val: string = 'Hello World';
  aboutToRecycle(): void {
    // This is where you can release memory-intensive content or other non-essential resource references to avoid continuous memory usage.
    console.info('ReusableComponent aboutToRecycle called');
  }
  aboutToReuse(params: ESObject): void {
    console.info('ReusableComponent aboutToReuse called');
    this.val = params.val ?? 'Hello World'; // Reassign the value of the @State variable.
  }
  build() {
    Column() {
      Text(`val: ${this.val}`)
    }
  }
}

// Migrated V2 Component
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  // Migrate to @Local when there are no externally passed values
  @Local val: string = 'Hello World';
  // Migrate to @Param or @Once when an external input value exists.
  @Require @Param @Once param: string;
  aboutToRecycle(): void {
    // aboutToRecycle does not need to be changed.
    console.info('ReusableV2Component aboutToRecycle called');
  }
  aboutToReuse(): void { // aboutToReuse does not have any parameter.
    // When aboutToReuse is executed, @Local has been reset back to 'Hello World', and @Param/@Once have been reset back to the externally passed values.
    console.info('ReusableV2Component aboutToReuse called');
    this.val = 'Hello ArkUI'; // The value can be changed to another one during reuse.
    this.param = 'Hello ArkUI'; // @Param/@Once can be modified locally.
  }
  build() {
    Column() {
      Text(`val: ${this.val}`)
      Text(`param: ${this.param}`)
    }
  }
}
```


### reuseId -> reuse

**Migration Rules**

In component reuse V1, the [reuseId](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-reuse-id.md#reuseid) attribute is used to mark the reuse group of a component. After the migration to component reuse V2, the [reuse](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-reuse.md#reuse) attribute needs to be used.

``` TypeScript
// Original writing method of V1
ReusableComponent().reuseId('groupA')
// Writing method after migration to V2
ReusableV2Component().reuse({reuseId: () => 'groupA'})
```


### Component Freezing

**Migration Rules**

In component reuse V1, components in the reuse pool are frozen only when the developer enables the freeze switch `freezeWhenInactive` of the reusable component. For details, refer to [Custom Component Freeze](./arkts-custom-components-freeze.md). In component reuse V2, freezing is enabled automatically. For details, refer to [Freeze During the Reuse Phase](./arkts-new-reusableV2.md#component-freezing-in-the-reuse-phase).


### LazyForEach -> Repeat

**Migration Rules**

In component reuse V1, **LazyForEach** is often used with component reuse to implement high-performance lazy loading. In component reuse V2, you are advised to use [Repeat](../rendering-control/arkts-new-rendering-control-repeat.md) instead of [LazyForEach](../rendering-control/arkts-rendering-control-lazyforeach.md). **Repeat** can reuse components. Compared with **LazyForEach**, **Repeat** has simpler APIs and better performance. For details about how to migrate **LazyForEach** to **Repeat**, see [Migrating from LazyForEach to Repeat](./arkts-v1-v2-migration-rendering-control-repeat.md#from-lazyforeach-to-repeat).


## @Reusable -> @ReusableV2 Migration Example


### if Statement

For details about the \@Reusable usage example, see [Dynamic Layout Update](./arkts-reusable.md#dynamic-layout-update).

The sample code snippet of **if** for \@ReusableV2 is as follows:

<!-- @[reusable_if_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableIfScene.ets) -->

``` TypeScript
// Data model, using @ObservedV2 and @Trace to implement deep observation.
@ObservedV2
class Message {
  // Use @Trace to decorate properties that need to be observed for changes.
  @Trace public value: string | undefined;

  constructor(value: string) {
    this.value = value;
  }
}

@Entry
@ComponentV2
struct ReusableIfScene {
  // Switch that controls the display and hiding of child components.
  @Local isSwitch: boolean = true;

  build() {
    Column() {
      // Click the button to toggle the display and hiding of child components, triggering component creation and reuse.
      Button('Hello')
        .fontSize(24)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.isSwitch = !this.isSwitch;
        })
      if (this.isSwitch) {
        // If there is only one reusable component, you do not need to set the reuse property.
        Child({ message: new Message('Child') })
          .reuse({ reuseId: () => 'Child' })
      }
    }
    .height('100%')
    .width('100%')
  }
}

// Reusable component.
@ReusableV2
@ComponentV2
struct Child {
  // @Param @Once receives externally passed values and synchronizes only once during initialization.
  @Require @Param @Once message: Message = new Message('AboutToReuse');

  // Callback during component reuse. Remove it if no additional modification to state variables is needed.
  aboutToReuse() {
    console.info('Reuse====Child==');
  }

  build() {
    Column() {
      // Display the current message content.
      Text(this.message.value)
        .fontSize(30)
        .margin(20)
    }
    .borderWidth(1)
    .margin({ top: 10 })
    .height(100)
  }
}
```
![](figures/v1_v2_reusable_if.gif)

### List Scrolling with Repeat

For details about the \@Reusable usage example, see [List Scrolling with LazyForEach](./arkts-reusable.md#list-scrolling-with-lazyforeach).

The sample code snippet of list scrolling with **Repeat** for \@ReusableV2 is as follows:

<!-- @[reusable_repeat_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableRepeatScene.ets) -->

``` TypeScript
@Entry
@ComponentV2
struct ReuseV2Demo {
  // List data source.
  private data: string[] = [];

  // Initialize the list data.
  aboutToAppear() {
    for (let i = 1; i < 1000; i++) {
      this.data.push(i + '');
    }
  }

  build() {
    Column() {
      List({ space: 10 }) {
        // Use the virtualScroll mode of Repeat to implement lazy loading, and improve scrolling performance with reusable components.
        Repeat(this.data)
          .virtualScroll()
          .each((ri) => {
            ListItem() {
              CardViewV2({ item: ri.item })
            }
          })
      }
      .width('100%')
      .height('100%')
      .padding(10)
    }
  }
}

// Reusable component
@ReusableV2
@ComponentV2
export struct CardViewV2 {
  // Use @Param to receive external variables and observe their changes.
  @Param item: string = '';

  // Repeat can perform reuse by itself and does not go through the lifecycle of custom component reuse.
  aboutToReuse(): void {
  }

  build() {
    Row() {
      // Display the sequence number of the current list item.
      Text(`#${this.item}`)
        .fontSize(20)
        .fontWeight(FontWeight.Bold)

      // Display the list item content.
      Text(`Item ${this.item}`)
        .fontSize(18)
        .fontColor('#333333')
        .margin({ left: 10 })
    }
    .width('100%')
    .height(80)
    .padding({ left: 20, right: 20 })
    .borderRadius(12)
    .backgroundColor('#ffffff')
    .shadow({
      radius: 4,
      color: '#1a000000',
      offsetX: 0,
      offsetY: 2
    })
  }
}
```
![](figures/v1_v2_reusable_repeat.gif)

### List Scrolling with if Statements

For details about the \@Reusable usage example, see [List Scrolling with if Statements](./arkts-reusable.md#list-scrolling-with-if-statements).

The sample code snippet of list scrolling with **if** statements for \@ReusableV2 is as follows:

<!-- @[reusable_list_if_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableListIfScene.ets) -->

``` TypeScript
@Entry
@ComponentV2
struct ReusableListIfScene {
  // List data source.
  private dataSource: FriendMoment[] = [];

  // Initialize the data source, including two types: with and without images.
  aboutToAppear(): void {
    for (let i = 0; i < 20; i++) {
      let title = i + 1 + 'test_if';
      // Replace the content of the displayed image. The following uses app.media.startIcon as an example.
      this.dataSource.push(new FriendMoment(i.toString(), title, 'app.media.startIcon'));
    }

    for (let i = 0; i < 50; i++) {
      let title = i + 1 + 'test_if';
      this.dataSource.push(new FriendMoment(i.toString(), title, ''));
    }
  }

  build() {
    Column() {
      List({ space: 3 }) {
        Repeat(this.dataSource)
          .virtualScroll()
          .each((ri) => {
            ListItem() {
              // Select different reuse groups based on whether an image is present.
              if (ri.item.image) {
                OneMoment({ moment: ri.item })
                  .reuse({ reuseId: () => 'withImage' })
              } else {
                OneMoment({ moment: ri.item })
                  .reuse({ reuseId: () => 'noImage' })
              }
            }
          })
      }
      .cachedCount(0)
    }
  }
}

// Data model.
@ObservedV2
class FriendMoment {
  @Trace public id: string = '';
  @Trace public text: string = '';
  @Trace public title: string = '';
  @Trace public image: string = '';
  @Trace public answers: Array<ResourceStr> = [];

  constructor(id: string, title: string, image: string) {
    this.text = id;
    this.title = title;
    this.image = image;
  }
}

// Reusable component.
@ReusableV2
@ComponentV2
export struct OneMoment {
  // Receive the data object passed in from outside.
  @Require @Param moment: FriendMoment;

  // Only components with the same reuse ID can trigger reuse. Remove this if no additional modification to state variables is required.
  aboutToReuse(): void {
    console.info(`=====aboutToReuse====OneMoment==Reused==${this.moment.text}`);
  }

  build() {
    Column() {
      // Display the text content.
      Text(this.moment.text)
      // if branch: display the image area when an image is present.
      if (this.moment.image !== '') {
        // Use Flex wrapping to implement automatic line wrapping layout.
        Flex({ wrap: FlexWrap.Wrap }) {
          Image($r(this.moment.image))
            .height(50)
            .width(50)
          Image($r(this.moment.image))
            .height(50)
            .width(50)
          Image($r(this.moment.image))
            .height(50)
            .width(50)
          Image($r(this.moment.image))
            .height(50)
            .width(50)
        }
      }
    }
  }
}
```
![](figures/v1_v2_reusable_if_two.gif)

### List Scrolling with Repeat Full Loading

In state management V2, you are advised to use the [full loading mode](../rendering-control/arkts-new-rendering-control-repeat.md#lazy-loading-capability) instead of [ForEach](../rendering-control/arkts-rendering-control-foreach.md) to implement cyclic rendering.

For details about the \@Reusable usage example, see [List Scrolling with ForEach](./arkts-reusable.md#list-scrolling-with-foreach).

The sample code snippet of list scrolling with **Repeat** full loading for \@ReusableV2 is as follows:

<!-- @[reusable_repeat_all_load_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableRepeatAllLoadScene.ets) -->

``` TypeScript
// xxx.ets
@Entry
@ComponentV2
struct ReusableRepeatAllLoadScene {
  // List data source.
  @Local dataSource: ListItemObject[] = [];

  build() {
    Column() {
      Row() {
        // Click clear to clear the list data and trigger component destruction.
        Button('clear')
          .onClick(() => {
            for (let i = 1; i < 50; i++) {
              this.dataSource.pop();
            }
          })
          .height(40)

        // Click update to refill the data and trigger component creation or reuse.
        Button('update')
          .onClick(() => {
            for (let i = 1; i < 50; i++) {
              let obj = new ListItemObject();
              obj.id = i;
              obj.uuid = Math.random().toString();
              obj.isExpand = false;
              this.dataSource.push(obj);
            }
          })
          .height(40)
      }

      List({ space: 10 }) {
        // Do not use virtualScroll; use the Repeat full loading mode instead.
        Repeat(this.dataSource)
          .each((ri) => {
            ListItem() {
              ListItemView({
                obj: ri.item
              })
            }
          })
      }
      .cachedCount(0)
      .width('100%')
      .height('100%')
    }
  }
}

// Reusable component.
@ReusableV2
@ComponentV2
struct ListItemView {
  // Receive the data object passed in from outside.
  @Require @Param obj: ListItemObject;

  // Callback when the component is created for the first time.
  aboutToAppear(): void {
    // Click update, enter for the first time, and scroll up and down. Because of the Repeat full loading attribute, the component cannot be reused.
    console.info('=====aboutToAppear=====ListItemView==Created==');
  }

  // Callback when the component is reused.
  aboutToReuse() {
    // Reuse succeeds after you click Clear and update again.
    // It meets the requirement of repeatedly creating multiple destroyed custom components in a frame.
    // Remove this if no additional modification to the state variable is required.
    console.info('=====aboutToReuse====ListItemView==Reused==');
  }

  build() {
    Column({ space: 10 }) {
      // Display the title text.
      Text(`${this.obj.id}.Title`)
        .fontSize(16)
        .fontColor('#000000')
        .padding({
          top: 20,
          bottom: 20,
        })

      // Display additional content based on the expanded state.
      if (this.obj.isExpand) {
        Text('expand')
          .fontSize(14)
          .fontColor('#999999')
      }
    }
    .width('100%')
    .borderRadius(10)
    .backgroundColor(Color.White)
    .padding(15)
    // Click to toggle the expanded/collapsed state.
    .onClick(() => {
      this.obj.isExpand = !this.obj.isExpand;
    })
  }
}

// Data model.
@ObservedV2
class ListItemObject {
  @Trace public uuid: string = '';
  @Trace public id: number = 0;
  @Trace public isExpand: boolean = false;
}
```
![](figures/v1_v2_reusable_repeat_two.gif)

### Grid

For details about the \@Reusable usage example, see [Grid](./arkts-reusable.md#grid).

The sample code snippet of Grid for \@ReusableV2 is as follows:

<!-- @[reusable_grid_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableGridScene.ets) -->

``` TypeScript
@Entry
@ComponentV2
struct MyComponent {
  // Data source.
  @Local data: number[] = [];

  // Initialize the grid data.
  aboutToAppear() {
    for (let i = 1; i < 1000; i++) {
      this.data.push(i);
    }
  }

  build() {
    Column({ space: 5 }) {
      Grid() {
        // Use the virtualScroll mode of Repeat with Grid to implement lazy loading.
        Repeat(this.data)
          .virtualScroll()
          .each((ri) => {
            GridItem() {
              ReusableV2ChildComponent({ item: ri.item })
            }
          })
      }
      .cachedCount(2) // Set the number of cached GridItems.
      .columnsTemplate('1fr 1fr 1fr') // Three-column equal-width layout.
      .columnsGap(10)
      .rowsGap(10)
      .margin(10)
      .height(500)
      .backgroundColor(0xFAEEE0)
    }
  }
}

// Reusable component.
@ReusableV2
@ComponentV2
struct ReusableV2ChildComponent {
  // Receive the sequence number passed in from outside.
  @Param item: number = 0;

  build() {
    Column() {
      // Replace the content of the displayed image. The following uses app.media.startIcon as an example.
      Image($r('app.media.startIcon'))
        .objectFit(ImageFit.Fill)
        .layoutWeight(1)
      // Display the image sequence number.
      Text(`Image${this.item}`)
        .fontSize(16)
        .textAlign(TextAlign.Center)
    }
    .width('100%')
    .height(120)
    .backgroundColor(0xF9CF93)
  }
}
```
![](figures/v1_v2_reusable_grid.png)

### WaterFlow

For details about the \@Reusable usage example, see [WaterFlow](./arkts-reusable.md#waterflow).

The sample code snippet of WaterFlow for \@ReusableV2 is as follows:

<!-- @[reusable_waterflow_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableWaterFlowScene.ets) -->

``` TypeScript
// Reusable component
@ReusableV2
@ComponentV2
struct ReusableV2FlowItem {
  // Receive the sequence number passed in from outside.
  @Param item: number = 0;

  build() {
    Column() {
      // Display the sequence number of the waterfall flow child item.
      Text('N' + this.item)
        .fontSize(24)
        .height(26)
        .margin(10)
      // Replace the content of the displayed image. The following uses app.media.startIcon as an example.
      Image($r('app.media.startIcon'))
        .objectFit(ImageFit.Cover)
        .width(50)
        .height(50)
    }
  }
}

@Entry
@ComponentV2
struct ReusableWaterFlowScene {
  // Minimum size of the flow layout child item.
  @Local minSize: number = 50;
  // Maximum size of the flow layout child item.
  @Local maxSize: number = 80;
  // Waterfall flow scroll controller.
  scroller: Scroller = new Scroller();
  // Waterfall flow data source.
  @Local dataSource: number[] = [];
  private itemWidthArray: number[] = [];
  private itemHeightArray: number[] = [];

  // Calculate the width/height of the flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Save the width/height of the flow item.
  getItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemWidthArray.push(this.getSize());
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Initialize the waterfall flow data.
  aboutToAppear() {
    for (let i = 0; i <= 60; i++) {
      this.dataSource.push(i);
    }
    this.getItemSizeArray();
  }

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Column({ space: 2 }) {
        // Click the button to return to the top of the waterfall flow.
        Button('back top')
          .height('5%')
          .onClick(() => {
            // Return to the top after clicking.
            this.scroller.scrollEdge(Edge.Top);
          })
        WaterFlow({ scroller: this.scroller }) {
          // Use the virtualScroll mode of Repeat with WaterFlow to implement lazy loading.
          Repeat(this.dataSource)
            .virtualScroll()
            .each((ri) => {
              FlowItem() {
                ReusableV2FlowItem({ item: ri.item })
              }
              .onAppear(() => {
                // Load more data when scrolling to the bottom.
                if (ri.item + 20 == this.dataSource.length) {
                  for (let i = 0; i < 50; i++) {
                    this.dataSource.splice(this.dataSource.length, 0, this.dataSource.length);
                  }
                }
              })
            })
        }
        .margin({ left: 160, top: 10 })
      }
    }
  }
}
```
![](figures/v1_v2_reusable_waterflow.gif)

### Swiper

For details about the \@Reusable usage example, see [Swiper](./arkts-reusable.md#swiper).

The sample code snippet of Swiper for \@ReusableV2 is as follows:

<!-- @[reusable_swiper_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableSwiperScene.ets) -->

``` TypeScript
@Entry
@ComponentV2
struct ReusableSwiperScene {
  // Swiper data source.
  private dataSource: Question[] = [];

  // Initialize the swiper data.
  aboutToAppear(): void {
    for (let i = 0; i < 1000; i++) {
      let title = i + 1 + 'test_swiper';
      let answers = ['test1', 'test2', 'test3', 'test4'];
      // Replace the content of the displayed image. The following uses app.media.startIcon as an example.
      this.dataSource.push(new Question(i.toString(), title, $r('app.media.startIcon'), answers));
    }
  }

  build() {
    Column({ space: 5 }) {
      Swiper() {
        // Use the virtualScroll mode of Repeat with Swiper to implement lazy loading.
        Repeat(this.dataSource)
          .virtualScroll()
          .each((ri) => {
            QuestionSwiperItem({ itemData: ri.item })
          })
      }
    }
    .width('100%')
    .margin({ top: 5 })
  }
}

// Data model.
@ObservedV2
class Question {
  @Trace public id: string = '';
  @Trace public title: ResourceStr = '';
  @Trace public image: ResourceStr = '';
  @Trace public answers: Array<ResourceStr> = [];

  constructor(id: string, title: ResourceStr, image: ResourceStr, answers: Array<ResourceStr>) {
    this.id = id;
    this.title = title;
    this.image = image;
    this.answers = answers;
  }
}

// Reusable component.
@ReusableV2
@ComponentV2
struct QuestionSwiperItem {
  // Receive the question data passed in from outside.
  @Param itemData: Question | null = null;

  build() {
    Column() {
      // Display the question title.
      Text(this.itemData?.title)
        .fontSize(18)
        .fontColor($r('sys.color.ohos_id_color_primary'))
        .alignSelf(ItemAlign.Start)
        .margin({
          top: 10,
          bottom: 16
        })
      // Display the question image.
      Image(this.itemData?.image)
        .borderRadius(12)
        .objectFit(ImageFit.Contain)
        .margin({
          bottom: 16
        })
        .height(80)
        .width(80)

      // Use Repeat to traverse and display the option list.
      Column({ space: 16 }) {
        Repeat(this.itemData?.answers)
          .each((ri) => {
            Text(ri.item)
              .fontSize(16)
              .fontColor($r('sys.color.ohos_id_color_primary'))
          })
      }
      .width('100%')
      .alignItems(HorizontalAlign.Start)
    }
    .width('100%')
    .padding({
      left: 16,
      right: 16
    })
  }
}
```
![](figures/v1_v2_reusable_swiper.gif)


### List Scrolling with ListItemGroup

For details about the \@Reusable usage example, see [List Scrolling with ListItemGroup](./arkts-reusable.md#list-scrolling-with-listitemgroup).

The sample code snippet of list scrolling with ListItemGroup for \@ReusableV2 is as follows:

<!-- @[reusable_listitemgroup_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableListItemGroupScene.ets) -->

``` TypeScript
@Entry
@ComponentV2
struct ListItemGroupAndReusable {
  // Data source for list groups.
  private dataSource: DataSrc[] = [];

  // Builder for list group headers.
  @Builder
  itemHead(text: string) {
    Text(text)
      .fontSize(20)
      .backgroundColor(0xff519db4)
      .width('100%')
      .padding(10)
  }

  // Initialize the group data.
  aboutToAppear() {
    for (let i = 0; i < 10000; i++) { // Loop 10000 times.
      let data = new DataSrc();
      for (let j = 0; j < 12; j++) { // 12 data items per group.
        data.dataScr1.push(`Test item data: ${i} - ${j}`);
      }
      this.dataSource.push(data);
    }
  }

  build() {
    Stack() {
      List() {
        // The outer Repeat iterates over the group data.
        Repeat(this.dataSource)
          .virtualScroll()
          .each((ri) => {
            ListItemGroup({ header: this.itemHead(ri.index.toString()) }) {
              // The inner Repeat iterates over the child items in each group.
              Repeat(ri.item.dataScr1)
                .virtualScroll()
                .each((ri) => {
                  ListItem() {
                    Inner({ str: ri.item })
                  }
                })
            }
          })
      }
    }
    .width('100%')
    .height('100%')
  }
}

// Reusable component.
@ReusableV2
@ComponentV2
struct Inner {
  // Receive the text content passed in from outside.
  @Param str: string = '';

  build() {
    // Display the text content.
    Text(this.str)
  }
}

// Group data model.
@ObservedV2
class DataSrc {
  @Trace public dataScr1: string[] = [];
}
```
![](figures/v1_v2_reusable_listitemgroup.gif)

### Multiple Item Types

For details about the \@Reusable usage example, see [Multiple Item Types](./arkts-reusable.md#scenarios-involving-multiple-item-types).

The sample code for using multiple item types of \@ReusableV2 is as follows:

**Standard**

The layout of the reusable components is the same. For details, see the examples in the list scrolling part of this document.

**Limited Variation**

There are differences between reusable components, but the number of types is limited. For example, reuse can be achieved by explicitly setting two **reuse** values or using two custom components.

<!-- @[reusable_limit_type_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableLimitTypeScene.ets) -->

``` TypeScript
@Entry
@ComponentV2
struct ReusableLimitTypeScene {
  // List data source.
  private data: number[] = [];

  // Initialize the list data.
  aboutToAppear() {
    for (let i = 0; i < 1000; i++) {
      this.data.push(i);
    }
  }

  build() {
    Column() {
      List({ space: 10 }) {
        Repeat(this.data)
          .virtualScroll()
          .each((ri) => {
            ListItem() {
              // Select different reuse groups based on parity.
              if (ri.item % 2 === 0) {
                // Even items use the ReusableV2ComponentOne reuse group.
                ReusableV2Component({ item: ri.item })
                  .reuse({ reuseId: () => 'ReusableV2ComponentOne' })
              } else {
                ReusableV2Component({ item: ri.item })
                  .reuse({ reuseId: () => 'ReusableV2ComponentTwo' })
              }
            }
          })
      }
      .cachedCount(2)
    }
  }
}

// Reusable component.
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  // Receive the sequence number passed in from outside.
  @Param item: number = 0;

  // Callback during component reuse. Remove it if no additional modification to state variables is required.
  aboutToReuse() {
    console.info(`ReusableComponent aboutToReuse called${this.item}`);
  }

  build() {
    Column() {
      // Render different content based on type differences within the component.
      if (this.item % 2 === 0) {
        // Even items render style one.
        Text(`Item ${this.item} ReusableComponentOne`)
          .fontSize(20)
          .margin({ left: 10 })
      } else {
        // Odd items render style two.
        Text(`Item ${this.item} ReusableComponentTwo`)
          .fontSize(20)
          .margin({ left: 10 })
      }
    }
    .margin({ left: 10, right: 10 })
  }
}
```
![](figures/v1_v2_reusable_limit.png)

**Composite**

There are multiple differences between reusable components, but they usually share common child components. After the three reusable components are converted into the [@Builder](./arkts-builder.md) function in composite mode, the shared child components are placed under the parent component **MyComponentV2**. When these child components are reused, the cache pool is shared at the parent component level to reduce resource consumption during component creation.

<!-- @[reusable_group_type_scene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/pages/reusablemigration/ReusableGroupTypeScene.ets) -->

``` TypeScript
@Entry
@ComponentV2
struct MyComponentV2 {
  // List data source
  private data: string[] = [];

  // Initialize the list data.
  aboutToAppear() {
    for (let i = 0; i < 1000; i++) {
      this.data.push(i.toString());
    }
  }

  // The implementation of itemBuilderOne as a reusable component is not shown. The following shows the implementation after converting it to a Builder.
  // Combination 1: contains child components A, B, and C.
  @Builder
  itemBuilderOne(item: string) {
    Column() {
      ChildComponentA({ item: item })
      ChildComponentB({ item: item })
      ChildComponentC({ item: item })
    }
  }

  // The implementation after converting itemBuilderTwo to a Builder.
  // Combination 2: contains child components A, C, and D.
  @Builder
  itemBuilderTwo(item: string) {
    Column() {
      ChildComponentA({ item: item })
      ChildComponentC({ item: item })
      ChildComponentD({ item: item })
    }
  }

  // The implementation after converting itemBuilderThree to a Builder.
  // Combination 3: contains child components A, B, and D.
  @Builder
  itemBuilderThree(item: string) {
    Column() {
      ChildComponentA({ item: item })
      ChildComponentB({ item: item })
      ChildComponentD({ item: item })
    }
  }

  build() {
    List({ space: 40 }) {
      Repeat(this.data)
        .virtualScroll()
        .each((ri) => {
          ListItem() {
            // Select different combination layouts based on the index.
            if (ri.index % 3 === 0) {
              this.itemBuilderOne(ri.item)
            } else if (ri.index % 5 === 0) {
              this.itemBuilderTwo(ri.item)
            } else {
              this.itemBuilderThree(ri.item)
            }
          }
        })
    }
    .width('100%')
    .height('100%')
    .cachedCount(0)
  }
}

// Reusable component A, containing text and an image grid.
@ReusableV2
@ComponentV2
struct ChildComponentA {
  // Receive the sequence number passed in from outside.
  @Param item: string = '';

  // Callback when the component is reused. Remove it if no additional modification to state variables is required.
  aboutToReuse() {
    console.info(`ChildComponentA Reuse ${this.item}`);
  }

  // Callback when the component is recycled.
  aboutToRecycle(): void {
    console.info(`ChildComponentA ${this.item} Recycle`);
  }

  build() {
    Column() {
      // Display the component identifier text.
      Text(`Item ${this.item} Child Component A`)
        .fontSize(20)
        .margin({ left: 10 })
        .fontColor(Color.Blue)
      // Use a grid to display multiple images.
      Grid() {
        ForEach((new Array(20)).fill(''), (item: string, index: number) => {
          GridItem() {
            // Replace the content of the displayed image. The following uses app.media.startIcon as an example.
            Image($r('app.media.startIcon'))
              .height(20)
          }
        })
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr') // Five-column equal-width layout.
      .rowsTemplate('1fr 1fr 1fr 1fr') // Four-row equal-height layout.
      .columnsGap(10)
      .width('90%')
      .height(160)
    }
    .margin({ left: 10, right: 10 })
    .backgroundColor(0xFAEEE0)
  }
}

// Reusable component B, displaying red text.
@ReusableV2
@ComponentV2
struct ChildComponentB {
  // Receive the sequence number passed in from outside.
  @Param item: string = '';

  build() {
    Row() {
      Text(`Item ${this.item} Child Component B`)
        .fontSize(20)
        .margin({ left: 10 })
        .fontColor(Color.Red)
    }
    .margin({ left: 10, right: 10 })
  }
}

// Reusable component C, displaying green text.
@ReusableV2
@ComponentV2
struct ChildComponentC {
  // Receive the sequence number passed in from outside.
  @Param item: string = '';

  build() {
    Row() {
      Text(`Item ${this.item} Child Component C`)
        .fontSize(20)
        .margin({ left: 10 })
        .fontColor(Color.Green)
    }
    .margin({ left: 10, right: 10 })
  }
}

// Reusable component D, displaying orange text.
@ReusableV2
@ComponentV2
struct ChildComponentD {
  // Receive the sequence number passed in from outside.
  @Param item: string = '';

  build() {
    Row() {
      Text(`Item ${this.item} Child Component D`)
        .fontSize(20)
        .margin({ left: 10 })
        .fontColor(Color.Orange)
    }
    .margin({ left: 10, right: 10 })
  }
}
```
![](figures/v1_v2_reusable_group.png)
