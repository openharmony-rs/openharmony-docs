# ArkTS-Sta与ArkTS-Dyn应用间V2状态存储互操作

从API version 20开始，支持应用间V2状态存储互操作，在ArkTS-Sta和ArkTS-Dyn上下文中使用[AppStorageV2](./state-management-static/arkts-static-appstoragev2.md)的场景。在互操作场景下，[占位组件](../reference/apis-arkui/arkui-ts/ts-interop-compatible-component.md)连接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。通过建立统一数据存储机制，确保ArkTS-Sta和ArkTS-Dyn访问相同数据管理对象，实现状态和数据互通，从而在逐步迁移ArkTS-Dyn模块到ArkTS-Sta模块过程中，应用全局数据能够平滑过渡。

完整示例结构如下图所示：

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
- 在ArkTS-Sta子模块`data_center`的`data_center/src/main/ets/components/MainPage.ets`中进行数据构建。

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

- 对ArkTS-Sta子模块`data_center`中的数据模型进行导出。

```TypeScript
'use static'
// data_center/Index.ets

export { MessageModel } from './src/main/ets/components/MainPage';
```

- 在子模块`library`的`oh-package.json5`文件中配置子模块依赖。

```json
// library/oh-package.json5

"dependencies": {
  "data_center": "file:../data_center"
}
```

- 在ArkTS-Dyn模块`library`的`entry/src/main/ets/component/MainPage.ets`中进行数据存储并实现互操作方法。

```TypeScript
// entry/src/main/ets/component/MainPage.ets

import { AppStorageV2 } from '@kit.ArkUI';
import { MessageModel } from "data_center";

@ComponentV2
export struct MainPage {
  // 使用connect在AppStorageV2中创建一个key为Message11的对象
  @Local message: MessageModel = AppStorageV2.connect(
    MessageModel,
    'Message11',
    () => new MessageModel(11, 'this is dynamic message')
  )!;

  build() {
    Column() {
      Divider();
      Text('以下为ArkTS-Dyn内容').fontSize(20);

      Button(`get value from static`)
        .onClick(() => {
          // 在ArkTS-Dyn模块中，读取ArkTS-Sta模块中存储的key为Message12的对象。
          let message = AppStorageV2.connect(
            MessageModel,
            'Message12',
            () => new MessageModel());
        })

      Button(`get all keys`)
        .onClick(() => {
          // 在ArkTS-Dyn模块中，获取ArkTS-Sta模块和ArkTS-Dyn模块中所存储的所有key。
          let keys = AppStorageV2.keys();
        })

      Button('remove key: Message12')
        .onClick(() => {
          // 在ArkTS-Dyn模块中，删除ArkTS-Sta模块所存储的key。
          AppStorageV2.remove('Message12');
        })

      Button('reconnect key: Message11')
        .onClick(() => {
          // 当ArkTS-Dyn模块和ArkTS-Sta模块中都没有存储key为Message12的对象时，会在ArkTS-Dyn模块创建一个key为Message11的对象。
          this.message = AppStorageV2.connect(
            MessageModel,
            'Message11',
            () => new MessageModel(1111, 'this is dynamic reconnect message')
          )!;
        })
    }
  }
}
```

- 对ArkTS-Dyn模块`library`中的组件进行导出。

```TypeScript
// library/Index.ets

export { MainPage } from './src/main/ets/components/MainPage';
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "data_center": "file:../data_center",
  "library": "file:../library"
}
```

- 在ArkTS-Sta主模块`entry`的`entry/src/main/ets/pages/Index.ets`中进行数据存储并实现互操作方法。

```TypeScript
'use static'
// entry/src/main/ets/pages/Index.ets

import { Entry, Text, Column, Button, Divider, ComponentV2, Row } from '@ohos.arkui.component'
import { AppStorageV2, ObservedV2, Local } from '@ohos.arkui.stateManagement'
import { MainPage } from "library";
import { MessageModel } from "data_center";

@ComponentV2
@Entry
struct Index {
  // 使用connect在AppStorageV2中创建一个key为Message12的对象
  @Local message: MessageModel = AppStorageV2.connect<MessageModel>(
    Type.from<MessageModel>(),
    'Message12',
    () => new MessageModel(12, 'This is static message')
  )!;

  build() {
    Row() {
      Column() {
        Divider();
        Text('以下为ArkTS-Sta模块内容').fontSize(20);

        Button('get value from dynamic')
          .onClick(() => {
            // 在ArkTS-Sta模块中，读取ArkTS-Dyn模块中存储的key为Message11的对象。
            let message = AppStorageV2.connect<MessageModel>(
              Type.from<MessageModel>(),
              'Message11',
              () => new MessageModel()
            );
          })

        Button(`get all keys`)
          .onClick(() => {
            // 在ArkTS-Sta模块中，获取ArkTS-Dyn模块和ArkTS-Sta模块中所存储的所有key。
            let keys = AppStorageV2.keys();
          })

        Button('remove dynamic obj with key: "Message11"')
          .onClick(() => {
            // 在ArkTS-Sta模块中，删除ArkTS-Dyn模块所存储的key。
            AppStorageV2.remove('Message11');
          })

        Button('reconnect key: Message12')
          .onClick(() => {
            // 当ArkTS-Sta模块和ArkTS-Dyn模块中都没有存储key为Message12的对象时，会在ArkTS-Sta模块创建一个key为Message12的对象。
            this.message = AppStorageV2.connect<MessageModel>(
              Type.from<MessageModel>(),
              'Message12',
              () => new MessageModel(1212, 'this is reconnect message')
            )!;
          })

        // 调用ArkTS-Dyn模块组件，验证ArkTS-Sta与ArkTS-Dyn可互操作。
        MainPage();
      }
    }
  }
}
```


