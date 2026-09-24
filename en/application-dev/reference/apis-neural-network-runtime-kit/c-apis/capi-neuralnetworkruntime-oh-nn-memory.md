# OH_NN_Memory

```c
typedef struct OH_NN_Memory {...} OH_NN_Memory
```

## Overview

Defines the memory structure.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: {@link NN_Tensor}

**Related module**: [NeuralNetworkRuntime](capi-neuralnetworkruntime.md)

**Header file**: [neural_network_runtime_type.h](capi-neural-network-runtime-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void * const data | Pointer to the shared memory. The shared memory is usually allocated by the underlying hardware driver. |
| const size_t length | Records the length of the shared memory, in bytes. |


