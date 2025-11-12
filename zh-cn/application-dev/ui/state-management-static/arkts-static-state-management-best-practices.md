# 状态管理优秀实践

本章节旨在帮助开发者提高ArkUI应用质量，重点提高状态管理效率。章节中列举了常见的低效开发场景及对应解决方案，并通过对比推荐用法与非推荐用法，帮助开发者正确使用状态变量，实现高性能开发。

## 不使用状态变量强行更新非状态变量关联组件

【反例】

```ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, ClickEvent, Color, ForEach } from '@kit.ArkUI';
import { Local } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@ComponentV2
struct MyComponent {
  @Local needsUpdate: boolean = true;
  realStateArr: Array<number> = [4.0, 1.0, 3.0, 2.0]; // 未使用状态变量装饰器

  updateUIArr(param: Array<number>): Array<number> {
    const triggerAGet = this.needsUpdate;
    return param;
  }
  build() {
    Column() {
      ForEach(this.updateUIArr(this.realStateArr),
        (item: number) => {
          Text(`${item}`)
        })
      Text('add item')
        .onClick(() => {
          // 仅改变realStateArr不会触发UI视图更新
          this.realStateArr.push(this.realStateArr[this.realStateArr.length-1] + 1);

          // 触发UI视图更新
          this.needsUpdate = !this.needsUpdate;
        })
    }
    .width(200).height(500)
  }
}
```

上述示例存在以下问题：

- 应用程序希望控制UI更新逻辑，然而ArkUI的UI更新是由框架检测状态变量的变化触发的。

- this.needsUpdate是一个自定义的状态变量，仅应用于其绑定的UI组件。变量this.realStateArr没有被装饰，它们的变化不会触发UI刷新。

- 但是在该应用中，用户试图通过this.needsUpdate的更新来带动常规变量this.realStateArr的更新，这种方法不合理且更新性能较差。

【正例】

解决此问题，需用[\@Local](./arkts-static-new-local.md)装饰realStateArr成员变量。解决后就不再需要变量needsUpdate。

```ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, ClickEvent, Color, ForEach } from '@kit.ArkUI';
import { Local } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@ComponentV2
struct CompA {
  @Local realStateArr: Array<number> = [4.0, 1.0, 3.0, 2.0];
  build() {
    Column() {
      ForEach(this.realStateArr,
        (item: number) => {
          Text(`${item}`)
        })
      Text('add item')
        .onClick(() => {
          // 改变realStateArr触发UI视图更新
          this.realStateArr.push(this.realStateArr[this.realStateArr.length-1] + 1);
        })
    }
    .width(200).height(500)
  }
}
```

## 精准控制状态变量关联的组件数

建议每个状态变量关联的组件数少于20个。精准控制状态变量关联的组件数可减少不必要的组件刷新，提高刷新效率。有时开发者会将同一个状态变量绑定多个同级组件的属性，状态变化时会让这些组件做出相同的改变，导致不必要的刷新，如果存在复杂的组件会显著影响整体性能。相反，将该状态变量绑定在这些组件的父组件上，可以减少需要刷新的组件数，提高性能。

【反例】

```ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, ClickEvent, Color, ForEach, Row, Stack, Image, $r } from '@kit.ArkUI';
import { Local, ObservedV2, Trace, Param, Require } from '@kit.ArkUI';

@ObservedV2
class Translate {
  @Trace translateX: number = 20;
}
@ComponentV2
struct Title {
  @Require @Param translateObj: Translate;
  build() {
    Row() {
      // 此处'app.media.startIcon'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行
      Image($r('app.media.startIcon'))
        .width(50)
        .height(50)
        .translate({
          x:this.translateObj.translateX // this.translateObj.translateX 绑定在Image和Text组件上
        })
      Text('Title')
        .fontSize(20)
        .translate({
          x: this.translateObj.translateX
        })
    }
  }
}
@Entry
@ComponentV2
struct Page {
  @Local translateObj: Translate = new Translate();

  build() {
    Column() {
      Title({
        translateObj: this.translateObj
      })
      Stack() {
      }
      .backgroundColor('black')
      .width(200)
      .height(400)
      .translate({
        x:this.translateObj.translateX // this.translateObj.translateX 绑定在Stack和Button组件上
      })
      Button('move')
        .translate({
          x:this.translateObj.translateX
        })
        .onClick(() => {
          this.getUIContext().animateTo({
            duration: 50
          },()=>{
            this.translateObj.translateX = (this.translateObj.translateX + 50) % 150;
          })
        })
    }
  }
}
```

