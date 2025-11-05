# UI调优
本章节主要介绍UI的dump和调优能力，用于提高开发效率和优化开发者体验。

为提升开发者定位状态管理问题的效率，UI提供针对状态变量的[hidumper](../../application-dev/dfx/hidumper.md)功能，将状态变量的内部信息提供给开发者，帮助开发者深入了解状态变量和UI组件的变化过程，提升开发高性能应用的效率。

## 状态管理hidumper能力
状态管理接入hidumper，支持通过-element选项获取状态变量、自定义组件树等信息，方便开发者了解状态变量影响的UI范围，便于写出高性能应用代码。

具体例子如下：下面的例子为嵌套两层子组件的典型示例，使用了装饰器[\@State](./state-management-static/arkts-static-state.md)和[\@Link](./state-management-static/arkts-static-link.md)。开发者可组合使用上述命令，展示前端组件树、自定义组件和状态变量等信息。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { State, Link } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Page {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text('Parent:' + this.message).fontSize(20).onClick((e: ClickEvent) => {
        this.message += '1';
      })
      Child({ message: this.message })
    }
  }
}

@Component
struct Child {
  @Link message: string;

  build() {
    Column() {
      Text('Child:' + this.message).fontSize(20)
      GrandChild({ message: this.message })
    }
  }
}

@Component
struct GrandChild {
  @Link message: string;

  build() {
    Column() {
      Text('GrandChild: ' + this.message).fontSize(20)
    }
  }
}
```

步骤1：获取当前激活窗口的id。

```shell
hdc shell hidumper -s WindowManagerService -a '-a'
```

步骤2：执行打印状态变量dump信息的命令。假定激活的窗口id是90，可通过下面的命令打印出所有组件树上的组件信息。

```shell
hdc shell hidumper -s WindowManagerService -a '-w 90 -element -c' > arkui.dump
```

执行上述命令后，查看dump文件，并搜索JsView关键字，以查看自定义节点信息，含义如下：

| Dump属性      | 含义                 |
| ------------- | -------------------- |
| ID            | 自定义组件节点ID。   |
| Depth         | 组件深度。           |
| InstanceId    | 所属的UI实例。       |
| ComponentName | 自定义节点名称。     |
| isV2          | 是否为V2自定义组件。 |
| decorator     | 使用的装饰器。       |
| propertyName  | 装饰器变量名称。     |
| value         | 装饰器的值。         |

```ts
|-> JsView childSize:1
    | ID: 2
    | Depth: 5
    | InstanceId: 100000
    | AccessibilityId: 2
    | ComponentName: "entry.src.main.ets.pages.Index.Page"
    | isV2: false
    | isFreezeAllowed: 
    | isViewActive: 
    | -----start print decoratorInfo
    | decorator:"@State" propertyName:"message" value:"hello world"
```

## Trace调试能力

ArkUI内部针对关键的UI处理流程添加了Trace信息，帮助开发者通过Trace工具观测应用的UI耗时，辅助定位问题。详细Trace说明及案例参考：[常用Trace使用指导](../performance/common-trace-using-instructions.md)。

## Inspector调试能力

ArkUI Inspector是DevEco Studio内置的页面布局检查工具，帮助开发者查看应用的UI层级结构、组件属性和布局效果。详细Inspector使用方法及案例参考：[页面布局检查器ArkUI Inspector使用指导](../performance/arkUI-inspector.md)。
