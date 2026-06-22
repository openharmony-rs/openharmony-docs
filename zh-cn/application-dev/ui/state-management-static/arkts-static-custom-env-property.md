# \@CustomEnv：自定义环境变量 (ArkTS-Sta)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @songyanhong-->
<!--Adviser: @zhang_yixin13-->

[\@CustomEnv](../../reference/apis-arkui/arkui-ts/ts-state-management-custom-env-static.md#customenv)可用于获取自定义环境变量。开发者可通过WithEnv组件的.customEnv接口设置自定义环境变量，在子组件中通过\@CustomEnv装饰器读取相同[CustomEnvKey\<S\>](../../reference/apis-arkui/arkui-ts/ts-state-management-custom-env-static.md#customenvkeys)对应的变量值。该机制实现了组件树间的数据透传，使父子组件能基于环境变量进行联动，同时保持代码解耦。

>**说明：**
>
> 从API版本26.0.0开始，[\@CustomEnv](../../reference/apis-arkui/arkui-ts/ts-state-management-custom-env-static.md#customenv)支持在[\@Component](./arkts-static-create-component.md)和[\@ComponentV2](./arkts-static-componentv2.md)中使用。

## 概述
[\@CustomEnv](../../reference/apis-arkui/arkui-ts/ts-state-management-custom-env-static.md#customenv)是响应式自定义环境变量装饰器，其功能包括：
- 根据入参读取相应的自定义环境变量信息，详情见[\@CustomEnv使用方法](#customenv使用方法)。
- 自定义环境变量改变时，通知\@CustomEnv装饰的变量更新，并触发\@CustomEnv关联组件刷新，以实现界面内容的更新。
- 使用\@CustomEnv装饰的变量具有只读特性，不允许开发者在初始化后对\@CustomEnv装饰的变量做整体赋值。如需更新该变量的值，必须通过父组件的WithEnv组件配合`.customEnv()`方法进行更新。尝试对\@CustomEnv变量赋值将导致编译错误。

开发者可以使用\@CustomEnv装饰器，并传入一个自定义的key，来声明响应式环境变量。示例如下：

```ts
'use static'

import { Entry, ComponentV2, Column, CustomEnv, CustomEnvKey } from '@kit.ArkUI';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  @CustomEnv('custom') varName: string = 'default value';

  build() {
    Column() {
    }
  }
}
```

其中：
- `custom`：开发者自定义的环境变量key，类型为[CustomEnvKey\<S\>](../../reference/apis-arkui/arkui-ts/ts-state-management-custom-env-static.md#customenvkeys)，自定义环境变量key需要为全局常量，否则会编译报错。
- `'custom'`：\@CustomEnv装饰器的入参。
- `varName`：装饰的变量名。
- `'default value'`：变量的默认值，当未找到对应的WithEnv组件提供的值时使用。

## \@CustomEnv使用方法

### 装饰器说明

| \@CustomEnv装饰器 | 说明 |
| ------------------- | ------------------------------------------------------------ |
| 装饰器参数 | [\@CustomEnv](../../reference/apis-arkui/arkui-ts/ts-state-management-custom-env-static.md#customenv)装饰器的入参必须为[CustomEnvKey\<S\>](../../reference/apis-arkui/arkui-ts/ts-state-management-custom-env-static.md#customenvkeys)实例同名的字符串。 |
| 可装饰的变量类型 | class、string、number、boolean、enum等基本类型以及Array、Date、Map、Set等内置类型。支持null、undefined以及联合类型。 |
| 装饰变量的初始值 | 必须本地初始化，不允许外部传入初始化。 |

### 变量传递

| 传递规则       | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| 从父组件初始化 | \@CustomEnv装饰的变量仅允许本地初始化，无法从外部传入初始化。    |
| \@CustomEnv装饰的变量初始化  | 初始化\@CustomEnv装饰的变量时，会优先向上递归查找父组件中通过WithEnv.customEnv注入的相同key的值；若找到，则使用该注入值，否则使用本地初始化值。|

### 观察变化

当点击更新按钮导致\@Local装饰的变量值发生变化时，WithEnv组件中通过.customEnv()方法设置的值也会通知\@CustomEnv，此时子组件中\@CustomEnv装饰的变量将更新最新值并触发界面重新渲染，实现了完整的响应式更新链路。

```ts
'use static'

import { Entry, ComponentV2, Text, Column, Button, CustomEnv, Local, CustomEnvKey } from '@kit.ArkUI';
import { WithEnv, WithEnvAttribute } from '@ohos.arkui.WithEnv';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  @Local customMsg: string = 'Hello';

  build() {
    Column() {
      Button('update')
        .onClick(() => {
          this.customMsg = 'Hello World';
        })

      WithEnv() {
        // 有WithEnv组件，显示this.customMessage的默认值'Hello'，点击Button后值更新为'Hello World'。
        Child()
      }.customEnv(custom, this.customMsg)

    }
  }
}

@ComponentV2
struct Child {
  @CustomEnv('custom') customMessage: string = 'default content';

  build() {
    Column() {
      Text(`Child: ${this.customMessage}`);
    }
  }
}
```

## \@CustomEnv和\@Env能力对比
\@CustomEnv和[\@Env](./arkts-static-new-env.md)都是环境变量相关，具体能力对比见下表。

| 能力 | \@CustomEnv | \@Env|
| ------------------ | ------------------ | ------------------ |
|起始API version|从API版本26.0.0开始支持。|从API version 22开始支持。|
|支持参数|开发者自定义的CustomEnvKey类型对象。|[SystemProperties的枚举值](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties)。<br/>API版本26.0.0之后支持[SystemProperties](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemproperties)和[SystemEnvKey\<T\>](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemenvkey)类型参数。|
|使用形式|\@CustomEnv为装饰器，可声明在\@Component或\@ComponentV2中，开发者通过WithEnv的customEnv接口设置的环境变量|\@Env为装饰器，可声明在\@Component或\@ComponentV2中，直接读取系统环境变量。<br/>API版本26.0.0之后，开发者可通过WithEnv的env接口设置[SystemEnvKey\<T\>](../../reference/apis-arkui/arkui-ts/ts-state-management-env-static.md#systemenvkey)类型参数的系统环境变量。|
|值的来源|初始化给定默认值或通过WithEnv组件的.customEnv()方法设置。|通过WithEnv的env接口设置的系统环境变量（支持查询系统环境变量后补充文档）。|
|是否有响应式能力|有，当WithEnv设置的值变化时，会通知\@CustomEnv装饰的变量更新，并通知关联组件刷新。|有，当系统环境变量变化时，会通知\@Env装饰的变量更新，并通知关联组件刷新。|

## 限制条件

- \@CustomEnv仅支持在\@Component和\@ComponentV2中使用，否则会有编译时报错。

  ```ts
  'use static'

  import { Entry, Component, Column, Text, CustomEnv, CustomEnvKey } from '@kit.ArkUI';

  const custom = CustomEnvKey.create<string>();

  class Info {
    @CustomEnv('custom') varName: string = 'defaultValue'; // 错误用法，编译时报错
  }

  @Entry
  @Component
  struct Index {
    @CustomEnv('custom') varName: string = 'defaultValue'; // 正确用法

   build() {
     Column() {
       Text(`this is @CustomEnv sample`)
     }
   }
  }
  ```

- \@CustomEnv的入参不支持复杂类型，必须是`string`类型，必须是通过[CustomEnvKey\<S\>](../../reference/apis-arkui/arkui-ts/ts-state-management-custom-env-static.md#customenvkeys)的[create\<T\>](../../reference/apis-arkui/arkui-ts/ts-state-management-custom-env-static.md#createt)方法创建的全局常量同名的字符串，否则会编译报错。
  ```ts
  'use static'

  import { Entry, Component, ComponentV2, Column, Text, Button, CustomEnv, State, UIUtils, ObjectLink, CustomEnvKey } from '@kit.ArkUI';
  
  @ObservedV2
  class CustomEnvValue {
    @Trace id: number = 123;
    @Trace userName: string = 'admin';
  }

  const custom = CustomEnvKey.create<string>();
  const customNum = CustomEnvKey.create<number>();
  const customBool = CustomEnvKey.create<boolean>();
  const customObj = CustomEnvKey.create<CustomEnvValue>();
  const customUnion = CustomEnvKey.create<string | number>();

  @Entry
  @Component
  struct Index {
    @CustomEnv('custom') customVarName: string = 'hello world'; // 正确用法
    @CustomEnv('customNum') customNumVarName: number = 1; // 正确用法
    @CustomEnv('customBool') customBoolVarName: boolean = true; // 正确用法
    @CustomEnv('customObj') customObjVarName: CustomEnvValue = new CustomEnvValue(); // 正确用法
    @CustomEnv('customUnion') customUnion: string | number = 'hello world'; // 正确用法
    cus: CustomEnvKey<string> = CustomEnvKey.create<string>();
    @CustomEnv(this.cus) customThisName: string = 'hello world';  // 错误用法，@CustomEnv的key不是全局常量，会编译报错
    @CustomEnv('invalidKey') customInvalidName: string = 'hello world';  // 错误用法，@CustomEnv的key不是CustomEnvKey实例名的字符串，会编译报错

    build() {
      Column() {
        Text(`this is @CustomEnv page`)
      }
    }
  }
  ```

- \@CustomEnv装饰的变量为只读属性，不允许开发者进行赋值操作，否则会有编译时报错。

  ```ts
  'use static'

  import { Entry, Component, Column, Text, Button, CustomEnv, CustomEnvKey } from '@kit.ArkUI';

  const custom = CustomEnvKey.create<string>();

  @Entry
  @Component
  struct Index {
    @CustomEnv('custom') varName: string = 'defaultValue'; // 正确用法

    build() {
      Column() {
        Text(`varName: ${this.varName}`)
          .fontSize(20)

        Button('change breakpoint')
          .onClick(() => {
            this.varName = 'new value'; // 错误用法，编译时报错
          })
      }
    }
  }
  ```

- \@CustomEnv装饰的变量不能通过父组件传参进行初始化。若在组件实例化时以参数形式赋值，编译阶段会进行拦截并报错。

  ```ts
  'use static'

  import { Entry, ComponentV2, CustomEnv, Text, Column, Button, CustomEnvKey } from '@kit.ArkUI';

  const custom = CustomEnvKey.create<string>();

  @Entry
  @ComponentV2
  struct PageOne {
    @CustomEnv('custom') defaultMessage: string = 'Hello';

    build() {
      Column() {
        Child({firstValue: this.defaultMessage}) // 错误用法，编译时报错
      }
    }
  }

  @ComponentV2
  struct Child {
    @CustomEnv('custom') firstValue: string = 'world';

    build() {
      Column() {
        Text(this.firstValue)
      }
    }
  }
  ```

- \@CustomEnv装饰器只能单独使用，不能和其他V1V2状态变量装饰器联用，否则会有编译时报错。

  ```ts
  'use static'

  import { Entry, Component, Column, Text, CustomEnv, State, Require, Local, ComponentV2, Watch, CustomEnvKey } from '@kit.ArkUI';

  const custom = CustomEnvKey.create<string>();

  @Entry
  @Component
  struct Index {
    @CustomEnv('custom') varName: string = 'defaultValue'; // 正确用法
    @State @CustomEnv('custom') varName2: string = 'defaultValue'; // 错误写法，编译时报错
    @Require @CustomEnv('custom') varName3: string = 'defaultValue'; // 错误写法，编译时报错
    @CustomEnv('custom') @Watch('observedFunction')  varName4: string = 'defaultValue'; // 错误用法，编译时报错

    observedFunction() {
      console.info(`xxx`);
    }

    build() {
      Column() {
        Text(`this is @CustomEnv sample`)
      }
    }
  }

  @ComponentV2
  struct IndexV2 {
    @Local @CustomEnv('custom') varName5: string = 'defaultValue'; // 错误写法，编译时报错

    build() {
      Column() {
        Text(`this is @CustomEnv sample`)
      }
    }
  }
  ```

- \@CustomEnv不会向上查找\@Component/\@ComponentV2中相同Key的\@CustomEnv设置的值。

  ```ts
  'use static'

  import { CustomEnv, ComponentV2, Component, Entry, Local, Text, Column, Button, CustomEnvKey } from '@kit.ArkUI';
  import { WithEnv, WithEnvAttribute } from '@ohos.arkui.WithEnv';

  const custom = CustomEnvKey.create<string>();

  @Entry
  @ComponentV2
  struct Index {
    @Local customMsg: string = 'Hello';
    @CustomEnv('custom') customMessage: string = 'parent';

    build() {
      Column() {
        Child()
      }
    }
  }

  @ComponentV2
  struct Child {
    @CustomEnv('custom') customMessage: string = 'child';

    build() {
      Column() {
        // 此时的value为child，不会获取父组件Index中相同key的@CustomEnv装饰变量的值
        Text(`Child: ${this.customMessage}`);
      }
    }
  }
  ```

- \@CustomEnv修饰的成员变量类型需要与\@CustomEnvKey类型中的泛型保持一致。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent, CustomEnv, CustomEnvKey } from '@kit.ArkUI';

const custom = CustomEnvKey.create<double>;

@Entry
@Component
struct Index {
  @CustomEnv('custom') message: string = 'test'; // 错误写法，编译时报错

  build() {
    Column(undefined) {

    }
  }
}
```

## \@CustomEnv初始化流程

\@CustomEnv变量初始化遵循以下流程：

1. 查找WithEnv组件中是否存在对应的key：
   - 判断当前父组件是否为WithEnv组件。
   - 若不是，则继续向上查找，直至根节点。
   - 若找到对应key的WithEnv组件，则获取组件提供的环境变量值，赋值给\@CustomEnv装饰的变量。
2. 使用\@CustomEnv声明的变量初始值：
   - 若未找到对应的key的WithEnv组件，则使用\@CustomEnv装饰变量的本地初始值。

流程图如下。

![image](../figures/customenv-flow.png)

## 使用场景

### 支持自定义key和value

新增的状态管理装饰器\@CustomEnv支持自定义key配置，并且可以指定变量的初始值。语法格式为：`@CustomEnv('custom') customVarName: string = 'hello world'`。其中'custom'为开发者自定义的环境变量key，'hello world'为该变量的初始值。

```ts
'use static'

import { CustomEnv, ComponentV2, Entry, Text, Column, CustomEnvKey } from '@kit.ArkUI';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  // 实现了定义的key及value
  @CustomEnv('custom') customVarName: string = 'hello world';

  build() {
    Column() {
      Text(this.customVarName)
    }
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-9.png)

### \@CustomEnv支持多种数据类型

\@CustomEnv支持简单类型和复杂类型的变量声明。简单类型包括string、number、boolean、enum等；复杂类型包括class、Object等对象类型。

```ts
'use static'

import {
  Entry, ComponentV2, Column, CustomEnv, Text, CustomEnvKey, ObservedV2, Trace
} from '@kit.ArkUI';

@ObservedV2
class CustomEnvValue {
  @Trace id: number = 123;
  @Trace userName: string = 'admin';
}

const customStr = CustomEnvKey.create<string>();
const customNum = CustomEnvKey.create<number>();
const customBool = CustomEnvKey.create<boolean>();
const customObj = CustomEnvKey.create<CustomEnvValue>();

@Entry
@ComponentV2
struct Index {
  @CustomEnv('customStr') customStrVarName: string = 'hello world';
  @CustomEnv('customNum') customNumVarName: number = 1;
  @CustomEnv('customBool') customBoolVarName: boolean = true;
  @CustomEnv('customObj') customObjVarName: CustomEnvValue = new CustomEnvValue();

  build() {
    Column() {
      Text(`customStrVarName type is ${typeof this.customStrVarName}`)
      Text(`customNumVarName type is ${typeof this.customNumVarName}`)
      Text(`customBoolVarName type is ${typeof this.customBoolVarName}`)
      Text(`customObjVarName type is ${typeof this.customObjVarName}`)
    }
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-11.png)

### \@CustomEnv支持默认初始值

当子组件中使用\@CustomEnv装饰的变量向上查找环境变量值但未找到匹配的WithEnv组件时，该变量将使用声明时指定的初始值作为默认值。

```ts
'use static'

import {
  Entry, ComponentV2, Column, Text, Local, CustomEnvKey, CustomEnv
} from '@kit.ArkUI'; 

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  @Local tempProp: string = 'Hello';

  build() {
    Column() {
        Child()
    }
  }
}

@ComponentV2
struct Child {
  @CustomEnv('custom') customProp: string = 'default content';

  build() {
    Column() {
      // 此时Text中的内容显示为: Child: default content
      Text(`Child: ${this.customProp}`);
    }
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-10.png)

### 环境变量查找遵循就近原则

子组件中使用\@CustomEnv装饰的变量在获取环境变量值时，会向上遍历组件树查找对应的WithEnv组件，并优先选择距离当前子组件最近的WithEnv组件所提供的值。当最近的WithEnv组件未定义该key时，会继续向更外层查找，直至找到匹配值，如果未找到匹配值，则使用本地默认值。

以下示例中，Child组件中声明\@CustomEnv(custom)将被离它最近的内层WithEnv赋值，最终值为'the nearest WithEnv'。

```ts
'use static'

import {
  Entry, ComponentV2, Column, Text, CustomEnv, Local, CustomEnvKey
} from '@kit.ArkUI';
import { WithEnv, WithEnvAttribute } from '@ohos.arkui.WithEnv';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      // 就近原则体现
      WithEnv() {
        // 优先查找该层WithEnv
        WithEnv() {
          // 就近原则，显示'the nearest WithEnv'
          Child()
        }.customEnv(custom, 'the nearest WithEnv')
      }.customEnv(custom, 'outer WithEnv')
    }
  }
}

@ComponentV2
struct Child {
  @CustomEnv('custom') customMessage: string = 'default content';

  build() {
    Column() {
      Text(`Child: ${this.customMessage}`);
    }
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-12.png)

### 响应式更新能力

当点击更新按钮导致\@Local装饰的变量值发生变化时，WithEnv组件中通过.customEnv()方法设置的值也会通知\@CustomEnv，此时子组件中\@CustomEnv装饰的变量将更新最新值并触发界面重新渲染，实现了完整的响应式更新链路。

```ts
'use static'

import {
  Entry, Component, ComponentV2, Column, Require, Param, ObjectLink, SystemProperties, Text, Button, Row, Local, CustomEnvKey, CustomEnv
} from '@kit.ArkUI';
import { WithEnv, WithEnvAttribute } from '@ohos.arkui.WithEnv';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  @Local customMsg: string = 'Hello';

  build() {
    Column() {
      Button('update')
        .onClick(() => {
          this.customMsg = 'Hello World';
        })

      WithEnv() {
        // 有WithEnv组件，显示this.customMessage的默认值'Hello'，点击Button后值更新为'Hello World'。
        Child()
      }.customEnv(custom, this.customMsg)

    }
  }
}

@ComponentV2
struct Child {
  @CustomEnv('custom') customMessage: string = 'default content';

  build() {
    Column() {
      Text(`Child: ${this.customMessage}`);
    }
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-1.gif)

### \@Monitor和addMonitor监听\@CustomEnv装饰变量变化

在ArkTS-Sta中，\@CustomEnv不支持与状态变量、[\@Watch](./arkts-static-watch.md)等其他装饰器连用，可以在\@Component里使用[addMonitor](./arkts-static-new-addmonitor-clearmonitor.md)监听变量变化。

```ts
'use static'

import { Entry, Row, Component, Column, Text, Button, CustomEnv, CustomEnvKey, UIUtils, IMonitorDecoratedVariable, IMonitor, State } from '@kit.ArkUI';
import { WithEnv, WithEnvAttribute } from '@ohos.arkui.WithEnv';

const custom = CustomEnvKey.create<string>();

@Entry
@Component
struct Test {
  @State defaultMessage: string = 'the nearest WithEnv';

  build() {
    Row() {
      Column() {
        Text(`Index message is : ${this.defaultMessage}`)
        WithEnv() {
          Child()
        }.customEnv(custom, this.defaultMessage)

        Button('change')
          .onClick(() => {
            this.defaultMessage = 'Hello World';
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

@Component
struct Child {
  @CustomEnv('custom') message: string = 'Hello';
  valueMonitor?: IMonitorDecoratedVariable;

  onChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[CustomEnv] value ${path} has changed from ${m.value<string>(path)?.before} to ${m.value<string>(path)?.now}`);
    })
  }

  aboutToAppear() {
    this.valueMonitor = UIUtils.addMonitor(() => this.message, this.onChange);
  }

  build() {
    Column() {
      Text(`Child message is : ${this.message}`)
    }
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-15.gif)

在\@ComponentV2中，可通过\@Monitor监听\@CustomEnv装饰变量的变化。需要注意的是，仅当\@CustomEnv装饰的变量被整体赋值时才会触发\@Monitor监听回调，其内部属性的变化不会触发回调。

```ts
'use static'

import { Entry, Row, ComponentV2, Column, Text, Button, CustomEnv, Local, IMonitor, Monitor, CustomEnvKey } from '@kit.ArkUI';
import { WithEnv, WithEnvAttribute } from '@ohos.arkui.WithEnv';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct MonitorTest {
  @Local message: string = 'Hello';

  build() {
    Row() {
      Column() {
        Button('change message').onClick(() => {
          this.message = 'Hello World';
        })
        WithEnv() {
          Child()
        }.customEnv(custom, this.message)
      }
      .width('100%')
    }
    .height('100%')
  }
}

@ComponentV2
struct Child {
  @CustomEnv('custom') message: string = 'CustomEnv';

  @Monitor(['message'])
  onStrChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[CustomEnv] value ${path} has changed from ${m.value<string>(path)?.before} to ${m.value<string>(path)?.now}`);
    })
  }

  build() {
    Column() {
      Text(`message:${this.message}`)
        .fontSize(50)
    }
  }
}
```

在上面的示例中：

点击'change message'更改message的值，将会触发\@Monitor装饰器的回调并输出对应日志。

运行效果图如下。

![image](../figures/custom-env-static-8.gif)


### \@CustomEnv支持组件冻结

当\@CustomEnv所在组件处于非激活状态的时候，WithEnv对应的key发生改变时，将不会通知非激活状态下\@Monitor装饰器的回调，当非激活状态的\@CustomEnv回到激活状态时，将会通知\@Monitor装饰器的回调。

需要注意的是：在首次渲染的时候，Tab只会创建当前正在显示的TabContent，当切换所有TabContent后，TabContent才会被全部创建。

```ts
'use static'

