# mutableBuilder: Implementing Dynamic Update of Global @Builder
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @zhangwenhan-->
<!--Adviser: @zhang_yixin13-->

 When multiple global [\@Builder](./arkts-builder.md) functions are used in a custom component to implement different UI effects, code maintenance becomes very difficult and the page is not neat enough. In this case, you can use [wrapBuilder](./arkts-wrapBuilder.md) to encapsulate the global @Builder. However, the wrapBuilder does not support dynamic switching of the @Builder. The [mutableBuilder](../../reference/apis-arkui/arkui-ts/ts-universal-mutableBuilder.md) is introduced to implement dynamic switching of the global @Builder.

> **NOTE**
>
> Since API version 22, developers can use mutableBuilder to dynamically switch global @Builders.
>
> Since API version 22, mutableBuilder can be used in atomic services.

## The wrapBuilder does not support dynamic global @Builder.
Currently, wrapBuilder does not support secondary value assignment. If \@Builder is modified, the UI does not change.
```ts
class TextContent {
  text: string = '';
}

@Builder
function textBuilder(p: TextContent) {
  Text(p.text)
}

@Builder
function buttonBuilder(p: TextContent) {
  Button(p.text)
}

@Entry
@Component
struct Index {
  @State message: string = 'init';
  @State text: WrappedBuilder<[TextContent]> = wrapBuilder(textBuilder); // Using textBuilder for initialization

  build() {
    Column() {
      this.text.builder({ text: this.message })
      Button().onClick(() => {
        this.text = wrapBuilder(buttonBuilder); // Click the button and replace textBuilder with buttonBuilder for secondary value assignment.
      })
    }
  }
}
```
In the preceding code, the textBuilder is used to initialize the wrapBuilder. When the onClick event of the button is clicked, the buttonBuilder is used to initialize the wrapBuilder again. The update of the corresponding @Builder is not triggered.

