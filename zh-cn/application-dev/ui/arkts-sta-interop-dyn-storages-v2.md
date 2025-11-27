# 在ArkTS-Sta中使用ArkTS-Dyn管理应用拥有的状态

## 概述

从API version 22开始，支持AppStorageV2互操作，在ArkTS-Sta和ArkTS-Dyn上下文中使用[AppStorageV2](./state-management-static/arkts-static-appstoragev2.md)的场景。

不支持[PersistenceV2](./state-management-static/arkts-static-new-persistencev2.md)互操作，详见[ArkTS-Sta和ArkTS-Dyn的PersistenceV2不支持互操作](#arkts-sta和arkts-dyn的persistencev2不支持互操作)。


## 使用限制

- 遵循ArkTS-Dyn AppStorageV2的[使用限制](../ui/state-management/arkts-new-appstoragev2.md#使用限制)；

- 遵循ArkTS-Dyn PersistenceV2的[使用限制](../ui/state-management/arkts-new-persistencev2.md#使用限制)；

- 遵循ArkTS-Sta AppStorageV2的[使用限制](../ui/state-management-static/arkts-static-appstoragev2.md#使用限制)；

- 遵循ArkTS-Sta PersistenceV2的[使用限制](../ui/state-management-static/arkts-static-new-persistencev2.md#使用限制)。


## 使用场景

### 在ArkTS-Sta模块调用AppStorageV2接口操作ArkTS-Dyn模块

完整示例结构如下：

```text
project/
├── entry/                             # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets      # 使用ArkTS-Dyn自定义组件，操作AppStorageV2的数据
│
├── dynamic_module/                    # ArkTS-Dyn子模块
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets   # 导出ArkTS-Dyn自定义组件，使用ArkTS-Sta导出的数据
│
└── static_module/                     # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets   # 导出数据ArkTS-Sta数据
```

示例如下：

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录进行数据构建。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { ObservedV2, Trace } from '@ohos.arkui.stateManagement';
import { enableCompatibleObservedV2ForDynamic } from '@ohos.arkui.component';

export const STATIC_KEY = 'MessageStatic';
export const DYNAMIC_KEY = 'MessageDynamic';
export const FONT_SIZE: int = 20;
export const MARGIN: int = 10;

// AppStorageV2所存储的数据模型
@ObservedV2
export class MessageModel { // 定义MessageModel数据类
  @Trace messageId: number;
  messageContent: string;

  constructor(messageId?: number, messageContent?: string) {
    this.messageId = messageId ?? 1;
    this.messageContent = messageContent ?? 'Hello';
  }
}

// 导出ArkTS-Sta中实现的enableCompatibleObservedV2ForDynamic方法
export function setEnableCompatibleObservedV2ForDynamic(T: Object) {
  // 调用enableCompatibleObservedV2ForDynamic方法，使ArkTS-Sta @Trace修饰的属性在ArkTS-Dyn中可观测
  enableCompatibleObservedV2ForDynamic(T);
}
```

- 对ArkTS-Sta子模块`static_module/Index.ets`文件中的数据模型进行导出。

```TypeScript
'use static'

// static_module/Index.ets
export {
  STATIC_KEY, DYNAMIC_KEY, FONT_SIZE, MARGIN, MessageModel, setEnableCompatibleObservedV2ForDynamic
} from './src/main/ets/components/MainPage'; // 导出MessageModel数据类
```

- 在子模块的`dynamic_module/oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// dynamic_module/oh-package.json5

"dependencies": {
  // 从根目录导入依赖模块
  "static_module": "file:../static_module"
}
```

- 在ArkTS-Dyn模块的`dynamic_module/src/main/ets/component/MainPage.ets`文件中进行数据模型声明并初始化一个key为MessageDynamic的MessageModel对象。

```TypeScript
// dynamic_module/src/main/ets/component/MainPage.ets

import { AppStorageV2 } from '@kit.ArkUI';
import {
  STATIC_KEY, DYNAMIC_KEY, FONT_SIZE, MARGIN, MessageModel, setEnableCompatibleObservedV2ForDynamic
} from 'static_module';

@ComponentV2
export struct MainPage {
  // 使用connect在ArkTS-Dyn模块的AppStorageV2中创建一个key为MessageDynamic的MessageModel对象
  // 修改connect的返回值即可同步回AppStorageV2
  @Local message: MessageModel = AppStorageV2.connect(
    MessageModel,
    `${DYNAMIC_KEY}`,
    () => new MessageModel(11, 'this is dynamic message')
  )!;

  aboutToAppear() {
    // 调用setEnableCompatibleObservedV2ForDynamic方法，使ArkTS-Sta @Trace修饰的属性在ArkTS-Dyn中可观测
    setEnableCompatibleObservedV2ForDynamic(this.message);
  }

  build() {
    Column() {
      Divider()
        .margin(`${MARGIN}`)

      Text('------ ArkTS-Dyn ------')
        .fontSize(`${FONT_SIZE}`)
        .margin(`${MARGIN}`)

      // 在ArkTS-Dyn模块调用connect函数, 会从ArkTS-Dyn模块的AppStorageV2中获取key为MessageDynamic的MessageModel的对象
      // 在ArkTS-Sta模块中remove之后，回到ArkTS-Dyn模块重新connect添加，修改ArkTS-Sta模块的组件的messageId，可以发现在ArkTS-Dyn模块数据已经不同步，在ArkTS-Sta模块中重新connect之后，数据一致
      // 在this.message被重新赋值时，需要调用setEnableCompatibleObservedV2ForDynamic方法，使ArkTS-Sta @Trace修饰的属性可以在ArkTS-Dyn中重新被观测
      Button(`connect key: ${DYNAMIC_KEY}`)
        .fontSize(`${FONT_SIZE}`)
        .margin(`${MARGIN}`)
        .onClick(() => {
          const msg = AppStorageV2.connect(
            MessageModel,
            `${DYNAMIC_KEY}`,
            () => new MessageModel(11, 'This is reconnected dynamic message')
          )!;
          if (this.message !== msg) {
            this.message = msg;
            setEnableCompatibleObservedV2ForDynamic(this.message);
          }
        })

      // 修改@Trace装饰的类属性，UI能同步刷新
      Text(`messageId: ${this.message.messageId}`)
        .fontSize(`${FONT_SIZE}`)
        .margin(`${MARGIN}`)
        .onClick(() => {
          this.message.messageId += 5;
        })

      // 修改非@Trace装饰的类属性，UI不会同步刷新，但修改的类属性已同步回AppStorageV2
      Text(`messageContent: ${this.message.messageContent}`)
        .fontSize(`${FONT_SIZE}`)
        .margin(`${MARGIN}`)
        .onClick(() => {
          this.message.messageContent += ' plus';
        })
    }
  }
}
```

- 对ArkTS-Dyn模块`dynamic_module/Index.ets`文件中的组件进行导出。

```TypeScript
// dynamic_module/Index.ets

export { MainPage } from './src/main/ets/components/MainPage'; // 导出ArkTS-Dyn自定义组件
```

- 在主模块的`entry/oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  // 从根目录导入依赖模块
  "static_module": "file:../static_module",
  "dynamic_module": "file:../dynamic_module"
}
```

- 在ArkTS-Sta主模块的`entry/src/main/ets/pages/Index.ets`文件中进行数据存储并实现互操作方法。

```TypeScript
'use static'

// entry/src/main/ets/pages/Index.ets
import { Entry, Text, Column, Button, Divider, ComponentV2, Row } from '@ohos.arkui.component';
import { AppStorageV2, Local } from '@ohos.arkui.stateManagement';

import { MainPage } from 'dynamic_module'; // 导入ArkTS-Dyn自定义组件
import { MessageModel, FONT_SIZE, STATIC_KEY, DYNAMIC_KEY, MARGIN } from 'static_module'; // 导入ArkTS-Sta数据类

@Entry
@ComponentV2
struct Index {
  // 声明一个MessageModel对象
  @Local dynMessage: MessageModel = new MessageModel();
  @Local keys: Array<string> = AppStorageV2.keys();

  build() {
    Row() {
      Column() {
        Text('------ ArkTS-Sta ------')
          .fontSize(`${FONT_SIZE}`)
          .margin(`${MARGIN}`)

        // 使用connect在ArkTS-Sta模块的AppStorageV2中创建一个key为MessageStatic的MessageModel对象
        Button(`connect key: ${STATIC_KEY}`)
          .fontSize(`${FONT_SIZE}`)
          .margin(`${MARGIN}`)
          .onClick(() => {
            const message: MessageModel = AppStorageV2.connect<MessageModel>(
              Type.from<MessageModel>(),
              `${STATIC_KEY}`,
              () => new MessageModel(22, 'This is static message')
            )!;
          })

        // 在ArkTS-Sta模块调用connect函数, 会从ArkTS-Dyn模块的AppStorageV2中获取key为MessageDynamic的MessageModel的对象
        // 修改connect的返回值即可同步回ArkTS-Dyn模块的AppStorageV2
        // 如果ArkTS-Dyn模块的AppStorageV2中不存在key为MessageDynamic的MessageModel的对象，则会在ArkTS-Sta模块的AppStorageV2中创建一个key为MessageDynamic的MessageModel对象
        Button(`connect key: ${DYNAMIC_KEY}`)
          .fontSize(`${FONT_SIZE}`)
          .margin(`${MARGIN}`)
          .onClick(() => {
             this.dynMessage = AppStorageV2.connect<MessageModel>(
              Type.from<MessageModel>(),
              `${DYNAMIC_KEY}`,
              () => new MessageModel(11, 'This message is connected in Sta')
            )!;
          })

        // 在ArkTS-Sta模块调用remove函数, 会从ArkTS-Sta模块和ArkTS-Dyn模块的AppStorageV2中删除key为MessageDynamic的MessageModel的对象
        // remove之后，修改messageId，ArkTS-Sta模块和ArkTS-Dyn模块的组件能同步变化，因为remove只是从AppStorageV2删除，不会影响组件中已存在的数据
        Button(`remove key: ${DYNAMIC_KEY}`)
          .fontSize(`${FONT_SIZE}`)
          .margin(`${MARGIN}`)
          .onClick(() => {
            AppStorageV2.remove(`${DYNAMIC_KEY}`);
          })

        // 修改@Trace装饰的类属性，UI能同步刷新
        Text(`messageId: ${this.dynMessage.messageId}`)
          .fontSize(`${FONT_SIZE}`)
          .margin(`${MARGIN}`)
          .onClick(() => {
            this.dynMessage.messageId += 1;
          })

        // 修改非@Trace装饰的类属性，UI不会同步刷新，但修改的类属性已同步回AppStorageV2
        Text(`messageContent: ${this.dynMessage.messageContent}`)
          .fontSize(`${FONT_SIZE}`)
          .margin(`${MARGIN}`)
          .onClick(() => {
            this.dynMessage.messageContent += ' plus';
          })

        // connect或者remove操作后，查看AppStorageV2存储的MessageModel对象的所有key
        Text(`get all keys: ${this.keys}`)
          .fontSize(`${FONT_SIZE}`)
          .margin(`${MARGIN}`)
          .onClick(() => {
            this.keys = AppStorageV2.keys();
          })

        // 调用ArkTS-Dyn模块组件，初始化一个ArkTS-Dyn对象
        MainPage()
      }
    }
  }
}
```

![appstoragev2_sta_to_dyn](figures/interop_appstoragev2_sta_to_dyn.gif)


### ArkTS-Sta和ArkTS-Dyn的PersistenceV2不支持互操作

ArkTS-Sta和ArkTS-Dyn的[PersistenceV2](state-management-static/arkts-static-new-persistencev2.md)由于序列化反序列化差异，不支持互操作。如果有场景必须在ArkTS-Dyn模块使用ArkTS-Sta模块的PersistenceV2或在ArkTS-Sta模块使用ArkTS-Dyn模块的PersistenceV2，从API version 22开始，可以通过在ArkTS-Sta模块或ArkTS-Dyn模块提供自定义对外接口封装PersistenceV2来实现相互使用。

完整示例结构如下：

```text
project/
├── entry/                            # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 使用ArkTS-Dyn导出的方法
|
└── dynamic_module/                   # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 导出ArkTS-Dyn方法供ArkTS-Sta调用，以操作PersistenceV2
```

示例如下：

- 在ArkTS-Dyn子模块的`dynamic_module/src/main/ets/component/MainPage.ets`文件中进行接口实现。

```TypeScript
// dynamic_module/src/main/ets/component/MainPage.ets

import { PersistenceV2, Type } from '@kit.ArkUI';

// 接受序列化失败的回调
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

// PersistenceV2存储的数据模型
@ObservedV2
class DynDataModelChild {
  @Trace canTraceProp: number = 0;
  normalProp: number = 10;

  constructor(canTraceProp?: number, normalProp?: number) {
    this.canTraceProp = canTraceProp ?? 0;
    this.normalProp = normalProp ?? 10;
  }
}

@ObservedV2
export class DynDataModel {
  // 对于复杂对象需要@Type修饰，确保序列化成功
  @Type(DynDataModelChild)
  @Trace dynDataModelChild: DynDataModelChild = new DynDataModelChild();
}

// 对外接口，对ArkTS-Dyn模块canTraceProp的值进行累加
// 如果ArkTS-Dyn模块的PersistenceV2中无key为DynDataModel的DynDataModel对象，则创建该对象
// 反之则获取该对象并与sample关联，返回sample的canTraceProp给调用者
export function canTracePropPlusInDynamic(): number {
  const sample = PersistenceV2.connect(DynDataModel, 'DynDataModel', () => new DynDataModel())!;
  sample.dynDataModelChild.canTraceProp++;
  return sample.dynDataModelChild.canTraceProp;
}

// 对外接口，对ArkTS-Dyn模块normalProp的值进行累加
// 如果ArkTS-Dyn模块的PersistenceV2中无key为DynDataModel的DynDataModel对象，则创建该对象
// 反之则获取该对象并与sample关联，返回sample的normalProp给调用者
// ArkTS-Dyn模块页面不刷新，但是normalProp值改变了
export function normalPropPlusInDynamic(): number {
  const sample = PersistenceV2.connect(DynDataModel, 'DynDataModel', () => new DynDataModel())!;
  sample.dynDataModelChild.normalProp++;
  return sample.dynDataModelChild.normalProp;
}

// 对外接口，实现调用ArkTS-Dyn模块的PersistenceV2.connect接口
export function connectInDynamic(): DynDataModel {
  return PersistenceV2.connect(DynDataModel, 'DynDataModel', () => new DynDataModel())!;
}

// 对外接口，实现调用ArkTS-Dyn模块的PersistenceV2.save接口
export function saveInDynamic(): void {
  PersistenceV2.save(DynDataModel);
}

// 对外接口，实现调用ArkTS-Dyn模块的PersistenceV2.remove接口
export function removeInDynamic(): void {
  PersistenceV2.remove(DynDataModel);
}

// 对外接口，实现调用ArkTS-Dyn模块的PersistenceV2.keys接口
export function keysInDynamic(): string[] {
  const result = PersistenceV2.keys();
  return result;
}

@ComponentV2
export struct MainPage {
  // 在PersistenceV2中创建一个key为DynDataModel的键值对（如果存在，则返回PersistenceV2中的数据），并且和localVar关联
  // 对于需要换connect对象的localVar属性，需要加@Local修饰（不建议对属性换connect的对象）
  @Local localVar: DynDataModel = PersistenceV2.connect(DynDataModel, () => new DynDataModel())!;
  @Local keys: string[] = PersistenceV2.keys();

  build() {
    Column() {
      Divider()
        .margin(10)

      Text('This is ArkTS-Dyn part')
        .fontSize(20)
        .margin(10)

      // 在ArkTS-Sta模块调用connect接口重连后，重新与localVar关联，页面数据刷新
      Button('refresh data')
        .margin(10)
        .onClick(() => {
          this.localVar = connectInDynamic();
        })

      // 页面刷新，canTraceProp的值改变了
      Text(`add 1 to canTraceProp: ${this.localVar.dynDataModelChild.canTraceProp}`)
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.localVar.dynDataModelChild.canTraceProp++;
        })

      // 页面不刷新，但是normalProp的值改变了
      Text(`add 1 to normalProp: ${this.localVar.dynDataModelChild.normalProp}`)
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.localVar.dynDataModelChild.normalProp++;
        })

      // 获取当前PersistenceV2里面的所有key
      Text(`get all keys: ${this.keys}`)
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          // 刷新页面中的所有key
          this.keys = PersistenceV2.keys();
        })
    }
  }
}
```

- 对ArkTS-Dyn子模块`dynamic_module/Index.ets`文件中的接口进行导出。

```TypeScript
// dynamic_module/Index.ets