import { Button, ClickEvent, Column, ComponentV2, Entry, FontWeight, ForEach, IMonitor, Local, Monitor, Param, Repeat, Row, TabContent, Tabs, Text, CustomEnvKey, CustomEnv } from '@kit.ArkUI';
import { WithEnv, WithEnvAttribute } from '@ohos.arkui.WithEnv';

const custom = CustomEnvKey.create<number>();

@Entry
@ComponentV2
struct TabContentTest {
  @Local message: number = 0;
  @Local data: number[] = [0, 1, 2, 3, 4];

  build() {
    Row() {
      Column() {
        Button('change message').onClick(() => {
          this.message++;
        })
        WithEnv() {
          Tabs() {
            Repeat<number>(this.data).each(ri => {
              TabContent() {
                FreezeChild({ index: ri.item })
              }.tabBar(`tab${ri.item}`)
            }).key((item: number) => item.toString()).virtualScroll({ disableVirtualScroll: true })
          }
        }.customEnv(custom, this.message)
      }
      .width('100%')
    }
    .height('100%')
  }
}

@ComponentV2
struct FreezeChild {
  @CustomEnv('custom') message: number = 0;
  @Param index: number = 0;
  // 仅处于激活状态的TabContent下的FreezeChild可以立刻触发@Monitor
  @Monitor(['message']) onMessageUpdated(mon: IMonitor) {
    console.info(`FreezeChild message callback func ${this.message}, index: ${this.index}`);
  }

