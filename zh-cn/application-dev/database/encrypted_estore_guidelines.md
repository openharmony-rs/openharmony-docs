# E类加密数据库的使用 (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997; @dboy190-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->


## 场景介绍

从安全角度考虑，为满足部分敏感数据的安全特性，提供了E类加密数据库的方案以提高锁屏下数据的安全性。存有敏感信息的应用在申请ohos.permission.PROTECT_SCREEN_LOCK_DATA权限后会在[EL5](../reference/apis-ability-kit/js-apis-app-ability-contextConstant.md#areamode)路径下创建一个E类数据库。在锁屏的情况下（未调用Access接口获取保留文件密钥）会触发文件密钥的销毁，此时E类数据库不可读写。当锁屏解锁后，密钥会恢复，E类数据库恢复正常读写操作。这样的设计可以有效防止用户数据的泄露。

在锁屏的情况下，应用程序仍然可以继续写入数据。由于此时E类数据库不可读写，这可能会导致数据丢失。为了解决这个问题，当前提供了一种方案：在锁屏的情况下，将数据存储在[EL2](../reference/apis-ability-kit/js-apis-app-ability-contextConstant.md#areamode)路径下的C类数据库中。当解锁后，再将数据迁移到E类数据库中。这样可以确保数据在锁屏期间的安全性和完整性。

键值型数据库和关系型数据库均支持E类加密数据库。

## 实现机制

通过封装Mover类、Store类、SecretKeyObserver类和ECStoreManager类实现应用数据库密钥加锁和解锁状态下E类数据库和C类数据库的切换和操作。

Mover类：提供数据库数据迁移接口，在锁屏解锁后，若C类数据库中有数据，使用该接口将数据迁移到E类数据库。

Store类：提供了获取数据库，在数据库中插入数据、删除数据、更新数据和获取当前数据数量的接口。

SecretKeyObserver类：提供了获取当前密钥状态的接口，在密钥销毁后，关闭E类数据库。

ECStoreManager类：用于管理应用的E类数据库和C类数据库。

## 配置权限

使用EL5路径下的数据库，需要配置ohos.permission.PROTECT_SCREEN_LOCK_DATA权限。

```ts
// module.json5
"requestPermissions": [
      {
        "name": "ohos.permission.PROTECT_SCREEN_LOCK_DATA"
      }
    ]
```

## 键值型数据库E类加密

本章节提供键值型数据库的E类加密数据库使用方式，提供[Mover](#mover)类、[Store](#store)类、[SecretKeyObserver](#secretkeyobserver)类和[ECStoreManager](#ecstoremanager)类的具体实现，并在[EntryAbility](#entryability)和[index按键事件](#index按键事件)中展示这几个类的使用方式。

> **说明**：
>
> * Logger封装示例参考[Logger](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/ECStoreSamples/entry/src/main/ets/common/Logger.ts)。

### Mover

提供数据库数据迁移接口，在锁屏解锁后，若C类数据库中存在数据，使用该接口将数据迁移到E类数据库。

<!-- @[Mover](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/ECStoreSamples/entry/src/main/ets/entryability/Mover.ts) -->

### Store

提供了获取数据库，在数据库中插入数据、删除数据、更新数据和获取当前数据数量的接口。

<!-- @[Store](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/ECStoreSamples/entry/src/main/ets/entryability/Store.ts) -->

### SecretKeyObserver

该类提供了获取当前密钥状态的接口，在密钥销毁后，关闭E类数据库。

<!-- @[SecretKeyObserver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/ECStoreSamples/entry/src/main/ets/entryability/SecretKeyObserver.ts) -->

### ECStoreManager

ECStoreManager类用于管理应用的E类数据库和C类数据库。支持配置数据库信息、配置迁移函数的信息，可根据密钥状态为应用提供相应的数据库句柄，并提供了关闭E类数据库、数据迁移完成后销毁C类数据库等接口。

<!-- @[ECStoreManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/ECStoreSamples/entry/src/main/ets/entryability/ECStoreManager.ts) -->

### EntryAbility

模拟应用启动期间，注册对COMMON_EVENT_SCREEN_LOCK_FILE_ACCESS_STATE_CHANGED公共事件的监听，并配置相应的数据库信息、密钥状态信息等。

<!-- @[EntryAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/ECStoreSamples/entry/src/main/ets/entryability/EntryAbility.ets) -->

### Index按键事件

使用Button按钮，通过点击按钮来模拟应用操作数据库，如插入数据、删除数据、更新数据和获取数据数量的操作等，展示数据库基本的增删改查能力。

<!-- @[Index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/ECStoreSamples/entry/src/main/ets/pages/Index.ets) -->

## 关系型数据库E类加密

本章节提供关系型数据库的E类加密数据库使用方式，提供[Mover](#mover-1)类，[Store](#store-1)类，[SecretKeyObserver](#secretkeyobserver-1)类和[ECStoreManager](#ecstoremanager-1)类的具体实现，并在[EntryAbility](#entryability-1)和[index按键事件](#index按键事件-1)中展示这几个类的使用方式。

### Mover

提供数据库数据迁移接口，在锁屏解锁后，若C类数据库中有数据，使用该接口将数据迁移到E类数据库。

```ts
// Mover.ts
import { relationalStore } from '@kit.ArkData';

export class Mover {
  async move(eStore: relationalStore.RdbStore, cStore: relationalStore.RdbStore) {
    if (eStore != null && cStore != null) {
      let predicates = new relationalStore.RdbPredicates('employee');
      let resultSet = await cStore.query(predicates);
      while (resultSet.goToNextRow()) {
        let bucket = resultSet.getRow();
        await eStore.insert('employee', bucket);
      }
    }
  }
}
```

### Store

提供了获取数据库，在数据库中插入数据、删除数据、更新数据和获取当前数据数量的接口。其中StoreInfo类用于存储获取数据库相关信息。

```ts
// Store.ts
import { relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';
import { Context } from '@kit.AbilityKit';

export class StoreInfo {
  context: Context;
  config: relationalStore.StoreConfig;
  storeId: string;
}

let id = 1;
const SQL_CREATE_TABLE = 'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL, AGE INTEGER, SALARY REAL, CODES BLOB)';


export class Store {
  async getECStore(storeInfo: StoreInfo): Promise<relationalStore.RdbStore> {
    let rdbStore: relationalStore.RdbStore | null;
    try {
      rdbStore = await relationalStore.getRdbStore(storeInfo.context, storeInfo.config);
      if (rdbStore.version == 0) {
        await rdbStore.executeSql(SQL_CREATE_TABLE);
        console.info(`ECDB_Encry succeeded in getting Store ：${storeInfo.storeId}`);
        rdbStore.version = 1;
      }
    } catch (e) {
      let error = e as BusinessError;
      console.error(`An unexpected error occurred.code is ${error.code},message is ${error.message}`);
    }
    return rdbStore;
  }

  async putOnedata(rdbStore: relationalStore.RdbStore) {
    if (rdbStore != undefined) {
      const valueBucket: relationalStore.ValuesBucket = {
        ID: id++,
        NAME: 'Lisa',
        AGE: 18,
        SALARY: 100.5,
        CODES: new Uint8Array([1, 2, 3, 4, 5]),
      };
      try {
        await rdbStore.insert("EMPLOYEE", valueBucket);
        console.info(`ECDB_Encry insert success`);
      } catch (e) {
        let error = e as BusinessError;
        console.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
      }
    }
  }

  async getDataNum(rdbStore: relationalStore.RdbStore) {
    if (rdbStore != undefined) {
      try {
        let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
        let resultSet = await rdbStore.query(predicates);
        let count = resultSet.rowCount;
        console.info(`ECDB_Encry getdatanum success count : ${count}`);
      } catch (e) {
        let error = e as BusinessError;
        console.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
      }
    }
  }

  async deleteAlldata(rdbStore: relationalStore.RdbStore) {
    if (rdbStore != undefined) {
      try {
        let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
        predicates.equalTo('AGE', 18);
        await rdbStore.delete(predicates);
        console.info(`ECDB_Encry delete Success`);
      } catch (e) {
        let error = e as BusinessError;
        console.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
      }
    }
  }

  async updateOnedata(rdbStore: relationalStore.RdbStore) {
    if (rdbStore != undefined) {
      try {
        let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
        predicates.equalTo('NAME', 'Lisa');
        const valueBucket: relationalStore.ValuesBucket = {
          NAME: 'Anna',
          SALARY: 100.5,
          CODES: new Uint8Array([1, 2, 3, 4, 5]),
        };
        await rdbStore.update(valueBucket, predicates);
        console.info(`ECDB_Encry update success`);
      } catch (e) {
        let error = e as BusinessError;
        console.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
      }
    }
  }
}
```

### SecretKeyObserver

该类提供了获取当前密钥状态的接口，在密钥销毁后，关闭E类数据库。

```ts
// SecretKeyObserver.ts
import { ECStoreManager } from './ECStoreManager';

export enum SecretStatus {
  Lock,
  UnLock
}

export class SecretKeyObserver {
  onLock(): void {
    this.lockStatus = SecretStatus.Lock;
    this.storeManager.closeEStore();
  }

  onUnLock(): void {
    this.lockStatus = SecretStatus.UnLock;
  }

  getCurrentStatus(): number {
    return this.lockStatus;
  }

  initialize(storeManager: ECStoreManager): void {
    this.storeManager = storeManager;
  }

  updateLockStatus(code: number) {
    if (this.lockStatus === SecretStatus.Lock) {
      this.onLock();
    } else {
      this.lockStatus = code;
    }
  }

  private lockStatus: number = SecretStatus.UnLock;
  private storeManager: ECStoreManager;
}

export let lockObserve = new SecretKeyObserver();
```

### ECStoreManager

ECStoreManager类用于管理应用的E类数据库和C类数据库。支持配置数据库信息、配置迁移函数的信息，可根据密钥状态为应用提供相应的数据库句柄，并提供了关闭E类数据库、数据迁移完成后销毁C类数据库等接口。

```ts
// ECStoreManager.ts
import { relationalStore } from '@kit.ArkData';
import { Mover } from './Mover';
import { BusinessError } from '@kit.BasicServicesKit';
import { StoreInfo, Store } from './Store';
import { SecretStatus } from './SecretKeyObserver';

let store = new Store();

export class ECStoreManager {
  config(cInfo: StoreInfo, other: StoreInfo): void {
    this.cInfo = cInfo;
    this.eInfo = other;
  }

  configDataMover(mover: Mover): void {
    this.mover = mover;
  }

  async getCurrentStore(screenStatus: number): Promise<relationalStore.RdbStore> {
    if (screenStatus === SecretStatus.UnLock) {
      try {
        this.eStore = await store.getECStore(this.eInfo);
      } catch (e) {
        let error = e as BusinessError;
        console.error(`Failed to GetECStore.code is ${error.code},message is ${error.message}`);
      }
      // 解锁状态 获取e类库
      if (this.needMove) {
        if (this.eStore != undefined && this.cStore != undefined) {
          await this.mover.move(this.eStore, this.cStore);
          console.info(`ECDB_Encry cstore data move to estore success`);
        }
        this.deleteCStore();
        this.needMove = false;
      }
      return this.eStore;
    } else {
      // 加锁状态 获取c类库
      this.needMove = true;
      try {
        this.cStore = await store.getECStore(this.cInfo);
      } catch (e) {
        let error = e as BusinessError;
        console.error(`Failed to GetECStore.code is ${error.code},message is ${error.message}`);
      }
      return this.cStore;
    }
  }

  closeEStore(): void {
    this.eStore = undefined;
  }

  async deleteCStore() {
    try {
      await relationalStore.deleteRdbStore(this.cInfo.context, this.cInfo.storeId)
    } catch (e) {
      let error = e as BusinessError;
      console.error(`Failed to create KVManager.code is ${error.code},message is ${error.message}`);
    }
  }

  private eStore: relationalStore.RdbStore = null;
  private cStore: relationalStore.RdbStore = null;
  private cInfo: StoreInfo | null = null;
  private eInfo: StoreInfo | null = null;
  private needMove: boolean = false;
  private mover: Mover | null = null;
}
```

### EntryAbility

模拟在应用启动期间，注册对COMMON_EVENT_SCREEN_LOCK_FILE_ACCESS_STATE_CHANGED公共事件的监听，并配置相应的数据库信息、密钥状态信息等。

```ts
// EntryAbility.ets
import { AbilityConstant, contextConstant, UIAbility, Want, application } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';
import { relationalStore } from '@kit.ArkData';
import { ECStoreManager } from './ECStoreManager';
import { StoreInfo } from './Store';
import { Mover } from './Mover';
import { SecretKeyObserver } from './SecretKeyObserver';
import { commonEventManager } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';


export let storeManager = new ECStoreManager();

export let e_secretKeyObserver = new SecretKeyObserver();

let mover = new Mover();

let subscriber: commonEventManager.CommonEventSubscriber;

export function createCB(err: BusinessError, commonEventSubscriber: commonEventManager.CommonEventSubscriber) {
  if (!err) {
    console.info('ECDB_Encry createSubscriber');
    subscriber = commonEventSubscriber;
    try {
      commonEventManager.subscribe(subscriber, (err: BusinessError, data: commonEventManager.CommonEventData) => {
        if (err) {
          console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
        } else {
          console.info(`ECDB_Encry SubscribeCB ${data.code}`);
          e_secretKeyObserver.updateLockStatus(data.code);
        }
      });
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
    }
  } else {
    console.error(`createSubscriber failed, code is ${err.code}, message is ${err.message}`);
  }
}

let cInfo: StoreInfo | null = null;
let eInfo: StoreInfo | null = null;

export default class EntryAbility extends UIAbility {
  async onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): Promise<void> {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let cContext = this.context;
    cInfo = {
      context: cContext,
      config: {
        name: 'cstore.db',
        securityLevel: relationalStore.SecurityLevel.S3,
      },
      storeId: "cstore.db"
    };
    let eContext = await application.createModuleContext(this.context, "entry");
    eContext.area = contextConstant.AreaMode.EL5;
    eInfo = {
      context: eContext,
      config: {
        name: 'estore.db',
        securityLevel: relationalStore.SecurityLevel.S3,
      },
      storeId: "estore.db",
    };
    // 监听COMMON_EVENT_SCREEN_LOCK_FILE_ACCESS_STATE_CHANGED事件 code == 1解锁状态，code==0加锁状态
    console.info(`ECDB_Encry store area : estore:${eContext.area},cstore${cContext.area}`)
    try {
      commonEventManager.createSubscriber({
        events: ['COMMON_EVENT_SCREEN_LOCK_FILE_ACCESS_STATE_CHANGED']
      }, createCB);
      console.info(`ECDB_Encry success subscribe`);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`createSubscriber failed, code is ${err.code}, message is ${err.message}`);
    }
    storeManager.config(cInfo, eInfo);
    storeManager.configDataMover(mover);
    e_secretKeyObserver.initialize(storeManager);
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content.');
    });
  }

  onWindowStageDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
  }

  onForeground(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onBackground(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
  }
}
```

### Index按键事件

使用Button按钮，通过点击按钮来模拟应用操作数据库，如插入数据、删除数据、更新数据和获取数据数量的操作等，展示数据库基本的增删改查能力。

```ts
// Index.ets
import { storeManager, e_secretKeyObserver } from "../entryability/EntryAbility";
import { relationalStore } from '@kit.ArkData';
import { Store } from '../entryability/Store';

let storeOption = new Store();

let lockStatus: number = 1;

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Button('加锁/解锁').onClick((event: ClickEvent) => {
          if (lockStatus) {
            e_secretKeyObserver.onLock();
            lockStatus = 0;
          } else {
            e_secretKeyObserver.onUnLock();
            lockStatus = 1;
          }
          lockStatus ? this.message = "解锁" : this.message = "加锁";
        }).margin("5");
        Button('store type').onClick(async (event: ClickEvent) => {
          e_secretKeyObserver.getCurrentStatus() ? this.message = "estore" : this.message = "cstore";
          console.info(`ECDB_Encry current store : ${this.message}`);
        }).margin("5");

        Button("put").onClick(async (event: ClickEvent) => {
          let store: relationalStore.RdbStore = await storeManager.getCurrentStore(e_secretKeyObserver.getCurrentStatus());
          storeOption.putOnedata(store);
        }).margin(5)

        Button("Get").onClick(async (event: ClickEvent) => {
          let store: relationalStore.RdbStore = await storeManager.getCurrentStore(e_secretKeyObserver.getCurrentStatus());
          storeOption.getDataNum(store);
        }).margin(5)

        Button("delete").onClick(async (event: ClickEvent) => {
          let store: relationalStore.RdbStore = await storeManager.getCurrentStore(e_secretKeyObserver.getCurrentStatus());
          storeOption.deleteAlldata(store);
        }).margin(5)

        Button("update").onClick(async (event: ClickEvent) => {
          let store: relationalStore.RdbStore = await storeManager.getCurrentStore(e_secretKeyObserver.getCurrentStatus());
          storeOption.updateOnedata(store);
        }).margin(5)

        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
