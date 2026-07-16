# ArkUI子系统变更说明

## cl.arkui.1 List组件onScrollVisibleContentChange事件行为变更

**访问级别**

公共能力

**变更原因**

[List](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-list.md)组件[onScrollVisibleContentChange](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-list.md#onscrollvisiblecontentchange12)事件索引输出规则与空列表参数设计定义不符，原列表从有数据切换成没有数据时复用旧start和end参数，优化后该场景start和end参数的index成员均为-1，itemGroupArea和itemIndexInGroup成员均为undefined，符合空列表参数设计定义。

**变更影响**

此变更涉及应用适配。

- 变更前：[List](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-list.md)组件[onScrollVisibleContentChange](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-list.md#onscrollvisiblecontentchange12)事件从有子组件切换到没有子组件时，上报的start和end参数均为原值。

- 变更后：[List](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-list.md)组件[onScrollVisibleContentChange](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-list.md#onscrollvisiblecontentchange12)事件从有子组件切换到没有子组件时，上报的start和end参数的index成员均为-1，itemGroupArea和itemIndexInGroup成员均为undefined。

```ts
@Entry
@Component
struct ListExample {
  @State listData: string[] = ['item1', 'item2', 'item3'];

  build() {
    Column() {
      Button('清空列表数据')
        .onClick(() => {
          this.listData = [];
        })
      List() {
        ForEach(this.listData, (item: string) => {
          ListItem() {
            Text(item)
              .width('100%')
              .height(100)
              .textAlign(TextAlign.Center)
          }
        })
      }
      .width('100%')
      .height('100%')
      .onScrollVisibleContentChange((start, end) => {
        console.info(`start: ${start.index}, end: ${end.index}`);
        // 变更前：当listData从['item1', 'item2', 'item3']变为[]时，打印 start: 0, end: 2
        // 变更后：当listData从['item1', 'item2', 'item3']变为[]时，打印 start: -1, end: -1
      })
    }
  }
}
```

**起始 API Level**

12

**变更发生版本**

从OpenHarmony SDK 7.0.0.28开始。

**变更的接口/组件**

[onScrollVisibleContentChange](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-list.md#onscrollvisiblecontentchange12)事件。

**适配指导**

如果应用依赖[onScrollVisibleContentChange](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-list.md#onscrollvisiblecontentchange12)事件的start和end参数来判断列表内容变化，当列表从有内容变为空时，开发者需要适配start和end参数的index为-1的场景。例如，开发者需要在事件回调中判断index是否为-1，以区分列表为空的情况。

```ts
@Entry
@Component
struct ListExample {
  @State listData: string[] = ['item1', 'item2', 'item3'];

  build() {
    Column() {
      Button('清空列表数据')
        .onClick(() => {
          this.listData = [];
        })
      List() {
        ForEach(this.listData, (item: string) => {
          ListItem() {
            Text(item)
              .width('100%')
              .height(100)
              .textAlign(TextAlign.Center)
          }
        })
      }
      .width('100%')
      .height('100%')
      .onScrollVisibleContentChange((start, end) => {
        // 适配指导：判断列表是否为空
        if (start.index === -1 && end.index === -1) {
          console.info('列表为空');
        } else {
          console.info(`可见列表项范围：start: ${start.index}, end: ${end.index}`);
        }
      })
    }
  }
}
```