  build() {
    Text('message' + `${this.message}, index: ${this.index}`)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}
```

在上面的示例中：

1. 点击'change message'更改message的值，当前正在显示的TabContent组件中的\@Monitor中注册的方法onMessageUpdated被触发。

2. 点击TabBar中的'tab1'切换到另外的TabContent，TabContent状态由inactive变为active，对应的\@Monitor中注册的方法onMessageUpdated被触发。 

3. 再次点击'change message'更改message的值，仅当前显示的TabContent子组件中的\@Monitor中注册的方法onMessageUpdated被触发。其他inactive的TabContent组件不会触发\@Monitor。

运行效果图如下。

![image](../figures/custom-env-static-2.gif)

### 装饰Array类型变量

当装饰的对象是Array时，可以通过调用Array的接口`push`, `pop`, `shift`, `unshift`, `splice`, `copyWithin`, `fill`, `reverse`, `sort`更新Array中的数据。

```ts
'use static'

import { Entry, Row, ComponentV2, Column, Text, Button, CustomEnv, ForEach, CustomEnvKey } from '@kit.ArkUI';

class Fruit {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }
}

const custom = CustomEnvKey.create<Fruit[]>();

@Entry
@ComponentV2
struct Index {
  @CustomEnv('custom') fruits: Fruit[] = [new Fruit('apple'), new Fruit('banana')]; // 使用@CustomEnv装饰Array类型变量

