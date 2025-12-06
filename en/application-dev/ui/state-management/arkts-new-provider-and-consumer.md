# \@Provider and \@Consumer Decorators: Synchronizing Across Component Levels in a Two-Way Manner
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Provider and \@Consumer are used for synchronizing data across the component levels in a two-way manner, so that you are free from the constraints of the component levels.
\@Provider and \@Consumer are decorators in state management V2, so they can be used only in \@ComponentV2. A compilation error will be reported if they are used in \@Component.

\@Provider and \@Consumer provide the capability of cross-component two-way data synchronization. Before reading this topic, you are advised to read [\@ComponentV2](./arkts-new-componentV2.md).

>**NOTE**
>
> The \@Provider and \@Consumer decorators are supported since API version 12.
>
> The \@Provider and \@Consumer decorators can be used in atomic services since API version 12.

## Overview

\@Provider provides data. Its child components can use the \@Consumer to obtain the data by binding the same **key**.
\@Consumer obtains data. It can obtain the \@Provider data of the nearest parent node by binding the same **key**. If the \@Provider data cannot be found, the local default value will be used.
The data types decorated with \@Provider and \@Consumer must be the same.

The following notes must be paid attention to when using \@Provider and \@Consumer:
- \@Provider and \@Consumer strongly depend on the custom component levels. \@Consumer is initialized to different values because the parent component of the custom component is different.
- Using \@Provider with \@Consumer is equivalent to bonding components together. From the perspective of independent component, usage of \@Provider and \@Consumer should be lessened.

## Capability Comparison: \@Provider and \@Consumer Vs. \@Provide and \@Consume
In state management V1, [\@Provide and \@Consume](./arkts-provide-and-consume.md) are the decorators which provide two-way synchronization across component levels. This topic introduces \@Provider and \@Consumer decorators in state management V2. Although the names and features of the two pairs are similar, there are still some differences.
If you are not familiar with \@Provide and \@Consume in state management V1, skip this section.

