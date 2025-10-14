# 从ArkTS-Dyn到ArkTS-Sta的UI语法规则适配

受ArkTS-Sta静态类型系统的影响，ArkUI的语法与接口需适配变化。本指南列出ArkTS-Sta中所有变化的UI语法与接口，提供代码适配的建议。

## 使用UI接口前需要导入

**规则：** `arkui-modular-interface`

**规则解释：**

在ArkTS-Sta中，使用UI接口前必须先导入，否则会违反该规则导致报错，非UI接口不会有报错信息。

**变更原因：**

在ArkTS-Sta中，使用UI接口时如果不导入，编译会报错。

**适配建议：**

使用UI接口前先导入。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

### 系统组件参数双向绑定

**规则解释：**

在ArkTS-Sta中，不支持`this.value!!`形式的双向绑定。对于系统组件参数的双向绑定，应改为`$$(this.value)`的形式。

**变更原因：**

在ArkTS-Sta中，不支持`this.value!!`形式的双向绑定。

**适配建议：**

对于系统组件参数的双向绑定，应改为`$$(this.value)`的形式。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，对于自定义组件间的双向绑定，要将原来的双向绑定语法糖展开。

**变更原因：**

在ArkTS-Dyn中，对于自定义组件间的双向绑定，编译过程中会将双向绑定语法糖展开。在ArkTS-Sta中则不会。

**适配建议：**

对于自定义组件间的双向绑定，要将原来的双向绑定语法糖展开。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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
      // 在ArkTS-Sta中，展开双向绑定语法糖
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

**规则解释：**

在ArkTS-Sta中，不支持`$$this.value`形式的双向绑定，应改为`$$(this.value)`的形式。

**变更原因：**

在ArkTS-Sta中，不支持`$$this.value`形式的双向绑定。

**适配建议：**

把`$$this.value`改为`$$(this.value)`的形式。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，不支持`$value`形式的数据绑定，要变更为`this.value`的形式。

**变更原因：**

在ArkTS-Sta中，不支持`$value`形式的数据绑定。

**适配建议：**

把`$value`变更为`this.value`的形式。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，不支持`@Extend`装饰器，使用`@Extend`装饰的函数需要进行修改。

**变更原因：**

在ArkTS-Sta中，`@Extend`装饰器被废弃。

**适配建议：**

使用`@Extend`装饰的函数需要按照示例进行修改。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，使用`@AnimatableExtend`装饰器装饰的函数需要进行修改。

**变更原因：**

受ArkTS-Sta静态类型系统的影响，使用`@AnimatableExtend`装饰器装饰的函数需要进行修改。

**适配建议：**

使用`@AnimatableExtend`装饰器装饰的函数需要按照示例进行修改。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，不支持`@Styles`装饰器。使用`@Styles`装饰器装饰的函数需要进行修改。

**变更原因：**

在ArkTS-Sta中，`@Styles`装饰器被废弃。

**适配建议：**

使用`@Styles`装饰器装饰的函数需要按照示例进行修改。

### `@Styles`装饰器装饰全局函数

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，传递给`stateStyles`的匿名代码块必须是箭头函数。

**变更原因：**

在ArkTS-Dyn中，传递给`stateStyles`的匿名代码块不符合标准语法。

**适配建议：**

把传递给给`stateStyles`的匿名代码块改为箭头函数。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，被特定装饰器装饰的状态变量，如果要实现数据监听，需要为状态变量所属的类添加`@Observed`装饰器。

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

**变更原因：**

受ArkTS-Sta静态类型系统的影响，如果要实现数据监听，需要为状态变量所属的类添加`@Observed`装饰器。

**适配建议：**

为状态变量所属的类添加`@Observed`装饰器。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，`@Entry`装饰器不支持传入动态参数，只能接受基础类型的常量。若`@Entry`装饰器没有入参，则不需要进行修改。

**变更原因：**

在ArkTS-Sta中，`@Entry`装饰器不支持传入动态参数，只能接受基础类型的常量。

**适配建议：**

把`@Entry`装饰器的入参改为基础类型的常量。

