# Mixing Use of Custom Components
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zzq212050299-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

V1 provides a series of state variable decorators (V1 decorators for short), such as @State, @Prop, and @Link, which can be used in custom components decorated with @Component (V1 custom components for short).

However, V1 has many restrictions on the observation of nested classes. For example, you need to use \@ObjectLink to continuously decompose nested classes so that deep-level data can be observed.

Therefore, V2 is provided in API version 12. You can declare custom components decorated with \@ComponentV2 (V2 custom components for short) and use a new set of decorators (V2 decorators for short). For example, \@Local and \@Param.

V2 not only solves the problem of V1's observation of nested classes, but also enhances the functions of some decorators. For example, \@Monitor in V2 can not only detect changed data, but also obtain data before the change.

In terms of design, the code of V1 and V2 are expected to be completely isolated because V2 can do better than V1 in certain scenarios. However, from the actual perspective, the code developed in V1 have a solid foundation and it is not practical to migrate the entire code to V2 at a time. Therefore, it is allowed to use some capabilities of V2 in the code of V1 and capabilities of V1 is not completely prohibited in V2. For example, a custom component of V1 uses a custom component of V2, or V1 uses a decorator of V2. In this way, a problem of mixed use of V1 and V2 occurs.

This guide describes the scenarios where V1 and V2 are mixed, helping you migrate V1 code to V2.

> **NOTE**
>
> State management V2 is supported since API version 12.
> The rules for mixed use described in this topic apply only to API version 18 and earlier. Since API version 19, to help you migrate your application from V1 to V2 more easily, the state management module provides new APIs [enableV2Compatibility](../../reference/apis-arkui/js-apis-StateManagement.md#enablev2compatibility19) and [makeV1Observed](../../reference/apis-arkui/js-apis-StateManagement.md#makev1observed19) to solve the mixed use problems during the migration. For details, see [Mixing Use of State Management V1 and V2](./arkts-v1-v2-mixusage.md).

## Overview

The rules for mixed use of state management V1 and V2 are as follows:

* The decorators of V2 cannot be used in the custom components of V1. Otherwise, an error is reported during compilation.

* If variables are not transferred between components, V1 custom components can use V2 custom components, including custom components decorated by the third-party \@ComponentV2 decorator.

* When variables are passed between components, such as passing variables of V1 to the custom components of V2, constraints are as follows:
  - Variables that are not decorated by decorators in V1 (common variables) can be received only by using \@Param in V2.
  - Variables decorated by the decorator in V1 (state variables) can be received only by using \@Param in V2 and are limited to simple data types such as boolean, number, enum, string, undefined and null.

* The decorators of V1 cannot be used in the custom components of V2. Otherwise, an error is reported during compilation.

* When no variable is passed between components, custom components of V2 can use custom components of V1 as well as import \@Component decorated custom components of a third party.

* When variables are passed between components, such as passing variables of V2 to the custom components of V1, constraints are as follows:
  - Variables that are not decorated by decorators in V2 (common variables) can be received by using \@State, \@Prop, and \@Provide in V1.
  - Variables decorated by the decorator in V2 (state variables) of the built-in types, such as Array, Set, Map, and Date, are not supported in V1.

## State Management Decorator Overview

### Decorators of V1

|  Type |                            Decorator                           |
| :----------: | :----------------------------------------------------------: |
| Intra-component decorator| \@State, \@Prop, \@Link, \@ObjectLink, \@Provide, \@Consume, \@StorageProp, \@StorageLink, \@LocalStorageProp, \@LocalStorageLink, \@Watch|
| Class-related decorator|                     \@Observed, \@Track                     |

### Decorators of V2

|  Type |                            Decorator                           |
| :----------: | :----------------------------------------------------------: |
| Intra-component decorator| \@Local, \@Param, \@Provider, \@Consumer, \@Once, \@Event, \@Monitor, \@Computed|
| Class-related decorator|                \@ObservedV2, \@Trace, \@Type                |

### Data Types Supported by State Management Decorators

The following data types are supported by status management:

| Type    | Keyword                                            |
| ------------ | -------------------------------------------------- |
| Simple type| boolean, number, enum, string, null, undefined    |
| Function type| function (supported only by \@Event, \@Monitor, and \@Computed of V2)|
| Object type  | Object                                             |
| Class type   | Class                                              |
| Built-in type    | Array, Map, Set, Date                             |



## Constraints

### Mixing Use of Decorators of V1 and V2 Is Forbidden

**1. The decorators of V2 cannot be used in the custom components of V1.**

```typescript
@Component
struct Child {
  // @Param cannot be used in @Component. Otherwise, an error is reported during compilation.
  // @Once and @Require are extended decorators of @Param and must be used together with @Param.
  @Param message: string = "";	                 
  @Event changeMessage: (val: string) => void;  // @Event cannot be used in @Component. Otherwise, an error is reported during compilation.

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.changeMessage('world hello');
        })
    }
  }
}

@Entry
@Component
struct Index {
  @Local message: string ='Hello World'; // @Local cannot be used in @Component. Otherwise, an error is reported during compilation.

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      Divider()
        .color(Color.Blue)
      Child({
        message: this.message,
        changeMessage: (val: string) => {
          this.message = val;
        }
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

The intra-component decorators in V2 cannot be used in the custom components of V1. Otherwise, an error is reported during compilation.

The sample code shows how \@Local, \@Param, \@Event, \@Provider, \@Consumer, \@Monitor and \@Computed decorators work.

**2. The decorators of V1 cannot be used in the custom components of V2.**

```typescript
@ComponentV2
struct Child {
  @Prop message: string = "";  	// @Prop cannot be used in @ComponentV2. Otherwise, an error is reported during compilation.
  @Link myId: number;           // @Link cannot be used in @ComponentV2. Otherwise, an error is reported during compilation.

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world hello';
        })
      Divider()
        .color(Color.Blue)
      Text(`${this.myId}`)
        .id('HelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.myId++;
        })
    }
  }
}

