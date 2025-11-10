# MVVM
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zzq212050299-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

After understanding the basic concepts of state management, you may be eager to develop your own applications. However, if the project structure is not carefully planned at the early stage of application development, the relationship between components becomes blurred as the project grows and state variables increase. In this case, the development of any new function may cause a chain reaction and increase the maintenance cost. This topic describes the MVVM mode and the relationship between the UI development mode of ArkUI and MVVM, and provides guidance for you to design your own project structures to facilitate product development and maintenance during product iteration and upgrade.


Most decorators are covered in this topic, therefore, you are advised to read [State Management Overview](./arkts-state-management-overview.md) and topics related to decorators of V1 to have a basic understanding of state management V1 before getting started.

## Introduction

### Concepts

In application development, UI updates need to synchronize data status changes in real time, which directly affects application performance and user experience. To reduce the complexity of data and UI synchronization, ArkUI uses the Model-View-ViewModel (MVVM) architecture. The MVVM divides an application into three core parts: Model, View, and ViewModel to separate data, views, and logic. In this mode, the UI can automatically update status changes, thereby more efficiently managing data and view binding and update.

- View: user interface layer. It is responsible for user interface display and interaction with users, and does not contain any service logic. It implements dynamic update by binding data provided by the ViewModel layer.
- Model: data access layer. It is data-centric and does not directly interact with the user interface. It is responsible for data structure definition, data management (obtaining, storing, and updating data), and service logic processing.
- ViewModel: logic layer. As a bridge between the Model and View, one View usually corresponds to one ViewModel. The View and ViewModel communicate in either of the following ways: 
  1. Method calling: The View listens to user behavior through events and triggers methods at the ViewModel layer in the callback. For example, when the View detects a button click event, it calls the corresponding method of the ViewModel to process the user operation. 
  2. Two-way binding: The view is bound to the data of the view model to implement two-way synchronization. 

The UI development mode of ArkUI belongs to the MVVM mode. By introducing the concept of MVVM, you may have basic understanding on how the state management work in MVVM. State management aims to drive data update and enable you to focus only on page design without paying attention to the UI re-render logic. In addition, ViewModel enables state variables to automatically maintain data. In this way, MVVM provides a more efficient way for you to develop applications.

### ArkUI Development

The UI development mode of ArkUI is the MVVM mode, in which the state variables play the role of ViewModel to re-render the UI and data. The following figure shows the overall architecture.

![MVVM image](./figures/MVVM_architecture.png)

### Layer Description

**View**

The view layer can be divided into the following components:
* Page components: All applications are classified by page, such as the login page, list page, editing page, help page, and copyright page. The data required by each page may be completely different, or the same set of data can be shared with multiple pages.
* Business components: a functional component that has some service capabilities of the application. Typically, the business component may be associated with the data in the ViewModel of the project and cannot be shared with other projects.
* Common components: Like system components, these components are not associated with the ViewModel data in the app. These components can be shared across multiple projects to implement common functions.

**Model**

The model layer is the provider of the original data of the app and represents the core service logic and data of the app.

**ViewModel**

The view model layer provides data for components at the view layer. The data is organized by page. When a user browses a page, some pages may not be displayed. Therefore, the page data is designed to be lazy-loaded (on-demand loading).

> The differences between the ViewModel data and the Model data are as follows:
>
> The data at the model layer is organized based on the entire project to form a complete app service data system.
>
> ViewModel data provides data used on a page. It may be a part of the service data of the entire application. In addition, ViewModel also provides auxiliary data for page display, which may be irrelevant to the application services.

### Core Principles of the Architecture

**Cross-layer access is not allowed.**

* View cannot directly call data from Model. Instead, use the methods provided by ViewModel to call.
* Model data cannot modify the UI directly but notifies the ViewModel to update the data.

**The lower layer cannot access the upper layer data.**

The lower layer can only notify the upper layer to update the data. In the service logic, the lower layer cannot directly obtain the upper-layer data. For example, the logic processing at the view model layer should not depend on a value on the view layer.

**Non-parent-child components cannot directly access each other.**

This is the core principle of View design. A component should comply with the following logic:

* Do not directly access the parent component. Event or subscription capability must be used.
* Direct access to sibling components is prohibited. This is because components can access only the child nodes (through parameter passing) and parent nodes (through events or notifications) that they can see. In this way, components are decoupled.

