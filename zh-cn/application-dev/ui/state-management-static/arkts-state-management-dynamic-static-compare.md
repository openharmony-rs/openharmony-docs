# 状态管理动静态差异

由于动态语言不支持多线程，因此在动态语言上演进出静态语言，以原生支持多线程。

部分基于动态语言实现的功能无法通过静态语言实现，导致部分功能受限或行为发生更改。下面介绍状态管理功能在ArkTS-Dyn和ArkTS-Sta上的差异。

## 修改状态变量后，@Monitor回调的触发机制不同

在状态变量被修改后，状态管理框架需要异步触发依赖状态变量的回调函数，比如触发[@Monitor](./arkts-static-new-monitor.md)回调，或者触发[@Computed](./arkts-static-new-computed.md)重新计算。ArkTS-Dyn中，该触发机制使用Promise任务异步，新建的Promise会被存入任务队列并延时执行。

ArkTS-Sta中，状态管理框架使用Vsync（渲染同步信号）异步触发依赖更新，在每一帧渲染UI组件之前执行依赖状态变量的回调函数。所以状态管理回调的触发机制不再依赖Promise任务，而是申请额外的Vsync渲染。Vsync由后端触发执行，相比Promise方案性能更好，但是可能会导致监听回调函数被执行的次数变少。受影响的[addMonitor](./arkts-static-new-addmonitor-clearmonitor.md)示例如下。

ArkTS-Dyn示例：

```ts
import { UIUtils } from '@kit.ArkUI';

@ObservedV2
class Info {
  @Trace message: string = 'not initialized';

  constructor() {
    UIUtils.addMonitor(this, 'message', this.onMessageChange);
    // 会触发onMessageChange回调，打印`message change from not initialized to initialized`
    this.message = 'initialized'; 
  }
  onMessageChange(monitor: IMonitor) {
    console.info(`message change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
}

@Entry
@ComponentV2
struct Page {
  info: Info = new Info();

  aboutToAppear(): void {
    // 会再次触发onMessageChange回调，打印`message change from initialized to Index aboutToAppear`
    this.info.message = 'Index aboutToAppear'; 
  }

  build() {
    Column() {
      Text('Hello world')
    }
  }
}
```

ArkTS-Sta示例：


```ts
'use static'

import { ObservedV2, Trace, Local, IMonitor, IMonitorDecoratedVariable, UIUtils,
         ComponentV2, Column, Entry, Button, Text } from '@kit.ArkUI';

@ObservedV2
class Info {
  @Trace message: string = 'not initialized';
  messageMonitor?: IMonitorDecoratedVariable;

  constructor() {
    this.messageMonitor = UIUtils.addMonitor(() => this.message, this.onMessageChange);
    // 不会触发onMessageChange回调，因为this.message修改时申请的Vsync在下方aboutToAppear执行后才被执行
    // 导致该修改被下方aboutToAppear里的修改覆盖。
    this.message = 'initialized';
  }
  onMessageChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`message change from ${monitor.value<string>(path)?.before} to ${monitor.value<string>(path)?.now}`);
    });
  }
}

@Entry
@ComponentV2
struct Page {
  @Local info: Info = new Info();

  aboutToAppear(): void {
    // 触发onMessageChange回调，打印`message change from not initialized to Index aboutToAppear`
    this.info.message = 'Index aboutToAppear';
  }

  build() {
    Column() {
      Text('Hello world')
    }
  }
}
```

