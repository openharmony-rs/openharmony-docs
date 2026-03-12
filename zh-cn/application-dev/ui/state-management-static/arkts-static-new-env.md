# \@Env：环境变量

在多设备开发的场景中，开发者可以使用\@Env装饰器监听系统环境变量的改变，并根据系统环境变量来进行相应的场景判断，以减少不同设备间的适配逻辑和重复开发。

> **说明：**
>
> 从API version 24开始，\@Env支持在[\@Component](./arkts-static-create-component.md)和[\@ComponentV2](./arkts-static-componentv2.md)中使用。

## 概述

\@Env是响应式系统环境变量装饰器，其功能包括：
- 根据入参读取相应的环境变量信息，详情见[\@Env支持参数](#env支持参数)。目前支持以下几种环境变量：
  - [SystemProperties.BREAK_POINT](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties)，用于获取窗口不同宽高阈值下对应的断点值信息。
  - [SystemProperties.WINDOW_SIZE](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties)，用于获取窗口的大小信息，单位为vp。
  - [SystemProperties.WINDOW_SIZE_PX](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties)，用于获取窗口的大小信息，单位为px。
  - [SystemProperties.WINDOW_AVOID_AREA](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties)，用于获取窗口的避让区域信息，单位为vp。
  - [SystemProperties.WINDOW_AVOID_AREA_PX](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties)，用于获取窗口的避让区域信息，单位为px。
- 系统环境变量改变时，通知\@Env装饰的变量更新，并触发\@Env关联组件刷新，以实现界面内容的同步更新。
- \@Env装饰的变量不允许开发者初始化。\@Env会返回给开发者可观察的环境变量类的实例。开发者如果想监听环境变量的变化，可以使用[addMonitor](./arkts-static-new-addmonitor-clearmonitor.md)，具体示例见[在\@ComponentV2中使用\@Env](#在componentv2中使用env)。

## \@Env支持参数

@Env支持的参数请参考[SystemProperties枚举类型说明](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties)。

## \@Env和Environment能力对比

\@Env和[Environment](./arkts-static-environment.md)都是系统环境变量相关，但两者能力有较大的不同，具体能力对比见下表。

| 能力 | \@Env | Environment |
| ------------------ | ------------------ | ------------------ |
| 起始API version | 从API version 24开始支持。 | 从API version 23开始支持。 |
| 支持参数 | [SystemProperties的枚举值](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties) | 支持`languageCode`等参数，详情见[Environment内置参数](./arkts-static-environment.md#environment内置参数)。 |
| 使用形式 | \@Env为装饰器，可声明在\@Component或\@ComponentV2中，获取对应参数的环境变量信息。 | 通过[envProp](../../reference/apis-arkui/arkui-ts/ts-state-management.md#envprop10)等接口获取当前应用的环境变量，并存入[AppStorage](./arkts-static-appstorage.md)中，开发者可通过AppStorage的接口访问系统环境变量的值，具体例子见[从UI中访问Environment参数](./arkts-static-environment.md#从UI中访问Environment参数)。 |
| 是否有响应式能力 | 有，当系统环境变量变化时，会通知\@Env装饰的环境变量的改变，并通知\@Env关联组件刷新。 | 无，系统环境变量变化时，不会通知Environment改变。 |

## 限制条件

- \@Env仅支持在\@Component和\@ComponentV2中使用，否则会有编译时报错。如果开发者绕过编译时检查，则会有运行时报错。

  ```ts
  'use static'

  import { Env, Component, Entry, SystemProperties } from '@kit.ArkUI';
  import uiObserver from '@ohos.arkui.observer';

  class Info {
    @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo; // 错误用法，编译时报错
  }

  @Entry
  @Component
  struct Index {
    @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo; // 正确用法

    build() {
    }
  }
  ```

- \@Env装饰的变量为只读属性，不允许开发者进行初始化或赋值操作，否则会有编译时报错。如果开发者绕过编译时检查，则会有运行时报错。

  ```ts
  'use static'

  import { Env, Component, Entry, SystemProperties, Text, Column, Button } from '@kit.ArkUI';
  import uiObserver from '@ohos.arkui.observer';

  @Entry
  @Component
  struct Index {
    @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo =
      new uiObserver.WindowSizeLayoutBreakpointInfo(); // 错误用法，编译时报错

    build() {
      Column() {
        Text(`breakpoint height ${this.breakpoint.heightBreakpoint}`)
          .fontSize(20)
        Text(`breakpoint width ${this.breakpoint.widthBreakpoint}`)
          .fontSize(20)
        Button('change breakpoint')
          .onClick(() => {
            this.breakpoint = new uiObserver.WindowSizeLayoutBreakpointInfo(); // 错误用法，编译时报错
          })
      }
    }
  }
  ```

- \@Env当前支持[SystemProperties的枚举值](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties)。若使用不支持的参数，将触发编译时报错。

  ```ts
  'use static'

  import { Env, Component, Entry, SystemProperties, Text } from '@kit.ArkUI';
  import uiObserver from '@ohos.arkui.observer';

  @Entry
  @Component
  struct Index {
    @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo; // 正确写法
    @Env('unsupported_key') breakpoint2: uiObserver.WindowSizeLayoutBreakpointInfo; // 错误写法，@Env非法入参，编译时报错。

    build() {
      Text(`breakpoint2 width: ${this.breakpoint2.widthBreakpoint} height: ${this.breakpoint2.heightBreakpoint}`)
    }
  }
  ```

- \@Env使用不同的key值时，装饰的变量类型必须一一对应，否则会有编译时报错。
  - \@Env使用`SystemProperties.BREAK_POINT`时，装饰的变量类型必须为`uiObserver.WindowSizeLayoutBreakpointInfo`类型。
  - \@Env使用`SystemProperties.WINDOW_SIZE`时，装饰的变量类型必须为`window.SizeInVP`类型。
  - \@Env使用`SystemProperties.WINDOW_SIZE_PX`时，装饰的变量类型必须为`window.Size`类型。
  - \@Env使用`SystemProperties.WINDOW_AVOID_AREA`时，装饰的变量类型必须为`window.UIEnvWindowAvoidAreaInfoVP`类型。
  - \@Env使用`SystemProperties.WINDOW_AVOID_AREA_PX`时，装饰的变量类型必须为`window.UIEnvWindowAvoidAreaInfoPX`类型。

  ```ts
  'use static'

  import { Env, Component, Entry, SystemProperties } from '@kit.ArkUI';
  import uiObserver from '@ohos.arkui.observer';

  @Entry
  @Component
  struct Index {
    @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo; // 正确写法
    @Env(SystemProperties.BREAK_POINT) breakpoint2: string; // 错误写法，@Env使用SystemProperties.BREAK_POINT时仅支持装饰WindowSizeLayoutBreakpointInfo类型

    build() {
    }
  }
  ```

- \@Env只能单独使用，不能和其他V1V2状态变量装饰器或@Require联用，否则会有编译时报错。

  ```ts
  @Env(SystemProperties.BREAK_POINT) breakpoint1: uiObserver.WindowSizeLayoutBreakpointInfo; // 正确写法
  @State @Env(SystemProperties.BREAK_POINT) breakpoint2: uiObserver.WindowSizeLayoutBreakpointInfo; // 错误写法，编译时报错
  @Require @Env(SystemProperties.BREAK_POINT) breakpoint3: uiObserver.WindowSizeLayoutBreakpointInfo; // 错误写法，编译时报错
  @Local @Env(SystemProperties.BREAK_POINT) breakpoint4: uiObserver.WindowSizeLayoutBreakpointInfo; // 错误写法，编译时报错
  ```

- \@Env装饰的变量在\@Component和\@ComponentV2传递遵循以下规则：
  - \@Env装饰的变量仅能用于初始化\@ComponentV2中@Param装饰的变量，否则会有编译时报错。
  - \@Env装饰的变量仅能用于初始化\@Component中常规变量，否则会有编译时报错。

  ```ts
  'use static'

  import { Env, Entry, Component, ComponentV2, Column, Require, Param, ObjectLink, SystemProperties } from '@kit.ArkUI';
  import uiObserver from '@ohos.arkui.observer';

  @Entry
  @Component
  struct Index {
    @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo; // 正确写法

    build() {
      Column() {
        CompV2({ breakpoint: this.breakpoint }) // 正确写法
        Comp({ breakpoint: this.breakpoint }) // 正确写法

        CompV2Invalid({ breakpoint: this.breakpoint }) // 错误写法，@Env装饰的变量仅能初始化V2的@Param变量
        CompInvalid({ breakpoint: this.breakpoint }) // 错误写法，@Env装饰的变量仅能初始化V1的常规变量
      }
    }
  }

  @ComponentV2
  struct CompV2 {
    @Require @Param breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo; // 正确写法

    build() {
    }
  }

  @ComponentV2
  struct CompV2Invalid {
    @Require breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo; // 错误写法

    build() {
    }
  }

  @Component
  struct Comp {
    @Require breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo; // 正确写法

    build() {
    }
  }

  @Component
  struct CompInvalid {
    @ObjectLink breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo; // 错误写法

    build() {
    }
  }
  ```

## \@Env初始化流程

\@Env变量不允许开发者初始化，其值由框架根据当前窗口的环境变量自动提供，\@Env变量在被第一次读值的时候，会触发初始化。\@Env变量初始化遵循以下流程：

1. 从父组件中查找已有实例：
   - 向上递归查找父组件。
   - 如果某个父组件在同一窗口中已经初始化过相同key的\@Env变量，则直接复用该实例。
   - 若未找到，则继续向上查找，直到父组件为空。需要注意，向上查找父组件的流程会被`BuilderNode`打断。
2. 查找当前窗口的\@Env实例。
   - 如果在父组件中未找到对应的实例，则检查当前窗口是否已有相同key的\@Env变量实例。
   - 如存在，则复用该窗口内的\@Env实例。
3. 首次请求：创建新环境变量实例。
   - 若以上两步都无法得到实例，则说明当前窗口第一次读取该环境变量。
   - 框架会创建一个新的可观察环境变量实例并与当前窗口绑定，然后完成初始化。

流程图如下。

![image](../figures/env-flow.png)

基于上面流程，下面的示例中以@Env使用`SystemProperties.BREAK_POINT`为例，各个组件中的初始化如下图。

![image](../figures/env-flow2.png)

1. `Child1`初始化`@Env(SystemProperties.BREAK_POINT)`：
   - 递归查找直到父组件为空：向上查找父组件`Index`，没有\@Env对应的`SystemProperties.BREAK_POINT`实例。
   - 查找当前窗口：没有\@Env对应的`SystemProperties.BREAK_POINT`实例。
   - 创建`SystemProperties.BREAK_POINT`对应的可观察的环境变量实例，并和当前窗口绑定。
2. `GrandChild1`初始化`@Env(SystemProperties.BREAK_POINT)`：
   - 递归查找父组件，直到父组件为空：向上查找父组件`Child1`，查找到`Child1`有\@Env对应的`SystemProperties.BREAK_POINT`实例。
   - 复用`Child1`中\@Env对应的`SystemProperties.BREAK_POINT`实例。
3. `GrandChild2`初始化`@Env(SystemProperties.BREAK_POINT)`：
   - 递归查找直到父组件为空：向上查找父组件`Child2`和祖先节点`Index`，均没有\@Env对应的`SystemProperties.BREAK_POINT`实例。
   - 查找当前窗口：有\@Env对应的`SystemProperties.BREAK_POINT`实例。
   - 复用窗口中`SystemProperties.BREAK_POINT`对应的环境变量实例。

```ts
'use static'

import {
  Env,
  Entry,
  Component,
  ComponentV2,
  Column,
  Require,
  Param,
  ObjectLink,
  SystemProperties,
  Text
} from '@kit.ArkUI';
import uiObserver from '@ohos.arkui.observer';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text(`Index`)
      Child1()
      Child2()
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct Child1 {
  // 父组件Index不存在对应的@Env实例，在此处创建。
  @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;

  build() {
    Column() {
      // 打印当前窗口宽度所在的布局断点枚举值
      Text(`Child1 breakpoint width: ${this.breakpoint.widthBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口高度所在的布局断点枚举值
      Text(`Child1 breakpoint height: ${this.breakpoint.heightBreakpoint}`)
        .fontSize(20)
      GrandChild1()
    }
  }
}

@Component
struct Child2 {
  build() {
    Column() {
      GrandChild2()
    }
  }
}

@Component
struct GrandChild1 {
  // 复用Child1组件中对应的@Env实例。
  @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;

  build() {
    Column() {
      // 打印当前窗口宽度所在的布局断点枚举值
      Text(`GrandChild1 breakpoint width: ${this.breakpoint.widthBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口高度所在的布局断点枚举值
      Text(`GrandChild1 breakpoint height: ${this.breakpoint.heightBreakpoint}`)
        .fontSize(20)
    }
  }
}

@Component
struct GrandChild2 {
  // Index与Child2组件均不存在对应的@Env实例，故在此处创建。
  @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;

  build() {
    Column() {
      // 打印当前窗口宽度所在的布局断点枚举值
      Text(`GrandChild2 breakpoint width: ${this.breakpoint.widthBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口高度所在的布局断点枚举值
      Text(`GrandChild2 breakpoint height: ${this.breakpoint.heightBreakpoint}`)
        .fontSize(20)
    }
  }
}
```

## 使用场景

### 在\@ComponentV2中使用\@Env

下面的例子中：
- 在\@ComponentV2中声明\@Env，获取当前\@ComponentV2组件创建时所在窗口尺寸的布局断点信息，并用[addMonitor](./arkts-static-new-addmonitor-clearmonitor.md)监听`this.breakpoint`的属性的变化。
- 在\@ComponentV2中声明\@Env，获取当前\@ComponentV2组件创建时所在窗口的大小信息，单位为vp，并用[addMonitor](./arkts-static-new-addmonitor-clearmonitor.md)监听`this.sizeInVP`的属性的变化。
- 在\@ComponentV2中声明\@Env，获取当前\@ComponentV2组件创建时所在窗口的大小信息，单位为px，并用[addMonitor](./arkts-static-new-addmonitor-clearmonitor.md)监听`this.sizeInPX`的属性的变化。
- 将\@Env装饰的变量传递给`CompV2`中[\@Param](./arkts-static-new-param.md)装饰的变量和`Comp`中的常规变量。
- 点击`Button('Landscape')`和`Button('Portrait')`切换横竖屏，`Index`、`CompV2`和`Comp`关联组件进行对应的刷新，`orientationChange`被触发监听回调。

```ts
'use static'

import {
  Env,
  Entry,
  Component,
  ComponentV2,
  Column,
  Require,
  Param,
  ObjectLink,
  SystemProperties,
  Text,
  UIUtils,
  IMonitor,
  Button,
  IMonitorDecoratedVariable
} from '@kit.ArkUI';
import uiObserver from '@ohos.arkui.observer';
import window from '@ohos.window';
import { common } from '@kit.AbilityKit';

@Entry
@ComponentV2
struct Index {
  @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;
  @Env(SystemProperties.WINDOW_SIZE) sizeInVP: window.SizeInVP;
  @Env(SystemProperties.WINDOW_SIZE_PX) sizeInPX: window.Size;
  valueMonitor?: IMonitorDecoratedVariable;

  orientationChange(mon: IMonitor) {
    // 当前窗口宽、高度对应的布局断点信息变化时，触发该回调将变化前后值打印。
    mon.dirty.forEach((path: string) => {
      console.info(`[Env] ${path} changes from ${mon.value<Any>(path)?.before} to ${mon.value<Any>(path)?.now}`);
    })
  }

  aboutToAppear(): void {
    // @Env装饰变量的属性的改变可以通过addMonitor监听
    const callBackArray: Array<() => Any> = [];
    callBackArray.push(() => this.breakpoint.widthBreakpoint);
    callBackArray.push(() => this.breakpoint.heightBreakpoint);
    this.valueMonitor = UIUtils.addMonitor(callBackArray, this.orientationChange);
  }

  private changeOrientation(isLandscape: boolean) {
    // 页面横竖屏切换
    const context = this.getUIContext()?.getHostContext() as common.UIAbilityContext;
    window.getLastWindow(context).then((lastWindow) => {
      lastWindow.setPreferredOrientation(isLandscape ? window.Orientation.LANDSCAPE : window.Orientation.PORTRAIT);
    });
  }

  build() {
    Column() {
      // 打印当前窗口宽度所在的布局断点枚举值
      Text(`Index breakpoint width: ${this.breakpoint.widthBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口高度所在的布局断点枚举值
      Text(`Index breakpoint height: ${this.breakpoint.heightBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位vp）
      Text(`Index sizeInVP width: ${this.sizeInVP.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位vp）
      Text(`Index sizeInVP height: ${this.sizeInVP.height}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位px）
      Text(`Index sizeInPX width: ${this.sizeInPX.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位px）
      Text(`Index sizeInPX height: ${this.sizeInPX.height}`)
        .fontSize(20)

      Button('Landscape')
        .onClick(() => {
          this.changeOrientation(true);
        })

      Button('Portrait')
        .onClick(() => {
          this.changeOrientation(false);
        })

      CompV2({ breakpoint: this.breakpoint, sizeInVP: this.sizeInVP, sizeInPX: this.sizeInPX })
      Comp({ breakpoint: this.breakpoint, sizeInVP: this.sizeInVP, sizeInPX: this.sizeInPX })
    }
  }
}

@ComponentV2
struct CompV2 {
  @Require @Param breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;
  @Require @Param sizeInVP: window.SizeInVP;
  @Require @Param sizeInPX: window.Size;

  build() {
    Column() {
      // 打印当前窗口宽度所在的布局断点枚举值
      Text(`CompV2 breakpoint width: ${this.breakpoint.widthBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口高度所在的布局断点枚举值
      Text(`CompV2 breakpoint height: ${this.breakpoint.heightBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位vp）
      Text(`CompV2 sizeInVP width: ${this.sizeInVP.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位vp）
      Text(`CompV2 sizeInVP height: ${this.sizeInVP.height}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位px）
      Text(`CompV2 sizeInPX width: ${this.sizeInPX.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位px）
      Text(`CompV2 sizeInPX height: ${this.sizeInPX.height}`)
        .fontSize(20)
    }
  }
}

@Component
struct Comp {
  @Require breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;
  @Require sizeInVP: window.SizeInVP;
  @Require sizeInPX: window.Size;

  build() {
    Column() {
      // 打印当前窗口宽度所在的布局断点枚举值
      Text(`Comp breakpoint width: ${this.breakpoint.widthBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口高度所在的布局断点枚举值
      Text(`Comp breakpoint height: ${this.breakpoint.heightBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位vp）
      Text(`Comp sizeInVP width: ${this.sizeInVP.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位vp）
      Text(`Comp sizeInVP height: ${this.sizeInVP.height}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位px）
      Text(`Comp sizeInPX width: ${this.sizeInPX.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位px）
      Text(`Comp sizeInPX height: ${this.sizeInPX.height}`)
        .fontSize(20)
    }
  }
}
```

### 在\@Component中使用\@Env

\@Env在\@Component中使用和其在\@ComponentV2中使用类似，示例如下。

```ts
'use static'

import {
  Env,
  Entry,
  Component,
  ComponentV2,
  Column,
  Require,
  Param,
  ObjectLink,
  SystemProperties,
  Text,
  UIUtils,
  IMonitor,
  Button,
  IMonitorDecoratedVariable
} from '@kit.ArkUI';
import uiObserver from '@ohos.arkui.observer';
import window from '@ohos.window';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;
  @Env(SystemProperties.WINDOW_SIZE) sizeInVP: window.SizeInVP;
  @Env(SystemProperties.WINDOW_SIZE_PX) sizeInPX: window.Size;
  valueMonitor?: IMonitorDecoratedVariable;

  orientationChange(mon: IMonitor) {
    // 当前窗口宽、高度对应的布局断点信息变化时，触发该回调将变化前后值打印。
    mon.dirty.forEach((path: string) => {
      console.info(`[Env] ${path} changes from ${mon.value<Any>(path)?.before} to ${mon.value<Any>(path)?.now}`);
    })
  }

  aboutToAppear(): void {
    // @Env装饰变量的属性的改变可以通过addMonitor监听
    const callBackArray: Array<() => Any> = [];
    callBackArray.push(() => this.breakpoint.widthBreakpoint);
    callBackArray.push(() => this.breakpoint.heightBreakpoint);
    this.valueMonitor = UIUtils.addMonitor(callBackArray, this.orientationChange)
  }

  private changeOrientation(isLandscape: boolean) {
    // 页面横竖屏切换
    const context = this.getUIContext()?.getHostContext() as common.UIAbilityContext;
    window.getLastWindow(context).then((lastWindow) => {
      lastWindow.setPreferredOrientation(isLandscape ? window.Orientation.LANDSCAPE : window.Orientation.PORTRAIT);
    });
  }

  build() {
    Column() {
      // 打印当前窗口宽度所在的布局断点枚举值
      Text(`Index breakpoint width: ${this.breakpoint.widthBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口高度所在的布局断点枚举值
      Text(`Index breakpoint height: ${this.breakpoint.heightBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位vp）
      Text(`Index sizeInVP width: ${this.sizeInVP.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位vp）
      Text(`Index sizeInVP height: ${this.sizeInVP.height}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位px）
      Text(`Index sizeInPX width: ${this.sizeInPX.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位px）
      Text(`Index sizeInPX height: ${this.sizeInPX.height}`)
        .fontSize(20)

      Button('Landscape')
        .onClick(() => {
          this.changeOrientation(true);
        })

      Button('Portrait')
        .onClick(() => {
          this.changeOrientation(false);
        })

      CompV2({ breakpoint: this.breakpoint, sizeInVP: this.sizeInVP, sizeInPX: this.sizeInPX })
      Comp({ breakpoint: this.breakpoint, sizeInVP: this.sizeInVP, sizeInPX: this.sizeInPX })
    }
  }
}

@ComponentV2
struct CompV2 {
  @Require @Param breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;
  @Require @Param sizeInVP: window.SizeInVP;
  @Require @Param sizeInPX: window.Size;

  build() {
    Column() {
      // 打印当前窗口宽度所在的布局断点枚举值
      Text(`CompV2 breakpoint width: ${this.breakpoint.widthBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口高度所在的布局断点枚举值
      Text(`CompV2 breakpoint height: ${this.breakpoint.heightBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位vp）
      Text(`CompV2 sizeInVP width: ${this.sizeInVP.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位vp）
      Text(`CompV2 sizeInVP height: ${this.sizeInVP.height}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位px）
      Text(`CompV2 sizeInPX width: ${this.sizeInPX.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位px）
      Text(`CompV2 sizeInPX height: ${this.sizeInPX.height}`)
        .fontSize(20)
    }
  }
}

@Component
struct Comp {
  @Require breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;
  @Require sizeInVP: window.SizeInVP;
  @Require sizeInPX: window.Size;

  build() {
    Column() {
      // 打印当前窗口宽度所在的布局断点枚举值
      Text(`Comp breakpoint width: ${this.breakpoint.widthBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口高度所在的布局断点枚举值
      Text(`Comp breakpoint height: ${this.breakpoint.heightBreakpoint}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位vp）
      Text(`Comp sizeInVP width: ${this.sizeInVP.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位vp）
      Text(`Comp sizeInVP height: ${this.sizeInVP.height}`)
        .fontSize(20)
      // 打印当前窗口宽度（单位px）
      Text(`Comp sizeInPX width: ${this.sizeInPX.width}`)
        .fontSize(20)
      // 打印当前窗口高度（单位px）
      Text(`Comp sizeInPX height: ${this.sizeInPX.height}`)
        .fontSize(20)
    }
  }
}
```
