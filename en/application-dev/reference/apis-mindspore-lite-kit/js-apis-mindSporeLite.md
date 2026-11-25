# @ohos.ai.mindSporeLite (On-device AI Framework)

<!--Kit: MindSpore Lite Kit-->
<!--Subsystem: AI-->
<!--Owner: @zhuguodong8-->
<!--Designer: @zhuguodong8; @jjfeing-->
<!--Tester: @principal87-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=dca31322189f91fc40f262b55618120da7c83182 translatedAt=2026-11-13T04:12:24.249Z pushedAt=2026-11-13T11:02:28.479Z nl=1 -->

MindSpore Lite is a lightweight, high-performance on-device AI engine. It provides standard model inference and training APIs, and is built with high-performance operator libraries for general-purpose hardware. It supports the Neural Network Runtime Kit to enable AI-dedicated chips for accelerated inference, helping build all-scenario intelligent applications.

This module mainly describes the capabilities of the MindSpore Lite AI engine for on-device model inference and training.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version. The models used in the sample code are all MindSpore on-device models.
> 
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { mindSporeLite } from '@kit.MindSporeLiteKit';
```

## mindSporeLite.loadModelFromFile

loadModelFromFile(model: string, callback: Callback&lt;Model&gt;): void

Loads an input model from a complete path for CPU inference. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type                      | Mandatory | Description                                             |
| -------- | ------------------------- | ---- | ------------------------------------------------ |
| model    | string                    | Yes   | Complete input path of the model. The string length limit follows the file system. |
| callback | Callback<[Model](#model)> | Yes   | Callback invoked to return the model object. Loading fails when the model input is detected to be empty.                         |

**Example** 

```ts
let modelFile: string = '/path/to/xxx.ms';
mindSporeLite.loadModelFromFile(modelFile, (mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  if (modelInputs == null) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Result: null`);
  } else if (modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Input count: 0`);
  } else {
    console.info(`Succeeded in getting model inputs. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
  }
})
```
## mindSporeLite.loadModelFromFile

loadModelFromFile(model: string, context: Context, callback: Callback&lt;Model&gt;): void

Loads the input model from the full path for inference. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type                                | Mandatory | Description                   |
| -------- | ----------------------------------- | ---- | ---------------------- |
| model    | string                              | Yes   | Complete input path of the model. The string length limit follows the file system. |
| context | [Context](#context) | Yes | Configuration of the runtime environment. |
| callback | Callback<[Model](#model)> | Yes   | Callback used to return the model object. If the model input is empty during the callback, the callback fails. |

**Example** 

```ts
let context: mindSporeLite.Context = {};
context.target = ['cpu'];
let modelFile: string = '/path/to/xxx.ms';
mindSporeLite.loadModelFromFile(modelFile, context, (mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  if (modelInputs == null) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Context: ${JSON.stringify(context)}, Result: null`);
  } else if (modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Context: ${JSON.stringify(context)}, Input count: 0`);
  } else {
    console.info(`Succeeded in getting model inputs. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
  }
})
```
## mindSporeLite.loadModelFromFile

loadModelFromFile(model: string, context?: Context): Promise&lt;Model&gt;

Loads an input model from a complete path for inference. This API uses a promise to return the result asynchronously.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name    | Type                | Mandatory | Description                                             |
| ------- | ------------------- | ---- | ------------------------------------------------ |
| model   | string              | Yes   | Complete input path of the model. The string length limit follows the file system. |
| context | [Context](#context) | No   | Configuration of the runtime environment. By default, CpuDevice is used for initialization.    |

**Return value**

| Type                      | Description                         |
| ------------------------- | ---------------------------- |
| Promise<[Model](#model)> | Promise object. Returns the Model object. |

**Example** 

```ts
let modelFile = '/path/to/xxx.ms';
mindSporeLite.loadModelFromFile(modelFile).then((mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  if (modelInputs == null) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Result: null`);
  } else if (modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Input count: 0`);
  } else {
    console.info(`Succeeded in getting model inputs. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
  }
}).catch((error: Error) => {
  console.error(`Failed to load model from file. Model file: ${modelFile}, Error: ${error.message}`);
});
```
## mindSporeLite.loadModelFromBuffer

loadModelFromBuffer(model: ArrayBuffer, callback: Callback&lt;Model&gt;): void

Loads an input model from memory for CPU inference. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type                      | Mandatory | Description                     |
| -------- | ------------------------- | ---- | ------------------------ |
| model    | ArrayBuffer               | Yes   | Memory that contains the model.         |
| callback | Callback<[Model](#model)> | Yes   | Callback used to return the model object. If the model input is empty during the callback, the callback fails. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let modelFile = 'xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(modelFile)
  .then((buffer: Uint8Array) => {
    let modelBuffer = buffer.buffer;
    mindSporeLite.loadModelFromBuffer(modelBuffer, (mindSporeLiteModel: mindSporeLite.Model) => {
      let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
      if (modelInputs == null || modelInputs.length === 0) {
        console.error(`Failed to get model inputs from buffer. Model file: ${modelFile}, Buffer size: ${modelBuffer.byteLength}`);
      } else {
        console.info(`Succeeded in getting model inputs from buffer. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
      }
    })
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read model file from resources. File name: ${modelFile}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```
## mindSporeLite.loadModelFromBuffer

loadModelFromBuffer(model: ArrayBuffer, context: Context, callback: Callback&lt;Model&gt;): void

Loads an input model from memory for inference. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type                                | Mandatory | Description                   |
| -------- | ----------------------------------- | ---- | ---------------------- |
| model    | ArrayBuffer                   | Yes   | Memory that contains the model. |
| context | [Context](#context) | Yes  | Configuration of the runtime environment. |
| callback | Callback<[Model](#model)> | Yes   | Callback used to return the model object. If the model input is empty during the callback, the callback fails. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let modelFile = 'xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
let context: mindSporeLite.Context = {};
context.target = ['cpu'];

globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(modelFile)
  .then((buffer: Uint8Array) => {
    let modelBuffer = buffer.buffer;
    mindSporeLite.loadModelFromBuffer(modelBuffer, context, (mindSporeLiteModel: mindSporeLite.Model) => {
      let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
      if (modelInputs == null || modelInputs.length === 0) {
        console.error(`Failed to get model inputs from buffer. Model file: ${modelFile}, Context: ${JSON.stringify(context)}, Buffer size: ${modelBuffer.byteLength}`);
      } else {
        console.info(`Succeeded in getting model inputs from buffer. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
      }
    })
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read model file from resources. File name: ${modelFile}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```
## mindSporeLite.loadModelFromBuffer

loadModelFromBuffer(model: ArrayBuffer, context?: Context): Promise&lt;Model&gt;

Loads an input model from memory for inference. This API uses a promise to return the result asynchronously.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name    | Type                | Mandatory | Description                                          |
| ------- | ------------------- | ---- | --------------------------------------------- |
| model   | ArrayBuffer         | Yes   | Memory that contains the model.                              |
| context | [Context](#context) | No   | Configuration of the runtime environment. By default, CpuDevice is used for initialization. |

**Return value**

| Type                            | Description                         |
| ------------------------------- | ---------------------------- |
| Promise<[Model](#model)> | Promise object. Returns the Model object. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let modelFile = 'xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(modelFile)
  .then((buffer: Uint8Array) => {
    let modelBuffer = buffer.buffer;
    mindSporeLite.loadModelFromBuffer(modelBuffer).then((mindSporeLiteModel: mindSporeLite.Model) => {
      let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
      if (modelInputs == null || modelInputs.length === 0) {
        console.error(`Failed to get model inputs from buffer. Model file: ${modelFile}, Buffer size: ${modelBuffer.byteLength}`);
      } else {
        console.info(`Succeeded in getting model inputs from buffer. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
      }
    }).catch((error: Error) => {
      console.error(`Failed to load model from buffer. Model file: ${modelFile}, Buffer size: ${modelBuffer.byteLength}, Error: ${error.message}`);
    });
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read model file from resources. File name: ${modelFile}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```
## mindSporeLite.loadModelFromFd

loadModelFromFd(model: number, callback: Callback&lt;Model&gt;): void

Loads the input model from a file descriptor for CPU inference. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type                                | Mandatory | Description                   |
| -------- | ----------------------------------- | ---- | ---------------------- |
| model    | number                         | Yes   | File descriptor of the model. Pass the fd value returned by the file system. |
| callback | Callback<[Model](#model)> | Yes   | Callback used to return the model object. If the model input is empty during the callback, the callback fails. |

**Example** 

```ts
import { fileIo } from '@kit.CoreFileKit';

let modelFile = '/path/to/xxx.ms';
let file = fileIo.openSync(modelFile, fileIo.OpenMode.READ_ONLY);
mindSporeLite.loadModelFromFd(file.fd, (mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  if (modelInputs == null) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, File descriptor: ${file.fd}, Result: null`);
  } else if (modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, File descriptor: ${file.fd}, Input count: 0`);
  } else {
    console.info(`Succeeded in getting model inputs. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
  }
})
```
## mindSporeLite.loadModelFromFd

loadModelFromFd(model: number, context: Context, callback: Callback&lt;Model&gt;): void

Loads an input model from a file descriptor for inference. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type                                | Mandatory | Description                   |
| -------- | ----------------------------------- | ---- | ---------------------- |
| model    | number                   | Yes   | File descriptor of the model. Pass the fd value returned by the file system. |
| context | [Context](#context) | Yes  | Configuration of the runtime environment. |
| callback | Callback<[Model](#model)> | Yes   | Callback used to return the model object. If the model input is empty during the callback, the callback fails. |

**Example** 

```ts
import { fileIo } from '@kit.CoreFileKit';

let modelFile = '/path/to/xxx.ms';
let context: mindSporeLite.Context = {};
context.target = ['cpu'];
let file = fileIo.openSync(modelFile, fileIo.OpenMode.READ_ONLY);
mindSporeLite.loadModelFromFd(file.fd, context, (mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  if (modelInputs == null) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, File descriptor: ${file.fd}, Context: ${JSON.stringify(context)}, Result: null`);
  } else if (modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, File descriptor: ${file.fd}, Context: ${JSON.stringify(context)}, Input count: 0`);
  } else {
    console.info(`Succeeded in getting model inputs. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
  }
})
```
## mindSporeLite.loadModelFromFd

loadModelFromFd(model: number, context?: Context): Promise&lt;Model&gt;

Loads the input model from a file descriptor for inference. This API uses a promise to return the result.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name    | Type                | Mandatory | Description                                          |
| ------- | ------------------- | ---- | --------------------------------------------- |
| model   | number              | Yes   | File descriptor of the model. Pass the fd value returned by the file system.  |
| context | [Context](#context) | No   | Configuration of the runtime environment. By default, CpuDevice is used for initialization. |

**Return value**

| Type                      | Description                         |
| ------------------------- | ---------------------------- |
| Promise<[Model](#model)> | Promise object. Returns the Model object. |

**Example** 

```ts
import { fileIo } from '@kit.CoreFileKit';

let modelFile = '/path/to/xxx.ms';
let file = fileIo.openSync(modelFile, fileIo.OpenMode.READ_ONLY);
mindSporeLite.loadModelFromFd(file.fd).then((mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  if (modelInputs == null) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, File descriptor: ${file.fd}, Result: null`);
  } else if (modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, File descriptor: ${file.fd}, Input count: 0`);
  } else {
    console.info(`Succeeded in getting model inputs. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
  }
}).catch((error: Error) => {
  console.error(`Failed to load model from file descriptor. Model file: ${modelFile}, File descriptor: ${file.fd}, Error: ${error.message}`);
});
```

## mindSporeLite.loadTrainModelFromFile<sup>12+</sup>

loadTrainModelFromFile(model: string, trainCfg?: TrainCfg, context?: Context): Promise&lt;Model&gt;

Loads a training model file from a path. This API uses a promise to return the result asynchronously.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type                    | Mandatory | Description                                             |
| -------- | ----------------------- | ---- | ------------------------------------------------ |
| model    | string                  | Yes   | Complete input path of the model. The string length limit follows the file system. |
| trainCfg | [TrainCfg](#traincfg12) | No   | Training configuration of the model. The default value is the default value of each TrainCfg attribute.     |
| context  | [Context](#context)     | No   | Configuration of the runtime environment. By default, CpuDevice is used for initialization.    |

**Return value**

| Type                       | Description                   |
| ------------------------ | -------------------- |
| Promise<[Model](#model)> | Promise object. Returns the Model object. |

**Example** 

```ts
let modelFile = '/path/to/xxx.ms';
mindSporeLite.loadTrainModelFromFile(modelFile).then((mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  if (modelInputs == null) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Result: null`);
  } else if (modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Input count: 0`);
  } else {
    console.info(`Succeeded in getting model inputs. Model file: ${modelFile}, Input name: ${modelInputs[0].name}`);
  }
}).catch((error: Error) => {
  console.error(`Failed to load train model from file. Model file: ${modelFile}, Error: ${error.message}`);
});
```

## mindSporeLite.loadTrainModelFromBuffer<sup>12+</sup>

loadTrainModelFromBuffer(model: ArrayBuffer, trainCfg?: TrainCfg, context?: Context): Promise&lt;Model&gt;

Loads a training model from a memory buffer. This API uses a promise to return the result asynchronously.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type                    | Mandatory | Description                                          |
| -------- | ----------------------- | ---- | --------------------------------------------- |
| model    | ArrayBuffer             | Yes   | Memory that contains the training model.                          |
| trainCfg | [TrainCfg](#traincfg12) | No   | Training configuration of the model. The default value is the default value of each TrainCfg attribute.  |
| context  | [Context](#context)     | No   | Configuration of the runtime environment. By default, CpuDevice is used for initialization. |

**Return value**

| Type                       | Description                   |
| ------------------------ | -------------------- |
| Promise<[Model](#model)> | Promise object. Returns the Model object. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let modelFile = 'xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(modelFile)
  .then((buffer: Uint8Array) => {
    let modelBuffer = buffer.buffer;
    mindSporeLite.loadTrainModelFromBuffer(modelBuffer).then((mindSporeLiteModel: mindSporeLite.Model) => {
      console.info(`Succeeded in loading train model. Train mode: ${mindSporeLiteModel.trainMode}`);
    }).catch((error: Error) => {
      console.error(`Failed to load train model from buffer. Model file: ${modelFile}, Buffer size: ${modelBuffer.byteLength}, Error: ${error.message}`);
    });
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read model file from resources. File name: ${modelFile}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```

## mindSporeLite.loadTrainModelFromFd<sup>12+</sup>

loadTrainModelFromFd(model: number, trainCfg?: TrainCfg, context?: Context): Promise&lt;Model&gt;

Loads a training model file from a file descriptor. This API uses a promise to return the result.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type                    | Mandatory | Description                                             |
| -------- | ----------------------- | ---- | ------------------------------------------------ |
| model    | number                  | Yes   | File descriptor of the training model. Pass the fd value returned by the file system. |
| trainCfg | [TrainCfg](#traincfg12) | No   | Training configuration of the model. The default value is the default value of each TrainCfg attribute.     |
| context  | [Context](#context)     | No   | Configuration of the runtime environment. By default, CpuDevice is used for initialization.    |

**Return value**

| Type                     | Description                         |
| ------------------------ | ---------------------------- |
| Promise<[Model](#model)> | Promise object. Returns the Model object. |

**Example** 

```ts
import { fileIo } from '@kit.CoreFileKit';

let modelFile = '/path/to/xxx.ms';
let file = fileIo.openSync(modelFile, fileIo.OpenMode.READ_ONLY);
mindSporeLite.loadTrainModelFromFd(file.fd).then((mindSporeLiteModel: mindSporeLite.Model) => {
  console.info(`Succeeded in loading train model. Train mode: ${mindSporeLiteModel.trainMode}`);
}).catch((error: Error) => {
  console.error(`Failed to load train model from file descriptor. Model file: ${modelFile}, File descriptor: ${file.fd}, Error: ${error.message}`);
});
```

## mindSporeLite.getAllNNRTDeviceDescriptions<sup>12+</sup>

getAllNNRTDeviceDescriptions() : NNRTDeviceDescription[]

Obtains all device descriptions in NNRt (Neural Network Runtime).

**System capability:** SystemCapability.AI.MindSporeLite

**Return value**

| Type                                                | Description                   |
| --------------------------------------------------- | ---------------------- |
| [NNRTDeviceDescription](#nnrtdevicedescription12)[] | Array of NNRt device descriptions. |

**Example** 

```ts
try {
  let allDevices = mindSporeLite.getAllNNRTDeviceDescriptions();
  if (allDevices == null || allDevices.length === 0) {
    console.error('Failed to get NNRT device descriptions. Result: null or empty array');
  } else {
    console.info(`Succeeded in getting NNRT device descriptions. Device count: ${allDevices.length}`);
  }
} catch (error) {
  console.error(`Failed to get NNRT device descriptions. Error: ${error}`);
}
```

## Context

Defines the configuration information of the runtime environment.

**System capability:** SystemCapability.AI.MindSporeLite


| Name   | Type                      | Read-Only | Optional | Description                                                         |
| ------ | ------------------------- | ---- | ---- | ------------------------------------------------------------ |
| target | string[]                  | No   | Yes   | Configures the target backend. The value can be 'cpu' or 'nnrt'. The default value is 'cpu'.                 |
| cpu    | [CpuDevice](#cpudevice)   | No   | Yes   | CPU backend device options. This attribute can be set only when target contains 'cpu'. The default value is the default value of each attribute of CpuDevice. |
| nnrt   | [NNRTDevice](#nnrtdevice) | No   | Yes   | NNRt backend device options. This attribute can be set only when target contains 'nnrt'. The default value is the default value of each attribute of NNRTDevice. |

**Example** 

```ts
let context: mindSporeLite.Context = {};
context.target = ['cpu','nnrt'];
```

## CpuDevice

CPU backend device options.

**System capability:** SystemCapability.AI.MindSporeLite

| Name                   | Type                                      | Read-Only | Optional | Description                                                         |
| ---------------------- | ----------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| threadNum              | number                                    | No   | Yes   | Sets the number of threads at runtime. Default value: **2**.                              |
| threadAffinityMode     | [ThreadAffinityMode](#threadaffinitymode) | No   | Yes   | Sets the CPU core binding policy mode at runtime. The default value is no core binding: **mindSporeLite.ThreadAffinityMode.NO_AFFINITIES**. |
| threadAffinityCoreList | number[]                                  | No   | Yes   | Sets the CPU core binding list at runtime. It takes effect after the core binding policy mode is set. When the core binding policy mode is **mindSporeLite.ThreadAffinityMode.NO_AFFINITIES**, the core binding list is empty. The numbers in the list represent the core sequence numbers. Default value: **[]**. |
| precisionMode          | string                                    | No   | Yes   | Sets whether to enable the **Float16 inference mode**. The value **'preferred_fp16'** enables half-precision inference, and any other value disables half-precision inference. The default value **'enforce_fp32'** indicates that half-precision inference is disabled. |

**Float16 inference mode**: Indicates that half-precision (Float16) is used for inference computation. Compared with full precision (Float32), it reduces memory usage and improves inference speed.

**Example** 

```ts
let context: mindSporeLite.Context = {};
context.cpu = {};
context.target = ['cpu'];
context.cpu.threadNum = 2;
context.cpu.threadAffinityMode = 0;
context.cpu.precisionMode = 'preferred_fp16';
context.cpu.threadAffinityCoreList = [0, 1, 2];
```

## ThreadAffinityMode

Sets the CPU core binding policy mode at runtime. The valid values are 0 to 2, where 0 indicates no core binding by default, 1 indicates binding to big cores, and 2 indicates binding to little cores.

**System capability:** SystemCapability.AI.MindSporeLite

| Name               | Value   | Description         |
| ------------------ | ---- | ------------ |
| NO_AFFINITIES      | 0    | No core binding.     |
| BIG_CORES_FIRST    | 1    | Big cores first. |
| LITTLE_CORES_FIRST | 2    | Little cores first. |

## NNRTDevice

Neural Network Runtime (NNRt) is a neural network runtime. As an intermediate bridge, it connects the upper-layer AI inference framework and the underlying acceleration chips to implement cross-chip inference computing of AI models. MindSpore Lite can be configured with the NNRt backend.

**System capability:** SystemCapability.AI.MindSporeLite

| Name                          | Type                                | Read-Only | Optional | Description                     |
| ----------------------------- | ----------------------------------- | ---- | ------------------------ | ------------------------ |
| deviceID<sup>12+</sup>        | bigint                              | No | Yes  | NNRt device ID. The default value is 0.     |
| performanceMode<sup>12+</sup> | [PerformanceMode](#performancemode12) | No  | Yes  | Working performance mode of the NNRt device. The default value is PERFORMANCE_NONE. |
| priority<sup>12+</sup>        | [Priority](#priority12)               | No  | Yes  | Priority of the NNRt inference task. The default value is PRIORITY_MEDIUM. |
| extensions<sup>12+</sup>      | [Extension](#extension12)[]         | No  | Yes  | Extended configuration of the NNRt device. The default value is empty. |

## PerformanceMode<sup>12+</sup>

Enumerates the performance modes of an NNRt (Neural Network Runtime) device.

**System capability:** SystemCapability.AI.MindSporeLite

| Name                | Value   | Description                |
| ------------------- | ---- | ------------------- |
| PERFORMANCE_NONE    | 0    | No special settings.        |
| PERFORMANCE_LOW     | 1    | Low power consumption mode.        |
| PERFORMANCE_MEDIUM  | 2    | Balanced power consumption and performance mode. |
| PERFORMANCE_HIGH    | 3    | High performance mode.        |
| PERFORMANCE_EXTREME | 4    | Extreme performance mode.      |

## Priority<sup>12+</sup>

Enumerates the priorities of NNRt inference tasks.

**System capability:** SystemCapability.AI.MindSporeLite

| Name            | Value   | Description           |
| --------------- | ---- | -------------- |
| PRIORITY_NONE   | 0    | No priority preference. |
| PRIORITY_LOW    | 1    | Low-priority task. |
| PRIORITY_MEDIUM | 2    | Medium-priority task. |
| PRIORITY_HIGH   | 3    | High-priority task. |

## Extension<sup>12+</sup>

Defines the extension information of an NNRt device.

**System capability:** SystemCapability.AI.MindSporeLite

| Name                | Type        | Read-Only | Optional | Description             |
| ------------------- | ----------- | ---- | ---- | ---------------- |
| name  | string      | No   | No   | Extension name.       |
| value | ArrayBuffer | No   | No   | Memory that contains the extension. |

## NNRTDeviceDescription<sup>12+</sup>

Describes the NNRt (Neural Network Runtime) device information, including the device ID, device name, and other information.

**System capability:** SystemCapability.AI.MindSporeLite

### deviceID<sup>12+</sup>

deviceID() : bigint

Obtains the NNRt device ID.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value**

| Type   | Description         |
| ------ | ------------ |
| bigint | NNRt device ID. |

**Example** 

```ts
let context: mindSporeLite.Context = {};
context.target = ["nnrt"];
context.nnrt = {};
let allDevices = mindSporeLite.getAllNNRTDeviceDescriptions();
if (allDevices == null || allDevices.length === 0) {
  console.error(`Failed to get NNRT device descriptions. Context: ${JSON.stringify(context)}, Result: null or empty`);
} else {
  console.info(`Succeeded in getting NNRT device descriptions. Device count: ${allDevices.length}`);
    for (let i: number = 0; i < allDevices.length; i++) {
      console.info(`Device ${i} ID: ${allDevices[i].deviceID().toString()}`);
    }
}
```

### deviceType<sup>12+</sup>

deviceType() : NNRTDeviceType

Obtains the NNRt device type.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value**

| Type                                | Description           |
| ----------------------------------- | -------------- |
| [NNRTDeviceType](#nnrtdevicetype12) | NNRt device type. |

**Example** 

```ts
let context: mindSporeLite.Context = {};
context.target = ["nnrt"];
context.nnrt = {};
let allDevices = mindSporeLite.getAllNNRTDeviceDescriptions();
if (allDevices == null || allDevices.length === 0) {
  console.error(`Failed to get NNRT device descriptions. Context: ${JSON.stringify(context)}, Result: null or empty`);
} else {
  console.info(`Succeeded in getting NNRT device descriptions. Device count: ${allDevices.length}`);
  for (let i: number = 0; i < allDevices.length; i++) {
    console.info(`Device ${i} type: ${allDevices[i].deviceType().toString()}`);
  }
}
```

### deviceName<sup>12+</sup>

deviceName() : string

Obtains the NNRt device name.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value**

| Type   | Description           |
| ------ | -------------- |
| string | NNRt device name. |

**Example** 

```ts
let context: mindSporeLite.Context = {};
context.target = ["nnrt"];
context.nnrt = {};
let allDevices = mindSporeLite.getAllNNRTDeviceDescriptions();
if (allDevices == null || allDevices.length === 0) {
  console.error(`Failed to get NNRT device descriptions. Context: ${JSON.stringify(context)}, Result: null or empty`);
} else {
  console.info(`Succeeded in getting NNRT device descriptions. Device count: ${allDevices.length}`);
  for (let i: number = 0; i < allDevices.length; i++) {
    console.info(`Device ${i} name: ${allDevices[i].deviceName()}`);
  }
}
```

## NNRTDeviceType<sup>12+</sup>

Enumerates the device types of NNRt (Neural Network Runtime).

**System capability:** SystemCapability.AI.MindSporeLite

| Name                   | Value   | Description                                |
| ---------------------- | ---- | ----------------------------------- |
| NNRTDEVICE_OTHERS      | 0    | The device type does not belong to any of the following three types. |
| NNRTDEVICE_CPU         | 1    | CPU device.                           |
| NNRTDEVICE_GPU         | 2    | GPU device.                           |
| NNRTDEVICE_ACCELERATOR | 3    | A specific accelerator device.                    |

## TrainCfg<sup>12+</sup>

Configuration file for on-device training related parameters.

**System capability:** SystemCapability.AI.MindSporeLite

| Name                            | Type                                      | Read-Only | Optional | Description                                                         |
| ------------------------------- | ----------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| lossName         | string[]                                  | No   | Yes   |  List of loss function names, used to identify the loss function nodes in the model during on-device training. The default value is ["loss_fct", "_loss_fn", "SigmoidCrossEntropy"]. |
| optimizationLevel | [OptimizationLevel](#optimizationlevel12) | No   | Yes   | Network optimization level for on-device training. The default value is O0.                         |

**Example** 

```ts
let cfg: mindSporeLite.TrainCfg = {};
cfg.lossName = ["loss_fct", "_loss_fn", "SigmoidCrossEntropy"];
cfg.optimizationLevel = mindSporeLite.OptimizationLevel.O0;
```

## OptimizationLevel<sup>12+</sup>

Enumerates the network optimization levels for on-device training.

**System capability:** SystemCapability.AI.MindSporeLite

| Name | Value   | Description                                                       |
| ---- | ---- | ---------------------------------------------------------- |
| O0   | 0    | No optimization.                                               |
| O2   | 2    | Converts the network to Float16 while keeping the batch normalization layers and the loss function as Float32. |
| O3   | 3    | Converts the network to Float16, including the batch normalization layers.                    |
| AUTO | 4    | Selects the optimization level based on the device.                                     |


## QuantizationType<sup>12+</sup>

Quantization type information. Valid values range from 0 to 2.

**System capability:** SystemCapability.AI.MindSporeLite

| Name         | Value   | Description       |
| ------------ | ---- | ---------- |
| NO_QUANT     | 0    | No quantization. |
| WEIGHT_QUANT | 1    | Weight quantization. |
| FULL_QUANT   | 2    | Full quantization.   |

## Model

Model instance. Describes the properties and methods of the Model object.

In the following API examples, you must first obtain a Model instance by using any of the following methods: [loadModelFromFile()](#mindsporeliteloadmodelfromfile), [loadModelFromBuffer()](#mindsporeliteloadmodelfrombuffer), or [loadModelFromFd()](#mindsporeliteloadmodelfromfd). Then call the corresponding method through this instance.

### Attributes

**System capability:** SystemCapability.AI.MindSporeLite

| Name                       | Type    | Read-Only | Optional | Description                                                         |
| -------------------------- | ------- | ---- | ---- | ------------------------------------------------------------ |
| learningRate<sup>12+</sup> | number  | No   | Yes   | Learning rate of the training model. The default value is read from the loaded model.                 |
| trainMode<sup>12+</sup>    | boolean | No   | Yes   | Whether the model is in training mode. The value true indicates training mode, and false indicates non-training mode. For a training model, the default value of trainMode is true; for an inference model, the default value is false. |

### getInputs

getInputs(): MSTensor[]

Obtains the model inputs for inference.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value**

| Type                    | Description               |
| ----------------------- | ------------------ |
| [MSTensor](#mstensor)[] | List of MSTensor objects. |

**Example** 

```ts
let modelFile = '/path/to/xxx.ms';
mindSporeLite.loadModelFromFile(modelFile).then((mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  if (modelInputs == null) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Result: null`);
  } else if (modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Input count: 0`);
  } else {
    console.info(`Succeeded in getting model inputs. Model file: ${modelFile}, Input name: ${modelInputs[0].name}, Total inputs: ${modelInputs.length}`);
  }
}).catch((error: Error) => {
  console.error(`Failed to load model. Model file: ${modelFile}, Error: ${error.message}`);
});
```
### predict

predict(inputs: MSTensor[], callback: Callback&lt;MSTensor[]&gt;): void

Performs model inference. This API uses an asynchronous callback to return the result. Ensure that the model object is not reclaimed by resources when this API is called.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name | Type                    | Mandatory | Description                       |
| ------ | ----------------------- | ---- | -------------------------- |
| inputs | [MSTensor](#mstensor)[] | Yes   | Input list of the model. An MSTensor object. |
| callback | Callback<[MSTensor](#mstensor)[]> | Yes   | Callback invoked to return the list of MSTensor objects. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Preprocessed model input activation file name.
let inputName = 'input_data.bin';
let modelFile: string = '/path/to/xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(inputName)
  .then(async (buffer: Uint8Array) => {
    let inputBuffer = buffer.buffer;
    console.info(`Succeeded in reading input data. File name: ${inputName}, Buffer size: ${inputBuffer.byteLength}`);
    
    let mindSporeLiteModel: mindSporeLite.Model = await mindSporeLite.loadModelFromFile(modelFile);
    console.info(`Succeeded in loading model. Model file: ${modelFile}`);
    
    let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
    if (modelInputs == null || modelInputs.length === 0) {
      console.error(`Failed to get model inputs. Model file: ${modelFile}, Input count: ${modelInputs ? modelInputs.length : 0}`);
      return;
    }

    modelInputs[0].setData(inputBuffer);
    console.info(`Succeeded in setting input data. Input tensor: ${modelInputs[0].name}`);
    
    mindSporeLiteModel.predict(modelInputs, (mindSporeLiteTensor: mindSporeLite.MSTensor[]) => {
      if (mindSporeLiteTensor == null || mindSporeLiteTensor.length === 0) {
        console.error(`Failed to get prediction output. Model file: ${modelFile}, Output count: ${mindSporeLiteTensor ? mindSporeLiteTensor.length : 0}`);
      } else {
        let output = new Float32Array(mindSporeLiteTensor[0].getData());
        console.info(`Succeeded in prediction. Output length: ${output.length}`);
        for (let i = 0; i < Math.min(5, output.length); i++) {
          console.info(`Output[${i}]: ${output[i].toString()}`);
        }
      }
    })
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read input data. File name: ${inputName}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```
### predict

predict(inputs: MSTensor[]): Promise&lt;MSTensor[]&gt;

Performs model inference and returns the inference result. This API uses a promise to return the result asynchronously. Ensure that the model object is not reclaimed by the resource collector when this API is called.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name | Type                    | Mandatory | Description                           |
| ------ | ----------------------- | ---- | ------------------------------ |
| inputs | [MSTensor](#mstensor)[] | Yes   | Input list of the model. An MSTensor object. |

**Return value**

| Type                    | Description                   |
| ----------------------- | ---------------------- |
| Promise<[MSTensor](#mstensor)[]> | Promise object. Returns a list of MSTensor objects. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Preprocessed model input activation file name.
let inputName = 'input_data.bin';
let modelFile = '/path/to/xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(inputName)
  .then(async (buffer: Uint8Array) => {
    let inputBuffer = buffer.buffer;
    console.info(`Succeeded in reading input data. File name: ${inputName}, Buffer size: ${inputBuffer.byteLength}`);
    
    let mindSporeLiteModel: mindSporeLite.Model = await mindSporeLite.loadModelFromFile(modelFile);
    console.info(`Succeeded in loading model. Model file: ${modelFile}`);
    
    let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
    if (modelInputs == null || modelInputs.length === 0) {
      console.error(`Failed to get model inputs. Model file: ${modelFile}, Input count: ${modelInputs ? modelInputs.length : 0}`);
      return;
    }
    
    modelInputs[0].setData(inputBuffer);
    console.info(`Succeeded in setting input data. Input tensor: ${modelInputs[0].name}`);
    
    mindSporeLiteModel.predict(modelInputs).then((mindSporeLiteTensor: mindSporeLite.MSTensor[]) => {
      if (mindSporeLiteTensor == null || mindSporeLiteTensor.length === 0) {
        console.error(`Failed to get prediction output. Model file: ${modelFile}, Output count: ${mindSporeLiteTensor ? mindSporeLiteTensor.length : 0}`);
      } else {
        let output = new Float32Array(mindSporeLiteTensor[0].getData());
        console.info(`Succeeded in prediction. Output length: ${output.length}`);
        for (let i = 0; i < Math.min(5, output.length); i++) {
          console.info(`Output[${i}]: ${output[i].toString()}`);
        }
      }
    }).catch((error: Error) => {
      console.error(`Failed to execute prediction. Model file: ${modelFile}, Error: ${error.message}`);
    });
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read input data. File name: ${inputName}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```

### resize

resize(inputs: MSTensor[], dims: Array&lt;Array&lt;number&gt;&gt;): boolean

Resizes the tensors. It allows the model input shape to be dynamically modified at runtime without reloading the model. It is commonly used to process images of different sizes, dynamically adjust the batch size, or accelerate inference by reducing the resolution. It changes only the input shape while keeping the model weights unchanged, so that a single model can support multiple input configurations, saving storage and improving flexibility.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name | Type                  | Mandatory | Description                          |
| ------ | --------------------- | ---- | ----------------------------- |
| inputs | [MSTensor](#mstensor)[]            | Yes   | Input list of the model.  |
| dims   | Array&lt;Array&lt;number&gt;&gt; | Yes   | Target tensor size to be modified. |

**Return value**

| Type    | Description                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | Whether the tensor size is set successfully. The value **true** indicates that the tensor size is set successfully, and **false** indicates the opposite. |

**Example** 

```ts
let modelFile = '/path/to/xxx.ms';
mindSporeLite.loadModelFromFile(modelFile).then((mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  let originalShape = modelInputs[0].shape;
  console.info(`Original input shape: [${originalShape.join(', ')}]`);
  
  let newDim = [[1, 32, 32, 1]];
  let ret = mindSporeLiteModel.resize(modelInputs, newDim);
  
  if (ret === false) {
    console.error(`Failed to resize model inputs. Model file: ${modelFile}, Original shape: [${originalShape.join(', ')}], Target shape: [${newDim[0].join(', ')}]`);
  } else {
    console.info(`Succeeded in resizing model inputs. Model file: ${modelFile}, Original shape: [${originalShape.join(', ')}], New shape: [${modelInputs[0].shape.join(', ')}]`);
  }
}).catch((error: Error) => {
  console.error(`Failed to load model. Model file: ${modelFile}, Error: ${error.message}`);
});
```

### runStep<sup>12+</sup>

runStep(inputs: MSTensor[]): boolean

Performs a single-step training of the model. This API is used only for on-device training.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name    | Type                      | Mandatory  | Description       |
| ------ | ----------------------- | --- | -------- |
| inputs | [MSTensor](#mstensor)[] | Yes   | Input list of the model. |

**Return value**

| Type    | Description                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | Whether the single-step training of the model is successful. The value **true** indicates that the single-step training is successful, and **false** indicates the opposite. |

**Example** 

```ts
let modelFile = '/path/to/xxx.ms';
mindSporeLite.loadTrainModelFromFile(modelFile).then((mindSporeLiteModel: mindSporeLite.Model) => {
  mindSporeLiteModel.trainMode = true;
  console.info(`Succeeded in setting train mode. Model file: ${modelFile}, Train mode: ${mindSporeLiteModel.trainMode}`);
  
  const modelInputs = mindSporeLiteModel.getInputs();
  if (modelInputs == null || modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}, Input count: ${modelInputs ? modelInputs.length : 0}`);
    return;
  }
  
  let ret = mindSporeLiteModel.runStep(modelInputs);
  if (ret === false) {
    console.error(`Failed to run training step. Model file: ${modelFile}, Input count: ${modelInputs.length}`);
  } else {
    console.info(`Succeeded in running training step. Model file: ${modelFile}`);
  }
}).catch((error: Error) => {
  console.error(`Failed to load train model. Model file: ${modelFile}, Error: ${error.message}`);
});
```

### getWeights<sup>12+</sup>

getWeights(): MSTensor[]

Obtains all weights of the model. This API is used only for on-device training.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value**

| Type                      | Description         |
| ----------------------- | ---------- |
| [MSTensor](#mstensor)[] | List of weight tensors of the model. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let modelFile = 'xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(modelFile)
  .then((modelBuffer: Uint8Array) => {
    mindSporeLite.loadTrainModelFromBuffer(modelBuffer.buffer.slice(0))
      .then((mindSporeLiteModel: mindSporeLite.Model) => {
        mindSporeLiteModel.trainMode = true;
        console.info(`Succeeded in setting train mode. Model file: ${modelFile}`);
        
        const weights = mindSporeLiteModel.getWeights();
        if (weights == null || weights.length === 0) {
          console.error(`Failed to get model weights. Model file: ${modelFile}, Weights count: ${weights ? weights.length : 0}`);
        } else {
          console.info(`Succeeded in getting model weights. Model file: ${modelFile}, Weights count: ${weights.length}`);
          for (let i = 0; i < Math.min(3, weights.length); i++) {
            console.info(`Weight[${i}]: name=${weights[i].name}, shape=[${weights[i].shape.join(', ')}], dtype=${weights[i].dtype}, dataSize=${weights[i].dataSize}`);
          }
        }
      })
      .catch((error: Error) => {
        console.error(`Failed to load train model from buffer. Model file: ${modelFile}, Buffer size: ${modelBuffer.byteLength}, Error: ${error.message}`);
      });
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read model file from resources. File name: ${modelFile}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```

### updateWeights<sup>12+</sup>

updateWeights(weights: MSTensor[]): boolean

Updates the weights of the model. This API is used only for on-device training.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                    | Mandatory | Description           |
| ------- | ----------------------- | ---- | -------------- |
| weights | [MSTensor](#mstensor)[] | Yes   | List of weight tensors. |

**Return value**

| Type    | Description                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | Whether the weights are updated successfully. true indicates success, and false indicates failure. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let modelFile = 'xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(modelFile)
  .then((modelBuffer: Uint8Array) => {
    mindSporeLite.loadTrainModelFromBuffer(modelBuffer.buffer.slice(0))
      .then((mindSporeLiteModel: mindSporeLite.Model) => {
        mindSporeLiteModel.trainMode = true;
        console.info(`Succeeded in setting train mode. Model file: ${modelFile}`);
        
        const weights = mindSporeLiteModel.getWeights();
        if (weights == null || weights.length === 0) {
          console.error(`Failed to get model weights. Model file: ${modelFile}, Weights count: ${weights ? weights.length : 0}`);
          return;
        }
        
        let ret = mindSporeLiteModel.updateWeights(weights);
        if (ret === false) {
          console.error(`Failed to update model weights. Model file: ${modelFile}, Weights count: ${weights.length}`);
        } else {
          console.info(`Succeeded in updating model weights. Model file: ${modelFile}, Weights count: ${weights.length}`);
        }
      })
      .catch((error: Error) => {
        console.error(`Failed to load train model from buffer. Model file: ${modelFile}, Buffer size: ${modelBuffer.byteLength}, Error: ${error.message}`);
      });
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read model file from resources. File name: ${modelFile}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```

### setupVirtualBatch<sup>12+</sup>

setupVirtualBatch(virtualBatchMultiplier: number, lr: number, momentum: number): boolean

Sets the virtual batch for training. This API is used only for on-device training.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name                 | Type   | Mandatory | Description                                                 |
| ---------------------- | ------ | ---- | ---------------------------------------------------- |
| virtualBatchMultiplier | number | Yes   | Virtual batch multiplier, which must be an integer. A value less than 1 disables the virtual batch. A value of 1 is equivalent to disabling the virtual batch. A value greater than 1 splits a large batch into N small batches. |
| lr                     | number | Yes   | Learning rate, which controls the step size moved along the gradient direction in each parameter update. A value of -1 uses the default learning rate. A value less than 0 but not -1 is invalid and causes the setting to fail. A value of 0 fixes the current parameters. A value greater than 0 uses a custom learning rate. |
| momentum               | number | Yes   | Momentum, which accelerates training and reduces gradient oscillation. A value of -1 uses the system default momentum, which is the choice when the exact value is uncertain. A value of 0 disables momentum optimization and degrades to the pure gradient descent algorithm. A value between 0.5 and 0.9 achieves a good balance between training speed and stability. A value between 0.9 and 0.99 significantly accelerates the training process and is suitable for convex optimization problems. A value less than 0 but not -1 is invalid and causes the virtual batch setting to fail.                                              |

**Return value**

| Type    | Description                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | Whether the virtual batch is set successfully. The value true indicates that the virtual batch is set successfully, and false indicates the opposite. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let modelFile = 'xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(modelFile)
  .then((modelBuffer: Uint8Array) => {
    mindSporeLite.loadTrainModelFromBuffer(modelBuffer.buffer.slice(0))
      .then((mindSporeLiteModel: mindSporeLite.Model) => {
        mindSporeLiteModel.trainMode = true;
        console.info(`Succeeded in setting train mode. Model file: ${modelFile}`);
        
        let virtualBatchMultiplier = 2;
        let lr = -1;
        let momentum = -1;
        
        let ret = mindSporeLiteModel.setupVirtualBatch(virtualBatchMultiplier, lr, momentum);
        if (ret === false) {
          console.error(`Failed to setup virtual batch. Model file: ${modelFile}, Virtual batch multiplier: ${virtualBatchMultiplier}, Learning rate: ${lr}, Momentum: ${momentum}`);
        } else {
          console.info(`Succeeded in setting up virtual batch. Model file: ${modelFile}, Virtual batch multiplier: ${virtualBatchMultiplier}`);
        }
      })
      .catch((error: Error) => {
        console.error(`Failed to load train model from buffer. Model file: ${modelFile}, Buffer size: ${modelBuffer.byteLength}, Error: ${error.message}`);
      });
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read model file from resources. File name: ${modelFile}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```

### exportModel<sup>12+</sup>

exportModel(modelFile: string, quantizationType?: QuantizationType, exportInferenceOnly?: boolean, outputTensorName?: string[]): boolean

Exports a training model, which is used only for on-device training.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name              | Type                                    | Mandatory | Description                                                         |
| ------------------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| modelFile           | string                                  | Yes   | Path of the model file to export. The string length limit follows the file system.             |
| quantizationType    | [QuantizationType](#quantizationtype12) | No   | Quantization type. The default value is NO_QUANT.                                   |
| exportInferenceOnly | boolean                                 | No   | Whether to export only the inference model. The value true means to export only the inference model, and false means to export both the training model and the inference model. The default value is true. |
| outputTensorName    | string[]                                | No   | Names of the output tensors of the exported model. The default value is an empty string array, which means to export all tensors. |

**Return value**

| Type    | Description                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | Whether the training model is exported successfully. The value true means that the training model is exported successfully, and false means that the export fails. |

**Example** 

```ts
let modelFile = '/path/to/xxx.ms';
let newPath = '/newpath/to';
let exportPath = newPath + "/new_model.ms";
mindSporeLite.loadTrainModelFromFile(modelFile).then((mindSporeLiteModel: mindSporeLite.Model) => {
  mindSporeLiteModel.trainMode = true;
  console.info(`Succeeded in setting train mode. Model file: ${modelFile}`);
  
  let ret = mindSporeLiteModel.exportModel(exportPath, mindSporeLite.QuantizationType.NO_QUANT, true);
  if (ret === false) {
    console.error(`Failed to export model. Source: ${modelFile}, Target: ${exportPath}, Quantization type: NO_QUANT, Inference only: true`);
  } else {
    console.info(`Succeeded in exporting model. Source: ${modelFile}, Target: ${exportPath}`);
  }
}).catch((error: Error) => {
  console.error(`Failed to load train model. Model file: ${modelFile}, Error: ${error.message}`);
});
```

### exportWeightsCollaborateWithMicro<sup>12+</sup>

exportWeightsCollaborateWithMicro(weightFile: string, isInference?: boolean, enableFp16?: boolean, changeableWeightsName?: string[]): boolean

Exports the model weights for micro inference. This API is used only for on-device training.

**Micro inference**: an ultra-lightweight AI deployment solution of MindSpore Lite for MCUs (MicroControllerUnits). This solution directly converts the model into lightweight code in the offline phase, without the need to parse the model and compile the graph online on the device.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name                | Type     | Mandatory | Description                                                         |
| --------------------- | -------- | ---- | ------------------------------------------------------------ |
| weightFile            | string   | Yes   | Path of the weight file. The string length limit follows the file system.                   |
| isInference           | boolean  | No   | Whether to export weights from the inference model. The value **true** means to export weights from the inference model. Currently, only **true** is supported, and the default value is **true**. |
| enableFp16            | boolean  | No   | Whether to save floating-point weights in float16 format. The value **true** means to save them in float16 format, and **false** means not to save them in float16 format. The default value is **false**. |
| changeableWeightsName | string[] | No   | Names of the changeable weights. The default value is an empty string array.                     |

**Return value**

| Type    | Description                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | Whether the model weights for micro inference are exported successfully. The value **true** means that the model weights for micro inference are exported successfully, and **false** means the opposite. |

**Example** 

```ts
let modelFile = '/path/to/xxx.ms';
let microWeight = '/path/to/xxx.bin';
mindSporeLite.loadTrainModelFromFile(modelFile).then((mindSporeLiteModel: mindSporeLite.Model) => {
  let ret = mindSporeLiteModel.exportWeightsCollaborateWithMicro(microWeight);
  if (ret === false) {
    console.error(`Failed to export weights for micro. Model file: ${modelFile}, Target weight file: ${microWeight}`);
  } else {
    console.info(`Succeeded in exporting weights for micro. Model file: ${modelFile}, Target weight file: ${microWeight}`);
  }
}).catch((error: Error) => {
  console.error(`Failed to load train model. Model file: ${modelFile}, Error: ${error.message}`);
});
```

## MSTensor

Represents a model tensor instance. Describes the attributes and methods of an MSTensor object. Similar to arrays and matrices, it is the basic data structure used in MindSpore Lite network operations.

In the API examples below, you need to first obtain an MSTensor instance by using [getInputs](#getinputs), and then call the corresponding method through this instance.

### Attributes

**System capability:** SystemCapability.AI.MindSporeLite

| Name       | Type                  | Read-Only | Optional | Description                   |
| ---------- | --------------------- | ---- | ---- | ---------------------- |
| name       | string                | No   | No   | Name of the tensor.           |
| shape      | number[]              | No   | No   | Dimension array of the tensor.       |
| elementNum | number                | No   | No   | Total number of elements in the tensor.       |
| dataSize   | number                | No   | No   | Length of the tensor data.     |
| dtype      | [DataType](#datatype) | No   | No   | Data type of the tensor.       |
| format     | [Format](#format)     | No   | No   | Data layout of the tensor.   |

**Example** 

```ts
let modelFile = '/path/to/xxx.ms';
mindSporeLite.loadModelFromFile(modelFile).then((mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  if (modelInputs == null || modelInputs.length === 0) {
    console.error(`Failed to get model inputs. Model file: ${modelFile}`);
    return;
  }
  
  let tensor = modelInputs[0];
  console.info(`Succeeded in getting model inputs. Input name: ${tensor.name}, Shape: [${tensor.shape.join(', ')}], Element num: ${tensor.elementNum}, Dtype: ${tensor.dtype}, Format: ${tensor.format}, Data size: ${tensor.dataSize}`);
}).catch((error: Error) => {
  console.error(`Failed to load model. Model file: ${modelFile}, Error: ${error.message}`);
});
```

### getData

getData(): ArrayBuffer

Obtains the data of the tensor.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value**

| Type        | Description                 |
| ----------- | -------------------- |
| ArrayBuffer | Pointer to the data of the tensor. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Preprocessed model input activation file name.
let inputName = 'input_data.bin';
let modelFile = '/path/to/xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(inputName)
  .then(async (buffer: Uint8Array) => {
    let inputBuffer = buffer.buffer;
    console.info(`Succeeded in reading input data. File name: ${inputName}, Buffer size: ${inputBuffer.byteLength}`);
    
    let mindSporeLiteModel: mindSporeLite.Model = await mindSporeLite.loadModelFromFile(modelFile);
    console.info(`Succeeded in loading model. Model file: ${modelFile}`);
    
    let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
    if (modelInputs == null || modelInputs.length === 0) {
      console.error(`Failed to get model inputs. Model file: ${modelFile}`);
      return;
    }
    
    modelInputs[0].setData(inputBuffer);
    console.info(`Succeeded in setting input data. Input tensor: ${modelInputs[0].name}`);
    
    mindSporeLiteModel.predict(modelInputs).then((mindSporeLiteTensor: mindSporeLite.MSTensor[]) => {
      if (mindSporeLiteTensor == null || mindSporeLiteTensor.length === 0) {
        console.error(`Failed to get prediction output. Model file: ${modelFile}`);
      } else {
        let output = new Float32Array(mindSporeLiteTensor[0].getData());
        console.info(`Succeeded in prediction. Output length: ${output.length}`);
        for (let i = 0; i < Math.min(5, output.length); i++) {
          console.info(`Output[${i}]: ${output[i].toString()}`);
        }
      }
    }).catch((error: Error) => {
      console.error(`Failed to execute prediction. Model file: ${modelFile}, Error: ${error.message}`);
    });
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read input data. File name: ${inputName}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```

### setData

setData(inputArray: ArrayBuffer): void

Sets the data of the tensor.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters**

| Name     | Type        | Mandatory | Description                   |
| ---------- | ----------- | ---- | ---------------------- |
| inputArray | ArrayBuffer | Yes   | Input data buffer of the tensor. |

**Example** 

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Preprocessed model input activation file name.
let inputName = 'input_data.bin';
let modelFile = '/path/to/xxx.ms';
let globalContext = new UIContext().getHostContext() as common.UIAbilityContext;
globalContext.getApplicationContext()
  .resourceManager
  .getRawFileContent(inputName)
  .then(async (buffer: Uint8Array) => {
    let inputBuffer = buffer.buffer;
    console.info(`Succeeded in reading input data. File name: ${inputName}, Buffer size: ${inputBuffer.byteLength}`);
    
    let mindSporeLiteModel: mindSporeLite.Model = await mindSporeLite.loadModelFromFile(modelFile);
    console.info(`Succeeded in loading model. Model file: ${modelFile}`);
    
    let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
    if (modelInputs == null || modelInputs.length === 0) {
      console.error(`Failed to get model inputs. Model file: ${modelFile}`);
      return;
    }
    
    modelInputs[0].setData(inputBuffer);
    console.info(`Succeeded in setting input data. Input tensor: ${modelInputs[0].name}, Buffer size: ${inputBuffer.byteLength}`);
  })
  .catch((error: BusinessError) => {
    console.error(`Failed to read input data. File name: ${inputName}, Error code: ${error.code}, Error message: ${error.message}`);
  });
```

## DataType

Data type of the tensor.

**System capability:** SystemCapability.AI.MindSporeLite

| Name                | Value   | Description                |
| ------------------- | ---- | ------------------- |
| TYPE_UNKNOWN        | 0    | Unknown.          |
| NUMBER_TYPE_INT8    | 32   | Keeps the Int8 type.    |
| NUMBER_TYPE_INT16   | 33   | Keeps the Int16 type.   |
| NUMBER_TYPE_INT32   | 34   | Keeps the Int32 type.   |
| NUMBER_TYPE_INT64   | 35   | Keeps the Int64 type.   |
| NUMBER_TYPE_UINT8   | 37   | Keeps the UInt8 type.   |
| NUMBER_TYPE_UINT16  | 38   | Keeps the UInt16 type.  |
| NUMBER_TYPE_UINT32  | 39   | Keeps the UInt32 type.  |
| NUMBER_TYPE_UINT64  | 40   | Keeps the UInt64 type.  |
| NUMBER_TYPE_FLOAT16 | 42   | Keeps the Float16 type. |
| NUMBER_TYPE_FLOAT32 | 43   | Keeps the Float32 type. |
| NUMBER_TYPE_FLOAT64 | 44   | Keeps the Float64 type. |

## Format

Data layout of the tensor.

**System capability:** SystemCapability.AI.MindSporeLite

| Name           | Value   | Description                  |
| -------------- | ---- | --------------------- |
| DEFAULT_FORMAT | -1   | Unknown data layout.    |
| NCHW           | 0    | Data layout is NCHW.  |
| NHWC           | 1    | Data layout is NHWC.  |
| NHWC4          | 2    | Data layout is NHWC4. |
| HWKC           | 3    | Data layout is HWKC.  |
| HWCK           | 4    | Data layout is HWCK.  |
| KCHW           | 5    | Data layout is KCHW.  |
