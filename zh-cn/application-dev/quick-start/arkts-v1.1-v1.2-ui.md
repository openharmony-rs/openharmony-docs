# ArkTS1.2UI迁移规则

受ArkTS1.2静态类型系统的影响，ArkUI的语法与接口需适配变化。本指南列出ArkTS1.2中所有变化的UI语法与接口，提供修改代码的建议。

## 使用UI接口前需要导入

**规则：** `arkui-modular-interface`

**级别：** error

在ArkTS1.2中，使用UI接口前必须先导入。

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('UI import')
    }
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  Component,
  Column,
  Text,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('UI import')
    }
  }
}
```

## 不支持`this.value!!`形式的双向绑定

**规则：** `arkui-no-!!-bidirectional-data-binding`

**级别：** error

### 系统组件参数双向绑定

在ArkTS1.2中，不支持`this.value!!`形式的双向绑定。对于系统组件参数的双向绑定，应改为`$$(this.value)`的形式。

**ArkTS1.1**

```typescript
@Entry
@ComponentV2
struct Index {
  @Local text: string = '';

  build() {
    Column() {
      Text(this.text)
      TextInput({text: this.text!!})
        .width(300)
    }.width('100%').height('100%')
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  ComponentV2,
  Local,
  Column,
  Text,
  TextInput,
  $$,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @Local text: string = '';

  build() {
    Column() {
      Text(this.text)
      TextInput({text: $$(this.text)})
        .width(300)
    }.width('100%').height('100%')
  }
}
```

### 自定义组件间双向绑定

在ArkTS1.2中，对于自定义组件间的双向绑定，要将原来的双向绑定语法糖展开。

**ArkTS1.1**

```typescript
@Entry
@ComponentV2
struct Index {
  @Local value: number = 0;

  build() {
    Column() {
      Text(`${this.value}`)
      Button(`change value`).onClick((e: ClickEvent) => {
        this.value++;
      })
      Star({ value: this.value!! })
    }
  }
}

@ComponentV2
struct Star {
  @Param value: number = 0;
  @Event $value: (val: number) => void = (val: number) => {};

  build() {
    Column() {
      Text(`${this.value}`)
      Button(`change value `).onClick((e: ClickEvent) => {
        this.$value(10);
      })
    }
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  ComponentV2,
  Local,
  Column,
  Text,
  Button,
  ClickEvent,
  Param,
  Event,
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local value: number = 0;

  build() {
    Column() {
      Text(`${this.value}`)
      Button(`change value`).onClick((e: ClickEvent) => {
        this.value++;
      })
      // 在ArkTS1.2中，展开双向绑定语法糖
      Star({
        value: this.value,
        $value: (value: number) => {
            this.value = value;
        }
      })
    }
  }
}

@ComponentV2
struct Star {
  @Param value: number = 0;
  @Event $value: (val: number) => void = (val: number) => {};

  build() {
    Column() {
      Text(`${this.value}`)
      Button(`change value `).onClick((e: ClickEvent) => {
        this.$value(10);
      })
    }
  }
}
```

## 不支持`$$this.value`形式的双向绑定

**规则：** `arkui-no-$$-bidirectional-data-binding`

**级别：** error

在ArkTS1.2中，不支持`$$this.value`形式的双向绑定，应改为`$$(this.value)`的形式。

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  @State text: string = '';

  build() {
    Column() {
      Text(this.text)
      TextInput({text: $$this.text})
        .width(300)
    }.width('100%').height('100%')
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  Component,
  State,
  Column,
  Text,
  TextInput,
  $$,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State text: string = '';

  build() {
    Column() {
      Text(this.text)
      TextInput({text: $$(this.text)})
        .width(300)
    }.width('100%').height('100%')
  }
}
```

## 不支持`$value`形式的数据绑定

**规则：** `arkui-link-decorator-passing`

**级别：** error

在ArkTS1.2中，不支持`$value`形式的数据绑定，要变更为`this.value`的形式。

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  @State count: number = 0;

  build() {
    Column() {
      MyCounter({
        count: $count
      })
      Text(`Double: ${this.count * 2}`)
    }
    .padding(60)
    .height('100%')
    .width('100%')
  }
}

@Component
struct MyCounter {
  @Link count: number;

