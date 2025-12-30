# \@ReusableV2装饰器：组件复用

为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@ReusableV2装饰[\@ComponentV2](arkts-static-componentv2.md)装饰的自定义组件，达成组件复用的效果。

>**说明：**
>
>从API version 23开始，可以在ArkTS-Sta中使用\@ReusableV2装饰\@ComponentV2装饰的自定义组件。

## 概述

\@ReusableV2用于装饰V2的自定义组件，表明该自定义组件具有被复用的能力：

- \@ReusableV2仅能装饰V2的自定义组件，即\@ComponentV2装饰的自定义组件。
- \@ReusableV2同样提供了[aboutToRecycle](../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttorecycle10+)和[aboutToReuse](../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse18+)的生命周期，在组件被回收时调用aboutToRecycle，在组件被复用时调用aboutToReuse，但与[\@Reusable](../../reference/apis-arkui/arkui-ts/ts-custom-component-decorator-reusable-static)不同的是，aboutToReuse没有入参。
- 在回收阶段，会递归地调用所有子组件的aboutToRecycle回调（即使子组件未被标记可复用）；在复用阶段，会递归地调用所有子组件的aboutToReuse回调（即使子组件未被标记可复用）。
- \@ReusableV2装饰的自定义组件会在被回收期间保持冻结状态，即无法触发UI刷新、无法触发[\@Monitor](arkts-static-new-monitor.md)回调，与[组件冻结](arkts-static-custom-components-freezeV2.md)不同的是，在解除冻结状态后，不会触发延后的刷新。
- \@ReusableV2装饰的自定义组件会在复用时自动重置组件内状态变量的值、重新计算组件内[\@Computed](arkts-static-new-computed.md)以及重置\@Monitor。不建议开发者在aboutToRecycle中更改组件内状态变量，详见[复用前的组件内状态变量重置](#复用前的组件内状态变量重置)。
- V1和V2的复用组件可以混合使用，详见[V1V2混合使用](#v1v2混合使用)。
- 不建议开发者嵌套滥用\@ReusableV2装饰器，这可能会导致复用效率降低以及内存开销变大。

在ArkTS-Sta中使用时，需要导入装饰器：

```ts
import { ReusableV2 } from '@kit.ArkUI';
```

## 装饰器说明

| \@ReusableV2装饰器 | 说明                          |
| ------------------ | ----------------------------- |
| 装饰器参数         | 无                            |
| 可装饰的组件       | \@ComponentV2装饰的自定义组件 |
| 装饰器作用         | 表明该组件可被复用            |

```ts
'use static'
import { ComponentV2, ReusableV2, Local, Column, Text } from '@kit.ArkUI';
@ReusableV2 // 装饰ComponentV2的自定义组件
@ComponentV2
struct ReusableV2Component {
  @Local message: string = 'Hello World';
  build () {
    Column() {
      Text(this.message)
    }
  }
}
```

## 接口说明

reuse、ReuseOptions、ReuseIdCallback的接口说明参考API文档：[**复用选项**](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-reuse.md)。

## V1V2混合使用

在ArkTS-Sta，V1V2的复用组件可混合使用。

下文提到的描述对应关系如下表：

| 描述       | 对应组件类型                         |
| ---------- | ------------------------------------ |
| V1普通组件 | @Component装饰的struct               |
| V2普通组件 | @ComponentV2装饰的struct             |
| V1复用组件 | @Reusable @Component装饰的struct     |
| V2复用组件 | @ReusableV2 @ComponentV2装饰的struct |

下面的表展示了V1和V2的混用支持关系，每行的含义为第一列作为父组件，能否将后面列的组件作为子组件。

以第一行V1普通组件为例，可以将V1普通组件、V2普通组件、V1复用组件以及V2复用组件作为子组件。

|            | V1普通组件 | V2普通组件 | V1复用组件 | V2复用组件 |
| ---------- | :--------: | :--------: | :--------: | :--------: |
| V1普通组件 |    支持    |    支持    |    支持    |    支持    |
| V2普通组件 |    支持    |    支持    |    支持    |    支持    |
| V1复用组件 |    支持    |    支持    |    支持    |    支持    |
| V2复用组件 |    支持    |    支持    |    支持    |    支持    |

根据上表，支持16种可能的父子关系。不建议开发者高度嵌套可复用组件，这会造成复用效率降低。

## 回收与复用的生命周期

\@ReusableV2提供了aboutToRecycle以及aboutToReuse的生命周期，当组件被回收时触发aboutToRecycle，当组件被复用时触发aboutToReuse。

以if的使用场景为例：

```ts
'use static'
import { Entry, ComponentV2, Local, Column, Button, Require, Param, Text, ReusableV2 } from '@kit.ArkUI';
@Entry
@ComponentV2
struct Index {
  @Local condition1: boolean = false;
  @Local condition2: boolean = true;
  build() {
    Column() {
      Button('step1. appear')
        .onClick(() => {
          this.condition1 = true;
        })
      Button('step2. recycle')
        .onClick(() => {
          this.condition2 = false;
        })
      Button('step3. reuse')
        .onClick(() => {
          this.condition2 = true;
        })
      Button('step4. disappear')
        .onClick(() => {
          this.condition1 = false;
        })
      if (this.condition1) {
        NormalV2Component({ condition: this.condition2 })
      }
    }
  }
}
@ComponentV2
struct NormalV2Component {
  @Require @Param condition: boolean;
  build() {
    if (this.condition) {
      ReusableV2Component()
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  aboutToAppear() {
    console.info('ReusableV2Component aboutToAppear called'); // 组件创建时调用
  }
  aboutToDisappear() {
    console.info('ReusableV2Component aboutToDisappear called'); // 组件销毁时调用
  }
  aboutToRecycle() {
    console.info('ReusableV2Component aboutToRecycle called'); // 组件回收时调用
  }
  aboutToReuse() {
    console.info('ReusableV2Component aboutToReuse called'); // 组件复用时调用
  }
  build() {
    Column() {
      Text('ReusableV2Component')
    }
  }
}
```

建议按下面顺序进行操作：

1. 点击`step1. appear`，此时`condition1`变为true，`Index`中的if组件切换分支，创建出`NormalV2Component`，由于`condition2`初始值为true，所以`NormalV2Component`中的if条件满足，尝试创建`ReusableV2Component`。此时复用池中无元素，因此会创建`ReusableV2Component`，并回调`aboutToAppear`的方法，输出`ReusableV2Component aboutToAppear called`的日志。
2. 点击`step2. recycle`，此时`condition2`变为false，通过\@Param同步给`NormalV2Component`，if条件切换，由于`ReusableV2Component`使用了\@ReusableV2，因此会将该组件回收至复用池而不是销毁，回调`aboutToRecycle`的方法并输出`ReusableV2Component aboutToRecycle called`的日志。
3. 点击`step3. reuse`，此时`condition2`变为true，通过\@Param传递给`NormalV2Component`，if条件切换，由于`ReusableV2Component`使用了\@ReusableV2，因此在创建该组件时尝试去复用池中寻找。此时复用池中有第二步放入的组件实例，因此从复用池中取出复用，回调`aboutToReuse`方法并输出`ReusableV2Component aboutToReuse called`的日志。
4. 点击`step4. disappear`，此时`condition1`变为false，`Index`组件中的if组件切换分支，销毁`NormalV2Component`，此时`ReusableV2Component`因为父组件销毁，所以会被一起销毁，回调`aboutToDisappear`的方法并输出`ReusableV2Component aboutToDisappear called`的日志。

倘若该复用组件下有子组件时，会在回收和复用时递归调用子组件的aboutToRecycle和aboutToReuse（与子组件是否被标记复用无关），直到遍历完所有的孩子组件。

## 复用阶段的冻结

V2组件在复用时将会被自动冻结，不会响应在回收期间发生的变化。这一个期间包括`aboutToRecycle`，即`aboutToRecycle`中的修改不会刷新到UI上，也不会触发\@Computed以及\@Monitor。冻结状态将持续到aboutToReuse前，即`aboutToReuse`及之后的变量更改，才会正常触发UI刷新、\@Computed重新计算以及\@Monitor的调用。

以if的使用场景为例：

```ts
'use static'
import { ObservedV2, Trace, Entry, ComponentV2, Local, Column, Button, Monitor, IMonitor, Text, ReusableV2 } from '@kit.ArkUI';
@ObservedV2
class Info {
  @Trace age: int = 25;
}
const info: Info = new Info();
@Entry
@ComponentV2
struct Index {
  @Local condition: boolean = true;
  build() {
    Column() {
      Button('复用/回收').onClick(()=>{this.condition=!this.condition;})
      Button('改值').onClick(()=>{info.age++;})
      if (this.condition) {
        ReusableV2Component()
      }
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  @Local info: Info = info; // 仅做演示使用，并不建议@Local赋值全局变量
  @Monitor(['info.age'])
  onValChange(m: IMonitor) {
    console.info('info.age change');
  }
  aboutToRecycle() {
    console.info('aboutToRecycle');
    this.info.age++;
  }
  aboutToReuse() {
    console.info('aboutToReuse');
    this.info.age++;
  }
  onRender(): string {
    console.info('info.age onRender');
    return this.info.age.toString();
  }
  build() {
    Column() {
      Text(this.onRender())
    }
  }
}
```

建议按如下步骤进行操作：

1. 点击`改值`按钮，可以观察到UI变化，\@Monitor触发并输出日志`info.age change`以及`info.age onRender`，说明此时能够正常监听到变化以及触发UI刷新。
2. 点击`复用/回收`按钮，此时调用`aboutToRecycle`回调并输出`aboutToRecycle`的日志，但\@Monitor不被触发，且`onRender`方法不被回调。
3. 点击`改值`按钮，UI无变化，\@Monitor不触发且`onRender`方法不被回调。
4. 点击`复用/回收`按钮，此时调用`aboutToReuse`回调并输出`aboutToReuse`的日志，\@Monitor触发并输出日志`info.age change`且`onRender`方法回调输出`info.age onRender`，UI发生变化。

如果去掉`aboutToReuse`方法中的自增操作，则上述第四步不会触发\@Monitor回调。

在ArkTS-Sta中，V1V2组件将在复用阶段自动冻结，无需开发者进行额外配置。

## 复用前的组件内状态变量重置

与\@Reusable不同的是，\@ReusableV2在复用前会重置组件中的状态变量以及\@Computed、\@Monitor的内容。在复用的过程当中，所有的V2自定义组件，无论是否被标记了\@ReusableV2，都会经历这一个重置过程。

重置会按照变量在组件中定义的顺序按照下面的规则依次进行：

| 装饰器                                     | 重置方法                                                     |
| ------------------------------------------ | ------------------------------------------------------------ |
| [\@Local](arkts-static-new-local.md)       | 直接使用定义时的初始值重新赋值。                             |
| [\@Param](arkts-static-new-param.md)       | 如果有外部传入则使用外部传入值重新赋值，否则用本地初始值重新赋值。注意：[\@Once](arkts-static-new-once.md)装饰的变量同样会被重置初始化一次。 |
| [\@Event](arkts-satic-new-event.md)        | 如果有外部传入则使用外部传入值重新赋值，否则用本地初始值重新赋值。注意：开发者必须为@Event指定外部传入值或本地初始值。 |
| [\@Provider](arkts-static-new-provider.md) | 直接使用定义时的初始值重新赋值。                             |
| [\@Consumer](arkts-static-new-consumer.md) | 如果有对应的\@Provider则直接使用\@Provider对应的值，否则使用本地初始值重新赋值。 |
| \@Computed                                 | 使用当前最新的值重新计算一次。                               |
| \@Monitor                                  | 更新所属[IMonitorValue](../../reference/apis-arkui/arkui-ts/ts-state-management-monitor-static.md#imonitorvalue)中的before值与now值。 |
| 常量                                       | 包括readonly的常量，不重置。                                 |

下面的例子展示了重置的一些效果：

```ts
'use static'
import { ObservedV2, Trace, Entry, ComponentV2, Local, Provider, Column, Button, Text, Param, Once, Require, Event, Consumer, Monitor, IMonitor, Computed, ReusableV2 } from '@kit.ArkUI';
@ObservedV2
class Info {
  @Trace age: int;
  constructor(age: int) {
    this.age = age;
  }
}
@Entry
@ComponentV2
struct Index {
  @Local local: int = 0;
  @Provider('inherit') inheritProvider: int = 100;
  @Local condition: boolean = true;
  build() {
    Column() {
      Button('回收/复用').onClick(()=>{this.condition=!this.condition;})
      Column() {
        Text('父组件变量')
        Text(`local: ${this.local}`).onClick(()=>{this.local++;})
        Text(`inheritProvider: ${this.inheritProvider}`).onClick(()=>{this.inheritProvider++;})
      }.borderWidth(2)
      if (this.condition) {
        ReusableV2Component({
          paramOut: this.local,
          paramOnce: this.local,
          changeParam: () => {
            this.local++;
          }
        })
      }
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  @Local val: int = 0;
  @Local info: Info = new Info(25);
  @Param paramLocal: int = 1;
  @Require @Param paramOut: int;
  @Require @Param @Once paramOnce: int;
  @Event changeParam: () => void;
  @Provider('selfProvider') selfProvider: int = 0;
  @Consumer('inherit') inheritConsumer: int = 0;
  @Consumer('selfConsumer') selfConsumer: int = 0;
  noDecoVariable: int = 0; // 未加装饰器，被视作常量
  noDecoInfo: Info = new Info(30); // 未加装饰器，被视作常量
  readonly readOnlyVariable: int = 0; // readonly常量
  @Computed
  get plusParam(): int {
    return this.paramLocal + this.paramOut + this.paramOnce;
  }
  @Monitor(['val'])
  onValChange(monitor: IMonitor) {
    console.info(`val change from ${monitor.value<int>()?.before} to ${monitor.value<int>()?.now}`);
  }
  @Monitor(['plusParam'])
  onPlusParamChange(monitor: IMonitor) {
    console.info(`plusParam change from ${monitor.value<int>()?.before} to ${monitor.value<int>()?.now}`);
  }
  build() {
    Column() {
      Column() {
        Text('重置为本地初始值的变量')
        Text(`val: ${this.val}`).onClick(()=>{this.val++;})
        Text(`info.age: ${this.info.age}`).onClick(()=>{this.info.age++;})
        Text(`paramLocal: ${this.paramLocal}`).onClick(()=>{/* 无外部传入的Local无法本地修改 */})
        Text(`selfProvider: ${this.selfProvider}`).onClick(()=>{this.selfProvider++;})
        Text(`selfConsumer: ${this.selfConsumer}`).onClick(()=>{this.selfConsumer++;})
      }.borderWidth(2)
      Column() {
        Text('重置为外部传入的变量')
        Text(`paramOut: ${this.paramOut}`).onClick(()=>{this.changeParam();})
        Text(`paramOnce: ${this.paramOnce}`).onClick(()=>{this.paramOnce++;})
      }.borderWidth(2)
      Column() {
        Text('根据父组件情况决定')
        Text(`inheritConsumer: ${this.inheritConsumer}`).onClick(()=>{this.inheritConsumer++;})
        Text(`plusParam: ${this.plusParam}`)
      }.borderWidth(2)
      Column() {
        Text('不被重置')
        Text(`noDecoVariable: ${this.noDecoVariable}`)
        Text(`noDecoInfo.age: ${this.noDecoInfo.age}`).onClick(()=>{this.noDecoInfo.age++;}) // 能够触发刷新但是复用时不会被重置
        Text(`readOnlyVariable: ${this.readOnlyVariable}`)
      }.borderWidth(2)
    }
  }
}
```

开发者可以尝试点击各个变量，并点击`回收/复用`按钮查看复用后的重置情况。

在ArkTS-Sta中，组件内的@Monitor会重置所属的IMonitorValue的before值与now值。当监听\@Trace装饰的属性时，即使对象本身未被重置，@Monitor也会重新设置before值与now值。

将上面的例子简化可得下面的例子：

```ts
'use static'
import { ObservedV2, Trace, Entry, ComponentV2, Local, Column, Button, Monitor, Text, IMonitor, ReusableV2 } from '@kit.ArkUI';
@ObservedV2
class Info {
  @Trace age: int;
  constructor(age: int) {
    this.age = age;
  }
}
@Entry
@ComponentV2
struct Index {
  @Local condition: boolean = true;
  build() {
    Column() {
      Button('回收/复用').onClick(()=>{this.condition=!this.condition;})
      if (this.condition) {
        ReusableV2Component()
      }
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  noDecoInfo: Info = new Info(30); // 未加装饰器，被视作常量
  @Monitor(['noDecoInfo.age'])
  onAgeChange(monitor: IMonitor) {
    console.info(`age change from ${monitor.value<int>()?.before} to ${monitor.value<int>()?.now}`);
  }
  aboutToRecycle() {
    this.noDecoInfo.age = 25;
  }
  aboutToReuse() {
    this.noDecoInfo.age = 35;
  }
  build() {
    Column() {
      Column() {
        Text(`noDecoInfo.age: ${this.noDecoInfo.age}`)
          .onClick(()=>{this.noDecoInfo.age++;}) // 能够触发刷新但是不会被重置
      }
    }
  }
}
```

建议按照下列步骤进行操作：

1. 点击`noDecoInfo.age: 30`，UI刷新为`noDecoInfo.age: 31`，\@Monitor触发并输出日志`age change from 30 to 31`。
2. 点击`回收/复用`两次，UI刷新为`noDecoInfo.age: 35`，\@Monitor触发并输出日志`age change from 25 to 35`。
3. 点击`noDecoInfo.age: 35`，UI刷新为`noDecoInfo.age: 36`，\@Monitor触发并输出日志`age change from 35 to 36`。

由于冻结机制的存在，在aboutToRecycle中赋值不会被\@Monitor观察到。而在经历完变量重置后，组件内状态变量又会被赋予新的值，因此对于组件内状态变量来说，在aboutToRecycle中赋值不会有明显的效果；而常量（例如上面的`noDecoInfo`）由于冻结机制的存在，在aboutToRecycle中更改`age`不会被观察到，也不会在复用前被重置。因此在上面的例子中，复用前重置组件内的@Monitor时，重新设置before值为`age`在aboutToRecycle修改后的25。最终表现出来的现象即：第二步回调的\@Monitor中，`monitor.value()?.before`得到的值为25，而非age的初始值30。

## 使用场景

### 在if组件中使用

通过改变if组件的条件可以触发组件回收/复用。在ArkTS-Sta中，从if分支切换到else分支时，将直接复用if分支的ReusableV2Component。

```ts
'use static'
import { Entry, ComponentV2, Local, Column, Button, ReusableV2, Text } from '@kit.ArkUI';
@Entry
@ComponentV2
struct Index {
  @Local condition: boolean = true;
  build() {
    Column() {
      Button('切换if分支').onClick(()=>{this.condition=!this.condition;}) // 点击切换if分支
      if (this.condition) {
        ReusableV2Component()
      } else {
        ReusableV2Component()
      }
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  @Local message: string = 'Hello World';
  aboutToRecycle() {
    console.info('ReusableV2Component aboutToRecycle'); // 回收时被调用
  }
  aboutToReuse() {
    console.info('ReusableV2Component aboutToReuse'); // 复用时被调用
  }
  build() {
    Column() {
      Text(this.message)
    }
  }
}
```

### 在Repeat组件中使用

Repeat组件懒加载场景中，将会优先使用Repeat组件的缓存池，正常滑动场景、更新场景不涉及组件的回收与复用。当Repeat的缓存池需要扩充时将会向自定义组件要求新的子组件，此时如果复用池中有可复用的节点，将会进行复用。

下面的例子中，先点击`改变condition`会让3个节点进入复用池，而后向下滑动List组件时，可以观察到日志输出`ReusableV2Component aboutToReuse`，表明Repeat可以使用自定义组件的复用池填充自己的缓存池。

```ts
'use static'
import { Entry, ComponentV2, Local, Column, Button, List, Repeat, ReusableV2, Param, Text, RepeatItem, Require, ListItem } from '@kit.ArkUI';
@Entry
@ComponentV2
struct Index {
  @Local condition: boolean = true;
  @Local simpleList: int[] = [];
  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.simpleList.push(i)
    }
  }
  build() {
    Column() {
      Button('改变condition').onClick(()=>{this.condition=!this.condition;})
      if (this.condition) {
        // 此处仅做演示使用，让复用池中填充3个组件
        ReusableV2Component({ num: 0})
        ReusableV2Component({ num: 0})
        ReusableV2Component({ num: 0})
      }
      List() {
        Repeat<int>(this.simpleList)
          .virtualScroll()
          .each((obj: RepeatItem<int>) => {
            ListItem() {
              Column() {
                ReusableV2Component({ num: obj.item })
              }
            }
          })
      }.height('50%')
      .cachedCount(2)
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  @Require @Param num: int;
  aboutToAppear() {
    console.info('ReusableV2Component aboutToAppear');
  }
  aboutToRecycle() {
    console.info('ReusableV2Component aboutToRecycle');
  }
  aboutToReuse() {
    console.info('ReusableV2Component aboutToReuse');
  }
  build() {
    Column() {
      Text(`${this.num}`).fontSize(50)
    }
  }
}
```

也可以在Repeat的template属性中使用@ReusableV2装饰的自定义组件，例子如下。

```ts
'use static'
import { Entry, ComponentV2, Local, Column, Button, List, Repeat, ReusableV2, Param, Text, RepeatItem, Require, ListItem, Color } from '@kit.ArkUI';
@Entry
@ComponentV2
struct Index {
  @Local condition: boolean = true;
  @Local simpleList: int[] = [];
  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.simpleList.push(i)
    }
  }
  build() {
    Column() {
      Button('改变condition').onClick(()=>{this.condition=!this.condition;})
      if (this.condition) {
        // 此处仅做演示使用，让复用池中填充3个组件
        ReusableV2Component({ num: 0})
        ReusableV2Component({ num: 0})
        ReusableV2Component({ num: 0})
      }
      List() {
        Repeat<int>(this.simpleList)
          .virtualScroll()
          .each(()=>{})
          .templateId((item: int, index: int) => {
            return item % 2 === 0 ? 'a' : 'b'
          })
          .template('a', (obj: RepeatItem<int>) => {
            ListItem() {
              Column() {
                ReusableV2Component({ num: obj.item })
              }
            }
          })
          .template('b', (obj: RepeatItem<int>) => {
            ListItem() {
              Column() {
                ReusableV2Component({ num: obj.item })
              }
            }
          })
      }.height('50%')
      .cachedCount(2)
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  @Require @Param num: int;
  aboutToAppear() {
    console.info('ReusableV2Component aboutToAppear');
  }
  aboutToRecycle() {
    console.info('ReusableV2Component aboutToRecycle');
  }
  aboutToReuse() {
    console.info('ReusableV2Component aboutToReuse');
  }
  build() {
    Column() {
      Text(`${this.num}`)
        .fontSize(50)
        .fontColor(this.num % 2 === 0 ? Color.Red : Color.Blue)
    }
  }
}

```

### 在Repeat组件非懒加载场景的each属性中使用

Repeat组件非懒加载场景中，会在删除/创建子树时触发回收/复用。

```ts
'use static'
import { Entry, ComponentV2, Local, Column, Button, List, Repeat, ReusableV2, Require, Param, Text, RepeatItem, ListItem } from '@kit.ArkUI';
@Entry
@ComponentV2
struct Index {
  @Local simpleList: int[] = [1, 2, 3, 4, 5];
  @Local condition: boolean = true;
  build() {
    Column() {
      Button('删除/创建Repeat').onClick(()=>{this.condition=!this.condition;})
      Button('增加元素').onClick(()=>{this.simpleList.push(this.simpleList.length+1);})
      Button('删除元素').onClick(()=>{this.simpleList.pop();})
      Button('更改元素').onClick(()=>{this.simpleList[0]++;})
      if (this.condition) {
        List({ space: 10 }) {
          Repeat<int>(this.simpleList)
            .each((obj: RepeatItem<int>) => {
              ListItem() {
                Column() {
                  ReusableV2Component({ num: obj.item })
                }
              }
            })
            .virtualScroll({ disableVirtualScroll: true })
        }
      }
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  @Require @Param num: int;
  aboutToAppear() {
    console.info('ReusableV2Component aboutToAppear');
  }
  aboutToRecycle() {
    console.info('ReusableV2Component aboutToRecycle');
  }
  aboutToReuse() {
    console.info('ReusableV2Component aboutToReuse');
  }
  build() {
    Column() {
      Text(`${this.num}`)
    }
  }
}
```

### 在ForEach组件中使用

>**说明：**
>
>推荐开发者使用Repeat组件的非懒加载场景代替ForEach组件

下面的例子中使用了ForEach组件渲染了数个可复用组件，由于每次点击`点击修改`按钮时key值都会发生变化，因此从第二次点击开始都会触发回收与复用（由于ForEach先判断有无可复用节点时复用池仍未初始化，因此第一次点击会创建新的节点，而后初始化复用池同时回收节点）。

```ts
'use static'
import { Entry, ComponentV2, Local, Column, ForEach, Row, Button, ReusableV2, Require, Param, Text } from '@kit.ArkUI';
@Entry
@ComponentV2
struct Index {
  @Local simpleList: int[] = [0, 1, 2, 3, 4, 5];
  build() {
    Column() {
      ForEach(this.simpleList, (num: int, index: int) => {
        Row() {
          Button('点击修改').onClick(()=>{this.simpleList[index]++;})
          ReusableV2Component({ num: num })
        }
      }) // 每次修改完key发生变化
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  @Require @Param num: int;
  aboutToAppear() {
    console.info('ReusableV2Component aboutToAppear', this.num); // 创建时触发
  }
  aboutToRecycle() {
    console.info('ReusableV2Component aboutToRecycle', this.num); // 回收时触发
  }
  aboutToReuse() {
    console.info('ReusableV2Component aboutToReuse', this.num); // 复用时触发
  }
  build() {
    Column() {
      Text(`child: ${this.num}`)
    }
  }
}
```

### 在LazyForEach组件中使用

>**说明：**
>
>推荐开发者使用Repeat组件的懒加载场景代替LazyForEach组件

下面的例子中使用了LazyForEach渲染了数个可复用组件，在滑动时可以先观察到组件创建，直到预加载节点全部创建完成之后，再滑动则触发复用和回收。

```ts
'use static'
import { IDataSource, DataChangeListener, DataOperation, ObservedV2, Trace, Entry, ComponentV2, List, LazyForEach, Button, ListItem, Column, Text, ReusableV2, Row, Param, Require } from '@kit.ArkUI';
class BasicDataSource<StringData> implements IDataSource<StringData> {
  private listeners: Array<DataChangeListener> = [];
  private originDataArray: StringData[] = [];

  public totalCount(): int {
    return this.originDataArray.length;
  }

  public getData(index: int): StringData {
    return this.originDataArray[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      console.info('add listener');
      this.listeners.push(listener);
    }
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
    const pos = this.listeners.indexOf(listener);
    if (pos >= 0) {
      console.info('remove listener');
      this.listeners.splice(pos, 1);
    }
  }

  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    })
  }

  notifyDataAdd(index: int): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    })
  }

  notifyDataChange(index: int): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    })
  }

  notifyDataDelete(index: int): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    })
  }

  notifyDataMove(from: int, to: int): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    })
  }

  notifyDatasetChange(operations: Array<DataOperation>): void {
    this.listeners.forEach(listener => {
      listener.onDatasetChange(operations);
    });
  }
}

export class StringDataSource extends BasicDataSource<StringData> {
  dataArray: Array<StringData> = [];

  public totalCount(): int {
    return this.dataArray.length;
  }

  public getData(index: int): StringData {
    return this.dataArray[index];
  }

  public addData(index: int, data: StringData): void {
    this.dataArray.splice(index, 0, data);
    this.notifyDataAdd(index);
  }

  public pushData(data: StringData): void {
    this.dataArray.push(data);
    this.notifyDataAdd(this.dataArray.length - 1);
  }

  public reloadData(): void {
    this.notifyDataReload();
  }


}

@ObservedV2
class StringData {
  @Trace message: string;
  constructor(message: string) {
    this.message = message;
  }
}

@Entry
@ComponentV2
struct Index {
  data: StringDataSource = new StringDataSource();

  aboutToAppear() {
    for (let i = 0; i <= 200; i++) {
      this.data.pushData(new StringData('Hello' + i));
    }
  }
  build() {
    List({ space: 3 }) {
      LazyForEach(this.data, (item: StringData, index: int) => {
        ListItem() {
          Column() {
            Text(item.message)
            ChildComponent({ data: item.message })
            Button('change message')
              .onClick(() => {
                item.message += '!'; // message为@Trace装饰的变量，可观察变化
              })
          }
        }
      })
    }.cachedCount(5)
  }
}

@ReusableV2
@ComponentV2
struct ChildComponent {
  @Param @Require data: string;
  aboutToAppear(): void {
    console.info('ChildComponent aboutToAppear', this.data);
  }
  aboutToDisappear(): void {
    console.info('ChildComponent aboutToDisappear', this.data);
  }
  aboutToReuse(): void {
    console.info('ChildComponent aboutToReuse', this.data); // 复用时触发
  }
  aboutToRecycle(): void {
    console.info('ChildComponent aboutToRecycle', this.data); // 回收时触发
  }
  build() {
    Row() {
      Text(this.data).fontSize(50)
    }
  }
}

```