| Capability| \@Provider and \@Consumer Decorators of V2                                            |\@Provide and \@Consume Decorators of V1|
| ------------------ | ----------------------------------------------------- |----------------------------------------------------- |
| \@Consume(r)         |Local initialization is mandatory. When \@Provider cannot be found, the local default value is used.| In versions earlier than API version 20, \@Consume does not support local initialization. When \@Provide cannot be found, an exception is thrown. From API version 20 onwards, \@Consume supports default value setting. If no default value is set and \@Provide cannot be found, an exception is thrown.|
| Supported type          | **function** is supported.| **function** is not supported.|
| Observation capability          | Only the value change of itself can be observed. To observe the nesting scenario, use this decorator together with [\@Trace](https://gitee.com/openharmony/docs/blob/master/en/application-dev/quick-start/arkts-new-observedV2-and-trace.md).| Changes at the first layer can be observed. To observe the nesting scenario, use this decorator together with [\@Observed and \@ObjectLink](https://gitee.com/openharmony/docs/blob/master/en/application-dev/quick-start/arkts-observed-and-objectlink.md).|
| alias and attribute name        | alias is the only matching key. By default, the attribute name is alias.| If both the **alias** and attribute name are **key**, the former one is matched first. If no match is found, the attribute name can be matched.|
| \@Provide(r) initialization from the parent component     | Not allowed.| Allowed.|
| \@Provide(r) overloading support | Enabled by default. That is, \@Provider can have duplicate names and \@Consumer can search upwards for the nearest \@Provider.| Disabled by default. That is, \@Provide with duplicate names is not allowed in the component tree. If overloading is required, set **allowOverride**.|

## Decorator Description

### Basic Rules
\@Provider syntax:
`@Provider(aliasName?: string) varName : varType = initValue`

| \@Provider Property Decorator| Description                                                 |
| ------------------ | ----------------------------------------------------- |
| Decorator parameters        | **aliasName?: string**: alias. The default value is the attribute name.|
| Supported type          | Member variables in custom components.<br> Property types include number, string, boolean, class, [Array](#decorating-variables-of-the-array-type), [Date](#decorating-variables-of-the-date-type), [Map](#decorating-variables-of-the-map-type), and [Set](#decorating-variables-of-the-set-type).<br>[Arrow functions](#using-provider-and-consumer-for-callback-decoration-and-component-behavior-abstraction).|
| Initialization from the parent component     | Forbidden.|
| Local initialization        | Required.|
| Observation capability        | Be equivalent to \@Trace. Changes are synchronized to the corresponding \@Consumer.|

\@Consumer syntax:
`@Consumer(aliasName?: string) varName : varType = initValue`

| \@Consumer Property Decorator| Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| Decorator parameters           | **aliasName?: string**: alias. The default value is the attribute name. The nearest \@Provider is searched upwards.   |
| Supported type         | Member variables in the custom component.<br> Property types include number, string, boolean, class, Array, Date, Map, and Set.<br> Arrow function.|
| Initialization from the parent component     | Forbidden.|
| Local initialization        | Required.|
| Observation capability        | Be equivalent to \@Trace. Changes will be synchronized to the corresponding \@Provider.|

### aliasName and Attribute Name

\@Provider and \@Consumer accept the optional parameter aliasName. If no parameter is configured, the attribute name is used as the default aliasName.

>**NOTE**
>
> **aliasName** is the unique key used to match \@Provider and \@Consumer.

The following three examples clearly describe how \@Provider and \@Consumer use **aliasName** for searching and matching.

```ts
@ComponentV2
struct Parent {
  // The aliasName is not defined. Use the property name "str" as the aliasName.
  @Provider() str: string = 'hello';
}

@ComponentV2
struct Child {
  // Define aliasName as"str" and use it to search.
  // If the value can be found on the Parent component, use the value "hello" of @Provider.
  @Consumer('str') str: string = 'world';
}
```

```ts
@ComponentV2
struct Parent {
  // Define aliasName as "alias".
  @Provider('alias') str: string = 'hello';
}

@ComponentV2 
struct Child {
  // Define aliasName as "alias", find out @Provider, and obtain the value "hello".
  @Consumer('alias') str: string = 'world';
}
```

```ts
@ComponentV2
struct Parent {
  // Define aliasName as "alias".
  @Provider('alias') str: string = 'hello';
}

@ComponentV2
struct Child {
  // The aliasName is not defined. Use the property name "str" as the aliasName.
  // The corresponding @Provider is not found, use the local value "world".
  @Consumer() str: string = 'world';
}
```

## Variable Passing

| Behavior      | Description                                                        |
| -------------- | ------------------------------------------------------------ |
| Initialization from the parent component| Variables decorated with \@Provider and \@Consumer can only be initialized locally and cannot be initialized from external sources.|
| Child component initialization  | Variables decorated by \@Provider and \@Consumer can be used to initialize \@Param decorated variables in the child component.|

## Constraints

1. \@Provider and \@Consumer are attribute decorators of custom components. They can only decorate attributes within custom components and cannot decorate class attributes.
2. \@Provider and \@Consumer are decorators of the state management V2, which can be used only in \@ComponentV2 but not in \@Component.
3. \@Provider and \@Consumer support only local initialization and do not support external initialization.

## Use Scenarios

### Synchronizing \@Provider and \@Consumer in a Two-Way Manner

**Establishing a Two-Way Binding**

1. Initialize the **Parent** and **Child** custom components:
    - **@Consumer() str: string = 'world'** in the **Child** component searches upwards to find **@Provider() str: string = 'hello'** in the **Parent** component.
    - **@Consumer() str: string = 'world'** is initialized to the value of **@Provider**, that is, **'hello'**.
    - Both of them establish a two-way synchronization relationship.
2. Click the button in the parent component to change the value of str decorated by \@Provider and notify the corresponding \@Consumer. The corresponding UI is refreshed.
3. Click the button in **Child** to change the \@Consumer decorated **str**, and notify the corresponding \@Provider to re-render the UI.

```ts
@Entry
@ComponentV2
struct Parent {
  @Provider() str: string = 'hello';

  build() {
    Column() {
      Button(this.str)
        .onClick(() => {
          this.str += '0';
        })
      Child()
    }
  }
}

@ComponentV2
struct Child {
  // The name of the attribute decorated by @Consumer is the same as that of the attribute decorated by @Provider in the parent component. Therefore, a bidirectional binding relationship is established.
  @Consumer() str: string = 'world';

  build() {
    Column() {
      Button(this.str)
        .onClick(() => {
          this.str += '0';
        })
    }
  }
}
```

**Establishing a Two-Way Binding Failed**

In the following example, \@Provider and \@Consumer fail to establish a two-way synchronization relationship because of different **aliasName** value.
1. Initialize the **Parent** and **Child** custom components:
    - @Provider is not found when **@Consumer() str: string = 'world'** in the **Child** component searches upwards.
    - **@Consumer() str: string = 'world'** uses the local default value 'world'.
    - Both of them fail to establish a two-way synchronization relationship.
2. Click the button in the **Parent** component to change @Provider decorated **str1** and re-render only the **Button** component associated with \@Provider.
3. Click the button in the **Child** component to change the @Consumer decorated **str** and re-render only the **Button** component associated with @Consumer.

```ts
@Entry
@ComponentV2
struct Parent {
  @Provider() str1: string = 'hello';

  build() {
    Column() {
      Button(this.str1)
        .onClick(() => {
          this.str1 += '0';
        })
      Child()
    }
  }
}

@ComponentV2
struct Child {
  // The name of the str attribute decorated by @Consumer is different from that of the str1 attribute decorated by @Provider in the Parent component. Therefore, the bidirectional binding relationship cannot be established.
  @Consumer() str: string = 'world';

  build() {
    Column() {
      Button(this.str)
        .onClick(() => {
          this.str += '0';
        })
    }
  }
}
```

### Decorating Variables of the Array Type

When the decorated object is of the **Array** type, the following can be observed: (1) complete array reassignment; (2) array item changes caused by calling **push**, **pop**, **shift**, **unshift**, **splice**, **copyWithin**, **fill**, **reverse**, or **sort**.

```ts
@Entry
@ComponentV2
struct Parent {
  @Provider() count: number[] = [1,2,3];

  build() {
    Row() {
      Column() {
        ForEach(this.count, (item: number) => {
          Text(`parent: ${item}`).fontSize(30)
          Divider()
        })
        Button('push').onClick(() => {
          this.count.push(111);
        })
        Button('reverse').onClick(() => {
          this.count.reverse();
        })
        Button('fill').onClick(() => {
          this.count.fill(6);
        })
        Child()
      }
      .width('100%')
    }
    .height('100%')
  }
}

@ComponentV2
struct Child {
  @Consumer() count: number[] = [9,8,7];

  build() {
    Column() {
      ForEach(this.count, (item: number) => {
        Text(`child: ${item}`).fontSize(30)
        Divider()
      })
      Button('push').onClick(() => {
        this.count.push(222);
      })
      Button('reverse').onClick(() => {
        this.count.reverse();
      })
      Button('fill').onClick(() => {
        this.count.fill(8);
      })
    }
    .width('100%')
  }
}
```

### Decorating Variables of the Date Type

When the decorated object is of the Date type, the following changes can be observed: (1) overall reassignment of the **Date** object in the data source; (2) changes caused by calling the **Date** APIs: **setFullYear**, **setMonth**, **setDate**, **setHours**, **setMinutes**, **setSeconds**, **setMilliseconds**, **setTime**, **setUTCFullYear**, **setUTCMonth**, **setUTCDate**, **setUTCHours**, **setUTCMinutes**, **setUTCSeconds**, or **setUTCMilliseconds**.

```ts
@Entry
@ComponentV2
struct Parent {
  @Provider() SelectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      Text(`parent: ${this.SelectedDate}`)
      Button('update the new date')
        .onClick(() => {
          this.SelectedDate = new Date('2023-07-07');
        })
      Button('increase the year by 1')
        .onClick(() => {
          this.SelectedDate.setFullYear(this.SelectedDate.getFullYear() + 1);
        })
      Button('increase the month by 1')
        .onClick(() => {
          this.SelectedDate.setMonth(this.SelectedDate.getMonth() + 1);
        })
      Button('increase the day by 1')
        .onClick(() => {
          this.SelectedDate.setDate(this.SelectedDate.getDate() + 1);
        })
      Child()
    }
  }
}
@ComponentV2
struct Child {
  @Consumer() SelectedDate: Date = new Date('2022-07-07');

  build() {
    Column() {
      Text(`child: ${this.SelectedDate}`)
      Button('update the new date')
        .onClick(() => {
          this.SelectedDate = new Date('2025-01-01');
        })
      Button('increase the year by 1')
        .onClick(() => {
          this.SelectedDate.setFullYear(this.SelectedDate.getFullYear() + 1);
        })
      Button('increase the month by 1')
        .onClick(() => {
          this.SelectedDate.setMonth(this.SelectedDate.getMonth() + 1);
        })
      Button('increase the day by 1')
        .onClick(() => {
          this.SelectedDate.setDate(this.SelectedDate.getDate() + 1);
        })
    }
  }
}
```

### Decorating Variables of the Map Type

When a map variable is decorated, you can observe the value assignment of the data source to the map and the changes brought by the set, clear, and delete interfaces of the map.

```ts
@Entry
@ComponentV2
struct Parent {
  @Provider() message: Map<number, string> = new Map([[0, 'a'], [1, 'b'], [3, 'c']]);

  build() {
    Column() {
      Text('Parent').fontSize(30)
      ForEach(Array.from(this.message.entries()), (item: [number, string]) => {
        Text(`${item[0]}`).fontSize(30)
        Text(`${item[1]}`).fontSize(30)
        Divider()
      })
      Button('init map').onClick(() => {
        this.message = new Map([[0, 'aa'], [1, 'bb'], [3, 'cc']]);
      })
      Button('set new one').onClick(() => {
        this.message.set(4, 'd');
      })
      Button('clear').onClick(() => {
        this.message.clear();
      })
      Button('replace the first one').onClick(() => {
        this.message.set(0, 'a~');
      })
      Button('delete the first one').onClick(() => {
        this.message.delete(0);
      })
      Child()
    }
  }
}
@ComponentV2
struct Child {
  @Consumer() message: Map<number, string> = new Map([[0, 'd'], [1, 'e'], [3, 'f']]);

  build() {
    Column() {
      Text('Child').fontSize(30)
      ForEach(Array.from(this.message.entries()), (item: [number, string]) => {
        Text(`${item[0]}`).fontSize(30)
        Text(`${item[1]}`).fontSize(30)
        Divider()
      })
      Button('init map').onClick(() => {
        this.message = new Map([[0, 'dd'], [1, 'ee'], [3, 'ff']]);
      })
      Button('set new one').onClick(() => {
        this.message.set(4, 'g');
      })
      Button('clear').onClick(() => {
        this.message.clear();
      })
      Button('replace the first one').onClick(() => {
        this.message.set(0, 'a*');
      })
      Button('delete the first one').onClick(() => {
        this.message.delete(0);
      })
    }
  }
}
```

### Decorating Variables of the Set Type

When a set variable is decorated, you can observe the value assignment to the set and the changes brought by the add, clear, and delete interfaces of the set.

```ts
@Entry
@ComponentV2
struct Parent {
  @Provider() message: Set<number> = new Set([1, 2, 3, 4]);

  build() {
    Column() {
      Text('Parent').fontSize(30)
      ForEach(Array.from(this.message.entries()), (item: [number, number]) => {
        Text(`${item[0]}`).fontSize(30)
        Divider()
      })
      Button('init set').onClick(() => {
        this.message = new Set([1, 2, 3, 4]);
      })
      Button('set new one').onClick(() => {
        this.message.add(5);
      })
      Button('clear').onClick(() => {
        this.message.clear();
      })
      Button('delete the first one').onClick(() => {
        this.message.delete(1);
      })
      Child()
    }
  }
}
@ComponentV2
struct Child {
  @Consumer() message: Set<number> = new Set([1, 2, 3, 4, 5, 6]);

  build() {
    Column() {
      Text('Child').fontSize(30)
      ForEach(Array.from(this.message.entries()), (item: [number, number]) => {
        Text(`${item[0]}`).fontSize(30)
        Divider()
      })
      Button('init set').onClick(() => {
        this.message = new Set([1, 2, 3, 4, 5, 6]);
      })
      Button('set new one').onClick(() => {
        this.message.add(7);
      })
      Button('clear').onClick(() => {
        this.message.clear();
      })
      Button('delete the first one').onClick(() => {
        this.message.delete(1);
      })
    }
  }
}
```

### Using \@Provider and \@Consumer for Callback Decoration and Component Behavior Abstraction

When a parent component needs to register callbacks for child components, the @Provider and @Consumer decorators can be applied to callback methods.
For drag scenarios requiring synchronization of child component drag start position to the parent component, refer to the following example.

```ts
@Entry
@ComponentV2
struct Parent {
  @Local childX: number = 0;
  @Local childY: number = 1;
  @Provider() onDrag: (x: number, y: number) => void = (x: number, y: number) => {
    console.info(`onDrag event at x=${x} y:${y}`);
    this.childX = x;
    this.childY = y;
  }

  build() {
    Column() {
      Text(`child position x: ${this.childX}, y: ${this.childY}`)
      Child()
    }
  }
}

@ComponentV2
struct Child {
  @Consumer() onDrag: (x: number, y: number) => void = (x: number, y: number) => {};

  build() {
    Button('changed')
      .draggable(true)
      .onDragStart((event: DragEvent) => {
        // Current Previewer does not support common drag events.
        this.onDrag(event.getDisplayX(), event.getDisplayY());
      })
  }
}
```

### Decorating Complex Types by \@Provider and \@Consumer and Using together with \@Trace

1. \@Provider and \@Consumer can only observe the changes of the data. To observe the attribute changes of the complex data types decorated by \@Provider and \@Consumer, you must use \@Trace together.
2. When decorating built-in types, such as Array, Map, Set, and Date, you can observe the changes of some APIs. The observation capability is the same as that of [\@Trace](./arkts-new-observedV2-and-trace.md#observed-changes).

```ts
@ObservedV2
class User {
  @Trace name: string;
  @Trace age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
const data: User[] = [new User('Json', 10), new User('Eric', 15)];
@Entry
@ComponentV2
struct Parent {
  @Provider('data') users: User[] = data;

  build() {
    Column() {
      Child()
      Button('add new user')
        .onClick(() => {
          this.users.push(new User('Molly', 18));
        })
      Button('age++')
        .onClick(() => {
          this.users[0].age++;
        })
      Button('change name')
        .onClick(() => {
          this.users[0].name = 'Shelly';
        })
    }
  }
}

@ComponentV2
struct Child {
  @Consumer('data') users: User[] = [];

  build() {
    Column() {
      ForEach(this.users, (item: User) => {
        Column() {
          Text(`name: ${item.name}`).fontSize(30)
          Text(`age: ${item.age}`).fontSize(30)
          Divider()
        }
      })
    }
  }
}
```

### Searching Upwards by \@Consumer for the Nearest \@Provider

If \@Provider has duplicate names in the component tree, \@Consumer will search upwards for the \@Provider data of the nearest parent node.

```ts
@Entry
@ComponentV2
struct Index {
  @Provider() val: number = 10;

  build() {
    Column() {
      Parent()
    }
  }
}

@ComponentV2
struct Parent {
  @Provider() val: number = 20;
  @Consumer('val') val2: number = 0; // 10

  build() {
    Column() {
      Text(`${this.val2}`)
      Child()
    }
  }
}

@ComponentV2
struct Child {
  @Consumer() val: number = 0; // 20

  build() {
    Column() {
      Text(`${this.val}`)
    }
  }
}
```

In the preceding example:

- The \@Consumer in Parent searches for the \@Provider() val: number = 10 defined in Index and initializes it to 10.
- The \@Consumer in Child searches for the \@Provider() val: number = 20 defined in Parent and stops searching. The value is initialized to 20.

### Initializing \@Param by \@Provider and \@Consumer

Variables decorated with \@Provider and \@Consumer can initialize variables decorated with \@Param in child components.

```ts
@Entry
@ComponentV2
struct Index {
  @Provider() val: number = 10;

  build() {
    Column() {
      Text(`Index @Provider val: ${this.val}`).fontSize(30)
      Parent({ val2: this.val })
    }
  }
}

@ComponentV2
struct Parent {
  @Consumer() val: number = 0;
  @Require @Param val2: number;

  build() {
    Column() {
      Text(`Parent @Consumer val: ${this.val}`).fontSize(30)
      Button('change val').onClick(() => {
        this.val++;
      })
      Text(`Parent @Param val2: ${this.val2}`).fontSize(30)
      Child({ val: this.val })
    }.border({ width: 2, color: Color.Green })
  }
}

@ComponentV2
struct Child {
  @Require @Param val: number;

  build() {
    Column() {
      Text(`Child @Param val ${this.val}`).fontSize(30)
    }.border({ width: 2, color: Color.Pink })
  }
}
```

In the preceding example:

- The variable val decorated with \@Provider in Index and the variable val decorated with \@Consumer in Parent establish bidirectional data binding. The variable val2 decorated with \@Param in Parent receives the data of the data source val in Index and synchronizes the changes. The variable val decorated with \@Param in Child receives the data of the data source val in Parent and synchronizes the changes.
- Click the button in Parent to trigger the change of @Consumer() val. The change is synchronized to @Provider() val in Index and @Param val in Child, and the corresponding UI is refreshed.
- The change of @Provider() val in Index is synchronized to @Param val2 in Parent, and the corresponding UI is refreshed.
