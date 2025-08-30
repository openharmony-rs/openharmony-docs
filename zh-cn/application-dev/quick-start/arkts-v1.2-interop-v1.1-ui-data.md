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

## 常见问题

### ArkTS1.1对象继承ArkTS1.2使用@Observed装饰的对象时@Track属性不生效

规格描述：基于语言互操作能力，ArkTS1.1对象可以继承ArkTS1.2对象。当ArkTS1.2对象使用@Observed装饰，并且属性标记@Track时，该对象在ArkTS1.1和ArkTS1.2中的行为会有差异。在ArkTS1.2的UI上下文使用时，针对ArkTS1.2基类对象中的非@Track属性修改，会遵循[@Observed数据刷新规格](../../third-party-cases/observed-and-objectlink.md)，UI不刷新。在ArKTS1.1的UI上下文使用时，针对ArkTS1.2基类对象中的非@Track属性修改，UI会刷新。

根因：当ArkTS1.1对象继承ArkTS1.2对象时，在ArkTS1.1上下文中会被当做普通动态类型对象，无法判断该对象内部是否包含静态@Track属性，故会按照普通动态类型对象的监听规则，对该对象的成员进行修改时都会进行UI更新。

相关示例如下所示：

- 创建ArkTS1.2子模块static_module，在静态模块中创建并导出静态数据类型。
  ```
  'use static'
  import { Observed, Track } from '@ohos.arkui.stateManagement';

  @Observed
  export class StaticData {
    @Track
    track: string = 'track';
    nonTrack: string = 'nonTrack';
  }
  ```

- 创建ArkTS1.1子模块dynamic_module，在动态模块中创建并导出自定义组件。
  ```
  import { StaticData } from 'static_module'

  @Component
  export struct Child {
    @State stateVar: DynamicData = new DynamicData();

    build() {
      Column() {
        Button('change stateVar.track: ' + this.stateVar.track)
          .onClick(() => {
            this.stateVar.track += '!';
          })

        // 在ArkTS1.1上下文改变ArkTS1.2基类的非@Track属性，仍会刷新1.1UI
        Button('change stateVar.nonTrack: ' + this.stateVar.nonTrack)
          .onClick(() => {
            this.stateVar.nonTrack += '!';
          })

        // 在ArkTS1.1上下文改变ArkTS1.1子类的属性，刷新1.1UI
        Button('change stateVar.dynamic: ' + this.stateVar.dynamic)
          .onClick(() => {
            this.stateVar.dynamic += '!';
          })
      }
    }
  }

  export class DynamicData extends StaticData {
    dynamic: string = 'dynamic';
  }
  ```

- 在ArkTS1.2模块中配置相关模块依赖后，导入动态模块。
  ```
  'use static'
  import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import { Child, DynamicData } from 'dynamic_module';

  @Entry
  @Component
  struct Parent {
    @State stateVar: DynamicData = new DynamicData();

    build() {
      Column() {
        Button('change stateVar.track: ' + this.stateVar.track)
          .onClick((e: ClickEvent) => {
            this.stateVar.track += '!';
          })

        // 在ArkTS1.2上下文改变ArkTS1.2基类的非@Track属性，UI不刷新
        Button('change stateVar.nonTrack: ' + this.stateVar.nonTrack)
          .onClick((e: ClickEvent) => {
            this.stateVar.nonTrack += '!';
          })

        // 在ArkTS1.2上下文改变ArkTS1.1子类的属性(非@Track装饰)，UI不刷新
        Button('change stateVar.dynamic: ' + this.stateVar.dynamic)
          .onClick((e: ClickEvent) => {
            this.stateVar.dynamic += '!';
          })

        Child({stateVar: this.stateVar})
      }
    }
  }
  ```
