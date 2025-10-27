# \@Prop Decorator: One-Way Synchronization from the Parent Component to Child Components
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

One-way synchronization is supported between an \@Prop decorated variable a variable of its parent component.

Before reading this topic, you are advised to understand the basic usage of [\@State](./arkts-state.md). For best practices, see [State Management](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-status-management).

> **NOTE**
>
> This decorator can be used in ArkTS widgets since API version 9.
>
> This decorator can be used in atomic services since API version 11.

## Overview

Variables decorated by \@Prop have the following features:

- Variables decorated by \@Prop can be modified locally, but the modification is not synchronized to the parent component.

- Whenever the data source changes, the \@Prop decorated variable gets updated, and any locally made changes are overwritten.

## Usage Rules

| \@Prop Decorator| Description                                      |
| ----------- | ---------------------------------------- |
| Parameters      | None.                                       |
| Synchronization type       | One-way synchronization One-way: from the data source provided by the parent component to the \@Prop decorated variable.<br>For details about the scenarios of nested types, see [Observed Changes](#observed-changes).|
| Allowed variable types  |  Object, class, string, number, Boolean, enum, and array of these types.<br>API version 10 and later: [Date type](#decorating-variables-of-the-date-type).<br>API version 11 and later: [Map](#decorating-variables-of-the-map-type), [Set](#decorating-variables-of-the-set-type), undefined, null, union types defined by the ArkUI framework, for example, [Length](../../reference/apis-arkui/arkui-ts/ts-types.md#length), [ResourceStr](../../reference/apis-arkui/arkui-ts/ts-types.md#resourcestr), and [ResourceColor](../../reference/apis-arkui/arkui-ts/ts-types.md#resourcecolor). For details, see [Using Union Types](#using-union-types).<br>For details about the scenarios of supported types, see [Observed Changes](#observed-changes).|
| Disallowed variable types| Function.     |
| Number of nested layers       | In component reuse scenarios, it is recommended that @Prop be nested with no more than five layers of data. If @Prop is nested with too many layers of data, garbage collection and increased memory usage caused by deep copy will arise, resulting in performance issues. To avoid such issues, use [\@ObjectLink](arkts-observed-and-objectlink.md) instead.|
| Initial value for the decorated variable  | Local initialization is allowed. Since API version 11, if this decorator is used together with [\@Require](arkts-require.md), the parent component must pass parameters through its constructor.|


## Variable Transfer/Access Rules

| Transfer/Access         | Description                                                        |
| ------------------ | ------------------------------------------------------------ |
| Initialization from the parent component    | If initialization is performed locally, this operation is optional. The initialization behavior is the same as that in [\@State](./arkts-state.md#variable-transferaccess-rules). If local initialization cannot be performed, this operation is mandatory. An @Prop decorated variable can be initialized from a regular variable (whose change does not trigger UI re-render). or an [\@State](arkts-state.md), [\@Link](arkts-link.md), @Prop, [\@Provide](arkts-provide-and-consume.md), [\@Consume](arkts-provide-and-consume.md), [\@ObjectLink](arkts-observed-and-objectlink.md), [\@StorageLink](arkts-appstorage.md#storagelink), [\@StorageProp](arkts-appstorage.md#storageprop), [\@LocalStorageLink](arkts-localstorage.md#localstoragelink), or [\@LocalStorageProp](arkts-localstorage.md#localstorageprop) decorated variable in its parent component.|
|Child component initialization| \@Prop can be used for initialization of a regular variable or \@State, \@Link, \@Prop, or \@Provide decorated variable in the child component.|
| Access from outside the component| Private, accessible only within the component.                |

 The following figure shows the initialization rules.

![en-us_image_0000001552972029](figures/en-us_image_0000001552972029.png)

## Observed Changes and Behavior

### Observed Changes

\@Prop decorated variables can observe the following changes:

- When the supported type is decorated, the value change can be observed.

  ```ts
  // Simple type.
  @Prop count: number;
  // The value change can be observed.
  this.count = 1;
  // Complex type
  @Prop title: Model;
  // The value change can be observed.
  this.title = new Model('Hi');
  ```

- When decorating Object or class complex types, it can observe its own assignments and changes to first-level properties, where properties refer to all attributes returned by **object.keys(observedObject)**.

```ts
class Info {
  public value: string;
  constructor(value: string) {
    this.value = value;
  }
}
class Model {
  public value: string;
  public info: Info;
  constructor(value: string, info: Info) {
    this.value = value;
    this.info = info;
  }
}

@Prop title: Model;
// The value changes at the first layer can be observed.
this.title.value = 'Hi';
// The value changes at the second layer cannot be observed.
this.title.info.value = 'ArkUI';
```

In the scenarios of nested objects, if a class is decorated by \@Observed, the value changes of the class property can be observed. For details, see [Nesting \@Prop](#nesting-prop).

- When the decorated variable is of the array type, the value change of the array as well as the addition, deletion, and update of array items can be observed.

```ts
// Assume that the object decorated by @Prop is an array.
@Prop title: string[];
// The value change of the array itself can be observed.
this.title = ['1'];
// The value change of array items can be observed.
this.title[0] = '2';
// The deletion of array items can be observed.
this.title.pop();
// The addition of array items can be observed.
this.title.push('3');
```

For synchronization between \@State and \@Prop decorated variables:

- The value of an \@State decorated variable in the parent component is used to initialize an \@Prop decorated variable in the child component. Any change to an \@State decorated variable is updated to the @Prop decorated variable.
- However, any change to the @Prop decorated variable does not affect the value of its source @State decorated variable.
- In addition to \@State, the source can also be decorated with \@Link or \@Prop, where the mechanisms for syncing the \@Prop decorated variable is the same.
- The source and \@Prop decorated variable must be of the same type. The \@Prop decorated variable can be of simple and class types.

- When the decorated object is of the Date type, the following changes can be observed: (1) complete **Date** object reassignment; (2) property changes caused by calling **setFullYear**, **setMonth**, **setDate**, **setHours**, **setMinutes**, **setSeconds**, **setMilliseconds**, **setTime**, **setUTCFullYear**, **setUTCMonth**, **setUTCDate**, **setUTCHours**, **setUTCMinutes**, **setUTCSeconds**, or **setUTCMilliseconds**. For details, see [Decorating Variables of the Date Type](#decorating-variables-of-the-map-type).

- When the decorated object is of the **Map** type, the following changes can be observed: (1) complete **Map** object reassignment; (2) changes caused by calling **set**, **clear**, or **delete**. For details, see [Decorating Variables of the Map Type](#decorating-variables-of-the-map-type).

- When the decorated object is of the **Set** type, the following changes can be observed: (1) complete **Set** object reassignment; (2) changes caused by calling **add**, **clear**, or **delete**. For details, see [Decorating Variables of the Set Type](#decorating-variables-of-the-set-type).

### Framework Behavior

To understand the \@Prop variable value initialization and update mechanism, you need to understand the rendering and update processes of the parent and child components.

1. Initial rendering:
   1. Execute the build () function of the parent component to create a new instance of the child component and transfer the data source.
   2. The @Prop decorated variable is initialized.

2. Update
   1. When the \@Prop decorated variable is modified locally, the change does not propagate back to its parent component.
   2. When the data source of the parent component is updated, the \@Prop decorated variable in the child component is reset, and its local value changes are overwritten.

> **NOTE**
>
> \@Prop The data source synchronization depends on the update of the component where the data source is located. However, the update cannot be triggered after the application enters the background. Therefore, @Prop cannot be updated from the data source after the application enters the background. In this scenario, if real-time data synchronization is required, you are advised to use @Link instead.

In the following example, the Father component is refreshed when the message variable decorated by @State changes. The Son component uses @Prop to receive the variable. Therefore, the Father component uses the latest value of message to update the value of @Prop. After @Prop is updated, the Son component is updated.

```ts
@Component
struct Son {
  @Prop message: string = 'Hi';

  build() {
    Column() {
      Text(this.message)
    }
  }
}

@Entry
@Component
struct Father {
  @State message: string = 'Hello';

  build() {
    Column() {
      Text(this.message)
      Button(`father click`).onClick(() => {
        this.message += '*';
      })
      Son({ message: this.message })
    }
  }
}
```

## Constraints

- When decorating variables, \@Prop makes a deep copy, during which all types, except primitive types, Map, Set, Date, and Array, will be lost. For example, for complex types provided by N-API, such as [PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md), because they are partially implemented in the native code, complete data cannot be obtained through a deep copy in ArkTS.

## Use Scenarios

### Synchronizing from \@State to \@Prop Simple Data Types

In this example, the \@Prop decorated **count** variable in the **CountDownComponent** child component is initialized from the \@State decorated **countDownStartValue** variable in the **ParentComponent**. When **Try again** is touched, the value of the **count** variable is modified, but the change remains within the **CountDownComponent** and does not affect the **ParentComponent**.

Updating **countDownStartValue** in the **ParentComponent** will update the value of the @Prop decorated **count**.

```ts
@Component
struct CountDownComponent {
  @Prop count: number = 0;
  costOfOneAttempt: number = 1;

  build() {
    Column() {
      if (this.count > 0) {
        Text(`You have ${this.count} Nuggets left`)
      } else {
        Text('Game over!')
      }
      // Changes to the @Prop decorated variables are not synchronized to the parent component.
      Button(`Try again`).onClick(() => {
        this.count -= this.costOfOneAttempt;
      })
    }
  }
}

@Entry
@Component
struct ParentComponent {
  @State countDownStartValue: number = 10;

  build() {
    Column() {
      Text(`Grant ${this.countDownStartValue} nuggets to play.`)
      // Changes to the data source provided by the parent component are synchronized to the child component.
      Button(`+1 - Nuggets in New Game`).onClick(() => {
        this.countDownStartValue += 1;
      })
      // Updating the parent component will also update the child component.
      Button(`-1  - Nuggets in New Game`).onClick(() => {
        this.countDownStartValue -= 1;
      })

      CountDownComponent({ count: this.countDownStartValue, costOfOneAttempt: 2 })
    }
  }
}
```

In the preceding example:

1. On initial render, when the **CountDownComponent** child component is created, its \@Prop decorated **count** variable is initialized from the \@State decorated **countDownStartValue** variable in the **ParentComponent**.

2. When the "+1" or "-1" button is touched, the \@State decorated **countDownStartValue** of the **ParentComponent** changes. This will cause the **ParentComponent** to re-render. At the minimum, the **CountDownComponent** will be updated because of the change in the **count** variable value.

3. Because of the change in the **count** variable value, the **CountDownComponent** child component will re-render. At a minimum, the **if** statement's condition (**this.counter > 0**) is evaluated, and the **Text** child component inside the **if** statement would be updated.

4. When **Try again** in the **CountDownComponent** child component is touched, the value of the **count** variable is decorated, but the change remains within the child component and does not affect the **countDownStartValue** in the parent component.

5. Updating **countDownStartValue** will overwrite the local value changes of the @Prop decorated **count** in the **CountDownComponent** child component.

### Synchronizing from \@State Array Items to \@Prop Simple Data Types

If @State in the parent component decorates a variable of the array type, its array item can also initialize @Prop. In the following example, the \@State decorated array **arr** in the parent component **Index** initializes the \@Prop decorated **value** variable in the child component **Child**.

```ts
@Component
struct Child {
  @Prop value: number = 0;

  build() {
    Text(`${this.value}`)
      .fontSize(50)
      .onClick(() => {
        this.value++;
      })
  }
}

@Entry
@Component
struct Index {
  @State arr: number[] = [1, 2, 3];

  build() {
    Row() {
      Column() {
        Child({ value: this.arr[0] })
        Child({ value: this.arr[1] })
        Child({ value: this.arr[2] })

        Divider().height(5)

        ForEach(this.arr,
          (item: number) => {
            Child({ value: item })
          },
          (item: number) => item.toString()
        )
        Text('replace entire arr')
          .fontSize(50)
          .onClick(() => {
            // Both arrays contain item "3".
            this.arr = this.arr[0] == 1 ? [3, 4, 5] : [1, 2, 3];
          })
      }
    }
  }
}
```

Initial render creates six instances of the **Child** component. Each \@Prop decorated variable is initialized with a copy of an array item. The **onclick** event handler of the **Child** component changes the local variable value.

Click **1** six times, 2 five times, and **3** four times on the page. The local values of all variables are then changed to **7**.

```
7
7
7
——————
7
7
7
```

After **replace entire arr** is clicked, the following information is displayed:

```
3
4
5
——————
7
4
5
```

- Changes made in the **Child** component are not synchronized to the parent component **Index**. Therefore, even if the values of the six instances of the **Child** component are **7**, the value of **this.arr** in the **Index** component is still **[1,2,3]**.

- After **replace entire arr** is clicked, if **this.arr[0] == 1** is true, **this.arr** is set to **[3, 4, 5]**.

- Because **this.arr[0]** has been changed, the **Child({value: this.arr[0]})** component synchronizes the update of **this.arr[0]** to the instance's \@Prop decorated variable. The same happens for **Child({value: this.arr[1]})** and **Child({value: this.arr[2]})**.

- The change of **this.arr** causes **ForEach** to update: According to the diff algorithm, the array item with the ID **3** is retained in this update, array items with IDs **1** and **2** are deleted, and array items with IDs **4** and **5** are added. The array before and after the update is **[1, 2, 3]** and **[3, 4, 5]**, respectively. This implies that the **Child** instance generated for item **3** is moved to the first place, but not updated. In this case, the component value corresponding to **3** is **7**, and the final render result of **ForEach** is **7**, **4**, and **5**.

### Synchronizing from \@State Class Object Properties to \@Prop Simple Data Types

In a library with one book and two readers, each reader can mark the book as read, and the marking does not affect the other reader. Technically speaking, local changes to the \@Prop decorated **book** object do not sync back to the @State decorated **book** in the **Library** component.

In this example, the \@Observed decorator can be applied to the **book** class, but it is not mandatory. It is only needed for nested structures. This will be further explained in [Synchronizing from \@State Array Items to \@Prop Class Types](#synchronizing-from-state-array-items-to-prop-class-types).

```ts
class Book {
  public title: string;
  public pages: number;
  public readIt: boolean = false;

  constructor(title: string, pages: number) {
    this.title = title;
    this.pages = pages;
  }
}

@Component
struct ReaderComp {
  @Prop book: Book = new Book('', 0);

  build() {
    Row() {
      Text(this.book.title)
      Text(`...has${this.book.pages} pages!`)
      Text(`...${this.book.readIt ? 'I have read' : 'I have not read it'}`)
        .onClick(() => this.book.readIt = true)
    }
  }
}

@Entry
@Component
struct Library {
  @State book: Book = new Book('100 secrets of C++', 765);

  build() {
    Column() {
      ReaderComp({ book: this.book })
      ReaderComp({ book: this.book })
    }
  }
}
```

### Synchronizing from \@State Array Items to \@Prop Class Types

In the following example, the properties of the Book object in the allBooks array decorated by \@State are changed, but the UI update is not triggered when Mark read for everyone is clicked. This is because the property is nested at the second layer, and the \@State decorator can observe only properties at the first layer. Therefore, the framework does not update **ReaderComp**.

```ts
let nextId: number = 1;

// @Observed
class Book {
  public id: number;
  public title: string;
  public pages: number;
  public readIt: boolean = false;

  constructor(title: string, pages: number) {
    this.id = nextId++;
    this.title = title;
    this.pages = pages;
  }
}

@Component
struct ReaderComp {
  @Prop book: Book = new Book('', 1);

  build() {
    Row() {
      Text(` ${this.book ? this.book.title : 'Book is undefined'}`).fontColor('#e6000000')
      Text(` has ${this.book ? this.book.pages : 'Book is undefined'} pages!`).fontColor('#e6000000')
      Text(` ${this.book ? this.book.readIt ? 'I have read' : 'I have not read it' : 'Book is undefined'}`)
        .fontColor('#e6000000')
        .onClick(() => this.book.readIt = true)
    }
  }
}

@Entry
@Component
struct Library {
  @State allBooks: Book[] = [new Book('C#', 765), new Book('JS', 652), new Book('TS', 765)];

  build() {
    Column() {
      Text('library`s all time favorite')
        .width(312)
        .height(40)
        .backgroundColor('#0d000000')
        .borderRadius(20)
        .margin(12)
        .padding({ left: 20 })
        .fontColor('#e6000000')
      ReaderComp({ book: this.allBooks[2] })
        .backgroundColor('#0d000000')
        .width(312)
        .height(40)
        .padding({ left: 20, top: 10 })
        .borderRadius(20)
        .colorBlend('#e6000000')
      Text('Books on loan to a reader')
        .width(312)
        .height(40)
        .backgroundColor('#0d000000')
        .borderRadius(20)
        .margin(12)
        .padding({ left: 20 })
        .fontColor('#e6000000')
      ForEach(this.allBooks, (book: Book) => {
        ReaderComp({ book: book })
          .margin(12)
          .width(312)
          .height(40)
          .padding({ left: 20, top: 10 })
          .backgroundColor('#0d000000')
          .borderRadius(20)
      },
        (book: Book) => book.id.toString())
      Button('Add new')
        .width(312)
        .height(40)
        .margin(12)
        .fontColor('#FFFFFF')
        .onClick(() => {
          this.allBooks.push(new Book('JA', 512));
        })
      Button('Remove first book')
        .width(312)
        .height(40)
        .margin(12)
        .fontColor('#FFFFFF')
        .onClick(() => {
          if (this.allBooks.length > 0) {
            this.allBooks.shift();
          } else {
            console.info('length <= 0');
          }
        })
      Button('Mark read for everyone')
        .width(312)
        .height(40)
        .margin(12)
        .fontColor('#FFFFFF')
        .onClick(() => {
          this.allBooks.forEach((book) => book.readIt = true)
        })
    }
  }
}
```

Use \@Observed to decorate a class book. The property changes of the book will be observed. Note that the \@Prop decorated state variable in the child component is synchronized from the data source of the parent component in uni-directional manner. This means that, the changes of the \@Prop decorated **book** in **ReaderComp** are not synchronized to the parent **library** component. The parent component triggers UI re-rendering only when the state variable changes.

```ts
@Observed
class Book {
  public id: number;
  public title: string;
  public pages: number;
  public readIt: boolean = false;

  constructor(title: string, pages: number) {
    this.id = nextId++;
    this.title = title;
    this.pages = pages;
  }
}
```

All instances of the \@Observed decorated class are wrapped with an opaque proxy object. This proxy can detect all property changes inside the wrapped object. If any property change happens, the proxy notifies the \@Prop, and the \@Prop value will be updated.

![Video-prop-UsageScenario-one](figures/Video-prop-UsageScenario-one.gif)

### Initializing \@Prop Locally Without Synchronizing with Parent Components

To enable an \@Component decorated component to be reusable, \@Prop allows for optional local initialization. This makes the synchronization with a variable in the parent component a choice, rather than mandatory. Providing a data source in the parent component is optional only when local initialization is provided for the \@Prop decorated variable.

The following example includes two @Prop decorated variables in the child component.

- **customCounter** is not initialized locally. Therefore, the parent component needs to provide the data source to deinitialize \@Prop. When the data source of the parent component changes, \@Prop is updated.

- **customCounter2** has local initialization. In this case, specifying a synchronization source in the parent component is allowed but not mandatory.

```ts
@Component
struct MyComponent {
  @Prop customCounter: number;
  @Prop customCounter2: number = 5;

  build() {
    Column() {
      Row() {
        Text(`From Main: ${this.customCounter}`).fontColor('#ff6b6565').margin({ left: -110, top: 12 })
      }

      Row() {
        Button('Click to change locally!')
          .width(288)
          .height(40)
          .margin({ left: 30, top: 12 })
          .fontColor('#FFFFFF')
          .onClick(() => {
            this.customCounter2++;
          })
      }

      Row() {
        Text(`Custom Local: ${this.customCounter2}`).fontColor('#ff6b6565').margin({ left: -110, top: 12 })
      }
    }
  }
}

@Entry
@Component
struct MainProgram {
  @State mainCounter: number = 10;

  build() {
    Column() {
      Row() {
        Column() {
          // customCounter must be initialized from the parent component due to lack of local initialization. Here, customCounter2 does not need to be initialized.
          MyComponent({ customCounter: this.mainCounter })
          // customCounter2 of the child component can also be initialized from the parent component. The value from the parent component overwrites the locally assigned value of customCounter2 during initialization.
          MyComponent({ customCounter: this.mainCounter, customCounter2: this.mainCounter })
        }
      }

      Row() {
        Column() {
          Button('Click to change number')
            .width(288)
            .height(40)
            .margin({ left: 30, top: 12 })
            .fontColor('#FFFFFF')
            .onClick(() => {
              this.mainCounter++;
            })
        }
      }
    }
  }
}
```

![Video-prop-UsageScenario-two](figures/Video-prop-UsageScenario-two.gif)

### Nesting \@Prop

In nesting scenario, each layer must be decorated with @Observed, and each layer must be received by @Prop. In this way, changes can be observed.

```ts
// The following is the data structure of a nested class object.
@Observed
class Son {
  public title: string;

  constructor(title: string) {
    this.title = title;
  }
}

@Observed
class Father {
  public name: string;
  public son: Son;

  constructor(name: string, son: Son) {
    this.name = name;
    this.son = son;
  }
}
```

The following component hierarchy shows the data structure in the \@Prop nesting scenario.

```ts
@Entry
@Component
struct Person {
  @State person: Father = new Father('Hello', new Son('world'));

  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
        Button('change Father name')
          .width(312)
          .height(40)
          .margin(12)
          .fontColor('#FFFFFF')
          .onClick(() => {
            this.person.name = 'Hi';
          })
        Button('change Son title')
          .width(312)
          .height(40)
          .margin(12)
          .fontColor('#FFFFFF')
          .onClick(() => {
            this.person.son.title = 'ArkUI';
          })
        Text(this.person.name)
          .fontSize(16)
          .margin(12)
          .width(312)
          .height(40)
          .backgroundColor('#ededed')
          .borderRadius(20)
          .textAlign(TextAlign.Center)
          .fontColor('#e6000000')
          .onClick(() => {
            this.person.name = 'Bye';
          })
        Text(this.person.son.title)
          .fontSize(16)
          .margin(12)
          .width(312)
          .height(40)
          .backgroundColor('#ededed')
          .borderRadius(20)
          .textAlign(TextAlign.Center)
          .onClick(() => {
            this.person.son.title = 'openHarmony';
          })
        Child({ child: this.person.son })
      }
    }
  }
}


@Component
struct Child {
  @Prop child: Son = new Son('');

  build() {
    Column() {
      Text(this.child.title)
        .fontSize(16)
        .margin(12)
        .width(312)
        .height(40)
        .backgroundColor('#ededed')
        .borderRadius(20)
        .textAlign(TextAlign.Center)
        .onClick(() => {
          this.child.title = 'Bye Bye';
        })
    }
  }
}
```

![Video-prop-UsageScenario-three](figures/Video-prop-UsageScenario-three.gif)

### Decorating Variables of the Map Type

> **NOTE**
>
> Since API version 11, \@Prop supports the Map type.

In this example, the **value** variable is of the Map\<number, string\> type. When the button is clicked, the value of **message** changes, and the UI is re-rendered.

```ts
@Component
struct Child {
  @Prop value: Map<number, string> = new Map([[0, 'a'], [1, 'b'], [3, 'c']]);

  build() {
    Column() {
      ForEach(Array.from(this.value.entries()), (item: [number, string]) => {
        Text(`${item[0]}`).fontSize(30)
        Text(`${item[1]}`).fontSize(30)
        Divider()
      })
      Button('child init map').onClick(() => {
        this.value = new Map([[0, 'a'], [1, 'b'], [3, 'c']]);
      })
      Button('child set new one').onClick(() => {
        this.value.set(4, 'd');
      })
      Button('child clear').onClick(() => {
        this.value.clear();
      })
      Button('child replace the first one').onClick(() => {
        this.value.set(0, 'aa');
      })
      Button('child delete the first one').onClick(() => {
        this.value.delete(0);
      })
    }
  }
}


@Entry
@Component
struct MapSample {
  @State message: Map<number, string> = new Map([[0, 'a'], [1, 'b'], [3, 'c']]);

  build() {
    Row() {
      Column() {
        Child({ value: this.message })
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
> Since API version 11, \@Prop supports the Set type.

In this example, the **message** variable is of the **Set\<number\>** type. When the button is clicked, the value of **message** changes, and the UI is re-rendered.

```ts
@Component
struct Child {
  @Prop message: Set<number> = new Set([0, 1, 2, 3, 4]);

  build() {
    Column() {
      ForEach(Array.from(this.message.entries()), (item: [number, number]) => {
        Text(`${item[0]}`).fontSize(30)
        Divider()
      })
      Button('init set').onClick(() => {
        this.message = new Set([0, 1, 2, 3, 4]);
      })
      Button('set new one').onClick(() => {
        this.message.add(5);
      })
      Button('clear').onClick(() => {
        this.message.clear();
      })
      Button('delete the first one').onClick(() => {
        this.message.delete(0);
      })
    }
    .width('100%')
  }
}


@Entry
@Component
struct SetSample {
  @State message: Set<number> = new Set([0, 1, 2, 3, 4]);

  build() {
    Row() {
      Column() {
        Child({ message: this.message })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### Decorating Variables of the Date Type

In this example, the **selectedDate** variable is of the Date type. After the button is clicked, the value of **selectedDate** changes, and the UI is re-rendered.

```ts
@Component
struct DateComponent {
  @Prop selectedDate: Date = new Date('');

  build() {
    Column() {
      Button('child update the new date')
        .margin(10)
        .onClick(() => {
          this.selectedDate = new Date('2023-09-09');
        })
      Button(`child increase the year by 1`).onClick(() => {
        this.selectedDate.setFullYear(this.selectedDate.getFullYear() + 1);
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
struct ParentComponent {
  @State parentSelectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      Button('parent update the new date')
        .margin(10)
        .onClick(() => {
          this.parentSelectedDate = new Date('2023-07-07');
        })
      Button('parent increase the day by 1')
        .margin(10)
        .onClick(() => {
          this.parentSelectedDate.setDate(this.parentSelectedDate.getDate() + 1);
        })
      DatePicker({
        start: new Date('1970-1-1'),
        end: new Date('2100-1-1'),
        selected: this.parentSelectedDate
      })

      DateComponent({ selectedDate: this.parentSelectedDate })
    }

  }
}
```

### Using Union Types

@Prop supports **undefined**, **null**, and union types. In the following example, the type of **animal** is **Animals | undefined**. If the property or type of **animal** is changed when the button in the parent component **Zoo** is clicked, the change will be synced to the child component.

```ts
class Animals {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }
}

@Component
struct Child {
  @Prop animal: Animals | undefined;

  build() {
    Column() {
      Text(`Child's animal is  ${this.animal instanceof Animals ? this.animal.name : 'undefined'}`).fontSize(30)

      Button('Child change animals into tigers')
        .onClick(() => {
          // Assign the value of an instance of Animals.
          this.animal = new Animals('Tiger');
        })

      Button('Child change animal to undefined')
        .onClick(() => {
          // Assign the value undefined.
          this.animal = undefined;
        })

    }.width('100%')
  }
}

@Entry
@Component
struct Zoo {
  @State animal: Animals | undefined = new Animals('lion');

  build() {
    Column() {
      Text(`Parents' animals are  ${this.animal instanceof Animals ? this.animal.name : 'undefined'}`).fontSize(30)

      Child({animal: this.animal})

      Button('Parents change animals into dogs')
        .onClick(() => {
          // Determine the animal type and update the property.
          if (this.animal instanceof Animals) {
            this.animal.name = 'Dog';
          } else {
            console.info('num is undefined, cannot change property');
          }
        })

      Button('Parents change animal to undefined')
        .onClick(() => {
          // Assign the value undefined.
          this.animal = undefined;
        })
    }
  }
}
```

## FAQs

### \@Prop Decorated State Variable Not Initialized

The \@Prop decorated state variable must be initialized. If not initialized locally, the variable must be initialized from the parent component. If it has been initialized locally, initialization from the parent component is optional.

**Incorrect Usage**

```ts
@Observed
class Commodity {
  public price: number = 0;

  constructor(price: number) {
    this.price = price;
  }
}

@Component
struct PropChild {
  @Prop fruit: Commodity; // The state variable is not initialized locally.

  build() {
    Text(`PropChild fruit ${this.fruit.price}`)
      .onClick(() => {
        this.fruit.price += 1;
      })
  }
}

@Entry
@Component
struct Parent {
  @State fruit: Commodity[] = [new Commodity(1)];

  build() {
    Column() {
      Text(`Parent fruit ${this.fruit[0].price}`)
        .onClick(() => {
          this.fruit[0].price += 1;
        })

      // The @Prop state variable is not initialized locally, nor initialized from the parent component.
      PropChild()
    }
  }
}
```

**Correct Usage**

```ts
@Observed
class Commodity {
  public price: number = 0;

  constructor(price: number) {
    this.price = price;
  }
}

@Component
struct PropChild1 {
  @Prop fruit: Commodity; // The state variable is not initialized locally.

  build() {
    Text(`PropChild1 fruit ${this.fruit.price}`)
      .onClick(() => {
        this.fruit.price += 1;
      })
  }
}

@Component
struct PropChild2 {
  @Prop fruit: Commodity = new Commodity(1); // The state variable is initialized locally.

  build() {
    Text(`PropChild2 fruit ${this.fruit.price}`)
      .onClick(() => {
        this.fruit.price += 1;
      })
  }
}

@Entry
@Component
struct Parent {
  @State fruit: Commodity[] = [new Commodity(1)];

  build() {
    Column() {
      Text(`Parent fruit ${this.fruit[0].price}`)
        .onClick(() => {
          this.fruit[0].price += 1;
        })

      // @PropChild1 is not initialized locally and must be initialized from the parent component.
      PropChild1({ fruit: this.fruit[0] })
      // @PropChild2 is initialized locally. In this case, initialization from the parent component is optional.
      PropChild2()
      PropChild2({ fruit: this.fruit[0] })
    }
  }
}
```

### Using the a.b(this.object) Pattern Fails to Trigger UI Re-rendering

In the **build** method, when the variable decorated by @Prop is of the object type and is called using the **a.b(this.object)** format, the original object of **this.object** is passed in the b method. If the property of **this.object** is changed, the UI cannot be re-rendered. In the following example, when the static method **Score.changeScore1** or **this.changeScore2** is used to change **this.score.value** in the custom component **Child**, the UI is not re-rendered.

**Incorrect Usage**

```ts
class Score {
  value: number;
  constructor(value: number) {
    this.value = value;
  }

  static changeScore1(param1:Score) {
    param1.value += 1;
  }
}

@Entry
@Component
struct Parent {
  @State score: Score = new Score(1);

  build() {
    Column({space:8}) {
      Text(`The value in Parent is ${this.score.value}.`)
        .fontSize(30)
        .fontColor(Color.Red)
      Child({ score: this.score })
    }
    .width('100%')
    .height('100%')
  }
}

@Component
struct Child {
  @Prop score: Score;

  changeScore2(param2:Score) {
    param2.value += 2;
  }

  build() {
    Column({space:8}) {
      Text(`The value in Child is ${this.score.value}.`)
        .fontSize(30)
      Button(`changeScore1`)
        .onClick(()=>{
          // Static method calls will not trigger UI re-rendering.
          Score.changeScore1(this.score);
        })
      Button(`changeScore2`)
        .onClick(()=>{
          // Internal component method calls using this will not trigger UI re-rendering.
          this.changeScore2(this.score);
        })
    }
  }
}
```

You can add a proxy for **this.score** to re-render the UI by assigning a value to the variable and then calling the variable.

**Correct Usage**

```ts
class Score {
  value: number;
  constructor(value: number) {
    this.value = value;
  }

  static changeScore1(score:Score) {
    score.value += 1;
  }
}

@Entry
@Component
struct Parent {
  @State score: Score = new Score(1);

  build() {
    Column({space:8}) {
      Text(`The value in Parent is ${this.score.value}.`)
        .fontSize(30)
        .fontColor(Color.Red)
      Child({ score: this.score })
    }
    .width('100%')
    .height('100%')
  }
}

@Component
struct Child {
  @Prop score: Score;

  changeScore2(score:Score) {
    score.value += 2;
  }

  build() {
    Column({space:8}) {
      Text(`The value in Child is ${this.score.value}.`)
        .fontSize(30)
      Button(`changeScore1`)
        .onClick(()=>{
          // Add a proxy by assigning a value.
          let score1 = this.score;
          Score.changeScore1(score1);
        })
      Button(`changeScore2`)
        .onClick(()=>{
          // Add a proxy by assigning a value.
          let score2 = this.score;
          this.changeScore2(score2);
        })
    }
  }
}
```
<!--no_check-->
