# enableCompatibleObservedV2ForStatic\<T\> (ArkTS-Sta)

调用enableCompatibleObservedV2ForStatic和enableCompatibleObservedV2ForDynamic方法，实现@ObservedV2自定义组件在互操作调用场景中的UI刷新。

>**说明：**
>
> 本模块仅适用于ArkTS-Sta。
>
>本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## enableCompatibleObservedV2ForStatic\<T\>

enableCompatibleObservedV2ForStatic\<T\>(value: T): T

在ArkTS-Sta中引用ArkTS-Dyn中使用@ObservedV2和@Trace修饰的类。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 22

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|value    | T    |是   | 在ArkTS-Dyn中@ObservedV2修饰的class。    |

**返回值：**

| 类型   | 说明                  |
| ------ | --------------------- |
| T      | 返回当前组件。          |

**示例：**

ArkTS-Dyn示例：
```typescript
// har1_1/src/main/ets/components/MainPage.ets
@ObservedV2
export class ObservedV2ForStatic {
  @Trace name: string = '';
  @Trace age: number []= [];
  constructor(name: string, age: number[]) {
    this.name = name;
    this.age = age;
  }
}
```
在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
      'har1_1': 'file:../har1_1'
  }
  ```

ArkTS-Sta示例：
```typescript
'use static'
// entry/src/main/ets/pages/Index.ets

import { enableCompatibleObservedV2ForStatic } from '@ohos.arkui.component';
import { ObservedV2ForStatic } from 'har1_1';
@Entry
@ComponentV2
struct Index {
  this.person = new ObservedV2ForStatic("张三", [23,24,25]);
  aboutToAppear(){
    enableCompatibleObservedV2ForStatic(this.person);
  }
  build() {
    Column() {
      Text(`年龄: ${this.person.age}` )
      Button('更新年龄')
        .onClick(() => {
          this.person.age++; // 触发UI刷新
        })
    }
  }
}
```
## enableCompatibleObservedV2ForDynamic\<T\>

enableCompatibleObservedV2ForDynamic\<T\>(value: T): T

在ArkTS-Dyn中引用ArkTS-Sta中使用@ObservedV2和@Trace修饰的类。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 22

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|value    | T    |是   | ArkTS-Sta@ObservedV2修饰的class。    |

**返回值：**

| 类型   | 说明                  |
| ------ | --------------------- |
| T      | 返回当前组件。 |

**示例：**

ArkTS-Dyn示例：
```typescript
// entry/src/main/ets/pages/Index.ets
import {setEnableCompatibleObservedV2ForDynamic,ObservedV2ForStatic } from 'har1_2';
@ComponentV2
export struct MainPage {
  person4: ObservedV2ForStatic = new ObservedV2ForStatic("我是", 9);
  aboutToAppear(){
    setEnableCompatibleObservedV2ForDynamic(this.person4);
  }
  build() {
    Row() {
      Column() {
        Text(`姓名: ${this.person4.name}`)
        Text(`年龄: ${this.person4.age}`)
        Button("增加年龄")
          .onClick(() => {
            this.person4.age++; // 触发UI刷新
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

ArkTS-Sta示例：
```typescript
'use static'
// har1_2/src/main/ets/components/MainPage.ets

import { enableCompatibleObservedV2ForDynamic } from '@ohos.arkui.component';
import { ObservedV2, Trace } from '@ohos.arkui.stateManagement';

export function setEnableCompatibleObservedV2ForDynamic(T: Object){
  enableCompatibleObservedV2ForDynamic(T);
}

@ObservedV2
export class ObservedV2ForStatic {
  @Trace name: string = '';
  @Trace age: number = 0;
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```
在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
      'har1_2': 'file:../har1_2'
  }
  ```