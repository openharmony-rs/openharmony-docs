# @ohos.worker (Starting the Worker) (System API)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=6765e63d2877178f84dcdcc92016726d39eb79a0 translatedAt=2026-11-06T09:54:03.129Z pushedAt=2026-11-13T07:19:47.236Z nl=1 -->

A Worker is an independent thread running in parallel with the host thread. The thread that creates a Worker is called the host thread, and the thread of the Worker itself is called the Worker thread. The URL file passed in when creating a Worker is executed in the Worker thread, which can handle time-consuming operations but cannot directly operate the UI.

The main purpose of a Worker is to provide a multi-threaded runtime environment for applications, so that the application is separated from the host thread during execution and runs scripts in a background thread to handle time-consuming operations, avoiding compute-intensive or high-latency tasks from blocking the host thread. Since a Worker is not actively destroyed once created, it keeps running when not in a task state, causing resource waste. Therefore, idle Workers should be destroyed in a timely manner.

The Context object of the Worker thread is different from that of the UI main thread. The Worker thread does not support UI operations.

See [Worker Notes](../../arkts-utils/worker-introduction.md) to learn about the relevant notes during Worker usage.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.worker (Starting the Worker)](js-apis-worker.md).

## Modules to Import

```ts
import { worker } from '@kit.ArkTS';
```

## RestrictedWorker<sup>11+</sup>

The RestrictedWorker class inherits [ThreadWorker<sup>9+</sup>](js-apis-worker.md#threadworker9) and supports all APIs in ThreadWorker.

RestrictedWorker is mainly used to provide a restricted Worker thread runtime environment, in which only the Worker module is allowed to be imported and no other APIs are allowed.

### constructor<sup>11+</sup>

constructor(scriptURL: string, options?: WorkerOptions)

RestrictedWorker constructor. Before using other methods, you must first construct a RestrictedWorker instance.

**System API**: This is a system API.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                           | Mandatory| Description                                                        |
| --------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| scriptURL | string                          | Yes  | URL of the Worker thread file. For details about the rules, see [Precautions for File URLs](../../arkts-utils/worker-introduction.md#precautions-for-file-urls).|
| options   | [WorkerOptions](js-apis-worker.md#workeroptions) | No   | Options for constructing a RestrictedWorker. The default value of type is 'classic', name defaults to 'undefined', shared defaults to 'undefined', and priority defaults to 'MEDIUM'. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200003 | Worker initialization failure. |
| 10200007 | The worker file path is invalid. |

**Example**

This uses the [Stage model](../../application-models/stage-model-development-overview.md) as an example of an Ability loading a Worker file. For the scenario of using Library to load a Worker thread file, see [File Path Notes](../../arkts-utils/worker-introduction.md#precautions-for-file-urls).

The following is sample code for creating a RestrictedWorker in the host thread:

```ts
import { worker } from '@kit.ArkTS';

// Two scenarios are involved.

// Scenario 1: URL of the Worker thread file: "entry/src/main/ets/workers/worker.ets"
const workerStageModel01 = new worker.RestrictedWorker('entry/ets/workers/worker.ets', {name: 'first worker in Stage model'});

// Scenario 2: URL of the Worker thread file: "testworkers/src/main/ets/ThreadFile/workers/worker.ets"
const workerStageModel02 = new worker.RestrictedWorker('testworkers/ets/ThreadFile/workers/worker.ets');
```

The restricted Worker thread file only allows importing the Worker module and does not allow importing any other APIs. The following is sample code for a restricted Worker thread file:

```ts
// Restricted Worker thread file
import { worker, MessageEvents } from '@kit.ArkTS';

//import { process } from '@kit.ArkTS'; // Only worker APIs can be imported to the restricted Worker thread file.

const workerPort = worker.workerPort;

workerPort.onmessage = (e: MessageEvents): void => {
  console.info('worker:: This is worker thread.');
  //console.info('worker:: worker tid: ' + process.tid) // Execute process.tid. The host thread will report a corresponding TypeError.
}
```