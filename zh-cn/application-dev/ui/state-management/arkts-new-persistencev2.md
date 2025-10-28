# PersistenceV2: 持久化存储UI状态
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zzq212050299-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

为了增强状态管理框架对持久化存储UI的能力，开发者可以使用PersistenceV2存储持久化的数据。

PersistenceV2是应用程序中的可选单例对象。此对象的作用是持久化存储UI相关的数据，以确保这些属性在应用程序重新启动时的值与应用程序关闭时的值相同。

PersistenceV2提供状态变量持久化能力，开发者可以通过connect或者globalConnect绑定同一个key，在状态变量变化和应用冷启动时，实现持久化能力。

在阅读本文档前，建议提前阅读：[\@ComponentV2](./arkts-new-componentV2.md)，[\@ObservedV2和\@Trace](./arkts-new-observedV2-and-trace.md)，配合阅读：[PersistentV2-API文档](../../reference/apis-arkui/js-apis-StateManagement.md#persistencev2)。

>**说明：**
>
>PersistenceV2从API version 12开始支持。
>
>globalConnect从API version 18开始支持，行为和connect保持一致，唯一的区别为connect的底层存储路径为module级别的路径，而globalConnect的底层存储路径为应用级别，详细区别见使用场景[在不同的module中使用connect和globalConnect](#在不同的module中使用connect和globalconnect)。


## 概述

PersistenceV2是在应用UI启动时会被创建的单例。它的目的是提供应用状态数据的中心存储，这些状态数据在应用级别都是可访问的。数据通过唯一的键值字符串访问。不同于AppStorageV2，PersistenceV2还将最新数据存储在设备磁盘上（持久化）。这意味着，应用退出再次启动后，依然能保存选定的结果。

对于与PersistenceV2关联的[\@ObservedV2](./arkts-new-observedV2-and-trace.md)对象，该对象的[\@Trace](./arkts-new-observedV2-and-trace.md)属性的变化，会触发**整个关联对象的自动持久化**；非[\@Trace](./arkts-new-observedV2-and-trace.md)属性的变化则不会，如有必要，可调用PersistenceV2 API手动持久化。请注意：被PersistenceV2持久化的类属性必须要有初值，否则不支持持久化。

PersistenceV2可以和UI组件同步，且可以在应用业务逻辑中被访问。

PersistenceV2支持应用的[主线程](../../application-models/thread-model-stage.md)内多个UIAbility实例间的状态共享。

## 使用说明

- connect：创建或获取存储的数据。

>**说明：**
>
>1、关联[\@Observed](./arkts-observed-and-objectlink.md)对象时，由于该类型的name属性未定义，需要指定key或者自定义name属性。
>
>2、数据存储路径为module级别，即哪个module调用了connect，数据副本存入对应module的持久化文件中。如果多个module使用相同的key，则数据为最先使用connect的module，并且PersistenceV2中的数据也会存入最先使用connect的module里。
>
>3、因为存储路径在应用第一个ability启动时就已确定，为该ability所属的module。如果一个ability调用了connect，并且该ability能被不同module的拉起， 那么ability存在多少种启动方式，就会有多少份数据副本。

- globalConnect：创建或获取存储的数据。
- remove：删除指定key的存储数据。删除PersistenceV2中不存在的key会报警告。
- keys：返回所有PersistenceV2中的key。包括module级别存储路径和应用级别存储路径中的所有key。
- save：手动持久化数据。
- notifyOnError：响应序列化或反序列化失败的回调。将数据存入磁盘时，需要对数据进行序列化；当某个key序列化失败时，错误是不可预知的；可调用该接口捕获异常。

以上接口详细描述请参考[状态管理API指南](../../reference/apis-arkui/js-apis-StateManagement.md)。

## 使用限制

1、需要配合UI使用（UI线程），不能在其他线程使用，如不支持@Sendable。

2、不支持collections.Set、collections.Map等类型。

3、不支持非built-in类型，如[PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md)、NativePointer、[ArrayList](../../reference/apis-arkts/js-apis-arraylist.md)等Native类型。

4、单个key支持数据大小约8k，过大会导致持久化失败。

5、持久化的数据必须是class对象，不支持容器类型（如Array、Set、Map），不支持built-in的构造对象（如Date、Number），不支持持久化基本类型（如string、number、boolean）。如果需要持久化非class对象，建议使用[Preferences](../../database/preferences-guidelines.md)进行数据持久化。

6、不支持循环引用的对象。

7、只有[\@Trace](./arkts-new-observedV2-and-trace.md)的数据改变会触发自动持久化，如V1状态变量、[\@Observed](./arkts-observed-and-objectlink.md)对象、普通数据的改变不会触发持久化。

8、不宜大量持久化数据，可能会导致页面卡顿。

9、connect和globalConnect不建议混用，如果混用，key不能一样，否则应用crash。

10、PersistenceV2必须与UI实例关联，持久化操作需在UI实例初始化完成后调用（即[loadContent](../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)回调触发后）。
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

11、如果开发者对数据持久化能力有较强的诉求，例如持久化时机，建议使用[Preferences](../../database/preferences-guidelines.md)进行数据持久化。注意：不允许混用PersistenceV2和Preferences，因为Preferences存储的数据不会有状态变量信息，反序列化的数据不能触发PersistenceV2的自动化存储。

## 使用场景

### 在两个页面之间存储数据

数据页面
<!-- @[persistence_v2_sample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/persistenceV2/Sample.ets) -->

页面1
<!-- @[Persistence_Use_Case_Data_Page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/persistenceV2/page/Page1.ets) -->

页面2
<!-- @[Persistence_Use_Case_Data_Page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/persistenceV2/page/Page2.ets) -->
使用Navigation时，需要添加配置系统路由表文件src/main/resources/base/profile/route_map.json，并替换pageSourceFile为Page2页面的路径，并且在module.json5中添加："routerMap": "$profile:route_map"。
```json
{
  "routerMap": [
    {
      "name": "Page2",
      "pageSourceFile": "src/main/ets/pages/Page2.ets",
      "buildFunction": "Page2Builder",
      "data": {
        "description" : "PersistenceV2 example"
      }
    }
  ]
}
```

### 使用globalConnect存储数据

<!-- @[persistence_v2_global_connect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/persistenceV2/PersistenceV2GlobalConnect.ets) -->

### 在不同的module中使用connect和globalConnect

**connect的存储路径需要注意以下两点：**

1、connect使用module级别的存储路径，以最先启动的module的路径作为存储路径，从内存回写磁盘时会回写到第一个连接该module的路径。应用如果之后先从另一个module启动，则会以新module的路径作为存储路径。

2、当不同module使用相同的key时，哪个module先启动，数据就为哪个module中保存的键值对，回写到对应的module中。

**globalConnect的存储路径需要注意：**

globalConnect虽然是应用级别的路径，但是可以设置不同的加密分区，不同加密分区即代表不同的存储路径。connect不支持设置加密分区，但是module自身切换加密级别时，module存储路径也会切换成对应加密分区路径。

示例代码如下：开发者需要在项目基础上，新建一个module，并按照示例代码跳转到新module中。

<!-- @[persistence_v2_module_connect_storage_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/persistenceV2/PersistenceV2ModuleConnectStorage1.ets) -->

<!-- @[persistence_v2_module_connect_storage_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/persistenceV2/PersistenceV2ModuleConnectStorage2.ets) -->

当开发者对newModule使用不同启动方式会有以下现象：

*   开发者直接启动newModule，分别修改globalConnect1和connect2绑定的变量，例如将childId都改成5。
* 应用退出并清空后台，启动模块entry，通过跳转按键启动newModule，会发现globalConnect1值为5，而connect2值为1未修改。
* globalConnect为应用级别存储，对于一个key，整个应用在对应加密分区只有一份存储路径；connect为module级别的存储路径，会因为module的启动方式不同而在各自的加密分区对应不同的存储路径。

## 使用建议

建议开发者使用新接口globalConnect创建和获取数据。globalConnect的存储规格和内存规格一致，对于应用只有一份，并且支持设置加密级别，不需要去切换ability的加密才能设置数据的加密级别。当然如果开发者应用不涉及多模块，保持使用connect也不会有影响。

### connect向globalConnect迁移实现

<!-- @[persistence_v2_connect_migration_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/persistenceV2/PersistenceV2ConnectMigration1.ets) -->

<!-- @[persistence_v2_connect_migration_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/persistenceV2/PersistenceV2ConnectMigration2.ets) -->

connect向globalConnect迁移，需要将key绑定的value赋值给globalConnect进行存储，之后当自定义组件使用globalConnect连接时，globalConnect绑定的数据即为之前使用connect保存的数据，开发者可以自定义move函数，并将其放在合适位置迁移即可。