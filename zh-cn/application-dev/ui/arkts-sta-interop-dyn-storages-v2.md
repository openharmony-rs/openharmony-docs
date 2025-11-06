# ArkTS-Dyn使用ArkTS-Sta的AppStorageV2进行状态存储

从API version 22开始，支持AppStorageV2互操作，在ArkTS-Sta和ArkTS-Dyn上下文中使用[AppStorageV2](./state-management-static/arkts-static-appstoragev2.md)的场景。在互操作场景下，[占位组件](../reference/apis-arkui/arkui-ts/ts-interop-compatible-component.md)连接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。通过建立统一数据存储机制，确保ArkTS-Sta和ArkTS-Dyn访问相同数据管理对象，实现状态和数据互通，从而在逐步迁移ArkTS-Dyn模块到ArkTS-Sta模块过程中，应用全局数据能够平滑过渡。

## 在ArkTS-Sta模块调用AppStorageV2接口操作ArkTS-Dyn模块

完整示例结构如下：

```text
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
├── library/        # ArkTS-Dyn子模块
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets
│
└── data_center/    # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

示例如下：
- 在ArkTS-Sta子模块的`data_center/src/main/ets/components/MainPage.ets`文件中进行数据构建。

```TypeScript
'use static'
// data_center/src/main/ets/components/MainPage.ets

import { ObservedV2, Trace } from '@ohos.arkui.stateManagement';

// 数据中心
@ObservedV2
export class MessageModel {
  @Trace messageId: number;
  @Trace messageContent: string;

  constructor(messageId?: number, messageContent?: string) {
    this.messageId = messageId ?? 1;
    this.messageContent = messageContent ?? 'Hello';
  }
}
```

- 对ArkTS-Sta子模块`data_center/Index.ets`文件中的数据模型进行导出。

```TypeScript
'use static'
// data_center/Index.ets

export { MessageModel } from './src/main/ets/components/MainPage';
```

- 在子模块的`library/oh-package.json5`文件中配置子模块依赖。

```json
// library/oh-package.json5

"dependencies": {
  // 从根目录导入依赖模块。
  "data_center": "file:../data_center"
}
```

- 在ArkTS-Dyn模块的`library/src/main/ets/component/MainPage.ets`文件中进行数据模型声明并初始化一个key为MessageDynamic的MessageModel对象。

```TypeScript
// library/src/main/ets/component/MainPage.ets

import { AppStorageV2 } from '@kit.ArkUI';
import { MessageModel } from "data_center";

@ComponentV2
export struct MainPage {
  // 使用connect在AppStorageV2中创建一个key为MessageDynamic的MessageModel对象。
  @Local message: MessageModel = AppStorageV2.connect(
    MessageModel,
    'MessageDynamic',
    () => new MessageModel(11, 'this is dynamic message')
  )!;

  build() {
  }
}
```

- 对ArkTS-Dyn模块`library/Index.ets`文件中的组件进行导出。

```TypeScript
// library/Index.ets

export { MainPage } from './src/main/ets/components/MainPage';
```

- 在主模块的`entry/oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  // 从根目录导入依赖模块。
  "data_center": "file:../data_center",
  "library": "file:../library"
}
```

- 在ArkTS-Sta主模块的`entry/src/main/ets/pages/Index.ets`文件中进行数据存储并实现互操作方法。

```TypeScript
'use static'
// entry/src/main/ets/pages/Index.ets

import { Entry, Text, Column, Button, Divider, ComponentV2, Row } from '@ohos.arkui.component';
import { AppStorageV2, Local } from '@ohos.arkui.stateManagement';
import { MainPage } from 'library';
import { MessageModel } from 'data_center';

@ComponentV2
@Entry
struct Index {
  // 使用connect在AppStorageV2中创建一个key为MessageStatic的MessageModel对象。
  @Local message: MessageModel = AppStorageV2.connect<MessageModel>(
    Type.from<MessageModel>(),
    'MessageStatic',
    () => new MessageModel(12, 'This is static message')
  )!;

