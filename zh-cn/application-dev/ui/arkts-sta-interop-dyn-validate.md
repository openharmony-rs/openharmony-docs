# ArkTS-Sta与ArkTS-Dyn状态管理V1V2混用互操作校验规格

## 概述
在ArkTS-Sta与ArkTS-Dyn互操作中，增加状态管理V1V2混用时的编译校验规格，解决兼容性问题并保障应用稳定性和数据可靠性。

## 混用校验规格
互操作时，状态管理V1V2混用的校验规格如下：
- 互操作时，不允许V1的任何this变量向V2传递数据；可以先通过[状态管理V1互操作](arkts-sta-interop-dyn-statemanager-v1.md)由V1向V1传递数据，再通过[状态管理V1V2混用](state-management/arkts-v1-v2-mixusage.md)由V1向V2传递数据。
- 互操作时，不允许V2的任何this变量向V1的状态变量传递数据；可以先通过[状态管理V2互操作](arkts-sta-interop-dyn-storages-v2.md)由V2向V2传递数据，再通过[状态管理V1V2混用](state-management/arkts-v1-v2-mixusage.md)由V2向V1传递数据。
- 互操作时，允许V2的所有this变量向V1的非状态变量传递数据。<br>

## 开发场景
### 父组件向子组件传递数据
下表展示此场景的校验规格，行代表父组件变量类型，列代表子组件变量类型。<br>
| 子组件变量类型（此列） | V2非状态变量 | V2状态变量 |
| -------- | -------- | -------- |
| V1非状态变量 | 允许 | 允许 |
| V1状态变量 | 禁止 | 禁止 |

| 子组件变量类型（此列） | V1非状态变量 | V1状态变量 |
| -------- | -------- | -------- |
| V2非状态变量 | 禁止 | 禁止 |
| V2状态变量 | 禁止 | 禁止 |

其中：<br>
V1的装饰器包括：\@State、\@Prop、\@Link、\@ObjectLink、\@Provide、\@Consume、\@StorageProp、\@StorageLink、\@LocalStorageProp、\@LocalStorageLink；<br>
V2的装饰器包括：\@Local、\@Param、\@Provider、\@Consumer、\@Event。

### 对象实例化
1、禁止V2的任何变量由\@Observed装饰的class初始化；<br>
2、禁止V1的任何变量由\@ObservedV2装饰的class初始化。

在ArkTS-Dyn中调用ArkTS-Sta时，V2的状态/非状态变量向V1的状态变量传递数据的示例如下。<br>
父组件：
```ts
import { MainPage、Info } from 'library';
@Entry
@ComponentV2
struct Index {
  // 若ArkTS-Dyn中V2的非状态变量由ArkTS-Sta中@Observed装饰的class实例化，编译做报错处理
  s1: Info = new Info('HELLO');
  // 若ArkTS-Dyn中V2的状态变量由ArkTS-Sta中@Observed装饰的class实例化，编译做报错处理
  @Local s2: Info = new Info('HELLO');

  message1: string = 'Parent';
  @Local message2: string = 'Parent';

  build() {
    Column(undefined) {
      Text('ArkTS-Dyn调用ArkTS-Sta').fontSize(40);
      // 互操作时，父组件V2的状态/非状态变量向子组件V1的状态变量传值，编译都做报错处理
      MainPage({message: this.message1, message22: this.message2});
    }
  }
}
```
子组件：
```ts
'use static'
import { Text, Column, Component, Row, ComponentV2 } from '@ohos.arkui.component';
import { State, Link, Prop, Provide, Consume, Observed } from '@ohos.arkui.stateManagement';
@Component
export struct MainPage {
  @State message: string = 'Child';
  @State message22: string = 'Child';
  build() {
    Row() {
      Column() {
        Text(this.message).fontSize(30);
        Text(this.message22).fontSize(30);
      }
    }
  }
}

@Observed
export class Info {
  private info: string = 'hello';

  constructor(info: string) {
    this.info = info;
  }
}
```