Reasons:

* The child components used by the component are clear, therefore, access is allowed.
* The parent node where the component is placed is unknown. Therefore, the component can access the parent node only through notifications or events.
* It is impossible for a component to know its sibling nodes, so the component cannot manipulate the sibling nodes.

## Memo Development

This section describes how to develop a memo application to help you understand how to use the ArkUI framework to design your own applications. This section directly develops functions without designing the code architecture. That is, the code is developed based on requirements without considering subsequent maintenance. In addition, this section describes the decorators required for function development.

### @State

* The @State decorator is one of the most commonly used decorators. It is used to define state variables. Generally, these state variables are used as the data source of the parent component. When you tap the component, the state variables are updated and the UI is refreshed.

```typescript
@Entry
@Component
struct Index {
  @State isFinished: boolean = false;

  build() {
    Column() {
      Row() {
        Text('To-Dos')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
      .margin({top: 10, bottom: 10})

      // To-Do list
      Row({space: 15}) {
        if (this.isFinished) {
          // 'app.media.finished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
          Image($r('app.media.finished'))
            .width(28)
            .height(28)
        }
        else {
          // 'app.media.unfinished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
          Image($r('app.media.unfinished'))
            .width(28)
            .height(28)
        }
        Text('Learn maths')
          .fontSize(24)
          .decoration({type: this.isFinished ? TextDecorationType.LineThrough : TextDecorationType.None})
      }
      .height('40%')
      .width('100%')
      .border({width: 5})
      .padding({left: 15})
      .onClick(() => {
        this.isFinished = !this.isFinished;
      })
    }
    .height('100%')
    .width('100%')
    .margin({top: 5, bottom: 5})
    .backgroundColor('#90f1f3f5')
  }
}
```

The following figure shows the final effect.

![state](./figures/MVVM_state.gif)

### @Prop and @Link

In the preceding example, all code is written in the @Entry decorated component. As more and more components need to be rendered, you need to split the @Entry decorated component and use the @Prop and @Link decorators to decorate the split child components.

* @Prop creates a one-way synchronization between the parent and child components. The child component can perform deep copy of the data from the parent component or update the data from the parent component or itself. However, it cannot synchronize data from the parent component.
* @Link creates a two-way synchronization between the parent and child components. When the parent component changes, all @Links are notified. In addition, when @Link is updated, the corresponding variables of the parent component are notified as well.

```typescript
@Component
struct TodoComponent {
  build() {
    Row() {
      Text('To-Dos')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .margin({top: 10, bottom: 10})
  }
}

@Component
struct AllChooseComponent {
  @Link isFinished: boolean;

  build() {
    Row() {
      Button('Select All', {type: ButtonType.Normal})
        .onClick(() => {
          this.isFinished = !this.isFinished;
        })
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .backgroundColor('#f7f6cc74')
    }
    .padding({left: 15})
    .width('100%')
    .margin({top: 10, bottom: 10})
  }
}

@Component
struct ThingComponent1 {
  @Prop isFinished: boolean;

  build() {
    // Task 1
    Row({space: 15}) {
      if (this.isFinished) {
        // 'app.media.finished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
        Image($r('app.media.finished'))
          .width(28)
          .height(28)
      }
      else {
        // 'app.media.unfinished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
        Image($r('app.media.unfinished'))
          .width(28)
          .height(28)
      }
      Text('Study language')
        .fontSize(24)
        .decoration({type: this.isFinished ? TextDecorationType.LineThrough : TextDecorationType.None})
    }
    .height('40%')
    .width('100%')
    .border({width: 5})
    .padding({left: 15})
    .onClick(() => {
      this.isFinished = !this.isFinished;
    })
  }
}

@Component
struct ThingComponent2 {
  @Prop isFinished: boolean;

  build() {
    // Task 1
    Row({space: 15}) {
      if (this.isFinished) {
        // 'app.media.finished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
        Image($r('app.media.finished'))
          .width(28)
          .height(28)
      }
      else {
        // 'app.media.unfinished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
        Image($r('app.media.unfinished'))
          .width(28)
          .height(28)
      }
      Text('Learn maths')
        .fontSize(24)
        .decoration({type: this.isFinished ? TextDecorationType.LineThrough : TextDecorationType.None})
    }
    .height('40%')
    .width('100%')
    .border({width: 5})
    .padding({left: 15})
    .onClick(() => {
      this.isFinished = !this.isFinished;
    })
  }
}

@Entry
@Component
struct Index {
  @State isFinished: boolean = false;

  build() {
    Column() {
      // All To-Do items.
      TodoComponent()

      // Select all.
      AllChooseComponent({isFinished: this.isFinished})

      // Task 1
      ThingComponent1({isFinished: this.isFinished})

      // Task 2
      ThingComponent2({isFinished: this.isFinished})
    }
    .height('100%')
    .width('100%')
    .margin({top: 5, bottom: 5})
    .backgroundColor('#90f1f3f5')
  }
}
```

