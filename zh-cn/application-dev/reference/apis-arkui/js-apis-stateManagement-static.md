# @ohos.arkui.stateManagement (状态管理)

状态管理模块提供了应用程序动态刷新、UI数据存储、使能数据观察等能力。

>**说明：**
>
>- 本模块首批接口从API version 20开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>- 本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { AppStorageV2, PersistenceV2, UIUtils } from '@ohos.arkui.stateManagement';
```

## AppStorageV2

AppStorageV2提供状态变量在应用级全局共享的能力。

AppStorageV2具体UI使用说明，详见[AppStorageV2：应用全局的UI状态存储](../../../application-dev/ui/state-management-static/arkts-static-appstoragev2.md)。

### connect

static connect\<T extends object\>(
    ttype: Type,
    key: string,
    defaultCreator?: StorageDefaultCreator\<T\> 
): T | undefined

将键值对数据存储在应用内存中。如果给定的key已经存在于[AppStorageV2](../../../application-dev/ui/state-management-static/arkts-static-appstoragev2.md)中，返回对应的值；否则，通过获取默认值的构造器构造默认值，存储后返回。

>**说明：**
>
>- 如果数据已存储在AppStorageV2中，可省略默认构造器，获取存储的数据；否则必须指定默认构造器，不指定将导致应用异常。
>
>- key相同，connect类型不同的数据会导致应用异常，开发者需要确保类型匹配。
>
>- 建议key使用有意义的值，可由字母、数字和下划线组成，长度不超过255字符，避免使用非法字符或空字符。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名         | 类型                                                                              | 必填 | 说明                 |
| -------------- | --------------------------------------------------------------------------------- | ---- | -------------------- |
| ttype          | Type                                                                              | 是   | 指定的类型。         |
| key            | string                                                                            | 是   | 指定的key。          |
| defaultCreator | [StorageDefaultCreator\<T\>](./js-apis-StateManagement.md#storagedefaultcreatort) | 否   | 获取默认值的构造器。 |

**返回值：**

| 类型           | 说明                                                            |
| -------------- | --------------------------------------------------------------- |
| T \| undefined | 创建或获取AppStorageV2数据成功时，返回数据；否则返回undefined。 |

**示例：**

```ts
'use static'

import { AppStorageV2 } from '@ohos.arkui.stateManagement';
import { ObservedV2, Trace } from '@ohos.arkui.stateManagement';

@ObservedV2
class SampleClass {
  @Trace p: number = 0;
}

const ISampleType = Type.of(new SampleClass());

// 将key为key_as1、value为new SampleClass()对象的键值对存储到内存中，并赋值给as1
const as1: SampleClass = AppStorageV2.connect<SampleClass>(ISampleType, 'key_as1', () => new SampleClass())!;
```

### connect

static connect\<T extends object\>(
    ttype: Type,
    defaultCreator?: StorageDefaultCreator\<T\>
): T | undefined

将键值对数据存储在应用内存中。如果给定的ttype已经存在于[AppStorageV2](../../../application-dev/ui/state-management-static/arkts-static-appstoragev2.md)中，返回对应的值；否则，通过获取默认值的构造器构造默认值，存储后返回。

>**说明：**
>
>- ttype使用[Type](../apis-arkts/js-apis-util.md#type10).of(object)方法获得。
>
>- 未传入key时，默认使用ttype的name作为key。
>
>- 如果数据已存储在AppStorageV2中，可省略默认构造器，获取存储的数据；否则必须指定默认构造器，不指定将导致应用异常。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名         | 类型                                                                              | 必填 | 说明                 |
| -------------- | --------------------------------------------------------------------------------- | ---- | -------------------- |
| ttype          | Type                                                                              | 是   | 指定的类型。         |
| defaultCreator | [StorageDefaultCreator\<T\>](./js-apis-StateManagement.md#storagedefaultcreatort) | 否   | 获取默认值的构造器。 |

**返回值：**

| 类型           | 说明                                                            |
| -------------- | --------------------------------------------------------------- |
| T \| undefined | 创建或获取AppStorageV2数据成功时，返回数据；否则返回undefined。 |

**示例：**

```ts
'use static'

