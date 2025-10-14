# \@State Decorator: State Owned by Component
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

A variable decorated by the state variable decorator is called a state variable, which enables common variables to have state attributes. When a state variable changes, the UI component directly bound to it is rendered and updated.

Among the decorators related to state variables, @State is the most basic decorator and is the data source of most state variables.

Before reading this topic, you are advised to read [State Management Overview](./arkts-state-management-overview.md) to have a basic understanding of the positioning of AppStorage in the state management framework. For best practices, see [State Management](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-status-management).

> **NOTE**
>
> This decorator can be used in ArkTS widgets since API version 9.
>
> This decorator can be used in atomic services since API version 11.

## **Overview**

A variable decorated by \@State is private and can be accessed only from the component. The type of the variable must be specified and initialized locally when the variable is declared. If the variable needs to be initialized from the parent component, you can use the named parameter mechanism to assign a value to the variable.

A variable decorated by \@State has the following features:

- The lifecycle of the \@State decorated variable is the same as that of its owning custom component.

## Usage Rules

| \@State Decorator | Description                                                        |
| ------------------ | ------------------------------------------------------------ |
| Parameters        | None                                                          |
| Synchronization type          | Does not synchronize with any type of variable in the parent component.                            |
| Allowed variable types| Object, class, string, number, Boolean, enum, and array of these types.<br>API version 10 and later: [Date type](#decorating-variables-of-the-date-type).<br>API version 11 and later: [Map](#decorating-variables-of-the-map-type), [Set](#decorating-variables-of-the-set-type), undefined, null, union types defined by the ArkUI framework, for example, [Length](../../reference/apis-arkui/arkui-ts/ts-types.md#length), [ResourceStr](../../reference/apis-arkui/arkui-ts/ts-types.md#resourcestr), and [ResourceColor](../../reference/apis-arkui/arkui-ts/ts-types.md#resourcecolor). For details, see [Using Union Types](#using-union-types).<br>For details about the scenarios where types are supported, see [Observed Changes](#observed-changes).|
| Disallowed variable types| Function.     |
| Initial value for the decorated variable| Required.     |

## Variable Transfer/Access Rules

| Transfer/Access         | Description                                                        |
| ------------------ | ------------------------------------------------------------ |
| Initialization from the parent component    | Can be initialized from the parent component or locally.<br>If the parent component passes a non-undefined value, the local initial value is overwritten. Otherwise, the local initial value of @State is used.<br>Common variables in the parent component and state variables decorated with decorators: \@State, [\@Link](arkts-link.md), [\@Prop](arkts-prop.md), [\@Provide](arkts-provide-and-consume.md), [\@Consume](arkts-provide-and-consume.md), [\@ObjectLink](arkts-observed-and-objectlink.md), [\@StorageLink](arkts-appstorage.md#storagelink), [\@StorageProp](arkts-appstorage.md#storageprop), [\@LocalStorageLink](arkts-localstorage.md#localstoragelink), and [\@LocalStorageProp](arkts-localstorage.md#localstorageprop) can be used to initialize @State. Note: When the external variable passed by the parent component is used to initialize \@State, it is used only as the initial value. Subsequent variable changes will not be synchronized to \@State.|
| Child component initialization  | Supported. An \@State decorated variable can be used to initialize a regular variable or \@State, \@Link, \@Prop, or \@Provide decorated variable in the child component.|
| Access from outside the component| Private, accessible only within the component.                                  |

  **Figure 1** Initialization rule

![en-us_image_0000001502091796](figures/en-us_image_0000001502091796.png)

## Observed Changes and Behavior

Not all changes to state variables cause UI updates. Only changes that can be observed by the framework do. This section describes what changes can be observed and how the framework triggers UI re-renders after the changes are observed, that is, how the framework behaves.

### Observed Changes

- When the decorated variable is of the Boolean, string, or number type, its value change can be observed.

  ```ts
  // Simple type.
  @State count: number = 0;
  // The value change can be observed.
  this.count = 1;
  ```

- When the decorated data type is class or Object, the value assignment and attribute assignment changes of the decorated data type can be observed, that is, all attributes returned by Object.keys(observedObject). Example:
  
  Declare the **Person** and **Model** classes.

  ```ts
  class Person {
    public value: string;
  
    constructor(value: string) {
      this.value = value;
    }
  }
  
  class Model {
    public value: string;
    public name: Person;
    constructor(value: string, person: Person) {
      this.value = value;
      this.name = person;
    }
  }
  ```

  \@State The decorative type is Model.

  ```ts
  // Class type
  @State title: Model = new Model('Hello', new Person('World'));
  ```

  Assign a value to the \@State decorated variable.

  ```ts
  // Assign a value to the class object.
  this.title = new Model('Hi', new Person('ArkUI'));
  ```

  Assign a value to a property of the \@State decorated variable.

  ```ts
  // Assign a value to a property of the class object.
  this.title.value = 'Hi';
  ```

  The value assignment of the nested property cannot be observed.

  ```ts
  // The value assignment of the nested property cannot be observed.
  this.title.name.value = 'ArkUI';
  ```
- When the decorated variable is of the array type, the addition, deletion, and updates of array items can be observed. Example:
  Declare the **Model** class.

  ```ts
  class Model {
    public value: number;
    constructor(value: number) {
      this.value = value;
    }
  }
  ```

  Use \@State to decorate a variable of the Model class array type.

  ```ts
  // Array type
  @State title: Model[] = [new Model(11), new Model(1)];
  ```

  The value assignment of the array itself can be observed.

  ```ts
  // Value assignment of the array
  this.title = [new Model(2)];
  ```

  The value assignment of array items can be observed.

  ```ts
  // Value assignment of an array item
  this.title[0] = new Model(2);
  ```

  The deletion of array items can be observed.

  ```ts
  // Array item change
  this.title.pop();
  ```

  The addition of array items can be observed.

  ```ts
  // Array item change
  this.title.push(new Model(12));
  ```

  The property value assignment in the array items cannot be observed.

  ```ts
  // The value assignment of the nested property cannot be observed.
  this.title[0].value = 6;
  ```

- When the decorated object is a Date, you can observe the assignment of Date and update the properties of Date by calling the setFullYear, setMonth, setDate, setHours, setMinutes, setSeconds, setMilliseconds, setTime, setUTCFullYear, setUTCMonth, setUTCDate, setUTCHours, setUTCMinutes, setUTCSeconds, setUTCMilliseconds interface of Date. For details, see [Decorating Variables of the Date Type](#decorating-variables-of-the-date-type).

- When the decorated object is of the **Map** type, the following changes can be observed: (1) complete **Map** object reassignment; (2) changes caused by calling **set**, **clear**, or **delete**. For details, see [Decorating Variables of the Map Type](#decorating-variables-of-the-map-type).

- When the decorated object is of the **Set** type, the following changes can be observed: (1) complete **Set** object reassignment; (2) changes caused by calling **add**, **clear**, or **delete**. For details, see [Decorating Variables of the Set Type](#decorating-variables-of-the-set-type).

### Framework Behavior

- When a state variable is changed, the framework searches for components that depend on this state variable.

- Execute the component update method that depends on the state variable to implement component update and rendering.

## Constraints

1. Variables decorated by \@State must be initialized. Otherwise, an error is reported during compilation.

    ```ts	
    // Incorrect usage. An error is reported during compilation.
    @State count: number;
    
    // Correct usage.
    @State count: number = 10;
    ```

2. \@State cannot decorate variables of the function type. Otherwise, the framework throws a runtime error.

## Use Cases

### Decorating Variables of Simple Types

In this example, \@State is used to decorate the **count** variable of the simple type, turning it into a state variable. The change of **count** causes the update of the **Button** component.

- When the state variable count changes, only the Button component can be queried.

- The framework executes the update method of the **Button** component to implement on-demand update.

```ts
@Entry
@Component
struct MyComponent {
  @State count: number = 0;

  build() {
    Button(`click times: ${this.count}`)
      .onClick(() => {
        this.count += 1;
      })
  }
}
```


### Decorating Variables of the Class Object Type

- In this example, \@State is used to decorate the variables **count** and **title** in the custom component **MyComponent**. The type of **title** is **Model**, a custom class. If the value of **count** or **title** changes, the framework searches for all **MyComponent** instances that depend on these variables and triggers re-rendering of them.

- The **EntryComponent** has multiple **MyComponent** instances. The internal state change of the first **MyComponent** instance does not affect the second **MyComponent** instance.

```ts
class Model {
  public value: string;

  constructor(value: string) {
    this.value = value;
  }
}

@Entry
@Component
struct EntryComponent {
  build() {
    Column() {
      // The parameters specified here will overwrite the default values defined locally during initial render. Not all parameters need to be initialized from the parent component.
      MyComponent({ count: 1, increaseBy: 2 })
        .width(300)
      MyComponent({ title: new Model('Hello World 2'), count: 7 })
    }
  }
}

@Component
struct MyComponent {
  @State title: Model = new Model('Hello World');
  @State count: number = 0;
  increaseBy: number = 1;

  build() {
    Column() {
      Text(`${this.title.value}`)
        .margin(10)
      Button(`Click to change title`)
        .onClick(() => {
          // The update of the @State decorated variable triggers the update of the <Text> component.
          this.title.value = this.title.value === 'Hello ArkUI' ? 'Hello World' : 'Hello ArkUI';
        })
        .width(300)
        .margin(10)

      Button(`Click to increase count = ${this.count}`)
        .onClick(() => {
          // The update of the @State decorated variable triggers the update of the <Button> component.
          this.count += this.increaseBy;
        })
        .width(300)
        .margin(10)
    }
  }
}
```

![Video-state](figures/Video-state.gif)

In the preceding example, the initialization mechanism of the \@State variable is as follows:

1. If no value is passed from the external, the default value is used for local initialization.

   ```ts
   // No external value is passed to title. Use the local value new Model('Hello World') for initialization.
   MyComponent({ count: 1, increaseBy: 2 })
   // No external value is passed to increaseBy. Use the local value 1 for initialization.
   MyComponent({ title: new Model('Hello World 2'), count: 7 })
   ```

2. If a value is passed from the external, use this value for initialization.

   ```ts
   // Used 1 and 2 passed from the external to initialize count and increaseBy.
   MyComponent({ count: 1, increaseBy: 2 })
   // Used new Model('Hello World 2') and 7 passed from the external to initialize title and count.
   MyComponent({ title: new Model('Hello World 2'), count: 7 })
   ```

### Decorating Variables of the Map Type

> **NOTE**
>
> Since API version 11, \@State supports the Map type.

In this example, the **message** variable is of the Map<number, string> type. When the button is clicked, the value of **message** changes, and the UI is re-rendered.

```ts
@Entry
@Component
struct MapSample {
  @State message: Map<number, string> = new Map([[0, 'a'], [1, 'b'], [3, 'c']]);

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.message.entries()), (item: [number, string]) => {
          Text(`${item[0]}`).fontSize(30)
          Text(`${item[1]}`).fontSize(30)
          Divider()
        })
        Button('init map').onClick(() => {
          this.message = new Map([[0, 'a'], [1, 'b'], [3, 'c']]);
        })
        Button('set new one').onClick(() => {
          this.message.set(4, 'd');
        })
        Button('clear').onClick(() => {
          this.message.clear();
        })
        Button('replace the first one').onClick(() => {
          this.message.set(0, 'aa');
        })
        Button('delete the first one').onClick(() => {
          this.message.delete(0);
        })
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
> Since API version 11, \@State supports the Set type.

In this example, the **message** variable is of the **Set\<number\>** type. When the button is clicked, the value of **message** changes, and the UI is re-rendered.

```ts
@Entry
@Component
struct SetSample {
  @State message: Set<number> = new Set([0, 1, 2, 3, 4]);

  build() {
    Row() {
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
    .height('100%')
  }
}
```

### Decorating Variables of the Date Type

In this example, the **selectedDate** variable is of the Date type. After the button is clicked, the value of **selectedDate** changes, and the UI is re-rendered.

```ts
  @Entry
  @Component
  struct DatePickerExample {
    @State selectedDate: Date = new Date('2021-08-08');
  
    build() {
      Column() {
        Button('set selectedDate to 2023-07-08')
          .margin(10)
          .onClick(() => {
            this.selectedDate = new Date('2023-07-08');
          })
        Button('increase the year by 1')
          .margin(10)
          .onClick(() => {
            this.selectedDate.setFullYear(this.selectedDate.getFullYear() + 1);
          })
        Button('increase the month by 1')
          .margin(10)
          .onClick(() => {
            this.selectedDate.setMonth(this.selectedDate.getMonth() + 1);
          })
        Button('increase the day by 1')
          .margin(10)
          .onClick(() => {
            this.selectedDate.setDate(this.selectedDate.getDate() + 1);
          })
        DatePicker({
          start: new Date('1970-1-1'),
          end: new Date('2100-1-1'),
          selected: this.selectedDate
        })
      }.width('100%')
    }
  }
```


### Using Union Types

\@State supports **undefined**, **null**, and union types. In the following example, the type of **count** is **number | undefined**. If the property or type of **count** is changed when the button is clicked, the change will be synced to the view.

```ts
@Entry
@Component
struct EntryComponent {
  build() {
    Column() {
      MyComponent()
    }
  }
}

@Component
struct MyComponent {
  @State count: number | undefined = 0;

  build() {
    Column() {
      Text(`count(${this.count})`)
      Button('change')
        .onClick(() => {
          this.count = undefined;
        })
    }
  }
}
```


## FAQs

### Failure to Change a State Variable Using an Arrow Function

The **this** object inside the arrow function's body is established based on the scope where the arrow function is defined points, not the scope where the arrow function is executed. As such, **this** of **changeCoverUrl** points to **PlayDetailViewModel** instead of the state variable decorated by \@State.

**Incorrect Usage**

```ts

export default class PlayDetailViewModel {
  coverUrl: string = '#00ff00';

  changeCoverUrl= ()=> {
    this.coverUrl = '#00F5FF';
  }

}
```

```ts
import PlayDetailViewModel from './PlayDetailViewModel';

@Entry
@Component
struct PlayDetailPage {
  @State vm: PlayDetailViewModel = new PlayDetailViewModel();

  build() {
    Stack() {
      Text(this.vm.coverUrl).width(100).height(100).backgroundColor(this.vm.coverUrl)
      Row() {
        Button('Change Color')
          .onClick(() => {
            this.vm.changeCoverUrl();
          })
      }
    }
    .width('100%')
    .height('100%')
    .alignContent(Alignment.Top)
  }
}
```

Pass the current this.vm and invoke the attribute value assignment of the proxy state variable.

**Correct Usage**

```ts

export default class PlayDetailViewModel {
  coverUrl: string = '#00ff00';

  changeCoverUrl= (model:PlayDetailViewModel)=> {
    model.coverUrl = '#00F5FF';
  }

}
```

```ts
import PlayDetailViewModel from './PlayDetailViewModel';

@Entry
@Component
struct PlayDetailPage {
  @State vm: PlayDetailViewModel = new PlayDetailViewModel();

  build() {
    Stack() {
      Text(this.vm.coverUrl).width(100).height(100).backgroundColor(this.vm.coverUrl)
      Row() {
        Button('Change Color')
          .onClick(() => {
            let self = this.vm;
            this.vm.changeCoverUrl(self);
          })
      }
    }
    .width('100%')
    .height('100%')
    .alignContent(Alignment.Top)
  }
}
```

### Capturing this in constructor() Fails to Observe Variable Changes

In state management, classes are wrapped with a proxy. When a member variable of a class is changed in a component, the proxy intercepts the change. When the value in the data source is changed, the proxy notifies the bound component of the change. In this way, the change can be observed and trigger UI re-rendering.

When the arrow function for modifying success is initialized in the constructor, the TestModel instance is not encapsulated by the proxy, and this points to the TestModel instance itself. Therefore, when the query event is triggered, the state management cannot observe the change.

When you place the arrow function for modifying success in query, the TestModel object has been initialized and encapsulated by the proxy. Call **this.viewModel.query()** and **this** in the function points to the **viewModel** object. In this case, the change of **isSuccess** is observable, so that the change of the query event can be observed by the state management.

**Incorrect Usage**

```ts
@Entry
@Component
struct Index {
  @State viewModel: TestModel = new TestModel();

  build() {
    Row() {
      Column() {
        Text(this.viewModel.isSuccess ? 'success' : 'failed')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            this.viewModel.query();
          })
      }.width('100%')
    }.height('100%')
  }
}

export class TestModel {
  isSuccess: boolean = false;
  model: Model

  constructor() {
    this.model = new Model(() => {
      this.isSuccess = true;
      console.info(`this.isSuccess: ${this.isSuccess}`);
    })
  }

  query() {
    this.model.query();
  }
}

export class Model {
  callback: () => void

  constructor(cb: () => void) {
    this.callback = cb;
  }

  query() {
    this.callback();
  }
}
```

In the preceding example code, the state variable is modified in the constructor. The message "failed" is displayed at the beginning. After you click the message, the log "this.isSuccess: true" is printed, indicating that the modification is successful. However, the message "failed" is still displayed, indicating that the UI is not refreshed.

**Correct Usage**

```ts
@Entry
@Component
struct Index {
  @State viewModel: TestModel = new TestModel();

  build() {
    Row() {
      Column() {
        Text(this.viewModel.isSuccess ? 'success' : 'failed')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            this.viewModel.query();
          })
      }.width('100%')
    }.height('100%')
  }
}

export class TestModel {
  isSuccess: boolean = false;
  model: Model = new Model(() => {
  })

  query() {
    this.model.callback = () => {
      this.isSuccess = true;
    }
    this.model.query();
  }
}

export class Model {
  callback: () => void

  constructor(cb: () => void) {
    this.callback = cb;
  }

  query() {
    this.callback();
  }
}
```

In the preceding example, the state variable is changed through a method of the class. After the button is clicked, the page content changes from "failed" to "success."

### A state variable causes a re-render of merely the bound UI component.

Example 1

```ts
class Info {
  address: string = 'Hangzhou';
}

@Entry
@Component
struct Test {
  @State message: string =' Shanghai';
  @State info: Info = new Info();

  aboutToAppear(): void {
    this.info.address = this.message;
  }

  build() {
    Column() {
      Text(`${this.message}`);
      Text(`${this.info.address}`);
      Button('change')
        .onClick(() => {
          this.info.address = 'Beijing';
        })
    }
  }
}
```

Clicking Button('change') triggers the refresh of only the second Text component because message is of the string type. The string is a value type. When you click the button, the address value in info is changed, but the value of this.message is not affected. Therefore, the first Text component is not refreshed.

Example 2

```ts
class Info {
  address: string = 'Hangzhou';

  constructor(address: string) {
    this.address = address;
  }
}

class User {
  info: Info = new Info('Tianjin');
}

@Entry
@Component
struct Test {
  @State info: Info = new Info('Shanghai');
  @State user: User = new User();

  aboutToAppear(): void {
    this.user.info = this.info;
  }

  build() {
    Column() {
      Text(`${this.info.address}`);
      Text(`${this.user.info.address}`);
      Button('change')
        .onClick(() => {
          this.user.info.address = 'Beijing'
        })
    }
  }
}
```

In aboutToAppear, the reference of info is assigned to the member attribute info of user. Therefore, when you click the button to change the attribute in info, the first Text component is refreshed. The second Text component cannot detect the change of the level-2 attribute because the observation capability has only one layer. Therefore, the second Text component is not refreshed.

Example 3

```ts
class Info {
  address: string = 'Hangzhou';

  constructor(address: string) {
    this.address = address;
  }
}

class User {
  info: Info = new Info('Tianjin');
}

@Entry
@Component
struct Test {
  @State info: Info = new Info('Shanghai');
  @State user: User = new User();

  aboutToAppear(): void {
    this.user.info = this.info;
  }

  build() {
    Column() {
      Text(`${this.info.address}`);
      Text(`${this.user.info.address}`);
      Button('change')
        .onClick(() => {
          this.user.info = new Info('Guangzhou');
          this.user.info.address = 'Beijing';
        })
    }
  }
}
```

In the preceding example, after you click the button, the following changes occur:

- The first Text component is not refreshed. This is because this.user.info = new Info ('Guangzhou') is executed in the click event. As a result, this.user.info does not reference this.info, but a new Info instance is assigned. Therefore, the attribute of this.user.info is not observed by this.info, and the first Text component is not refreshed.
- The second Text component is refreshed. After you click the button, this.user.info = new Info ('Guangzhou') is executed. This change is an assignment at the first layer and can be observed. The current custom component is marked as dirty and the next frame is requested for refresh. Then, this.user.info.address = 'Beijing' is executed. This change is an assignment at the second layer and cannot be observed. However, note that although the current change cannot be observed, the assignment takes effect. When the next frame is refreshed, this.user.info.address has been changed to Beijing. Therefore, the second Text component displays Beijing.

If this.user.info = new Info ('Guangzhou') is commented out in the preceding example, the scenario is the same as that in example 2. Only the first Text component is updated, and the second Text component cannot be updated.

### Repeated Assignment of Complex Type Constants to State Variables Triggers Re-rendering

```ts
class DataObj {
  name: string = 'default name';

  constructor(name: string) {
    this.name = name;
  }
}

@Entry
@Component
struct Index {
  list: DataObj[] = [new DataObj('a'), new DataObj('b'), new DataObj('c')];
  @State dataObjFromList: DataObj = this.list[0];

  build() {
    Column() {
      ConsumerChild({ dataObj: this.dataObjFromList })
      Button('change to self').onClick(() => {
        this.dataObjFromList = this.list[0];
      })
    }
  }
}

@Component
struct ConsumerChild {
  @Link @Watch('onDataObjChange') dataObj: DataObj;

  onDataObjChange() {
    console.info('dataObj changed');
  }

  getContent() {
    console.info(`this.dataObj.name change: ${this.dataObj.name}`);
    return this.dataObj.name;
  }

  build() {
    Column() {
      Text(this.getContent()).fontSize(30)
    }
  }
}
```

In the preceding example, each time the **change to self** button is clicked, the same class constant is assigned to a state variable of the class type. This operation triggers re-render and generates the log **this.dataObj.name change: a**. In state management V1, a proxy is added to the @Observed decorated class objects and the @State decorated objects of the Class, Date, Map, Set, or Array type to observe the changes of top-level properties or API invoking. 
When list[0] is assigned again, dataObjFromList is of the Proxy type, and list[0] is of the Object type. Therefore, the system determines that the two values are different, triggering value assignment and refresh.
To avoid unnecessary value changes and re-renders, use \@Observed to decorate the class, or use [UIUtils.getTarget()](./arkts-new-getTarget.md) to obtain the original value and determine whether the original and new values are the same. If they are the same, do not perform value changes. 
Method 1: Add \@Observed decorator.

```ts
@Observed
class DataObj {
  name: string = 'default name';

  constructor(name: string) {
    this.name = name;
  }
}

@Entry
@Component
struct Index {
  list: DataObj[] = [new DataObj('a'), new DataObj('b'), new DataObj('c')];
  @State dataObjFromList: DataObj = this.list[0];

  build() {
    Column() {
      ConsumerChild({ dataObj: this.dataObjFromList })
      Button('change to self').onClick(() => {
        this.dataObjFromList = this.list[0];
      })
    }
  }
}

@Component
struct ConsumerChild {
  @Link @Watch('onDataObjChange') dataObj: DataObj;

  onDataObjChange() {
    console.info('dataObj changed');
  }

  build() {
    Column() {
      Text(this.dataObj.name).fontSize(30)
    }
  }
}
```

In the preceding example, the \@Observed decorator is added to decorate the class, **list[0]** is of the **Proxy** type. In this case, when a value is reassigned, the same object will not be re-rendered.

Method 2: Use [UIUtils.getTarget()](./arkts-new-getTarget.md) to obtain the original object.

```ts
import { UIUtils } from '@ohos.arkui.StateManagement';

class DataObj {
  name: string = 'default name';

  constructor(name: string) {
    this.name = name;
  }
}

@Entry
@Component
struct Index {
  list: DataObj[] = [new DataObj('a'), new DataObj('b'), new DataObj('c')];
  @State dataObjFromList: DataObj = this.list[0];

  build() {
    Column() {
      ConsumerChild({ dataObj: this.dataObjFromList })
      Button('change to self').onClick(() => {
        // Obtain the original value and compare it with the new value.
        if (UIUtils.getTarget(this.dataObjFromList) !== this.list[0]) {
          this.dataObjFromList = this.list[0];
        }
      })
    }
  }
}

@Component
struct ConsumerChild {
  @Link @Watch('onDataObjChange') dataObj: DataObj;

  onDataObjChange() {
    console.info('dataObj changed');
  }

  build() {
    Column() {
      Text(this.dataObj.name).fontSize(30)
    }
  }
}
```

In the preceding example, **getTarget** is used to obtain the original value of the corresponding state variable before value change. After comparison, if the original value is the same as the new value, re-rendering will not be triggered.

### Changing State Variables in build() Is Forbidden

State variables cannot be changed in **build()**. Otherwise, the state management framework reports error logs during runtime.

The rendering process is as follows:

1. Create a custom component in **Index**.

2. Execute the **build** method of **Index** as follows:

    1. Create a **Column** component.

    2. Create a Text component. **This.count++** is triggered when the **Text** component is created.

    3. The value change of **count** triggers the re-render of the **Text** component.

    4. Return value of **Text** is 2.

```ts
@Entry
@Component
struct Index {
  @State count: number = 1;

  build() {
    Column() {
      // Avoid directly changing the value of count in the Text component.
      Text(`${this.count++}`)
        .width(50)
        .height(50)
    }
  }
}
```

During the first creation, the Text component is rendered for multiple times, and the final display is 2.

If the framework identifies that the state variable is changed in **build()**, an error log is generated. The error log is as follows:

```ts
FIX THIS APPLICATION ERROR: @Component 'Index'[4]: State variable 'count' has changed during render! It's illegal to change @Component state while build (initial render or re-render) is on-going. Application error!
```

In the preceding example, the Text component is rendered for multiple times. This error does not cause serious consequences. Therefore, many developers ignore this log.

However, this behavior is serious. As the project complexity increases, the potential risks increase gradually. Example:

```ts
@Entry
@Component
struct Index {
  @State message: number = 20;

  build() {
    Column() {
      Text(`${this.message++}`)

      Text(`${this.message++}`)
    }
    .height('100%')
    .width('100%')
  }
}
```
The rendering process of the preceding example is as follows:

1. Create the first **Text** component to trigger the change of **this.message**.

2. The change of **this.message** triggers the re-render of the second **Text** component.

3. The re-render of the second **Text** component triggers the change of **this.message**, which again triggers the re-render of the first **Text** component.

4. Cyclic re-rendering.

5. The system does not respond for a long time, causing an App Freeze.

Therefore, it is completely wrong to change the state variable in the build method. When the error "FIX THIS APPLICATION ERROR: @Component ...has changed during render! It's illegal to change @Component state while build (initial render or re-render) is on-going. Application error!" log is found, you should be vigilant and correct the incorrect writing even if no serious consequences are caused.

### Using the a.b(this.object) Pattern Fails to Trigger UI Re-rendering

In the **build** method, when the variable decorated by \@State is of the object type and is called in the **a.b(this.object)** format, the original object of **this.object** is passed in the b method. If the property of **this.object** is changed, the UI cannot be re-rendered. In the following example, when the static method **Balloon.increaseVolume** or **this.reduceVolume** is used to change the **volume** of **Balloon**, the UI is not re-rendered.

**Incorrect Usage**

```ts
class Balloon {
  volume: number;
  constructor(volume: number) {
    this.volume = volume;
  }

  static increaseVolume(balloon:Balloon) {
    balloon.volume += 2;
  }
}

@Entry
@Component
struct Index {
  @State balloon: Balloon = new Balloon(10);

  reduceVolume(balloon:Balloon) {
    balloon.volume -= 1;
  }

  build() {
    Column({space:8}) {
      Text(`The volume of the balloon is ${this.balloon.volume} cubic centimeters.`)
        .fontSize(30)
      Button(`increaseVolume`)
        .onClick(()=>{
          // Static method calls will not trigger UI re-rendering.
          Balloon.increaseVolume(this.balloon);
        })
      Button(`reduceVolume`)
        .onClick(()=>{
          // Internal component method calls using this will not trigger UI re-rendering.
          this.reduceVolume(this.balloon);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

The state variable observes the attribute change through the proxy. When a.b(this.object) is used, the framework converts the proxy object to the original object. The attributes of the original object cannot be observed. Therefore, the UI is not refreshed. You can use the following methods to modify the attributes:

1. Assign this.balloon to a temporary variable.
2. Use the temporary variable to complete the original invoking logic.
For details, see the positive example.

**Correct Usage**

```ts
class Balloon {
  volume: number;
  constructor(volume: number) {
    this.volume = volume;
  }

  static increaseVolume(balloon:Balloon) {
    balloon.volume += 2;
  }
}

@Entry
@Component
struct Index {
  @State balloon: Balloon = new Balloon(10);

  reduceVolume(balloon:Balloon) {
    balloon.volume -= 1;
  }

  build() {
    Column({space:8}) {
      Text(`The volume of the balloon is ${this.balloon.volume} cubic centimeters.`)
        .fontSize(30)
      Button(`increaseVolume`)
        .onClick(()=>{
          // Assign the value to a temporary variable to retain the proxy.
          let balloon1 = this.balloon;
          Balloon.increaseVolume(balloon1);
        })
      Button(`reduceVolume`)
        .onClick(()=>{
          // Assign the value to a temporary variable to retain the proxy.
          let balloon2 = this.balloon;
          this.reduceVolume(balloon2);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Unregistration Existing Functions Before Changing State Variables by Registering a Callback

You can register the arrow function in **aboutToAppear** to change the state variables in the component.

>**Note:**
>
> In aboutToDisappear, you need to set the registered function to null. Otherwise, the arrow function captures the this instance of the custom component. As a result, the custom component cannot be released, causing memory leakage.

```ts
class Model {
  private callback: (() => void) | undefined = () => {};

  add(callback: () => void): void {
    this.callback = callback;
  }

  delete(): void {
    this.callback = undefined;
  }

  call(): void {
    if (this.callback) {
      this.callback();
    }
  }
}

let model: Model = new Model();

@Entry
@Component
struct Test {
  @State count: number = 10;

  aboutToAppear(): void {
    model.add(() => {
      this.count++;
    })
  }

  build() {
    Column() {
      Text(`Value of count: ${this.count}`)
      Button('change')
        .onClick(() => {
          model.call();
        })
    }
  }

  aboutToDisappear(): void {
    model.delete();
  }
}
```

In addition, you can use LocalStorage to change the state variable outside the custom component. (./arkts-localstorage.md#changing-the-status-variable-outside-the-custom-component)