  build() {
    Row() {
      Text(`${this.count}`)
      Blank()
      Button('+', { type: ButtonType.Circle }).onClick((e: ClickEvent) => {this.count++;})
      Button('-', { type: ButtonType.Circle }).onClick((e: ClickEvent) => {this.count--;})
    }
    .width('100%')
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  Component,
  State,
  Column,
  Text,
  Link,
  Row,
  Blank,
  Button,
  ButtonType,
  ClickEvent,
  Circle,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State count: number = 0;

  build() {
    Column() {
      MyCounter({
        count: this.count
      })
      Text(`Double: ${this.count * 2}`)
    }
    .padding(60)
    .height('100%')
    .width('100%')
  }
}

@Component
struct MyCounter {
  @Link count: number;

  build() {
    Row() {
      Text(`${this.count}`)
      Blank()
      Button('+', { type: ButtonType.Circle }).onClick((e: ClickEvent) => {this.count++;})
      Button('-', { type: ButtonType.Circle }).onClick((e: ClickEvent) => {this.count--;})
    }
    .width('100%')
  }
}
```

## 不支持`@Extend`装饰器

**规则：** `arkui-no-extend-decorator`

**级别：** error

在ArkTS1.2中，不支持`@Extend`装饰器，使用`@Extend`装饰的函数需要进行修改。

**ArkTS1.1**

```typescript
@Extend(Text)
function fancy(fontSize: number) {
  .fontColor(Color.Red)
  .fontSize(fontSize)
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('Test').fancy(50)
    }
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  TextAttribute,
  Color,
  Entry,
  Component,
  Column,
  Text,
} from '@kit.ArkUI';

// 使用`@Extend`装饰的函数需要参照下列代码进行修改
function fancy(this: TextAttribute, fontSize: number): this {
    this.fontColor(Color.Red);
    this.fontSize(fontSize);
    return this;
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('Test').fancy(50.0)
    }
  }
}
```

## `@AnimatableExtend`装饰器使用方式变更

**规则：** `arkui-animatableextend-use-receiver`

**级别：** error

在ArkTS1.2中，使用`@AnimatableExtend`装饰器装饰的函数需要进行修改。

**ArkTS1.1**

```typescript
@AnimatableExtend(Text)
function animatableWidth(width: number) {
  .width(width)
}

@Entry
@Component
struct Index {
  @State textWidth: number = 80;

  build() {
    Column() {
      Text('AnimatableProperty')
        .animatableWidth(this.textWidth)
        .animation({ duration: 2000, curve: Curve.Ease })
      Button("Play")
        .onClick((e: ClickEvent) => {
          this.textWidth = this.textWidth == 80 ? 160 : 80;
        })
    }.width("100%")
    .padding(10)
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  AnimatableExtend,
  TextAttribute,
  Entry,
  Component,
  State,
  Column,
  Text,
  Curve,
  Button,
  ClickEvent,
} from '@kit.ArkUI';

// 使用`@AnimatableExtend`装饰器装饰的函数需要参照下列代码进行修改
@AnimatableExtend
function animatableWidth(this: TextAttribute, width: number): this {
    this.width(width);
    return this;
}

@Entry
@Component
struct Index {
  @State textWidth: number = 80.0;

  build() {
    Column() {
      Text('AnimatableProperty')
        .animatableWidth(this.textWidth)
        .animation({ duration: 2000.0, curve: Curve.Ease })
      Button("Play")
        .onClick((e: ClickEvent) => {
          this.textWidth = this.textWidth == 80.0 ? 160.0 : 80.0;
        })
    }.width("100%")
    .padding(10.0)
  }
}
```

## 不支持`@Styles`装饰器

**规则：** `arkui-no-styles-decorator`

**级别：** error

在ArkTS1.2中，不支持`@Styles`装饰器。使用`@Styles`装饰器装饰的函数需要进行修改。

### `@Styles`装饰器装饰全局函数

**ArkTS1.1**

```typescript
@Styles
function cardStyle() {
  .backgroundColor(Color.Red)
  .borderRadius(8)
  .padding(8)
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('Card')
    }
    .cardStyle()
    .width('100%')
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  CommonMethod,
  Color,
  Entry,
  Component,
  Column,
  Text,
  applyStyles,
} from '@kit.ArkUI';

