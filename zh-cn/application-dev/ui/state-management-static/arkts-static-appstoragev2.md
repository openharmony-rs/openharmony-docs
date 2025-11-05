# AppStorageV2: 应用全局的UI状态存储

为了增强状态管理框架对应用全局UI状态变量存储的能力，开发者可以使用AppStorageV2存储应用全局UI状态变量数据。

从API version 20开始AppStorageV2提供状态变量在应用级全局共享的能力。开发者可以通过connect绑定同一个key，进行跨ability的数据共享。

## 概述

AppStorageV2是在应用UI启动时会被创建的单例。目的是提供应用状态数据的中心存储，这些状态数据在应用级别都是可访问的。AppStorageV2将在应用运行过程中保留其数据。数据通过唯一的键字符串值访问。

>**说明：**
>
>- 在静态语言上下文中使用时，需要导入AppStorageV2。
>- AppStorageV2可以修改connect的返回值，实现与UI组件的同步。
>- AppStorageV2支持应用的[主线程](../../application-models/thread-model-stage.md)内多个UIAbility实例间的状态共享。
>- [AppStorage](./arkts-static-appstorage.md)与AppStorageV2之间的数据互不共享。

```ts
import { AppStorageV2 } from '@ohos.arkui.stateManagement';
```

## 使用说明

