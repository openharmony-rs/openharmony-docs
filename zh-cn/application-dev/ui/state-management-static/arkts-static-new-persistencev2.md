# PersistenceV2: 持久化储存UI状态

为了增强状态管理框架对持久化存储UI的能力，开发者可以使用PersistenceV2存储持久化的数据。

PersistenceV2是应用程序中的可选单例对象。此对象的作用是持久化存储UI相关的数据，以确保这些属性在应用程序重新启动时的值与应用程序关闭时的值相同。

PersistenceV2提供状态变量持久化能力，开发者可以通过connect或者globalConnect绑定同一个key，在状态变量变换和应用冷启动时，实现持久化能力。

在阅读本文档前，建议提前阅读：[\@ComponentV2](./arkts-static-componentv2.md)，[\@ObservedV2和\@Trace](./arkts-static-new-observedV2-and-trace.md)，配合阅读：[PersistentV2-API文档](../../reference/apis-arkui/js-apis-stateManagement-static.md#PersistenceV2)。

>**说明：**
>
>从API version 20开始支持。
>
>globalConnect行为和connect保持一致，唯一的区别为connect的底层存储路径为module级别的路径，而globalConnect的底层存储路径为应用级别。


## 概述

PersistenceV2是在应用UI启动时会被创建的单例。它的目的是为了提供应用状态数据的中心存储，这些状态数据在应用级别都是可访问的。数据通过唯一的键字符串值访问。不同于AppStorageV2，PersistenceV2还将最新数据储存在设备磁盘上（持久化）。这意味着，应用退出再次启动后，依然能保存选定的结果。

对于与PersistenceV2关联的[\@ObservedV2](./arkts-static-new-observedV2-and-trace.md)对象，该对象的[\@Trace](./arkts-static-new-observedV2-and-trace.md)属性的变化，会触发**整个关联对象的自动持久化**；非[\@Trace](./arkts-static-new-observedV2-and-trace.md)属性的变化则不会，如有必要，可调用PersistenceV2 API手动持久化。请注意：被PersistenceV2持久化的类属性必须要有初值，否则不支持持久化。

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

1、不支持非built-in类型，如PixelMap、NativePointer、ArrayList等Native类型。

2、单个key支持数据大小约8k，过大会导致持久化失败。

3、持久化的数据必须是class对象，不支持容器类型（如Array、Set、Map），不支持buildin的构造对象（如Date、Number），不支持持久化基本类型（如string、number、boolean）。如果需要持久化非class对象，建议使用[prefrence](../../database/preferences-guidelines.md)进行数据持久化。

4、不支持循环引用的对象。

5、不宜大量持久化数据，可能会导致页面卡顿。

6、connect和globalConnect不建议混用，如果混用，key不能一样，否则应用crash。

7、PersistenceV2必须与UI实例关联，持久化操作需在UI实例初始化完成后调用（即[loadContent](../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)回调触发后）。
```ts
// EntryAbility.ets
// 以下为代码片段，需要开发者自己在EntryAbility.ets中补全
import { PersistenceV2 } from '@kit.ArkUI';

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
    PersistenceV2.connect(Storage, () => new Storage());
  });
}
```

## 使用建议

建议开发者使用新接口globalConnect创建和获取数据。globalConnect的存储规格和内存规格一致，对于应用只有一份，并且支持设置加密级别，不需要去切换ability的加密才能设置数据的加密级别。当然如果开发者应用不涉及多模块，保持使用connect也不会有影响。

### connect向globalConnect迁移实现

```ts
'use static'

// 使用connect存储数据
import { PersistenceV2, Type } from '@kit.ArkUI';

// 接受序列化失败的回调
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@ObservedV2
class SampleChild {
  @Trace childId: number = 0;
  groupId: number = 1;
}

@ObservedV2
export class Sample {
  // 对于复杂对象需要@Type修饰，确保序列化成功
  @Type(SampleChild)
  @Trace father: SampleChild = new SampleChild();
}

@Entry
@ComponentV2
struct Page1 {
  @Local refresh: number = 0;
  // 使用key:connect2存储
  @Local p: Sample = PersistenceV2.connect(Sample, 'connect2', () => new Sample())!;

  build() {
    Column({space: 5}) {
      /**************************** 显示数据 **************************/
      Text('Key connect2: ' + this.p.father.childId.toString())
        .onClick(() => {
          this.p.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)

      /**************************** save接口 **************************/
      // 非状态变量需要借助状态变量refresh才能刷新
      Text('save key Sample: ' + this.p.father.groupId.toString() + ' refresh:' + this.refresh)
        .onClick(() => {
          // 未被@Trace保存的对象无法自动存储，需要调用key存储
          this.p.father.groupId += 1;
          PersistenceV2.save('connect2');
          this.refresh += 1
        })
        .fontSize(25)
    }
    .width('100%')
  }
}
```

```ts
'use static'

// 迁移到globalConnect
import { PersistenceV2, Type } from '@kit.ArkUI';

// 接受序列化失败的回调
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@ObservedV2
class SampleChild {
  @Trace childId: number = 0;
  groupId: number = 1;
}

@ObservedV2
export class Sample {
  // 对于复杂对象需要@Type修饰，确保序列化成功
  @Type(SampleChild)
  @Trace father: SampleChild = new SampleChild();
}

// 用于判断是否完成数据迁移的辅助数据
@ObservedV2
class StorageState {
  @Trace isCompleteMoving: boolean = false;
}

function move() {
  let movingState = PersistenceV2.globalConnect({type: StorageState, defaultCreator: () => new StorageState()})!;
  if (!movingState.isCompleteMoving) {
    let p: Sample = PersistenceV2.connect(Sample, 'connect2', () => new Sample())!;
    PersistenceV2.remove('connect2');
    let p1 = PersistenceV2.globalConnect({type: Sample, key: 'connect2', defaultCreator: () => p})!;  // 使用默认构造函数也可以
    // 赋值数据，@Trace修饰的会自动保存
    p1.father = p.father;
    // 将迁移标志设置为true
    movingState.isCompleteMoving = true;
  }
}

move();

@Entry
@ComponentV2
struct Page1 {
  @Local refresh: number = 0;
  // 使用key:connect2存入数据
  @Local p: Sample = PersistenceV2.globalConnect({type: Sample, key:'connect2', defaultCreator:() => new Sample()})!;

  build() {
    Column({space: 5}) {
      /**************************** 显示数据 **************************/
      Text('Key connect2: ' + this.p.father.childId.toString())
        .onClick(() => {
          this.p.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)

      /**************************** save接口 **************************/
      // 非状态变量需要借助状态变量refresh才能刷新
      Text('save key connect2: ' + this.p.father.groupId.toString() + ' refresh:' + this.refresh)
        .onClick(() => {
          // 未被@Trace保存的对象无法自动存储，需要调用key存储
          this.p.father.groupId += 1;
          PersistenceV2.save('connect2');
          this.refresh += 1
        })
        .fontSize(25)
    }
    .width('100%')
  }
}
```

connect向globalConnect迁移，需要将key绑定的value赋值给globalConnect进行存储，之后当自定义组件使用globalConnect连接时，globalConnect绑定的数据即为之前使用connect保存的数据，开发者可以自定义move函数，并将其放在合适位置迁移即可。