### 参数类型为`LocalStorage`

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

ArkTS-Sta的`@Provide`装饰器不支持传入联合类型参数，仅接受基础类型常量。若`@Provide`装饰器没有入参，无需修改。

**变更原因：**

ArkTS-Sta的`@Provide`装饰器不支持传入联合类型参数，仅接受基础类型常量。

**适配建议：**

把`@Provide`装饰器的入参改为基础类型的常量。

### 参数类型为`string`

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，`CustomBuilder`类型的参数接收被`@Builder`装饰器装饰的调用函数时，需用匿名箭头函数包裹。

**变更原因：**

在ArkTS-Sta中，`CustomBuilder`的接口定义发生变更。

**适配建议：**

`CustomBuilder`类型的参数接收被`@Builder`装饰器装饰的调用函数时，需用匿名箭头函数包裹。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，被`@Builder`装饰器装饰的函数的执行上下文需要在声明时确定。

**变更原因：**

在ArkTS-Dyn中，回调函数的执行上下文在调用时指定。

在ArkTS-Sta中，回调函数的执行上下文是函数所在的实例对象。

**适配建议：**

在声明时就确定被`@Builder`装饰器装饰的函数的执行上下文。

**示例：**

ArkTS-Dyn

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
        // ArkTS-Dyn：this指向SubComponent
        // ArkTS-Sta：this指向SuperComponent
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
      // ArkTS-Dyn：执行代码后，SuperComponent组件显示的文本内容是'child'
      // ArkTS-Sta：执行相同代码后，SuperComponent组件显示的文本内容是'parent'
      SuperComponent()
    }
  }
}
```

ArkTS-Sta

在ArkTS-Sta中，为实现与ArkTS-Dyn相同的运行效果，需改造代码，将状态变量作为回调函数的参数传递。

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

## 禁止在`build`函数中修改状态变量

**规则：** `arkui-no-update-in-build`

**规则解释：**

在ArkTS-Sta中，禁止在`build`函数中修改状态变量。

**变更原因：**

在ArkTS-Dyn中，在`build`函数中修改状态变量的行为会导致告警，但代码可以正常运行。

在在ArkTS-Sta中，在`build`函数中修改状态变量的行为会导致运行时异常。

**适配建议：**

建议把修改状态变量的代码移动到`aboutToAppear`函数中，以避免运行时异常。

**示例：**

ArkTS-Dyn

```typescript
@Entry
@Component
struct Index {
  @State count: number = 1;

  build() {
    Column() {
      // ArkTS-Dyn：在build函数中修改状态变量的行为会导致告警
      // ArkTS-Sta：在build函数中修改状态变量的行为会导致运行时异常
      Text(`${this.count++}`)
    }
  }
}
```

ArkTS-Sta

```typescript
'use static'
import {
  Entry,
  Component,
  State,
  Column,
  Text,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State count: number = 1;

  // 把修改状态变量的代码移动到aboutToAppear函数中
  aboutToAppear(): void {
    this.count ++;
  }

  build() {
    Column() {
      Text(`${this.count}`)
    }
  }
}
```

## `AppStorage`中的值发生改变时会触发界面更新

**规则：** `arkui-stateful-appstorage`

**规则解释：**

在ArkTS-Sta中，当`AppStorage`中对应的值发生改变时，会触发界面更新。

**变更原因：**

在ArkTS-Sta中，如果在自定义组件的`build`方法中调用`AppStorage`的`get`、`has`、`keys`或`size`接口，会和组件建立依赖关系。

**适配建议：**

ArkTS-Sta的处理方式是能力增强，因此仅提示开发者上述情况可能产生的差异。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

ArkTS-Sta的处理方式是能力增强，因此仅提示开发者上述情况可能产生的差异。

## `UIUtils.makeObserved`接口不支持监听自定义类

**规则：** `arkui-makeobserved-cannot-observe-custom-class`

**规则解释：**

在ArkTS-Sta中，`UIUtils.makeObserved`不支持监听开发者自定义的类，需要按照示例进行修改。

**变更原因：**

在ArkTS-Sta中，`UIUtils.makeObserved`不支持监听开发者自定义的类。

**适配建议：**

按照示例进行修改。

### `makeObserved`和V1装饰器配合使用

如果`UIUtils.makeObserved`的入参是自定义类的对象，需为该类添加`@Observed`装饰器，并使用`@State`装饰监听的变量。

**示例：**

ArkTS-Dyn

```typescript
import { UIUtils } from '@kit.ArkUI';

