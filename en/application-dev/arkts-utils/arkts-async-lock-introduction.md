---
kits: ["ArkTS"]
description: "Introduces the ArkTS asynchronous lock (AsyncLock) capability, which is used to resolve data race issues between concurrent instances in multithreading, prevents blocking locks from causing deadlocks in asynchronous scenarios, supports cross-thread reference passing, and protects the data security of Sendable shared objects."
keywords: [asynchronous lock, AsyncLock, data race, multithreaded concurrency, non-blocking lock, cross-thread reference passing, Sendable, lockAsync, deadlock]
doctype: guide
status: active
---

# Asynchronous Lock
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @dwhuawei-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=d802165dde49a731f0fcacc5a6108aec607634d1 translatedAt=2026-11-06T10:06:54.452Z pushedAt=2026-11-09T08:31:35.542Z nl=1 -->

To address data race issues in concurrent multithreading instances, ArkTS introduces asynchronous locks. These locks can be held by class objects. To simplify access across concurrent instances, the [AsyncLock object](../reference/apis-arkts/arkts-apis-arkts-utils-locks.md#asynclock) supports pass-by-reference across threads.

Because the ArkTS language supports asynchronous operations, blocking locks are prone to deadlocks. Therefore, ArkTS supports only asynchronous locks (non-blocking locks). In addition, asynchronous locks can be used to ensure the timing consistency of asynchronous tasks within a single thread, preventing data race issues caused by the uncertain execution order of asynchronous tasks.

For more details about asynchronous lock APIs, see [ArkTSUtils.locks](../reference/apis-arkts/arkts-apis-arkts-utils-locks.md).

> **NOTE**
>
> Methods using asynchronous locks must be marked as **async**, and the caller must use the **await** keyword to ensure correct timing.

## Usage Example

To prevent data races when modifying shared variables across threads with [@Sendable objects](arkts-sendable.md), asynchronous locks can be used for data protection. The sample code is as follows:
<!-- @[example_protect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableObjectRelated/entry/src/main/ets/managers/ArktsAsyncLockIntroduction.ets) -->  

``` TypeScript
import { ArkTSUtils, taskpool } from '@kit.ArkTS';

@Sendable
export class A {
  private count_: number = 0;
  public lock_: ArkTSUtils.locks.AsyncLock = new ArkTSUtils.locks.AsyncLock();

  public async getCount(): Promise<number> {
    // Add an asynchronous lock to protect the data.
    return this.lock_.lockAsync(() => {
      return this.count_;
    })
  }

  public async increaseCount() {
    // Add an asynchronous lock to protect the data.
    await this.lock_.lockAsync(() => {
      this.count_++;
    })
  }
}

@Concurrent
async function printCount(a: A) {
  await a.increaseCount();
  console.info(`InputModule: count is: ${await a.getCount()}`);
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(async () => {
          // Create the Sendable object a.
          let a: A = new A();
          // Pass object a to a child thread.
          await taskpool.execute(printCount, a);
          this.message = 'success';
        })
    }
    .height('100%')
    .width('100%')
  }
}
```