// 使用`@Styles`装饰器装饰的函数需要参照下列代码进行修改
function cardStyle(instance: CommonMethod): void {
  instance.backgroundColor(Color.Red);
  instance.borderRadius(8.0);
  instance.padding(8.0);
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('Card')
    }
    .applyStyles(cardStyle)
    .width('100%')
  }
}
```

### `@Styles`装饰器装饰成员函数

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  @Styles
  cardStyles() {
    .backgroundColor(Color.Blue)
    .borderRadius(8)
    .padding(8)
  }

  build() {
    Column() {
      Text('Card')
    }
    .cardStyles()
    .width('100%')
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  Component, 
  CommonMethod,
  Color,
  Column,
  Text,
  CustomStyles,
  applyStyles,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // 使用`@Styles`装饰器装饰的函数需要参照下列代码进行修改
  cardStyles: CustomStyles = (instance: CommonMethod): void => {
    instance.backgroundColor(Color.Blue);
    instance.borderRadius(8.0);
    instance.padding(8.0);
  }

  build() {
    Column() {
      Text('Card')
    }
    .applyStyles(this.cardStyles)
    .width('100%')
  }
}
```

## 传递给`stateStyles`的代码块必须是箭头函数

**规则：** `arkui-statestyles-block-need-arrow-func`

**级别：** error

在ArkTS1.2中，传递给`stateStyles`的匿名代码块必须是箭头函数。

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('Button')
        .stateStyles({
          normal: {
            .backgroundColor(Color.Red)
            .borderWidth(8)
          },
          pressed: {
            .backgroundColor(Color.Green)
          }
        })
    }
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  Component,
  Column,
  CommonMethod,
  Button,
  Color,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('Button')
        .stateStyles({
          normal: (instance: CommonMethod): void => {
            instance.backgroundColor(Color.Red);
            instance.borderWidth(8.0);
          },
          pressed: (instance: CommonMethod): void => {
            instance.backgroundColor(Color.Green);
          }
        })
    }
  }
}
```

## 数据监听需要增加`@Observed`装饰器

**规则：** `arkui-data-observation`

**级别：** error

在ArkTS1.2中，被特定装饰器装饰的状态变量，如果要实现数据监听，需要为状态变量所属的类添加`@Observed`装饰器。

装饰器范围如下：

- `@State`
- `@Prop`
- `@Link`
- `@Provide`
- `@Consume`
- `@LocalStorageProp`
- `@LocalStorageLink`
- `@StorageProp`
- `@StorageLink`

**ArkTS1.1**

```typescript
class Num {
  count: number = 1;
}

@Entry
@Component
struct Index {
  @State num: Num = new Num();

  build() {
    Column() {
      Text(`${this.num.count}`)
      Button('count++')
        .onClick((e: ClickEvent) => {
          this.num.count ++;
        })
    }
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Observed,
  Entry,
  Component,
  State,
  Column,
  Text,
  Button,
  ClickEvent,
} from '@kit.ArkUI';

@Observed
class Num {
  count: number = 1;
}

@Entry
@Component
struct Index {
  @State num: Num = new Num();

  build() {
    Column() {
      Text(`${this.num.count}`)
      Button('count++')
        .onClick((e: ClickEvent) => {
          this.num.count ++;
        })
    }
  }
}
```

## `@Entry`装饰器不支持传入动态参数

**规则：** `arkui-entry-annotation`

**级别：** error

在ArkTS1.2中，`@Entry`装饰器不支持传入动态参数，只能接受基础类型的常量。若`@Entry`装饰器没有入参，则不需要进行修改。

### 参数类型为`LocalStorage`

**ArkTS1.1**

```typescript
const storage = new LocalStorage();
@Entry(storage)
@Component
struct Index {
  build() {
    Text('Hello World')
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  LocalStorage,
  Entry,
  Component,
  Text,
} from '@kit.ArkUI';

const storage = new LocalStorage();
const __get_local_storage__ = (): LocalStorage => storage;
@Entry({ storage: "__get_local_storage__" })
@Component
struct Index {
  build() {
    Text('Hello World')
  }
}
```

### 参数类型为`EntryOptions`

**ArkTS1.1**

```typescript
const storage = new LocalStorage();
@Entry({ storage: storage })
@Component
struct Index {
  build() {
    Text('Hello World')
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  LocalStorage,
  Entry,
  Component,
  Text,
} from '@kit.ArkUI';

const storage = new LocalStorage();
const __get_local_storage__ = (): LocalStorage => storage;
@Entry({ storage: "__get_local_storage__" })
@Component
struct Index {
  build() {
    Text('Hello World')
  }
}
```

## `@Provide`装饰器不支持传入联合类型的参数

**规则：** `arkui-provide-annotation`

**级别：** error

ArkTS1.2的`@Provide`装饰器不支持传入联合类型参数，仅接受基础类型常量。若`@Provide`装饰器没有入参，无需修改。

### 参数类型为`string`

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  @Provide("value")
  value: number = 0;

  build() {
    Text('Hello World')
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  Component,
  Provide,
  Text,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @Provide({ alias: "value" })
  value: number = 0;

  build() {
    Text('Hello World')
  }
}
```

### 参数类型为`ProvideOptions`

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  @Provide({ allowOverride: "value" })
  value: number = 0;

