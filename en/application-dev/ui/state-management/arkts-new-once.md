# \@Once: Implementing Initialization Once
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

To initialize data from an external source only once without accepting subsequent synchronization changes, you can use the \@Once decorator together with the \@Param decorator.

Before reading this document, read [\@Param](./arkts-new-param.md).

> **NOTE**
>
> The \@Once decorator is supported in custom components decorated with \@ComponentV2 since API version 12.
>
> This decorator can be used in atomic services since API version 12.
>
> This decorator can be used in ArkTS widgets since API version 23.

## Overview

The \@Once decorator accepts values passed only during variable initialization. Subsequent data source changes will not be synchronized to child components.

- \@Once must be used with \@Param. Using it independently or with other decorators is not allowed.
- \@Once does not affect the observation capability of \@Param. Only changes in data source are intercepted.
- The sequence of the variables decorated by \@Once and \@Param does not affect the actual functions.
- When \@Once and \@Param are used together, you can change the value of \@Param variables locally.

## Rules of Use

As an auxiliary decorator, the \@Once decorator does not have requirements on the decoration type and the capability of observing variables.

| \@Once Decorator| Description                                     |
| ---------------- | ----------------------------------------- |
| Parameters      | None                                     |
| Usage conditions        | It cannot be used independently and must be used together with the \@Param decorator.|


## Constraints

- \@Once can only be used together with \@Param inside custom components decorated with [\@ComponentV2](./arkts-create-custom-components.md#componentv2).

  <!-- @[once_param_componentV2_pair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArktsNewOnce/entry/src/main/ets/pages/MyComponent.ets) -->
  
  ``` TypeScript
  @ComponentV2
  struct MyComponent {
    @Param @Once onceParam: string = 'onceParam'; // Correct usage.
    @Once onceStr: string = 'Once'; // Incorrect usage. @Once cannot be used independently.
    @Local @Once onceLocal: string = 'onceLocal'; // Incorrect usage. @Once cannot be used with @Local.
  // ···
  }
  @Component
  struct Index {
    @Once @Param onceParam: string = 'onceParam'; // Incorrect usage.
  }
  ```

- The order of \@Once and \@Param does not matter. Both \@Param \@Once and \@Once \@Param are correct.

  <!-- @[once_param_order_irrelevant](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArktsNewOnce/entry/src/main/ets/pages/MyComponent.ets) -->
  
  ``` TypeScript
  @ComponentV2
  struct MyComponent {
  // ···
    @Param @Once param1: number = 0;
    @Once @Param param2: number = 0;
  // ···
  }
  ```

## Scenario

### Initializing Variables Only Once

\@Once is used for scenarios where a variable is expected to be initialized by synchronizing with the data source only once, and subsequent changes are no longer synchronized.

<!-- @[once_init_sync_noMore](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArktsNewOnce/entry/src/main/ets/pages/MyComponent.ets) --> 

``` TypeScript
@ComponentV2
struct ChildComponent {
  // The onceParam decorated with @Once is initialized and synchronized only once.
  @Param @Once onceParam: string = '';

  build() {
    Column() {
      Text(`onceParam: ${this.onceParam}`)
    }
  }
}

@Entry
@ComponentV2
struct MyComponent {
  // ...
  @Local message: string = 'Hello World';

  build() {
    Column() {
      Text(`Parent message: ${this.message}`)
      Button('change message')
        .onClick(() => {
          this.message = 'Hello Tomorrow';
        })
      ChildComponent({ onceParam: this.message })
    }
  }
}
```

### Changing the \@Param Variables Locally

When \@Once is used together with \@Param, it can lift the restriction that \@Param cannot be modified locally and can trigger UI re-rendering. In this case, the effect of using \@Param and \@Once is similar to [\@Local](arkts-new-local.md), but \@Param and \@Once can also receive initial values passed from outside.

<!-- @[once_param_modify_init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArktsNewOnce/entry/src/main/ets/pages/Index.ets) --> 

``` TypeScript
@ObservedV2
class Info {
  @Trace name: string;
  constructor(name: string) {
    this.name = name;
  }
}
@ComponentV2
struct Child {
  // When @Once is used together with @Param, it can be modified locally and can trigger UI re-rendering.
  @Param @Once onceParamNum: number = 0;
  @Param @Once @Require onceParamInfo: Info;

  build() {
    Column() {
      Text(`Child onceParamNum: ${this.onceParamNum}`)
      Text(`Child onceParamInfo: ${this.onceParamInfo.name}`)
      Button('changeOnceParamNum')
        .onClick(() => {
          this.onceParamNum++;
        })
      Button('changeParamInfo')
        .onClick(() => {
          this.onceParamInfo = new Info('Cindy');
        })
    }
  }
}
@Entry
@ComponentV2
struct Index {
  @Local localNum: number = 10;
  @Local localInfo: Info = new Info('Tom');

  build() {
    Column() {
      Text(`Parent localNum: ${this.localNum}`)
      Text(`Parent localInfo: ${this.localInfo.name}`)
      Button('changeLocalNum')
        .onClick(() => {
          this.localNum++;
        })
      Button('changeLocalInfo')
        .onClick(() => {
          this.localInfo = new Info('Cindy');
        })
      Child({
        onceParamNum: this.localNum,
        onceParamInfo: this.localInfo
      })
    }
  }
}
```