class Info {
  id: number = 0;
  constructor(id: number) {
    this.id = id;
  }
}

@Entry
@Component
struct Index {
  message: Info = UIUtils.makeObserved(new Info(10));

  build() {
    Column() {
      Text(`${this.message.id}`)
      Button('change id').onClick((e: ClickEvent) => {
        this.message.id ++;
      })
    }
  }
}
```

ArkTS-Sta

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
class Info {
  id: number = 0;
  constructor(id: number) {
    this.id = id;
  }
}

@Entry
@Component
struct Index {
  @State message: Info = new Info(10);

  build() {
    Column() {
      Text(`${this.message.id}`)
      Button('change id').onClick((e: ClickEvent) => {
        this.message.id ++;
      })
    }
  }
}
```

### `makeObserved`和V2装饰器配合使用

如果`UIUtils.makeObserved`的入参是自定义类的对象，需为该类添加`@ObservedV2`装饰器，为该类的属性添加`@Trace`装饰器，并使用`@Local`装饰监听的变量。

**示例：**

ArkTS-Dyn

```TypeScript
import { UIUtils } from '@kit.ArkUI';

class Info {
  id: number = 0;
  constructor(id: number) {
    this.id = id;
  }
}

@Entry
@ComponentV2
struct Index {
  message: Info = UIUtils.makeObserved(new Info(10));

  build() {
    Column() {
      Text(`${this.message.id}`)
      Button('change id').onClick((e: ClickEvent) => {
        this.message.id ++;
      })
    }
  }
}
```

ArkTS-Sta

```TypeScript
'use static'
import {
  ObservedV2,
  Trace,
  Entry,
  ComponentV2,
  Local,
  Column,
  Text,
  Button,
  ClickEvent,
} from '@kit.ArkUI';

@ObservedV2
class Info {
  @Trace id: number = 0;
  constructor(id: number) {
    this.id = id;
  }
}

@Entry
@ComponentV2
struct Index {
  @Local message: Info = new Info(10);

  build() {
    Column() {
      Text(`${this.message.id}`)
      Button('change id').onClick((e: ClickEvent) => {
        this.message.id ++;
      })
    }
  }
}
```

## 不支持`@Prop`、`@StorageProp`和`@LocalStorageProp`装饰器

**规则：** `arkui-no-prop-decorator`、`arkui-no-storageprop-decorator`、`arkui-no-localstorageprop-decorator`

**规则解释：**

在ArkTS-Sta中，不支持`@Prop`、`@StorageProp`和`@LocalStrorageProp`装饰器，要分别用`@PropRef`、`@StoragePropRef`和`@LocalStroragePropRef`装饰器替代。

**变更原因：**

在ArkTS-Sta中，`@Prop`、`@StorageProp`和`@LocalStrorageProp`装饰器被废弃。

**适配建议：**

分别用`@PropRef`、`@StoragePropRef`和`@LocalStroragePropRef`装饰器去替代`@Prop`、`@StorageProp`和`@LocalStrorageProp`装饰器。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

## 不支持`LocalStorage.prop`、`LocalStorage.setAndProp`、`AppStorage.prop`和`AppStorage.setAndProp`接口

**规则：** `arkui-no-prop-function`、`arkui-no-setandprop-function`

**规则解释：**

在ArkTS-Sta中，不支持`LocalStorage.prop`、`LocalStorage.setAndProp`、`AppStorage.prop`和`AppStorage.setAndProp`接口，要分别用`LocalStorage.ref`、`LocalStorage.setAndRef`、`AppStorage.ref`和`AppStorage.setAndRef`接口替代。

**变更原因：**