export {
  MainPage, canTracePropPlusInDynamic, normalPropPlusInDynamic, connectInDynamic, saveInDynamic, removeInDynamic,
  keysInDynamic, DynDataModel
} from './src/main/ets/components/MainPage';
```

- 在主模块的`entry/oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  // 从根目录导入依赖模块
  "dynamic_module": "file:../dynamic_module"
}
```

- 在ArkTS-Sta模块的`entry/src/main/ets/pages/Index.ets`文件中调用ArkTS-Dyn模块的自定义接口。

```TypeScript
'use static'
// entry/src/main/ets/pages/Index.ets

import { Entry, Text, Column, ComponentV2, Button, Divider } from '@ohos.arkui.component';
import { Local } from '@ohos.arkui.stateManagement';
import {
  MainPage, canTracePropPlusInDynamic, normalPropPlusInDynamic, connectInDynamic, saveInDynamic, removeInDynamic,
  keysInDynamic, DynDataModel
} from 'dynamic_module';

@Entry
@ComponentV2
struct Index {
  // 承接ArkTS-Dyn模块的数据
  @Local canTraceProp: number = 0;
  @Local normalProp: number = 10;
  @Local keys: Array<string> = [];

  build() {
    Column() {
      Text('This is ArkTS-Sta part')
        .fontSize(20)
        .margin(10)

      // 在ArkTS-Sta模块调用ArkTS-Dyn模块的connect接口，返回一个key为DynDataModel的DynDataModel对象
      Button('connect key DynDataModel by Dyn')
        .margin(10)
        .onClick(() => {
          const dynDataModel: DynDataModel = connectInDynamic();
          this.canTraceProp = dynDataModel.dynDataModelChild.canTraceProp;
          this.normalProp = dynDataModel.dynDataModelChild.normalProp;
        })

      // 在ArkTS-Sta模块调用ArkTS-Dyn模块的remove接口
      Button('remove key DynDataModel by Dyn')
        .margin(10)
        .onClick(() => {
          removeInDynamic();
        })

      // 在ArkTS-Sta模块调用ArkTS-Dyn模块的save接口
      Button('save key DynDataModel by Dyn')
        .margin(10)
        .onClick(() => {
          saveInDynamic();
        })

      // 在ArkTS-Sta模块调用ArkTS-Dyn模块的canTraceProp累加接口
      // this.canTraceProp被重新赋值，页面刷新
      Text(`add 1 to canTraceProp by Dyn: ${this.canTraceProp}`)
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.canTraceProp = canTracePropPlusInDynamic();
        })

      // 在ArkTS-Sta模块调用ArkTS-Dyn模块的normalProp累加接口
      // this.normalProp被重新赋值，页面刷新
      Text(`add 1 to normalProp by Dyn: ${this.normalProp}`)
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.normalProp = normalPropPlusInDynamic();
        })

      Text(`get all keys by Dyn: ${this.keys}`)
        .fontSize(20)
        .margin(10)
        .onClick(() => {
          this.keys = keysInDynamic();
        })

      // 调用ArkTS-Dyn模块组件，初始化一个ArkTS-Dyn对象
      MainPage()
    }
    .width('100%')
    .height('100%')
  }
}
```

![persistenceV2_sta_to_dyn](figures/interop_persistencev2_sta_to_dyn.gif)