  build() {
    Row() {
      Column() {
        Divider()
        Text('以下为ArkTS-Sta模块内容').fontSize(20)

        Button('get value from dynamic')
          .onClick(() => {
            // 在ArkTS-Sta模块中，读取ArkTS-Dyn模块中存储的key为MessageDynamic的MessageModel对象。
            let message = AppStorageV2.connect<MessageModel>(
              Type.from<MessageModel>(),
              'MessageDynamic',
              () => new MessageModel()
            );
          })

        Button(`get all keys`)
          .onClick(() => {
            // 在ArkTS-Sta模块中，获取ArkTS-Dyn模块和ArkTS-Sta模块中所存储的所有key。
            let keys = AppStorageV2.keys();
          })

        Button('remove dynamic obj with key: "MessageDynamic"')
          .onClick(() => {
            // 在ArkTS-Sta模块中，删除ArkTS-Dyn模块所存储的key。
            AppStorageV2.remove('MessageDynamic');
          })

        Button('reconnect key: MessageStatic')
          .onClick(() => {
            // 当ArkTS-Sta模块和ArkTS-Dyn模块中都没有存储key为MessageDynamic的对象时，会在ArkTS-Sta模块创建一个key为MessageDynamic的对象。
            this.message = AppStorageV2.connect<MessageModel>(
              Type.from<MessageModel>(),
              'MessageDynamic',
              () => new MessageModel(1111, 'this is reconnect message')
            )!;
          })

        // 调用ArkTS-Dyn模块组件，初始化一个ArkTS-Dyn对象。
        MainPage()
      }
    }
  }
}
```


## ArkTS-Sta和ArkTS-Dyn的PersistenceV2不支持互操作

ArkTS-Sta和ArkTS-Dyn的[PersistenceV2](state-management-static/arkts-static-new-persistencev2.md)由于序列化反序列化差异，不支持互操作。如果有场景必须在ArkTS-Dyn模块使用ArkTS-Sta模块的PersistenceV2或在ArkTS-Sta模块使用ArkTS-Dyn模块的PersistenceV2，从API version 22开始，可以通过在ArkTS-Sta模块或ArkTS-Dyn模块提供自定义对外接口封装PersistenceV2来实现相互使用。

**在ArkTS-Sta模块调用ArkTS-Dyn模块提供的自定义接口**

完整示例结构如下：

```text
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
|
└── dynamic/        # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

- 在ArkTS-Dyn子模块的`dynamic/src/main/ets/component/MainPage.ets`文件中进行接口实现。

```TypeScript
// dynamic/src/main/ets/component/MainPage.ets

import { PersistenceV2 } from '@kit.ArkUI';

// 接受序列化失败的回调
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@ObservedV2
class PersistenceModel {
  @Trace p1: number = 1;
  @Trace p2: number = 2;

  constructor(p1?: number, p2?: number) {
    this.p1 = p1 ?? 10001;
    this.p2 = p2 ?? 10002;
  }
}

// 在ArkTS-Dyn模块声明并实现connect接口。
export function connectInDynamic(key: string): PersistenceModel | undefined {
  let pModel = PersistenceV2.connect(PersistenceModel, key, () => new PersistenceModel())!;
  return pModel;
}

// 在ArkTS-Dyn模块声明并实现save接口。
export function saveInDynamic(key: string): void {
  PersistenceV2.save(key);
}

// 在ArkTS-Dyn模块声明并实现remove接口。
export function removeInDynamic(key: string): void {
  PersistenceV2.remove(key);
}
```

- 对ArkTS-Dyn子模块`dynamic/Index.ets`文件中的接口进行导出。

```TypeScript
// dynamic/Index.ets

export { connectInDynamic, saveInDynamic, removeInDynamic } from './src/main/ets/components/MainPage';
```

- 在主模块的`entry/oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  // 从根目录导入依赖模块。
  "dynamic": "file:../dynamic"
}
```

- 在ArkTS-Sta模块的`entry/src/main/ets/pages/Index.ets`文件中调用ArkTS-Dyn模块的自定义接口。

```TypeScript
'use static'
// entry/src/main/ets/pages/Index.ets

import { Entry, Text, Column, ComponentV2, Button, Divider } from '@ohos.arkui.component';
import { connectInDynamic, saveInDynamic, removeInDynamic } from 'dynamic';

@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      Divider()
      Text('This is Ark-Sta part').fontSize(20)

      Button('dynamic connect')
        .onClick(() => {
          // 在ArkTS-Sta模块调用ArkTS-Dyn模块的自定义connect接口。
          let pModel = connectInDynamic('dynamic_key_persistence_dynamic');
        })

      Button('dynamic save')
        .onClick(() => {
          // 在ArkTS-Sta模块调用ArkTS-Dyn模块的自定义save接口。
          saveInDynamic('dynamic_key_persistence_dynamic');
        })

      Button('dynamic remove')
        .onClick(() => {
          // 在ArkTS-Sta模块调用ArkTS-Dyn模块的自定义remove接口。
          removeInDynamic('dynamic_key_persistence_dynamic');
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#e6aaeeff')
  }
}
```