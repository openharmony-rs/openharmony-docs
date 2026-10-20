# \@CustomEnv: Custom Environment Variable
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @songyanhong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4d4c58ec461e3e07b3e5682a39329e8060373a85 translatedAt=2026-10-12T09:08:29.786Z pushedAt=2026-10-12T10:14:31.169Z -->

[\@CustomEnv](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#customenv) can be used to obtain custom environment variables. Developers can set custom environment variables via the [.customEnv](../reference/apis-arkui/arkui-ts/ts-container-with-env.md#customenv) API of the [WithEnv](../reference/apis-arkui/arkui-ts/ts-container-with-env.md) component, and read the variable value corresponding to the same [CustomEnvKey\<S\>](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#customenvkeys) in child components through the [\@CustomEnv](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#customenv) decorator. This mechanism implements data transparent transmission within the component tree, enabling parent-child components to interact based on environment variables while keeping the code decoupled.

>**NOTE**
>
> Starting from API version 26.0.0, [\@CustomEnv](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#customenv) supports use in [\@Component](./state-management/arkts-create-custom-components.md#component) and [\@ComponentV2](./state-management/arkts-create-custom-components.md#componentv2).
>
> Starting from API version 26.0.0, this decorator supports use in atomic services.

## Overview
[\@CustomEnv](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#customenv) is a reactive custom environment variable decorator. Its capabilities include:
- Reads the corresponding custom environment variable information based on the input parameter. For details, see [\@CustomEnv Usage Method](#customenv-usage-method).
- When the custom environment variable changes, it notifies the \@CustomEnv decorated variable to update and triggers the refresh of the associated component of \@CustomEnv to update the UI content.
- Variables decorated with \@CustomEnv are read-only. You are not allowed to assign the variable as a whole after initialization. To update the value of such a variable, it must be updated via the parent component's WithEnv component in conjunction with the `.customEnv()` method. Attempting to assign a value to a \@CustomEnv variable will result in a compilation error.

You can use the `@CustomEnv` decorator and pass in a custom key to declare a reactive environment variable. For an example, see [Supporting Custom Keys and Values](#supporting-custom-keys-and-values).
## \@CustomEnv Usage Method

### Decorator Description

| \@CustomEnv decorator | Description |
| ------------------- | ------------------------------------------------------------ |
| Decorator parameter | The input parameter of the [\@CustomEnv](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#customenv) decorator must be of the [CustomEnvKey\<S\>](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#customenvkeys) type. |
| Decoratable variable type | Basic types such as string, number, boolean, and enum, object types such as Object and class, and built-in types such as Array, Date, Map, and Set. null, undefined, and union types are supported. |
| Initial value of decorated variable | Must be initialized locally; external initialization is not allowed. |

### Variable Passing

| Passing rule       | Description                                                         |
| -------------- | ------------------------------------------------------------ |
| Initialization from parent component | Variables decorated by \@CustomEnv only allow local initialization and cannot be initialized from outside.    |
| Initialization of \@CustomEnv decorated variable | When initializing a variable decorated by \@CustomEnv, it will first recursively search upwards for a value with the same key injected via WithEnv.customEnv in the parent component; if found, that injected value is used, otherwise the local initial value is used.|

### Observing Changes

When the value of a variable decorated by `@Local` changes due to a tap on the update button, the value set via the `.customEnv()` method in the WithEnv component will also notify `@CustomEnv`. At this point, the variable decorated by `@CustomEnv` in the child component will update to the latest value and trigger a UI re-render, implementing a complete reactive update chain. For an example, see [Reactive Update Capability](#reactive-update-capability).


## \@CustomEnv and \@Env Capability Comparison
Both \@CustomEnv and [\@Env](./arkts-env-system-property.md) are related to environment variables. See the table below for a specific capability comparison.

| Capability | \@CustomEnv | \@Env|
| ------------------ | ------------------ | ------------------ |
|Starting API version|Supported from API version 26.0.0.|Supported from API version 22.|
|Support parameter|Customized CustomEnvKey type object.|[Enumeration values of SystemProperties](./arkts-env-system-property.md#supported-parameters).<br/>After API version 26.0.0, supports [SystemProperties](./arkts-env-system-property.md#supported-parameters)\|[SystemEnvKey\<T\>](./arkts-env-system-property.md#supported-parameters) type parameters.|
|Usage form|\@CustomEnv is a decorator that can be declared in \@Component or \@ComponentV2. The environment variable is set by the developer via the customEnv API of WithEnv.|\@Env is a decorator that can be declared in \@Component or \@ComponentV2 to directly read system environment variables.<br/>After API version 26.0.0, developers can set system environment variables of the [SystemEnvKey\<T\>](./arkts-env-system-property.md#supported-parameters) type via the env API of WithEnv.|
|Source of value|An initial default value is given or set via the .customEnv() method of the WithEnv component.|System environment variables set via the env API of WithEnv.|
|Whether it has reactive capability|Yes. When the value set by WithEnv changes, it notifies the \@CustomEnv decorated variable to update and notifies the associated component to refresh.|Yes. When the system environment variable changes, it notifies the \@Env decorated variable to update and notifies the associated component to refresh.|

## Constraints
- \@CustomEnv is only supported in \@Component and \@ComponentV2; otherwise, a compilation error occurs.
```ts

const custom = CustomEnvKey.create<string>();
// Incorrect usage. A compilation error occurs.
class CustomEnvKey {
  @CustomEnv(custom) customVarName: string = 'hello world'; 
}
// Correct usage
@Entry
@Component
struct Index {
  @CustomEnv(custom) customVarName: string = 'hello world'; 

  build() {
    Column() {
      Text(`this is @CustomEnv page`)
    }
  }
}
```

- The input parameter of \@CustomEnv must be a global constant created via the [create\<T\>](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#createt) method of [CustomEnvKey\<S\>](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#customenvkeys), and its type must be a developer-defined CustomEnvKey\<S\>; otherwise, a compilation error will occur. If the developer bypasses the compilation check, a runtime error will occur.

```ts
const custom = CustomEnvKey.create<string>();
@Entry
@Component
struct Index {
  @CustomEnv(custom) customVarName: string = 'hello world'; // Correct usage
  // cus: CustomEnvKey<string> = CustomEnvKey.create<string>()
  // @CustomEnv(this.cus) customVarName: string = 'hello world';  // Incorrect usage, will cause a compilation error

  build() {
    Column() {
      Text(`this is @CustomEnv page`)
    }
  }
}
```

- Variables decorated by \@CustomEnv are read-only attributes. Developers are not allowed to perform assignment operations; otherwise, a compilation error occurs.
```ts
import { WithEnv, WithEnvAttribute } from '@kit.ArkUI';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  @CustomEnv(custom) customVarName: string = 'hello world';
  @Local newVarName: string = 'customMessage';

  build() {
    Column() {
      Button('update')
        .onClick(() => {
          this.customVarName = 'Change Message'; // Incorrect usage, compilation error.
        })

      WithEnv() {
        Child()
      }.customEnv(custom, this.newVarName)

    }
  }
}
```

- Variables decorated by \@CustomEnv cannot be initialized by passing parameters from the parent component. If a value is assigned in the form of a parameter during component instantiation, it will be intercepted and an error will be reported during the compilation phase.
```ts

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct PageOne {
  @CustomEnv(custom) defaultMessage: string = 'Hello';

  build() {
    Column() {
      Child({ firstValue: this.defaultMessage }) // Incorrect usage. Compilation error.
    }
  }
}

@ComponentV2
struct Child {
  @CustomEnv(custom) firstValue: string = 'world';

  build() {
    Column() {
      Text(this.firstValue)
    }
  }
}
```

- \@CustomEnv does not look up the value set by \@CustomEnv with the same key in \@Component/\@ComponentV2.
```ts

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  @CustomEnv(custom) customMessage: string = 'parent';

  build() {
    Column() {
      Child()
    }
  }
}

@ComponentV2
struct Child {
  @CustomEnv(custom) customMessage: string = 'child';

  build() {
    Column() {
      Text(`Child: ${this.customMessage}`);
    }
  }
}
```

## \@CustomEnv Initialization Process

The \@CustomEnv variable initialization follows the process below:

1. Find whether the corresponding key exists in the WithEnv component:
   - Determine whether the current parent component is a WithEnv component.
   - If not, continue searching upward until the root node.
   - If a WithEnv component with the corresponding key is found, obtain the environment variable value provided by the component and assign it to the variable decorated by \@CustomEnv.
2. Initial value of the variable declared with \@CustomEnv:
   - If no WithEnv component with the corresponding key is found, the local initial value of the \@CustomEnv decorated variable is used.

The flowchart is shown in the figure below.

![image](./figures/customenv-flow.png)

## Use Cases

### Supporting Custom Keys and Values

The newly added state management decorator `@CustomEnv` supports custom key configuration and allows you to specify the initial value of the variable. The syntax is: `@CustomEnv(custom) customVarName: string = 'hello world'`. Here, `custom` is the custom environment variable key defined by the developer, of type [CustomEnvKey\<S\>](../reference/apis-arkui/arkui-ts/ts-custom-env-property.md#customenvkeys), and `hello world` is the initial value of the variable.

<!-- @[CustomValue]
(https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomValuePage.ets) -->
```ts

const customString = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct CustomValue {
  // 1. Implements the defined key and value
  @CustomEnv(customString) customVarName: string = 'hello world';

  build() {
    Column() {
      Text(`Parent: ${this.customVarName}`)
    }
  }
}
```

The running effect is shown in the figure below.

![image](./figures/custom-env-9.png)

### \@CustomEnv Supports Multiple Data Types

\@CustomEnv supports variable declarations of both simple and complex types. Simple types include string, number, boolean, enum, etc.; complex types include object types such as class and Object.

<!-- @[CustomEnvSupportClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvValueClassPage.ets) -->
```ts

@ObservedV2
class CustomVal {
  @Trace public id: number = 123;
  @Trace public userName: string = 'admin';
}

const customStr = CustomEnvKey.create<string>();
const customNum = CustomEnvKey.create<number>();
const customBool = CustomEnvKey.create<boolean>();
const customObj = CustomEnvKey.create<CustomVal>();

@Entry
@ComponentV2
struct ClassIndex {
  @CustomEnv(customStr) customStrVarName: string = 'hello world';
  @CustomEnv(customNum) customNumVarName: number = 1;
  @CustomEnv(customBool) customBoolVarName: boolean = true;
  @CustomEnv(customObj) customObjVarName: CustomVal = new CustomVal();

  build() {
    Column() {
      Text(`customStrVarName type is ${typeof this.customStrVarName}`)
      Text(`customNumVarName type is ${typeof this.customNumVarName}`)
      Text(`customBoolVarName type is ${typeof this.customBoolVarName}`)
      Text(`customObjVarName type is ${typeof this.customObjVarName}`)
    }
  }
}
```

The running effect is shown in the figure below.

![image](./figures/custom-env-11.png)

### \@CustomEnv Supports Default Initial Values

When a variable decorated with \@CustomEnv in a child component searches upward for an environment variable value but does not find a matching WithEnv component, the variable will use the initial value specified at declaration as the default value.

<!-- @[CustomEnvDefaultValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvDefaultValPage.ets) -->
```ts

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct DefaultValue {
  build() {
    Column() {
      DefaultChild()
    }
  }
}

@ComponentV2
struct DefaultChild {
  @CustomEnv(custom) customMessage: string = 'default content';

  build() {
    Column() {
      // At this point, the content in Text is displayed as: Child: default content. 
      Text(`Child: ${this.customMessage}`);
    }
  }
}
```

The running effect is shown in the figure below.

![image](./figures/custom-env-10.png)

### Environment Variable Lookup Follows the Nearest-First Principle

When a child component uses a variable decorated with @CustomEnv to obtain an environment variable value, it traverses up the component tree to find the corresponding **WithEnv** components and prioritizes the value provided by the **WithEnv** component closest to the current child component. If the nearest **WithEnv** component does not define that key, the search continues to outer layers until a matching value is found. If no match is found, the local default value is used.

In the following example, the \@CustomEnv(custom) declared in the Child component will be assigned by the innermost WithEnv closest to it, resulting in the final value 'the nearest WithEnv'.

<!-- @[CustomEnvNearValue]
(https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvNearPage.ets) -->
```ts
import { WithEnv } from '@kit.ArkUI';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct NearPage {
  build() {
    Column() {
      // Nearest-first principle demonstration
      WithEnv() {
        // Prioritize searching for WithEnv at this level
        WithEnv() {
          // Nearest-first principle, display 'the nearest WithEnv'
          NearChild()
        }.customEnv(custom, 'the nearest WithEnv')
      }.customEnv(custom, 'outer WithEnv')
    }
  }
}

@ComponentV2
struct NearChild {
  // @CustomEnv searches upward for parent components, prioritizing WithEnv
  @CustomEnv(custom) customMessage: string = 'default content';

  build() {
    Column() {
      Text(`Child: ${this.customMessage}`);
    }
  }
}
```

The running effect figure is shown below.

![image](./figures/custom-env-12.png)

### Reactive Update Capability

When clicking the update button causes the value of a variable decorated with @Local to change, the value set via the **.customEnv()** method in the **WithEnv** component will also notify @CustomEnv. At this point, the variable decorated with @CustomEnv in the child component will be updated with the latest value and trigger a UI re-render, thus implementing a complete reactive update chain.

<!-- @[CustomEnvUpdateValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvValUpdatePage.ets) -->
```ts
import { WithEnv, WithEnvAttribute } from '@kit.ArkUI';

const customMsge = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct UpdateIndex {
  @Local customMsg: string = 'Hello';

  build() {
    Column() {
      Button('update')
        .onClick(() => {
          this.customMsg = 'Hello World';
        })

      WithEnv() {
        // With the WithEnv component, Child's customMessage displays the value 'Hello' provided by WithEnv. After tapping the Button, the value updates to 'Hello World'.
        UpdateChild()
      }.customEnv(customMsge, this.customMsg)

    }
  }
}

@ComponentV2
struct UpdateChild {
  @CustomEnv(customMsge) customMessage: string = 'default content';

  build() {
    Column() {
      Text(`Child: ${this.customMessage}`);
    }
  }
}
```

The running effect is shown in the figure below.

![image](./figures/customenv_1.gif)

### \@Watch and \@Monitor Listening to \@CustomEnv Decorated Variables

In \@Component, you can use [\@Watch](state-management/arkts-watch.md) to listen for changes to variables decorated by `@CustomEnv`.

<!-- @[CustomEnvSupportWatch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvSupportWatchPage.ets) -->
```ts
import { WithEnv, WithEnvAttribute } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

const customWatch: CustomEnvKey<number> = CustomEnvKey.create<number>();

@Entry
@Component
struct WatchIndex {
  @State message: number = 1;

  build() {
    Column() {
      Button('update').onClick(() => {
        this.message++;
      })

      WithEnv() {
        WatchChild()
      }.customEnv(customWatch, this.message)
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
  }
}

@Component
struct WatchChild {
  @CustomEnv(customWatch) @Watch('onParentValChanged') parentVal: number = 100;

  // Watch callback
  onParentValChanged() {
    hilog.info(0x0000, 'testTag','@Watch message update');
  }

  build() {
    Column() {
      Text('parentVal is: ' + this.parentVal)
        .fontSize(22);
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```
In the above example:

Tap 'update' to change the value of message, which will trigger the callback of the \@Watch decorator and output the corresponding log.

The running effect is shown in the figure below.

![image](./figures/custom-env-16.png)

When the internal properties of a variable decorated by `@CustomEnv` change, the callback is also triggered.

<!-- @[CustomEnvDeepWatch]
(https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvSupportDeepWatchPage.ets) -->
```ts
import { WithEnv } from '@kit.ArkUI';

const customDeepWatch = CustomEnvKey.create<number[][]>()

@Entry
@Component
struct BuildIn_Watch {
  @State message: number[][] = [[1, 2]];

  build() {
    Column() {
      Button('ss').onClick(() => {
        this.message[0][0]++
      })
      WithEnv() {
        Child()
      }.customEnv(customDeepWatch, this.message)
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct Child {
  @Watch('update') @CustomEnv(customDeepWatch) msg: number[][] = [[3, 4]]

  update() {
    console.info(`TabContent message callback func ${this.msg}`)
  }

  build() {
    Column() {
      Text(this.msg[0][0] + '')
    }
  }
}
```

In the preceding example:

Tap 'ss' to change the value of message, which will trigger the callback decorated by \@Watch and output the corresponding log.

The following figure shows the running effect.

![image](./figures/DeepWatch.png)

In \@ComponentV2, \@Monitor can be used to listen for changes to \@CustomEnv decorated variables. Note that the \@Monitor listening callback is triggered only when the \@CustomEnv decorated variable is assigned as a whole; changes to its internal properties will not trigger the callback.

<!-- @[CustomEnvSupportMonitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvSupportMonitorPage.ets) -->
```ts
import { WithEnv, WithEnvAttribute } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

const customMon = CustomEnvKey.create<number>();

@Entry
@ComponentV2
struct MonitorTest {
  @Local message: number = 20;

  build() {
    Row() {
      Column() {
        Button('change message').onClick(() => {
          this.message++;
        })
        WithEnv() {
          MonitorChild()
        }.customEnv(customMon, this.message)
      }
      .width('100%')
    }
    .height('100%')
  }
}

@ComponentV2
struct MonitorChild {
  @CustomEnv(customMon) message: number = 0;

  @Monitor('message')
  onStrChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      hilog.info(0x0000, 'testTag',
        `${path} changed from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
    });
  }

  build() {
    Column() {
      Text('message' + `${this.message}`)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
  }
}
```

In the example above:

Click 'change message' to change the value of message, which will trigger the \@Monitor decorator's callback and output the corresponding log.

The running effect is shown in the figure below.

![image](./figures/customenv_8.gif)

### \@CustomEnv Supports Component Freezing

When the component where \@CustomEnv is located is in an inactive state and the key corresponding to WithEnv changes, the callback of the \@Monitor decorator in the inactive state will not be notified. When the inactive \@CustomEnv returns to the active state, the callback of the \@Monitor decorator will be notified.

Note: During the first render, the Tab only creates the currently displayed TabContent. All TabContent components are created only after switching through all of them.

<!-- @[CustomEnvSupportFreezed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvSupportComponentFreezePage.ets) -->
```ts
import { WithEnv, WithEnvAttribute } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

const custom = CustomEnvKey.create<number>();

@Entry
@ComponentV2
struct TabContentTest {
  @Local message: number = 20;
  @Local data: number[] = [0, 1];

  build() {
    Row() {
      Column() {
        Button('change message').onClick(() => {
          this.message++;
        })
        WithEnv() {
          Tabs() {
            ForEach(this.data, (item: number) => {
              TabContent() {
                FreezeChild()
              }.tabBar(`tab${item}`)
            }, (item: number) => item.toString())
          }
        }.customEnv(custom, this.message)
      }
      .width('100%')
    }
    .height('100%')
  }
}

@ComponentV2({ freezeWhenInactive: true })
struct FreezeChild {
  @CustomEnv(custom) message: number = 0;
  @Param index: number = 0;

  @Monitor('message')
  onStrChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      hilog.info(0x0000, 'testTag',
        `${path} changed from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
    });
  }

  build() {
    Column() {
      Text('message' + `${this.message}, index: ${this.index}`)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
  }
}
```

In the above example:

1. Tap 'change message' to change the value of message. The method onStrChange registered in \@Monitor in the currently displayed TabContent component is triggered.

2. Tap 'tab1' in the TabBar to switch to another TabContent. The TabContent state changes from inactive to active, and the corresponding method onStrChange registered in \@Monitor is triggered. 

3. Tap 'change message' again to change the value of message. Only the method onStrChange registered in \@Monitor in the currently displayed TabContent child component is triggered. Other inactive TabContent components do not trigger \@Monitor.

The running effect is shown in the figure below.

![image](./figures/customenv_2.gif)


### Decorating Array type variables

When the decorated object is an Array, the data in the Array can be updated by calling the Array APIs `push`, `pop`, `shift`, `unshift`, `splice`, `copyWithin`, `fill`, `reverse`, `sort`.

<!-- @[CustomEnvArray]
(https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvSupportArrayPage.ets) -->
```ts

class Fruit {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }
}

const customArray = CustomEnvKey.create<Fruit[]>();

@Entry
@ComponentV2
struct FruitPage {
  @CustomEnv(customArray) fruits: Fruit[] = [new Fruit('apple'), new Fruit('banana')]; // Use @CustomEnv to decorate an Array type variable.

  build() {
    Row() {
      Column() {
        ForEach(this.fruits, (item: Fruit) => {
          Text(`${item.name}`)
            .fontSize(20)
            .margin(10)
        })
        // Add array elements to trigger UI refresh
        Button('Push element')
          .onClick(() => {
            this.fruits.push(new Fruit('cherry'));
          })
          .width(300)
          .margin(10)
        // Reverse array elements, triggering UI refresh
        Button('Reverse array')
          .onClick(() => {
            this.fruits.reverse();
          })
          .width(300)
          .margin(10)
        // Fill array with the same element, triggering UI refresh
        Button('Fill array')
          .onClick(() => {
            this.fruits.fill(new Fruit('apple'));
          })
          .width(300)
          .margin(10)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

The running effect figure is shown below.

![image](./figures/customenv_4.gif)

### Decorating Date Type Variables

When the decorated object is a Date, the properties of the Date can be updated by calling the Date APIs `setFullYear`, `setMonth`, `setDate`, `setHours`, `setMinutes`, `setSeconds`, `setMilliseconds`, `setTime`, `setUTCFullYear`, `setUTCMonth`, `setUTCDate`, `setUTCHours`, `setUTCMinutes`, `setUTCSeconds`, `setUTCMilliseconds`.

<!-- @[CustomEnvDate]
(https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvSupportDatePage.ets) -->
```ts

const customDate = CustomEnvKey.create<Date>();

@Entry
@ComponentV2
struct DatePickerExample {
  @CustomEnv(customDate) selectedDate: Date = new Date('2021-08-08'); // Use @CustomEnv to decorate a Date type variable.

  build() {
    Row() {
      Column() {
        // Call the setFullYear API of Date to modify the year, triggering a UI refresh
        Button('increase the year by 1')
          .onClick(() => {
            this.selectedDate.setFullYear(this.selectedDate.getFullYear() + 1);
          })
          .margin(10)
          .width(300)
        // Call the setMonth API of Date to modify the month, triggering a UI refresh
        Button('increase the month by 1')
          .onClick(() => {
            this.selectedDate.setMonth(this.selectedDate.getMonth() + 1);
          })
          .margin(10)
          .width(300)
        // Call the setDate API of Date to modify the day, triggering a UI refresh
        Button('increase the day by 1')
          .onClick(() => {
            this.selectedDate.setDate(this.selectedDate.getDate() + 1);
          })
          .margin(10)
          .width(300)
        DatePicker({
          start: new Date('1970-1-1'),
          end: new Date('2100-1-1'),
          selected: this.selectedDate
        }).margin(20)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

The running effect is shown in the figure below.

![image](./figures/customenv_5.gif)

### Decorating Map Type Variables

When the decorated object is a Map, the data in the Map can be updated by calling the Map APIs `set`, `clear`, and `delete`.


<!-- @[CustomEnvMap]
(https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvSupportMapPage.ets) -->
```ts

const customMap = CustomEnvKey.create<Map<string, number>>();

@Entry
@ComponentV2
struct MapSample {
  @CustomEnv(customMap) fruits: Map<string, number> = new Map([['apple', 1], ['banana', 2]]); // Use @CustomEnv to decorate a Map type variable.

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.fruits.entries()), (item: [string, number]) => {
          Text(`key: ${item[0]}, value: ${item[1]}`)
            .fontSize(20)
            .margin(10)
        })
        // Add a key-value pair, triggering UI refresh
        Button('Set entry cherry')
          .onClick(() => {
            this.fruits.set('cherry', 3);
          })
          .width(300)
          .margin(10)
        // Update a key-value pair, triggering UI refresh
        Button('Update entry apple')
          .onClick(() => {
            this.fruits.set('apple', 4);
          })
          .width(300)
          .margin(10)
        // Delete a key-value pair, triggering UI refresh
        Button('Delete entry apple')
          .onClick(() => {
            this.fruits.delete('apple');
          })
          .width(300)
          .margin(10)
        // Clear the map, triggering UI refresh
        Button('Clear map')
          .onClick(() => {
            this.fruits.clear();
          })
          .width(300)
          .margin(10)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

The running effect is shown in the figure below.

![image](./figures/customenv_6.gif)

### Decorating Set Type Variables

When the decorated object is a **Set**, the data in the **Set** can be updated by calling the **Set** APIs `add`, `clear`, and `delete`.

<!-- @[CustomEnvSet]
(https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvSupportSetPage.ets) -->
```ts

const customSet = CustomEnvKey.create<Set<string>>();

@Entry
@ComponentV2
struct SetSample {
  @CustomEnv(customSet) fruits: Set<string> = new Set(['apple', 'banana']); // Use @CustomEnv to decorate a Set type variable.

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.fruits.entries()), (item: [string, string]) => {
          Text(`${item[0]}`)
            .fontSize(20)
            .margin(10)
        })
        // Add element, triggering UI refresh
        Button('Add element')
          .onClick(() => {
            this.fruits.add('cherry');
          })
          .width(300)
          .margin(10)
        // Delete element, trigger UI refresh
        Button('Delete element apple')
          .onClick(() => {
            this.fruits.delete('apple');
          })
          .width(300)
          .margin(10)
        // Clear Set, trigger UI refresh
        Button('Clear set')
          .onClick(() => {
            this.fruits.clear();
          })
          .width(300)
          .margin(10)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

The running effect figure is as follows.

![image](./figures/customenv_7.gif)

### V1/V2 Mixed Use of \@CustomEnv

\@CustomEnv can be used in \@Component and \@ComponentV2, and it follows the [basic rules for V1/V2 mixing](./state-management/arkts-v1-v2-mixusage.md). When a variable decorated by \@CustomEnv is passed to V1, it follows the rule that V1 state variable decorators cannot be used with classes decorated by [\@ObservedV2](./state-management/arkts-new-observedV2-and-trace.md). When a variable decorated by \@CustomEnv is passed to V2, it follows the rule that only [\@Param](./state-management/arkts-new-param.md) in V2 can receive external variables.



- When a variable decorated with \@CustomEnv is passed to V1, it follows the following rule: V1 state variable decorators cannot receive classes decorated with \@ObservedV2.

<!-- @[V2ToV1Mix]
(https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvObservedV2MixV2ToV1Page.ets) -->
```ts
@ObservedV2
class CustomDefaultvalue {
  @Trace public defaultVal: string = 'hello';
}

const customOne = CustomEnvKey.create<string>();
const customTwo = CustomEnvKey.create<CustomDefaultvalue>();

@Entry
@ComponentV2
struct PageTwo {
  @CustomEnv(customOne) defaultMessage: string = 'parent Value';
  @CustomEnv(customTwo) defaultMessage1: CustomDefaultvalue = new CustomDefaultvalue();

  build() {
    Column() {
      Text(`Parent Value is :${this.defaultMessage}`)
      PageTwoChild({ message: this.defaultMessage }) // Correct usage.
      // Child({ customMessage: this.defaultMessage1 }) // Incorrect usage, compilation error.
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct PageTwoChild {
  @Require @Prop message: string;
  // @Prop customMessage: CustomValue; //  Incorrect usage, the type decorated by a V1 state variable decorator cannot be a class decorated by ObservedV2.

  build() {
    Column() {
      Text(`Child value is :${this.message}`)
    }
    .height('100%')
    .width('100%')
  }
}
```

The running effect is shown in the figure below.

![image](./figures/custom-env-13.png)

- When a variable decorated by \@CustomEnv is passed to V2, it follows the rule that only \@Param can receive external variables in V2.

<!-- @[V1ToV2MixParam]
(https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvMixParamV1ToV2Page.ets) -->
```ts
@ObservedV2
class CustomStrValue {
  @Trace public defaultVal: string = 'hello';
}

const customMix = CustomEnvKey.create<CustomStrValue>();

@Entry
@Component
struct PageOne {
  @CustomEnv(customMix) defaultMessage: CustomStrValue = new CustomStrValue();

  build() {
    Column() {
      Text(this.defaultMessage.defaultVal)
      Button('update')
        .onClick(() => {
          this.defaultMessage.defaultVal = 'hello world';
        })
      PageOneChild({ message: this.defaultMessage })
    }
    .height('100%')
    .width('100%')
  }
}

@ComponentV2
struct PageOneChild {
  @Require @Param message: CustomStrValue;

  build() {
    Column() {
      Text(`Child Value is : ${this.message.defaultVal}`)
    }
    .height('100%')
    .width('100%')
  }
}
```

The running effect is shown in the figure below.

![image](./figures/custom-env-14.gif)

- \@CustomEnv provides the observation capability of state management V2. When the type of a variable decorated by \@CustomEnv is decorated by \@Observed, you need to call [enableV2Compatibility](../reference/apis-arkui/js-apis-stateManagement.md#enablev2compatibility19) to enable it to observe class properties. Otherwise, changes to class properties cannot be observed.

<!-- @[CustomEnvWithenableV2Compatibility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/CustomEnvSample/entry/src/main/ets/pages/CustomEnvObservedMixV2ToV1WithenableV2CompatibilityPage.ets) -->
```ts
import { UIUtils } from '@kit.ArkUI';

@Observed
class CustomValue {
  @Track public defaultVal: string = 'hello';
}

const custom = CustomEnvKey.create<CustomValue>();

@Entry
@ComponentV2
struct ComponentV2Page {
  @CustomEnv(custom) defaultMessage: CustomValue = UIUtils.enableV2Compatibility(new CustomValue());

  build() {
    Column() {
      Text(this.defaultMessage.defaultVal)
      Button('update')
        .onClick(() => {
          this.defaultMessage.defaultVal = 'hello world';
        })
      ComponentPageChild({ message: this.defaultMessage })
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct ComponentPageChild {
  @ObjectLink message: CustomValue;

  build() {
    Column() {
      Text(`Child value is : ${this.message.defaultVal}`)
    }
    .height('100%')
    .width('100%')
  }
}
```

The running effect is shown in the figure below.

![image](./figures/custom-env-15.gif)