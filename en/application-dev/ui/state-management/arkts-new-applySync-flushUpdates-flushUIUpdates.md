# applySync/flushUpdates/flushUIUpdates APIs: Synchronous Update

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

To synchronize the update of state management V2 and animation effects such as [animateTo](../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#animateto), you can use the [applySync](../../reference/apis-arkui/js-apis-stateManagement.md#applysync22), [flushUpdates](../../reference/apis-arkui/js-apis-stateManagement.md#flushupdates22), or [flushUIUpdates](../../reference/apis-arkui/js-apis-stateManagement.md#flushuiupdates22) API.

> **NOTE**
>
> Since API version 22, you can use the applySync, flushUpdates, and flushUIUpdates APIs in UIUtils to implement synchronous dirty data marking for state management V2.

## Overview

Unlike state management V1, state management V2 does not immediately [mark the variable as dirty](./arkts-state-management-glossary.md#mark-dirty). Instead, it throws a Promise microtask (with a lower priority than a macrotask). The microtask processes the dirty marking of the custom component only after the current macrotask is executed. For details about the differences, see [Differences Between V1 State Variable Update and V2 State Variable Update](./arkts-v1-v2-update-difference.md#differences-between-v1-state-variable-update-and-v2-state-variable-update). The animateTo animation immediately refreshes the marked dirty node to determine the first frame of the animation. If the V2 state variable is used in the animation and the state variable is modified before the animation, the first frame of the animation does not meet the expectation because the change of the state variable is not marked dirty when animateTo is called. Therefore, the **applySync**, **flushUpdates**, and **flushUIUpdates** APIs are introduced to achieve synchronized dirty marking for state management V2, thus ensuring that animation effects meet expectations.

To use the **applySync/flushUpdates/flushUIUpdates** APIs, you need to import the UIUtils tool.

```ts
import { UIUtils } from '@kit.ArkUI';
```

## Use Rules

- The **applySync** API is used to synchronously refresh the specified state variables. It accepts a closure function and only refreshes the modifications made within the closure function, including updating [@Computed](./arkts-new-computed.md) calculations, triggering [@Monitor](./arkts-new-monitor.md) callbacks, and re-rendering UI nodes.
  
  <!-- @[ApplySyncUse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/ApplySyncUse.ets) -->
  
  ``` TypeScript
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Index {
    @Local w: number = 50; // Width.
    @Local h: number = 50; // Height.
    @Local message: string = 'Hello';
  
    @Monitor('message')
    onMessageChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
    }
  
    build() {
      Column() {
        Button('change size')
          .margin(20)
          .onClick(() => {
            // Values are changed additionally before the animation is executed.
            UIUtils.applySync(() => {
              this.w = 100;
              this.h = 100;
              this.message = 'Hello World';
            });
  
            this.getUIContext().animateTo({
              duration: 1000
            }, () => {
              this.w = 200;
              this.h = 200;
              this.message = 'Hello ArkUI';
            });
          })
          // ...
        Column() {
          Text(`${this.message}`)
        }
        .backgroundColor('#ff17a98d')
        .width(this.w)
        .height(this.h)
      }
    }
  }
  ```

  ![applySync-flushUpdates-flushUIUpdates](./figures/applySync-flushUpdates-flushUIUpdates.gif)
  
- The **flushUpdates** API is used to synchronously refresh all state variable modifications before this function is called, including updating the @Computed calculation, @Monitor callback, and re-rendering the UI node.
  
  <!-- @[FlushUpdatesUse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/FlushUpdatesUse.ets) -->
  
  ``` TypeScript
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Index {
    @Local w: number = 50; // Width.
    @Local h: number = 50; // Height.
    @Local message: string = 'Hello';
  
    @Monitor('message')
    onMessageChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
    }
  
    build() {
      Column() {
        Button('change size')
          .margin(20)
          .onClick(() => {
            // Values are changed additionally before the animation is executed.
            this.w = 100;
            this.h = 100;
            this.message = 'Hello World';
            UIUtils.flushUpdates();
  
            this.getUIContext().animateTo({
              duration: 1000
            }, () => {
              this.w = 200;
              this.h = 200;
              this.message = 'Hello ArkUI';
            });
          })
          // ...
        Column() {
          Text(`${this.message}`)
        }
        .backgroundColor('#ff17a98d')
        .width(this.w)
        .height(this.h)
      }
    }
  }
  ```

  ![applySync-flushUpdates-flushUIUpdates](./figures/applySync-flushUpdates-flushUIUpdates.gif)
  
- The mentioned **applySync** and **flushUpdates** APIs both synchronously execute @Computed calculations and trigger @Monitor callbacks. This causes two @Monitor callbacks to be triggered by a single click event in the above sample code, which may be inconsistent with your expectations. For this reason, the **flushUIUpdates** API is introduced. It is only used to synchronously refresh all UI nodes modified before the function is called, and does not execute @Computed calculations or trigger @Monitor callbacks.
  
  <!-- @[FlushUIUpdatesUse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/FlushUIUpdatesUse.ets) -->
  
  ``` TypeScript
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Index {
    @Local message: string = 'Hello';
  
    @Monitor('message')
    onMessageChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
    }
  
    build() {
      Column() {
        Text(`message: ${this.message}`)
        Button('change size')
          .margin(20)
          .onClick(() => {
            // test1: Call the applySync API. The log is printed twice.
            // UIUtils.applySync(() => {
            //   this.message = 'Hello World';
            // })
  
            // test2: Call the flushUpdates API. The log is printed twice.
            // this.message = 'Hello World';
            // UIUtils.flushUpdates();
  
            // test3: Call the flushUIUpdates API. The log is printed once.
            this.message = 'Hello World';
            UIUtils.flushUIUpdates();
            this.message = 'Hello ArkUI';
          })
          // ...
      }
    }
  }
  ```

## Constraints

- If **applySync** is called nestedly within the closure function of another applySync, the inner **applySync** will be skipped and return **undefined**, and the warning message "UIUtils.applySync will be skipped when called within another UIUtils.applySync. The inner UIUtils.applySync will return undefined" will be printed.
  
  <!-- @[ApplySyncNestApplySync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/ApplySyncNestApplySync.ets) -->
  
  ``` TypeScript
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Index {
    @Local w: number = 50; // Width.
    @Local h: number = 50; // Height.
  
    build() {
      Column() {
        Button('change size')
          .margin(20)
          .onClick(() => {
            // Values are changed additionally before the animation is executed.
            UIUtils.applySync(() => {
              this.w = 100;
              // The inner applySync is skipped.
              UIUtils.applySync(() => {
                this.h = 100;
              });
            });
  
            this.getUIContext().animateTo({
              duration: 1000
            }, () => {
              this.w = 200;
              this.h = 200;
            });
          })
          // ...
        Column() {
          Text('BOX')
        }
        .backgroundColor('#ff17a98d')
        .width(this.w)
        .height(this.h)
      }
    }
  }
  ```

- Calling the **flushUpdates** or **flushUIUpdates** API in the **applySync** closure function will have no effect, and the warning message "UIUtils.flushUpdates will be skipped when called within UIUtils.applySync"/"UIUtils.flushUIUpdates will be skipped when called within UIUtils.applySync" will be printed.
  
  <!-- @[ApplySyncNestOthers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/ApplySyncNestOthers.ets) -->
  
  ``` TypeScript
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Index {
    @Local w: number = 50; // Width.
    @Local h: number = 50; // Height.
  
    build() {
      Column() {
        Button('change size')
          .margin(20)
          .onClick(() => {
            // Values are changed additionally before the animation is executed.
            UIUtils.applySync(() => {
              this.w = 100;
              UIUtils.flushUpdates(); // In applySync, flushUpdates is ignored.
              UIUtils.flushUIUpdates(); // In applySync, flushUIUpdates is ignored.
            });
            this.h = 100;
            UIUtils.flushUpdates(); // Take effect.
  
            this.getUIContext().animateTo({
              duration: 1000
            }, () => {
              this.w = 200;
              this.h = 200;
            });
          })
          // ...
        Column() {
          Text('BOX')
        }
        .backgroundColor('#ff17a98d')
        .width(this.w)
        .height(this.h)
      }
    }
  }
  ```
  
- Calling the **applySync**, **flushUpdates**, and **flushUIUpdates** APIs within the **getter** methods decorated with @Computed is not supported; otherwise, a runtime error is reported. The error message is "The function is not allowed to be called in @Computed", and the error code is [140001](../../reference/apis-arkui/errorcode-stateManagement.md#140001-invalid-invocation-of-applysync-flushupdates-or-flushuiupdates).
  
  <!-- @[CallInComputed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/CallInComputed.ets) -->
  
  ``` TypeScript
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Page {
    @Local firstName: string = 'Hua';
    @Local lastName: string = 'Li';
    @Local count: number = 0;
  
    @Computed
    get fullName() {
      // An error is reported when applySync, flushUpdates, and flushUIUpdates are called in computed.
      UIUtils.flushUIUpdates();
      UIUtils.flushUpdates();
      UIUtils.applySync(() => {
        this.count++;
      });
      return this.firstName + ' ' + this.lastName;
    }
  
    build() {
      Column() {
        Text(`${this.fullName}`)
        Text(`${this.count}`)
        Button('change fullName').onClick(() => {
          this.firstName = 'Zhang';
          this.lastName = 'San';
        })
      }
    }
  }
  ```

- Calling the flushUpdates and flushUIUpdates APIs in the @Monitor callback function is not supported. Otherwise, an error is reported. The error message is "The function is not allowed to be called in @Monitor", and the error code is [140002](../../reference/apis-arkui/errorcode-stateManagement.md#140002-invalid-invocation-of-flushupdates-or-flushuiupdates).
  
  <!-- @[CallInMonitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/CallInMonitor.ets) -->
  
  ``` TypeScript
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Page {
    @Local count: number = 0;
  
    @Monitor('count')
    onCountChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`${path} changed from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
      UIUtils.flushUpdates(); // An error is reported when flushUpdates is called in the monitor.
      UIUtils.flushUIUpdates(); // An error is reported when flushUIUpdates is called in the monitor.
    }
  
    build() {
      Column() {
        Text(`${this.count}`)
        Button('change count')
          .onClick(() => {
          this.count++;
          })
          // ...
      }
    }
  }
  ```

## Use Cases

### Animation Scenario

There is a conflict between the asynchronous dirty marking logic of state management V2 and the logic where **animateTo** immediately refreshes dirty nodes, which causes no animation to be displayed when **animateTo** is triggered in @Monitor. The expected effect can be achieved by using the **applySync** API to synchronize the changes of state variables. The following is an example:

<!-- @[AnimateToUse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/AnimateToUse.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';
  @Local x: number = 0;
  @Local y: number = 0;
  @Local w: number = 200;
  @Local h: number = 50;

  @Monitor('message')
  onMsgChange() {
    console.info('message change to', this.message);
    this.animateAction();
  }

  animateAction() {
    this.getUIContext().animateTo({
      duration: 1000
    }, () => {
      // Call the applySync API to synchronously refresh the animation tail frame. Otherwise, the animation is not displayed.
      UIUtils.applySync(() => {
        this.x = 100;
        this.y = 100;
      });
    });
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(20)
        .width(this.w)
        .height(this.h)
        .backgroundColor(Color.Pink)
        .onClick(() => {
          this.message = 'New Message';
        })
        .position({
          x: this.x,
          y: this.y
        })
        // ...
    }
    .height('100%')
    .width('100%')
  }
}
```

![applySync-animateTo](./figures/applySync-animateTo.gif)

### Routing Scenario

To set [shared transition](../../reference/apis-arkui/arkui-ts/ts-transition-animation-shared-elements.md#sharedtransition) in the routing scenario, use the **applySync** API to refresh the **name** value during transition. In the following sample code, when navigating from the index page to the **PageTransitionTwo** page, the IDs of the two pages do not match, and the page transition animation fails to play. When the index page is returned from the **PageTransitionTwo** page, the IDs of the two pages match, and the page transition displayed.

<!-- @[PageUse_PageOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/PageUse.ets) -->

``` TypeScript
// PageUse.ets

import { UIUtils, AppStorageV2 } from '@kit.ArkUI';

@ObservedV2
export class Info {
  @Trace public name: string = '';
}

@Entry
@ComponentV2
struct SharedTransitionExample {
  @Local info: Info = AppStorageV2.connect(Info, () => new Info())!;

  build() {
    Column() {
      // 'app.media.startIcon' is only an example. Replace it with the actual one.
      Image($r('app.media.startIcon'))
        .width(50)
        .height(50)
        .margin({ left: 20, top: 20 })
        .sharedTransition(this.info.name, { duration: 800, curve: Curve.Linear, delay: 100 })
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Start)
    .onClick(() => {
      UIUtils.applySync(() => {
        this.info.name = 'id1'; // Not matched.
      });
      this.getUIContext().getRouter().pushUrl({ url: 'pages/PageTransitionTwo' })
    })
    // ...
  }
}
```

<!-- @[PageUse_PageTwo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UpdateDirtySync/entry/src/main/ets/pages/PageTransitionTwo.ets) -->

``` TypeScript
// PageTransitionTwo.ets

import { UIUtils, AppStorageV2 } from '@kit.ArkUI';
import { Info } from './PageUse';

@Entry
@ComponentV2
struct PageBExample {
  build() {
    Stack() {
      // 'app.media.startIcon' is only an example. Replace it with the actual one.
      Image($r('app.media.startIcon'))
        .width(150)
        .height(150)
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 })
        .onClick(() => {
          UIUtils.applySync(() => {
            AppStorageV2.connect(Info, () => new Info())!.name = 'sharedImage'; // Matched.
          });
          this.getUIContext().getRouter().back();
        })
        // ...
    }
    .width('100%')
    .height('100%')
  }
}
```

![applySync-pagetransition](./figures/applySync-pagetransition.gif)
