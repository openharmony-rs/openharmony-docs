# memorizeUpdatedState接口：并行化UI创建场景下的状态变量拷贝接口
开发者可以使用memorizeUpdatedState接口在[并行化UI创建组件树](../../reference/apis-arkui/js-apis-arkui-Parallelize.md)时拷贝状态变量。

## 概述

在[ParallelizeUI](../../reference/apis-arkui/js-apis-arkui-Parallelize.md)的并行化创建环境中，不能直接使用外层的状态变量。memomemorizeUpdatedState提供了一种机制，将外层状态变量拷贝成可在并行化中安全使用的状态变量副本。状态变量更新时，副本也会随着更新。

## 导入模块

```ts
import { memorizeUpdatedState } from '@ohos.arkui.stateManagement'
```

## MemoState
表示一个状态变量包装对象，封装类型为 T 的值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型    | 必填 | 说明                  |
| -------- | ------ | ---- |--------------------- |
| value    | T      | 是   | 当前状态变量的值。 |



## RememberFactory
无参函数，返回类型为 T。

type RememberFactory\<T> = () => T

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

> **说明：**
> 如果函数体中使用了状态变量，则在状态变量更新时，函数会重新执行以返回新的值。

## memorizeUpdatedState
创建一个状态变量，用于更新UI。

memorizeUpdatedState\<T>(factory: RememberFactory\<T>): MemoState\<T>

**参数：**

| 参数名    | 类型    | 必填 | 说明                  |
| -------- | ------ | ---- |--------------------- |
| factory    | RememberFactory\<T>       | 是   | 返回value的函数。如果该函数中使用了状态变量，状态变量更新时，该函数会重新执行，返回新的value。 |

**返回值：**

| 类型 | 描述                   |
| ---- | ---------------------- |
| MemoState\<T> | 代表状态变量，封装给定类型的值。 |

**示例：**

```ts
'use static'

import { Entry, Component, Button, ClickEvent, Column, Text } from '@ohos.arkui.component';
import { State, memorizeUpdatedState } from '@ohos.arkui.stateManagement'
import { ParallelOption, ParallelizeUI } from "@ohos.arkui.Parallelize"

class PageInfo {
  name:string = ''
  id:int = 0
  constructor(name:string, id:int) {
    this.name = name
    this.id = id
  }
}

@Entry
@Component
struct MyStateSample {
  @State stateVar: string = 'state var';
  @State page: PageInfo = new PageInfo('页面', 1);
  changeValue() {
    this.page = new PageInfo('页面状态更新', 2);
  }

  build() {
    Column(undefined) {
      let prop = memorizeUpdatedState<PageInfo>(() => {
        return new PageInfo(this.page.name, this.page.id)
      })
      ParallelizeUI() {
        Column() {
          Text(prop.value.name).fontSize('20')
        }
      }
      Button(this.message).backgroundColor('#FFFF00FF')
        .onClick((e: ClickEvent) => {
          this.changeValue();
        })
      Child({stateVar: this.stateVar} as __Options_Child)
    }
  }
}
```

