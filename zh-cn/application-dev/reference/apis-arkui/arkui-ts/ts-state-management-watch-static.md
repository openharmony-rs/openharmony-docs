# @Watch

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@Watch装饰器用于状态管理V1中，监听状态变量的变化。

在静态语言上下文中使用时，开发指南参考：[@Watch装饰器：状态变量更改通知（ArkTS-ST）](../../../ui/state-management/arkts-static-watch.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                     |
| ------ | ------ | ---- | ---------------------------------------- |
| value  | string | 是   | 用于监听的回调函数名，内容由开发者指定。 |

**示例：**

```ts
import { Entry, Component, Column, Button, ClickEvent, Text } from '@ohos.arkui.component';
import { State, Watch } from '@ohos.arkui.stateManagement';
@Entry
@Component
struct Index {
  @State @Watch('onChange') count: number = 0;
  @State total: number = 0;

  onChange(propertyName: string): void {
    this.total += this.count;
  }

  build() {
    Column() {
      Text(`Total: ${this.total}`)
      Button('change')
        .onClick((e: ClickEvent) => {
          this.count++;
        })
    }
  }
}
```