  build() {
    Text('Hello World')
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  Component,
  Provide,
  Text,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @Provide({ alias: "value", allowOverride: true })
  value: number = 0;

  build() {
    Text('Hello World')
  }
}
```

## `CustomBuilder`类型参数接收带`@Builder`装饰器的函数调用时，需要为其包裹匿名的箭头函数

**规则：** `arkui-custombuilder-passing`

**级别：** error

在ArkTS1.2中，`CustomBuilder`类型的参数接收被`@Builder`装饰器装饰的调用函数时，需用匿名箭头函数包裹。

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  @State inputValue: string = '';

  @Builder
  CustomKeyboardBuilder() {
    Text('使用自定义键盘').fontSize(100)
  }
  
  build() {
    Column() {
      TextInput({ text: this.inputValue })
        .customKeyboard(this.CustomKeyboardBuilder())
    }
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  Component,
  State,
  Builder,
  Text,
  Column,
  TextInput,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State inputValue: string = '';

  @Builder
  CustomKeyboardBuilder() {
    Text('使用自定义键盘').fontSize(100.0)
  }
  
  build() {
    Column() {
      TextInput({ text: this.inputValue })
        .customKeyboard(() => {
          this.CustomKeyboardBuilder()
        })
    }
  }
}
```

## 被`@Builder`装饰器装饰的函数的执行上下文需要在声明时确定

**规则：** `arkui-buildparam-passing`

**级别：** error

在ArkTS1.1中，回调函数的执行上下文在调用时指定。

在ArkTS1.2中，回调函数的执行上下文是函数所在的实例对象。

**ArkTS1.1**

```typescript
@Component
struct SuperComponent {
  @State value: string = 'parent';

  @Builder
  builder() {
    Text(this.value)
  }

  build() {
    Column() {
      SubComponent({
        // ArkTS1.1：this指向SubComponent
        // ArkTS1.2：this指向SuperComponent
        content: this.builder
      })
    }
  }
}

@Component
struct SubComponent {
  @Builder
  builder() {
  }

  @Require
  @BuilderParam content: () => void = this.builder;
  @State value: string = 'child';

  build() {
    Column() {
      this.content()
    }
  }
}

@Entry
@Component
struct TestBuilderParam1 {
  build() {
    Column() {
      // ArkTS1.1：执行代码后，SuperComponent组件显示的文本内容是'child'
      // ArkTS1.2：执行相同代码后，SuperComponent组件显示的文本内容是'parent'
      SuperComponent()
    }
  }
}
```

**ArkTS1.2**

在ArkTS1.2中，为实现与ArkTS1.1相同的运行效果，需改造代码，将状态变量作为回调函数的参数传递。

```typescript
'use static'
import {
  Component,
  State,
  Builder,
  Text,
  Column,
  Require,
  BuilderParam,
  Entry,
} from '@kit.ArkUI';

@Component
struct SuperComponent {
  @State value: string = 'parent';

  @Builder
  builder(value: string) {
    Text(value)
  }

  build() {
    Column() {
      SubComponent({
        content: this.builder
      })
    }
  }
}

@Component
struct SubComponent {
  @Builder
  builder() {
  }

  @Require
  @BuilderParam content: (value: string) => void = this.builder;
  @State value: string = 'child';

  build() {
    Column() {
      this.content(this.value)
    }
  }
}


@Entry
@Component
struct TestBuilderParam1 {
  build() {
    Column() {
      SuperComponent()
    }
  }
}
```

## 禁止在UI渲染过程中修改状态变量

**规则：** `arkui-no-update-in-build`

**级别：** error

在ArkTS1.2中，禁止在UI渲染过程中修改状态变量。如果在自定义组件的`build`方法中修改了状态变量，会导致编译报错。

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  @State count: number = 1;