  build() {
    Row() {
      Column() {
        ForEach(this.fruits, (item: Fruit) => {
          Text(`${item.name}`)
            .fontSize(20)
            .margin(10)
        })
        // 新增数组元素，触发UI刷新
        Button('Push element')
          .onClick(() => {
            this.fruits.push(new Fruit('cherry'));
          })
          .width(300)
          .margin(10)
        // 翻转数组元素，触发UI刷新
        Button('Reverse array')
          .onClick(() => {
            this.fruits.reverse();
          })
          .width(300)
          .margin(10)
        // 使用同一元素填充数组，触发UI刷新
        Button('Fill array')
          .onClick(() => {
            this.fruits.fill(new Fruit('apple'));
          })
          .width(300)
          .margin(10)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-4.gif)

### 装饰Date类型变量

当装饰的对象是Date时，可通过调用Date的接口`setFullYear`，`setMonth`，`setDate`，`setHours`，`setMinutes`，`setSeconds`，`setMilliseconds`，`setTime`，`setUTCFullYear`，`setUTCMonth`，`setUTCDate`，`setUTCHours`，`setUTCMinutes`，`setUTCSeconds`，`setUTCMilliseconds`更新Date的属性。

```ts
'use static'

import { Entry, Row, ComponentV2, Column, Text, Button, CustomEnv, CustomEnvKey, DatePicker } from '@kit.ArkUI';

const custom = CustomEnvKey.create<Date>();

@Entry
@ComponentV2
struct DatePickerExample {
  @CustomEnv('custom') selectedDate: Date = new Date('2021-08-08'); // 使用@CustomEnv装饰Date类型变量

  build() {
    Row() {
      Column() {
        // 调用Date的setFullYear接口修改年份，触发UI刷新
        Button('increase the year by 1')
          .onClick(() => {
            this.selectedDate.setFullYear(this.selectedDate.getFullYear() + 1);
          })
          .margin(10)
          .width(300)
        // 调用Date的setMonth接口修改月份，触发UI刷新
        Button('increase the month by 1')
          .onClick(() => {
            this.selectedDate.setMonth(this.selectedDate.getMonth() + 1);
          })
          .margin(10)
          .width(300)
        // 调用Date的setDate接口修改日期，触发UI刷新
        Button('increase the day by 1')
          .onClick(() => {
            this.selectedDate.setDate(this.selectedDate.getDate() + 1);
          })
          .margin(10)
          .width(300)
        DatePicker({
          start: new Date('1970-1-1'),
          end: new Date('2100-1-1'),
          selected: this.selectedDate
        }).margin(20)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-5.gif)

### 装饰Map类型变量

当装饰的对象是Map时，可以通过调用Map的接口`set`, `clear`, `delete`更新Map中的数据。

```ts
'use static'

import { Entry, Row, ComponentV2, Column, Text, Button, CustomEnv, CustomEnvKey, ForEach } from '@kit.ArkUI';

const custom = CustomEnvKey.create<Map<string, number>>();

@Entry
@ComponentV2
struct MapSample {
  @CustomEnv('custom') fruits: Map<string, number> = new Map<string, number>([['apple', 1], ['banana', 2]]); // 使用@CustomEnv装饰Map类型变量

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.fruits.entries()), (item: [string, number]) => {
          Text(`key: ${item[0]}, value: ${item[1]}`)
            .fontSize(20)
            .margin(10)
        })
        // 新增键值对，触发UI刷新
        Button('Set entry cherry')
          .onClick(() => {
            this.fruits.set('cherry', 3);
          })
          .width(300)
          .margin(10)
        // 更新键值对，触发UI刷新
        Button('Update entry apple')
          .onClick(() => {
            this.fruits.set('apple', 4);
          })
          .width(300)
          .margin(10)
        // 删除键值对，触发UI刷新
        Button('Delete entry apple')
          .onClick(() => {
            this.fruits.delete('apple');
          })
          .width(300)
          .margin(10)
        // 清空Map，触发UI刷新
        Button('Clear map')
          .onClick(() => {
            this.fruits.clear();
          })
          .width(300)
          .margin(10)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-6.gif)

### 装饰Set类型变量

当装饰的对象是Set时，可以通过调用Set的接口`add`, `clear`, `delete`更新Set中的数据。

```ts
'use static'

import { Entry, Row, ComponentV2, Column, Text, Button, CustomEnv, Local, ForEach, CustomEnvKey } from '@kit.ArkUI';

const custom = CustomEnvKey.create<Set<string>>();

@Entry
@ComponentV2
struct SetSample {
  @CustomEnv('custom') fruits: Set<string> = new Set<string>(['apple', 'banana']); // 使用@CustomEnv装饰Set类型变量

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.fruits.entries()), (item: [string, string]) => {
          Text(`${item[0]}`)
            .fontSize(20)
            .margin(10)
        })
        // 新增元素，触发UI刷新
        Button('Add element')
          .onClick(() => {
            this.fruits.add('cherry');
          })
          .width(300)
          .margin(10)
        // 删除元素，触发UI刷新
        Button('Delete element apple')
          .onClick(() => {
            this.fruits.delete('apple');
          })
          .width(300)
          .margin(10)
        // 清空Set，触发UI刷新
        Button('Clear set')
          .onClick(() => {
            this.fruits.clear();
          })
          .width(300)
          .margin(10)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-7.gif)

### \@CustomEnv支持状态管理V1/V2装饰器混用

\@CustomEnv可以在\@Component和\@ComponentV2中使用，其遵循[V1V2混用的基本规则](./arkts-static-v1-v2-mixusage.md)。\@CustomEnv装饰的变量传递给V1时，遵循V1状态管理装饰器不能接收[\@ObservedV2](./arkts-static-new-observedV2-and-trace.md)装饰的class的规则。\@CustomEnv装饰的变量传递给V2时，遵循V2只有[\@Param](./arkts-static-new-param.md)可以接收外部变量的规则。


- \@CustomEnv装饰的变量传递给V1时，遵循V1状态变量装饰器不能接收\@ObservedV2装饰的class的规则。
```ts
'use static'

import { Entry, Row, ComponentV2, Component, Column, Text, Button, CustomEnv, ObservedV2, Trace, Require, PropRef, CustomEnvKey } from '@kit.ArkUI';

@ObservedV2
class CustomValue {
  @Trace defaultVal: string = 'hello';
} 

const custom = CustomEnvKey.create<string>();
const customObj = CustomEnvKey.create<CustomValue>();

@Entry
@ComponentV2
struct PageOne {
  @CustomEnv('custom') defaultMessage: string = 'parent Value';
  @CustomEnv('customObj') defaultObj: CustomValue = new CustomValue();

