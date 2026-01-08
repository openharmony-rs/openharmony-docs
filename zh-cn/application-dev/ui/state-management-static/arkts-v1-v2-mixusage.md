# 状态管理V1V2混用指导

## 概述

在状态管理框架的演进过程中，分别于API version 7和API version 12推出了状态管理V1和V2两个版本。对于已经使用状态管理V1的应用，如果有诉求向状态管理V2迁移，可参考[状态管理V1和V2迁移文档](../state-management/arkts-v1-v2-migration.md)。

在ArkTS-Sta中，保持与ArkTS-Dyn API version 19之后的校验规则一致，具体校验规则可参考下表。由于ArkTS-Sta的状态管理V1V2采用相同的逻辑实现状态变量的收集依赖与触发更新，V1和V2天然支持状态变量的传递，因此弃用了ArkTS-Dyn的方法[enableV2Compatibility](../../reference/apis-arkui/js-apis-StateManagement.md#enablev2compatibility19)和[makeV1Observed](../../reference/apis-arkui/js-apis-StateManagement.md#makev1observed19)，可以直接混用状态管理V1与V2。

> **说明：**
>
> 本文档中使用“->”表示变量的传递，比如“V1->V2”，表示V1状态变量向V2状态变量传递。


## 校验规则
在ArkTS-Sta中，编译期校验见下表。

| ArkTS-Sta场景                             | ArkTS-Sta编译是否报错 |
| ----------------------------------------- | --------------------- |
| V1->V2传递[@Observed](./arkts-static-observed-and-objectlink.md)装饰的class                 | 不报错                |
| V1->V2传递非@Observed装饰的class               | 不报错                |
| V1->V2传递builtin类型                        | 不报错                |
| V2->V1传递@Observed类型                       | 不报错                |
| V2->V1传递builtin类型                         | 不报错                |
| V2->V1传递[@ObservedV2](./arkts-static-new-observedV2-and-trace.md)类型                     | 编译期报错            |
| V2->V1传递普通class类型                       | 不报错                |
| V2装饰器装饰@Observed数据                 | 不报错                |
| V1装饰器装饰@ObservedV2数据               | 编译期报错            |
| V2->V1传递非@Observed数据，传给V1的[@ObjectLink](./arkts-static-observed-and-objectlink.md) | 不报错                |



## 接口变化
从ArkTS-Sta开始，[\@Component](./arkts-static-create-component.md#component)和[\@ComponentV2](./arkts-static-componentv2.md#componentv2)天然支持V1/V2状态变量的传递，弃用ArkTS-Dyn的[UIUtils.makeV1Observed](../../reference/apis-arkui/js-apis-StateManagement.md#makev1observed19)和[UIUtils.enableV2Compatibility](../../reference/apis-arkui/js-apis-StateManagement.md#enablev2compatibility19)两个接口。



## 混用范式

### V1->V2
- V1的状态变量传递给V2的[\@Param](./arkts-static-new-param.md)，V1的状态变量在\@ComponentV2中有观察能力。完整示例见[常见场景](#v1-v2-1)。
```ts
@Observed
class ObservedClass {
}

@Entry
@Component
struct CompV1 {
  @State observedClass: ObservedClass = new ObservedClass();

  build() {
    Column() {
      CompV2({ observedClass: this.observedClass })
    }
  }
}

@ComponentV2
struct CompV2 {
  @Param observedClass: ObservedClass = new ObservedClass();

  build() {
  }
}
```
- V1状态变量可观察第一层属性，在传递给\@Param后，\@Param也可观察第一层属性的变化。

具体场景能力可见下表。

| \@Component(父) -> \@ComponentV2(子)  | 观察行为 |
|------|----|
| 常规变量| 可观察。 |
| \@Observed装饰class   | 可观察第一层属性。 |
| V1装饰器装饰的变量，其类型为Array、Map、Set和Date  | 可观察API调用。 |
| V1装饰器装饰的变量，其类型为非\@Observed装饰的class  | 在ArkTS-Sta不可观察。 |
| 普通Array，其数组项为\@Observed装饰的class  | 不可观察。 |
| V1装饰器装饰的变量，其类型为普通Array，其数组项为\@Observed装饰的class  | 在\@Component中仅可观察第一层，如果想深度观察，则需搭配\@ObjectLink使用。在\@ComponentV2中可深度观察。 |
| \@ObservedV2装饰的class  | 在V1和V2中可观察，其观察能力源于\@ObservedV2和\@Trace的能力。 |
| V1装饰器装饰的变量，其类型为普通Array，其数组项为\@ObservedV2装饰的class | 可观察，\@ObservedV2装饰的class的属性观察能力源自于\@ObservedV2和[\@Trace](./arkts-static-new-observedV2-and-trace.md)。 |

### V2->V1

在V2->V1时，V2的状态变量传递给V1的\@ObjectLink，V2的状态变量在\@Component中有观察能力。完整示例见[常见场景](#v2-v1-1)。

```ts
'use static'
import { Entry, Column, Component, ComponentV2, Local, ObjectLink, Observed } from '@kit.ArkUI';

@Observed
class ObservedClass {}

@Entry
@ComponentV2
struct CompV2 {
  @Local observedClass: ObservedClass = new ObservedClass();
  build() {
    Column() {
      CompV1({ observedClass: this.observedClass })
    }
  }
}

@Component
struct CompV1 {
  @ObjectLink observedClass: ObservedClass;
  build() {}
}
```

具体场景如下表。

| \@ComponentV2(父) -> \@Component(子)  | 观察行为 |
|------|----|
| \@Observed装饰class的嵌套类 | 在\@ComponentV2可深度观察嵌套属性的变化。 |
| 普通class  | 在ArkTS-Sta不可观察。 |
| Array\<number\>，或其他简单类型数组  | 可以观察。 |
| Array\<ObservedClass\>，即数组项是\@Observed装饰的class  | 可以观察。 |
|  Array\<Array\<number\>\>，二维数组，数组项或为其他简单类型 | 可以观察。 |



## 混用规则

- ArkTS-Sta中V1->V2传递复杂类型数据，由于@Component和@ComponentV2天然支持V1/V2状态变量的传递，因此无需调用`UIUtils.enableV2Compatibility`，即可实现V1和V2的数据联动。

```ts
// 无需调用enableV2Compatibility
SubComponentV2({param: this.state})
```

- ArkTS-Sta中V2->V1传递复杂类型数据，由于@Component和@ComponentV2天然支持V1/V2状态变量的传递，因此无需调用`UIUtils.enableV2Compatibility`，即可实现V2和V1的数据联动。

```ts
// 无需调用enableV2Compatibility与makeV1Observed
SubComponentV2({objectLink: this.local})
```


## 常见场景

### 普通JS Object

在ArkTS-Sta中，普通class（无@Observed/@ObservedV2）不可观察。

**V1->V2**
```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, Button, ClickEvent, State, Param } from '@kit.ArkUI';

class CommonClass {
  name: string = 'Tom';
}

@Entry
@Component
struct CompV1 {
  @State commonObject: CommonClass = new CommonClass();

  build() {
    Column() {
      Text(`@State commonObject: ${this.commonObject.name}`)
      Button('Change object in V1')
        .onClick(() => {
          this.commonObject.name += '!'; // 非Observed/ObservedV2类，组件不刷新
        })
      CompV2({ commonObject: this.commonObject })
    }
  }
}

@ComponentV2
struct CompV2 {
  @Param commonObject: CommonClass = new CommonClass();

  build() {
    Column() {
      // 非Observed/ObservedV2类，观察不到变化
      Text(`@Param commonObject: ${this.commonObject.name}`)
      Button('Change object in V2')
        .onClick(() => {
          this.commonObject.name += '!'; // 非Observed/ObservedV2类，组件不刷新
        })
    }
  }
}
```


**V2->V1**

```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, Button, ClickEvent, Local, ObjectLink } from '@kit.ArkUI';

class CommonClass {
  name: string = 'Tom';
}

@Entry
@ComponentV2
struct CompV2 {
  @Local commonObject: CommonClass = new CommonClass();

  build() {
    Column() {
      Text(`@Local commonObject: ${this.commonObject.name}`)
      Button('Change object in V2')
        .onClick(() => {
          this.commonObject.name += '!'; // 非Observed/ObservedV2类，组件不刷新
        })
      // @ObjectLink可接收@Observed装饰class的实例
      CompV1({ commonObject: this.commonObject })
    }
  }
}

@Component
struct CompV1 {
  @ObjectLink commonObject: CommonClass;

  build() {
    Column() {
      // 非Observed/ObservedV2类，观察不到变化
      Text(`@ObjectLink commonObject: ${this.commonObject.name}`)
      Button('Change object in V1')
        .onClick(() => {
          this.commonObject.name += '!'; // 非Observed/ObservedV2类，组件不刷新
        })
    }
  }
}
```


### \@Observed装饰的class
**V1->V2**
下面的示例中：
- `ObservedClass`是\@Observed装饰的class，并在传递给V2时使能了在V2中观察的能力。
- `name`是`@Track`装饰的属性，其在V1和V2均是可观察的。
- `count`是非`@Track`装饰的属性，其在V1和V2的UI中使用均是非法的。
    - 在V1中，如果将非`@Track`装饰的属性使用在UI中，是非法行为，会有运行时报错。
    - 在V2中，非`@Track`装饰的属性使用在UI不会有运行时报错，但不会响应更新。

```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, ClickEvent, State, Param, Observed, Track } from '@kit.ArkUI';

@Observed
class ObservedClass {
  @Track name: string = 'a';
  count: number = 0;
}

@Entry
@Component
struct CompV1 {
  @State observedClass: ObservedClass = new ObservedClass();
  build() {
    Column() {
      Text(`name: ${this.observedClass.name}`).onClick(() => {
        // 触发刷新
        this.observedClass.name += 'a';
      })
      // 使用非@Track的变量在V1中会崩溃
      // Text(`count: ${this.observedClass.count}`)

      CompV2({ observedClass: this.observedClass })
    }
  }
}

@ComponentV2
struct CompV2 {
  @Param observedClass: ObservedClass = new ObservedClass();
  build() {
    // 使用非@Track的变量在V2中不会崩溃，但不会响应更新
    Text(`count: ${this.observedClass.count}`).onClick(() => {
      // 不触发刷新
      this.observedClass.count++;
    })
  }
}
```
**V2->V1**
- `ObservedClass`是\@Observed装饰的class，该类的状态变量传递给V1可观察。
- 只有[\@Track](./arkts-static-track.md)装饰的变量在V1和V2中可观察。非\@Track的变量在V1中使用在UI上会有运行时报错，在V2中不会报错，但不会响应刷新。
```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, ClickEvent, Local, ObjectLink, Observed, Track } from '@kit.ArkUI';

@Observed
class ObservedClass {
  @Track name: string = 'a';
  count: number = 0;
}

@Entry
@ComponentV2
struct CompV2 {
  @Local observedClass: ObservedClass = new ObservedClass();

  build() {
    Column() {
      Text(`name V2: ${this.observedClass.name}`).onClick(() => {
        // 触发刷新
        this.observedClass.name += 'a';
      })
      // 使用非@Track的变量在V2中不会崩溃，但不触发刷新
      Text(`count V2: ${this.observedClass.count}`).onClick(() => {
        this.observedClass.count++;
      })

      CompV1({ observedClass: this.observedClass })
    }
  }
}

@Component
struct CompV1 {
  @ObjectLink observedClass: ObservedClass;

  build() {
    Column() {
      Text(`name V1: ${this.observedClass.name}`).onClick(() => {
        // 触发刷新
        this.observedClass.name += 'a';
      })
      // 使用非@Track的变量在V1中会崩溃
      // Text(`count V1: ${this.observedClass.count}`)
    }
  }
}
```

### 内置类型
以Array为例。
**V1->V2**
```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, Button, ClickEvent, State, Param } from '@kit.ArkUI';

@Entry
@Component
struct CompV1 {
  @State arr: Array<number> = [1.0, 2.0, 3.0];

  build() {
    Column() {
      Text(`V1 ${this.arr[0]}`)
      Button('Change object in V1')
        .onClick(() => {
          // 点击触发ArrayCompV1和ArrayCompV2变化
          this.arr[0]++;
        })
      ArrayCompV2({ arr: this.arr })
    }
    .height('100%')
    .width('100%')
  }
}

@ComponentV2
struct ArrayCompV2 {
  @Param arr: Array<number> = [1.0, 2.0, 3.0];

  build() {
    Column() {
      Text(`V2 ${this.arr[0]}`)
      Button('Change object in V2')
        .onClick(() => {
          // 点击触发ArrayCompV1和ArrayCompV2变化
          this.arr[0]++;
        })
    }
  }
}
```


**V2->V1**
```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, Button, ClickEvent, Local, ObjectLink } from '@kit.ArkUI';

@Entry
@ComponentV2
struct CompV2 {
  @Local arr: Array<number> = [1, 2, 3];

  build() {
    Column() {
      Text(`V2 ${this.arr[0]}`).fontSize(20)
      Button('Change object in V2')
        .onClick(() => {
          // 点击触发V2变化，且同步给V1 @ObjectLink
          this.arr[0]++;
        })
      ArrayCompV1({ arr: this.arr })
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct ArrayCompV1 {
  @ObjectLink arr: Array<number>;

  build() {
    Column() {
      Text(`V1 ${this.arr[0]}`).fontSize(20)
      Button('Change object in V1')
        .onClick(() => {
          // 点击触发V1变化，且双向同步回给V2
          this.arr[0]++;
        })
    }
  }
}

```


### 二维数组
**V1->V2**

下面的示例中：
- ArkTS-Sta状态变量已默认具有V2的观察能力，因此可直接传递至V2子组件。

```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, Button, ClickEvent, Divider, ForEach, Row, Require, Param, State } from '@kit.ArkUI';

@ComponentV2
struct Item {
  @Require @Param itemArr: Array<string>;

  build() {
    Row() {
      ForEach(this.itemArr, (item: string, index: int) => {
        Text(`${index}: ${item}`)
      }, (item: string) => item + Math.random())

      Button('@Param push')
        .onClick(() => {
          this.itemArr.push('Param');
        })
    }
  }
}

@Entry
@Component
struct CompV1 {
  @State arr: Array<Array<string>> =
    [['apple'], ['banana'], ['orange']];

  build() {
    Column() {
      ForEach(this.arr, (itemArr: Array<string>) => {
        Item({ itemArr: itemArr })
      }, (itemArr: Array<string>) => JSON.stringify(itemArr) + Math.random())
      Divider()
      Button('@State push two-dimensional array item')
        .onClick(() => {
          this.arr[0].push('strawberry');
        })

      Button('@State push array item')
        .onClick(() => {
          this.arr.push(['pear']);
        })

      Button('@State change two-dimensional array first item')
        .onClick(() => {
          this.arr[0][0] = 'APPLE';
        })

      Button('@State change array first item')
        .onClick(() => {
          this.arr[0] = ['watermelon'];
        })
    }
  }
}
```

**V2->V1**

下面的示例中：
- V2中的二维数组已具有V2观察能力，在V1中使用\@ObjectLink接收二维数组的内层数组，点击`Button('@ObjectLink push')`，会正常响应刷新。

```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, Button, ClickEvent, Divider, ForEach, Row, ObjectLink, Local } from '@kit.ArkUI';

@Component
struct Item {
  @ObjectLink itemArr: Array<string>;

  build() {
    Row() {
      ForEach(this.itemArr, (item: string, index: int) => {
        Text(`${index}: ${item}`)
      }, (item: string) => item + Math.random())

      Button('@ObjectLink push')
        .onClick(() => {
          this.itemArr.push('ObjectLink');
        })
    }
  }
}

@Entry
@ComponentV2
struct IndexPage {
  @Local arr: Array<Array<string>> = [['apple'], ['banana'], ['orange']];

  build() {
    Column() {
      ForEach(this.arr, (itemArr: Array<string>) => {
        Item({ itemArr: itemArr })
      }, (itemArr: Array<string>) => JSON.stringify(itemArr) + Math.random())
      Divider()
      Button('@Local push two-dimensional array item')
        .onClick(() => {
          this.arr[0].push('strawberry');
        })

      Button('@Local push array item')
        .onClick(() => {
          this.arr.push(['pear']);
        })

      Button('@Local change two-dimensional array first item')
        .onClick(() => {
          this.arr[0][0] = 'APPLE';
        })

      Button('@Local change array first item')
        .onClick(() => {
          this.arr[0] = ['watermelon'];
        })
    }
  }
}
```

### 嵌套类型
**V1->V2**
结合上述基本场景，下面是嵌套场景的示例。
下面示例的行为可以总结为：

- [\@State](arkts-static-state.md)仅能观察第一层的变化，如果要深度观察，需要传递给\@ObjectLink。
- 数据源\@State的第二层的改变，虽然不能带来本层的刷新，但会被\@ObjectLink和\@Param观察到，并触发它们关联组件的刷新。
- \@ObjectLink和\@Param是同一个对象的引用，其属性改变也会带来其他引用的刷新。

完整示例如下。
```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, Button, ClickEvent, ForEach, Observed, State, Track, ObjectLink, Require, Param } from '@kit.ArkUI';

@Observed
class ArrayItem {
  value: number = 0;

  constructor(value: number) {
    this.value = value;
  }
}

@Observed
class Inner {
  innerValue: string = 'inner';
  arr: Array<ArrayItem>;

  constructor(arr: Array<ArrayItem>) {
    this.arr = arr;
  }
}

@Observed
class Outer {
  @Track outerValue: string = 'out';
  @Track inner: Inner;

  constructor(inner: Inner) {
    this.inner = inner;
  }
}

@Entry
@Component
struct CompV1 {
  // 需保证每一层都是V1的状态变量
  @State outer: Outer =
    new Outer(
      new Inner([
        new ArrayItem(1),
        new ArrayItem(2)
      ])
    );

  build() {
    Column() {
      Text(`@State outer.outerValue can update ${this.outer.outerValue}`)
        .fontSize(20)
        .onClick(() => {
          // @State可以观察第一层的变化
          // 变化会通知@ObjectLink和@Param刷新
          this.outer.outerValue += '!';
        })

      Text(`@State outer.inner.innerValue cannot update ${this.outer.inner.innerValue}`)
        .fontSize(20)
        .onClick(() => {
          // @State无法观察第二层的变化
          // 但该变化会被@ObjectLink和@Param观察
          this.outer.inner.innerValue += '!';
        })
      // 将inner传递给@ObjectLink可观察inner属性的变化
      NestedClassV1ObjectLink({ inner: this.outer.inner })
      // 将outer传给V2
      NestedClassV2({ outer: this.outer })
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct NestedClassV1ObjectLink {
  @ObjectLink inner: Inner;

  build() {
    Text(`@ObjectLink inner.innerValue can update ${this.inner.innerValue}`)
      .fontSize(20)
      .onClick(() => {
        // 可以触发刷新，和@Param是同一个对象的引用，@Param也会进行刷新
        this.inner.innerValue += '!';
      })
  }
}

@ComponentV2
struct NestedClassV2 {
  @Require @Param outer: Outer;

  build() {
    Column() {
      Text(`@Param outer.outerValue can update ${this.outer.outerValue}`)
        .fontSize(20)
        .onClick(() => {
          // 可以观察第一层的变化
          this.outer.outerValue += '!';
        })
      Text(`@Param outer.inner.innerValue can update ${this.outer.inner.innerValue}`)
        .fontSize(20)
        .onClick(() => {
          // 可以观察第二层的变化，和@ObjectLink是同一个对象的引用，也会触发刷新
          this.outer.inner.innerValue += '!';
        })

      ForEach(this.outer.inner.arr, (item: ArrayItem, index: int) => {
        Text(`${index}: ${item.value}`)
      }, (item: ArrayItem) => '' + item.value + Math.random())

      Button('@Param push')
        .onClick(() => {
          // outer已经使能了V2观察能力，对于新增加的数据，则默认开启V2观察能力
          this.outer.inner.arr.push(new ArrayItem(20));
        })

      Button('@Param change the last Item')
        .onClick(() => {
          // 可以观察最后一个数组项的属性变化
          this.outer.inner.arr[this.outer.inner.arr.length - 1].value++;
        })
    }
  }
}
```

**V2->V1**
- V1中仅能观察第一层的变化，所以需要多层自定义组件，且每层都配合使用\@ObjectLink来接收，从而实现深度观察能力。

```ts
'use static'
import { Entry, Text, Column, Component, ComponentV2, Button, ClickEvent, ForEach, Observed, Track, ObjectLink, Local } from '@kit.ArkUI';

@Observed
class ArrayItem {
  value: number = 0;

  constructor(value: number) {
    this.value = value;
  }
}

@Observed
class Inner {
  innerValue: string = 'inner';
  arr: Array<ArrayItem>;

  constructor(arr: Array<ArrayItem>) {
    this.arr = arr;
  }
}

@Observed
class Outer {
  @Track outerValue: string = 'out';
  @Track inner: Inner;

  constructor(inner: Inner) {
    this.inner = inner;
  }
}

@Entry
@ComponentV2
struct CompV2 {
  // 需保证每一层都是V1的状态变量
  @Local outer: Outer =
    new Outer(
      new Inner([
        new ArrayItem(1),
        new ArrayItem(2)
      ]));

  build() {
    Column() {
      Text(`@Local outer.outerValue can update ${this.outer.outerValue}`)
        .fontSize(20)
        .onClick(() => {
          // 可观察第一层的变化
          this.outer.outerValue += '!';
        })

      Text(`@Local outer.inner.innerValue can update ${this.outer.inner.innerValue}`)
        .fontSize(20)
        .onClick(() => {
          // 可观察第二层的变化
          this.outer.inner.innerValue += '!';
        })
      // 将inner传递给@ObjectLink可观察inner属性的变化
      NestedClassV1ObjectLink({ inner: this.outer.inner })
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct NestedClassV1ObjectLink {
  @ObjectLink inner: Inner;

  build() {
    Column() {
      Text(`@ObjectLink inner.innerValue can update ${this.inner.innerValue}`)
        .fontSize(20)
        .onClick(() => {
          // 可以触发刷新
          this.inner.innerValue += '!';
        })
      NestedClassV1ObjectLinkArray({ arr: this.inner.arr })
    }
  }
}

@Component
struct NestedClassV1ObjectLinkArray {
  @ObjectLink arr: Array<ArrayItem>;

  build() {
    Column() {
      ForEach(this.arr, (item: ArrayItem) => {
        NestedClassV1ObjectLinkArrayItem({ item: item })
      }, (item: ArrayItem, index: int) => {
        return item.value.toString() + index.toString();
      })

      Button('@ObjectLink push')
        .onClick(() => {
          this.arr.push(new ArrayItem(20));
        })

      Button('@ObjectLink change the last Item')
        .onClick(() => {
          // 在NestedClassV1ObjectLinkArrayItem中可以观察最后一个数组项的属性变化
          this.arr[this.arr.length - 1].value++;
        })
    }
  }
}

@Component
struct NestedClassV1ObjectLinkArrayItem {
  @ObjectLink item: ArrayItem;

  build() {
    Text(`@ObjectLink outer.inner.arr item: ${this.item.value}`)
  }
}

```