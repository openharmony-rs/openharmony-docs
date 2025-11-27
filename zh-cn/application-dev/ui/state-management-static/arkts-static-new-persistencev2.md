# PersistenceV2: 持久化储存UI状态

为了增强状态管理框架对持久化存储UI的能力，开发者可以使用PersistenceV2存储持久化的数据。

PersistenceV2是应用程序中的可选单例对象。此对象的作用是持久化存储UI相关的数据，以确保这些属性在应用程序重新启动时的值与应用程序关闭时的值相同。

PersistenceV2提供状态变量持久化能力，开发者可以通过connect或者globalConnect绑定同一个key，在状态变量变换和应用冷启动时，实现持久化能力。

在阅读本文档前，建议提前阅读：[\@ComponentV2](./arkts-static-componentv2.md)，[\@ObservedV2和\@Trace](./arkts-static-new-observedV2-and-trace.md)，配合阅读：[PersistenceV2-API文档](../../reference/apis-arkui/js-apis-stateManagement-static.md#PersistenceV2)。

>**说明：**
>
>从API version 20开始支持。
>
>globalConnect行为和connect保持一致，唯一的区别为connect的底层存储路径为module级别的路径，而globalConnect的底层存储路径为应用级别。


## 概述

PersistenceV2是在应用UI启动时会被创建的单例。它的目的是为了提供应用状态数据的中心存储，这些状态数据在应用级别都是可访问的。数据通过唯一的键字符串值访问。不同于AppStorageV2，PersistenceV2还将最新数据储存在设备磁盘上（持久化）。这意味着，应用退出再次启动后，依然能保存选定的结果。

对于与PersistenceV2关联的[\@ObservedV2](./arkts-static-new-observedV2-and-trace.md)对象，该对象的[\@Trace](./arkts-static-new-observedV2-and-trace.md)属性的变化，可通过[enableAutoSave](../../reference/apis-arkui/js-apis-stateManagement-static.md#connect-1)接口控制是否自动持久化。如未设置该参数或设置为true，则修改会自动存储，否则，需要通过调用PersistenceV2的save接口手动持久化。

PersistenceV2可以和UI组件同步，且可以在应用业务逻辑中被访问。

PersistenceV2支持应用的[主线程](../../application-models/thread-model-stage.md)内多个UIAbility实例间的状态共享。

## 使用说明

- connect：创建或获取存储的数据。

>**说明：**
>
>1、关联[\@Observed](./arkts-static-observed-and-objectlink.md)对象时，由于该类型的name属性未定义，需要指定key或者自定义name属性。
>
>2、数据存储路径为module级别，即哪个module调用了connect，数据副本存入对应module的持久化文件中。如果多个module使用相同的key，则数据为最先使用connect的module，并且PersistenceV2中的数据也会存入最先使用connect的module里。
>
>3、因为存储路径在应用第一个ability启动时就已确定，为该ability所属的module。如果一个ability调用了connect，并且该ability能被不同module的拉起， 那么ability存在多少种启动方式，就会有多少份数据副本。

- globalConnect：创建或获取存储的数据。
- remove：删除指定key的存储数据。删除PersistenceV2中不存在的key会报警告。
- keys：返回所有PersistenceV2中的key。包括module级别存储路径和应用级别存储路径中的所有key。
- save：手动持久化数据。
- notifyOnError：响应序列化或反序列化失败的回调。将数据存入磁盘时，需要对数据进行序列化；当某个key序列化失败时，错误是不可预知的；可调用该接口捕获异常。

以上接口详细描述请参考[状态管理API指南](../../reference/apis-arkui/js-apis-stateManagement-static.md)。

## 使用限制

1、不支持非built-in类型，如[PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md)、NativePointer、[ArrayList](../../reference/apis-arkts/js-apis-arraylist.md)等Native类型，使用会编译报错。

2、单个key支持数据大小约8k，过大会导致持久化失败。

3、持久化的数据必须是class对象，不支持容器类型（如Array、Set、Map），不支持built-in的构造对象（如Date），不支持持久化基本类型（如string、number、boolean），使用会运行时报错。如果需要持久化非class对象，建议使用[prefrence](../../database/preferences-guidelines.md)进行数据持久化。

4、不支持循环引用的对象，使用会编译报错。

5、不宜大量持久化数据，可能会导致页面卡顿。

6、connect和globalConnect不建议混用，如果混用，key必须不一致，否则会运行时报错。

7、PersistenceV2必须与UI实例关联，持久化操作需在UI实例初始化完成后调用（即[loadContent](../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)回调触发后）。

```ts
// EntryAbility.ets
// 以下为代码片段，需要开发者自己在EntryAbility.ets中补全
import { PersistenceV2, ObservedV2 } from '@kit.ArkUI';

// 在EntryAbility外部定义class
@ObservedV2
class Storage {
  @Trace isPersist: boolean = false;

  public toJson(): jsonx.JsonElement {
    const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    // 存储userName
    const isPersistEle = new jsonx.JsonElement();
    isPersistEle.setBoolean(this.isPersist);
    root.setElement('isPersist', isPersistEle);
    return root;
  }

  public fromJson(json: jsonx.JsonElement): void {
    this.isPersist = json.getElement('isPersist').asBoolean();
  }
}

const toJsonStorage = (s: Storage) => {
  return s.toJson();
}

const fromJsonStorage = (json: jsonx.JsonElement): Storage => {
  let s = new Storage();
  s.fromJson(json);
  return s;
}

// 在onWindowStageCreate的loadContent回调中调用PersistenceV2
onWindowStageCreate(windowStage: window.WindowStage): void {
  windowStage.loadContent('pages/Index', (err) => {
    if (err.code) {
      return;
    }
    PersistenceV2.connect<Storage>(
      Type.from<Storage>(),
      toJsonStorage,
      fromJsonStorage,
      (): Storage => {
        return new Storage();
      })!;
  });
}
```

## 使用场景

### 使用connect、globalConnect存储数据

此示例结合enableAutoSave参数确定是否自动持久化存储数据。

```ts
'use static'

import { PersistenceV2, ObservedV2, Trace, Local, Entry, 
  Button, Column, ClickEvent, ComponentV2, Text, SerializableObject, ConnectOptions } from '@kit.ArkUI';

import contextConstant from '@ohos.app.ability.contextConstant';

// 接受序列化失败的回调
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@ObservedV2
class Info {
  @Trace userInfo: int = 1;
}

@ObservedV2
class Person implements SerializableObject {
  @Trace userName: string = 'John';
  userId: int = 1;
  @Trace info: Info = new Info();

  public toJSON(): jsonx.JsonElement {
    const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    // 存储userName
    const userNameEle = new jsonx.JsonElement();
    userNameEle.setString(this.userName);
    root.setElement('userName', userNameEle);
    // 存储userId
    const userIdEle = new jsonx.JsonElement();
    userIdEle.setInteger(this.userId);
    root.setElement('userId', userIdEle);
    // 存储info对象
    const inforoot = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    const infoEle = new jsonx.JsonElement();
    infoEle.setInteger(this.info.userInfo);
    inforoot.setElement('userInfo', infoEle);
    root.setElement('inforoot', inforoot);
    return root;
  }

  public fromJSON(json: jsonx.JsonElement): void {
    this.userName = json.getElement('userName').asString();
    this.userId = json.getElement('userId').asInteger();
    this.info.userInfo = json.getElement('inforoot').getElement('userInfo').asInteger();
  }
}

@Entry
@ComponentV2
struct Index {
  // 调用globalConnect存储key为Person的对象，并返回。
  @Local cp1: Person = PersistenceV2.globalConnect<Person>({
    type: Type.from<Person>(),
    key: 'Person',
    defaultCreator: (): Person => {
      return new Person();
    },
    areaMode: contextConstant.AreaMode.EL1, // EL1-EL5代表5种加密等级。
    enableAutoSave: false  // 不自动持久化存储，需要开发者使用save接口手动持久化存储。
  })!;

  @Local cp2: Person = PersistenceV2.connect<Person>(
    Type.from<Person>(),
    'Person1',
    (): Person => {
      return new Person();
    },true // 持久化存储
    )!;

  options: ConnectOptions<Person> =
    { type: Type.from<Person>(), key: 'Person2', defaultCreator: () => new Person(), areaMode: contextConstant.AreaMode.EL1, enableAutoSave: true} as ConnectOptions<Person>;
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

## 使用建议

建议开发者使用新接口globalConnect创建和获取数据。globalConnect的存储规格和内存规格一致，对于应用只有一份，并且支持设置加密级别，不需要去切换ability的加密才能设置数据的加密级别。当然如果开发者应用不涉及多模块，保持使用connect也不会有影响。

### connect向globalConnect迁移实现

```ts
'use static'

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

  public toJson(): jsonx.JsonElement {
    const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    // 存储userName
    const userNameEle = new jsonx.JsonElement();
    userNameEle.setString(this.userName);
    root.setElement('userName', userNameEle);
    // 存储userId
    const userIdEle = new jsonx.JsonElement();
    userIdEle.setInteger(this.userId);
    root.setElement('userId', userIdEle);
    // 存储info对象
    const inforoot = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    const infoEle = new jsonx.JsonElement();
    infoEle.setInteger(this.info.userInfo);
    inforoot.setElement('userInfo', infoEle);
    root.setElement('inforoot', inforoot);
    return root;
  }

  public fromJson(json: jsonx.JsonElement): void {
    this.userName = json.getElement('userName').asString();
    this.userId = json.getElement('userId').asInteger();
    this.info.userInfo = json.getElement('inforoot').getElement('userInfo').asInteger();
  }
}

const toJsonPerson = (person: Person) => {
  return person.toJson();
}

const fromJsonPerson = (json: jsonx.JsonElement): Person => {
  let person = new Person();
  person.fromJson(json);
  return person;
}

@Entry
@ComponentV2
struct Index {
  // 调用connect存储key为Person的对象，并返回。
  @Local cp1: Person = PersistenceV2.connect<Person>(
    Type.from<Person>(),
    'Person',
    toJsonPerson,
    fromJsonPerson,
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

```ts
'use static'

// 迁移到globalConnect
import { PersistenceV2, ObservedV2, Trace, Local, Entry, 
  Button, Column, ClickEvent, ComponentV2, Text } from '@kit.ArkUI';

import contextConstant from '@ohos.app.ability.contextConstant';

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

  public toJson(): jsonx.JsonElement {
    const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    // 存储userName
    const userNameEle = new jsonx.JsonElement();
    userNameEle.setString(this.userName);
    root.setElement('userName', userNameEle);
    // 存储userId
    const userIdEle = new jsonx.JsonElement();
    userIdEle.setInteger(this.userId);
    root.setElement('userId', userIdEle);
    // 存储info对象
    const inforoot = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    const infoEle = new jsonx.JsonElement();
    infoEle.setInteger(this.info.userInfo);
    inforoot.setElement('userInfo', infoEle);
    root.setElement('inforoot', inforoot);
    return root;
  }

  public fromJson(json: jsonx.JsonElement): void {
    this.userName = json.getElement('userName').asString();
    this.userId = json.getElement('userId').asInteger();
    this.info.userInfo = json.getElement('inforoot').getElement('userInfo').asInteger();
  }
}

const toJsonPerson = (person: Person) => {
  return person.toJson();
}

const fromJsonPerson = (json: jsonx.JsonElement): Person => {
  let person = new Person();
  person.fromJson(json);
  return person;
}

// 用于判断是否完成数据迁移的辅助数据
@ObservedV2
class StorageState {
  @Trace isCompleteMoving: boolean = false;

  public toJson(): jsonx.JsonElement {
    const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    // 存储userName
    const movingStateEle = new jsonx.JsonElement();
    movingStateEle.setBoolean(this.isCompleteMoving);
    root.setElement('movingState', movingStateEle);
    return root;
  }

  public fromJson(json: jsonx.JsonElement): void {
    this.isCompleteMoving = json.getElement('movingState').asBoolean();
  }
}

const toJsonState = (s: StorageState) => {
  return s.toJson();
}

const fromJsonState = (json: jsonx.JsonElement): StorageState => {
  let s = new StorageState();
  s.fromJson(json);
  return s;
}

function move() {
  let movingState =
    PersistenceV2.globalConnect({ type: Type.from<StorageState>(), defaultCreator: () => new StorageState() },
      toJsonState, fromJsonState)!;
  if (!movingState.isCompleteMoving) {
    let p: Person = PersistenceV2.connect<Person>(
      Type.from<Person>(),
      'Person',
      toJsonPerson,
      fromJsonPerson,
      (): Person => {
        return new Person();
      })!;
    PersistenceV2.remove('Person');

    let p1 = PersistenceV2.globalConnect<Person>({
      type: Type.from<Person>(),
      key: 'Person',
      defaultCreator: (): Person => p,
      areaMode: contextConstant.AreaMode.EL1 // EL1-EL5代表5种加密等级。
    }, toJsonPerson, fromJsonPerson)!;
    // 将迁移标志设置为true
    movingState.isCompleteMoving = true;
  }
}

@Entry
@ComponentV2
struct Index {
  // 调用globalConnect存储key为Person的对象，并返回。
  @Local cp1: Person = PersistenceV2.globalConnect<Person>({
    type: Type.from<Person>(),
    key: 'Person',
    defaultCreator: (): Person => {
      return new Person();
    },
    areaMode: contextConstant.AreaMode.EL1 // EL1-EL5代表5种加密等级。
  }, toJsonPerson, fromJsonPerson)!;
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