The following figure shows an example.

![Prop&Link](./figures/MVVM_Prop&Link.gif)

### Rendering Repeated Components

* In the preceding example, child components are split, but the code of component 1 and component 2 is similar. If the settings of the rendered components are the same except the data, the ForEach loop rendering is required.
* In this way, redundant code is decreased and the code structure is clearer.

```typescript
@Component
struct TodoComponent {
  build() {
    Row() {
      Text('To-Dos')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .margin({top: 10, bottom: 10})
  }
}

@Component
struct AllChooseComponent {
  @Link isFinished: boolean;

  build() {
    Row() {
      Button('Select All', {type: ButtonType.Normal})
        .onClick(() => {
          this.isFinished = !this.isFinished;
        })
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .backgroundColor('#f7f6cc74')
    }
    .padding({left: 15})
    .width('100%')
    .margin({top: 10, bottom: 10})
  }
}

@Component
struct ThingComponent {
  @Prop isFinished: boolean;
  @Prop thing: string;
  build() {
    // Task 1
    Row({space: 15}) {
      if (this.isFinished) {
        // 'app.media.finished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
        Image($r('app.media.finished'))
          .width(28)
          .height(28)
      }
      else {
        // 'app.media.unfinished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
        Image($r('app.media.unfinished'))
          .width(28)
          .height(28)
      }
      Text(`${this.thing}`)
        .fontSize(24)
        .decoration({type: this.isFinished ? TextDecorationType.LineThrough : TextDecorationType.None})
    }
    .height('8%')
    .width('90%')
    .padding({left: 15})
    .opacity(this.isFinished ? 0.3: 1)
    .border({width:1})
    .borderColor(Color.White)
    .borderRadius(25)
    .backgroundColor(Color.White)
    .onClick(() => {
      this.isFinished = !this.isFinished;
    })
  }
}

@Entry
@Component
struct Index {
  @State isFinished: boolean = false;
  @State planList: string[] = [
    '7:30 Get up'
    '8:30 Breakfast'
    '11:30 Lunch'
    '17:30 Dinner'
    '21:30 Snack'
    '22:30 Shower'
    '1:30 Go to bed'
  ];

  build() {
    Column() {
      // All To-Do items.
      TodoComponent()

      // Select all.
      AllChooseComponent({isFinished: this.isFinished})

      List() {
        ForEach(this.planList, (item: string) => {
          // Task 1
          ThingComponent({isFinished: this.isFinished, thing: item})
            .margin(5)
        })
      }
    }
    .height('100%')
    .width('100%')
    .margin({top: 5, bottom: 5})
    .backgroundColor('#90f1f3f5')
  }
}
```

The following figure shows an example.

![ForEach](./figures/MVVM_ForEach.gif)

### @Builder

* The **Builder** method is used to define methods in a component so that the same code can be reused in the component.
* In this example, the @Builder method is used for deduplication and moving out data so that the code is clearer and easier to read. Compared with the initial code, the @Entry decorated component is used only to process page construction logic and does not process a large amount of content irrelevant to page design.

