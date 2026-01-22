# PersistentStorage：持久化存储UI状态

前两个小节介绍的LocalStorage和AppStorage都是运行时的内存，但是在应用退出再次启动后，依然能保存选定的结果，是应用开发中十分常见的现象，这就需要用到PersistentStorage。

PersistentStorage是应用程序中的可选单例对象。此对象的作用是持久化存储选定的AppStorage属性，以确保这些属性在应用程序重新启动时的值与应用程序关闭时的值相同。

PersistentStorage提供状态变量持久化的能力。需要注意，其持久化和读回UI的功能都需要依赖AppStorage。在阅读本文档前，建议提前阅读：[AppStorage](./arkts-static-appstorage.md) 和 [PersistentStorage API文档](../../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#persistentstorage)。

## 概述

PersistentStorage将选定的AppStorage属性保留在设备磁盘上。应用程序通过API决定哪些AppStorage属性应借助PersistentStorage进行持久化。UI和业务逻辑不直接访问PersistentStorage中的属性，所有属性访问都是通过AppStorage进行，AppStorage中的更改会自动同步到PersistentStorage。

PersistentStorage和AppStorage中的属性建立双向同步。应用开发通常通过AppStorage访问PersistentStorage，另外还有一些接口可以用于管理持久化属性，但是业务逻辑始终是通过AppStorage获取和设置属性的。

PersistentStorage的存储路径为module级别，即哪个module调用了PersistentStorage，数据副本就会存入该module的持久化文件中。如果多个module使用相同的key，数据将被存储在最先调用PersistentStorage的module中。

PersistentStorage的存储路径在应用第一个ability启动时就已确定，为该ability所属的module。如果一个ability调用了PersistentStorage，并且该ability能被不同的module拉起，那么ability存在多少种启动方式，就会有多少份数据副本。

在静态上下文中使用时，需导入PersistentStorage：

```ts
import { PersistentStorage } from '@kit.ArkUI';
```

## 限制条件

PersistentStorage允许的类型和值有：

- `number, string, boolean, enum` 等简单类型，对于简单类型，开发者无需传入[toJson](../../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#ToJsonType)和[fromJson](../../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#FromJsonType)方法即可实现持久化。
- 对于以下复杂类型，开发者必须传入toJson和fromJson才能实现数据持久化：
- 支持Map类型，可以观察到Map整体的赋值，同时可通过调用Map的接口`set`, `clear`, `delete` 更新Map的值。且更新的值被持久化存储。详见[装饰Map类型变量](#装饰map类型变量)。
- 支持Set类型，可以观察到Set整体的赋值，同时可通过调用Set的接口`add`, `clear`, `delete` 更新Set的值。且更新的值被持久化存储。详见[装饰Set类型变量](#装饰set类型变量)。
- 支持Date类型，可以观察到Date整体的赋值，同时可通过调用Date的接口`setFullYear`, `setMonth`, `setDate`, `setHours`, `setMinutes`, `setSeconds`, `setMilliseconds`, `setTime`, `setUTCFullYear`, `setUTCMonth`, `setUTCDate`, `setUTCHours`, `setUTCMinutes`, `setUTCSeconds`, `setUTCMilliseconds` 更新Date的属性。且更新的值被持久化存储。详见[装饰Date类型变量](#装饰date类型变量)。
- 支持class类型，class需要被@Observed装饰才能够持久化。
- [支持联合类型](#支持联合类型)。

持久化数据是一个相对缓慢的操作，应用程序应避免以下情况：

- 持久化大型数据集。

- 持久化经常变化的变量。

PersistentStorage的持久化变量应小于2kb，避免大量数据的持久化。因为PersistentStorage写入磁盘的操作是同步的，大量数据的本地化读写会同步在UI线程中执行，影响UI渲染性能。如果开发者需要存储大量数据，建议使用数据库API。

PsistentStorage和UI实例相关联，持久化操作需要在UI实例初始化成功后（即[loadContent](../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)传入的回调被调用时）才可以被调用，早于该时机调用会导致持久化失败, 最早使用时机如下：

```ts
// EntryAbility.ets
// EntryAbility中，persistentStorage只支持这一个时机调用
onWindowStageCreate(windowStage: window.WindowStage): void {
  windowStage.loadContent('pages/Index', (err) => {
    if (err.code) {
      return;
    }
    PersistentStorage.persistProp<number>('aProp', 47);
  });
}
```

如果开发者对数据持久化能力有较强的诉求，例如持久化时机，建议使用[Preferences](../../database/preferences-guidelines.md)进行数据持久化。

## 使用场景

### 从AppStorage中访问PersistentStorage初始化的属性

1. 初始化PersistentStorage：

   ```ts
   PersistentStorage.persistProp<number>('aProp', 47);
   ```

2. 从AppStorage中获取对应属性：

  ```ts
  AppStorage.get<number>('aProp'); // returns 47
  ```

  或在组件内部定义：

  ```ts
  @StorageLink('aProp') aProp: number = 48;
  ```

完整代码如下：

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@kit.ArkUI';
import { PersistentStorage, StorageLink, State } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  @StorageLink('aProp') aProp: number = 48;
  // 在ArkTS-Sta中，全局的逻辑代码不会默认执行。开发者可将需要执行的逻辑代码移至static代码块中，以达到与ArkTS-Dyn一样的效果。
  static {
    PersistentStorage.persistProp<number>('aProp', 47);
  }

  build() {
    Row() {
      Column() {
        Text(this.message)
        // 应用退出时会保存当前结果；重新启动后，会显示上一次的保存结果。
        // 未修改时默认值为47
        Text(`${this.aProp}`)
          .onClick((e: ClickEvent) => {
            this.aProp += 1;
          })
      }
    }
  }
}
```

- 新应用安装后首次启动运行：

  1. 调用persistProp初始化PersistentStorage，首先查询在PersistentStorage本地文件中是否存在“aProp”，查询结果为不存在，因为应用是第一次安装。
  2. 接着查询属性“aProp”在AppStorage中是否存在，依旧不存在。
  3. 在AppStorage中创建名为“aProp”的number类型属性，属性初始值是定义的默认值47。
  4. PersistentStorage将属性“aProp”和值47写入磁盘，AppStorage中“aProp”对应的值和其后续的更改将被持久化。
  5. 在Index组件中创建状态变量\@StorageLink('aProp') aProp，和AppStorage中“aProp”双向绑定，在创建的过程中会在AppStorage中查找，成功找到“aProp”，所以使用其在AppStorage找到的值47。

- 触发点击事件后：
  1. 状态变量\@StorageLink('aProp') aProp改变，触发Text组件重新刷新。
  2. \@StorageLink装饰的变量是和AppStorage中建立双向同步的，所以\@StorageLink('aProp') aProp的变化会被同步回AppStorage中。
  3. AppStorage中“aProp”属性的改变会同步到所有绑定该“aProp”的单向或者双向变量，在本示例中没有其他的绑定“aProp”的变量。
  4. 因为“aProp”对应的属性已经被持久化，所以在AppStorage中“aProp”的改变会触发PersistentStorage，将新的改变写入本地磁盘。

- 后续启动应用：
  1. 执行PersistentStorage.persistProp('aProp', 47)，首先在PersistentStorage本地文件查询“aProp”属性，成功查询到。
  2. 将在PersistentStorage查询到的值写入AppStorage中。
  3. 在Index组件里，\@StorageLink绑定的“aProp”为PersistentStorage写入AppStorage中的值，即为上一次退出应用存入的值。

### 在PersistentStorage之前访问AppStorage中的属性

该示例为反例。在调用PersistentStorage.persistProp或者persistProps之前使用接口访问AppStorage中的属性是错误的，因为这样的调用顺序会丢失上一次应用程序运行中的属性值：

```ts
'use static'

import { PersistentStorage, AppStorage } from '@kit.ArkUI';

let aProp = AppStorage.setOrCreate('aProp', 47);
PersistentStorage.persistProp('aProp', 48);
```

应用在非首次运行时，先执行AppStorage.setOrCreate('aProp', 47)：属性“aProp”在AppStorage中创建，其类型为number，其值设置为指定的默认值47。“aProp”是持久化的属性，所以会被写回PersistentStorage磁盘中，PersistentStorage存储的上次退出应用的值被覆盖。

PersistentStorage.persistProp('aProp', 48)：在PersistentStorage中查找到“aProp”，值为刚刚使用AppStorage接口写入的47。

### 在PersistentStorage之后访问AppStorage中的属性

开发者可以先判断是否需要覆盖上一次保存在PersistentStorage中的值，如果需要覆盖，再调用AppStorage的接口进行修改，如果不需要覆盖，则不调用AppStorage的接口。

```ts
'use static'

import { PersistentStorage, AppStorage } from '@kit.ArkUI';

PersistentStorage.persistProp('aProp', 48);
if (AppStorage.get('aProp') > 50) {
    // 如果PersistentStorage存储的值超过50，设置为47
    AppStorage.setOrCreate('aProp',47);
}
```

示例代码在读取PersistentStorage存储的数据后，判断“aProp”的值是否大于50，如果大于50，则使用AppStorage的接口将其设置为47。

### 支持联合类型

在静态ArkTS中，联合类型都是Object类型，因此所有的联合类型都是复杂类型，需要传入toJson和fromJson才能实现持久化。
静态ArkTS中,语言不支持序列化undefined，因此，不建议开发者使用PersitentStorage时去持久化undefined，可使用null代替，如在下面的示例中，使用persistProp方法初始化'P'为12。通过@StorageLink('P')绑定变量p，类型为number | string | null，点击Button改变P的值，视图会随之刷新。且P的值被持久化存储。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@kit.ArkUI';
import { Observed, PersistentStorage, AppStorage, StorageLink } from '@kit.ArkUI';

@Entry
@Component
struct MapSample {
  success: boolean = PersistentStorage.persistProp<number | string | null>('union', 12,
    (val: number | string | null): jsonx.JsonElement => {
      const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
      const unionElmt = new jsonx.JsonElement();
      if (Type.of(val) === Type.from<number>()) {
        unionElmt.setDouble(val as Double);
      } else if (val === null) {
        unionElmt.setNull();
      } else {
        unionElmt.setString(val as string);
      }
      root.setElement('union', unionElmt);
      return root;
    }, 
    (json: jsonx.JsonElement): number | string | null => {
      let unionElmt: jsonx.JsonElement = json.getElement('union');
      if (unionElmt.jsonType === jsonx.JsonType.JsonNumber) {
        return unionElmt.asInteger();
      } else if (unionElmt.jsonType === jsonx.JsonType.JsonNull) {
        return null;
      } else {
        return unionElmt.asString();
      }
    } 
  );
  @StorageLink('union') union: number | string | null = 'strUnion';

  build() {
    Column() {
      // @LocalStorage装饰set，set api操作，能触发PersistentStorage的持久化
      Text(`${this.union}`)
      Button(`union change:`)
        .onClick((e: ClickEvent) => {
          if (Type.of(this.union) === Type.from<number>()) {
            this.union = null
          } else if (this.union === null) {
            this.union = 'strUnion';
          } else {
            this.union = 3;
          }
        })    
      // appStorage整体赋值能触发PersistentStorage的持久化
      Button(`map change by appStorage:`)
        .onClick((e: ClickEvent) => {
          if (AppStorage.has('union')) {
            AppStorage.set<number | string | null>('union', 15);
          }
        })
    }
  }
}
```

### 装饰Date类型变量

在下面的示例中，@StorageLink装饰的persistedDate类型为Date，点击Button改变persistedDate的值，视图会随之刷新，并且persistedDate的值会被持久化存储。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@kit.ArkUI';
import { Observed, PersistentStorage, AppStorage, StorageLink } from '@kit.ArkUI';

@Entry
@Component
struct MapSample {
  success: boolean = PersistentStorage.persistProp<Date>('date', new Date(),
    (date: Date): jsonx.JsonElement => {
      const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
      const dateEle = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
      dateEle.setString(this.date.toString());
      root.setElement('date', dateEle);
      return root;
    }, 
    (json: jsonx.JsonElement): Date => {
      let date: Date = new Date(json.getElement('date').asString());
      return date;
    }
  );
  @StorageLink('date') date: Date = new Date();

  build() {
    Column() {
      // @LocalStorage装饰set，set api操作，能触发PersistentStorage的持久化
      Text(`${this.date}`)
      Button(`change update`).onClick((e: ClickEvent) => {
        this.date = new Date('2023-09-09');
      })
      Button('increase the year by 1').onClick((e: ClickEvent) => {
        this.date.setFullYear(this.date.getFullYear() + 1);
      })
      Button('increase the month by 1').onClick((e: ClickEvent) => {
        this.date.setMonth(this.date.getMonth() + 1);
      })
      Button('parent increase the day by 1').onClick((e: ClickEvent) => {
        this.date.setDate(this.date.getDate() + 1);
      })
      // appStorage整体赋值能触发PersistentStorage的持久化
      Button(`map change by appStorage:`)
        .onClick((e: ClickEvent) => {
          let date = new Date();
          if (AppStorage.has('date')) {
            AppStorage.set<Date>('date', date);
          }
        })
    }
  }
}
```

### 装饰Map类型变量

在下面的示例中，@StorageLink装饰的map类型为Map\<string, string\>，点击Button改变map的值，视图会随之刷新，并且map的值被持久化存储。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@kit.ArkUI';
import { Observed, PersistentStorage, AppStorage, StorageLink } from '@kit.ArkUI';

@Entry
@Component
struct MapSample {
  success: boolean = PersistentStorage.persistProp<Map<string, string>>('map', new Map<string, string>(),
    (map: Map<string, string>): jsonx.JsonElement => {
      const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
      const mapEle = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
      map.forEach((v: string, k: string) => {
        mapEle.setElement(k, jsonx.JsonElement.createString(v));
      });
      root.setElement('map', mapEle);
      return root;
    }, 
    (json: jsonx.JsonElement): Map<string, string> => {
      let mapEles: jsonx.JsonElement = json.getElement('map');
      let map: Map<string, string> = new Map<string, string>();
      for (let ele of mapEles) {
        map.set(ele[0], ele[1].asString());
      }
      return map;
    }
  );
  @StorageLink('map') map: Map<string, string> = new Map<string, string>([
    ['1', 'value1'],
    ['2', 'value2'],
    ['3', 'value3']
  ]);

  build() {
    Column() {
      // @LocalStorage装饰set，set api操作，能触发PersistentStorage的持久化
      Text(`${this.map}`)
      Button(`map add:`)
        .onClick((e: ClickEvent) => {
            this.map.set('4', 'value4');
        })
      Button(`map delete:`)
        .onClick((e: ClickEvent) => {
            this.map.delete('4');
        })
      // appStorage整体赋值能触发PersistentStorage的持久化
      Button(`map change by appStorage:`)
        .onClick((e: ClickEvent) => {
          this.map = new Map<string, string>([
            ['4', 'value4'],
            ['5', 'value5'],
            ['6', 'value6']
          ]);
          if (AppStorage.has('map')) {
            AppStorage.set<Map<string, string>>('map', this.map);
          }
        })
    }
  }
}
```

### 装饰Set类型变量

在下面的示例中，@StorageLink装饰的set类型为Set\<string\>，点击Button改变set的值，视图会随之刷新。且persistedSet的值被持久化存储。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@kit.ArkUI';
import { Observed, PersistentStorage, AppStorage, StorageLink } from '@kit.ArkUI';

@Entry
@Component
struct SetSample {
  success: boolean = PersistentStorage.persistProp<Set<string>>('set', new Set<string>(['1', '2', '3']),
    (set: Set<string>): jsonx.JsonElement => {
      const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
      const setEle = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
      set.forEach((v: string) => {
        setEle.setElement(v, jsonx.JsonElement.createString(v));
      });
      root.setElement('set', setEle);
      return root;
    }, 
    (json: jsonx.JsonElement): Set<string> => {
      let setEles: jsonx.JsonElement = json.getElement('set');
      let set: Set<string> = new Set<string>();
      for (let ele of setEles) {
        set.add(ele[1].asString());
      }
      return set;
    }
  );
  @StorageLink('set') set: Set<string> = new Set<string>([
    'value1',
    'value2',
    'value3'
  ]);

  build() {
    Column() {
      // @LocalStorage装饰set，set api操作，能触发PersistentStorage的持久化
      Text(`${this.set}`)
      Button(`set add:`)
        .onClick((e: ClickEvent) => {
            this.set.add('value4');
        })
      Button(`set delete:`)
        .onClick((e: ClickEvent) => {
            this.set.delete('value4');
        })
      // appStorage整体赋值能触发PersistentStorage的持久化
      Button(`set change by appStorage:`)
        .onClick((e: ClickEvent) => {
          this.set = new Set<string>([
            'value4',
            'value5',
            'value6'
          ]);
          if (AppStorage.has('set')) {
            AppStorage.set<Set<string>>('set', this.set);
          }
        })
    }
  }
}
```

### 装饰class

在下面的示例中，@StorageLink装饰的class被@Observed修饰，@Observed装饰的class属性改变时，能触发PersistentStorage持久化。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@kit.ArkUI';
import { Observed, PersistentStorage, AppStorage, StorageLink } from '@kit.ArkUI';

interface JsonSerializable {
  toJson(): jsonx.JsonElement;
}

interface JsonDeserializable {
  fromJson(json: jsonx.JsonElement): void;
}

@Observed
class User implements JsonSerializable, JsonDeserializable {
  userId: number = 1;
  userName: string = 'jack';
  isUser: boolean = false;

  constructor(userId?: number, userName?: string, isUser?: boolean) {
    this.userName = userName ?? 'default';
    this.userId = userId ?? 1;
    this.isUser = isUser ?? false;
  }

  toJson(): jsonx.JsonElement {
    const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);

    // 存储ID
    const userIdEle = new jsonx.JsonElement();
    userIdEle.setDouble(this.userId);
    root.setElement('userId', userIdEle);

    // 存储 userName
    const userNameEle = new jsonx.JsonElement();
    userNameEle.setString(this.userName);
    root.setElement('userName', userNameEle);

    const isUserEle = new jsonx.JsonElement();
    isUserEle.setBoolean(this.isUser);
    root.setElement('isUser', isUserEle);

    return root;
  }

  fromJson(json: jsonx.JsonElement): void {
    this.userName = json.getElement('userName').asString();
    this.userId = json.getElement('userId').asInteger();
    this.isUser = json.getElement('isUser').asBoolean();
  }
}

@Entry
@Component
struct ClassSample {
  success: boolean = PersistentStorage.persistProp<User>('user', new User(),
    (user: User) => {
      return user.toJson();
    }, 
    (json: jsonx.JsonElement): User => {
      let temp = new User();
      temp.fromJson(json);
      return temp;
    }
  );
  @StorageLink('user') user: User = new User();

  build() {
    Column() {
      // @Observed修饰的class属性改变，能触发PersistentStorage的持久化
      Button(`user Id: ${this.user.userId}`)
        .onClick((e: ClickEvent) => {
            this.user.userId += 10;
        })
      // appStorage整体赋值能触发PersistentStorage的持久化
      Button(`user Id: ${this.user.userId}`)
        .onClick((e: ClickEvent) => {
          this.user = new User(456, 'byAppStorage', true);
          if (AppStorage.has('user')) {
            AppStorage.set<User>('user', this.user);
          }
        })
    }
  }
}
```