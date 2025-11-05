# ArkTS-Sta使用ArkTS-Dyn的AppStorageV2进行状态存储

从API version 22开始，支持AppStorageV2互操作，在ArkTS-Sta和ArkTS-Dyn上下文中使用[AppStorageV2](./state-management-static/arkts-static-appstoragev2.md)的场景。在互操作场景下，[占位组件](../reference/apis-arkui/arkui-ts/ts-interop-compatible-component.md)连接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。通过建立统一数据存储机制，确保ArkTS-Sta和ArkTS-Dyn访问相同数据管理对象，实现状态和数据互通，从而在逐步迁移ArkTS-Dyn模块到ArkTS-Sta模块过程中，应用全局数据能够平滑过渡。

## 在ArkTS-Dyn模块调用AppStorageV2接口操作ArkTS-Sta模块

完整示例结构如下：

```text
project/
├── entry/          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
└── static/         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

示例如下：
- 在ArkTS-Sta模块的`static/src/main/ets/component/MainPage.ets`文件中进行数据模型声明并初始化一个key为MessageStatic的MessageModel对象。

```TypeScript
'use static'
// static/src/main/ets/component/MainPage.ets

import { ComponentV2 } from '@ohos.arkui.component';
import { AppStorageV2, ObservedV2, Trace, Local } from '@ohos.arkui.stateManagement';

@ObservedV2
export class MessageModel {
  @Trace messageId: number;
  @Trace messageContent: string;

  constructor(messageId?: number, messageContent?: string) {
    this.messageId = messageId ?? 1;
    this.messageContent = messageContent ?? 'Hello';
  }
}

@ComponentV2
export struct MainPage {
  // 使用connect在AppStorageV2中创建一个key为MessageStatic的MessageModel对象。
  @Local message: MessageModel = AppStorageV2.connect<MessageModel>(
    Type.from<MessageModel>(),
    'MessageStatic',
    () => new MessageModel(12, 'This is static message')
  )!;

  build() {
  }
}
```

- 对ArkTS-Sta模块`static/Index.ets`文件中的组件进行导出。

```TypeScript
'use static'
// static/Index.ets

export { MainPage, MessageModel } from './src/main/ets/components/MainPage';
```

- 在主模块的`entry/oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  // 从根目录导入依赖模块。
  "static": "file:../static"
}
```

- 在ArkTS-Dyn主模块的`entry/src/main/ets/pages/Index.ets`文件中进行数据存储并实现互操作方法。

```TypeScript
// entry/src/main/ets/pages/Index.ets

import { AppStorageV2 } from '@kit.ArkUI';
import { MessageModel, MainPage } from 'static';

@Entry
@ComponentV2
export struct Index {
  // 声明一个MessageModel对象。
  @Local message: MessageModel = new MessageModel();

  build() {
    Column() {
      Divider()
      Text('以下为ArkTS-Dyn内容').fontSize(20)

      Button(`dynamic connect`)
        .onClick(() => {
          // 需要待ArkTS-Sta中注册绑定互操作后ArkTS-Dyn才能实现互操作。
          // 在ArkTS-Dyn中，使用connect在AppStorageV2中创建一个key为MessageDynamic的MessageModel对象。
          this.message = AppStorageV2.connect(
            MessageModel,
            'MessageDynamic',
            () => new MessageModel(11, 'this is dynamic message')
          )!;
        })

      Button(`get value from static`)
        .onClick(() => {
          // 在ArkTS-Dyn中，读取ArkTS-Sta中存储的key为MessageStatic的MessageModel对象。
          let message = AppStorageV2.connect(
            MessageModel,
            'MessageStatic',
            () => new MessageModel());
        })

      Button(`get all keys`)
        .onClick(() => {
          // 在ArkTS-Dyn中，获取ArkTS-Sta和ArkTS-Dyn中所存储的所有key。
          let keys = AppStorageV2.keys();
        })

      Button('remove key: MessageStatic')
        .onClick(() => {
          // 在ArkTS-Dyn中，删除ArkTS-Sta所存储的key。
          AppStorageV2.remove('MessageStatic');
        })

      Button('reconnect key: MessageStatic')
        .onClick(() => {
          // 当ArkTS-Dyn和ArkTS-Sta中都没有存储key为MessageStatic的MessageModel对象时，会在ArkTS-Dyn模块创建一个key为MessageStatic的MessageModel对象。
          this.message = AppStorageV2.connect(
            MessageModel,
            'MessageStatic',
            () => new MessageModel(1212, 'this is dynamic reconnect message')
          )!;
        })

      // 注册绑定互操作并调用ArkTS-Sta模块组件，初始化一个ArkTS-Sta对象。
      MainPage()
    }
  }
}
```

## ArkTS-Dyn和ArkTS-Sta的PersistenceV2不支持互操作

ArkTS-Sta和ArkTS-Dyn的[PersistenceV2](state-management-static/arkts-static-new-persistencev2.md)由于序列化反序列化差异，不支持互操作。如果有场景必须在ArkTS-Dyn模块使用ArkTS-Sta模块的PersistenceV2或在ArkTS-Sta模块使用ArkTS-Dyn模块的PersistenceV2，从API version 22开始，可以通过在ArkTS-Sta模块或ArkTS-Dyn模块提供自定义对外接口封装PersistenceV2来实现相互使用。

**在ArkTS-Dyn模块调用ArkTS-Sta模块提供的自定义接口**

完整示例结构如下：

```text
project/
├── entry/          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
└── static/         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

