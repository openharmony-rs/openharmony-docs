# ArkTS1.2 Repeat组件迁移规范

本指南介绍ArkTS1.2语言中Repeat组件的功能变更和迁移规范。完整Demo见[ArkTS1.2的写法差异示例](#arkts12的写法差异示例)。

> **说明：**
>
> 从API version 20起引入ArkTS1.2。

## 迁移说明

- ArkTS1.2需要加入模块导入语句：
```ts
import { Repeat, RepeatItem } from '@ohos.arkui.component';
```

- ArkTS1.2中Repeat()强制要求声明数组类型`<T>`。

## API变更

ArkTS1.2新增API：[disableVirtualScroll](../../reference/apis-arkui/arkui-ts/ts-rendering-control-repeat.md#virtualscrolloptions对象说明)。

## 规格变更

### 默认懒加载

当Repeat属性`.virtualScroll()`缺省时：<br>
1）ArkTS1.1中，渲染方式默认为全量加载，需要添加`.virtualScroll()`开启懒加载。<br>
2）ArkTS1.2中，渲染方式默认为懒加载。需要设置`disableVirtualScroll`配置项为true关闭懒加载，缺省时默认值为false。

> **注意：**
>
> 关闭懒加载后，Repeat仅有`.each()`和`.key()`属性生效，其他懒加载特有的功能（如template、totalCount、onLazyLoading等）不可用。

## 写法变更

### ArkTS1.2的写法差异示例

1. 全量加载模式

**ArkTS1.1**

```ts
@Entry
@Component
struct Repeat_1_1 {
  @State simpleList: Array<string> = ['one', 'two', 'three'];

  build() {
    Column() {
      Repeat(this.simpleList)
        .each((ri) => { // RepeatItem可以省略
          Text(`#${ri.index}: ${ri.item}`)
        })
        .key((item: string) => item)
    }
  }
}
```

**ArkTS1.2**

```ts
import { Entry, Component, Column, Text, Repeat, RepeatItem } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Repeat_1_2 {
  @State simpleList: Array<string> = ['one', 'two', 'three'];

  build() {
    Column() {
      Repeat<string>(this.simpleList) // 必须声明数据类型<T>
        .each((ri: RepeatItem<string>) => { // RepeatItem可以省略
          Text(`#${ri.index}: ${ri.item}`)
        })
        .key((item: string) => item)
        .virtualScroll({
          disableVirtualScroll: true // 关闭懒加载
        })
    }
  }
}
```

2. 懒加载模式

**ArkTS1.1**

```ts
@Entry
@Component
struct Repeat_Virtual_1_1 {
  @State simpleList: Array<string> = [];

  aboutToAppear(): void {
    for (let i = 0; i < 50; i++) {
      this.simpleList.push(`data_${i}`); // 向数组中添加一些数据
    }
  }

  build() {
    Column() {
      List() {
        Repeat(this.simpleList) // 数据类型<T>可以省略
          .each((ri) => { // RepeatItem可以省略
            ListItem() {
              Text(`#${ri.index}: ${ri.item}`).fontColor(Color.Red)
            }
          })
          .key((item: string) => item)
          .virtualScroll() // 懒加载模式必须声明.virtualScroll()
          .template('ttype_a', (ri) => { // RepeatItem可以省略
            ListItem() {
              Text(`#${ri.index}: ${ri.item}`).fontColor(Color.Blue)
            }
          }, { cachedCount: 1 })
          .templateId((item: string, index: number) => index % 2 === 0 ? 'ttype_a' : '')
      }.height('40%')
    }
  }
}
```

**ArkTS1.2**

```ts
import { Entry, Component, Column, Text, Color, Repeat, RepeatItem, List, ListItem } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Repeat_Virtual_1_2 {
  @State simpleList: Array<string> = new Array<string>();

  aboutToAppear(): void {
    for (let i = 0; i < 50; i++) {
      this.simpleList.push(`data_${i}`); // 向数组中添加一些数据
    }
  }

  build() {
    Column() {
      List() {
        Repeat<string>(this.simpleList) // 必须声明数据类型<T>
          .each((ri: RepeatItem<string>) => { // RepeatItem可以省略
            ListItem() {
              Text(`#${ri.index}: ${ri.item}`).fontColor(Color.Red)
            }
          })
          .key((item: string) => item)
          .virtualScroll() // 可以省略
          .template('ttype_a', (ri: RepeatItem<string>) => { // RepeatItem可以省略
            ListItem() {
              Text(`#${ri.index}: ${ri.item}`).fontColor(Color.Blue)
            }
          }, { cachedCount: 1 })
          .templateId((item: string, index: number) => index % 2 === 0 ? 'ttype_a' : '')
      }.height('40%')
    }
  }
}
```