在上面的示例中，状态变量this.translateObj.translateX被用在多个同级的子组件下，当this.translateObj.translateX变化时，会导致所有关联它的组件一起刷新，但实际上由于这些组件的变化是相同的，因此可以将这个属性绑定到他们共同的父组件上，来实现减少组件的刷新数量。经过分析，所有的子组件其实都处于Page下的Column中，因此将所有子组件相同的translate属性统一到Column上，来实现精准控制状态变量关联的组件数。

【正例】

```ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, ClickEvent, Color, ForEach, Row, Stack, Image, $r } from '@kit.ArkUI';
import { Local, ObservedV2, Trace, Param, Require } from '@kit.ArkUI';

@ObservedV2
class Translate {
  @Trace translateX: number = 20;
}
@ComponentV2
struct Title {
  build() {
    Row() {
      // 此处'app.media.startIcon'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行
      Image($r('app.media.startIcon'))
        .width(50)
        .height(50)
      Text('Title')
        .fontSize(20)
    }
  }
}
@Entry
@ComponentV2
struct Page1 {
  @Local translateObj: Translate = new Translate();

  build() {
    Column() {
      Title()
      Stack() {
      }
      .backgroundColor('black')
      .width(200)
      .height(400)
      Button('move')
        .onClick(() => {
          this.getUIContext().animateTo({
            duration: 50
          },()=>{
            this.translateObj.translateX = (this.translateObj.translateX + 50) % 150;
          })
        })
    }
    .translate({ // 子组件Stack和Button设置了同一个translate属性，可以统一到Column上设置
      x: this.translateObj.translateX
    })
  }
}
```

## 合理控制对象类型状态变量关联的组件数量

如果将一个复杂对象定义为状态变量，需要合理控制其关联的组件数。当对象中某个成员属性发生变化时，会导致该对象关联的所有组件刷新，即使这些组件并未直接使用该属性。

【反例】

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent, Color, ForEach, Row, Stack } from '@kit.ArkUI';
import { State, Observed, ObjectLink } from '@kit.ArkUI';

@Observed
class ClassA {
  prop1: number = 0;
  prop2: string = 'This is Prop2';
}

@Component
struct CompA {
  @ObjectLink a: ClassA;
  private sizeFont: number = 30; // 私有变量不会执行渲染

  private isRenderText(): number {
    this.sizeFont++; // sizeFont改变时组件不会刷新，但是可以看到方法是在被调用的
    console.info('Text prop2 is rendered');
    return this.sizeFont;
  }

  build() {
    Column() {
      Text(this.a.prop2) // 当this.a.prop2的值改变时，会执行组件渲染
        .fontSize(this.isRenderText()) // 当Text组件刷新时，会执行isRenderText方法
    }
  }
}

@Entry
@Component
struct Page {
  @State a: ClassA = new ClassA();

