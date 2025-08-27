# UI数据互操作

## 介绍

在ArkTS1.2中，与ArkTS1.1相关UI数据交互主要涉及以下几种场景：：

1. 在ArkTS1.2上下文中使用ArkTS1.1的类型数据。
2. 在ArkTS1.2上下文中使用ArkTS1.1的[@Observed](../ui/state-management/arkts-observed-and-objectlink.md)和[@ObservedV2](../ui/state-management/arkts-new-observedV2-and-trace.md)装饰器修饰的类型数据。
3. 在ArkTS1.2上下文中使用ArkTS1.1的SDK类型数据，如[FrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md)，[UIContext](../reference/apis-arkui/js-apis-arkui-UIContext.md)。

## 使用ArkTS1.1的SDK类型数据

### 通过transferStatic接口转换为ArkTS1.2类型

针对开发者无法手动从ArkTS1.1对象创建ArkTS1.2对象的情况，ArkUI开发框架通过[transferStatic](../reference/apis-arkts/js-apis-transfer.md)接口提供动静类型转换，如下示例代码展示了相关用法。

- 创建ArkTS1.1子模块dynamic_module，在动态模块中创建并导出自定义组件。有关如何创建子模块的详细信息，请参阅共享包（[HAR](har-package.md)）说明。
  ```
  @Component
  export struct Child {
    onClick?: (value: Object) => void;
  
    build() {
      Column() {
        Text('Event Transfer')
      }.onClick((value: ClickEvent) => {
        if (this.onClick) {
          // 触发ArkTS1.2回调函数
          this.onClick(value);
        }
      })
    }
  }
  ```

- 在ArkTS1.2模块中配置相关模块依赖后，导入动态模块。如何导入和使用子模块，请参考共享包（[HAR](har-package.md)）说明。本指南不进行详细阐述。
  ```
  'use static'
  import { Entry, Component, Column, ClickEvent } from '@ohos.arkui.component';
  import transfer from '@ohos.transfer';
  import { Child } from 'dynamic_module';

  @Entry
  @Component
  struct Parent {
  
    handleChildEvent(value: Any) {
      // 通过transferStatic转换ArkTS1.1事件类型对象为ArkTS1.2对象
      const clickEvent: ClickEvent = transfer.transferStatic(value, 'ArkUI.ClickEvent') as ClickEvent;
      console.info(`click info: x: ${clickEvent.x}, y: ${clickEvent.y}`);
    }
  
    build() {
      Column() {
        // 传递回调事件给ArkTS1.1自定义组件
        Child({onClick: this.handleChildEvent})
      }
    }
  }
  ```

支持系统动静态转换接口的UI相关SDK类型包括：FrameNode，NavDestinationInfo，NavigationInfo，RouterPageInfo，Resource，DragEvent，KeyEvent，TouchEvent，MouseEvent，AxisEvent，ClickEvent，HoverEvent，ScrollableTargetInfo, DrawableDescriptor，ColorFilter, LengthMetrics，ColorMetrics, UIContext等，详情请参见[transferStatic接口](../reference/apis-arkts/js-apis-transfer.md)文档。
