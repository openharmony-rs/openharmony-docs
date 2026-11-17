---
kits: ["ArkTS / Ark Programming Language"]
description: "Introduces the use of Sendable objects in ArkUI data update scenarios: because state decorators and Sendable decorators cannot modify the same object simultaneously, use makeObserved to convert Sendable data obtained from a child thread into an observable object to trigger UI updates, and explain the limitation that observable data cannot be passed back to a child thread."
keywords: [makeObserved, Sendable observable object, ArkUI data update, UI state management, child thread data synchronization, data observation]
doctype: guide
status: active
---

# ArkUI Data Updates
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @huanghello-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:38:05.179Z pushedAt=2026-11-12T08:32:59.236Z nl=1 -->

When data obtained from network downloads or generated locally needs to be sent to the UI thread for display, because ArkUI's annotation and the [@Sendable](../arkts-utils/arkts-sendable.md#sendable-decorator) decorator cannot modify variables and objects at the same time, you need to use [makeObserved](../ui/state-management/arkts-new-makeObserved.md) to import observable Sendable shared data in ArkUI.

This example describes the following scenarios:
- After being processed by the makeObserved method, data of the @Sendable type gains observability, and its changes can trigger UI updates.
- Obtain data from a child thread, convert it into observable data by executing makeObserved, and then replace it as a whole on the UI thread to observe data changes.
- When passing data from the UI main thread back to a child thread, pass only non-observable data. The return value of makeObserved cannot be passed directly to a child thread.

<!-- @[define_sendable_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/SendableData.ets) -->

``` TypeScript
@Sendable
export class SendableData {
  public name: string = 'Tom';
  public age: number = 20;
  public gender: number = 1;
  public likes: number = 1;
  public follow: boolean = false;
}
```

<!-- @[update_arkui_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/MakeobservedSendable.ets) -->

``` TypeScript
import { taskpool } from '@kit.ArkTS';
import { SendableData } from './SendableData';
import { UIUtils } from '@kit.ArkUI';

@Concurrent
function threadGetData(param: string): SendableData {
  // Process data in the child thread.
  let ret = new SendableData();
  console.info(`Concurrent threadGetData, param ${param}`);
  ret.name = param + '-o';
  ret.age = Math.floor(Math.random() * 40);
  ret.likes = Math.floor(Math.random() * 100);
  return ret;
}

@Entry
@ComponentV2
struct Index {
  // Add observability to a common object or a Sendable object through makeObserved.
  @Local send: SendableData = UIUtils.makeObserved(new SendableData());

  build() {
    Column() {
      Text(this.send.name)
      Button('change name').onClick(() => {
        // Observe property changes.
        this.send.name += '0';
      })
        .id('change name')
      Button('task').onClick(() => {
        // Put the function to be executed into the taskpool internal task queue and wait for it to be dispatched to a worker thread for execution.
        // Data construction and processing can be completed in the child thread, but observable data cannot be passed to the child thread. Observable data can only be operated on the UI main thread.
        // Therefore, only the property `name` of `this.send` is passed to the child thread for operation here.
        taskpool.execute(threadGetData, this.send.name).then(val => {
          // Used together with @Local to observe changes to this.send.
          this.send = UIUtils.makeObserved(val as SendableData);
        })
      })
        .id('task')
    }
  }
}
```