```typescript
@Observed
class TodoListData {
  planList: string[] = [
    '7:30 Get up'
    '8:30 Breakfast'
    '11:30 Lunch'
    '17:30 Dinner'
    '21:30 Snack'
    '22:30 Shower'
    '1:30 Go to bed'
  ];
}

@Component
struct TodoComponent {
  build() {
    Row() {
      Text('To-Dos')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .margin({top: 10, bottom: 10})
  }
}

@Component
struct AllChooseComponent {
  @Link isFinished: boolean;

  build() {
    Row() {
      Button('Select All', {type: ButtonType.Capsule})
        .onClick(() => {
          this.isFinished = !this.isFinished;
        })
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .backgroundColor('#f7f6cc74')
    }
    .padding({left: 15})
    .width('100%')
    .margin({top: 10, bottom: 10})
  }
}

@Component
struct ThingComponent {
  @Prop isFinished: boolean;
  @Prop thing: string;

  @Builder displayIcon(icon: Resource) {
    Image(icon)
      .width(28)
      .height(28)
      .onClick(() => {
        this.isFinished = !this.isFinished;
      })
  }

  build() {
    // Task 1
    Row({space: 15}) {
      if (this.isFinished) {
        // 'app.media.finished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
        this.displayIcon($r('app.media.finished'));
      }
      else {
        // 'app.media.unfinished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
        this.displayIcon($r('app.media.unfinished'));
      }
      Text(`${this.thing}`)
        .fontSize(24)
        .decoration({type: this.isFinished ? TextDecorationType.LineThrough : TextDecorationType.None})
        .onClick(() => {
          this.thing += 'la';
        })
    }
    .height('8%')
    .width('90%')
    .padding({left: 15})
    .opacity(this.isFinished ? 0.3: 1)
    .border({width:1})
    .borderColor(Color.White)
    .borderRadius(25)
    .backgroundColor(Color.White)
  }
}

@Entry
@Component
struct Index {
  @State isFinished: boolean = false;
  @State data: TodoListData = new TodoListData(); // Data bound from the view to the view model

  build() {
    Column() {
      // All To-Do items.
      TodoComponent()

      // Select all.
      AllChooseComponent({isFinished: this.isFinished})

      List() {
        ForEach(this.data.planList, (item: string) => {
          // Task 1
          ThingComponent({isFinished: this.isFinished, thing: item})
            .margin(5)
        })
      }
    }
    .height('100%')
    .width('100%')
    .margin({top: 5, bottom: 5})
    .backgroundColor('#90f1f3f5')
  }
}
```

 The following figure shows an example.

![builder](./figures/MVVM_builder.gif)

### Summary

* By optimizing the code structure step by step, you can see that the @Entry component is the entry of the page. The build function of the @Entry component should only combine the required components, which is similar to building blocks. The child components called by the page are like building blocks, waiting to be called by the required page. The state variable is similar to the adhesive. When the UI refresh event is triggered, the state variable automatically refreshes the bound component to implement on-demand refresh of the page.
* Although the existing architecture does not use the MVVM design concept, the core concept of MVVM has been seen. The MVVM pattern is suitable for ArkUI development. In ArkUI, pages and components constitute the view layer. Pages organize components, and components are the elements. When a component needs to be updated, the state variable is used to drive the component to refresh and update the page. The data of the ViewModel comes from the Model layer.
* The code in the example is simple. However, as the functions increase, the code volume of the main page increases gradually. When more functions need to be added to the memo and the components of the main page need to be used on other pages, the MVVM pattern can be used to organize the project structure.

## Developing a To-Do List Through MVVM

The previous section shows the code organization mode in non-MVVM mode. As the code volume of the main page increases, a proper layering policy should be adopted to make the project structure clear and prevent components from referencing each other. This avoids the difficulty in updating functions during subsequent maintenance. This section describes how to use MVVM to refactor the code in the previous section based on the core file organization mode of MVVM.

### MVVM File Structure

```
├── src
│   ├── ets
│ │ ├── pages: stores page components.
│ │ ├── views: stores service components.
│ │ ├── shares: stores common components.
│ │ └── viewModel: data service.
│ │ │ ├── LoginViewModel.ets: ViewModel of the login page.
│ │ │ └── xxxViewModel.ets: ViewModel of other pages.
│
```

### Layered Design

**Model**

* The Model layer stores the core data structure of the application. This layer is not closely related to UI development. You can encapsulate the data structure based on your service logic.

**ViewModel**

> Note:
>
> The ViewModel layer stores data and provides data services and processing.

* The ViewModel layer is the data layer that serves views. It has the following two characteristics:
  1. Data is organized by page.
  2. Data on each page is lazy loaded.

**View**

The View layer is organized as required. You need to distinguish the following three types of components at this layer:

* Page components: provides the overall page layout, implements redirection between multiple pages, and processes foreground and background events.
* Business components: referenced by a page to construct a page.
* Shared components: shared by multiple projects.

