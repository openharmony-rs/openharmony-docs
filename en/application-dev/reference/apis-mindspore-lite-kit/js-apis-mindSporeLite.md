# @ohos.ai.mindSporeLite (On-device AI Framework)

<!--Kit: MindSpore Lite Kit-->
<!--Subsystem: AI-->
<!--Owner: @zhuguodong8-->
<!--Designer: @zhuguodong8; @jjfeing-->
<!--Tester: @principal87-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=d18790e6ef1247c1fd8194f3838e7698bf6e9bf2 translatedAt=2026-06-24T06:29:43.986Z pushedAt=2026-06-25T01:35:11.429Z -->

MindSpore Lite is a lightweight and high-performance on-device AI engine that provides standard model inference and training APIs and built-in universal high-performance operator libraries. It supports Neural Network Runtime Kit for a higher inference efficiency, empowering intelligent applications in all scenarios.

This topic describes the model inference and training capabilities supported by the MindSpore Lite AI engine.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version. Unless otherwise stated, the MindSpore model is used in the sample code.
> 
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { mindSporeLite } from '@kit.MindSporeLiteKit';
```

## mindSporeLite.loadModelFromFile

loadModelFromFile(model: string, callback: Callback&lt;Model&gt;): void

Loads the input model from the full path for CPU inference. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                     | Mandatory| Description                                            |
| -------- | ------------------------- | ---- | ------------------------------------------------ |
| model    | string                    | Yes  | Complete path of the input model. The string length is subject to the file system.|
| callback | Callback<[Model](#model)> | Yes  | Callback used to return the model object. If the check finds the model input is empty during the callback, the callback fails.                         |

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

Loads the input model from the full path for model inference. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                               | Mandatory| Description                  |
| -------- | ----------------------------------- | ---- | ---------------------- |
| model    | string                              | Yes  | Complete path of the input model. The string length is subject to the file system.|
| context | [Context](#context) | Yes| Configuration information of the running environment.|
| callback | Callback<[Model](#model)> | Yes | Callback used to return the model object. If the model input is empty during the callback, the callback fails. |

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

Loads the input model from the full path for model inference. This API uses a promise to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name | Type               | Mandatory| Description                                            |
| ------- | ------------------- | ---- | ------------------------------------------------ |
| model   | string              | Yes  | Complete path of the input model. The string length is subject to the file system.|
| context | [Context](#context) | No  | Configuration information of the running environment. By default, **CpuDevice** is used for initialization.   |

**Return value**

| Type                     | Description                        |
| ------------------------- | ---------------------------- |
| Promise<[Model](#model)> | Promise used to return the result, which is a **Model** object.|

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

Loads the input model from the memory for CPU inference. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                     | Mandatory| Description                    |
| -------- | ------------------------- | ---- | ------------------------ |
| model    | ArrayBuffer               | Yes  | Memory that contains the input model.        |
| callback | Callback<[Model](#model)> | Yes   | Callback used to return the model object. If the check finds that the model input is empty during the callback, the callback fails. |

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

Loads the input model from the memory for inference. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                               | Mandatory| Description                  |
| -------- | ----------------------------------- | ---- | ---------------------- |
| model    | ArrayBuffer                   | Yes  | Memory that contains the input model.|
| context | [Context](#context) | Yes | Configuration information of the running environment.|
| callback | Callback<[Model](#model)> | Yes   | Callback used to return the model object. If the check finds that the model input is empty during the callback, the callback fails. |

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

Loads the input model from the memory for inference. This API uses a promise to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name | Type               | Mandatory| Description                                         |
| ------- | ------------------- | ---- | --------------------------------------------- |
| model   | ArrayBuffer         | Yes  | Memory that contains the input model.                             |
| context | [Context](#context) | No  | Configuration information of the running environment. By default, **CpuDevice** is used for initialization.|

**Return value**

| Type                           | Description                        |
| ------------------------------- | ---------------------------- |
| Promise<[Model](#model)> | Promise used to return the result, which is a **Model** object.|

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

Loads the input model based on the specified file descriptor for CPU inference. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                               | Mandatory| Description                  |
| -------- | ----------------------------------- | ---- | ---------------------- |
| model    | number                         | Yes  | File descriptor of the input model. The **fd** value returned by the file system is passed.|
| callback | Callback<[Model](#model)> | Yes   | Callback used to return the model object. If the check finds that the model input is empty during the callback, the callback fails. |

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

Loads the input model based on the specified file descriptor for inference. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                               | Mandatory| Description                  |
| -------- | ----------------------------------- | ---- | ---------------------- |
| model    | number                   | Yes  | File descriptor of the input model. The **fd** value returned by the file system is passed.|
| context | [Context](#context) | Yes | Configuration information of the running environment.|
| callback | Callback<[Model](#model)> | Yes | Callback used to return the model object. If the check finds that the model input is empty during the callback, the callback fails. |

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

Loads the input model based on the specified file descriptor for inference. This API uses a promise to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name | Type               | Mandatory| Description                                         |
| ------- | ------------------- | ---- | --------------------------------------------- |
| model   | number              | Yes  | File descriptor of the input model. The **fd** value returned by the file system is passed. |
| context | [Context](#context) | No  | Configuration information of the running environment. By default, **CpuDevice** is used for initialization.|

**Return value**

| Type                     | Description                        |
| ------------------------- | ---------------------------- |
| Promise<[Model](#model)> | Promise used to return the result, which is a **Model** object.|

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

Loads the training model file based on the specified path. This API uses a promise to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                   | Mandatory| Description                                            |
| -------- | ----------------------- | ---- | ------------------------------------------------ |
| model    | string                  | Yes  | Complete path of the input model. The string length is subject to the file system.|
| trainCfg | [TrainCfg](#traincfg12) | No  | Model training configuration. The default value is an array of the default values of attributes in **TrainCfg**.    |
| context  | [Context](#context)     | No  | Configuration information of the running environment. By default, **CpuDevice** is used for initialization.   |

**Return value**

| Type                      | Description                  |
| ------------------------ | -------------------- |
| Promise<[Model](#model)> | Promise used to return the result, which is a **Model** object.|

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

Loads a training model from the memory buffer. This API uses a promise to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                   | Mandatory| Description                                         |
| -------- | ----------------------- | ---- | --------------------------------------------- |
| model    | ArrayBuffer             | Yes  | Memory accommodating the training model.                         |
| trainCfg | [TrainCfg](#traincfg12) | No  | Model training configuration. The default value is an array of the default values of attributes in **TrainCfg**. |
| context  | [Context](#context)     | No  | Configuration information of the running environment. By default, **CpuDevice** is used for initialization.|

**Return value**

| Type                      | Description                  |
| ------------------------ | -------------------- |
| Promise<[Model](#model)> | Promise used to return the result, which is a **Model** object.|

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

Loads the training model file from the file descriptor. This API uses a promise to return the result.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name  | Type                   | Mandatory| Description                                            |
| -------- | ----------------------- | ---- | ------------------------------------------------ |
| model    | number                  | Yes  | File descriptor of the training model. The **fd** value returned by the file system is passed.|
| trainCfg | [TrainCfg](#traincfg12) | No  | Model training configuration. The default value is an array of the default values of attributes in **TrainCfg**.    |
| context  | [Context](#context)     | No  | Configuration information of the running environment. By default, **CpuDevice** is used for initialization.   |

**Return value**

| Type                    | Description                        |
| ------------------------ | ---------------------------- |
| Promise<[Model](#model)> | Promise used to return the result, which is a **Model** object.|

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

Obtains all device descriptions in NNRt.

**System capability**: SystemCapability.AI.MindSporeLite

**Return value**

| Type                                               | Description                  |
| --------------------------------------------------- | ---------------------- |
| [NNRTDeviceDescription](#nnrtdevicedescription12)[] | NNRt device description array.|

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

Defines the configuration information of the running environment.

**System capability**: SystemCapability.AI.MindSporeLite

| Name  | Type                     | Read Only| Optional| Description                                                        |
| ------ | ------------------------- | ---- | ---- | ------------------------------------------------------------ |
| target | string[]                  | No  | Yes  | Target backend. The value can be **cpu** or **nnrt**. The default value is **cpu**.                |
| cpu    | [CpuDevice](#cpudevice)   | No  | Yes  | CPU backend device option. Set this parameter set only when **target** is set to **cpu**. The default value is an array of the default values of attributes in **CpuDevice**.|
| nnrt   | [NNRTDevice](#nnrtdevice) | No  | Yes  | NNRt backend device option. Set this parameter set only when **target** is set to **nnrt**. The default value is an array of the default values of attributes in **NNRTDevice**.|

**Example**

```ts
let context: mindSporeLite.Context = {};
context.target = ['cpu','nnrt'];
```

## CpuDevice

Defines the CPU backend device option.

**System capability**: SystemCapability.AI.MindSporeLite

| Name                  | Type                                     | Read Only| Optional| Description                                                        |
| ---------------------- | ----------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| threadNum              | number                                    | No  | Yes  | Number of runtime threads. The default value is **2**.                             |
| threadAffinityMode     | [ThreadAffinityMode](#threadaffinitymode) | No  | Yes  | Affinity mode for binding runtime threads to CPU cores. The default value is **mindSporeLite.ThreadAffinityMode.NO_AFFINITIES**.|
| threadAffinityCoreList | number[]                                  | No  | Yes  | List of CPU cores bound to runtime threads. Set this parameter only when **threadAffinityMode** is set. If **threadAffinityMode** is set to **mindSporeLite.ThreadAffinityMode.NO_AFFINITIES**, this parameter is empty. The number in the list indicates the SN of the CPU core. The default value is **[]**.|
| precisionMode          | string                                    | No  | Yes  | Whether to enable the Float16 inference mode. The value **preferred_fp16** means to enable half-precision inference and the default value **enforce_fp32** means to disable half-precision inference. Other settings are not supported.|

**Float16 inference mode**: a mode that uses half-precision inference. Float16 uses 16 bits to represent a number and therefore it is also called half-precision.

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

Specifies the affinity mode for binding runtime threads to CPU cores.

**System capability**: SystemCapability.AI.MindSporeLite

| Name              | Value  | Description        |
| ------------------ | ---- | ------------ |
| NO_AFFINITIES      | 0    | No affinities.    |
| BIG_CORES_FIRST    | 1    | Big cores first.|
| LITTLE_CORES_FIRST | 2    | Medium cores first.|

## NNRTDevice

Represents an NNRt device. Neural Network Runtime (NNRt) is a bridge that connects the upper-layer AI inference framework to the bottom-layer acceleration chip to implement cross-chip inference and computing of AI models. An NNRt backend can be configured for MindSpore Lite.

**System capability**: SystemCapability.AI.MindSporeLite

| Name                         | Type                               | Read Only| Optional| Description                    |
| ----------------------------- | ----------------------------------- | ---- | ------------------------ | ------------------------ |
| deviceID<sup>12+</sup>        | bigint                              | No| Yes | NNRt device ID. The default value is **0**.    |
| performanceMode<sup>12+</sup> | [PerformanceMode](#performancemode12) | No | Yes | NNRt device performance mode. The default value is **PERFORMANCE_NONE**.|
| priority<sup>12+</sup>        | [Priority](#priority12)               | No | Yes | NNRt inference task priority. The default value is **PRIORITY_MEDIUM**.|
| extensions<sup>12+</sup>      | [Extension](#extension12)[]         | No | Yes | Extended NNRt device configuration. This parameter is left empty by default.|

## PerformanceMode<sup>12+</sup>

Enumerates NNRt device performance modes.

**System capability**: SystemCapability.AI.MindSporeLite

| Name               | Value  | Description               |
| ------------------- | ---- | ------------------- |
| PERFORMANCE_NONE    | 0    | No special settings.       |
| PERFORMANCE_LOW     | 1    | Low power consumption.       |
| PERFORMANCE_MEDIUM  | 2    | Power consumption and performance balancing.|
| PERFORMANCE_HIGH    | 3    | High performance.       |
| PERFORMANCE_EXTREME | 4    | Ultimate performance.     |

## Priority<sup>12+</sup>

Enumerates NNRt inference task priorities.

**System capability**: SystemCapability.AI.MindSporeLite

| Name           | Value  | Description          |
| --------------- | ---- | -------------- |
| PRIORITY_NONE   | 0    | No priority preference.|
| PRIORITY_LOW    | 1    | Low priority.|
| PRIORITY_MEDIUM | 2    | Medium priority.|
| PRIORITY_HIGH   | 3    | High priority.|

## Extension<sup>12+</sup>

Defines the extended NNRt device configuration.

**System capability**: SystemCapability.AI.MindSporeLite

| Name               | Type       | Read Only| Optional| Description            |
| ------------------- | ----------- | ---- | ---- | ---------------- |
| name  | string      | No  | No  | Configuration name.      |
| value | ArrayBuffer | No  | No  | Memory accommodating the extended configuration.|

## NNRTDeviceDescription<sup>12+</sup>

Defines NNRt device information, including the device ID and device name.

**System capability**: SystemCapability.AI.MindSporeLite

### deviceID<sup>12+</sup>

deviceID() : bigint

Obtains the NNRt device ID.

**System capability**: SystemCapability.AI.MindSporeLite

**Return value**

| Type  | Description        |
| ------ | ------------ |
| bigint | NNRt device ID.|

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

Obtains the device model.

**System capability**: SystemCapability.AI.MindSporeLite

**Return value**

| Type                               | Description          |
| ----------------------------------- | -------------- |
| [NNRTDeviceType](#nnrtdevicetype12) | NNRt device type.|

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

**System capability**: SystemCapability.AI.MindSporeLite

**Return value**

| Type  | Description          |
| ------ | -------------- |
| string | NNRt device name.|

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

Enumerates NNRt device types.

**System capability**: SystemCapability.AI.MindSporeLite

| Name                  | Value  | Description                               |
| ---------------------- | ---- | ----------------------------------- |
| NNRTDEVICE_OTHERS      | 0    | Others (any device type except the following three types).|
| NNRTDEVICE_CPU         | 1    | CPU.                          |
| NNRTDEVICE_GPU         | 2    | GPU.                          |
| NNRTDEVICE_ACCELERATOR | 3    | Specific acceleration device.                   |

## TrainCfg<sup>12+</sup>

Defines the configuration for on-device training.

**System capability**: SystemCapability.AI.MindSporeLite

| Name                           | Type                                     | Read Only| Optional| Description                                                        |
| ------------------------------- | ----------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| lossName         | string[]                                  | No  | Yes  | List of loss functions. The default value is ["loss_fct", "_loss_fn", "SigmoidCrossEntropy"].|
| optimizationLevel | [OptimizationLevel](#optimizationlevel12) | No  | Yes  | Network optimization level for on-device training. The default value is **O0**.                        |

**Example**

```ts
let cfg: mindSporeLite.TrainCfg = {};
cfg.lossName = ["loss_fct", "_loss_fn", "SigmoidCrossEntropy"];
cfg.optimizationLevel = mindSporeLite.OptimizationLevel.O0;
```

## OptimizationLevel<sup>12+</sup>

Enumerates network optimization levels for on-device training.

**System capability**: SystemCapability.AI.MindSporeLite

| Name| Value  | Description                                                      |
| ---- | ---- | ---------------------------------------------------------- |
| O0   | 0    | No optimization level.                                              |
| O2   | 2    | Converts the precision type of the network to float16 and keeps the precision type of the batch normalization layer and loss function as float32.|
| O3   | 3    | Converts the precision type of the network (including the batch normalization layer) to float16.                   |
| AUTO | 4    | Selects an optimization level based on the device.                                    |

## QuantizationType<sup>12+</sup>

Enumerates quantization types.

**System capability**: SystemCapability.AI.MindSporeLite

| Name        | Value  | Description      |
| ------------ | ---- | ---------- |
| NO_QUANT     | 0    | No quantification.|
| WEIGHT_QUANT | 1    | Weight quantization.|
| FULL_QUANT   | 2    | Full quantization.  |

## Model

Represents a **Model** instance, with properties and APIs defined.

In the following sample code, you first need to use [loadModelFromFile()](#mindsporeliteloadmodelfromfile), [loadModelFromBuffer()](#mindsporeliteloadmodelfrombuffer), or [loadModelFromFd()](#mindsporeliteloadmodelfromfd) to obtain a **Model** instance before calling related APIs.

### Attributes

**System capability**: SystemCapability.AI.MindSporeLite

| Name                      | Type   | Read Only| Optional| Description                                                        |
| -------------------------- | ------- | ---- | ---- | ------------------------------------------------------------ |
| learningRate<sup>12+</sup> | number  | No  | Yes  | Learning rate of a training model. The default value is read from the loaded model.                |
| trainMode<sup>12+</sup>    | boolean | No  | Yes  | Training mode. The value **true** indicates the training mode, and the value **false** indicates the non-training mode. The default value is **true** for a training model and **false** for an inference model.|

### getInputs

getInputs(): MSTensor[]

Obtains the model input for inference.

**System capability**: SystemCapability.AI.MindSporeLite

**Return value**

| Type                   | Description              |
| ----------------------- | ------------------ |
| [MSTensor](#mstensor)[] | List of **MSTensor** objects. |

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

Executes the inference model. This API uses an asynchronous callback to return the result. Ensure that the model object is not reclaimed when being invoked.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name| Type                   | Mandatory| Description                      |
| ------ | ----------------------- | ---- | -------------------------- |
| inputs | [MSTensor](#mstensor)[] | Yes  | List of input models.  |
| callback | Callback<[MSTensor](#mstensor)[]> | Yes | Callback used to return the list of **MSTensor** objects. . |

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// File name of the preprocessed model input data
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

Executes model inference. This API uses a promise to return the result. Ensure that the model object is not reclaimed when being invoked.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name| Type                   | Mandatory| Description                          |
| ------ | ----------------------- | ---- | ------------------------------ |
| inputs | [MSTensor](#mstensor)[] | Yes  | List of input models.  |

**Return value**

| Type                   | Description                  |
| ----------------------- | ---------------------- |
| Promise<[MSTensor](#mstensor)[]> | Promise used to return the result, List of **MSTensor** objects.|

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// File name of the preprocessed model input data
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

Resets the tensor size. It allows dynamic modification of model input shapes at runtime without reloading the model. It is commonly used to process images of different sizes, dynamically adjust batch sizes, or accelerate inference by reducing resolution. It only changes the input shape while keeping the model weights unchanged, enabling a single model to support multiple input configurations, saving storage and improving flexibility.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name| Type                 | Mandatory| Description                         |
| ------ | --------------------- | ---- | ----------------------------- |
| inputs | [MSTensor](#mstensor)[]            | Yes  | List of input models. |
| dims   | Array&lt;Array&lt;number&gt;&gt; | Yes  | Target tensor size.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Result indicating whether the setting is successful. The value **true** indicates that the tensor size is successfully reset, and the value **false** indicates the opposite.|

**Example**

```ts
let modelFile = '/path/to/xxx.ms';
mindSporeLite.loadModelFromFile(modelFile).then((mindSporeLiteModel: mindSporeLite.Model) => {
  let modelInputs: mindSporeLite.MSTensor[] = mindSporeLiteModel.getInputs();
  let originalShape = modelInputs[0].shape;
  console.info(`Original input shape: [${originalShape.join(', ')}]`);
  
  let new_dim = [[1, 32, 32, 1]];
  let ret = mindSporeLiteModel.resize(modelInputs, new_dim);
  
  if (ret === false) {
    console.error(`Failed to resize model inputs. Model file: ${modelFile}, Original shape: [${originalShape.join(', ')}], Target shape: [${new_dim[0].join(', ')}]`);
  } else {
    console.info(`Succeeded in resizing model inputs. Model file: ${modelFile}, Original shape: [${originalShape.join(', ')}], New shape: [${modelInputs[0].shape.join(', ')}]`);
  }
}).catch((error: Error) => {
  console.error(`Failed to load model. Model file: ${modelFile}, Error: ${error.message}`);
});
```

### runStep<sup>12+</sup>

runStep(inputs: MSTensor[]): boolean

Defines a single-step training model. This API is used only for on-device training.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name   | Type                     | Mandatory | Description      |
| ------ | ----------------------- | --- | -------- |
| inputs | [MSTensor](#mstensor)[] | Yes  | List of input models.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Result indicating whether the operation is successful. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite.|

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

Obtains all weight tensors of a model. This API is used only for on-device training.

**System capability**: SystemCapability.AI.MindSporeLite

**Return value**

| Type                     | Description        |
| ----------------------- | ---------- |
| [MSTensor](#mstensor)[] | The weight tensor list of the model. |

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

Weight of the updated model, which is used only for on-device training.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name | Type                   | Mandatory| Description          |
| ------- | ----------------------- | ---- | -------------- |
| weights | [MSTensor](#mstensor)[] | Yes  | List of weight tensors.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Result indicating whether the operation is successful. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite.|

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

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name                | Type  | Mandatory| Description                                                |
| ---------------------- | ------ | ---- | ---------------------------------------------------- |
| virtualBatchMultiplier | number | Yes  | Virtual batch multiplier, which must be an integer. A value less than 1 indicates that the virtual batch is disabled. A value of 1 is equivalent to disabling the virtual batch. A value greater than 1 indicates that a large batch is split into multiple small batches. |
| lr                     | number | Yes  | Learning rate, which controls the step size of moving along the gradient direction during each parameter update. A value of -1 indicates that the default learning rate is used. A value less than -1 or greater than -1 but less than 0 indicates an invalid value, which will cause the setting to fail. A value of 0 indicates that the current parameters are fixed. A value greater than 0 indicates a custom learning rate. |
| momentum               | number | Yes  | Momentum, which is used to accelerate training and reduce gradient oscillation. A value of -1 indicates that the system default momentum value is used, which is the choice when the specific value is uncertain. A value of 0 indicates that momentum optimization is not used, and the algorithm degrades to a pure gradient descent algorithm. A value between 0.5 and 0.9 can achieve a good balance between training speed and stability. A value between 0.9 and 0.99 can significantly accelerate the training process and is suitable for convex optimization problems. A value less than 0 and not -1 indicates an invalid value, which will cause the virtual batch setting to fail.                                              |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Result indicating whether the operation is successful. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite.|

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

Exports a training model. This API is used only for on-device training.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name             | Type                                   | Mandatory| Description                                                        |
| ------------------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| modelFile           | string                                  | Yes  | File path of the training models. The string length is subject to the file system.            |
| quantizationType    | [QuantizationType](#quantizationtype12) | No  | Quantization type. The default value is **NO_QUANT**.                                  |
| exportInferenceOnly | boolean                                 | No  | Whether to export inference models only. The value **true** means to export only inference models, and the value **false** means to export both training and inference models. The default value is **true**.|
| outputTensorName    | string[]                                | No  | Name of the output tensor of the exported training model. The default value is an empty string array, which indicates full export.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Result indicating whether the operation is successful. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite.|

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

Exports model weights for micro inference usage, only for on-device training.

Micro inference is an ultra-lightweight micro AI deployment solution provided by MindSpore Lite to deploy hardware backends for Micro Controller Units (MCUs). This solution directly converts models into lightweight code in offline mode, eliminating the need for online model parsing and graph compilation.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name               | Type    | Mandatory| Description                                                        |
| --------------------- | -------- | ---- | ------------------------------------------------------------ |
| weightFile            | string   | Yes  | Path of the weight file. The string length is subject to the file system.                  |
| isInference           | boolean  | No  | Whether to export weights from the inference model. The value **true** means to export weights from the inference model. The default value is **true**. Currently, only **true** is supported.|
| enableFp16            | boolean  | No  | Whether to store floating-point weights in float16 format. The value **true** means to store floating-point weights in float16 format, and the value **false** means the opposite. The default value is **false**.|
| changeableWeightsName | string[] | No  | Name of the variable weight. The default value is an empty string array.                    |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Result indicating whether the operation is successful. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite.|

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

Represents an **MSTensor** instance, with properties and APIs defined. It is a special data structure similar to arrays and matrices. It is the basic data structure used in MindSpore Lite network operations.

In the following sample code, you first need to use [getInputs()](#getinputs) to obtain an **MSTensor** instance before calling related APIs.

### Attributes

**System capability**: SystemCapability.AI.MindSporeLite

| Name      | Type                 | Read Only| Optional| Description                  |
| ---------- | --------------------- | ---- | ---- | ---------------------- |
| name       | string                | No  | No  | Tensor name.          |
| shape      | number[]              | No  | No  | Tensor dimension array.      |
| elementNum | number                | No  | No  | Length of the tensor dimension array.|
| dataSize   | number                | No  | No  | Length of tensor data.    |
| dtype      | [DataType](#datatype) | No  | No  | Tensor data type.      |
| format     | [Format](#format)     | No  | No  | Tensor data format.  |

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

Obtains tensor data.

**System capability**: SystemCapability.AI.MindSporeLite

**Return value**

| Type       | Description                |
| ----------- | -------------------- |
| ArrayBuffer | Pointer to the tensor data.|

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// File name of the preprocessed model input data
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

Sets the tensor data.

**System capability**: SystemCapability.AI.MindSporeLite

**Parameters**

| Name    | Type       | Mandatory| Description                  |
| ---------- | ----------- | ---- | ---------------------- |
| inputArray | ArrayBuffer | Yes  | Input data buffer of the tensor.|

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// File name of the preprocessed model input data
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

Tensor data type.

**System capability**: SystemCapability.AI.MindSporeLite

| Name               | Value  | Description               |
| ------------------- | ---- | ------------------- |
| TYPE_UNKNOWN        | 0    | Unknown type.         |
| NUMBER_TYPE_INT8    | 32   | Int8 type.   |
| NUMBER_TYPE_INT16   | 33   | Int16 type.  |
| NUMBER_TYPE_INT32   | 34   | Int32 type.  |
| NUMBER_TYPE_INT64   | 35   | Int64 type.  |
| NUMBER_TYPE_UINT8   | 37   | UInt8 type.  |
| NUMBER_TYPE_UINT16  | 38   | UInt16 type. |
| NUMBER_TYPE_UINT32  | 39   | UInt32 type. |
| NUMBER_TYPE_UINT64  | 40   | UInt64 type. |
| NUMBER_TYPE_FLOAT16 | 42   | Float16 type.|
| NUMBER_TYPE_FLOAT32 | 43   | Float32 type.|
| NUMBER_TYPE_FLOAT64 | 44   | Float64 type.|

## Format

Enumerates tensor data formats.

**System capability**: SystemCapability.AI.MindSporeLite

| Name          | Value  | Description                 |
| -------------- | ---- | --------------------- |
| DEFAULT_FORMAT | -1   | Unknown data format.   |
| NCHW           | 0    | NCHW format. |
| NHWC           | 1    | NHWC format. |
| NHWC4          | 2    | NHWC4 format.|
| HWKC           | 3    | HWKC format. |
| HWCK           | 4    | HWCK format. |
| KCHW           | 5    | KCHW format. |