- 在ArkTS-Sta子模块的`static/src/main/ets/component/MainPage.ets`文件中进行接口实现。

```TypeScript
'use static'
// static/src/main/ets/components/MainPage.ets

import { ObservedV2, Trace } from '@ohos.arkui.stateManagement';
import { PersistenceV2 } from '@ohos.arkui.stateManagement';

@ObservedV2
class User {
  userId: int = 1;
  userName: string = 'Join';
  isUser: boolean = false;

  constructor(userId?: int, userName?: string, isUser?: boolean) {
    this.userName = userName ?? 'default';
    this.userId = userId ?? 1;
    this.isUser = isUser ?? false;
  }

  public toJson(): jsonx.JsonElement {
    const root = new jsonx.JsonElement();
    // 存储id。
    const userIdEle = new jsonx.JsonElement();
    userIdEle.setInteger(this.userId);
    root.setElement("userId", userIdEle);

    // 存储name。
    const userNameEle = new jsonx.JsonElement();
    userNameEle.setString(this.userName);
    root.setElement("userName", userNameEle);

    // 存储isUser。
    const isUserEle = new jsonx.JsonElement();
    isUserEle.setBoolean(this.isUser);
    root.setElement("isUser", isUserEle);

    return root;
  }

  public fromJson(json: jsonx.JsonElement): void {
    this.userName = json.getElement("userName").asString();
    this.userId = json.getElement("userId").asInteger();
    this.isUser = json.getElement("isUser").asBoolean();
  }

  public getName(): string {
    return this.userName;
  }
}

// 接受序列化失败的回调。
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

const toJsonUser = (user: User) => {
  return user.toJson();
}

const fromJsonUser = (json: jsonx.JsonElement): User => {
  let user = new User();
  user.fromJson(json);
  return user;
}

// 在ArkTS-Sta模块声明并实现connect接口。
export function connectInStatic(key: string): User | undefined {
  let user = PersistenceV2.connect(
    Type.from<User>(),
    key,
    toJsonUser,
    fromJsonUser,
    (): User => { return new User() }
  );
  return user;
}

// 在ArkTS-Sta模块声明并实现save接口。
export function saveInStatic(key: string): void {
  PersistenceV2.save(key);
}

// 在ArkTS-Sta模块声明并实现remove接口。
export function removeInStatic(key: string): void {
  PersistenceV2.remove(key);
}
```

- 对ArkTS-Sta子模块`static/Index.ets`文件中的接口进行导出。

```TypeScript
// static/Index.ets

export { connectInStatic, saveInStatic, removeInStatic } from './src/main/ets/components/MainPage';
```

- 在子模块的`entry/oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  // 从根目录导入依赖模块。
  "static": "file:../static"
}
```

- 在ArkTS-Dyn模块的`entry/src/main/ets/pages/Index.ets`文件中调用ArkTS-Sta模块的自定义接口。

```TypeScript
'use static'
// entry/src/main/ets/pages/Index.ets

import { PersistenceV2 } from '@kit.ArkUI';
import { connectInStatic, saveInStatic, removeInStatic } from 'static';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Divider()
      Text('This is ArkTS-Dyn part').fontSize(20)

      Button('static connect')
        .onClick(() => {
          // 在ArkTS-Dyn模块调用ArkTS-Sta模块的自定义connect接口。
          let person = connectInStatic('static_key_user');
        })

      Button('static save')
        .onClick(() => {
          // 在ArkTS-Dyn模块调用ArkTS-Sta模块的自定义save接口。
          saveInStatic('static_key_user');
        })

      Button('static remove')
        .onClick(() => {
          // 在ArkTS-Dyn模块调用ArkTS-Sta模块的自定义remove接口。
          removeInStatic('static_key_user');
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#ffeeaaff')
  }
}
```