在ArkTS-Sta中，`LocalStorage.prop`、`LocalStorage.setAndProp`、`AppStorage.prop`和`AppStorage.setAndProp`接口被废弃。

**适配建议：**

分别用`LocalStorage.ref`、`LocalStorage.setAndRef`、`AppStorage.ref`和`AppStorage.setAndRef`接口去替代`LocalStorage.prop`、`LocalStorage.setAndProp`、`AppStorage.prop`和`AppStorage.setAndProp`接口。

**示例：**

ArkTS-Dyn

```typescript
AppStorage.setOrCreate('PropA', 47);
let prop1: SubscribedAbstractProperty<number> = AppStorage.setAndProp<number>('PropA', 48);
let prop2: SubscribedAbstractProperty<number> = AppStorage.prop<number>('PropA');

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('PropB', 17);
let prop3: SubscribedAbstractProperty<number> = storage.setAndProp<number>('PropB', 18);
let prop4: SubscribedAbstractProperty<number> = storage.prop<number>('PropB');

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('Test')
    }
  }
}
```

ArkTS-Sta

```typescript
'use static'
import {
  AppStorage,
  AbstractProperty,
  LocalStorage,
  Entry,
  Component,
  Column,
  Text,
} from '@kit.ArkUI';

AppStorage.setOrCreate('PropA', 47);
let prop1: AbstractProperty<number> = AppStorage.setAndRef<number>('PropA', 48);
let prop2: AbstractProperty<number> | undefined = AppStorage.ref<number>('PropA');

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('PropB', 17);
let prop3: AbstractProperty<number> = storage.setAndRef<number>('PropB', 18);
let prop4: AbstractProperty<number> | undefined = storage.ref<number>('PropB');

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('Test')
    }
  }
}
```

## 不支持`@LocalBuilder`装饰器

**规则：** `arkui-no-localbuilder-decorator`

**规则解释：**

在ArkTS-Sta中，不支持`@LocalBuilder`装饰器，用`@Builder`装饰器替代。

**变更原因：**

在ArkTS-Sta中，`@LocalBuilder`装饰器和`@Builder`装饰器的作用相同，因此废弃`@LocalBuilder`装饰器。

**适配建议：**

用`@Builder`装饰器替代`@LocalBuilder`装饰器。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，自定义组件需要加上`@CustomLayout`装饰器，才能获得自定义布局能力。

**变更原因：**

受ArkTS-Sta静态类型系统的影响，自定义组件需要组件加上`@CustomLayout`装饰器，才能获得自定义布局能力。

**适配建议：**

为自定义组件加上`@CustomLayout`装饰器。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

**规则解释：**

在ArkTS-Sta中，如果想要渲染全部子组件，需要禁用`Repeat`的默认懒加载。

**变更原因：**

在ArkTS-Dyn中，`Repate`默认渲染全部子组件。

在ArkTS-Sta中，`Repeat`默认支持懒加载，如果想要渲染全部子组件，需要禁用默认的懒加载。

**适配建议：**

禁用`Repeat`的默认懒加载。

**示例：**

ArkTS-Dyn

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

ArkTS-Sta

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

## 使用`WrappedBuilder`时，需添加参数为箭头函数的泛型

**规则：** `arkui-wrappedbuilder-require-arrow-func-generic`

**规则解释：**

在ArkTS-Sta中，使用`WrappedBuilder`时，必须添加泛型，且泛型的参数必须为箭头函数。

**变更原因：**

在ArkTS-Sta中，`WrappedBuilder`的接口定义发生变更。

**适配建议：**

使用`WrappedBuilder`时，添加参数为箭头函数的泛型。

**示例：**

ArkTS-Dyn

```typescript
@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size);
}

const wrappedBuilder1: WrappedBuilder<[string, number]> = new WrappedBuilder(MyBuilder);
const wrappedBuilder2: WrappedBuilder<[string, number]> = new WrappedBuilder<[string, number]>(MyBuilder);

@Entry
@Component
struct TestWrappedBuilder1 {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        wrappedBuilder1.builder(this.message, 50);
        wrappedBuilder2.builder(this.message, 50);
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta

```typescript
'use static'
import {
  Builder,
  Text,
  WrappedBuilder,
  Entry,
  Component,
  State,
  Row,
  Column,
} from '@kit.ArkUI';

