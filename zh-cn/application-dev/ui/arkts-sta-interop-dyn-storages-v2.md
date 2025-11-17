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
├── entry/                           # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 使用ArkTS-Dyn自定义组件，操作AppStorageV2的数据
│
├── dynamic_module/                   # ArkTS-Dyn子模块
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

// 数据
@ObservedV2
export class MessageModel { // 定义MessageModel数据类
  @Trace messageId: number;
  @Trace messageContent: string;

  constructor(messageId?: number, messageContent?: string) {
    this.messageId = messageId ?? 1;
    this.messageContent = messageContent ?? 'Hello';
  }
}
```

- 对ArkTS-Sta子模块`static_module/Index.ets`文件中的数据模型进行导出。

```TypeScript
'use static'

// static_module/Index.ets
export { MessageModel } from './src/main/ets/components/MainPage'; // 导出MessageModel数据类
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
import { MessageModel } from 'static_module';

@ComponentV2
export struct MainPage {
  // 使用connect在AppStorageV2中创建一个key为MessageDynamic的MessageModel对象
  @Local message: MessageModel = AppStorageV2.connect(
    MessageModel,
    'MessageDynamic',
    () => new MessageModel(11, 'this is dynamic message')
  )!;

  build() {
    Column() {}
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
import { MessageModel } from 'static_module'; // 导入ArkTS-Sta数据类

@Entry
@ComponentV2
struct Index {
  // 使用connect在AppStorageV2中创建一个key为MessageStatic的MessageModel对象
  @Local message: MessageModel = AppStorageV2.connect<MessageModel>(
    Type.from<MessageModel>(),
    'MessageStatic',
    () => new MessageModel(12, 'This is static message')
  )!;

  build() {
    Row() {
      Column() {
        Divider()
        Text('------ ArkTS-Sta ------')
          .fontSize(30)

        Button('get value from dynamic')
          .onClick(() => {
            // 在ArkTS-Sta模块中，读取ArkTS-Dyn模块中存储的key为MessageDynamic的MessageModel对象
            let message = AppStorageV2.connect<MessageModel>(
              Type.from<MessageModel>(),
              'MessageDynamic',
              () => new MessageModel()
            );
          })

        Button(`get all keys`)
          .onClick(() => {
            // 在ArkTS-Sta模块中，获取ArkTS-Dyn模块和ArkTS-Sta模块中所存储的所有key
            let keys = AppStorageV2.keys();
          })

        Button('remove dynamic obj with key: "MessageDynamic"')
          .onClick(() => {
            // 在ArkTS-Sta模块中，删除ArkTS-Dyn模块所存储的key
            AppStorageV2.remove('MessageDynamic');
          })

        Button('reconnect key: MessageStatic')
          .onClick(() => {
            // 当ArkTS-Sta模块和ArkTS-Dyn模块中都没有存储key为MessageDynamic的对象时，会在ArkTS-Sta模块创建一个key为MessageDynamic的对象
            this.message = AppStorageV2.connect<MessageModel>(
              Type.from<MessageModel>(),
              'MessageDynamic',
              () => new MessageModel(1111, 'this is reconnect message')
            )!;
          })

        // 调用ArkTS-Dyn模块组件，初始化一个ArkTS-Dyn对象
        MainPage()
      }
    }
  }
}
```


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

import { PersistenceV2 } from '@kit.ArkUI';

// 接受序列化失败的回调
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@ObservedV2
class PersistenceModel {
  @Trace year: number = 1;
  @Trace day: number = 2;

  constructor(year?: number, day?: number) {
    this.year = year ?? 1;
    this.day = day ?? 2;
  }
}

// 在ArkTS-Dyn模块声明并实现connect接口
export function connectInDynamic(key: string): PersistenceModel | undefined {
  let pModel = PersistenceV2.connect(PersistenceModel, key, () => new PersistenceModel())!;
  return pModel;
}

// 在ArkTS-Dyn模块声明并实现save接口
export function saveInDynamic(key: string): void {
  PersistenceV2.save(key);
}

// 在ArkTS-Dyn模块声明并实现remove接口
export function removeInDynamic(key: string): void {
  PersistenceV2.remove(key);
}
```

- 对ArkTS-Dyn子模块`dynamic_module/Index.ets`文件中的接口进行导出。

```TypeScript
// dynamic_module/Index.ets

export { connectInDynamic, saveInDynamic, removeInDynamic } from './src/main/ets/components/MainPage';
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
import { connectInDynamic, saveInDynamic, removeInDynamic } from 'dynamic_module'; // 导入ArkTS-Dyn方法

@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      Divider()
      Text('This is ArkTS-Sta part')
        .fontSize(30)

      Button('dynamic connect')
        .onClick(() => {
          // 在ArkTS-Sta模块调用ArkTS-Dyn模块的自定义connect接口
          let pModel = connectInDynamic('dynamic_key_persistence_dynamic');
        })

      Button('dynamic save')
        .onClick(() => {
          // 在ArkTS-Sta模块调用ArkTS-Dyn模块的自定义save接口
          saveInDynamic('dynamic_key_persistence_dynamic');
        })

      Button('dynamic remove')
        .onClick(() => {
          // 在ArkTS-Sta模块调用ArkTS-Dyn模块的自定义remove接口
          removeInDynamic('dynamic_key_persistence_dynamic');
        })
    }
    .width('100%')
    .height('100%')
  }
}
```