import { AppStorageV2 } from '@ohos.arkui.stateManagement';
import { ObservedV2, Trace } from '@ohos.arkui.stateManagement';

@ObservedV2
class SampleClass {
  @Trace p: number = 0;
}

const ISampleType = Type.of(new SampleClass());

// 将ttype为SampleClass的Type、value为new SampleClass()对象的键值对存储到内存中，并赋值给as2
const as2: SampleClass | undefined = AppStorageV2.connect<SampleClass>(ISampleType, () => new SampleClass());

// ttype为SampleClass的Type的对象已经在AppStorageV2中，将该对象返回给as3
const as3: SampleClass = AppStorageV2.connect<SampleClass>(ISampleType)!;
```

### remove

static remove(keyOrType: string | Type): void

将指定的键值对数据从[AppStorageV2](../../../application-dev/ui/state-management-static/arkts-static-appstoragev2.md)里面删除。如果指定的键值不存在于AppStorageV2中，将删除失败。

>**说明：**
>
>删除AppStorageV2中不存在的key会报警告。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型           | 必填 | 说明                                                                   |
| --------- | -------------- | ---- | ---------------------------------------------------------------------- |
| keyOrType | string \| Type | 是   | 需要删除的key。如果传入的是Type类型，则删除的key为Type类型入参的name。 |

**示例：**

<!--code_no_check-->
```ts
'use static'

import { AppStorageV2 } from '@ohos.arkui.stateManagement';

// 假设AppStorageV2中存在keyOrType为key_as2的键，从AppStorageV2中删除该键值对数据
AppStorageV2.remove('key_as2');

// 假设AppStorageV2中存在keyOrType为SampleClass的Type的键，从AppStorageV2中删除该键值对数据
AppStorageV2.remove(Type.of(new SampleClass()));

// 假设AppStorageV2中不存在keyOrType为key_as1的键，报警告
AppStorageV2.remove('key_as1');
```
### keys

static keys(): Array\<string\>

获取[AppStorageV2](../../../application-dev/ui/state-management-static/arkts-static-appstoragev2.md)中的所有key。

>**说明：**
>
>key在Array中的顺序是无序的，与key插入到AppStorageV2中的顺序无关。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型            | 说明                      |
| --------------- | ------------------------- |
| Array\<string\> | 所有AppStorageV2中的key。 |

**示例：**

```ts
'use static'

import { AppStorageV2 } from '@ohos.arkui.stateManagement';