  build() {
    Row() {
      Column() {
        Text('Prop1: ' + this.a.prop1)
          .fontSize(50)
        CompA({ a: this.a })
        Button('Change prop1')
          .width(200)
          .onClick(() => {
            this.a.prop1 = this.a.prop1 + 1;
          })
      }
      .width('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```

为了避免这种“冗余刷新”对性能产生影响，可以使用状态管理V2中的[\@ObservedV2和\@Trace装饰器](./arkts-static-new-observedV2-and-trace.md)。被@Trace装饰器装饰的属性变化时，仅会通知该属性关联的组件进行刷新。

【正例】

```ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, ClickEvent, Color, ForEach, Row, Stack } from '@kit.ArkUI';
import { Local, ObservedV2, Trace, Param, Require } from '@kit.ArkUI';

@ObservedV2
class ClassA {
  @Trace prop1: number = 0;
  @Trace prop2: string = 'This is Prop2';
}

@ComponentV2
struct CompA {
  @Require @Param a: ClassA;
  private sizeFont: number = 30; // 私有变量不会执行渲染

  private isRenderText(): number {
    this.sizeFont++; // sizeFont改变时组件不会刷新，但是可以看到方法是在被调用的
    console.info('Text prop2 is rendered');
    return this.sizeFont;
  }

  build() {
    Column() {
      Text(this.a.prop2) // 当this.a.prop2的值改变时，会执行组件渲染
        .fontSize(this.isRenderText()) // 当Text组件刷新时，会执行isRenderText方法
    }
  }
}

@Entry
@ComponentV2
struct Page {
  @Local a: ClassA = new ClassA();

  build() {
    Row() {
      Column() {
        Text('Prop1: ' + this.a.prop1)
          .fontSize(50)
        CompA({ a: this.a })
        Button('Change prop1')
          .width(200)
          .onClick(() => {
            this.a.prop1 = this.a.prop1 + 1;
          })
      }
      .width('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```

## 避免在for、while等循环逻辑中频繁读取状态变量

在应用开发中，应避免在循环逻辑中频繁读取状态变量，而是应该放在循环外面读取。

【反例】

```ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, ClickEvent, Color, ForEach, Row, Stack, FlexAlign, HorizontalAlign } from '@kit.ArkUI';
import { Local } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'TAG logMessage';

  build() {
    Column() {
      Button('print logmessage')
        .onClick(() => {
          for (let i = 0; i < 10; i++) {
            hilog.info(0x0000, 'TAG', '%{public}s', this.message);
          }
        })
        .width('90%')
        .backgroundColor(Color.Blue)
        .fontColor(Color.White)
    }
    .justifyContent(FlexAlign.Start)
    .alignItems(HorizontalAlign.Center)
  }
}
```

【正例】

```ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, ClickEvent, Color, ForEach, Row, Stack, FlexAlign, HorizontalAlign } from '@kit.ArkUI';
import { Local } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'TAG logMessage';

  build() {
    Column() {
      Button('print logmessage')
        .onClick(() => {
          let logMessage: string = this.message;
          for (let i = 0; i < 10; i++) {
            hilog.info(0x0000, 'TAG', '%{public}s', logMessage);
          }
        })
        .width('90%')
        .backgroundColor(Color.Blue)
        .fontColor(Color.White)
    }
    .justifyContent(FlexAlign.Start)
    .alignItems(HorizontalAlign.Center)
  }
}
```

## 建议使用临时变量替换状态变量

在应用开发中，应尽量减少对状态变量的直接赋值，通过临时变量完成数据计算操作。

状态变量发生变化时，ArkUI会查询依赖该状态变量的组件并执行该组件的更新方法，完成组件渲染的行为。通过使用临时变量的计算代替直接操作状态变量，可以使ArkUI仅在最后一次状态变量变更时查询并渲染组件，减少不必要的操作，从而提高应用性能。

【反例】

```ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, ClickEvent, Color, ForEach, Row, Stack, FlexAlign, HorizontalAlign } from '@kit.ArkUI';
import { Local } from '@kit.ArkUI';
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Message';

  appendMsg(newMsg: string) {
    // 性能打点
    hiTraceMeter.startTrace('StateVariable', 1);
    this.message += newMsg;
    this.message += '~';
    hiTraceMeter.finishTrace('StateVariable', 1);
  }

  build() {
    Column() {
      Text(this.message)
      Button('change')
        .onClick(() => {
          this.appendMsg('add');
        })
        .width('90%')
        .backgroundColor(Color.Blue)
        .fontColor(Color.White)
    }
    .justifyContent(FlexAlign.Start)
    .alignItems(HorizontalAlign.Center)
  }
}
```

【正例】

```ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, ClickEvent, Color, ForEach, Row, Stack, FlexAlign, HorizontalAlign } from '@kit.ArkUI';
import { Local } from '@kit.ArkUI';
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Message';

  appendMsg(newMsg: string) {
    // 性能打点
    hiTraceMeter.startTrace('TemporaryVariable', 2);
    let message = this.message;
    message += newMsg;
    message += '~';
    this.message = message;
    hiTraceMeter.finishTrace('TemporaryVariable', 2);
  }

  build() {
    Column() {
      Text(this.message)
      Button('change')
        .onClick(() => {
          this.appendMsg('add');
        })
        .width('90%')
        .backgroundColor(Color.Blue)
        .fontColor(Color.White)
    }
    .justifyContent(FlexAlign.Start)
    .alignItems(HorizontalAlign.Center)
  }
}
```