@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size);
}

const wrappedBuilder1: WrappedBuilder<@Builder (arg1: string, arg2: number) => void> = new WrappedBuilder<@Builder (arg1: string, arg2: number) => void>(MyBuilder);
const wrappedBuilder2: WrappedBuilder<@Builder (arg1: string, arg2: number) => void> = new WrappedBuilder<@Builder (arg1: string, arg2: number) => void>(MyBuilder);

@Entry
@Component
struct TestWrappedBuilder1 {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        wrappedBuilder1.builder(this.message, 50.0);
        wrappedBuilder2.builder(this.message, 50.0);
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用`wrappBuilder`时，泛型参数必须为箭头函数

**规则：** `arkui-wrapbuilder-require-arrow-func-generic`

**规则解释：**

在ArkTS-Sta中，`wrapBuilder`的泛型是可选的。如果指定了泛型，则其参数必须为箭头函数。

**变更原因：**

在ArkTS-Sta中，`WrappedBuilder`的接口定义发生变更。

**适配建议：**

把`wrapBuilder`的泛型参数改为箭头函数的形式。

**示例：**

ArkTS-Dyn
 
```typescript
@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size);
}

const wrappedBuilder1: WrappedBuilder<[string, number]> = wrapBuilder(MyBuilder);
const wrappedBuilder2: WrappedBuilder<[string, number]> = wrapBuilder<[string, number]>(MyBuilder);

@Entry
@Component
struct TestWrappedBuilder1 {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        wrappedBuilder1.builder(this.message, 50);
        wrappedBuilder2.builder(this.message, 50);
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta

```typescript
'use static'
import {
  Builder,
  Text,
  WrappedBuilder,
  wrapBuilder,
  Entry,
  Component,
  State,
  Row,
  Column,
} from '@kit.ArkUI';

@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size);
}

const wrappedBuilder1: WrappedBuilder<@Builder (arg1: string, arg2: number) => void> = wrapBuilder(MyBuilder);
const wrappedBuilder2: WrappedBuilder<@Builder (arg1: string, arg2: number) => void> = wrapBuilder<@Builder (arg1: string, arg2: number) => void>(MyBuilder);

