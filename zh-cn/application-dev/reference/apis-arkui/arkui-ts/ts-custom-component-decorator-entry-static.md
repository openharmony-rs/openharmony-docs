# @Entry：页面入口

\@Entry装饰的自定义组件将作为UI页面的入口。在单个UI页面中，仅允许存在一个由@Entry装饰的自定义组件作为页面的入口。开发指南参考：[\@Component装饰器：自定义组件](../../../ui/state-management-static/arkts-static-create-component.md#entry)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 本装饰器首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数**

| 名称   | 类型   | 只读 | 可选 | 说明                                                           |
| ------ | ------ | ---- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| routeName | string | 否 | 是 | 表示作为[命名路由](../../../ui/arkts-routing.md#命名路由)页面的名字。 |
| storage | string | 否 | 是 | 返回[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例对象的函数名。 |
| useSharedStorage | boolean | 否 | 是 | 是否使用UIContext.getSharedLocalStorage()接口返回的共享的[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例对象，默认值false。<br>true表示使用共享的[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例对象。<br>false表示不使用共享的[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例对象。 |

**示例**

```ts
'use static'

import { Component, Entry, Column, Text, LocalStorage } from '@kit.ArkUI';

const myStorage: () => LocalStorage = () => new LocalStorage();

@Entry({routeName: 'myPage', storage: 'myStorage', useSharedStorage: false})
@Component
struct MyComponent {
  build() {
    Column() {
      Text('Hello world!')
    }
  }
}
```