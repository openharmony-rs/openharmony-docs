# @ohos.ai.mindSporeLite

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

## Modules to Import

```TypeScript
import { mindSporeLite } from '@kit.MindSporeLiteKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllNNRTDeviceDescriptions](arkts-mindsporelite-mindsporelite-getallnnrtdevicedescriptions-f.md) | Obtain the all device descriptions in NNRT. |
| [loadModelFromBuffer](arkts-mindsporelite-mindsporelite-loadmodelfrombuffer-f.md) | Create a Model instance from buffer |
| [loadModelFromBuffer](arkts-mindsporelite-mindsporelite-loadmodelfrombuffer-f.md) | Create a Model instance from buffer |
| [loadModelFromBuffer](arkts-mindsporelite-mindsporelite-loadmodelfrombuffer-f.md) | Create a Model instance from buffer |
| [loadModelFromFd](arkts-mindsporelite-mindsporelite-loadmodelfromfd-f.md) | Creates a Model instance file description |
| [loadModelFromFd](arkts-mindsporelite-mindsporelite-loadmodelfromfd-f.md) | Create a Model instance from file description |
| [loadModelFromFd](arkts-mindsporelite-mindsporelite-loadmodelfromfd-f.md) | Create a Model instance from file description |
| [loadModelFromFile](arkts-mindsporelite-mindsporelite-loadmodelfromfile-f.md) | Create a Model instance from file path |
| [loadModelFromFile](arkts-mindsporelite-mindsporelite-loadmodelfromfile-f.md) | Create a Model instance from file path. |
| [loadModelFromFile](arkts-mindsporelite-mindsporelite-loadmodelfromfile-f.md) | Create a Model instance from file path. |
| [loadTrainModelFromBuffer](arkts-mindsporelite-mindsporelite-loadtrainmodelfrombuffer-f.md) | Load train model from buffer |
| [loadTrainModelFromFd](arkts-mindsporelite-mindsporelite-loadtrainmodelfromfd-f.md) | Load train model from file description |
| [loadTrainModelFromFile](arkts-mindsporelite-mindsporelite-loadtrainmodelfromfile-f.md) | Load train model from file |

### Interfaces

| Name | Description |
| --- | --- |
| [Context](arkts-mindsporelite-mindsporelite-context-i.md) | Provides the device configurations |
| [CpuDevice](arkts-mindsporelite-mindsporelite-cpudevice-i.md) | Provides the CPU device info |
| [Extension](arkts-mindsporelite-mindsporelite-extension-i.md) | Provides the extension information of nnrt device |
| [Model](arkts-mindsporelite-mindsporelite-model-i.md) | Provides manages model function. Including get inputs, predict ,resize. |
| [MSTensor](arkts-mindsporelite-mindsporelite-mstensor-i.md) | Provides MSTensor definition |
| [NNRTDevice](arkts-mindsporelite-mindsporelite-nnrtdevice-i.md) | Provides the NNRT device info |
| [NNRTDeviceDescription](arkts-mindsporelite-mindsporelite-nnrtdevicedescription-i.md) | Provides the nnrt device description |
| [TrainCfg](arkts-mindsporelite-mindsporelite-traincfg-i.md) | Provides the train configuration |

### Enums

| Name | Description |
| --- | --- |
| [DataType](arkts-mindsporelite-mindsporelite-datatype-e.md) | Enum for provides MSTensor data type |
| [Format](arkts-mindsporelite-mindsporelite-format-e.md) | Enum for provides MSTensor format |
| [NNRTDeviceType](arkts-mindsporelite-mindsporelite-nnrtdevicetype-e.md) | Enum for nnrt device type |
| [OptimizationLevel](arkts-mindsporelite-mindsporelite-optimizationlevel-e.md) | Enum for optimization level |
| [PerformanceMode](arkts-mindsporelite-mindsporelite-performancemode-e.md) | Enum for performance mode |
| [Priority](arkts-mindsporelite-mindsporelite-priority-e.md) | Enum for scheduling priority |
| [QuantizationType](arkts-mindsporelite-mindsporelite-quantizationtype-e.md) | Enum for quantization type |
| [ThreadAffinityMode](arkts-mindsporelite-mindsporelite-threadaffinitymode-e.md) | Enum for provides CPU thread affinity mode |
