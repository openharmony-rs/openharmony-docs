# Asynchronous Lock
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @dwhuawei-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e8dba876a1b7d39f7c767932ca03dc0b32b0ffb0 translatedAt=2026-11-04T09:00:41.816Z pushedAt=2026-11-04T09:21:53.967Z nl=1 -->

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