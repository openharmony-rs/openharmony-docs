# switch/case:条件渲染

在静态ArkTS中，UI内容可以使用switch语句根据整型表达式的值选择多个代码段，实现条件渲染。

> **说明：**
>
> 从API version 20开始，仅支持在静态ArkTS中用于条件渲染控制。

## 语法

```typescript
switch (condition) {  // condition （控制条件：只能为char 、有符号或无符号整型，或枚举）
    case constant:    // constant：常量表达式
        expression;   // expression 可以为任何执行语句
    default:          // 默认条件，case中的语句都不满足时，会执行default的expression
        expression;   // expression可以为任何执行语句
}
```

## 使用规则

- switch语句的condition只能为整型或者可以明确转为整型的类型（如char、short等）。
- switch语句的condition可以使用状态变量或者常规变量（状态变量的值改变会实时渲染UI，而常规变量则不会）。
- switch的执行语句expression可以是构建组件或者执行其他逻辑，当为构建组件时，必须在容器组件中使用，通过condition进行条件渲染控制，构建不同的子组件。
- 条件渲染语句在涉及到组件的父子关系时是“透明”的，父组件和子组件之间的条件渲染语句不影响父组件关于子组件使用的限制。例如，某些容器组件限制子组件的类型或数量。将条件渲染语句用于这些组件内时，这些限制同样适用于条件渲染语句内创建的组件。具体而言，[Grid](../../reference/apis-arkui/arkui-ts/ts-container-grid.md)容器组件的子组件仅支持[GridItem](../../reference/apis-arkui/arkui-ts/ts-container-griditem.md)组件。在Grid内使用条件渲染语句时，条件渲染语句内仅允许使用GridItem组件。
- 每个分支内部的构建函数必须遵循构建函数的规则，并创建一个或多个组件。无法创建组件的空构建函数会产生语法错误。

## 更新规则

当switch语句的condition使用状态变量时，condition值改变会进行更新，更新步骤如下：
1. 评估switch的condition，如果没有变化，无需执行以下步骤。如果有变化，则执行后续步骤。
2. 删除此前构建的所有子组件。
3. 执行满足常量表达式的执行语句，将生成的子组件添加到执行switch语句的容器组件中。如果缺少满足常量表达式的执行语句，则执行default的执行语句，没有default则不会执行任何语句。

## 使用限制

- 该语法仅在静态ArkTS中支持，动态ArkTS不支持。
- 当case分支的执行语句是组件时，调用switch的组件必须是容器组件。否则，切换到该case分支时，由于非容器组件不能挂载组件，应用会直接崩溃。

## 使用场景

使用switch语句进行条件渲染

```typescript
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct MyStateSample {
  @State stateVar: int = 1;

  build() {
    Column() {
      switch(this.stateVar) {
        case 1:
          Text('show text1')
          break;  // 不加break会执行下一个case分支
        case 2:
          Text('show text2');
          break;
        case 3:
          Text('show text3');
          break;
        default:
          Text('show default');
          break;
      }
      Button('change stateVar')
        .onClick((e: ClickEvent) => {
          this.stateVar = (this.stateVar + 1) % 4;
        })
    }
    .width('100%')
    .height('100%')
  }
}
```
上述switch示例包含3个case分支和一个default分支。当condition满足case分支的常量表达式时，将执行对应case分支。如果所有case分支都不满足，将执行default分支。