@Entry
@ComponentV2
struct Index {
  @State message: string = 'Hello World';      // @State cannot be used in @ComponentV2. Otherwise, an error is reported during compilation.
  @State @Watch('idChange') myId: number = 1;  // @Watch cannot be used in @ComponentV2. Otherwise, an error is reported during compilation.

  idChange(propName: number) : void {
    console.info(`id changed ${this.myId}`);
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      Divider()
        .color(Color.Blue)
      Child({
        message: this.message,
        myId: this.myId
      })
    }
    .height('100%')
    .width('100%')
    .margin(5)
  }
}
```

The intra-component decorators in V1 cannot be used in the custom components of V2. Otherwise, an error is reported during compilation.

The sample code shows how \@ObjectLink, \@Provide, \@Consume, \@StorageProp, \@StorageLink, \@LocalStorageProp, and \@LocalStorageLink decorators work.

### Using Multiple Decorators to Decorate the Same Variable Is Forbidden (Except \@Watch, \@Once, and \@Require)

```typescript
@Component
struct Child {
  @State @Prop message: string = "";	// Multiple decorators of V1 cannot decorate the same variable. Otherwise, an error is reported during compilation.

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world hello';
        })
    }
  }
}

@Entry
@ComponentV2
struct Index {
  @Local @Param message: string = 'Hello World'; // Multiple decorators of V2 cannot decorate the same variable. Otherwise, an error is reported during compilation.

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      Divider()
        .color(Color.Blue)
      Child({
        message: this.message
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

Except \@Watch, \@Once, and \@Require, other capability extension decorators cannot be used together with other decorators.

## Introduction to Mixed Use  

### Mixing Use of Decorators of V1 and V2

1. Use the class object decorated by \@ObservedV2 in the V1 custom component.

```typescript
@ObservedV2
class Info {
  @Trace myId: number;   		// Observable.
  name: string;           		// Not observable.
  @Track trackId: number = 1; 	// As a decorator of V1, @Track cannot be used in @ObservedV2. Otherwise, an error is reported during compilation. Remove @Track to eliminate the error.
  
  constructor(id?: number, name?: string) {
    this.myId = id || 0;
    this.name = name || 'aaa';
  }
}

@Observed
class message extends Info {	// Classes inherited from @ObservedV2 cannot be decorated by Observed. Otherwise, an error is reported during compilation. Remove @Observed to eliminate the error.
}

class MessageInfo extends Info {
}

@Entry
@Component
struct Index {
  info1: Info = new Info();                      // @ObservedV2 decorated class can be used in V1, and @Trace decorated class is observable.
  @State info2: Info = new Info();               // @ObservedV2 decorated class cannot be decorated by the decorator of V1. Otherwise, an error is reported during compilation. Remove @State to eliminate the error.

  @State messageInfo: MessageInfo = new MessageInfo();  // Classes inherited from @ObservedV2 cannot be decorated by the decorator of V1. Otherwise, an error is reported during runtime. Remove @State to eliminate the error.
  build() {
    Column() {
      Text(`info1 name: ${this.info1.name}`)            // name is not decorated by @Trace and is not observable.
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info1.name += 'b';
        })
      Text(`info1 id: ${this.info1.myId}`)              // myId is decorated by @Trace and is observable.
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info1.myId += 1;
        })
      Divider()
        .color(Color.Blue)
      Text(`info2 id: ${this.info2.myId}`)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info2.myId += 1;
        })
      Divider()
        .color(Color.Blue)
      Text(`messageInfo id: ${this.messageInfo.myId}`) // A crash occurs during runtime when the class inherited from @ObservedV2 is decorated by the decorators of V1. Remove @State to eliminate the error.
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.messageInfo.myId += 1;
        })
    }
    .height('100%')
    .width('100%')
    .margin(5)
  }
}
```

Using \@ObservedV2 must comply with the following rules:

* \@ObservedV2 can decorate only Class; \@Trace and \@Type can decorate only class properties and can be used only in \@ObservedV2.
* \@Track cannot be used in \@ObservedV2.
* A class decorated by \@ObservedV2 cannot be directly decorated by the decorator of V1. Otherwise, an error is reported during compilation.
* In the example, the code can be executed properly after you remove the decorator that reports error. The property change can be observed only when the class is decorated by \@Trace.

**2. Use the \@Observed decorated class object in a custom component of V2.**

```typescript
@Observed
class Info {
  @Track myId: number;   		  // Not observable. Only associated update caused by other property changes can be prevented.
  name: string;           		  // Not observable.
  @Trace trackId: number = 1; 	  // As a decorator of V2, @Trace cannot be used in @Observed. Otherwise, an error is reported during compilation. Remove @Trace to eliminate the error.
  constructor(id?: number, name?: string) {
    this.myId = id || 0;
    this.name = name || 'aaa';
  }
}

@ObservedV2
class message extends Info {      // @ObservedV2 decorated class cannot inherit from @Observed. Otherwise, an error is reported during compilation. Remove @ObservedV2 to eliminate the error.
}

class MessageInfo extends Info {  
}

@Entry
@ComponentV2
struct Index {
  info1: Info = new Info();             // @Observed decorated class can be used in V2.
  @Local info2: Info = new Info();      // @Observe decorated class cannot be decorated by the decorator of V2. Otherwise, an error is reported during compilation. Remove @Local to eliminate the error.
  @Local messageInfo: MessageInfo = new MessageInfo(); 
  build() {
    Column() {
      Text(`info1 name: ${this.info1.name}`)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info1.name += 'b';
        })
      Text(`info1 id: ${this.info1.myId}`)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info1.myId += 1;
        })
      Divider()
        .color(Color.Blue)
      Text(`info2 id: ${this.info2.myId}`)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info2.myId += 1;
        })
      Divider()
        .color(Color.Blue)
      // Classes inherited from @ObservedV2 are decorated by the decorator of V2, but the class properties cannot be observed by the decorator of V2. Therefore, you are not advised to use the @Observed decorated classes in V2.
      Text(`messageInfo id: ${this.messageInfo.myId}`)   
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.messageInfo.myId += 1;
        })
    }
    .height('100%')
    .width('100%')
    .margin(5)
  }
}
```

You are not advised to use \@Observed decorated classes in V2 because \@Observed and \@Track decorated class properties can only be distinguished but not be observed. In-depth data can be observed only when \@Observed and \@ObjectLink are used to split nested data. However, \@ObjectLink cannot be used in custom components of V2.

When migrating V1 code to V2, you are not advised to use the class decorated by @Observed in @ComponentV2 (no observation capability in V2). If you must use it, comply with the following rules:

* \@Observed can only decorate class, and \@Trace cannot be used in \@Observed.
* \@Observed and \@Track decorated classes are not observable and you can use the decorators only to prevent the entire class from being refreshed when a class property is changed.
* Classes inherited from @Observed are decorated by the decorator of V2, but the class properties cannot be observed the intra-component decorator of V2. Therefore, class property changes cannot be observed using \@Observed.
* In the example, the code can be executed properly after you remove the decorator that reports error. Because the observation capability is unavailable, you are not advised to use \@Observed in V2.

### Mixing Use of Custom Components of V1 and V2 When No Variable Is Passed

**1. Use the custom components of V2 in V1.**

```typescript
@ComponentV2
struct Child {
  @Local message: string = "hello";

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world';
        })
    }
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world hello';
        })
      Divider()
        .color(Color.Blue)
      Child()
    }
    .height('100%')
    .width('100%')
  }
}
```

When V2 custom components are used in V1, if no variable passing is involved, there will be no impact. If variable passing is involved, follow the instructions in [Mixing Use of State Management V1 and V2](arkts-v1-v2-mixusage.md).

**2. Use the custom components of V1 in V2.**

```typescript
@Component
struct Child {
  @State message: string = "hello";

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world';
        })
    }
  }
}

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world hello';
        })
      Divider()
        .color(Color.Blue)
      Child()
    }
    .height('100%')
    .width('100%')
  }
}
```

When V1 custom components are used in V2, if no variable passing is involved, there will be no impact. If variable passing is involved, follow the instructions in [Mixing Use of State Management V1 and V2](arkts-v1-v2-mixusage.md).

### Mixing Use of Custom Components of V1 and V2 When Variables Are Passed

**1. V1 > V2: Pass the common variables of V1 to the custom component of V2.**

```typescript
class Info {
  myId: number;
  name: string;

  constructor(myId?: number, name?: string) {
    this.myId = myId || 0;
    this.name = name || 'aaa';
  }
}

@ComponentV2
struct Child {  
  // V2 strictly manages data input. When receiving data from the parent component, the @Param decorator must be used to receive data.
  @Param @Once message: string = "hello";	              // Changes are observable and can be synchronized to the parent component through @Event. @Once can be used to change @Param decorated variables.
  @Param @Once undefinedVal: string | undefined = undefined;  // @Once can be used to change @Param decorated variables.
  @Param info: Info = new Info();		                 // The class property changes are not observable.
  @Require @Param set: Set<number>;
  
  build() {
    Column() {
      Text(`child message:${this.message}`) // Display the string.
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world';
        })

      Divider()
        .color(Color.Blue)
      Text (`undefinedVal:${this.undefinedVal}`) // Displays undefinedVal
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.undefinedVal = "change to define";
        })
      Divider()
        .color(Color.Blue)
      Text(`info id:${this.info.myId}`) // Display info:myId.
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info.myId++;
        })
      Divider()
        .color(Color.Blue)
      ForEach(Array.from(this.set.values()), (item: number) => {  // Display set.
        Text(`${item}`)
          .fontSize(30)
      })
    }
    .margin(5)
  }
}

@Entry
@Component
struct Index {
  message: string = 'Hello World';       // Simple type.
  undefinedVal: undefined = undefined;    // Simple type, undefined
  info: Info = new Info();               // Class type.
  set: Set<number> = new Set([10, 20]);  // Built-in type.

  build() {
    Column() {
      Text(`message:${this.message}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world hello';
        })
      Divider()
        .color(Color.Blue)
      Child({
        message: this.message,
        undefinedVal: this.undefinedVal,
        info: this.info,
        set: this.set
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

When the common variables of V1 are passed to a custom component of V2, constraints are as follows:

* The custom component of V2 must receive data through \@Param.
* To observe the received data changes, use \@Param; to observe the received class changes, use \@ObservedV2 and \@Trace.

**2. V1 > V2: Pass the state variables of V1 to the custom component of V2.**

```typescript
class Info {
  myId: number;
  name: string;

  constructor(myId?: number, name?: string) {
    this.myId = myId || 0;
    this.name = name || 'aaa';
  }
}

@ComponentV2
struct Child {  
  // V2 strictly manages data input. When receiving data from the parent component, the @Param decorator must be used to receive data.
  @Param @Once message: string = "hello";
  @Param @Once undefinedVal: string | undefined = undefined;  // @Once can be used to change @Param decorated variables.
  @Param info: Info = new Info();
  @Require @Param set: Set<number>;
  build() {
    Column() {
      Text(`child message:${this.message}`) // Display the string.
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world';
        })
      Divider()
        .color(Color.Blue)
      Text (`undefinedVal:${this.undefinedVal}`) // Displays undefinedVal
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.undefinedVal = "change to define";
        })
      Divider()
        .color(Color.Blue)
      Text('info id:${this.info.myId}') // Display info:myId.
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info.myId++;
        })
      Divider()
        .color(Color.Blue)
      ForEach(Array.from(this.set.values()), (item: number) => { // Display set.
        Text(`${item}`)
          .fontSize(30)
      })
    }
    .margin(5)
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';       // Simple type data can be passed.
  @State undefinedVal: undefined = undefined;    // Simple type data, undefined, can be passed.
  @State info: Info = new Info();               // Class type cannot be passed. Otherwise, an error is reported during compilation. Remove @State to eliminate the error.
  @State set: Set<number> = new Set([10, 20]);  // Built-in type cannot be passed. Otherwise, an error is reported during compilation. Remove @State to eliminate the error.

  build() {
    Column() {
      Text(`message:${this.message}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world hello';
        })
      Divider()
        .color(Color.Blue)
      Child({
        message: this.message,
        undefinedVal: this.undefinedVal,
        info: this.info,
        set: this.set
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

When the state variable of V1 is transferred to the custom component of V2, the following rules are followed:

* Only simple variables are supported. For other types of data, an error is reported during compilation.

* In the example, the \@State decorator is used. Other decorators such as \@Prop, \@Link, \@ObjectLink, \@Provide, \@Consume, \@StorageProp, \@StorageLink, \@LocalStorageProp and \@LocalStorageLink work in the same way as \@State.

**3. V2 > V1: Pass the common variables of V2 to the custom component of V1.**

```typescript
class Info {
  myId: number;
  name: string;

  constructor(myId?: number, name?: string) {
    this.myId = myId || 0;
    this.name = name || 'aaa';
  }
}

@Component
struct Child {  
  // State variable received by V1 from V2. Only @State, @Prop, and @Provide decorators can be used.
  @State  message: string = "hello";	         // Changes are observable.
  @State info: Info = new Info();		      	// Top-level class property changes are observable.
  @Prop undefinedVal: undefined | string = undefined;
  @Provide setMap: Set<number> = new Set();
  build() {
    Column() {
      Text(`child message:${this.message}`) 	// Display the string.
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world';
        })
      Divider()
        .color(Color.Blue)
      Text(`undefinedVal:${this.undefinedVal}`) // Display undefinedVal.
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.undefinedVal = "change to define";
        })
      Divider()
        .color(Color.Blue)
      Text(`info id:${this.info.myId}`)		 	// Display info:myId.
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info.myId++;
        })
      Divider()
        .color(Color.Blue)
      ForEach(Array.from(this.setMap.values()), (item: number) => {  // Display set.
        Text(`${item}`)
          .fontSize(30)
      })
    }
    .margin(5)
  }
}

@Entry
@ComponentV2
struct Index {
  message: string = 'Hello World';       // Simple type.
  undefinedVal: undefined = undefined; // Simple data type, undefined
  info: Info = new Info();               // Class type.
  set: Set<number> = new Set([10, 20]);  // Built-in type.

  build() {
    Column() {
      Text(`message:${this.message}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world hello';
        })
      Divider()
        .color(Color.Blue)
      Child({
        message: this.message,
        undefinedVal: this.undefinedVal,
        info: this.info,
        setMap: this.set
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

When a common variable of V2 is passed to a custom component of V1:

* V1 does not need to use the decorator to receive data. The received variable is a common variable in the V1 custom component.

* If V1 uses a decorator to receive data, data can be received only through \@State, \@Prop, and \@Provide.

**4. V2 > V1: Pass the state variables of V2 to the custom component of V1.**

```typescript
class Info {
  myId: number;
  name: string;

  constructor(myId?: number, name?: string) {
    this.myId = myId || 0;
    this.name = name || 'aaa';
  }
}

@Component
struct Child {  
  // State variable received by V1 from V2. Only @State, @Prop, and @Provide can be used.
  @State  message: string = "hello";	        // Changes are observable.
  @State info: Info = new Info();		        // Top-level class property changes are observable.
  @Prop undefinedVal: undefined | string = undefined;
  @Provide set: Set<number> = new Set();
  build() {
    Column() {
      Text(`child message:${this.message}`) 	// Display the string.
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world';
        })
      Divider()
        .color(Color.Blue)
      Text (`undefinedVal:${this.undefinedVal}`) // Displays undefinedVal
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.undefinedVal = "change to define";
        })
      Divider()
        .color(Color.Blue)
      Text(`info id:${this.info.myId}`) 	// Display info:myId.
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.info.myId++;
        })

      Divider()
        .color(Color.Blue)
      ForEach(Array.from(this.set.values()), (item: number) => {  // Display set.
        Text(`${item}`)
          .fontSize(30)
      })
    }
    .margin(5)
  }
}

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';       	// Simple type data can be passed.
  @Provider() undefinedVal: undefined = undefined;   // Simple type data, undefined, can be passed.
  @Consumer() info: Info = new Info();          	// Class type can be passed.
  @Param set: Set<number> = new Set([10, 20]);  	// Built-in type cannot be passed. Otherwise, an error is reported during compilation. Remove @Param to eliminate the error.

  build() {
    Column() {
      Text(`message:${this.message}`)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = 'world hello';
        })

      Divider()
        .color(Color.Blue)
      Child({
        message: this.message,
        undefinedVal: this.undefinedVal,
        info: this.info,
        set: this.set
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

When the state variables of V2 are passed to a custom component of V1, constraints are as follows:

* V1 can receive data without using the decorator. The received variables are also common variables in the custom component of V1.
* If V1 uses a decorator to receive data, data can be received only through \@State, \@Prop, and \@Provide.
* When V1 uses the decorator to receive data, built-in data is not supported.

### Summary

After sorting out the hybrid use of V1 and V2, you can summarize the following information:

1. When V2 code is mixed with V1 code (that is, V1 component or class data is transferred to V2), most V1 capabilities are disabled in V2.

2. When V1 code is mixed with V2 code (that is, V2 components or class data is transferred to V1), some functions are opened. For example, \@ObservedV2 and \@Trace are the biggest help for observing V1 nested class data.

Therefore, during code development, you are not advised to use V1 and V2 together for mixed development. However, you can gradually migrate the code of V1 to V2 to steadily replace the function code of V1. In addition, you are not advised to use the code of V1 in V2.

## Supplementary Scenarios

Classes can be nested at multiple levels because they are decorated by \@Observed and \@ObservedV2, leading to a complex scenario. This section mainly describes the self-nesting of the class type and the nesting of the built-in type. Lack of in-depth observation capability like \@ObservedV2 and @Trace, the in-depth nesting of \@Observed is not discussed. Only the use scenarios of \@ObservedV2 in V1 are discussed.

### Using \@Observed and \@ObjectLink to Observe Nested Classes

```typescript
@Observed
class Info {
  myId: number;
  name: string;

  constructor(myId?: number, name?: string) {
    this.myId = myId || 0;
    this.name = name || 'aaa';
  }
}

@Observed
class MessageInfo { 		// One-level nesting.
  @Track info: Info;        // Prevent the info from being updated when the messageId is changed.
  @Track messageId: number; // Prevent the info from being updated when the messageId is changed.

  constructor(info?: Info, messageId?: number) {
    this.info = info || new Info();   
    this.messageId = messageId || 0;
  }
}

@Observed
class MessageInfoNested { // Dual-level nesting.
  messageInfo: MessageInfo;

  constructor(messageInfo?: MessageInfo) {
    this.messageInfo = messageInfo || new MessageInfo();
  }
}

@Component
struct GrandSon {
  @ObjectLink info: Info;

  build() {
    Column() {
      Text(`ObjectLink info info.myId:${this.info.myId}`)  // After @ObjectLink disassembles the level twice, the change is observable.
        .fontSize(30)
        .onClick(() => {
          this.info.myId++;
        })
    }
  }
}

@Component
struct Child {
  @ObjectLink messageInfo: MessageInfo;

  build() {
    Column() {
      Text(`ObjectLink MessageInfo messageId:${this.messageInfo.messageId}`)  // After @ObjectLink disassembles the levels, the change of the top-level class property is observable.
        .fontSize(30)
        .onClick(() => {
          this.messageInfo.messageId++;
        })
      Divider()
        .color(Color.Blue)
      Text(`ObjectLink MessageInfo info.myId:${this.messageInfo.info.myId}`)  // After @ObjectLink disassembles the level, the change is not observable.
        .fontSize(30)
        .onClick(() => {
          this.messageInfo.info.myId++;
        })
      GrandSon({info: this.messageInfo.info});				// Continue to disassemble the top-level child components.
    }
  }
}



@Entry
@Component
struct Index {
  @State messageInfoNested: MessageInfoNested = new MessageInfoNested();  // For the data nested at three levels, you need to observe all data.

  build() {
    Column() {
      // Observe messageInfoNested.
      Text(`messageInfoNested messageId:${this.messageInfoNested.messageInfo.messageId}`)  // @State can only observe the top-level class properties but not their changes.
        .fontSize(30)
        .onClick(() => {
          this.messageInfoNested.messageInfo.messageId++;
        })
      Divider()
        .color(Color.Blue)
      // Observe messageInfoId through @ObjectLink.
      Child({messageInfo: this.messageInfoNested.messageInfo})      // After disassembling, you can use @ObjectLink to observe the lower-level changes.
      Divider()
        .color(Color.Blue)
    }
    .height('100%')
    .width('100%')
    .margin(10)
  }
}
```

The preceding example is a three-layer nesting scenario, indicating that:

* The observation capability of the decorator of V1 is to function as a proxy for data. Therefore, when data is nested, the decorator of V1 can only disassemble the child component to observe lower-level data through \@Observed and \@ObjectLink.

* \@Track prevents the info in the MessageInfo class from being changed by the messageId and then refreshed. If you remove \@Track, you can observe that the info is refreshed when the messageId changes. However, this is not the observation capability of \@ObjectLink.

### Using @ObsevedV2 and @Trace to Observe Nested Classes

```typescript
@ObservedV2
class Info {
  @Trace myId: number;
  name: string;

  constructor(myId?: number, name?: string) {
    this.myId = myId || 0;
    this.name = name || 'aaa';
  }
}

@Observed
class MessageInfo { // One-level nesting.
  @Track info: Info;        // Prevent the info from being updated when the messageId is changed.
  @Track messageId: number; // Prevent the info from being updated when the messageId is changed.

  constructor(info?: Info, messageId?: number) {
    this.info = info || new Info();   // Use the input info or create an Info.
    this.messageId = messageId || 0;
  }
}

@Observed
class MessageInfoNested { // Dual-level nesting. If MessageInfoNested is decorated by @ObservedV2, it cannot be decorated by the state variable decorator of V1, such as @State.
  messageInfo: MessageInfo;

  constructor(messageInfo?: MessageInfo) {
    this.messageInfo = messageInfo || new MessageInfo();
  }
}

@Component
struct Child {
  @ObjectLink messageInfo: MessageInfo;

  build() {
    Column() {
      Text(`ObjectLink MessageInfo messageId:${this.messageInfo.messageId}`)  // After @ObjectLink disassembles the levels, the change of the top-level class property is observable.
        .fontSize(30)
        .onClick(() => {
          this.messageInfo.messageId++;
        })
    }
  }
}

@Entry
@Component
struct Index {
  @State messageInfoNested: MessageInfoNested = new MessageInfoNested();  // For the data nested at three levels, you need to observe the internal data.

  build() {
    Column() {
      // Observe messageInfoNested. @State can only observe the top-level data and cannot observe the changes.
      Text(`messageInfoNested messageId:${this.messageInfoNested.messageInfo.messageId}`)
        .fontSize(30)
        .onClick(() => {
          this.messageInfoNested.messageInfo.messageId++;
        })
      Divider()
        .color(Color.Blue)
      Text(`messageInfoNested name:${this.messageInfoNested.messageInfo.info.name}`)   // Being not decorated by @Trace, it is not observable.
        .fontSize(30)
        .onClick(() => {
          this.messageInfoNested.messageInfo.info.name += 'a';
        })
      Divider()
        .color(Color.Blue)
      Text(`messageInfoNested myId:${this.messageInfoNested.messageInfo.info.myId}`) // Decorated by @Trace, data changes can be observed no matter how many levels data is nested in.
        .fontSize(30)
        .onClick(() => {
          this.messageInfoNested.messageInfo.info.myId++;
        })
      Divider()
        .color(Color.Blue)
      // Observe messageInfoId through @ObjectLink.
      Child({messageInfo: this.messageInfoNested.messageInfo})      // After disassembling, you can use @ObjectLink to observe the lower-level changes.
    }
    .height('100%')
    .width('100%')
    .margin(10)
  }
}
```

When \@ObservedV2+\@Trace is used, you can find that:

* \@ObservedV2+\@Trace implements the observation capability on class attributes. Therefore, when a class attribute is marked with @Trace, changes can be observed regardless of the number of nested layers.
* When \@ObservedV2 and \@Observed are nested, whether the class object can be decorated by the V1 decorator depends on the decorator used by the outermost class. For example, in the example, the \@ObservedV2 decoration of the nested class does not affect the decoration of the outermost class by the V1 decorator.
