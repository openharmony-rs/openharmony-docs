# wrapBuilder: Encapsulating Global @Builder
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

  When multiple global \@Builder functions are used within a single struct to implement different UI effects, code maintenance becomes challenging and the page structure appears cluttered. In this case, you can use [wrapBuilder](../../reference/apis-arkui/arkui-ts/ts-universal-wrapBuilder.md) to encapsulate the global \@Builder.

  Before reading this topic, you are advised to read [\@Builder](./arkts-builder.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 11.
>
> Since API version 12, wrapBuilder is supported in atomic services.
>
> Since API version 22, you are advised to use [mutableBuilder](./arkts-mutableBuilder.md) to update the UI after the second assignment.

When the \@Builder method is assigned to a variable or array, it cannot be used in the UI method.

```ts
@Builder
function builderElement() {}

let builderArr: Function[] = [builderElement];
@Builder
function testBuilder() {
  ForEach(builderArr, (item: Function) => {
    item();
  })
}
```

In the preceding code, **builderArr** is an array of \@Builder methods. When you obtain each \@Builder method in the ForEach loop, an issue arises where the \@Builder method cannot be used in the UI method.

To address this issue, **wrapBuilder** is introduced as a global \@Builder encapsulation function. wrapBuilder returns a WrappedBuilder object, which is used to assign and transfer the [global \@Builder decorated function](arkts-builder.md#global-custom-builder-function).

## Available APIs

A template function that returns a **WrappedBuilder** object.

```ts
declare function wrapBuilder<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder<Args>;
```

The **WrappedBuilder** object is also a template class.

```ts
declare class WrappedBuilder<Args extends Object[]> {
  builder: (...args: Args) => void;

  constructor(builder: (...args: Args) => void);
}
```

> **NOTE**
>
> The template parameter **Args extends Object[]** needs to match the type of the \@Builder function parameter.

Example

```ts
let builderVar: WrappedBuilder<[string, number]> = wrapBuilder(MyBuilder);
let builderArr: WrappedBuilder<[string, number]>[] = [wrapBuilder(MyBuilder)]; // Can be placed in arrays.
```



## Constraints

1. **wrapBuilder** only accepts a [global \@Builder decorated function](arkts-builder.md#global-custom-builder-function) as its argument.

2. The builder attribute of the WrappedBuilder object can be used only in the struct.

## Assigning a Value to a Variable Using the @Builder Method

Use the myBuilder method decorated with the \@Builder decorator as the parameter of wrapBuilder, and assign the return value of wrapBuilder to the globalBuilder variable. In this way, the \@Builder method can be used after being assigned to a variable.

 <!-- @[wrapbuilder_page_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/wrapbuilder/entry/src/main/ets/pages/PageTwo.ets) -->
 
 ``` TypeScript
 @Builder
 function myBuilder(value: string, size: number) {
   Text(value)
     .fontSize(size)
 }
 
 let globalBuilder: WrappedBuilder<[string, number]> = wrapBuilder(myBuilder);
 
 @Entry
 @Component
 struct TestIndex {
   @State message: string = 'Hello World';
 
   build() {
     Row() {
       Column() {
         globalBuilder.builder(this.message, 50)
       }
       .width('100%')
     }
     .height('100%')
   }
 }
 ```

## Assigning a Value to a Variable by the @Builder Method to Use the Variable in UI Syntax

The custom component IndexItem uses ForEach to render different \@Builder functions. You can use the wrapBuilder array declared by builderArr to implement different \@Builder functions. This results in cleaner and more organized code.

<!-- @[wrapbuilder_page_three](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/wrapbuilder/entry/src/main/ets/pages/PageThree.ets) --> 

``` TypeScript
@Builder
function myBuilder0(value: string, size: number) {
  Text(value)
    .fontSize(size)
    .fontColor(Color.Blue)
}

@Builder
function yourBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
    .fontColor(Color.Pink)
}

const builderArr: WrappedBuilder<[string, number]>[] = [wrapBuilder(myBuilder0), wrapBuilder(yourBuilder)];

@Entry
@Component
struct IndexItem {
  @Builder
  IndexItem() {
    ForEach(builderArr, (item: WrappedBuilder<[string, number]>) => {
      item.builder('Hello World', 30);
    })
  }

  build() {
    Row() {
      Column() {
        this.IndexItem();
      }
      .width('100%')
    }
    .height('100%')
  }
}
```


## Assigning a Value to a Class or API Attribute Using the @Builder Method

Use the MyBuilder method decorated by the \@Builder decorator as the parameter of wrapBuilder, and assign the return value of wrapBuilder to the attribute in the ChildOptions interface. The attribute can be transferred to other subcomponents in the form of data.

```ts
@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

interface ChildOptions {
  wrappedBuilder: WrappedBuilder<[string, number]>; // The attribute of the WrappedBuilder type can transfer the @Builder function.
}

@Entry
@Component
struct Index {
  childOptions: ChildOptions = {
    wrappedBuilder: wrapBuilder(MyBuilder)
  };

  build() {
    Row() {
      Column() {
        Child({ options: this.childOptions })
      }
      .width('100%')
    }
    .height('100%')
  }
}

@Component
struct Child {
  @Prop options: ChildOptions;
  build() {
    this.options.wrappedBuilder.builder('Hello', 20);
  }
}
```

## Passing Parameters by Reference

When parameters are transferred by reference, the change of the status variable causes the UI in the \@Builder method to be refreshed.

<!-- @[wrapbuilder_page_four](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/wrapbuilder/entry/src/main/ets/pages/PageFour.ets) -->

``` TypeScript
class Tmp {
  public paramA2: string = 'hello';
}

@Builder
function overBuilder(param: Tmp) {
  Column() {
    Text(`wrapBuildervalue:${param.paramA2}`)
  }
}

const wBuilder: WrappedBuilder<[Tmp]> = wrapBuilder(overBuilder);

@Entry
@Component
struct Parent {
  @State label: Tmp = new Tmp();

  build() {
    Column() {
      wBuilder.builder({ paramA2: this.label.paramA2 })
      Button('Click me').onClick(() => {
        this.label.paramA2 = 'ArkUI';
      })
    }
  }
}
```

## FAQs

### Failure of Duplicate wrapBuilder Initialization

In the same custom component, the same **wrapBuilder** can be initialized only once. For example, after **builderObj** is initialized through **wrapBuilder (MyBuilderFirst)**, the **wrapBuilder(MyBuilderSecond)** value assigned to **builderObj** does not take effect.

<!-- @[wrapbuilder_page_five](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/wrapbuilder/entry/src/main/ets/pages/PageFive.ets) -->

``` TypeScript
@Builder
function myBuilderFirst(value: string, size: number) {
  Text('MyBuilderFirst: ' + value)
    .fontSize(size)
}

@Builder
function myBuilderSecond(value: string, size: number) {
  Text('MyBuilderSecond: ' + value)
    .fontSize(size)
}

interface BuilderModel {
  globalBuilder: WrappedBuilder<[string, number]>;
}

@Entry
@Component
struct TestBuilderIndex {
  @State message: string = 'Hello World';
  @State builderObj: BuilderModel = { globalBuilder: wrapBuilder(myBuilderFirst) };

  aboutToAppear(): void {
    setTimeout(() => {
      // wrapBuilder (myBuilderSecond) does not take effect.
      this.builderObj.globalBuilder = wrapBuilder(myBuilderSecond);
    }, 1000);
  }

  build() {
    Row() {
      Column() {
        this.builderObj.globalBuilder.builder(this.message, 20)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
