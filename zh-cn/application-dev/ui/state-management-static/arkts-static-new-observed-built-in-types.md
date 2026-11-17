# ObservedArray/ObservedMap/ObservedSet/ObservedDate：具有观察能力的Built-in类型

从API version 26.0.0开始，ArkTS-Sta提供`ObservedArray`、`ObservedMap`、`ObservedSet`和`ObservedDate`，用于创建具有观察能力的Built-in类型。需注意的是，此处的“具有观察能力”，是指具有API操作可观察能力。相关接口定义详见[ObservedArray](../../reference/apis-arkui/js-apis-stateManagement-static.md#observedarrayt)、[ObservedMap](../../reference/apis-arkui/js-apis-stateManagement-static.md#observedmapk-v)、[ObservedSet](../../reference/apis-arkui/js-apis-stateManagement-static.md#observedsetk)、[ObservedDate](../../reference/apis-arkui/js-apis-stateManagement-static.md#observeddate)。

## 概述

- `ObservedArray`、`ObservedMap`、`ObservedSet`和`ObservedDate`分别继承自`Array`、`Map`、`Set`和`Date`。
- 使用这些类型创建的对象直接具备API操作可观察能力，不依赖于状态管理装饰器（例如[@State](./arkts-static-state.md)等）的自动添加观察能力。
- 使用这些类型创建的对象不具备一层观察能力，如果想让继承这些类型的子类也具备观察能力，则可使用[@Observed](./arkts-static-observed-and-objectlink.md)/[@ObservedV2](./arkts-static-new-observedV2-and-trace.md)装饰，示例详见[常见问题](#常见问题)。

在静态语言上下文中使用时，需要导入对应类型：

```ts
import { ObservedArray, ObservedDate, ObservedMap, ObservedSet } from '@kit.ArkUI';
```

## 使用场景

以下示例展示了使用基本的API操作，会触发Text组件中显示的内容的刷新。

### 使用ObservedArray

`ObservedArray`为可观察API操作的Array对象，支持以下构造方式：

- `new ObservedArray<T>()`
- `new ObservedArray<T>(first: T, ...d: T[])`
- `new ObservedArray<T>(arrayLen: int, initializer: (index: int) => T)`

示例：

<!-- @[observed_array_usage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ObservedBuiltInTypes/entry/src/main/ets/pages/ObservedArrayUsage.ets) -->

``` TypeScript
import { Button, Column, Component, Entry, Text, ObservedArray } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // 直接创建ObservedArray实例即具有API操作可观察能力，不依赖于状态管理装饰器。
  arr: ObservedArray<int> = new ObservedArray<int>(3, (index: int): int => index);

  build() {
    Column() {
      Text(`${this.arr}`)
      Button('push')
        .onClick(() => {
          // 添加元素，UI会刷新
          this.arr.push(this.arr.length);
        })
      Button('reverse')
        .onClick(() => {
          // 翻转arr中的元素，UI会刷新
          this.arr.reverse();
        })
    }
  }
}
```

### 使用ObservedMap

`ObservedMap`为可观察API操作的Map对象，支持以下构造方式：

- `new ObservedMap<K, V>()`
- `new ObservedMap<K, V>(initialCapacity: int)`
- `new ObservedMap<K, V>(entries: [K, V][])`
- `new ObservedMap<K, V>(map: Map<K, V>)`

示例：

<!-- @[observed_map_usage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ObservedBuiltInTypes/entry/src/main/ets/pages/ObservedMapUsage.ets) -->

``` TypeScript
import { Button, Column, Component, Divider, Entry, ForEach, ObservedMap, Row, Text } from '@kit.ArkUI';

@Entry
@Component
struct MapSample {
  // 直接创建ObservedMap实例即具有API操作可观察能力，不依赖于状态管理装饰器。
  message: ObservedMap<int, string> = new ObservedMap<int, string>([[0, 'a'], [1, 'b']]);

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.message.entries()), (item: [int, string]) => {
          Text(`${item[0]}: ${item[1]}`)
          Divider()
        })
        Button('set')
          .onClick(() => {
            // 添加新的键值对，UI会刷新
            this.message.set(2, 'c');
          })
        Button('delete')
          .onClick(() => {
            // 删除key为0的键值对，UI会刷新
            this.message.delete(0);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 使用ObservedSet

`ObservedSet`为可观察API操作的Set对象，支持以下构造方式：

- `new ObservedSet<K>()`
- `new ObservedSet<K>(bucketsCount: int)`
- `new ObservedSet<K>(values: K[])`
- `new ObservedSet<K>(set: Set<K>)`

示例：

<!-- @[observed_set_usage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ObservedBuiltInTypes/entry/src/main/ets/pages/ObservedSetUsage.ets) -->

``` TypeScript
import { Button, Column, Component, Divider, Entry, ForEach, ObservedSet, Row, Text } from '@kit.ArkUI';

@Entry
@Component
struct SetSample {
  // 直接创建ObservedSet实例即具有API操作可观察能力，不依赖于状态管理装饰器。
  message: ObservedSet<int> = new ObservedSet<int>([0, 1, 2, 3]);

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.message.values()), (item: int) => {
          Text(`${item}`)
          Divider()
        })
        Button('add')
          .onClick(() => {
            // 添加元素，UI会刷新
            this.message.add(this.message.size);
          })
        Button('delete')
          .onClick(() => {
            // 移除值为0的元素，UI会刷新
            this.message.delete(0);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 使用ObservedDate

`ObservedDate`为可观察API操作的Date对象，支持以下构造方式：

- `new ObservedDate()`
- `new ObservedDate(value: long | string | Date)`

示例：

<!-- @[observed_date_usage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ObservedBuiltInTypes/entry/src/main/ets/pages/ObservedDateUsage.ets) -->

``` TypeScript
import { Button, Column, Component, Entry, ObservedDate, Text } from '@kit.ArkUI';

@Entry
@Component
struct DateSample {
  // 直接创建ObservedDate实例即具有API操作可观察能力，不依赖于状态管理装饰器。
  selectedDate: ObservedDate = new ObservedDate('2026-05-01');

  build() {
    Column() {
      Text(`${this.selectedDate}`)
      Button('increase year')
        .onClick(() => {
          // 将selectedDate实例对应的年份加1，UI会刷新
          this.selectedDate.setFullYear(this.selectedDate.getFullYear() + 1);
        })
      Button('increase month')
        .onClick(() => {
          // 将selectedDate实例对应的月份加1，UI会刷新
          this.selectedDate.setMonth(this.selectedDate.getMonth() + 1);
        })
    }
    .width('100%')
  }
}
```

## 与UIUtils.makeObserved的关系

- `UIUtils.makeObserved`适用于将已有的built-in对象或interface字面量转换为可观察对象，可通过设置allowDeep参数控制该对象为一层可观察（对于built-in对象则为API操作可观察）或深层可观察（对于built-in对象则为API操作可观察，其中元素也可深层观察）。
- `ObservedArray`、`ObservedMap`、`ObservedSet`和`ObservedDate`适用于创建可观察API操作的built-in对象。

<!-- @[observed_built_in_types_make_observed](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ObservedBuiltInTypes/entry/src/main/ets/pages/ObservedBuiltInTypesMakeObserved.ets) -->

``` TypeScript
import { Button, Column, Component, Entry, Text, ObservedArray, UIUtils } from '@kit.ArkUI';

export interface Info {
  name: string;
}

@Entry
@Component
struct Index {
  arr: ObservedArray<Info> = new ObservedArray<Info>({ name: 'Hi' } as Info, { name: 'Hello' } as Info);
  arr2: Array<Info> = UIUtils.makeObserved([{ name: 'Hi' } as Info, { name: 'Hello' } as Info], false);
  arr3: Array<Info> = UIUtils.makeObserved([{ name: 'Hi' } as Info, { name: 'Hello' } as Info]);

  build() {
    Column() {
      Text(`${this.arr[0].name}`)
      Button('change arr[0] name')
        .onClick(() => {
          // 由于ObservedArray仅可观察API行为，故修改该属性，UI不会刷新。
          this.arr[0].name += 'Hi';
        })
      Text(`${this.arr2[0].name}`)
      Button('change arr2[0] name')
        .onClick(() => {
          // 由于allowDeep设置为false，故仅可观察API行为，修改该属性，UI不会刷新。
          this.arr2[0].name += 'Hi';
        })
      Text(`${this.arr3[0].name}`)
      Button('change arr3[0] name')
        .onClick(() => {
          // 由于此处未设置allowDeep，默认为深度观察，故修改该属性，UI会刷新。
          this.arr3[0].name += 'Hi';
        })
    }
  }
}
```

## 常见问题

1. ObservedArray/ObservedMap/ObservedSet/ObservedDate创建的实例，仅具备API操作可观察能力，不会对其中的元素添加可观察能力。

    <!-- @[observed_built_in_types_faq1](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ObservedBuiltInTypes/entry/src/main/ets/pages/ObservedBuiltInTypesFAQ1.ets) -->
    
    ``` TypeScript
    import { Button, Column, Component, Entry, Text, ObservedArray } from '@kit.ArkUI';

    export interface Info {
      name: string;
    }

    @Entry
    @Component
    struct Index {
      arr: ObservedArray<Info> = new ObservedArray<Info>(3, (index: int): Info => {
        return { name: ('Hello World ' + index.toString()) } as Info
      });

      build() {
        Column() {
          Text(`${this.arr[0].name}`)
          Button('change arr[0] name')
            .onClick(() => {
              // 由于不会给元素添加代理，所以修改第一个元素的属性，UI不会刷新。
              this.arr[0].name += 'Hi';
            })
        }
      }
    }
    ```

2. 继承ObservedArray/ObservedMap/ObservedSet/ObservedDate类型中的自定义属性没有观察能力。如果需要这些自定义属性具有观察能力，可以使用@Observed/@ObservedV2装饰该子类。

    <!-- @[observed_built_in_types_faq2](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ObservedBuiltInTypes/entry/src/main/ets/pages/ObservedBuiltInTypesFAQ2.ets) -->
    
    ``` TypeScript
    import { Button, Column, Component, Entry, Text, ObservedSet, Observed, ObservedV2, Track, Trace } from '@kit.ArkUI';

    export class UserInfo extends ObservedSet<int> {
      userName: string = 'Jack';

      constructor() {
        super();
      }
    }

    @Observed
    export class UserInfo1 extends ObservedSet<int> {
      @Track userName: string = 'Jack';

      constructor() {
        super();
      }
    }

    @ObservedV2
    export class UserInfo2 extends ObservedSet<int> {
      @Trace userName: string = 'Jack';

      constructor() {
        super();
      }
    }

    @Entry
    @Component
    struct Index {
      arr1: UserInfo = new UserInfo();
      arr2: UserInfo1 = new UserInfo1();
      arr3: UserInfo2 = new UserInfo2();

      build() {
        Column() {
          Text(`${this.arr1.userName}`)
          Button('change arr1 userName')
            .onClick(() => {
              // 修改arr1的userName属性，UI不刷新。
              this.arr1.userName += 'Hi';
            })
          Text(`${this.arr2.userName}`)
          Button('change arr2 userName')
            .onClick(() => {
              // 修改arr2的userName属性，UI会刷新。
              this.arr2.userName += 'Hi';
            })
          Text(`${this.arr3.userName}`)
          Button('change arr3 userName')
            .onClick(() => {
              // 修改arr3的userName属性，UI会刷新。
              this.arr3.userName += 'Hi';
            })
        }
      }
    }
    ```