  build() {
    Column() {
      Text(`Parent Value is :${this.defaultMessage}`)
      Child({ message: this.defaultMessage }) // 正确用法
      // Child({ customMessage: this.defaultObj }) // 错误用法，编译报错。
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct Child {
  @Require @PropRef message: string;
  // @PropRef customMessage: CustomValue; //  错误用法，V1状态变量装饰器装饰的类型不能是ObservedV2装饰的class。

  build() {
    Column() {
      Text(`Child value is :${this.message}`)
    }
    .height('100%')
    .width('100%')
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-13.png)

- \@CustomEnv装饰的变量传递给V2时，遵循V2只有\@Param可以接收外部变量的规则。
```ts
'use static'

import { Entry, Row, ComponentV2, Component, Column, Text, Button, CustomEnv, ObservedV2, Trace, Require, CustomEnvKey, Param } from '@kit.ArkUI';

@ObservedV2
class CustomValue {
  @Trace defaultVal: string = 'hello';
}

const custom = CustomEnvKey.create<CustomValue>();

@Entry
@Component
struct PageOne {
  @CustomEnv('custom') defaultMessage: CustomValue = new CustomValue();

  build() {
    Column() {
      Text(this.defaultMessage.defaultVal)
      Button('update')
        .onClick(() => {
          this.defaultMessage.defaultVal = 'hello world';
        })
      Child({ message: this.defaultMessage })
    }
    .height('100%')
    .width('100%')
  }
}

@ComponentV2
struct Child {
  @Require @Param message: CustomValue;

  build() {
    Column() {
      Text(`Child Value is : ${this.message.defaultVal}`)
    }
    .height('100%')
    .width('100%')
  }
}
```

运行效果图如下。

![image](../figures/custom-env-static-14.gif)