// 假设AppStorageV2中存在两个key（key_as1、key_as2），返回[key_as1、key_as2]，并赋值给keys
const keys: Array<string> = AppStorageV2.keys();
```

## PersistenceV2

继承自[AppStorageV2](#appstoragev2)，PersistenceV2具体UI使用说明，详见[PersistenceV2(持久化存储UI状态)](../../ui/state-management-static/arkts-static-new-persistencev2.md)。

### globalConnect

static globalConnect\<T extends object\>(connectOptions: ConnectOptions\<T\>, toJson: ToJSONType<T>, fromJson: FromJSONType<T>): T | undefined

将键值对数据储存在应用磁盘中。如果给定的key已经存在于[PersistenceV2](../../ui/state-management-static/arkts-static-new-persistencev2.md)中，返回对应的值；否则，会通过获取默认值的构造器构造默认值，并返回。如果globalConnect的是\@ObservedV2对象，该对象\@Trace属性的变化，会触发整个关联对象的自动刷新；非\@Trace属性变化则不会，如有必要，可调用PersistenceV2.save接口手动存储。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**
| 参数名         | 类型                                     | 必填 | 说明                                                  |
| -------------- | ---------------------------------------- | ---- | ----------------------------------------------------- |
| connectOptions | [ConnectOptions\<T\>](#connectoptions20) | 是   | 传入的connect参数，详细说明见ConnectOptions参数说明。 |
| toJson         | ToJSONType\<T\>                          | 是   | 转换存储对象到json格式对象的函数                      |
| fromJson       | FromJSONType\<T\>                        | 是   | 转换json格式对象到存储对象的函数                      |

**返回值：**

| 类型           | 说明                                                |
| -------------- | --------------------------------------------------- |
| T \| undefined | 创建或获取数据成功时，返回数据；否则返回undefined。 |

> **说明：**
>
>
> 1、确保数据已经存储在PersistenceV2中，可省略默认构造器，获取存储的数据；否则必须指定默认构造器，不指定将导致应用异常。
>
> 2、同一个key，globalConnect不同类型的数据会导致应用异常，应用需要确保类型匹配。
>
> 3、key建议使用有意义的值，可由字母、数字、下划线组成，长度不超过255，使用非法字符或空字符的行为是未定义的。
>
> 4、关联[\@Observed](../../ui/state-management-static/arkts-static-observed-and-objectlink.md)对象时，因为该类型的name属性未定义，需要指定key或者自定义name属性。
>
> 4、数据的存储路径为应用级别，不同module使用相同的key和相同的加密分区进行globalConnect，存储的数据副本应用仅有一份。
>
> 5、globalConnect使用同一个key但设置了不同的加密级别，数据为第一个使用globalConnect的加密级别，并且PersistenceV2中的数据也会存入最先使用key的加密级别。
>
> 6、connect和globalConnect不建议混用，因为数据副本路径不同，如果混用，则key不可以一样，否则会crash。
>
> 7、EL5加密要想生效，需要开发者在module.json中配置字段ohos.permission.PROTECT_SCREEN_LOCK_DATA，使用说明见[声明权限](../../security/AccessToken/declare-permissions.md)。

**示例：**
仅供开发者了解globalConnect用法，完整使用需开发者自己写出@Entry组件。

<!--code_no_check-->
```ts
'use static'

import { contextConstant } from '@kit.AbilityKit';
import {
  PersistenceV2,
  ObservedV2,
  Trace
} from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace childId: number = 0;
  groupId: number = 1;
  public toJson(): jsonx.JsonElement {
    const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    // 存储 childId
    const childId = new jsonx.JsonElement();
    childId.setString(this.childId);
    root.setElement('childId', childId);
    const groupId = new jsonx.JsonElement();
    groupId.setDouble(this.groupId);
    root.setElement('groupId', groupId);
    return root;
  }
  public fromJson(json: jsonx.JsonElement): void {
    this.childId = json.getElement('childId').asString();
    this.groupId = json.getElement('groupId').asInteger();
  }
}

const toJsonSampleChild = (child: SampleChild) => {
    return child.toJson();
};

const fromJsonSampleChild = (json: jsonx.JsonElement): SampleChild => {
    let child = new SampleChild();
    child.fromJson(json);
    return child;
};

@ObservedV2
export class Sample {
  @Trace father: SampleChild = new SampleChild();
}

// key不传入尝试用为type的name作为key，加密参数不传入默认加密等级为EL2
const p: Sample = PersistenceV2.globalConnect({
  type: Sample,
  defaultCreator: () => new Sample(),
  }, toJsonSampleChild, fromJsonSampleChild)!;

// 使用key:global1连接，传入加密等级为EL1
const p1: Sample = PersistenceV2.globalConnect({
  type: Sample,
  key: 'global1',
  defaultCreator: () => new Sample(),
  areaMode: contextConstant.AreaMode.EL1
}，toJsonSampleChild, fromJsonSampleChild)!;

// 使用key:global2连接，使用构造函数形式，加密参数不传入默认加密等级为EL2
const p2: Sample = PersistenceV2.globalConnect({ 
  type: Sample,
  key: 'global2',
  defaultCreator: () => new Sample()
  }, toJsonSampleChild, fromJsonSampleChild)!;

// 使用key:global3连接，直接写加密数值，范围只能在0-4，否则运行会crash,例如加密设置为EL3
const p3: Sample = PersistenceV2.globalConnect({
  type: Sample,
  key: 'global3',
  defaultCreator: () => new Sample(),
  areaMode: 3
}, toJsonSampleChild, fromJsonSampleChild)!;