@Entry
@Component
struct TestWrappedBuilder1 {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        wrappedBuilder1.builder(this.message, 50.0);
        wrappedBuilder2.builder(this.message, 50.0);
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

## `BuilderNode`的泛型参数不能为元组

**规则：** `arkui-buildernode-generic-no-tuple`

**规则解释：**

在ArkTS-Sta中，`BuilderNode`的泛型参数不能为元组，需要进行修改。

**变更原因：**

在ArkTS-Sta中，`BuilderNode`的接口定义发生变更。

**适配建议：**

如果`BuilderNode`的泛型参数为元组，就按照示例进行修改。

**示例：**

ArkTS-Dyn

```typescript
import { BuilderNode, NodeController, FrameNode } from '@kit.ArkUI';

class Params {
  item: string = '';

  constructor(item: string) {
    this.item = item;
  }
}

class MyNodeController extends NodeController {
  public builderNode1: BuilderNode<[]> | null = null;
  public builderNode2: BuilderNode<[Params]> | null = null;
  public frameNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    if (this.builderNode1 == null || this.builderNode2 == null) {
      this.builderNode1 = new BuilderNode(uiContext, { selfIdealSize : { width: 300, height: 200} });
      this.builderNode2 = new BuilderNode<[Params]>(uiContext, { selfIdealSize: { width: 300, height: 200} });
    }
    return this.frameNode;
  }
}
```

ArkTS-Sta

```typescript
'use static'
import { UIContext } from '@kit.ArkUI';

import { BuilderNode, NodeController, FrameNode } from '@kit.ArkUI';

class Params {
  item: string = '';

  constructor(item: string) {
    this.item = item;
  }
}

class MyNodeController extends NodeController {
  public builderNode1: BuilderNode | null = null;
  public builderNode2: BuilderNode<Params> | null = null;
  public frameNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    if (this.builderNode1 == null || this.builderNode2 == null) {
      this.builderNode1 = new BuilderNode(uiContext, { selfIdealSize : { width: 300.0, height: 200.0} });
      this.builderNode2 = new BuilderNode<Params>(uiContext, { selfIdealSize: { width: 300.0, height: 200.0} });
    }
    return this.frameNode;
  }
}
```

## `BuilderNode`的`update`接口的入参不能是字面量

**规则：** `arkui-buildernode-update-no-literal`

**规则解释：**

在ArkTS-Sta中，`BuilderNode`的`update`接口的入参不能是字面量。需要将字面量替换为新建`BuilderNode`节点时泛型中指定的类的实例，并确保该实例具有和字面量相同的字段值。

**变更原因：**

在ArkTS-Sta中，`BuilderNode`的`update`接口的定义发生变更。

**适配建议：**

将字面量替换为新建`BuilderNode`节点时泛型中指定的类的实例，并确保该实例具有和字面量相同的字段值。

**示例：**

ArkTS-Dyn

```typescript
import { NodeController, BuilderNode, FrameNode } from '@kit.ArkUI';

class Params {
  item: string = '';

  constructor(item: string) {
    this.item = item;
  }
}

interface CustomInterface {
  item: string;
}

class MyNodeController extends NodeController {
  public builderNode1: BuilderNode<[Params]> | null = null;
  public builderNode2: BuilderNode<[Params]> | null = null;
  public builderNode3: BuilderNode<[Params]> | null = null;
  public frameNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    if (this.builderNode1 == null || this.builderNode2 == null || this.builderNode3 == null) {
      this.builderNode1 = new BuilderNode<[Params]>(uiContext, { selfIdealSize : { width: 300, height: 200} });
      this.builderNode2 = new BuilderNode<[Params]>(uiContext, { selfIdealSize : { width: 300, height: 200} });
      this.builderNode3 = new BuilderNode<[Params]>(uiContext, { selfIdealSize : { width: 300, height: 200} });
    }

    return this.frameNode;
  }

  updateItem(item: string, customParam: boolean): void {
    if (this.builderNode1 && this.builderNode2 && this.builderNode3) {
      if (customParam) {
        const customInterfaceParams: CustomInterface = { item: 'C' };
        this.builderNode1!.update(customInterfaceParams);
        this.builderNode2!.update({ item: 'C' });
        this.builderNode3!.update({ item: item });
      } else {
      }
    }
  }
}
```

ArkTS-Sta

```typescript
'use static'
import { UIContext } from '@kit.ArkUI';

import { NodeController, BuilderNode, FrameNode } from '@kit.ArkUI';

class Params {
  item: string = '';

  constructor(item: string) {
    this.item = item;
  }
}

interface CustomInterface {
  item: string;
}

class MyNodeController extends NodeController {
  public builderNode1: BuilderNode<Params> | null = null;
  public builderNode2: BuilderNode<Params> | null = null;
  public builderNode3: BuilderNode<Params> | null = null;
  public frameNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    if (this.builderNode1 == null || this.builderNode2 == null || this.builderNode3 == null) {
      this.builderNode1 = new BuilderNode<Params>(uiContext, { selfIdealSize : { width: 300.0, height: 200.0} });
      this.builderNode2 = new BuilderNode<Params>(uiContext, { selfIdealSize : { width: 300.0, height: 200.0} });
      this.builderNode3 = new BuilderNode<Params>(uiContext, { selfIdealSize : { width: 300.0, height: 200.0} });
    }

    return this.frameNode;
  }

  updateItem(item: string, customParam: boolean): void {
    if (this.builderNode1 && this.builderNode2 && this.builderNode3) {
      if (customParam) {
        const customInterfaceParams: CustomInterface = { item: 'C' };
        this.builderNode1!.update(new Params(customInterfaceParams.item));
        this.builderNode2!.update(new Params('C'));
        this.builderNode3!.update(new Params(item));
      } else {
      }
    }
  }
}
```

## 不支持`nestingBuilderSupported`属性

**规则：** `arkui-buildernode-no-nestingbuildersupported`

**规则解释：**

在ArkTS-Sta中，不支持`nestingBuilderSupported`属性。如果`BuilderNode`中`build`接口的入参中包含该属性，需要按照示例进行修改。

**变更原因：**

在ArkTS-Sta中，不支持`nestingBuilderSupported`属性。

**适配建议：**

如果`BuilderNode`中`build`接口的入参中包含`nestingBuilderSupported`属性，需要按照示例进行修改。

**示例：**

ArkTS-Dyn

```typescript
import { NodeController, BuilderNode, FrameNode } from '@kit.ArkUI';

class Params {
  item: string = '';

  constructor(item: string) {
    this.item = item;
  }
}

@Builder
function buildNode(param: Params) {}

class MyNodeController extends NodeController {
  public builderNode1: BuilderNode<[Params]> | null = null;
  public builderNode2: BuilderNode<[Params]> | null = null;
  public frameNode: FrameNode | null = null;
  public item: string = "";
  public flag: boolean = true;

  makeNode(uiContext: UIContext): FrameNode | null {
    if (this.builderNode1 == null || this.builderNode2 == null) {
      this.builderNode1 = new BuilderNode<[Params]>(uiContext, { selfIdealSize : { width: 300, height: 200} });
      this.builderNode2 = new BuilderNode<[Params]>(uiContext, { selfIdealSize : { width: 300, height: 200} });
      this.builderNode1!.build(wrapBuilder(buildNode), new Params(this.item), { nestingBuilderSupported: false });
      this.builderNode2!.build(wrapBuilder(buildNode), new Params(this.item), { nestingBuilderSupported: this.flag });
    }

    return this.frameNode;
  }
}
```

ArkTS-Sta

```typescript
'use static'
import {
  Builder,
  UIContext,
  wrapBuilder,
} from '@kit.ArkUI';

import { NodeController, BuilderNode, FrameNode } from '@kit.ArkUI';

class Params {
  item: string = '';

  constructor(item: string) {
    this.item = item;
  }
}

@Builder
function buildNode(param: Params) {}

class MyNodeController extends NodeController {
  public builderNode1: BuilderNode<Params> | null = null;
  public builderNode2: BuilderNode<Params> | null = null;
  public frameNode: FrameNode | null = null;
  public item: string = "";
  public flag: boolean = true;

  makeNode(uiContext: UIContext): FrameNode | null {
    if (this.builderNode1 == null || this.builderNode2 == null) {
      this.builderNode1 = new BuilderNode<Params>(uiContext, { selfIdealSize : { width: 300.0, height: 200.0} });
      this.builderNode2 = new BuilderNode<Params>(uiContext, { selfIdealSize : { width: 300.0, height: 200.0} });
      this.builderNode1!.build(wrapBuilder(buildNode), new Params(this.item), {});
      this.builderNode2!.build(this.flag ? wrapBuilder(buildNode) : wrapBuilder(buildNode), new Params(this.item), {});
    }

    return this.frameNode;
  }
}
```

## 已废弃的高频UI接口用`UIContext`提供的接口作为替代

**规则：** `arkui-deprecated-interface`

**规则解释：**

在ArkTS-Sta中，对于使用频率较高的废弃UI接口，迁移工具提供自动修复能力。

**变更原因：**

在ArkTS-Sta中，部分UI接口被废弃。

**适配建议：**

按照示例进行修改。

**示例：**

ArkTS-Dyn

```typescript
@Entry
@Component
struct Index {
  @State message: string = 'Hello World'

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let context: Context = getContext(this) as Context;
            console.info("CacheDir:" + context.cacheDir);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

ArkTS-Sta

```typescript
'use static'
import {
  Entry,
  Component,
  State,
  Row,
  Column,
  Text,
  FontWeight,
  Context,
  UIContext,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World'

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let context: Context = UIContext.getFocusedUIContext()!.getHostContext() as Context;
            console.info("CacheDir:" + context.cacheDir);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```