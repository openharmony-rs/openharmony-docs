# PersistenceV2: 持久化储存UI状态

为了增强状态管理框架对持久化存储UI的能力，开发者可以使用PersistenceV2存储持久化的数据。

PersistenceV2是应用程序中的可选单例对象。此对象的作用是持久化存储UI相关的数据，以确保这些属性在应用程序重新启动时的值与应用程序关闭时的值相同。

PersistenceV2提供状态变量持久化能力，开发者可以通过[connect](../../reference/apis-arkui/js-apis-stateManagement-static.md#connect)或者[globalConnect](../../reference/apis-arkui/js-apis-stateManagement-static.md#globalconnect)绑定同一个key，在状态变量变换和应用冷启动时，实现持久化能力。

在阅读本文档前，建议提前阅读：[\@ComponentV2](./arkts-static-componentv2.md)，[\@ObservedV2和\@Trace](./arkts-static-new-observedV2-and-trace.md)，配合阅读：[PersistenceV2-API文档](../../reference/apis-arkui/js-apis-stateManagement-static.md#persistencev2)。

>**说明：**
>
>从API版本26.0.0开始支持。
>
>globalConnect行为和connect保持一致，唯一的区别为connect的底层存储路径为module级别的路径，而globalConnect的底层存储路径为应用级别。


## 概述

PersistenceV2是在应用UI启动时会被创建的单例。它的目的是为了提供应用状态数据的中心存储，这些状态数据在应用级别都是可访问的。数据通过唯一的键字符串值访问。不同于AppStorageV2，PersistenceV2还将最新数据储存在设备磁盘上（持久化）。这意味着，应用退出再次启动后，依然能保存选定的结果。

对于与PersistenceV2关联的[\@ObservedV2](./arkts-static-new-observedV2-and-trace.md)对象，该对象的[\@Trace](./arkts-static-new-observedV2-and-trace.md)属性的变化，可通过[enableAutoSave](../../reference/apis-arkui/js-apis-stateManagement-static.md#baseconnectoptions)接口控制是否自动持久化。如未设置该参数或设置为true，则修改会自动存储，否则，需要通过调用PersistenceV2的save接口手动持久化。

PersistenceV2可以和UI组件同步，且可以在应用业务逻辑中被访问。

PersistenceV2支持应用的[主线程](../../application-models/thread-model-stage.md)内多个UIAbility实例间的状态共享。

## 使用说明

- connect：创建或获取存储的数据。

>**说明：**
>
>1. 关联[\@Observed](./arkts-static-observed-and-objectlink.md)对象时，由于该类型的name属性未定义，需要指定key或者自定义name属性。
>
>2. 数据存储路径为module级别，即哪个module调用了connect，数据副本存入对应module的持久化文件中。如果多个module使用相同的key，则数据为最先使用connect的module，并且PersistenceV2中的数据也会存入最先使用connect的module里。
>
>3. 因为存储路径在应用第一个ability启动时就已确定，为该ability所属的module。如果一个ability调用了connect，并且该ability能被不同module拉起， 那么ability存在多少种启动方式，就会有多少份数据副本。

- globalConnect：创建或获取存储的数据。
- remove：删除指定key的存储数据。删除PersistenceV2中不存在的key会报警告。
- keys：返回所有PersistenceV2中的key。包括module级别存储路径和应用级别存储路径中的所有key。
- save：手动持久化数据。
- notifyOnError：响应序列化或反序列化失败的回调。将数据存入磁盘时，需要对数据进行序列化；当某个key序列化失败时，错误是不可预知的；可调用该接口捕获异常。

以上接口详细描述请参考[状态管理](../../reference/apis-arkui/js-apis-stateManagement-static.md)。

## globalConnect支持集合类型

globalConnect支持以下类型的持久化：

| 支持类型 | 说明 |
|---------|------|
| **Array** | 数组类型，元素可为任意可序列化类型。 |
| **Map** | 映射表，key仅支持string/number及其子类型。 |
| **Set** | 集合类型，元素可为任意可序列化类型。 |
| **Date** | 日期对象，在持久化时自动完成序列化和反序列化。 |
| **嵌套自定义类** | 通过`defaultSubCreators`提供子对象构造器恢复类型。 |
| **循环引用** | 支持对象间互相引用的正确持久化和恢复。 |

[ConnectOptions](../../reference/apis-arkui/js-apis-stateManagement-static.md#connectoptions)提供可选字段defaultSubCreators，用于为嵌套的自定义类注册构造器，确保持久化数据恢复时能正确还原为类实例。构造器的返回类型必须与注册的className严格一致，如果不一致或未提供对应的构造器，数据将不能正确地恢复，可能会导致使用该数据的地方出现异常。

此外，数值类型（byte/short/int/long/float/double）之间以及与string还支持一定程度的转换容错，当开发者修改数值类型为string时，框架会尝试将数值类型转成string类型。当前支持的转换如下表所示，其中`-`表示不支持转换，`=`表示源类型与目标类型一致，`✓`表示会发生转换。


| 源类型  / 目标类型 | byte | short | int | long | float | double | string |
|----------------------|------|-------|-----|------|-------|--------|--------|
| byte | = | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| short | ✓ | = | ✓ | ✓ | ✓ | ✓ | ✓ |
| int | ✓ | ✓ | = | ✓ | ✓ | ✓ | ✓ |
| long | ✓ | ✓ | ✓ | = | ✓ | ✓ | ✓ |
| float | ✓ | ✓ | ✓ | ✓ | = | ✓ | ✓ |
| double/number | ✓ | ✓ | ✓ | ✓ | ✓ | = | ✓ |
| string | - | - | - | - | - | - | = |

### Array类型

此示例展示通过globalConnect持久化Array类型数据，并在UI中动态添加和展示数组元素。

<!-- @[persistence_v2_array](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2Array.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Button, ForEach, List, ListItem, StorageDefaultSubCreators } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

// 定义嵌套的数据类
@ObservedV2
export class Inner {
  @Trace age: int = 24;
}
@ObservedV2
export class Info {
  @Trace userInfo: int = 1;
  @Trace arr: Array<Inner> = new Array<Inner>();
}
@ObservedV2
export class Person {
  @Trace userName: string = 'John';
  userId: int = 1;
  @Trace info: Info = new Info();
}

// 为所有嵌套类型注册构造器，确保反序列化时恢复正确的类型
const creators = new StorageDefaultSubCreators([
  [Class.from<Person>(), () => new Person()],
  [Class.from<Inner>(), () => new Inner()],
  [Class.from<Info>(), () => new Info()]
]);

@Entry
@ComponentV2
struct PersistenceV2ArrayExample {
  // 通过globalConnect持久化Array<Person>类型数据
  @Local stateVar: Array<Person> = PersistenceV2.globalConnect<Array<Person>>({
    type: Class.from<Array<Person>>(),
    key: 'PersonArray',
    defaultCreator: () => {
      return new Array<Person>();
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;

  build() {
    Column(undefined) {
      Text(`length: ${this.stateVar.length}`)
      // 点击按钮向数组中添加一个新的Person对象
      Button('push')
        .onClick(() => {
          this.stateVar.push(new Person());
        })
      List() {
        ForEach(this.stateVar, (item: Person, index: int) => {
          ListItem() {
            if (item instanceof Person) {
              Column() {
                Text(`item: ${item.userName}`)
                  .fontSize(30)
                  // 点击修改当前item的userName、userInfo，并添加Inner对象到arr中
                  .onClick(() => {
                    item.userName += '~';
                    item.info.userInfo++;
                    let inner = new Inner();
                    inner.age = item.info.userInfo;
                    item.info.arr.push(inner);
                  })
                Text(`userInfo: ${item.info.userInfo}`)
                Text(`arr: ${JSON.stringify(item.info.arr)}`)
              }
            } else {
              Text(`${Class.of(item).getName()}`)
            }
          }
        }, (item: Person, index: int) => {
          return item.userName + item.info.userInfo + Math.random().toString();
        })
      }
    }
  }
}
```

### Map类型

此示例展示通过globalConnect持久化Map类型数据，key为string类型，value为自定义类Person。

<!-- @[persistence_v2_map](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2Map.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Button, List, ListItem, StorageDefaultCreator, ForEach } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

// 定义嵌套的数据类
@ObservedV2
export class Inner {
  @Trace age: int = 24;
}

@ObservedV2
export class Person {
  @Trace userName: string = 'John';
  userId: int = 1;
  @Trace inner: Inner = new Inner();
}

// 为所有嵌套类型注册构造器
const creators = new Map<Class, StorageDefaultCreator<object>>([
  [Class.from<Person>(), () => new Person()],
  [Class.from<Inner>(), () => new Inner()]
]);

@Entry
@ComponentV2
struct PersistenceV2MapExample {
  // 通过globalConnect持久化Map<string, Person>类型数据
  @Local stateVar: Map<string, Person> = PersistenceV2.globalConnect<Map<string, Person>>({
    type: Class.from<Map<string, Person>>(),
    key: 'PersonMap',
    defaultCreator: () => {
      return new Map<string, Person>();
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;

  build() {
    Column(undefined) {
      Text(`map size: ${this.stateVar.size}`)
      // 点击按钮创建一个新的Person对象并添加到Map中
      Button('add')
        .onClick(() => {
          let p = new Person();
          p.userName = 'user_' + this.stateVar.size.toString();
          p.userId = this.stateVar.size;
          p.inner.age = 20 + this.stateVar.size;
          this.stateVar.set('key_' + this.stateVar.size.toString(), p);
        })
      // 点击按钮删除最后一个Map条目
      Button('delete last')
        .onClick(() => {
          this.stateVar.delete('key_' + (this.stateVar.size - 1));
        })
      List() {
        ForEach(Array.from(this.stateVar.entries()), (entry: Tuple2<string, Person>, index: int) => {
          ListItem() {
            Column() {
              let key = entry.$0 as string;
              let val = entry.$1 as Person;
              if (val instanceof Person) {
                Column() {
                  Text(`[${key}] ${val.userName}`)
                    .fontSize(20)
                    // 点击修改当前条目的userName和age
                    .onClick(() => {
                      val.userName += '~';
                      val.inner.age++;
                    })
                  Text(`userId: ${val.userId}, inner.age: ${val.inner.age}`)
                    .fontSize(16)
                }
              }
            }
          }
        }, (entry: Tuple2<string, Person>, index: int) => {
          return entry.$0 + index.toString();
        })
      }
    }
  }
}
```

### Set类型

此示例展示通过globalConnect持久化Set类型数据，元素为自定义类Person。

<!-- @[persistence_v2_set](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2Set.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Button, List, ListItem, ForEach, StorageDefaultCreator } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

// 定义嵌套的数据类
@ObservedV2
export class Inner {
  @Trace age: int = 24;
}

@ObservedV2
export class Person {
  @Trace userName: string = 'John';
  userId: int = 1;
  @Trace inner: Inner = new Inner();
}

// 为所有嵌套类型注册构造器
const creators = new Map<Class, StorageDefaultCreator<object>>([
  [Class.from<Person>(), () => new Person()],
  [Class.from<Inner>(), () => new Inner()]
]);

@Entry
@ComponentV2
struct PersistenceV2SetExample {
  // 通过globalConnect持久化Set<Person>类型数据
  @Local stateVar: Set<Person> = PersistenceV2.globalConnect<Set<Person>>({
    type: Class.from<Set<Person>>(),
    key: 'PersonSet',
    defaultCreator: () => {
      return new Set<Person>();
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;
  // 记录最后添加的Person，用于remove操作
  @Local lastPerson: Person | undefined = undefined;

  build() {
    Column(undefined) {
      Text(`set size: ${this.stateVar.size}`)
      // 点击按钮创建一个新的Person对象并添加到Set中
      Button('add')
        .onClick(() => {
          let p = new Person();
          p.userName = 'user_' + this.stateVar.size.toString();
          p.userId = this.stateVar.size;
          p.inner.age = 20 + this.stateVar.size;
          this.stateVar.add(p);
          this.lastPerson = p;
        })
      // 点击按钮移除Set中最后添加的元素
      Button('remove last')
        .onClick(() => {
          if (this.lastPerson && this.stateVar.has(this.lastPerson!)) {
            this.stateVar.delete(this.lastPerson!);
          } else {
            let s = this.stateVar.size;
            this.stateVar.forEach((val: Person) => {
              if (--s === 0) {
                this.stateVar.delete(val);
              }
            });
          }
        })
      List() {
        ForEach(Array.from(this.stateVar.values()), (item: Person, index: int) => {
          ListItem() {
            Column() {
              if (item instanceof Person) {
                Text(`[${index}] ${item.userName}`)
                  .fontSize(20)
                Text(`userId: ${item.userId}, inner.age: ${item.inner.age}`)
                  .fontSize(16)
              }
            }
          }
        }, (item: Person, index: int) => {
          return item.userId + item.userName + index.toString();
        })
      }
    }
  }
}
```

### Date类型

此示例展示通过globalConnect持久化包含Date类型字段的自定义类，Date对象在持久化时自动完成序列化和反序列化。

<!-- @[persistence_v2_date](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2Date.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Button, StorageDefaultCreator } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

// 定义包含Date字段的嵌套数据类
@ObservedV2
export class Inner {
  @Trace tag: string = 'inner';
  @Trace nextDate: Date = new Date(0);
}

@ObservedV2
export class Event {
  @Trace name: string = 'event';
  @Trace createdAt: Date = new Date(0);
  @Trace lastLogin: Date = new Date(0);
  @Trace inner: Inner = new Inner();
}

// 为所有嵌套类型注册构造器
const creators = new Map<Class, StorageDefaultCreator<object>>([
  [Class.from<Event>(), () => new Event()],
  [Class.from<Inner>(), () => new Inner()]
]);

@Entry
@ComponentV2
struct PersistenceV2DateExample {
  // 通过globalConnect持久化包含Date字段的Event对象
  @Local stateVar: Event = PersistenceV2.globalConnect<Event>({
    type: Class.from<Event>(),
    key: 'EventDate',
    defaultCreator: () => {
      return new Event();
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;

  build() {
    Column(undefined) {
      Text(`name: ${this.stateVar.name}`)
      Text(`createdAt: ${this.stateVar.createdAt.toISOString()}`)
      Text(`lastLogin: ${this.stateVar.lastLogin.toISOString()}`)
      Text(`inner.tag: ${this.stateVar.inner.tag}`)
      Text(`inner.nextDate: ${this.stateVar.inner.nextDate.toISOString()}`)
      // 点击按钮更新所有Date字段和name字段
      Button('update')
        .onClick(() => {
          this.stateVar.createdAt = new Date();
          this.stateVar.lastLogin = new Date();
          this.stateVar.name = 'updated_' + Date.now().toString();
          this.stateVar.inner.nextDate = new Date();
          this.stateVar.inner.tag = 'tag_' + Date.now().toString();
        })
    }
  }
}
```

### 嵌套自定义类

此示例展示通过globalConnect持久化多层嵌套的自定义类（Company → Dept → Person → Inner，共4层），所有层级的类型均需在`defaultSubCreators`中注册。

<!-- @[persistence_v2_nested_class](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2NestedClass.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Button, StorageDefaultCreator } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

// 定义4层嵌套的数据类
@ObservedV2
export class Inner {
  @Trace age: int = 0;
}

@ObservedV2
export class Person {
  @Trace userName: string = '';
  @Trace inner: Inner = new Inner();
}

@ObservedV2
export class Dept {
  @Trace deptName: string = '';
  @Trace person: Person = new Person();
}

@ObservedV2
export class Company {
  @Trace companyName: string = '';
  @Trace dept: Dept = new Dept();
}

// 为所有层级的嵌套类型注册构造器
const creators = new Map<Class, StorageDefaultCreator<object>>([
  [Class.from<Company>(), () => new Company()],
  [Class.from<Dept>(), () => new Dept()],
  [Class.from<Person>(), () => new Person()],
  [Class.from<Inner>(), () => new Inner()]
]);

@Entry
@ComponentV2
struct PersistenceV2NestedClassExample {
  // 通过globalConnect持久化多层嵌套的Company对象
  @Local stateVar: Company = PersistenceV2.globalConnect<Company>({
    type: Class.from<Company>(),
    key: 'Company',
    defaultCreator: () => {
      return new Company();
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;

  build() {
    Column(undefined) {
      Text(`company: ${this.stateVar.companyName}`)
      Text(`dept: ${this.stateVar.dept.deptName}`)
      Text(`person: ${this.stateVar.dept.person.userName}`)
      Text(`inner.age: ${this.stateVar.dept.person.inner.age}`)
      // 点击按钮初始化所有层级的嵌套数据
      Button('init')
        .onClick(() => {
          this.stateVar.companyName = 'MyCompany';
          this.stateVar.dept.deptName = 'Engineering';
          this.stateVar.dept.person.userName = 'Alice';
          this.stateVar.dept.person.inner.age = 30;
        })
      // 点击按钮逐级修改嵌套数据
      Button('modify')
        .onClick(() => {
          this.stateVar.companyName += '_v2';
          this.stateVar.dept.deptName += '_upd';
          this.stateVar.dept.person.userName += '!';
          this.stateVar.dept.person.inner.age += 1;
        })
    }
  }
}
```

### 循环引用

此示例展示通过globalConnect持久化包含循环引用的对象。Node的parent字段可指向自身或另一个Node，globalConnect内部会自动处理对象间的引用关系，不会无限递归。

<!-- @[persistence_v2_circular_ref](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2CircularRef.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Button, StorageDefaultCreator } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

// 定义包含循环引用的Node类，parent可指向自身
@ObservedV2
export class Node {
  @Trace name: string = '';
  @Trace value: int = 0;
  @Trace parent: Node | undefined = undefined;
}

// 为Node类型注册构造器
const creators = new Map<Class, StorageDefaultCreator<object>>([
  [Class.from<Node>(), () => new Node()]
]);

@Entry
@ComponentV2
struct PersistenceV2CircularRefExample {
  // 通过globalConnect持久化包含循环引用的Node对象
  @Local stateVar: Node = PersistenceV2.globalConnect<Node>({
    type: Class.from<Node>(),
    key: 'NodeCircular',
    defaultCreator: () => {
      let root = new Node();
      root.name = 'root';
      root.value = 1;
      root.parent = root; // 设置自引用，演示循环引用的持久化
      return root;
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;

  build() {
    Column(undefined) {
      Text(`name: ${this.stateVar.name}`)
      Text(`value: ${this.stateVar.value}`)
      if (this.stateVar.parent !== undefined) {
        Text(`parent.name: ${this.stateVar.parent!.name}`)
        Text(`parent === self: ${this.stateVar.parent === this.stateVar}`)
          .fontSize(20)
      } else {
        Text(`parent: undefined`)
      }
      // 点击按钮将parent设为自身引用并修改name和value
      Button('set self-ref')
        .onClick(() => {
          this.stateVar.parent = this.stateVar;
          this.stateVar.name = 'root_' + Date.now().toString();
          this.stateVar.value += 1;
        })
      // 点击按钮清除循环引用
      Button('clear ref')
        .onClick(() => {
          this.stateVar.parent = undefined;
        })
    }
  }
}
```

### 多种集合类型混合

此示例展示通过globalConnect持久化一个包含Array、Map、Set三种集合类型的自定义类MixedData。

<!-- @[persistence_v2_mixed_collection](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2MixedCollection.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Button, List, ListItem, ForEach, StorageDefaultCreator } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

// 定义嵌套的数据类
@ObservedV2
export class Inner {
  @Trace age: int = 0;
}

@ObservedV2
export class Person {
  @Trace userName: string = '';
  @Trace inner: Inner = new Inner();
}

// 定义包含多种集合类型的数据类
@ObservedV2
export class MixedData {
  @Trace tags: Array<string> = new Array<string>();
  @Trace people: Map<string, Person> = new Map<string, Person>();
  @Trace unique: Set<Person> = new Set<Person>();
}

// 为所有嵌套类型注册构造器
const creators = new Map<Class, StorageDefaultCreator<object>>([
  [Class.from<MixedData>(), () => new MixedData()],
  [Class.from<Person>(), () => new Person()],
  [Class.from<Inner>(), () => new Inner()]
]);

@Entry
@ComponentV2
struct PersistenceV2MixedCollectionExample {
  // 通过globalConnect持久化包含Array、Map、Set的MixedData对象
  @Local stateVar: MixedData = PersistenceV2.globalConnect<MixedData>({
    type: Class.from<MixedData>(),
    key: 'MixedData',
    defaultCreator: () => {
      return new MixedData();
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;

  build() {
    Column(undefined) {
      Text(`tags: ${this.stateVar.tags.length}`)
        .fontSize(20)
      Text(`people: ${this.stateVar.people.size}`)
        .fontSize(20)
      Text(`unique: ${this.stateVar.unique.size}`)
        .fontSize(20)

      // 点击按钮初始化所有集合数据
      Button('init all')
        .onClick(() => {
          this.stateVar.tags.push('tag_a', 'tag_b', 'tag_c');
          let p1 = new Person();
          p1.userName = 'alice';
          p1.inner.age = 25;
          let p2 = new Person();
          p2.userName = 'bob';
          p2.inner.age = 30;
          this.stateVar.people.set('alice', p1);
          this.stateVar.people.set('bob', p2);
          this.stateVar.unique.add(p1);
          this.stateVar.unique.add(p2);
        })
      // 点击按钮向tags数组中添加新标签
      Button('add tag')
        .onClick(() => {
          this.stateVar.tags.push('tag_' + this.stateVar.tags.length.toString());
        })
      // 点击按钮创建新的Person对象并添加到Map中
      Button('add person to map')
        .onClick(() => {
          let p = new Person();
          p.userName = 'user_' + this.stateVar.people.size.toString();
          p.inner.age = 20 + this.stateVar.people.size;
          this.stateVar.people.set(p.userName, p);
        })
      // 点击按钮创建新的Person对象并添加到Set中
      Button('add person to set')
        .onClick(() => {
          let p = new Person();
          p.userName = 'set_' + this.stateVar.unique.size.toString();
          p.inner.age = 20 + this.stateVar.unique.size;
          this.stateVar.unique.add(p);
        })

      // 展示tags数组内容
      Text('--- tags ---')
        .fontSize(16)
      List() {
        ForEach(this.stateVar.tags, (tag: string, index: int) => {
          ListItem() {
            Text(`[${index}] ${tag}`)
              .fontSize(16)
          }
        }, (tag: string, index: int) => {
          return tag + index.toString();
        })
      }

      // 展示people Map内容
      Text('--- people (map) ---')
        .fontSize(16)
      List() {
        ForEach(Array.from(this.stateVar.people.entries()), (entry: Tuple2<string, Person>, index: int) => {
          ListItem() {
            Column() {
              if (entry.$1 instanceof Person) {
                Text(`${entry.$0}: ${entry.$1.userName} (age ${entry.$1.inner.age})`)
                  .fontSize(16)
              }
            }
          }
        }, (entry: Tuple2<string, Person>, index: int) => {
          return entry.$0 + index.toString();
        })
      }

      // 展示unique Set内容
      Text('--- unique (set) ---')
        .fontSize(16)
      List() {
        ForEach(Array.from(this.stateVar.unique.values()), (item: Person, index: int) => {
          ListItem() {
            Column() {
              if (item instanceof Person) {
                Text(`${item.userName} (age ${item.inner.age})`)
                  .fontSize(16)
              }
            }
          }
        }, (item: Person, index: int) => {
          return item.userName + index.toString();
        })
      }
    }
  }
}
```

## 使用限制

1. 不支持非built-in类型，如[PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md)、NativePointer、[ArrayList](../../reference/apis-arkts/js-apis-arraylist.md)等Native类型，使用会编译报错。

2. connect接口持久化的数据必须是class对象，不支持容器类型（如Array、Set、Map），不支持built-in的构造对象（如Date），不支持持久化基本类型（如string、number、boolean），使用会运行时报错。globalConnect接口支持Array、Map、Set、Date等集合类型及嵌套自定义类和循环引用，需配合[defaultSubCreators](../../reference/apis-arkui/js-apis-stateManagement-static.md#connectoptions)使用，详见[globalConnect支持集合类型](#globalconnect支持集合类型)。如果需要持久化非class对象且不使用globalConnect，建议使用[Preference](../../database/preferences-guidelines.md)进行数据持久化。

3. connect接口不支持循环引用的对象，使用会编译报错。globalConnect接口支持循环引用，详见[globalConnect支持集合类型](#globalconnect支持集合类型)。

4. 不宜大量持久化数据，可能会导致页面卡顿。

5. connect和globalConnect不建议混用，如果混用，key必须不一致，否则会运行时报错。

6. PersistenceV2必须与UI实例关联，持久化操作需在UI实例初始化完成后调用（即[loadContent](../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)回调触发后）。

   ```ts
   // EntryAbility.ets
   // 以下为代码片段，需要开发者自己在EntryAbility.ets中补全
   import { PersistenceV2, ObservedV2 } from '@kit.ArkUI';
   
   // 在EntryAbility外部定义class
   @ObservedV2
   class Storage {
     @Trace isPersist: boolean = false;
   }
   
   // 在onWindowStageCreate的loadContent回调中调用PersistenceV2
   onWindowStageCreate(windowStage: window.WindowStage): void {
     windowStage.loadContent('pages/Index', (err) => {
       if (err.code) {
         return;
       }
       PersistenceV2.connect<Storage>(
         Class.from<Storage>(),
         (): Storage => {
           return new Storage();
         })!;
     });
   }
   ```

7. 当存储数据的结构与当前数据的结构不一致时，可能会导致反序列化失败。[PersistenceErrorCallback](../../reference/apis-arkui/js-apis-stateManagement-static.md#persistenceerrorcallback)支持传入oldValue参数，开发者可通过该参数获取存于磁盘的旧的序列化数据，具体用例可见[通过notifyOnError获取旧的序列化数据](#通过notifyonerror获取旧的序列化数据)。

8. 使用globalConnect持久化集合类型时，Map的key仅支持string和number类型（含byte/short/int/long/float），使用不支持的key类型会导致整个Map被存储为空Map。

9. 使用globalConnect持久化集合类型时，如果磁盘数据的首个元素类型与目标容器首个元素类型不一致，会导致跳过恢复容器，即不使用磁盘数据重新填充容器，而是使用[defaultCreator](../../reference/apis-arkui/js-apis-stateManagement-static.md#connectoptions)中的默认值。

10. 使用globalConnect持久化集合类型时，如果[defaultSubCreators](../../reference/apis-arkui/js-apis-stateManagement-static.md#connectoptions)中注册的构造器返回了错误类型（如Person的构造器返回Dog），会导致该元素被跳过，不影响其他元素。

11. 使用globalConnect持久化集合类型时，如果磁盘数据包含嵌套对象但未在[defaultSubCreators](../../reference/apis-arkui/js-apis-stateManagement-static.md#connectoptions)中提供对应构造器，会导致该字段无法正确恢复为对应类实例。

12. 使用globalConnect持久化集合类型时，如果磁盘中的数值类型与目标字段类型不同，会尝试类型转换，转换失败则保留默认值。

## 使用场景

### 使用connect、globalConnect存储数据

此示例结合enableAutoSave参数确定是否自动持久化存储数据。

<!-- @[persistence_v2_connect_global_connect](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2ConnectGlobalConnect.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Local, Entry, 
  Button, Column, ClickEvent, ComponentV2, Text, ConnectOptions } from '@kit.ArkUI';

import contextConstant from '@ohos.app.ability.contextConstant';

// 接受序列化失败的回调
PersistenceV2.notifyOnError((key: string, reason: string, msg: string, oldValue?: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@ObservedV2
class Info {
  @Trace userInfo: int = 1;
}

@ObservedV2
class Person {
  @Trace userName: string = 'John';
  userId: int = 1;
  @Trace info: Info = new Info();
}

@Entry
@ComponentV2
struct PersistenceV2ConnectGlobalConnectExample {
  // 调用globalConnect存储key为Person的对象，并返回。
  @Local cp1: Person = PersistenceV2.globalConnect<Person>({
    type: Class.from<Person>(),
    key: 'PersistenceV2Connect',
    defaultCreator: (): Person => {
      return new Person();
    },
    areaMode: contextConstant.AreaMode.EL1, // EL1-EL5代表5种加密等级。
    enableAutoSave: false  // 不自动持久化存储，需要开发者使用save接口手动持久化存储。
  })!;

  @Local cp2: Person = PersistenceV2.connect<Person>(
    Class.from<Person>(),
    'Person1',
    (): Person => {
      return new Person();
    }, {
      enableAutoSave: true, // 持久化存储
    }
  )!;

  options: ConnectOptions<Person> =
    { type: Class.from<Person>(), key: 'Person2', defaultCreator: () => new Person(), areaMode: contextConstant.AreaMode.EL1, enableAutoSave: true} as ConnectOptions<Person>;
  @Local refresh: number = 0;

  build() {
    Column() {
      Button('Change cp1 userId userName userInfo')
        .onClick((e: ClickEvent) => {
          this.cp1.userId++;
          this.cp1.userName += 'A';
          this.cp1.info.userInfo += 100;
          console.info(`cp1 userId ${this.cp1.userId}`);
        })
      Text(`userName: ${this.cp1.userName}`) // Person类由@ObservedV2装饰，且该属性由@Trace装饰，所以可观测刷新。
      Text(`userId: ${this.cp1.userId}`) // Person类由@ObservedV2装饰，但该属性非@Trace装饰，所以刷新不可观测。
      Text(`userInfo: ${this.cp1.info.userInfo}`) // Info类由@ObservedV2装饰，且userInfo属性由@Track装饰，所以可观测刷新。

      Button('Change cp2 userId userName userInfo')
        .onClick((e: ClickEvent) => {
          this.cp2.userId++;
          this.cp2.userName += 'A';
          this.cp2.info.userInfo += 100;
          console.info(`cp2 userId ${this.cp2.userId}`);
        })
      Text(`userName: ${this.cp2.userName}`) // Person类由@ObservedV2装饰，且该属性由@Trace装饰，所以可观测刷新。
      Text(`userId: ${this.cp2.userId}`) // Person类由@ObservedV2装饰，但该属性非@Trace装饰，所以刷新不可观测。
      Text(`userInfo: ${this.cp2.info.userInfo}`) // Info类由@ObservedV2装饰，且userInfo属性由@Track装饰，所以可观测刷新。

      Text(`save key Person userId: ${this.cp1.userId} refresh: ${this.refresh}`)
      // 点击Text组件后，由于refresh改变，所以引起Text组件刷新，进而使得此处userId刷新。
        .onClick((e: ClickEvent) => {
          this.cp1.userId++;
          PersistenceV2.save('Person'); // 调用save存储该对象。
          this.refresh += 1;
        })
        .fontSize(25)

      Text(`PersistenceV2 keys: ${PersistenceV2.keys()} refresh: ${this.refresh}`)
        .onClick(() => {
          this.refresh += 1;
        })
        .fontSize(25)

      Text('Remove key Person: ' + 'refresh: ' + this.refresh)
        .onClick((e: ClickEvent) => {
          // 在PersistenceV2中删除keyorType为Person的对象。
          PersistenceV2.remove('Person');
          this.refresh += 1;
        })
        .fontSize(25)

      Text('globalConnect key Person2: ' + 'refresh: ' + this.refresh)
        .onClick((e: ClickEvent) => {
          this.cp1 = PersistenceV2.globalConnect<Person>(this.options)!;
          this.refresh += 1;
        })
        .fontSize(25)
    }
    .width('100%')
    .height('100%')
  }
}
```

### 通过notifyOnError获取旧的序列化数据

当存储数据的结构与当前数据的结构不同时，可能会导致反序列化失败。开发者可通过向notifyOnError的回调函数参数中加入oldValue参数来获取存于磁盘的旧的序列化数据，从而直观地感知到数据结构的差异。

<!-- @[persistence_v2_notify_on_error](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2NotifyOnError.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Color } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

@ObservedV2
export class SampleInfo {
  @Trace public info: boolean = true;
  @Trace public propertyName: string = 'Hello';
}

@ObservedV2
export class SampleChild {
  // 起始时childInfo类型为SampleInfo，使用connect/globalConnect将其存储到磁盘
  @Trace public childInfo: SampleInfo = new SampleInfo();
  // 将childInfo类型切换为number，并重新运行
  // @Trace public childInfo: number = 0;
  public groupId: number = 1;
}

@ObservedV2
export class Sample {
  @Trace public father: SampleChild = new SampleChild();
}

@Entry
@ComponentV2
struct PersistenceV2NotifyOnErrorExample {
  static {
    // 接受序列化失败的回调
    PersistenceV2.notifyOnError((key: string, reason: string, msg: string, oldValue?: string) => {
      hilog.error(DOMAIN, 'testTag', '%{public}s',
        `error key: ${key}, reason: ${reason}, message: ${msg}, oldValue: ${oldValue}`);
    });
  }
  @Local refresh: number = 0;
  // 调用connect存储
  @Local p: Sample = PersistenceV2.connect<Sample>(Class.from<Sample>(), 'connectSample', () => new Sample())!;

  build() {
    Column() {
      // 显示数据
      Text('Key connectSample: ' + this.p.father.groupId.toString())
        .onClick(() => {
          this.p.father.groupId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)

      // save接口
      // 未被@Trace装饰的变量需要借助状态变量refresh才能刷新
      Text('save key connect3: ' + this.p.father.groupId.toString() + ' refresh:' + this.refresh)
        .onClick(() => {
          // 未被@Trace保存的对象无法自动存储，需要调用save存储
          this.p.father.groupId += 1;
          PersistenceV2.save('connectSample');
          this.refresh += 1;
        })
        .fontSize(25)
    }
    .width('100%')
  }
}
```
初始时，SampleChild中的childInfo变量类型为SampleInfo，正常存储后，将childInfo变量的类型切换为number，并赋值为1，之后再次启动应用程序，此时会由于存储数据的结构与当前数据的结构不一致，导致数据反序列化失败。此时会通过notifyOnError中设置的回调函数，将磁盘中存储的旧的序列化数据打印出来。即在Error日志中显示：
```text
error key: connectSample, reason: serialization, message: TypeError: Receiver is not a JSObject, oldValue: {"father":{"childInfo":{"info":true,"propertyName":"Hello"},"groupId":1}}
```

## 使用建议

建议开发者使用新接口globalConnect创建和获取数据。globalConnect的存储规格和内存规格一致，对于应用只有一份，并且支持设置加密级别，不需要去切换ability的加密才能设置数据的加密级别。当然如果开发者应用不涉及多模块，保持使用connect也不会有影响。

### connect向globalConnect迁移实现

<!-- @[persistence_v2_connect_usage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2ConnectUsage.ets) -->

``` TypeScript
// 使用connect存储数据
import { PersistenceV2, ObservedV2, Trace, Local, Entry, 
  Button, Column, ClickEvent, ComponentV2, Text } from '@kit.ArkUI';

// 接受序列化失败的回调
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@ObservedV2
class Info {
  @Trace userInfo: int = 1;
}

@ObservedV2
class Person {
  @Trace userName: string = 'John';
  userId: int = 1;
  @Trace info: Info = new Info();
}

@Entry
@ComponentV2
struct PersistenceV2ConnectUsageExample {
  // 调用connect存储key为Person的对象，并返回。
  @Local cp1: Person = PersistenceV2.connect<Person>(
    Class.from<Person>(),
    'Person',
    (): Person => {
      return new Person();
    })!;
  @Local refresh: number = 0;

  build() {
    Column() {
      Button('Change userId userName userInfo')
        .onClick((e: ClickEvent) => {
          this.cp1.userId++;
          this.cp1.userName += 'A';
          this.cp1.info.userInfo += 100;
          console.info(`cp1 userId ${this.cp1.userId}`);
        })
      Text(`userName: ${this.cp1.userName}`) // Person类由@ObservedV2装饰，且该属性由@Trace装饰，所以可观测刷新。
      Text(`userId: ${this.cp1.userId}`) // Person类由@ObservedV2装饰，但该属性非@Trace装饰，所以刷新不可观测。
      Text(`userInfo: ${this.cp1.info.userInfo}`) // Info类由@ObservedV2装饰，且userInfo属性由@Track装饰，所以可观测刷新。

      Text(`save key Person userId: ${this.cp1.userId} refresh: ${this.refresh}`)
      // 点击Text组件后，由于refresh改变，所以引起Text组件刷新，进而使得此处userId刷新。
        .onClick((e: ClickEvent) => {
          this.cp1.userId++;
          PersistenceV2.save('Person'); // 调用save存储该对象。
          this.refresh += 1;
        })
        .fontSize(25)
    }
    .width('100%')
    .height('100%')
  }
}
```

<!-- @[persistence_v2_connect_migration](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2ConnectMigration.ets) -->

``` TypeScript
// 迁移到globalConnect
import { PersistenceV2, ObservedV2, Trace, Local, Entry, 
  Button, Column, ClickEvent, ComponentV2, Text } from '@kit.ArkUI';

import contextConstant from '@ohos.app.ability.contextConstant';

// 接受序列化失败的回调
PersistenceV2.notifyOnError((key: string, reason: string, msg: string, oldValue?: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@ObservedV2
class Info {
  @Trace userInfo: int = 1;
}

@ObservedV2
class Person {
  @Trace userName: string = 'John';
  userId: int = 1;
  @Trace info: Info = new Info();
}

// 用于判断是否完成数据迁移的辅助数据
@ObservedV2
class StorageState {
  @Trace isCompleteMoving: boolean = false;
}

function move() {
  let movingState =
    PersistenceV2.globalConnect<StorageState>({ type: Class.from<StorageState>(), defaultCreator: () => new StorageState() })!;
  if (!movingState.isCompleteMoving) {
    let p: Person = PersistenceV2.connect<Person>(
      Class.from<Person>(),
      'Person',
      (): Person => {
        return new Person();
      })!;
    PersistenceV2.remove('Person');

    let p1 = PersistenceV2.globalConnect<Person>({
      type: Class.from<Person>(),
      key: 'Person',
      defaultCreator: (): Person => p,
      areaMode: contextConstant.AreaMode.EL1 // EL1-EL5代表5种加密等级。
    })!;
    // 将迁移标志设置为true
    movingState.isCompleteMoving = true;
  }
}

@Entry
@ComponentV2
struct PersistenceV2ConnectMigrationExample {
  // 调用globalConnect存储key为Person的对象，并返回。
  @Local cp1: Person = PersistenceV2.globalConnect<Person>({
    type: Class.from<Person>(),
    key: 'Person',
    defaultCreator: (): Person => {
      return new Person();
    },
    areaMode: contextConstant.AreaMode.EL1 // EL1-EL5代表5种加密等级。
  })!;
  @Local refresh: number = 0;
  // 在ArkTS-Sta中，全局的逻辑代码不会默认执行。开发者可将需要执行的逻辑代码移至static代码块中，以达到与ArkTS-Dyn一样的效果。
  static {
    move();
  }

  build() {
    Column() {
      Button('Change userId userName userInfo')
        .onClick((e: ClickEvent) => {
          this.cp1.userId++;
          this.cp1.userName += 'A';
          this.cp1.info.userInfo += 100;
          console.info(`cp1 userId ${this.cp1.userId}`);
        })
      Text(`userName: ${this.cp1.userName}`) // Person类由@ObservedV2装饰，且该属性由@Trace装饰，所以可观测刷新。
      Text(`userId: ${this.cp1.userId}`) // Person类由@ObservedV2装饰，但该属性非@Trace装饰，所以刷新不可观测。
      Text(`userInfo: ${this.cp1.info.userInfo}`) // Info类由@ObservedV2装饰，且userInfo属性由@Track装饰，所以可观测刷新。

      Text(`save key Person userId: ${this.cp1.userId} refresh: ${this.refresh}`)
      // 点击Text组件后，由于refresh改变，所以引起Text组件刷新，进而使得此处userId刷新。
        .onClick((e: ClickEvent) => {
          this.cp1.userId++;
          PersistenceV2.save('Person'); // 调用save存储该对象。
          this.refresh += 1;
        })
        .fontSize(25)
    }
    .width('100%')
    .height('100%')
  }
}
```

connect向globalConnect迁移，需要将key绑定的value赋值给globalConnect进行存储，之后当自定义组件使用globalConnect连接时，globalConnect绑定的数据即为之前使用connect保存的数据，开发者可以自定义move函数，并将其放在合适位置迁移即可。

## 常见问题

### 容器元素类型变更后重新进入应用数据异常

当开发者将`@Trace`字段的容器元素类型从自定义对象数组`Person[]`改为基本类型数组（如`int[]`），如果defaultCreator中未给数组添加默认元素，此时旧数据中存储的`Person`类型元素会被错误地填充到新类型的数组中，导致运行时类型错误或instanceof检查失败。这是由于框架侧无法获取容器类型的泛型信息，在没有容器默认元素的情况下无法感知到容器元素的类型发生了变更。因此，不建议开发者手动更改容器中的元素类型。

<!-- @[persistence_v2_container_type_error](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2ContainerTypeError.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Button, List, ListItem, ForEach, StorageDefaultCreator } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

@ObservedV2
export class Person {
  @Trace userName: string = 'John';
  userId: int = 1;
}

const creators = new Map<Class, StorageDefaultCreator<object>>([
  [Class.from<Person>(), () => new Person()]
]);

@Entry
@ComponentV2
struct PersistenceV2ContainerTypeErrorExample {
  @Local stateVar: Array<Person> = PersistenceV2.globalConnect<Array<Person>>({
    type: Class.from<Array<Person>>(),
    key: 'PersonArray',
    defaultCreator: () => {
      return new Array<Person>();
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;

  // 以下为错误演示：将元素类型从Person改为int后，未提供默认元素，旧数据被错误恢复
  /* @Local stateVar: Array<int> = PersistenceV2.globalConnect<Array<int>>({
       type: Class.from<Array<int>>(),
       key: 'PersonArray',
       defaultCreator: () => {
         return new Array<int>();
       },
       areaMode: contextConstant.AreaMode.EL1,
       enableAutoSave: true,
       defaultSubCreators: creators
     })!;
   */

  build() {
    Column(undefined) {
      Text(`length: ${this.stateVar.length}`)
      // 点击按钮添加新的Person对象
      Button('add Person')
        .onClick(() => {
          let p = new Person();
          p.userName = 'user_' + this.stateVar.length.toString();
          this.stateVar.push(p);
        })
      /* Button('add int')
         .onClick(() => {
           this.stateVar.push(this.stateVar.length);
         })
       */
      List() {
        ForEach(this.stateVar, (item: Any, index: int) => {
          ListItem() {
            Column() {
              if (item instanceof Person) {
                Text(`[${index}] ${(item as Person).userName}`)
                  .fontSize(20)
              } else if (item instanceof int) {
                Text(`[${index}] ${item as int}`)
                  .fontSize(20)
              } else {
                Text(`[${index}] NOT Person or int: ${Class.ofAny(item)!.getName()}`)
                  .fontSize(20)
              }
            }
          }
        }, (item: Any, index: int) => {
          return index.toString();
        })
      }
    }
  }
}
```

在提供了默认元素的情况下，框架会判断出元素类型发生改变，跳过数据恢复，直接使用默认值。

<!-- @[persistence_v2_container_element_change](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/PersistenceV2/entry/src/main/ets/pages/PersistenceV2ContainerElementChange.ets) -->

``` TypeScript
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local, Column, Text, Button, List, ListItem, ForEach, StorageDefaultCreator } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

@ObservedV2
export class Person {
  @Trace userName: string = 'John';
  userId: int = 1;
}

const creators = new Map<Class, StorageDefaultCreator<object>>([
  [Class.from<Person>(), () => new Person()]
]);

@Entry
@ComponentV2
struct Index {
  // 提供默认元素new Person()，框架可据此检测到类型变更并跳过旧数据恢复
  @Local stateVar: Array<Person> = PersistenceV2.globalConnect<Array<Person>>({
    type: Class.from<Array<Person>>(),
    key: 'PersonArray',
    defaultCreator: () => {
      return new Array<Person>(new Person());
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;

  // 以下为将元素类型从Person改为int的演示，提供了默认元素0, 1, 2，框架可据此检测到类型变更
  /* @Local stateVar: Array<int> = PersistenceV2.globalConnect<Array<int>>({
       type: Class.from<Array<int>>(),
       key: 'PersonArray',
       defaultCreator: () => {
         return new Array<int>(0, 1, 2);
       },
       areaMode: contextConstant.AreaMode.EL1,
       enableAutoSave: true,
       defaultSubCreators: creators
     })!;
   */

  build() {
    Column(undefined) {
      Text(`length: ${this.stateVar.length}`)
      // 点击按钮添加新的Person对象
      Button('add Person')
        .onClick(() => {
          let p = new Person();
          p.userName = 'user_' + this.stateVar.length.toString();
          this.stateVar.push(p);
        })
      /* Button('add int')
         .onClick(() => {
           this.stateVar.push(this.stateVar.length);
         })
       */
      List() {
        ForEach(this.stateVar, (item: Any, index: int) => {
          ListItem() {
            Column() {
              if (item instanceof Person) {
                Text(`[${index}] ${(item as Person).userName}`)
                  .fontSize(20)
              } else if (item instanceof int) {
                Text(`[${index}] ${item as int}`)
                  .fontSize(20)
              } else {
                Text(`[${index}] NOT Person or int: ${Class.ofAny(item)!.getName()}`)
                  .fontSize(20)
              }
            }
          }
        }, (item: Any, index: int) => {
          return index.toString();
        })
      }
    }
  }
}
```
