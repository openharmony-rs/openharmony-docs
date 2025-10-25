# \@Provide and \@Consume Decorators: Two-Way Synchronization with Descendant Components
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Provide and @Consume are used to synchronize data bidirectionally with descendant components and transfer state data between multiple levels. They do not involve passing a variable from component to component multiple times.

An \@Provide decorated state variable exists in the ancestor component and is said to be "provided" to descendent components. An \@Consume decorated state variable is used in a descendent component. It is linked to ("consumes") the provided state variable in its ancestor component.

@Provide and @Consume are used for bidirectional synchronization across component levels. Before reading the @Provide and @Consume documents, you are advised to have a basic understanding of the basic syntax of the UI paradigm and custom components. you are advised to read [Basic Syntax Overview](./arkts-basic-syntax-overview.md), [Declarative UI Description](./arkts-declarative-ui-description.md), and [Creating a Custom Component](./arkts-create-custom-components.md) to have an understanding of the basic syntax of UI paradigms. For best practices, see [State Management](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-status-management).

> **NOTE**
>
> These two decorators can be used in ArkTS widgets since API version 9.
>
> These two decorators can be used in atomic services since API version 11.
>
>In API version 19 and earlier versions, @Provide and @Consume support bidirectional synchronization only in declarative nodes.
>
> From API version 20, the variable decorated with @Consume supports the setting of default values. If no matching result is found for @Provide, the variable decorated with @Consume is initialized using the default value. If a matching result is found for @Provide, the variable decorated with @Consume uses the value of the matching result for @Provide, and the default value does not take effect.
>
> From API version 20, you can set the [BuildOptions](../../reference/apis-arkui/js-apis-arkui-builderNode.md#buildoptions12) parameter [BuilderNode](../../reference/apis-arkui/js-apis-arkui-builderNode.md) to true to enable @Provide and @Consume to support cross-[BuilderNode](../../reference/apis-arkui/js-apis-arkui-builderNode.md) bidirectional synchronization. Note that BuilderNode constructs nodes before adding them to the tree. Therefore, the default value must be set for @Consume defined in BuilderNode. After BuilderNode is added to the tree, the latest data of @Provide is obtained again to establish a bidirectional synchronization relationship. For details, see [Using @Consume to Establish Two-Way Synchronization with @Provide Across BuilderNode Scenarios](#using-consume-to-establish-two-way-synchronization-with-provide-across-buildernode-scenarios).

## Overview

\@Provide/\@Consume decorated state variables have the following features:

- State variables decorated with @Provide are automatically available to all their descendant components. Developers do not need to pass variables between components repeatedly.

- A descendent component gains access to the provided state variable by decorating a variable with \@Consume. This establishes a two-way data synchronization between the provided and the consumed variable. This synchronization works in the same manner as a combination of \@State and \@Link does. The only difference is that the former allows transfer across multiple levels of the UI parent-child hierarchy.

- \@Provide and \@Consume can be bound using the same variable name or variable alias. They must be of the same type. Otherwise, implicit type conversion occurs, causing abnormal application behavior.

```ts
// Binding through the same variable name
@Provide age: number = 0;
@Consume age: number;

// Binding through the same variable alias
@Provide('a') id: number = 0;
@Consume('a') age: number;

// The alias of the variable provided by @Provide is the same as the name of the variable consumed by @Consume.
@Provide('a') id: number = 0;
@Consume a: number;

// The name of the variable provided by @Provide is the same as the alias of the variable consumed by @Consume.
@Provide id: number = 0;
@Consume('id') a: number;

```
When @Provide specifies a variable alias, both the variable name and alias are saved. When @Consume searches for a variable, the variable alias is used as the search value. If no alias is available, the variable name is used as the search value. As long as the search value provided by @Consume is the same as the variable name or alias saved by @Provide, the binding relationship can be successfully established.

## Decorator Description

The rules of \@State also apply to \@Provide. The difference is that \@Provide also functions as a synchronization source for multi-layer descendants.

| \@Provide Decorator| Description                                      |
| -------------- | ---------------------------------------- |
| Parameters         | Alias: constant string, optional.|
| Synchronization type          | Two-way:<br>Data synchronization from the @Provide variable to all @Consume variables and vice versa. The two-way synchronization behaviour is the same as that of the combination of \@State and \@Link.|
| Allowed variable types     | Object, class, string, number, Boolean, enum, and array of these types.<br>Since API version 10, the [Date](#decorating-variables-of-the-date-type) type is supported.<br>Since API version 11, the [Map](#decorating-variables-of-the-map-type), [Set](#decorating-variables-of-the-set-type), undefined, and null types, the union type [Length](../../reference/apis-arkui/arkui-ts/ts-types.md#length), [ResourceStr](../../reference/apis-arkui/arkui-ts/ts-types.md#resourcestr) defined by the ArkUI framework, the ResourceColor type, and the union type of these types are supported. For the implementation example, see [Using @Provide and @Consume with Union Type Instances](#using-provide-and-consume-with-union-type-instances).<br>For details about the scenarios of supported types, see [Observed Changes](#observed-changes).|
| Variable types that cannot be decorated| The Function type cannot be decorated.     |
| Initial value for the decorated variable     | Required.                                   |
| Support for the **allowOverride** parameter         | Yes. After **allowOverride** is declared, both aliases and attribute names can be overridden. For details, see [Support for the allowOverride Parameter](#support-for-the-allowoverride-parameter).|

| \@Consume Decorator| Description                                      |
| -------------- | ---------------------------------------- |
| Parameters         | Alias: constant string, optional.|
| Synchronization type          | Bidirectional synchronization: from \@Provide variables (for details, see \@Provide) to all \@Consume variables, and vice versa. The two-way synchronization behaviour is the same as that of the combination of \@State and \@Link.|
| Allowed variable types     | Object, class, string, number, Boolean, enum, and array of these types.<br>Since API version 10, the [Date](#decorating-variables-of-the-date-type) type is supported.<br>Since API version 11, the [Map](#decorating-variables-of-the-map-type), [Set](#decorating-variables-of-the-set-type), undefined, and null types, the union type [Length](../../reference/apis-arkui/arkui-ts/ts-types.md#length), [ResourceStr](../../reference/apis-arkui/arkui-ts/ts-types.md#resourcestr) defined by the ArkUI framework, the ResourceColor type, and the union type of these types are supported. For the implementation example, see [Using @Provide and @Consume with Union Type Instances](#using-provide-and-consume-with-union-type-instances).<br>For details about the supported types, see [Observed Changes](#observed-changes).<br>**NOTE**<br>Before API version 20, the \@Consume-decorated variable must have a corresponding property and \@Provide-decorated variable of the alias on the parent component or ancestor component.
| Initial value for the decorated variable     | From API version 20, \@Consume supports default values. If there is a \@Provide that is successfully matched, the variable value of \@Provide is used as the initial value. For details, see [Setting Default Values for @Consume Decorated Variables](#setting-default-values-for-consume-decorated-variables).                           |

## Variable Transfer/Access Rules

| \@Provide Transfer/Access| Description                                      |
| -------------- | ---------------------------------------- |
| Initialization and update from the parent component    | Optional. An @Provide decorated variable can be initialized from a regular variable (whose change does not trigger UI refresh) or an [\@State](./arkts-state.md), [\@Link](./arkts-link.md), [\@Prop](./arkts-prop.md), \@Provide, \@Consume, [\@ObjectLink](./arkts-observed-and-objectlink.md), [\@StorageLink](./arkts-appstorage.md#storagelink), [\@StorageProp](./arkts-appstorage.md#storageprop), [\@LocalStorageLink](./arkts-localstorage.md#localstoragelink), or [\@LocalStorageProp](./arkts-localstorage.md#localstorageprop) decorated variable in its parent component.|
| Child component initialization      | Supported; can be used to initialize an \@State, \@Link, \@Prop, or \@Provide decorated variable in the child component.|
| Synchronization with the parent component        | No                                      |
| Synchronization with descendant components       | Two-way with @Consume decorated variables in descendant components.                         |
| Access from outside the component     | Private, accessible only within the component.                         |

  **Figure 1** \@Provide initialization rule 

![en-us_image_0000001552614217](figures/en-us_image_0000001552614217.png)

| \@Consume Transfer/Access| Description                                      |
| -------------- | ---------------------------------------- |
| Initialization and update from the parent component    | Forbidden.     |
| Child component initialization      | Supported; can be used to initialize an \@State, \@Link, \@Prop, or \@Provide decorated variable in the child component.|
| Synchronization with the ancestor component       | Two-way with the @Provide decorated variable in the ancestor component.                         |
| Access from outside the component     | Private, accessible only within the component.                          |

  **Figure 2** \@Consume initialization rule 


![en-us_image_0000001502094666](figures/en-us_image_0000001502094666.png)

## Observed Changes and Behavior

### Observed Changes

- When the decorated variable is of the Boolean, string, or number type, its value change can be observed.

- When the decorated variable is of the class or Object type, its value change and value changes of all its attributes, that is, the attributes that **Object.keys(observedObject)** returns, can be observed.

- When the decorated variable is an array, you can observe the value change of the array, array items, and API operations.

- When the decorated variable is a date, you can observe the value change of the date. You can also call the setFullYear, setMonth, setDate, setHours, setMinutes, setSeconds, setMilliseconds, setTime, setUTCFullYear, setUTCMonth, setUTCDate, setUTCHours, setUTCMinutes, setUTCSeconds, setUTCMilliseconds API of the date to update the date properties. For details, see [Decorating Variables of the Date Type](#decorating-variables-of-the-date-type).

- When the decorated variable is of the **Map** type, the following changes can be observed: (1) complete **Map** object reassignment; (2) changes caused by calling **set**, **clear**, or **delete**. For details, see [Decorating Variables of the Map Type](#decorating-variables-of-the-map-type).

- When the decorated variable is of the **Set** type, the following changes can be observed: (1) complete **Set** object reassignment; (2) changes caused by calling **add**, **clear**, or **delete**. For details, see [Decorating Variables of the Set Type](#decorating-variables-of-the-set-type).

### Framework Behavior

1. Initial rendering:
   1. The variable decorated by \@Provide is passed to all child components of the component to which \@Provide belongs in the form of a map.
   2. If \@Consume variables are used in child components, the framework searches the map for the \@Provide variable corresponding to the variable name or alias. If no matching variable is found, the framework throws a JS error before API version 20. From API version 20, if the @Provide-decorated variable is not found, the framework checks whether the @Consume-decorated variable has a default value. If not, the framework throws a JS error.
   3. When initializing the @Consume-decorated variable, if the variable name or alias in the map corresponds to the @Provide-decorated variable, the process is similar to that of @State/\@Link. The @Consume-decorated variable searches for the corresponding @Provide-decorated variable in the map, saves the variable, and registers itself with the @Provide-decorated variable.
   4. From API version 20, when initializing the @Consume-decorated variable, if the variable name or alias in the map does not correspond to the @Provide-decorated variable and the @Consume-decorated variable has a default value, the @Consume-decorated variable uses the default value to create a temporary data source to ensure the continuity of the notification link.

2. When the \@Provide decorated variable is updated:
   1. The system traverses and updates all system components (**elementId**) and state variable (\@Consume) that depend on the \@Provide decorated variable, with which the \@Consume decorated variable has registered itself on initial render. After the \@Provide decorated variable of the parent component is changed, all system components (**elementId**) and state variables (\@Consume) that depend on the parent component are traversed and updated.
   2. After the \@Consume decorated variable is updated in all owning child components, all system components (**elementId**) that depend on the \@Consume decorated variable are updated. In this way, changes to the \@Provide decorated variable are synchronized to the \@Consume decorated variable.

3. When the \@Consume decorated variable is updated:

   As can be learned from the initial render procedure, the \@Consume decorated variable holds an instance of \@Provide. After the \@Consume decorated variable is updated, the update method of \@Provide is called to synchronize the changes to \@Provide.



## Constraints

1. The key of the @Provide/\@Consume parameter must be of the string type. Otherwise, an error is reported during compilation.

    ```ts
    // Incorrect usage. An error is reported during compilation.
    let change: number = 10;
    @Provide(change) message: string = 'Hello';
  
    // Correct usage.
    let change: string = 'change';
    @Provide(change) message: string = 'Hello';
    ```

2. Variables decorated with \@Consume cannot be initialized in constructor parameters. Otherwise, an error will be reported during compilation. \@Consume can match the corresponding \@Provide variable only by key or initialize the \@Provide variable by setting the default value from API version 20.

    **Incorrect Usage**
  
    ```ts
    @Component
    struct Child {
      @Consume msg: string;
  
      build() {
        Text(this.msg)
      }
    }
  
    @Entry
    @Component
    struct Parent {
      @Provide message: string = 'Hello';
  
      build() {
        Column() {
          // Incorrect format. External initialization is not allowed.
          Child({msg: 'Hello'})
        }
      }
    }
    ```

    **Correct Usage**
  
    ```ts
    @Component
    struct Child {
      @Consume num: number;
      //From API version 20, the variables decorated with \@Consume support default value setting.
      @Consume num1: number = 17;
  
      build() {
        Column() {
          Text(`Value of num: ${this.num}`)
          Text(`num1: ${this.num1}`)
        }
      }
    }
  
    @Entry
    @Component
    struct Parent {
      @Provide num: number = 10;
  
      build() {
        Column() {
          Text(`Value of num: ${this.num}`)
          Child()
        }
      }
    }
    ```
  
3. \@When the **key** of \@Provide is defined repeatedly, the framework throws a runtime error to remind you. If you need to define the **key** repeatedly, use [allowoverride](#support-for-the-allowoverride-parameter).

    ```ts
    // Incorrect format. "a" is defined repeatedly.
    @Provide('a') count: number = 10;
    @Provide('a') num: number = 10;
  
    // Correct usage.
    @Provide('a') count: number = 10;
    @Provide('b') num: number = 10;
    ```
  
4. In versions earlier than API version 20, if the @Provide variable corresponding to the key is not defined when the @Consume variable is initialized, the framework throws a runtime error, indicating that the @Consume variable fails to be initialized because the @Provide variable corresponding to the key cannot be found. From API version 20 onwards, if the @Provide variable corresponding to the key is not defined and no default value is set when the @Consume variable is initialized, the framework throws a runtime error, indicating that the @Consume variable fails to be initialized because the @Provide variable corresponding to the key cannot be found and no default value is set.

    **Incorrect Usage**
  
    ```ts
    @Component
    struct Child {
      @Consume num: number;
  
      build() {
        Column() {
          Text(`Value of num: ${this.num}`)
        }
      }
    }
  
    @Entry
    @Component
    struct Parent {
      // Incorrect format. @Provide is missing.
      num: number = 10;
  
      build() {
        Column() {
          Text(`Value of num: ${this.num}`)
          Child()
        }
      }
    }
    ```

    **Correct Usage**
  
    ```ts
    @Component
    struct Child {
      @Consume num: number;
      // Correct. From API version 20 onwards, the @Consume-decorated variable supports default value setting.
      @Consume num_with_defaultValue: number = 6;
  
      build() {
        Column() {
          Text(`Value of num: ${this.num}`)
          Text(`num_with_defaultValue value: ${this.num_with_defaultValue}`)
        }
      }
    }
  
    @Entry
    @Component
    struct Parent {
      // Correct usage.
      @Provide num: number = 10;

      build() {
        Column() {
          Text(`Value of num: ${this.num}`)
          Child()
        }
      }
    }
    ```

5. \@Provide and \@Consume cannot decorate variables of the function type. Otherwise, the framework throws a runtime error.

6. From API version 20 onwards, @Provide and @Consume can be used for cross-BuilderNode pairing. When the BuilderNode is constructed, \@Consume finds the nearest \@Provide by matching keys. The types of the two must be the same. If the types are different, a runtime error is reported.
You need to check whether the types are different, including the class instance. For example:
```ts
class A {}
class B {}
//The two messages are of the object type, but their constructors are different. The two messages are of different types.
@Provide message: A = new A();
@Consume message: B = new B();
```
In non- BuilderNode scenarios, it is recommended that the \@Provide/\@Consume types be the same. Although there is no strong verification during running, the \@Consume-decorated variable is implicitly converted to the type of the \@Provide-decorated variable during initialization.
```ts
import { NodeController, BuilderNode, FrameNode, UIContext } from '@kit.ArkUI';

@Builder
function buildText() {
  Column() {
    Child()
  }
}

class TextNodeController extends NodeController {
  private builderNode: BuilderNode<[]> | null = null;

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    this.builderNode = new BuilderNode(context);
    //Configure cross- BuilderNode support for @Provide/@Consume.
    this.builderNode.build(wrapBuilder(buildText), undefined,
      { enableProvideConsumeCrossing: true });
    //Mount the root node of the BuilderNode to the NodeContainer.
    return this.builderNode.getFrameNode();
  }
}

@Entry
@Component
struct Index {
  @Provide message: string = 'hello';
  controller: TextNodeController = new TextNodeController();

  build() {
    Column() {
      NodeContainer(this.controller)
        .width('100%')
        .height(100)
    }
    .width('100%')
    .height('100%')
  }
}


@Component
struct Child {
  // After the child component is added to the tree through BuilderNode, the types of @Consume and @Provide in Index are inconsistent. As a result, a runtime error is thrown.
  @Consume message: number = 0;

  build() {
    Column() {
      Text(`@Consume ${this.message}`)
    }
  }
}
```

## Application scenarios

The following example shows how to synchronize the @Provide variable and the @Consume variable in the child component bidirectionally. When you click the buttons in the ToDo and ToDoItem components, the change of count is synchronized bidirectionally in the ToDo and ToDoItem components.

```ts
@Component
struct ToDoItem {
  // The @Consume decorated variable is bound to the @Provide decorated variable in its ancestor component ToDo under the same attribute name.
  @Consume count: number;

  build() {
    Column() {
      Text(`count(${this.count})`)
      Button(`count(${this.count}), count + 1`)
        .onClick(() => this.count += 1)
    }
    .width('50%')
  }
}

@Component
struct ToDoList {
  build() {
    Row({ space: 5 }) {
      ToDoItem()
      ToDoItem()
    }
  }
}

@Component
struct ToDoDemo {
  build() {
    ToDoList()
  }
}

@Entry
@Component
struct ToDo {
  // The variable decorated with @Provide count is provided by the entry component ToDo for its child components.
  @Provide count: number = 0;

  build() {
    Column() {
      Button(`count(${this.count}), count + 1`)
        .onClick(() => this.count += 1)
      ToDoDemo()
    }
  }
}
```
### Decorating Variables of the Map Type

> **NOTE**
>
> \@Provide and \@Consume support the Map type since API version 11.

In the following example, the message type is Map\<number, string\>. When you tap the button, the value of message is changed and the view is refreshed accordingly.

```ts
@Component
struct Child {
  @Consume message: Map<number, string>

  build() {
    Column() {
      ForEach(Array.from(this.message.entries()), (item: [number, string]) => {
        Text(`${item[0]}`)
          .fontSize(30)
        Text(`${item[1]}`)
          .fontSize(30)
        Divider()
      })
      Button('Consume init Map')
        .onClick(() => {
          this.message = new Map([[0, 'a'], [1, 'b'], [3, 'c']]);
        })
      Button('Consume set new one')
        .onClick(() => {
          this.message.set(4, 'd');
        })
      Button('Consume clear')
        .onClick(() => {
          this.message.clear();
        })
      Button('Consume replace the first item')
        .onClick(() => {
          this.message.set(0, 'aa');
        })
      Button('Consume delete the first item')
        .onClick(() => {
          this.message.delete(0);
        })
    }
  }
}


@Entry
@Component
struct MapSample {
  @Provide message: Map<number, string> = new Map([[0, 'a'], [1, 'b'], [3, 'c']])

  build() {
    Row() {
      Column() {
        Button('Provide init Map')
          .onClick(() => {
            this.message = new Map([[0, 'a'], [1, 'b'], [3, 'c'], [4, 'd']]);
          })
        Child()
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### Decorating Variables of the Set Type

> **NOTE**
>
> \@Provide and \@Consume support the Set type since API version 11.

In the following example, the message type is Set\<number\>. When you tap the button, the value of message is changed and the view is refreshed accordingly.

```ts
@Component
struct Child {
  @Consume message: Set<number>

  build() {
    Column() {
      ForEach(Array.from(this.message.entries()), (item: [number, number]) => {
        Text(`${item[0]}`)
          .fontSize(30)
        Divider()
      })
      Button('Consume init set')
        .onClick(() => {
          this.message = new Set([0, 1, 2, 3, 4]);
        })
      Button('Consume set new one')
        .onClick(() => {
          this.message.add(5);
        })
      Button('Consume clear')
        .onClick(() => {
          this.message.clear();
        })
      Button('Consume delete the first one')
        .onClick(() => {
          this.message.delete(0);
        })
    }
    .width('100%')
  }
}


@Entry
@Component
struct SetSample {
  @Provide message: Set<number> = new Set([0, 1, 2, 3, 4])

  build() {
    Row() {
      Column() {
        Button('Provide init set')
          .onClick(() => {
            this.message = new Set([0, 1, 2, 3, 4, 5]);
          })
        Child()
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### Decorating Variables of the Date Type

In the following example, the selectedDate variable is of the Date type. When you tap the button, the value of selectedDate is changed and the view is refreshed accordingly.

```ts
@Component
struct Child {
  @Consume selectedDate: Date;

  build() {
    Column() {
      Button(`child increase the day by 1`)
        .onClick(() => {
          this.selectedDate.setDate(this.selectedDate.getDate() + 1);
        })
      Button('child update the new date')
        .margin(10)
        .onClick(() => {
          this.selectedDate = new Date('2023-09-09');
        })
      DatePicker({
        start: new Date('1970-1-1'),
        end: new Date('2100-1-1'),
        selected: this.selectedDate
      })
    }
  }
}

@Entry
@Component
struct Parent {
  @Provide selectedDate: Date = new Date('2021-08-08')

  build() {
    Column() {
      Button('parent increase the day by 1')
        .margin(10)
        .onClick(() => {
          this.selectedDate.setDate(this.selectedDate.getDate() + 1);
        })
      Button('parent update the new date')
        .margin(10)
        .onClick(() => {
          this.selectedDate = new Date('2023-07-07');
        })
      DatePicker({
        start: new Date('1970-1-1'),
        end: new Date('2100-1-1'),
        selected: this.selectedDate
      })
      Child()
    }
  }
}
```

### Using @Provide and @Consume with Union Type Instances

@Provide and @Consume support union types, undefined, and null. In the following example, the type of count is string | undefined. When clicking the Button in the parent component Parent to change the property or type of count, the Child component will refresh accordingly.

```ts
@Component
struct Child {
  // The @Consume decorated variable is bound to the @Provide decorated variable in its ancestor component Ancestors under the same attribute name.
  @Consume count: string | undefined;

  build() {
    Column() {
      Text(`count(${this.count})`)
      Button(`count(${this.count}), Child`)
        .onClick(() => this.count = 'Ancestors')
    }
    .width('50%')
  }
}

@Component
struct Parent {
  build() {
    Row({ space: 5 }) {
      Child()
    }
  }
}

@Entry
@Component
struct Ancestors {
  // The @Provide decorated variable count of the union type is provided by the entry component Ancestors for its descendant components.
  @Provide count: string | undefined = 'Child';

  build() {
    Column() {
      Button(`count(${this.count}), Child`)
        .onClick(() => this.count = undefined)
      Parent()
    }
  }
}
```

### Support for the allowOverride Parameter

**allowOverride** allows you to override an existing \@Provide decorated variable.

> **NOTE**
>
> This feature is supported since API version 11.

| Name  | Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| allowOverride | string | No| Enables overriding for \@Provide. When you define an \@Provide decorated variable, use this parameter to override the existing variable with the same name (if any) in the same component tree. If this parameter is not used, defining a variable whose name is already in use will return an error.|

```ts
@Component
struct MyComponent {
  @Provide({allowOverride : 'reviewVotes'}) reviewVotes: number = 10;
}
```

The complete sample code is as follows:

```ts
@Component
struct GrandSon {
  // The @Consume decorated variable is bound to the @Provide decorated variable in its ancestor component under the same attribute name.
  @Consume('reviewVotes') reviewVotes: number;

  build() {
    Column() {
      Text(`reviewVotes(${this.reviewVotes})`) // The Text component displays 10.
      Button(`reviewVotes(${this.reviewVotes}), give +1`)
        .onClick(() => this.reviewVotes += 1)
    }
    .width('50%')
  }
}

@Component
struct Child {
  @Provide({ allowOverride: 'reviewVotes' }) reviewVotes: number = 10;

  build() {
    Row({ space: 5 }) {
      GrandSon()
    }
  }
}

@Component
struct Parent {
  @Provide({ allowOverride: 'reviewVotes' }) reviewVotes: number = 20;

  build() {
    Child()
  }
}

@Entry
@Component
struct GrandParent {
  @Provide('reviewVotes') reviewVotes: number = 40;

  build() {
    Column() {
      Button(`reviewVotes(${this.reviewVotes}), give +1`)
        .onClick(() => this.reviewVotes += 1)
      Parent()
    }
  }
}
```

In the preceding example:
- GrandParent declares @Provide('reviewVotes') reviewVotes: number = 40.
- Parent is a child component of GrandParent. @Provide is declared as allowOverride to override @Provide('reviewVotes') reviewVotes: number = 40 of GrandParent. If **allowOverride** is not declared, a runtime error is thrown to indicate that the @Provide decorated variable is already in use. The same case applies to **Child**.
- The @Consume decorated variable of **GrandSon** is initialized from the @Provide decorated variable of its nearest ancestor under the same attribute name.
- GrandSon finds that the @Provide with the same attribute name is in the ancestor Child. Therefore, the initialized value of @Consume('reviewVotes') reviewVotes: number is 10. If an @Provide decorated variable with the same attribute name as @Consume decorated variable is not defined in **Child**, **GrandSon** continues its search in **Parent** until it finds the one decorated by @Provide with the same attribute name, whose value is **20**.
- If no such a variable is found when **GrandSon** has reached the root node, an error is thrown to indicate that @Provide could not be found for @Consume initialization.

### Setting Default Values for @Consume Decorated Variables

> **NOTE**
>
> From API version 20, the variable decorated with \@Consume supports the setting of the default value.

```ts
@Component
struct MyComponent {
  @Consume('withDefault') defaultValue: number = 10;
}
```

The complete sample code is as follows:

```ts
@Entry
@Component
struct Parent {
  @Provide('firstKey') provideOne: string | undefined = undefined;
  @Provide('secondKey') provideTwo: string = 'the second provider';

  build(){
    Column(){
      Row(){
        Column() {
          Text(`${this.provideOne}`)
          Text(`${this.provideTwo}`)
        }

        Column(){
          //Click the change provideOne button. The provideOne and textOne attributes in the child component change at the same time.
          Button('change provideOne')
            .onClick(() => {
              this.provideOne = undefined;
            })
          //Click the change provideTwo button. The provideTwo and textTwo attributes in the child component change at the same time.
          Button('change provideTwo')
            .onClick(() => {
              this.provideTwo = 'the next provider';
            })
        }
      }

      Row(){
        Column() {
          Child()
        }
      }
    }
  }
}

@Component
struct Child {
  // @Consume-decorated variables are bound to @Provide-decorated variables in the ancestor using the same alias, and the default value is set.
  @Consume('firstKey') textOne: string | undefined = 'child';
  // @Consume-decorated variables are bound to @Provide-decorated variables in the ancestor using the same alias, and the default value is not set.
  @Consume('secondKey') textTwo: string;
  // @Consume-decorated variables do not match @Provide-decorated variables in the ancestor, but the default value is set.
  @Consume('thirdKey') textThree: string = 'defaultValue';

  build(){
    Column() {
      Text(`${this.textOne}`)
      Text(`${this.textTwo}`)
      Text(`${this.textThree}`)
      // When you click the change textOne button, textOne and provideOne of the parent component change at the same time.
      Button('change textOne')
        .onClick(() => {
          this.textOne = 'not undefined';
        })
      // When you click the change textTwo button, textTwo and provideTwo of the parent component change at the same time.
      Button('change textTwo')
        .onClick(() => {
          this.textTwo = 'change textTwo';
        })
    }
  }
}
```

In the preceding example:
- Parent declares @Provide('firstKey') provideOne: string | undefined = undefined and @Provide('secondKey') provideTwo: string = 'the second provider'.
- Child declares @Consume('firstKey') textOne: string | undefined = 'child', @Consume('secondKey') textTwo: string, and @Consume('thirdKey') textThree: string = 'defaultValue'.
- Child is a child component of Parent. When initializing the three attributes decorated with @Consume, textOne is bound to the provideOne attribute in Parent based on the alias firstKey. The value of provideOne overwrites the default value of textOne. Therefore, the initial value of textOne is undefined. textTwo is bound to the providedTwo attribute in Parent based on the alias secondKey. The initial value of textTwo is the second provider. textThree does not have a matching result in the ancestor component. If no default value is set for @Consume, a runtime error is reported. In the example, textThree has a default value defaultValue. Therefore, the initial value of textThree is defaultValue.
- The default value set for the attribute decorated with @Consume takes effect only when no matching result is found in the ancestor component.

### Using @Consume to Establish Two-Way Synchronization with @Provide Across BuilderNode Scenarios

> **NOTE**
>
> From API version 20, @Provide and @Consume can be paired across BuilderNodes.

@Provide and @Consume are supported by BuilderNodes. Note the following:
1. You need to set a default value for @Consume defined in the BuilderNode subtree, or ensure that @Provide exists in the subtree. Otherwise, a runtime error will occur.
2. After the BuilderNode is mounted to the tree, @Consume with a default value will search for @Provide upwards. After finding the nearest @Provide based on the key matching rule, @Consume will establish a bidirectional synchronization relationship with @Provide. If no matching @Provide is found, @Consume still uses the default value.
3. After the bidirectional synchronization relationship is established, if the value of the variable decorated with @Provide is different from the default value of @Consume, the @Watch method of @Consume and the @Watch method of the variable that has a synchronization relationship with @Consume are called back. For example, @Consume notifies @Link that is bidirectionally synchronized with @Consume to trigger the @Watch method.
4. After the BuilderNode is unmounted from the tree, @Consume attempts to search for the corresponding @Provide again. If @Consume cannot find the previously paired @Provide after being unmounted from the tree, the bidirectional synchronization relationship with @Provide is disconnected, and the variable decorated with @Consume is restored to the default value.
5. \@Consume disconnects from \@Provide and restores the default value. It checks whether the value of the \@Consume decoration variable changes from \@Provide to the default value of \@Consume. If the value changes, the \@Watch method of \@Consume and the variables that have synchronization relationships with \@Consume is called back.

In the following example:
1. Click add Child.
    - The child node Child under BuilderNode is constructed. \@Consume in Child does not find \@Provide and uses the local default value default value for initialization.
    - When BuilderNode is added to the tree, \@Consume in Child finds the nearest \@Provide in Index, updates the value of \@Consume from the default value to the value of \@Provide, and calls back the \@Watch method of \@Consume.
2. After \@Provide and \@Consume are paired, a bidirectional synchronization relationship is established. Click Text(`@Provide: ${this.message}`) and Text(`@Consume ${this.message}`). The Text components bound to \@Provide and \@Consume are refreshed, and the \@Watch methods of \@Provide and \@Consume are called back.
3. Click remove Child. The child node under BuilderNode is removed from the tree. \@Consume in Child is disconnected from \@Provide in Index, \@Consume in Child is restored to the default value, and the \@Watch method of \@Consume is called back.
4. Click dispose Child to release the child node under BuilderNode. The child node Child under BuilderNode is destroyed, and aboutToDisappear is executed.

```ts
import { NodeController, BuilderNode, FrameNode, UIContext } from '@kit.ArkUI';

@Builder
function buildText() {
  Column() {
    Child()
  }
}

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;
  private builderNode: BuilderNode<[]> | null = null;

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.uiContext = context;
    //Mount rootNode to NodeContainer.
    return this.rootNode;
  }

  addBuilderNode(): void {
    if (this.builderNode === null && this.uiContext && this.rootNode) {
      this.builderNode = new BuilderNode(this.uiContext);
      //Configure cross-BuilderNode @Provide/@Consume.
      this.builderNode.build(wrapBuilder(buildText), undefined,
        { enableProvideConsumeCrossing: true });
      //Mount the root node of BuilderNode to rootNode.
      this.rootNode.appendChild(this.builderNode.getFrameNode());
    }
  }

  removeBuilderNode(): void {
    if (this.rootNode && this.builderNode) {
      //Remove the BuildNode node from rootNode.
      this.rootNode.removeChild(this.builderNode.getFrameNode());
    }
  }

  disposeNode(): void {
    if (this.rootNode && this.builderNode) {
      //Release the current BuilderNode immediately.
      this.builderNode.dispose();
    }
  }
}

@Entry
@Component
struct Index {
  @Provide @Watch('onChange') message: string = 'hello';
  controller: TextNodeController = new TextNodeController();

  onChange() {
    console.info(`Index Provide change ${this.message}`);
  }

  build() {
    Column() {
      Text(`@Provide: ${this.message}`)
        .fontSize(20)
        .onClick(() => {
          this.message += ' Provide';
        })

      // Execute the build method of BuilderNode to construct the Child component.
      // Mount BuilderNode to NodeContainer.
      // @Consume in Child can be paired with @Provide in Index.
      // The message variable decorated with @Consume changes from the default value to hello, and the @Watch method decorated with @Consume is called back.
      Button('add Child')
        .onClick(() => {
          this.controller.addBuilderNode();
        })
      // Remove the nodes under BuilderNode from NodeContainer.
      // The message variable decorated with @Consume changes from the value paired with @Provide to the default value, and the @Watch method decorated with @Consume is called back.
      Button('remove Child')
        .onClick(() => {
          this.controller.removeBuilderNode();
        })

      // Release the current BuilderNode immediately. Nodes under BuilderNode are destroyed, and the Child component executes aboutToDisappear.
      Button('dispose Child')
        .onClick(() => {
          this.controller.disposeNode();
        })
      NodeContainer(this.controller)
        .width('100%')
        .height(100)
        .backgroundColor(Color.Pink)
    }
    .width('100%')
    .height('100%')
  }
}


@Component
struct Child {
  @Consume @Watch('onChange') message: string = 'default value';

  onChange() {
    console.info(`Child Consume change ${this.message}`);
  }

  aboutToDisappear(): void {
    console.info(`Child aboutToDisappear`);
  }

  build() {
    Column() {
      Text(`@Consume ${this.message}`)
        .fontSize(20)
        .onClick(() => {
          this.message += ' Consume';
        })
    }
  }
}
```

## Frequently Asked Questions

### \@Provide Not Defined Error in the Case of a \@BuilderParam Trailing Closure

In the scenario where @BuilderParam is followed by a closure (arkts-builderparam.md#initializing-a-component-using-a-closure), when CustomWidget executes this.builder() to create the child component CustomWidgetChild, this points to HomePage. As such, the \@Provide decorated variable of **CustomWidget** cannot be found, and an error is thrown. In light of this, exercise caution with **this** when using \@BuilderParam.

Incorrect example:

```ts
class Tmp {
  a: string = '';
}

@Entry
@Component
struct HomePage {
  // Error point 1: @Provide is not declared for HomePage.
  @Builder
  builder2($$: Tmp) {
    Text(`${$$.a}test`)
  }

  build() {
    Column() {
      // Error point 2: Use the closure to pass the function for creating CustomWidgetChild to CustomWidget. In this case, this in the closure points to HomePage.
      CustomWidget() {
        CustomWidgetChild({ builder: this.builder2 })
      }
    }
  }
}

@Component
struct CustomWidget {
  // Error point 3: The @Provide variable is declared in CustomWidget. Only CustomWidget and its child components can consume the variable.
  @Provide('a') a: string = 'abc';
  @BuilderParam
  builder: () => void;

  build() {
    Column() {
      Button('Hello').onClick(() => {
        if (this.a == 'ddd') {
          this.a = 'abc';
        }
        else {
          this.a = 'ddd';
        }

      })
      this.builder()
    }
  }
}

@Component
struct CustomWidgetChild {
  // Error point 4: Attempt to consume @Provide ('a') of CustomWidget. However, the parent component of CustomWidgetChild is HomePage, and the corresponding @Provide cannot be found.
  @Consume('a') a: string;
  @BuilderParam
  builder: ($$: Tmp) => void;

  build() {
    Column() {
      this.builder({ a: this.a })
    }
  }
}
```

[Correct Example]

```ts
class Tmp {
  name: string = '';
}

@Entry
@Component
struct HomePage {
  // Correction point 1: Declare @Provide in the Entry component (root scope) to ensure that child components can consume @Provide correctly.
  @Provide('name') name: string = 'abc';

  @Builder
  builder2($$: Tmp) {
    Text(`${$$.name} test`)
  }

  build() {
    Column() {
      Button('Hello').onClick(() => {
        if (this.name == 'ddd') {
          this.name = 'abc';
        } else {
          this.name = 'ddd';
        }
      })
      // Correction point 2: CustomWidget does not declare @Provide and only functions as a container to transfer builder.
      CustomWidget() {
        CustomWidgetChild({ builder: this.builder2 })
      }
    }
  }
}

@Component
struct CustomWidget {
  @BuilderParam
  builder: () => void;

  build() {
    this.builder()
  }
}

@Component
struct CustomWidgetChild {
  // Correction point 3: @Consume obtains @Provide ('name') from the root scope (HomePage). The scope is correct.
  @Consume('name') name: string;
  @BuilderParam
  builder: ($$: Tmp) => void;

  build() {
    Column() {
      this.builder({ name: this.name })
    }
  }
}
```

### Using the a.b(this.object) Pattern Fails to Trigger UI Re-rendering

In the **build** method, when the variable decorated by @Provide and @Consume is of the object type and is called using the **a.b(this.object)** format, the original object of **this.object** is passed in the b method. If the property of **this.object** is changed, the UI cannot be re-rendered. In the following example, the UI re-render is not triggered when **this.dog.age** and **this.dog.name** in the component is changed by using a static method or using **this** to call the internal method of the component.

**Incorrect Usage**

```ts
class Animal {
  name:string;
  type:string;
  age: number;

  constructor(name:string, type:string, age:number) {
    this.name = name;
    this.type = type;
    this.age = age;
  }

  static changeName(animal:Animal) {
    animal.name = 'Jack';
  }
  static changeAge(animal:Animal) {
    animal.age += 1;
  }
}

@Entry
@Component
struct Zoo {
  @Provide dog:Animal = new Animal('WangCai', 'dog', 2);

  changeZooDogAge(animal:Animal) {
    animal.age += 2;
  }

  build() {
    Column({ space:10 }) {
      Text(`Zoo: This is a ${this.dog.age}-year-old ${this.dog.type} named ${this.dog.name}.`)
        .fontColor(Color.Red)
        .fontSize(30)
      Button('changeAge')
        .onClick(()=>{
          // Static method calls will not trigger UI re-rendering.
          Animal.changeAge(this.dog);
        })
      Button('changeZooDogAge')
        .onClick(()=>{
          // Internal component method calls using this will not trigger UI re-rendering.
          this.changeZooDogAge(this.dog);
        })
      ZooChild()
    }
  }
}

@Component
struct ZooChild {

  build() {
    Column({ space:10 }) {
      Text(`ZooChild`)
        .fontColor(Color.Blue)
        .fontSize(30)
      ZooGrandChild()
    }
  }
}

@Component
struct ZooGrandChild {
  @Consume dog:Animal;

  changeZooGrandChildName(animal:Animal) {
    animal.name = 'Marry';
  }

  build() {
    Column({ space:10 }) {
      Text(`ZooGrandChild: This is a ${this.dog.age}-year-old ${this.dog.type} named ${this.dog.name}.`)
        .fontColor(Color.Yellow)
        .fontSize(30)
      Button('changeName')
        .onClick(()=>{
          // Static method calls will not trigger UI re-rendering.
          Animal.changeName(this.dog);
        })
      Button('changeZooGrandChildName')
        .onClick(()=>{
          // Internal component method calls using this will not trigger UI re-rendering.
          this.changeZooGrandChildName(this.dog);
        })
    }
  }
}
```

You can assign a value to this.dog and then invoke the variable to reserve the proxy for this.dog, implementing UI update.

**Correct Usage**

```ts
class Animal {
  name:string;
  type:string;
  age: number;

  constructor(name:string, type:string, age:number) {
    this.name = name;
    this.type = type;
    this.age = age;
  }

  static changeName(animal:Animal) {
    animal.name = 'Jack';
  }
  static changeAge(animal:Animal) {
    animal.age += 1;
  }
}

@Entry
@Component
struct Zoo {
  @Provide dog:Animal = new Animal('WangCai', 'dog', 2);

  changeZooDogAge(animal:Animal) {
    animal.age += 2;
  }

  build() {
    Column({ space:10 }) {
      Text(`Zoo: This is a ${this.dog.age}-year-old ${this.dog.type} named ${this.dog.name}.`)
        .fontColor(Color.Red)
        .fontSize(30)
      Button('changeAge')
        .onClick(()=>{
          //Retain the proxy by assigning a value to a temporary variable.
          let newDog = this.dog;
          Animal.changeAge(newDog);
        })
      Button('changeZooDogAge')
        .onClick(()=>{
          //Retain the proxy by assigning a value to a temporary variable.
          let newDog = this.dog;
          this.changeZooDogAge(newDog);
        })
      ZooChild()
    }
  }
}

@Component
struct ZooChild {

  build() {
    Column({ space:10 }) {
      Text(`ZooChild.`)
        .fontColor(Color.Blue)
        .fontSize(30)
      ZooGrandChild()
    }
  }
}

@Component
struct ZooGrandChild {
  @Consume dog:Animal;

  changeZooGrandChildName(animal:Animal) {
    animal.name = 'Marry';
  }

  build() {
    Column({ space:10 }) {
      Text(`ZooGrandChild: This is a ${this.dog.age}-year-old ${this.dog.type} named ${this.dog.name}.`)
        .fontColor(Color.Yellow)
        .fontSize(30)
      Button('changeName')
        .onClick(()=>{
          //Retain the proxy by assigning a value to a temporary variable.
          let newDog = this.dog;
          Animal.changeName(newDog);
        })
      Button('changeZooGrandChildName')
        .onClick(()=>{
          //Retain the proxy by assigning a value to a temporary variable.
          let newDog = this.dog;
          this.changeZooGrandChildName(newDog);
        })
    }
  }
}
```