以下接口详细描述请参考API文档：[AppStorageV2](../../../application-dev/reference/apis-arkui/js-apis-stateManagement-static.md#appstoragev2)。

### connect

创建或获取存储的数据。

>**说明：**
>
>- 当主动传入key时，使用第三个参数作为默认构造器；否则使用第二个参数作为默认构造器。
>
>- 如果数据已经存储在AppStorageV2中，可省略默认构造器，获取存储的数据；否则必须指定默认构造器，不指定将导致应用异常。
>
>- key相同，connect类型不同的数据会导致应用异常，开发者需要确保类型匹配。
>
>- 建议key使用有意义的值，可由字母、数字和下划线组成，长度不超过255字符，避免使用非法字符或空字符。

### remove

删除指定key的存储数据。

>**说明：**
>
>删除AppStorageV2中不存在的key会报警告。

### keys

返回所有AppStorageV2中的key。


## 使用限制

1. 只支持class类型。

2. 需要配合UI使用（UI线程），不能在其他线程使用。

3. 不支持非built-in类型，如PixelMap、NativePointer、ArrayList等Native类型。

4. 不支持存储基本类型，如string、number、boolean等。注意：不支持存储基本类型意味着connect接口传入的类型不能是基本类型，但connect传入的class中可以包含基本类型。

## 使用场景

### 使用AppStorageV2

AppStorageV2使用connect接口即可实现对AppStorageV2中数据的修改和同步，如果修改的数据被@Trace装饰，该数据的修改会同步更新UI。需要注意的是，使用remove接口只会将数据从AppStorageV2中删除，不影响组件中已创建的数据，详见以下示例代码。

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent, ComponentV2, Divider } from '@ohos.arkui.component';
import { State, Link, LocalStorage, LocalStorageLink, Local, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
import { PersistentStorage } from '@ohos.arkui.stateManagement';
import { AppStorageV2 } from '@ohos.arkui.stateManagement';

@ObservedV2
class Message {
  @Trace userID: number;
  userName: string;

  constructor(userID?: number, userName?: string) {
    this.userID = userID ?? 1;
    this.userName = userName ?? 'Jack';
  }
}

const IMessageType = Type.of(new Message());

@Entry
@ComponentV2
struct Index {
  // 使用connect在AppStorageV2中创建一个ttype为Message的Type的对象
  // 修改connect的返回值即可同步回AppStorageV2
  @Local message: Message = AppStorageV2.connect<Message>(IMessageType, () => new Message())!;

  build() {
    Column() {
      // 修改@Trace装饰的类属性，UI能同步刷新
      Button(`Index userID: ${this.message.userID}`)
        .onClick((e: ClickEvent) => {
          this.message.userID += 1;
        })
      // 修改非@Trace装饰的类属性，UI不会同步刷新，但修改的类属性已同步回AppStorageV2
      Button(`Index userName: ${this.message.userName}`)
        .onClick((e: ClickEvent) => {
          this.message.userName += 'suf';
        })
      // remove keyOrType IMessageType, 会从AppStorageV2中删除keyOrType为Message的Type的对象
      // remove之后，修改父组件的userId，子组件能同步变化，因为remove只是从AppStorageV2删除，不会影响组件中已存在的数据
      Button('remove keyOrType: IMessageType')
        .onClick((e: ClickEvent) => {
          AppStorageV2.remove(IMessageType);
        })
      // connect ttype IMessageType, 会从AppStorageV2中添加ttype为Message的Type的对象
      // remove之后，重新添加，修改父子组件的userID，可以发现数据已经不同步，子组件重新connect之后，数据一致
      Button('connect ttype: IMessageType')
        .onClick((e: ClickEvent) => {
          this.message = AppStorageV2.connect<Message>(IMessageType, () => new Message(5, 'Rose'))!;
        })
      Divider()
      Child()
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct Child {
  // 使用connect在AppStorageV2中取出一个ttype为Message的Type的对象，该对象已在父组件中创建
  @Local message: Message = AppStorageV2.connect<Message>(IMessageType, () => new Message())!;
  @Local name: string = this.message.userName;

  build() {
    Column() {
      // 修改@Trace装饰的类属性，UI同步刷新，父组件能感知该变化
      Button(`Child userID: ${this.message.userID}`)
        .onClick((e: ClickEvent) => {
          this.message.userID += 5;
        })
      // 修改父组件中的userName属性，点击name可以同步父组件的类属性修改
      Button(`Child name: ${this.name}`)
        .onClick((e: ClickEvent) => {
          this.name = this.message.userName;
        })
      // remove keyOrType IMessageType，会从AppStorageV2中删除keyOrType为Message的Type的对象
      Button('remove keyOrType: IMessageType')
        .onClick((e: ClickEvent) => {
          AppStorageV2.remove(IMessageType);
        })
      // connect ttype IMessageType，会从AppStorageV2中添加ttype为Message的Type的对象
      Button('connect ttype: IMessageType')
        .onClick((e: ClickEvent) => {
          this.message = AppStorageV2.connect<Message>(IMessageType, () => new Message(10, 'Lucy'))!;
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### AppStorageV2应用于两页面场景

数据页面（Sample.ets）。
```ts
'use static'

import { ObservedV2, Trace } from '@ohos.arkui.stateManagement';

@ObservedV2
export class Sample {
  @Trace p1: number = 0;
  p2: number = 10;
}

export const ISampleType = Type.of(new Sample());
```

页面1（Page1.ets）。
```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent, ComponentV2, Divider, NavPathStack, Builder, ButtonType, NavigationMode, NavDestination, FontWeight, Navigation, NavPathInfo } from '@ohos.arkui.component';
import { State, Link, LocalStorage, LocalStorageLink, Local, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
import { PersistentStorage } from '@ohos.arkui.stateManagement';
import { AppStorageV2 } from '@ohos.arkui.stateManagement';
import { Sample, ISampleType } from './Sample';
import { Page2 } from './Page2';

@Entry
@ComponentV2
struct Page1 {
  // 在AppStorageV2中创建一个ttype为Sample的Type的键值对（如果存在，则返回AppStorageV2中对应的数据），并且和prop关联
  @Local prop: Sample = AppStorageV2.connect<Sample>(ISampleType, () => new Sample())!;
  pageStack: NavPathStack = new NavPathStack();

  @Builder
  PageBuilder(name: string, param: Object | null | undefined){
    if (name == 'Page2') {
      Page2()
    }
  }

  build() {
    Navigation(this.pageStack) {
      Column() {
        Button('Go to page2')
          .onClick((e: ClickEvent) => {
            let info: NavPathInfo = new NavPathInfo('Page2', new Object());
            this.pageStack.pushPath(info, true);
          })

        Button('Page1 connect key Sample')
          .onClick((e: ClickEvent) => {
            // 在AppStorageV2中创建一个key为Sample的键值对（如果存在，则返回AppStorageV2中对应的数据），并且和prop关联
            this.prop = AppStorageV2.connect<Sample>(ISampleType, 'Sample', () => new Sample())!;
          })

        Button('Page1 connect key Samplex')
          .onClick((e: ClickEvent) => {
            // 在AppStorageV2中创建一个key为Samplex的键值对（如果存在，则返回AppStorageV2中对应的数据），并且和prop关联
            this.prop = AppStorageV2.connect<Sample>(ISampleType, 'Samplex', () => new Sample())!;
          })

        Button('Page1 remove keyOrType ISampleType')
          .onClick((e: ClickEvent) => {
            // 从AppStorageV2中删除后，AppStorageV2中不存在ttype为Sample的Type的对象，但prop关联的对象并没有被删除，所以点击下方的Text组件修改prop.p1，其值仍然会变化。
            AppStorageV2.remove(ISampleType);
          })

        Text(`Page1 add 1 to prop.p1: ${this.prop.p1}`)
          .fontSize(30)
          .onClick((e: ClickEvent) => {
            this.prop.p1++;
          })

        Text(`Page1 add 1 to prop.p2: ${this.prop.p2}`)
          .fontSize(30)
          .onClick((e: ClickEvent) => {
            // 页面不刷新，但p2的值已改变
            this.prop.p2++;
          })

        // 获取当前AppStorageV2里面的所有key
        Text(`all keys in AppStorage: ${AppStorageV2.keys()}`)
          .onClick((e: ClickEvent) => {
            console.info(`${AppStorageV2.keys()}`)
          })
          .fontSize(30)
      }
    }.navDestination(this.PageBuilder)
  }
}
```

页面2（Page2.ets）。
```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent, ComponentV2, Divider, NavPathStack, Builder, ButtonType, NavigationMode, NavDestination, FontWeight, Navigation, NavPathInfo, NavDestinationContext } from '@ohos.arkui.component';
import { State, Link, LocalStorage, LocalStorageLink, Local, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
import { PersistentStorage } from '@ohos.arkui.stateManagement';
import { AppStorageV2 } from '@ohos.arkui.stateManagement';
import { Sample, ISampleType } from './Sample'

@Builder
export function Page2Builder() {
  Page2()
}

@ComponentV2
export struct Page2 {
  // 在AppStorageV2中创建一个ttype为Sample的Type的键值对（如果存在，则返回AppStorageV2中对应的数据），并且和prop关联
  @Local prop: Sample = AppStorageV2.connect<Sample>(ISampleType, () => new Sample())!;
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Button('Page2 connect key Sample')
          .onClick((e: ClickEvent) => {
            // 在AppStorageV2中创建一个key为Sample的键值对（如果存在，则返回AppStorageV2中对应的数据），并且和prop关联
            this.prop = AppStorageV2.connect<Sample>(ISampleType, 'Sample', () => new Sample())!;
          })

        Text(`Page2 add 1 to prop.p1: ${this.prop.p1}`)
          .fontSize(30)
          .onClick((e: ClickEvent) => {
            this.prop.p1++;
          })

        Text(`Page2 add 1 to prop.p2: ${this.prop.p2}`)
          .fontSize(30)
          .onClick((e: ClickEvent) => {
            // 页面不刷新，但p2的值已改变
            this.prop.p2++;
          })

      }
    }
  }
}
```
使用[Navigation](../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md)时，需要先添加配置系统路由表文件src/main/resources/base/profile/route_map.json，再替换pageSourceFile为Page2页面的路径，最后在module.json5中添加："routerMap": "$profile:route_map"。
```json
{
  "routerMap": [
    {
      "name": "Page2",
      "pageSourceFile": "src/main/ets/pages/Page2.ets",
      "buildFunction": "Page2Builder",
      "data": {
        "description" : "AppStorageV2 example"
      }
    }
  ]
}
```