To solve this problem, mutableBuilder is introduced as the dynamic global \@Builder encapsulation function. mutableBuilder returns a MutableBuilder object, which is used to dynamically refresh [global \@Builder](arkts-builder.md#global-custom-builder-function).

## Available APIs

mutableBuilder is a template function that returns a [MutableBuilder](../../reference/apis-arkui/arkui-ts/ts-universal-mutableBuilder.md#mutablebuilder-2) object. Compared with [WrappedBuilder](../../reference/apis-arkui/arkui-ts/ts-universal-wrapBuilder.md#wrappedbuilder), MuableBuilder can dynamically switch the global @Builder.
```ts
declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>;
```
In addition, the MutableBuilder object is a template class , which is inherited from [WrappedBuilder](./arkts-wrapBuilder.md#available-apis).

```ts
declare class MutableBuilder<Args extends Object[]> extends WrappedBuilder<Args> {
}
```

> **NOTE**
>
> The template parameter **Args extends Object[]** needs to match the type of the \@Builder function parameter.

Invocation pattern:

```ts
let builderVar: MutableBuilder<[string, number]> = mutableBuilder(MyBuilder);
let builderArr: MutableBuilder<[string, number]>[] = [mutableBuilder(MyBuilder)]; // mutableBuilder can be placed in an array.
```



## Constraints

1. The mutableBuilder method can only pass the [global \@Builder](arkts-builder.md#global-custom-builder-function) method. An error is reported when the local @Builder method is passed for compilation.

   ```ts
   class TextContent {
     text: string = '';
   }
   
   @Builder
   function globalBuilder(p: TextContent) {
     Text(p.text)
   }
   
   @ComponentV2
   struct MyApp {
     @Local message: string = 'init';
     // Correct usage. Use the global @Builder.
     @Local switchingBuilder: MutableBuilder<[TextContent]> = mutableBuilder(globalBuilder);
     // Incorrect usage. When the local @Builder is used, an error is reported during compilation.
     @Local localBuilderObject: MutableBuilder<[TextContent]> = mutableBuilder(this.localBuilder);
     
     @Builder
     localBuilder(p: TextContent) {
       Text(p.text)
     }
     build() {
       Column() {
         this.switchingBuilder.builder({ text: this.message })
       }
     }
   }
   ```

2. The builder attribute method of the MutableBuilder object can be used only inside a custom component. If it is used outside a custom component, the program will crash.

   ```ts
   class TextContent {
     text: string = '';
   }
   
   @Builder
   function globalBuilder(p: TextContent) {
     Text(p.text)
   }
   
   // Incorrect usage. The builder attribute method of the MutableBuilder object is used outside the custom component. As a result, the system breaks down during running.
   let outSideBuilder: MutableBuilder<[TextContent]> = mutableBuilder(globalBuilder);
   outSideBuilder.builder({ text: 'message' });
   
   @ComponentV2
   struct MyApp {
     @Local message: string = 'init';
     @Local switchingBuilder: MutableBuilder<[TextContent]> = mutableBuilder(globalBuilder);
     build() {
       Column() {
         // Correct usage. The builder attribute method of the MutableBuilder object is used in the customized component.
         this.switchingBuilder.builder({ text: this.message })
       }
     }
   }
   ```

3. You are not advised to use mutableBuilder together with wrapBuilder because the object type created by mutableBuilder is MutableBuilder, which may cause unexpected updates.

   The following usage is not recommended:

   ```ts
   // When instantiating the MutableBuilder object, you are advised to use the mutableBuilder (builderName) method.
   @State switchingBuilder: MutableBuilder<[MutableBinding]> = mutableBuilder(textBuilder);
   // The value of a variable of the MutableBuilder type cannot be undefined or null. Otherwise, the system crashes during running.
   @State switchingBuilder: MutableBuilder<[MutableBinding]> | undefined | null = null; 
   Button(`MutableBuilder`).onClick(() => {
     // You are not advised to assign the object created by wrapBuilder to an object of the MutableBuilder type. After the value is assigned, textBuilder is dynamically switched to buttonBuilder.
     this.switchingBuilder = wrapBuilder(buttonBuilder);  
   })
   ```

   The recommended usage is as follows:

   ```ts
   // When instantiating the MutableBuilder object, you are advised to use the mutableBuilder (builderName) method.
   @State switchingBuilder: MutableBuilder<[MutableBinding]> = mutableBuilder(textBuilder);
   
   Button(`MutableBuilder`).onClick(() => {
     // Assigning a value will dynamically switch textBuilder in wrapBuilder to buttonBuilder.
     this.switchingBuilder = mutableBuilder(buttonBuilder); // Recommended usage
   })
   ```

## Dynamically Changing the Global @Builder Instance
Use the textBuilder method decorated with the \@Builder decorator as the parameter of mutableBuilder, and assign the return value of mutableBuilder to the switchingBuilder variable. In the button click event, use the buttonBuilder method decorated with the \@Builder decorator as the parameter of mutableBuilder, and assign the return value of mutableBuilder to the switchingBuilder variable again. In this way, textBuilder can be updated to buttonBuilder, solving the problem that wrapBuilder does not support secondary assignment.


```ts
class TextContent {
  text: string = '';
}

@Builder
function textBuilder(p: TextContent) {
  Text(p.text).margin(20)
}

@Builder
function buttonBuilder(p: TextContent) {
  Button(p.text).margin(20)
}

let counter: number = 1;
@Entry
@ComponentV2
struct MyApp {
  @Local message: string = 'init';
  @Local switchingBuilder: MutableBuilder<[TextContent]> = mutableBuilder(textBuilder);
  build() {
    Column() {
      this.switchingBuilder.builder({ text: this.message })
      Button('Click to change')
      .onClick(() => {
        counter++; // Increment the counter on each button click to dynamically switch the global @Builder.
        if(counter % 2 === 0) {
          this.message += 'B';
          this.switchingBuilder = mutableBuilder(buttonBuilder); // textBuilder--->buttonBuilder
        } else {
          this.message += 'T';
          this.switchingBuilder = mutableBuilder(textBuilder); // buttonBuilder--->textBuilder
        }
      })
    }.position({x: 120, y: 60})
  }
}
```
Click the button to dynamically change textBuilder to buttonBuilder, as shown in the following figure.

![arkts-mutableBuilder-dynamic-demo1](figures/mutableBuilder-dynamic-demo1.gif)


## Using mutableBuilder to Display Pop-up Menus

MutableBuilder inherits WrappedBuilder. Therefore, @Builder corresponding to mutableBuilder has the same capabilities as WrappedBuilder. As shown in the following example, the @Builder method corresponding to mutableBuilder can be used as the input parameter of bindMenu, and the pop-up menu can be displayed upon a click.
```ts
@Builder
function overBuilder() {
  Row() {
    Text('Global Builder')
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }
}

@Entry
@Component
struct Index {
  @State arr: number[] = [1,2,3,4,5];

  mutableBuilderMenu: MutableBuilder<[]> = mutableBuilder<[]>(overBuilder);
  build() {
    Column() {
      List({ space: 10 }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text(`${item}`)
            .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
          .bindMenu(this.mutableBuilderMenu.builder)
        }, (item: number) => JSON.stringify(item))
      }
    }
  }
}
```

## Observing the Change of @Builder in mutableBuilder

 You can use [MutableBinding](../../reference/apis-arkui/js-apis-stateManagement.md#mutablebindingt20) to wrap the @Builder function corresponding to mutableBuilder to observe the changes of the state variable. In addition, you can use [@Monitor](./arkts-new-monitor.md) or [addMonitor](./arkts-new-addMonitor-clearMonitor.md) to listen to the changes of @Builder in mutableBuilder.

```ts
import { UIUtils, MutableBinding } from '@kit.ArkUI';

@Builder
function textBuilder(p: MutableBinding<string>) {
  Text(p.value)
    .margin(20)
    .onClick(() => {
      p.value += 't';
    })
}

@Builder
function buttonBuilder(p: MutableBinding<string>) {
  Button(p.value)
    .margin(20)
    .onClick(() => {
      p.value += 'b';
    })
}

let counter: number = 1;

@Entry
@ComponentV2
struct MyApp {
  @Local message: string = 'init';
  @Local switchingBuilder: MutableBuilder<[MutableBinding<string>]> = mutableBuilder(textBuilder);

  @Monitor('switchingBuilder') variableChange(m: IMonitor): void {
    console.info(`Builder changed. is buttonBuilder: ${m.value<MutableBuilder<[MutableBinding<string>]>>()?.now.builder === buttonBuilder}`);
  }

  build() {
    Column() {
      this.switchingBuilder.builder(UIUtils.makeBinding(()=> this.message, txt => this.message = txt))
      Button('Click to change')
        .onClick(() => {
          counter++;
          if(counter % 2 === 0) {
            this.message += 'B';
            this.switchingBuilder = mutableBuilder(buttonBuilder); // textBuilder--->buttonBuilder, @Monitor will trigger the callback.
          } else {
            this.message += 'T';
            this.switchingBuilder = mutableBuilder(textBuilder); // buttonBuilder--->textBuilder, @Monitor will trigger the callback.
          }
        })
    }.position({x: 120, y: 60})
  }
}
```
Click the button to dynamically switch **textBuilder** to **buttonBuilder**. Click **buttonBuilder**. **B** is automatically added to **this.message**, as shown in the following figure.

![arkts-mutableBuilder-dynamic-demo2](figures/mutableBuilder-dynamic-demo2.gif)

When you click the button to dynamically switch the **textBuilder** to the **buttonBuilder**, the @Monitor listens to the change of the global @Builder and prints the "@Builder change. is buttonBuilder: true" log.
