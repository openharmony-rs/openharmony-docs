# NeuralNetworkRuntime

## Overview

Provides APIs for accelerating the Neural Network Runtime model inference.

**Since**: 9

## Files

| Name | Description |
| -- | -- |
| [neural_network_runtime_type.h](capi-neural-network-runtime-type-h.md) | Defines the structure and enumeration.<br> include "neural_network_runtime/neural_network_runtime_type.h" |
| [neural_network_core.h](capi-neural-network-core-h.md) | Defines the Neural Network Core APIs. The AI inference framework uses the Native APIs provided by Neural Network Core to compile models and perform inference and computing on acceleration hardware.<br> Note: Currently, the APIs of Neural Network Core do not support multi-thread calling. <br> include "neural_network_runtime/neural_network_core.h" |
| [neural_network_runtime.h](capi-neural-network-runtime-h.md) | Defines the Neural Network Runtime APIs. The AI inference framework uses the Native APIs provided by Neural Network Runtime to construct models.  Note: Currently, the APIs of Neural Network Runtime do not support multi-thread calling. <br> include "neural_network_runtime/neural_network_runtime.h" |
