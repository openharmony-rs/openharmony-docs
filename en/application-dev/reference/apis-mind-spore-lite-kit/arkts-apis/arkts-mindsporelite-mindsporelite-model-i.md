# Model

```TypeScript
interface Model
```

Provides manages model function. Including get inputs, predict ,resize.

**Since:** 10

**System capability:** SystemCapability.AI.MindSporeLite

## Modules to Import

```TypeScript
import { mindSporeLite } from '@kit.MindSporeLiteKit';
```

## exportModel

```TypeScript
exportModel(
      modelFile: string,
      quantizationType?: QuantizationType,
      exportInferenceOnly?: boolean,
      outputTensorName?: string[]): boolean
```

Export train model to file

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modelFile | string | Yes | model file path. |
| quantizationType | [QuantizationType](arkts-mindsporelite-mindsporelite-quantizationtype-e.md) | No | the quantization type, default NO_QUANT. |
| exportInferenceOnly | boolean | No | whether to export a inference only model, default true. |
| outputTensorName | string[] | No | the set of name of output tensor the exported inference model, |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean result if the operation is successful |

**Examples**

```TypeScript
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

## exportWeightsCollaborateWithMicro

```TypeScript
exportWeightsCollaborateWithMicro(
      weightFile: string,
      isInference?: boolean,
      enableFp16?: boolean,
      changeableWeightsName?: string[]): boolean
```

Export model's weights, which can be used in micro only. Only valid for Lite Train

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| weightFile | string | Yes | weight file path |
| isInference | boolean | No | whether to export weights from inference model, only support this is `true` for now, default true |
| enableFp16 | boolean | No | float-weight is whether to be saved in float16 format, default false |
| changeableWeightsName | string[] | No | changeable weights name |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean result if the operation is successful |

**Examples**

```TypeScript
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

## getInputs

```TypeScript
getInputs(): MSTensor[]
```

Get model input tensors.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value:**

| Type | Description |
| --- | --- |
| [MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md)[] | the MSTensor array of the inputs. |

**Examples**

```TypeScript
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

## getWeights

```TypeScript
getWeights(): MSTensor[]
```

Obtain all weights of the model

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value:**

| Type | Description |
| --- | --- |
| [MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md)[] | the weight tensors of the model |

**Examples**

```TypeScript
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

## predict

```TypeScript
predict(inputs: MSTensor[], callback: Callback<MSTensor[]>): void
```

Infer model

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputs | [MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md)[] | Yes | indicates the MSTensor array of the inputs. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md)[]&gt; | Yes | the callback of MSTensor array. |

**Examples**

```TypeScript
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

<a id="predict-1"></a>

## predict

```TypeScript
predict(inputs: MSTensor[]): Promise<MSTensor[]>
```

Infer model

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputs | [MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md)[] | Yes | indicates the MSTensor array of the inputs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md)[]&gt; | the promise returned by the function. |

**Examples**

```TypeScript
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

## resize

```TypeScript
resize(inputs: MSTensor[], dims: Array<Array<number>>): boolean
```

resize model input

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputs | [MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md)[] | Yes | indicates the MSTensor array of the inputs. |
| dims | Array&lt;Array&lt;number&gt;&gt; | Yes | indicates the target new shape array |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean result if the resize operation is successful |

**Examples**

```TypeScript
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

## runStep

```TypeScript
runStep(inputs: MSTensor[]): boolean
```

Train model by step

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputs | [MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md)[] | Yes | indicates the MSTensor array of the inputs. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean result if the runStep operation is successful |

**Examples**

```TypeScript
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

## setupVirtualBatch

```TypeScript
setupVirtualBatch(virtualBatchMultiplier: number, lr: number, momentum: number): boolean
```

Setup training with virtual batches

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| virtualBatchMultiplier | number | Yes | virtual batch multiplier, use any number &lt; 1 to disable |
| lr | number | Yes | learning rate to use for virtual batch, -1 for internal configuration |
| momentum | number | Yes | batch norm momentum to use for virtual batch, -1 for internal configuration |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean result if the operation is successful |

**Examples**

```TypeScript
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

## updateWeights

```TypeScript
updateWeights(weights: MSTensor[]): boolean
```

Update weights of the model

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| weights | [MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md)[] | Yes | indicates the MSTensor array of the inputs |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean result if updating weights operation is successful |

**Examples**

```TypeScript
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

## learningRate

```TypeScript
learningRate?: number
```

The learning rate of the training model

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

## trainMode

```TypeScript
trainMode?: boolean
```

The running mode of the model

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite
