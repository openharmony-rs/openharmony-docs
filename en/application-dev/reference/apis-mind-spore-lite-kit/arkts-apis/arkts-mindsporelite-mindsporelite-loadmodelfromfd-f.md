# loadModelFromFd

## Modules to Import

```TypeScript
import { mindSporeLite } from '@kit.MindSporeLiteKit';
```

## loadModelFromFd

```TypeScript
function loadModelFromFd(
    model: number,
    context?: Context): Promise<Model>
```

Creates a Model instance file description

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| model | number | Yes | model indicates model file description to be loaded |
| context | [Context](arkts-mindsporelite-mindsporelite-context-i.md) | No | context indicates model context information |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Model](arkts-mindsporelite-mindsporelite-model-i.md)&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 1000001 | Invalid context. Possible causes: 1. The context target is incorrect; 2. The device information is incorrect.  **ArkTS mode:** This error code applies only to ArkTS-Sta. |
| 1000007 | Failed to create native model from file descriptor (fd). Possible causes: 1. The file descriptor (fd) is incorrect; 2. The model file is damaged.  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
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


<a id="loadmodelfromfd-1"></a>

## loadModelFromFd

```TypeScript
function loadModelFromFd(
    model: number, callback: Callback<Model>): void
```

Create a Model instance from file description

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| model | number | Yes | model indicates model file description to be loaded |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Model](arkts-mindsporelite-mindsporelite-model-i.md)&gt; | Yes | the callback of model |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 1000001 | Invalid context. Possible causes: 1. The context target is incorrect; 2. The device information is incorrect.  **ArkTS mode:** This error code applies only to ArkTS-Sta. |
| 1000007 | Failed to create native model from file descriptor (fd). Possible causes: 1. The file descriptor (fd) is incorrect; 2. The model file is damaged.  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
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


<a id="loadmodelfromfd-2"></a>

## loadModelFromFd

```TypeScript
function loadModelFromFd(
    model: number,
    context: Context, callback: Callback<Model>): void
```

Create a Model instance from file description

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| model | number | Yes | model indicates model file description to be loaded |
| context | [Context](arkts-mindsporelite-mindsporelite-context-i.md) | Yes | context indicates model context information |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Model](arkts-mindsporelite-mindsporelite-model-i.md)&gt; | Yes | the callback of model |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 1000001 | Invalid context. Possible causes: 1. The context target is incorrect; 2. The device information is incorrect.  **ArkTS mode:** This error code applies only to ArkTS-Sta. |
| 1000007 | Failed to create native model from file descriptor (fd). Possible causes: 1. The file descriptor (fd) is incorrect; 2. The model file is damaged.  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
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