  build() {
    // ArkTS1.1：在build方法中修改状态变量的行为仅触发告警
    // ArkTS1.2：在build方法中修改状态变量的行为会导致编译报错
    Text(`${++this.count}`)
  }
}
```

**ArkTS1.2**

在ArkTS1.2中，自定义组件的`build`方法中修改状态变量会导致编译报错，因此禁止该类行为，不提供修改建议。

## `AppStorage`中的值发生改变时会触发界面更新

**规则：** `arkui-stateful-appstorage`

**级别：** error

在ArkTS1.2中，如果在自定义组件的`build`方法中调用`AppStorage`的`get`、`has`、`keys`或`size`接口，会和组件建立依赖关系。当`AppStorage`中对应的值发生改变时，会触发界面更新。

**ArkTS1.1**

```typescript
@Entry
@Component
struct MyComponent {
  build() {
    Column() {
      Text(`${AppStorage.get('value')}`)
      Button("Button")
        .onClick(() => {
          AppStorage.set("value", 10); // AppStorage中的值发生了改变，会触发Text组件的更新
        })
    }
  }
}
```

**ArkTS1.2**

ArkTS1.2的处理方式是能力增强，因此仅提示开发者上述情况可能产生的差异，而不提供具体的修改建议。

## 不支持`@Prop`、`@StorageProp`和`@LocalStorageProp`装饰器

**规则：** `arkui-no-prop-decorator`、`arkui-no-storageprop-decorator`、`arkui-no-localstorageprop-decorator`

**级别：** error

在ArkTS1.2中，不支持`@Prop`、`@StorageProp`和`@LocalStrorageProp`装饰器，要分别用`@PropRef`、`@StoragePropRef`和`@LocalStroragePropRef`装饰器替代。

**ArkTS1.1**

```typescript
class User {
  name: string = "";
  age: number = 0;
}

@Entry
@Component
struct FatherComponent {
  @Prop user1: User = new User();
  @StorageLink("user2") user2: User = new User();
  @LocalStorageLink("user3") user3: User = new User();

  build() {
  }
}

@Component
struct ChildComponent {
  @StorageProp("user2") user2: User = new User();
  @LocalStorageProp("user3") user3: User = new User();

  build() {
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Observed,
  Entry,
  Component,
  PropRef,
  StorageLink,
  LocalStorageLink,
  StoragePropRef,
  LocalStoragePropRef,
} from '@kit.ArkUI';

class User {
  name: string = "";
  age: number = 0.0;
}

@Entry
@Component
struct FatherComponent {
  @PropRef user1: User = new User();
  @StorageLink("user2") user2: User = new User();
  @LocalStorageLink("user3") user3: User = new User();

  build() {
  }
}

@Component
struct ChildComponent {
  @StoragePropRef("user2") user2: User = new User();
  @LocalStoragePropRef("user3") user3: User = new User();