```

### save

static&nbsp;save\<T\>(keyOrType:&nbsp;string&nbsp;|&nbsp;Type\<T\>):&nbsp;void

将指定的键值对数据持久化一次。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型                | 必填 | 说明                                                             |
| --------- | ------------------- | ---- | ---------------------------------------------------------------- |
| keyOrType | string \| Type\<T\> | 是   | 需要持久化的key；如果指定的是type类型，持久化的key为type的name。 |

>**说明：**
>
>由于非[\@Trace](../../ui/state-management-static/arkts-static-new-observedV2-and-trace.md)的数据改变不会触发[PersistenceV2](../../ui/state-management-static/arkts-static-new-persistencev2.md)的自动持久化，如有必要，可调用该接口持久化对应key的数据。
>
>手动持久化当前内存中不处于connect状态的key是无意义的。

**示例：**

<!--code_no_check-->

```ts
@ObservedV2
class SampleClass {
  @Trace p: number = 0;
}

// 假设PersistenceV2中存在key为key_as2的键，持久化该键值对数据
PersistenceV2.save('key_as2');

// 假设PersistenceV2中存在key为SampleClass的键，持久化该键值对数据
PersistenceV2.save(Type.of(SampleClass));

// 假设PersistenceV2中不存在key为key_as1的键，无意义的操作
PersistenceV2.save('key_as1');
```

### notifyOnError

static notifyOnError(callback: PersistenceErrorCallback | undefined): void

在持久化失败时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名   | 类型                                  | 必填 | 说明               |
| -------- | ------------------------------------- | ---- | ------------------ |
| callback | PersistenceErrorCallback \| undefined | 是   | 持久化失败时调用。 |

**示例：**

```ts
// 持久化失败时调用
PersistenceV2.notifyOnError((key: string, reason: string, message: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${message}`);
});
```

## PersistenceErrorCallback

type PersistenceErrorCallback = (key: string, reason: 'quota' | 'serialization' | 'unknown', message: string) => void

持久化失败时返回错误原因的回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                    | 必填 | 说明             |
| ------- | --------------------------------------- | ---- | ---------------- |
| key     | string                                  | 是   | 出错的键值。     |
| reason  | 'quota' \| 'serialization' \| 'unknown' | 是   | 出错的原因类型。 |
| message | string                                  | 是   | 出错的更多消息。 |

**示例：**

```ts
'use static'

import {
  PersistenceV2,
  ObservedV2,
  Trace,
  Local,
  Entry,
  Column,
  Button,
  ClickEvent,
  ComponentV2
} from '@kit.ArkUI';

@ObservedV2
class Person {
  @Trace userName: string = 'John';
  userId: number = 1;

  public toJson(): jsonx.JsonElement {
    const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
    // 存储 userName
    const userNameEle = new jsonx.JsonElement();
    userNameEle.setString(this.userName);
    root.setElement('userName', userNameEle);

    const userIdEle = new jsonx.JsonElement();
    userIdEle.setDouble(this.userId);
    root.setElement('userId', userIdEle);

    return root;
  }

  public fromJson(json: jsonx.JsonElement): void {
    this.userName = json.getElement('userName').asString();
    this.userId = json.getElement('userId').asInteger();
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

// 接受序列化失败的回调
// PersistenceErrorCallback 指的是 (key: string, reason: string, msg: string) => {console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);}
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@Entry
@ComponentV2
struct Index {
  @Local cp: Person = PersistenceV2.connect<Person>(
    Type.from<Person>(),
    toJsonPerson,
    fromJsonPerson,
    (): Person => {
      return new Person();
    })!;

  build() {
    Column() {
      Button(`Page1 connect the key Sample ${this.cp.userName}`)
        .onClick((e: ClickEvent) => {
          this.cp = PersistenceV2.connect<Person>(Type.from<Person>(),
            'Key',
            toJsonPerson,
            fromJsonPerson,
            () => new Person())!;
        })
    }
    .width('100%')
    .height('100%')
  }
}
```


## ConnectOptions

globalConnect参数类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称           | 类型                       | 只读 | 可选 | 说明                                                                                                                                                                                                                                      |
| -------------- | -------------------------- | ---- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type           | Type                  | 否   | 否   | 指定的类型。                                                                                                                                                                                                                              |
| key            | string                     | 否   | 是   | 传入的key，不传则使用type的名字作为key。                                                                                                                                                                                                  |
| defaultCreator | StorageDefaultCreator\<T\> | 否   | 是   | 默认数据的构造器，建议传递，如果globalConnect是第一次连接key，不传会报错。                                                                                                                                                                |
| areaMode       | contextConstant.AreaMode   | 否   | 是   | 加密级别：EL1-EL5，详见[加密级别](../../application-models/application-context-stage.md#获取和修改加密分区)，对应数值：0-4，不传时默认为EL2，不同加密级别对应不同的加密分区，即不同的存储路径，传入的加密等级数值不在0-4会直接运行crash。 |

## UIUtils

UIUtils是状态管理提供的工具，用于处理可观察数据。

### makeObserved

static makeObserved\<T extends object\>(source: T): T

将不可观察数据转化为可观察数据。支持built-in类型（Array、Map、Set、Date）以及interface字面量。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| source | T    | 是   | 数据源对象。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| T    | 可观察的数据对象。 |

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, ClickEvent } from '@ohos.arkui.component';
import { UIUtils } from '@ohos.arkui.stateManagement';
interface Info {
  name: string,
  age: number
}
@Entry
@Component
struct Index {
  info: Info = UIUtils.makeObserved({ name: 'Jack', age: 25} as Info) as Info;
  build() {
    Column() {
      Text(`info.name: ${this.info.name}`)
        .onClick((e: ClickEvent) => {
          this.info.name = 'Tom';
        })
    }
  }
}
```

### getTarget

static getTarget\<T extends object\>(source: T): T

获取状态管理框架包装前的原始对象。支持built-in类型（Array、Map、Set、Date）以及interface字面量。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明                     |
| ------ | ---- | ---- | ------------------------ |
| source | T    | 是   | 状态管理框架包装的对象。 |

**返回值：**

| 类型 | 说明                           |
| ---- | ------------------------------ |
| T    | 状态管理框架包装前的原始对象。 |

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, ClickEvent } from '@ohos.arkui.component';
import { State, UIUtils } from '@ohos.arkui.stateManagement';
interface Info {
  name: string,
  age: number
}
@Entry
@Component
struct Index {
  rawInfo: Info = { name: 'Jack', age: 25} as Info;
  // 装饰字面量
  @State info: Info = this.rawInfo;
  build() {
    Column() {
      Text(`rawInfo === info: ${this.rawInfo === this.info}`) // false
      Text(`rawInfo === UIUtils.getTarget(info): ${this.rawInfo === UIUtils.getTarget(this.info)}`) // true
    }
  }
}
```

### makeBindingReadonly\<T\>

static makeBindingReadonly\<T\>(getter: GetterCallback\<T\>): Binding\<T\>

创建只读的单向数据绑定实例，用于在@Builder函数中为参数类型为Binding的参数提供实参。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                                                 |
| ------ | --------------------------------------- | ---- | ---------------------------------------------------- |
| getter | [GetterCallback\<T\>](#gettercallbackt) | 是   | 获取值的回调函数，每次访问值时重新执行以获取最新值。 |

**返回值：**

| 类型                      | 说明                                                            |
| ------------------------- | --------------------------------------------------------------- |
| [Binding\<T\>](#bindingt) | 包含一个value属性，用于获取当前绑定的值，且只能读取，不能修改。 |

**示例：**

```ts
'use static'

import { UIUtils, Binding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(readOnlyParam: Binding<number>) {
  Row() {
    Button(`Custom btn: ${readOnlyParam.value}`)
  }
}

@Entry
@Component
struct MyApp {
  @State num1: number = 1;
  build() {
    Column() {
      Button(`Entry btn ${this.num1}`)
        .onClick((e) => {
          this.num1 += 1;
        });
      CustomButton(
        /**
         * 创建只读绑定实例
         * @param getter - 返回this.number1的函数
         * @returns 只读的Binding<number>对象
         *
         * 特点：
         * 1. 每次访问.value时重新计算
         * 2. 不能直接修改值
         */
        UIUtils.makeBindingReadonly(() => this.num1),
      );
    }
  }
}
```

### makeBindingMutable\<T\>

static makeBindingMutable\<T\>(getter: GetterCallback\<T\>, setter: SetterCallback\<T\>): MutableBinding\<T\>

创建双向数据绑定实例，用于构建@Builder函数中类型为MutableBinding的参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                                     |
| ------ | --------------------------------------- | ---- | ---------------------------------------- |
| getter | [GetterCallback\<T\>](#gettercallbackt) | 是   | 获取值的回调函数，每次访问值时重新执行。 |
| setter | [SetterCallback\<T\>](#settercallbackt) | 是   | 定义如何更新值，当.value被修改时调用。   |

**返回值：**

| 类型                                    | 说明                                                                     |
| --------------------------------------- | ------------------------------------------------------------------------ |
| [MutableBinding\<T\>](#mutablebindingt) | 包含一个value属性，支持读取和修改数据，设置值时检查类型是否匹配泛型`T`。 |

**示例：**

```ts
'use static'

import { UIUtils, MutableBinding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(mutableParam1: MutableBinding<number>, mutableParam2: MutableBinding<number>) {
  Row() {
    Button(`Custom btn: ${mutableParam1.value} -- ${mutableParam2.value}`)
      .onClick((e) => {
        mutableParam1.value += 1;
        mutableParam2.value += 1;
      });
  }
}

@Entry
@Component
struct MyApp {
  @State num2: number = 10;
  @State num3: number = 100;

  build() {
    Column() {
      Button(`Entry btn ${this.num2} -- ${this.num3}`)
        .onClick((e) => {
          this.num2 += 1;
          this.num3 += 1;
        });
      CustomButton(
        /**
         * 创建绑定
         * @param getter - 返回this.number2的函数
         * @param setter - 绑定值修改时调用的回调
         * @returns 可变的MutableBinding<number>对象
         *
         * 特点：
         * 1. 支持读写操作
         * 2. 修改.value时会自动调用setter回调
         */
        UIUtils.makeBindingMutable(() => this.num2, (v) => {
          this.num2 = v;
        }),
        UIUtils.makeBindingMutable(() => this.num3, (v) => {
          this.num3 = v;
        })
      );
    }
  }
}
```

### makeBinding

static overload makeBinding { makeBindingReadonly, makeBindingMutable }

根据入参，自动匹配makeBindingReadonly和makeBindingMutable。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { UIUtils, Binding, MutableBinding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(readOnlyParam: Binding<number>, mutableParam: MutableBinding<number>) {
  Row() {
    Button(`Custom btn: ${readOnlyParam.value} -- ${mutableParam.value}`)
      .onClick((e) => {
        mutableParam.value += 1;
      });
  }
}

@Entry
@Component
struct MyApp {
  @State num2: number = 10;
  @State num3: number = 100;

  build() {
    Column() {
      Button(`Entry btn ${this.num2} -- ${this.num3}`)
        .onClick((e) => {
          this.num2 += 1;
          this.num3 += 1;
        });
      CustomButton(
        UIUtils.makeBinding(() => this.num2),
        UIUtils.makeBinding(() => this.num3, (v) => {
          this.num3 = v;
        })
      );
    }
  }
}
```

## GetterCallback\<T\>

type GetterCallback\<T\> = () => T

获取绑定值的回调方法。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明           |
| ---- | -------------- |
| T    | 返回当前组件。 |

**示例：**

```ts
'use static'

import { UIUtils, Binding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(readOnlyParam: Binding<number>) {
  Row() {
    Button(`Custom btn: ${readOnlyParam.value}`)
  }
}

@Entry
@Component
struct MyApp {
  @State num1: number = 1;
  build() {
    Column() {
      Button(`Entry btn ${this.num1}`)
        .onClick((e) => {
          this.num1 += 1;
        });
      CustomButton(
        // UIUtils.makeBinding函数的第一个参数是GetterCallback
        UIUtils.makeBinding(() => this.num1),
      );
    }
  }
}
```

## SetterCallback\<T\>

type SetterCallback\<T\> = (newValue: T) => void

设置绑定值的回调方法。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型 | 必填 | 说明            |
| -------- | ---- | ---- | --------------- |
| newValue | T    | 是   | 类型为T的参数。 |

**示例：**

```ts
'use static'

import { UIUtils,MutableBinding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(mutableParam1: MutableBinding<number>, mutableParam2: MutableBinding<number>) {
  Row() {
    Button(`Custom btn: ${mutableParam1.value} -- ${mutableParam2.value}`)
      .onClick((e) => {
        mutableParam1.value += 1;
        mutableParam2.value += 1;
      });
  }
}

@Entry
@Component
struct MyApp {
  @State num2: number = 10;
  @State num3: number = 100;

  build() {
    Column() {
      Button(`Entry btn ${this.num2} -- ${this.num3}`)
        .onClick((e) => {
          this.num2 += 1;
          this.num3 += 1;
        });
      CustomButton(
        // UIUtils.makeBinding函数的第二个参数应为SetterCallback
        UIUtils.makeBinding(() => this.num2, (v) => {
          this.num2 = v;
        }),
        UIUtils.makeBinding(() => this.num3, (v) => {
          this.num3 = v;
        })
      );
    }
  }
}
```

## Binding\<T\>

只读数据绑定的泛型类可以绑定任意类型的数据（需要与@builder参数列表同时使用）。当调用函数时，需要使用makeBinding来进行值的传递。

### value
get value(): T

提供get访问器以获取当前绑定值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明                                                  |
| ---- | ----------------------------------------------------- |
| T    | 返回值类型为泛型参数T，与Binding\<T\>定义的类型一致。 |

**示例：**

```ts
'use static'

import { Binding } from '@ohos.arkui.stateManagement';
import { Row, Button, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(readOnlyParam: Binding<number>) {
  // CustomButton的第一个参数为Binding，一个只读数据绑定的泛型类
  Row() {
    // num1.value Binding类可以使用绑定的值
    Button(`Custom btn: ${readOnlyParam.value}`)
  }
}
```

## MutableBinding\<T\>

可变数据绑定的泛型类，允许对绑定值进行读写操作，提供完整的get和set访问器（需要与@builder参数列表同时使用）。当调用函数时，需要使用makeBinding来进行值的传递。

### value
set value(newValue: T)

提供set访问器，用于设置当前绑定值。构造MutableBinding类实例时必须提供set访问器，否则会触发运行时错误。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型 | 必填 | 说明                                                       |
| -------- | ---- | ---- | ---------------------------------------------------------- |
| newValue | T    | 是   | 参数类型为泛型参数T，与MutableBinding\<T\>定义的类型一致。 |

### value
get value(): T

提供get访问器，用于获取当前绑定值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 描述                                                  |
| ---- | ----------------------------------------------------- |
| T    | 返回值类型为泛型参数T，与Binding\<T\>定义的类型一致。 |

**示例：**

```ts
'use static'

import { MutableBinding } from '@ohos.arkui.stateManagement';
import { Row, Button, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(mutableParam1: MutableBinding<number>, mutableParam2: MutableBinding<number>) {
  // CustomButton的第二个参数为MutableBinding，即一个可变数据绑定的泛型类
  Row() {
    Button(`Custom btn: ${mutableParam1.value} -- ${mutableParam2.value}`)
      .onClick((e) => {
        // 可变数据绑定的泛型类可以修改绑定的值
        mutableParam1.value += 1;
        mutableParam2.value += 1;
      });
  }
}
```

