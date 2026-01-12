# @Consumer

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 23开始，支持该装饰器。

@Provider和@Consumer搭配使用，用于状态管理V2中，实现跨组件层级的数据双向同步。@Consumer修饰数据消费方，获取数据源数据。

在ArkTS-Sta中使用时，开发指南参考：[\@Provider装饰器和\@Consumer装饰器：跨组件层级双向同步（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-new-provider-and-consumer.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                               |
| ------ | ------ | ---- | ---------------------------------- |
| alias  | string | 否   | 用于设置别名，缺省时默认为变量名。 |

**示例：**

```ts
'use static'

import { Entry, ComponentV2, Column, Text } from '@ohos.arkui.component';
import { Provider, Consumer } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Index {
  @Provider() str: string = 'aaa';
  build() {
    Column() {
      Child()
    }
  }
}

@ComponentV2
struct Child {
  @Consumer() str: string = '';
  build() {
    Column() {
      Text(`${this.str}`)
    }
  }
}
```