> The differences between shared components and business components are as follows:
>
> A business component contains ViewModel data. Without ViewModel, the component cannot be executed.
>
> A shared component does not contain ViewModel data and requires external data. It contains a custom component that can work as long as external parameters (without service parameters) are met.

### Example

Reconstruct the code based on the MVVM pattern:

```
├── src
│   ├── ets
│   │   ├── model
│   │   │   ├── ThingModel.ets
│   │   │   └── TodoListModel.ets
│   │   ├── pages
│   │   │   ├── Index.ets
│   │   ├── views
│   │   │   ├── AllChooseComponent.ets
│   │   │   ├── ThingComponent.ets
│   │   │   ├── TodoComponent.ets
│   │   │   └── TodoListComponent.ets
│   │   ├── viewModel
│   │   │   ├── ThingViewModel.ets
│   │   │   └── TodoListViewModel.ets
│   └── resources
│   │   ├── rawfile
│   │   │   ├── default_tasks.json
│
```

The code is as follows:

  * ThingModel.ets

  ```typescript
  export default class ThingModel {
    thingName: string = 'Todo';
    isFinish: boolean = false;
  }
  ```

  * TodoListModel.ets

  ```typescript
  import { common } from '@kit.AbilityKit';
  import { util } from '@kit.ArkTS';
  import ThingModel from './ThingModel';

  export default class TodoListModel {
    things: Array<ThingModel> = [];

    constructor(things: Array<ThingModel>) {
      this.things = things;
    }

    async loadTasks(context: common.UIAbilityContext) {
      let getJson = await context.resourceManager.getRawFileContent('default_tasks.json');
      let textDecoderOptions: util.TextDecoderOptions = { ignoreBOM: true };
      let textDecoder = util.TextDecoder.create('utf-8', textDecoderOptions);
      let result = textDecoder.decodeToString(getJson, { stream: false });
      this.things = JSON.parse(result);
    }
  }
  ```