  build() {
  }
}
```

## 不支持`@LocalBuilder`装饰器

**规则：** `arkui-no-localbuilder-decorator`

**级别：** error

在ArkTS1.2中，`@LocalBuilder`装饰器和`@Builder`装饰器的作用相同，因此废弃`@LocalBuilder`装饰器，用`@Builder`装饰器替代。

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  @State label: string = 'Hello World';

  @LocalBuilder
  citeLocalBuilder(params: string) {
    Row() {
      Text(`UseStateVarByReference: ${params}`)
    }
  };

  build() {
    Column() {
      this.citeLocalBuilder(this.label)
    }
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import { Builder } from '@kit.ArkUI';

import {
  Entry,
  Component,
  State,
  Row,
  Text,
  Column,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State label: string = 'Hello World';

  @Builder
  citeLocalBuilder(params: string) {
    Row() {
      Text(`UseStateVarByReference: ${params}`)
    }
  };

  build() {
    Column() {
      this.citeLocalBuilder(this.label)
    }
  }
}
```

## 自定义组件需要加上`@CustomLayout`装饰器以获得自定义布局能力

**规则：** `arkui-custom-layout-need-add-decorator`

**级别：** error

在ArkTS1.2中，自定义组件需要组件加上`@CustomLayout`装饰器，才能获得自定义布局能力。

**ArkTS1.1**

```typescript
@Entry
@Component
struct Index {
  build() {
    Column() {
      MyComponent({ builder: ColumnChildren })
    }
  }
}

@Builder
function ColumnChildren() {
  ForEach([1, 2, 3], (index: number) => {
    Text('S' + index)
      .fontSize(30)
      .width(100)
      .height(100)
      .borderWidth(2)
      .offset({ x: 10, y: 20 } as Position)
  })
}

@Component
struct MyComponent {
  @Builder
  doNothingBuilder() {
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;
  @State startSize: number = 100;
  result: SizeResult = {
    width: 0,
    height: 0
  } as SizeResult;

  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    let startPos = 300;
    children.forEach((child) => {
      let pos = startPos - child.measureResult.height;
      child.layout({ x: pos, y: pos });
    })
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size = 100;
    children.forEach((child) => {
      let result: MeasureResult = child.measure({ minHeight: size, minWidth: size, maxWidth: size, maxHeight: size });
      size += result.width / 2;
    })
    this.result.width = 100;
    this.result.height = 400;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import { CustomLayout } from '@kit.ArkUI';

import {
  Entry,
  Component,
  Column,
  Builder,
  ForEach,
  Text,
  Position,
  BuilderParam,
  State,
  SizeResult,
  GeometryInfo,
  Layoutable,
  ConstraintSizeOptions,
  Measurable,
  MeasureResult
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      MyComponent({ builder: ColumnChildren })
    }
  }
}

@Builder
function ColumnChildren() {
  ForEach([1, 2, 3], (item: Int, index: number) => {
    Text('S' + index)
      .fontSize(30)
      .width(100)
      .height(100)
      .borderWidth(2)
      .offset({ x: 10, y: 20 } as Position)
  })
}

@Component
@CustomLayout
struct MyComponent {
  @Builder
  doNothingBuilder() {
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;
  @State startSize: number = 100;
  result: SizeResult = {
    width: 0,
    height: 0
  } as SizeResult;

  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    let startPos = 300;
    children.forEach((child) => {
      let pos = startPos - child.measureResult.height;
      child.layout({ x: pos, y: pos });
    })
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size = 100;
    children.forEach((child) => {
      let result: MeasureResult = child.measure({ minHeight: size, minWidth: size, maxWidth: size, maxHeight: size });
      size += result.width / 2;
    })
    this.result.width = 100;
    this.result.height = 400;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```

## `Repeat`禁用默认的懒加载

**规则：** `arkui-repeat-disable-default-virtualscroll`

**级别：** error

在ArkTS1.1中，`Repate`默认渲染全部子组件。

在ArkTS1.2中，`Repeat`默认支持懒加载，如果想要渲染全部子组件，需要禁用默认的懒加载。

**ArkTS1.1**

```typescript
@Entry
@ComponentV2
struct Index {
  @Local dataArr: Array<string> = [];

  aboutToAppear(): void {
    for (let i = 0; i < 50; i++) {
      this.dataArr.push(`data_${i}`);
    }
  }

  build() {
    Column() {
      List() {
        Repeat<string>(this.dataArr)
          .each((ri: RepeatItem<string>) => {
            ListItem() {
              Text('each_' + ri.item).fontSize(30)
            }
          })
      }
      .cachedCount(2)
      .height('70%')
      .border({ width: 1 })
    }
  }
}
```

**ArkTS1.2**

```typescript
'use static'
import {
  Entry,
  ComponentV2,
  Local,
  Column,
  List,
  Repeat,
  RepeatItem,
  ListItem,
  Text,
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local dataArr: Array<string> = [];

  aboutToAppear(): void {
    for (let i: number = 0.0; i < 50.0; i++) {
      this.dataArr.push(`data_${i}`);
    }
  }

  build() {
    Column() {
      List() {
        Repeat<string>(this.dataArr)
          .each((ri: RepeatItem<string>) => {
            ListItem() {
              Text('each_' + ri.item).fontSize(30.0)
            }
          })
          .virtualScroll({ disableVirtualScroll: true })
      }
      .cachedCount(2.0)
      .height('70%')
      .border({ width: 1.0 })
    }
  }
}
```