* Index.ets

  ```typescript
  import { common } from '@kit.AbilityKit';
  // import ViewModel
  import TodoListViewModel from '../viewModel/TodoListViewModel';

  // import View
  import { TodoComponent } from '../views/TodoComponent';
  import { AllChooseComponent } from '../views/AllChooseComponent';
  import { TodoListComponent } from '../views/TodoListComponent';

  @Entry
  @Component
  struct TodoList {
    @State todoListViewModel: TodoListViewModel = new TodoListViewModel(); // Data bound from the view to the view model.
    private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

    async aboutToAppear() {
      await this.todoListViewModel.loadTasks(this.context);
    }

    build() {
      Column() {
        Row({ space: 40 }) {
          // All To-Do items.
          TodoComponent()
          // Select all.
          AllChooseComponent({ todoListViewModel: this.todoListViewModel })
        }

        Column() {
          TodoListComponent({ thingViewModelArray: this.todoListViewModel.things })
        }
      }
      .height('100%')
      .width('100%')
      .margin({ top: 5, bottom: 5 })
      .backgroundColor('#90f1f3f5')
    }
  }
  ```

  * AllChooseComponent.ets

  ```typescript
  import TodoListViewModel from "../viewModel/TodoListViewModel";

  @Component
  export struct AllChooseComponent {
    @State titleName: string = 'Select All';
    @Link todoListViewModel: TodoListViewModel;

    build() {
      Row() {
        Button(`${this.titleName}`, { type: ButtonType.Capsule })
          .onClick(() => {
            Invoke the chooseAll method at the this.todoListViewModel.chooseAll(); // View layer to process the click event.
            this.titleName = this.todoListViewModel.isChoosen ? ' Select all' : 'Deselect all';
          })
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .backgroundColor('#f7f6cc74')
      }
      .padding({ left: this.todoListViewModel.isChoosen ? 15 : 0 })
      .width('100%')
      .margin({ top: 10, bottom: 10 })
    }
  }
  ```

  * ThingComponent.ets

  ```typescript
  import ThingViewModel from "../viewModel/ThingViewModel";

  @Component
  export struct ThingComponent {
    @ObjectLink thing: ThingViewModel;

    @Builder
    displayIcon(icon: Resource) {
      Image(icon)
        .width(28)
        .height(28)
        .onClick(() => {
          When a click event occurs at the this.thing.updateIsFinish(); // View layer, the updateIsFinish method at the ViewModel layer is called to process the logic.
        })
    }

    build() {
      // To-Do list
      Row({ space: 15 }) {
        if (this.thing.isFinish) {
          // 'app.media.finished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
          this.displayIcon($r('app.media.finished'));
        } else {
          // 'app.media.unfinished' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
          this.displayIcon($r('app.media.unfinished'));
        }

        Text(`${this.thing.thingName}`)
          .fontSize(24)
          .decoration({ type: this.thing.isFinish ? TextDecorationType.LineThrough : TextDecorationType.None })
          .onClick(() => {
            When a click event occurs at the this.thing.addSuffixes(); // View layer, the addSuffixes method at the ViewModel layer is called to process the logic.
          })
      }
      .height('8%')
      .width('90%')
      .padding({ left: 15 })
      .opacity(this.thing.isFinish ? 0.3 : 1)
      .border({ width: 1 })
      .borderColor(Color.White)
      .borderRadius(25)
      .backgroundColor(Color.White)
    }
  }
  ```

  * TodoComponent.ets

  ```typescript
  @Component
  export struct TodoComponent {
    build() {
      Row() {
        Text('To-Dos')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
      }
      .padding({ left: 15 })
      .width('50%')
      .margin({ top: 10, bottom: 10 })
    }
  }
  ```

  * TodoListComponent.ets

  ```typescript
  import ThingViewModel from "../viewModel/ThingViewModel";
  import { ThingViewModelArray } from "../viewModel/TodoListViewModel"
  import { ThingComponent } from "./ThingComponent";

  @Component
  export struct TodoListComponent {
    @ObjectLink thingViewModelArray: ThingViewModelArray;

    build() {
      Column() {
        List() {
          ForEach(this.thingViewModelArray, (item: ThingViewModel) => {
            // To-Do list
            ListItem() {
              ThingComponent({ thing: item })
                .margin(5)
            }
          }, (item: ThingViewModel) => {
            return item.thingName;
          })
        }
      }
    }
  }
  ```

  * ThingViewModel.ets

  ```typescript
  import ThingModel from "../model/ThingModel";

  @Observed
  export default class ThingViewModel {
    @Track thingName: string = 'Todo';
    @Track isFinish: boolean = false;

    updateTask(thing: ThingModel) {
      this.thingName = thing.thingName;
      this.isFinish = thing.isFinish;
    }

    updateIsFinish(): void {
      this.isFinish = !this.isFinish;
    }

    addSuffixes(): void {
      this.thingName += 'La'
    }
  }
  ```

  * TodoListViewModel.ets

  ```typescript
  import ThingViewModel from "./ThingViewModel";
  import { common } from "@kit.AbilityKit";
  import TodoListModel from "../model/TodoListModel";

  @Observed
  export class ThingViewModelArray extends Array<ThingViewModel> {
  }

  @Observed
  export default class TodoListViewModel {
    @Track isChoosen: boolean = true;
    @Track things: ThingViewModelArray = new ThingViewModelArray();

    async loadTasks(context: common.UIAbilityContext) {
      let todoList = new TodoListModel([]);
      await todoList.loadTasks(context);
      for (let thing of todoList.things) {
        let todoListViewModel = new ThingViewModel();
        todoListViewModel.updateTask(thing);
        this.things.push(todoListViewModel);
      }
    }

    chooseAll(): void {
      for (let thing of this.things) {
        thing.isFinish = this.isChoosen;
      }
      this.isChoosen = !this.isChoosen;
    }
  }
  ```

  * default_tasks.json

  ```typescript
  [
    {"thingName": "7.30 wake up", "isFinish": false},
    {"thingName": "8.30 breakfast", "isFinish": false},
    {"thingName": "11.30 lunch", "isFinish": false},
    {"thingName": "17.30 dinner", "isFinish": false},
    {"thingName": "21.30 midnight snack", "isFinish": false},
    {"thingName": "22.30 shower", "isFinish": false},
    {"thingName": "1.30 sleep", "isFinish": false}
  ]
  ```

  The code structure after the MVVM mode is split is clearer, and the module responsibilities are clearer. The event component, for example, the TodoListComponent component, needs to be used on the new page. You only need to import the component.

  The following figure shows the effect.

  ![MVVM_index.gif](./figures/MVVM_index.gif)

  

  
